# Changelog
# Changelog
### 1.0.0 (2015-10-13)
* **This release contains breaking changes, read through this list before updating.**
* The following, deprecated, methods have been removed:
    * `Session::refreshToken()`
    * `Session::requestToken()`
    * `SpotifyWebAPI::deletePlaylistTracks()`
    * `SpotifyWebAPI::reorderPlaylistTracks()`
    * `SpotifyWebAPI::replacePlaylistTracks()`
* Added docs for the `market` parameter to the following methods:
    * `SpotifyWebAPI::getAlbums()`
    * `SpotifyWebAPI::getAlbumTracks()`
    * `SpotifyWebAPI::getMySavedTracks()`
    * `SpotifyWebAPI::getTrack()`
    * `SpotifyWebAPI::getTracks()`
    * `SpotifyWebAPI::getUserPlaylist()`
    * `SpotifyWebAPI::getUserPlaylistTracks()`
* `Session::setRefreshToken()` has been removed, a refresh token is now passed directly to `Session::refreshAccessToken()` instead. [#20](https://github.com/jwilsson/spotify-web-api-php/issues/20).
* `Session::getExpires()` has been removed and `Session::getTokenExpiration()` has been added instead, returning the exact token expiration time.
* The minimum required PHP version has been increased to 5.5 and support for PHP 7 has been added.
* HTTP response headers returned by `Request::send()` and `SpotifyWebAPI::getLastResponse()` are now parsed to an array.
* In `SpotifyWebAPI::deleteUserPlaylistTracks()`, `position` has been renamed to `positions` (note the extra "s"). This change was made to better align with the official Spotify docs.
* The `positions` argument to `SpotifyWebAPI::deleteUserPlaylistTracks()` now also accept `int`s.
* `SpotifyWebAPI::getArtistTopTracks()` now accepts an array of options.
* `Session::getAuthorizeUrl()` no longer sends empty query strings.
* Stopped `SpotifyWebAPI::deleteUserPlaylistTracks()` from sending internal, leftover data.
* Clarified docs for `SpotifyWebAPI::followPlaylist()` and `SpotifyWebAPI::reorderUserPlaylistTracks()`.
* Fixed an issue where `SpotifyWebAPI::reorderUserPlaylistTracks()` couldn't reorder the first track.
[#39](https://github.com/jwilsson/spotify-web-api-php/pull/39) props [@vorenusgithub](https://github.com/vorenusgithub).
* Better tests and coverage.

### 0.10.0 (2015-09-05)
* The following methods has been added:
    * `SpotifyWebAPI::getUserFollowedArtists()`

### 0.9.0 (2015-07-06)
* **This release contains breaking changes, read through this list before updating.**
* As we're moving closer to 1.0 the work to make the API more consistent and stable is continuing. This time with an effort to make method names and signatures more consistent.
* Thus, the following methods have been renamed and the old names are deprecated:
    * `SpotifyWebAPI::deletePlaylistTracks()` -> `SpotifyWebAPI::deleteUserPlaylistTracks()`
    * `SpotifyWebAPI::reorderPlaylistTracks` -> `SpotifyWebAPI::reorderUserPlaylistTracks()`
    * `SpotifyWebAPI::replacePlaylistTracks()` -> `SpotifyWebAPI::replaceUserPlaylistTracks()`
* The following method arguments now also accepts strings:
    * `fields` in `SpotifyWebAPI::getUserPlaylistTracks()`.
    * `fields` in `SpotifyWebAPI::getUserPlaylist()`.
    * `album_type` in `SpotifyWebAPI::getArtistAlbums()`.
    * `ids` in `SpotifyWebAPI::userFollowsPlaylist()`.
* A new method, `SpotifyWebAPI::getLastResponse()` has been introduced which allows for retrieval of the latest full response from the Spotify API.
* Lots of internal changes to increase code consistency and ensure full PSR-2 compatibility.
* Better handling of errors from cURL.

### 0.8.2 (2015-05-02)
* CA Root Certificates are now included with the library, allowing cURL to always find it. [#32](https://github.com/jwilsson/spotify-web-api-php/issues/32).

### 0.8.1 (2015-03-29)
* Fixed an issue where `SpotifyWebAPI::updateUserPlaylist()` would fail without `name` set.

### 0.8.0 (2015-03-22)
* **This release contains breaking changes, read through this list before updating.**
* The following methods have been renamed:
    * `Session::refreshToken()` -> `Session::refreshAccessToken()`
    * `Session::requestToken()` -> `Session::requestAccessToken()`
* The following methods has been added:
    * `SpotifyWebAPI::currentUserFollows()`
    * `SpotifyWebAPI::followArtistsOrUsers()`
    * `SpotifyWebAPI::followPlaylist()`
    * `SpotifyWebAPI::getCategoriesList()`
    * `SpotifyWebAPI::getCategory()`
    * `SpotifyWebAPI::getFeaturedPlaylists()`
    * `SpotifyWebAPI::reorderPlaylistTracks()`
    * `SpotifyWebAPI::unfollowArtistsOrUsers()`
    * `SpotifyWebAPI::unfollowPlaylist()`
    * `SpotifyWebAPI::userFollowsPlaylist()`
* The `$redirectUri` argument in `Session::__construct()` is now optional.

## 0.7.0 (2014-12-06)
* The following methods to control the return type of all API methods were added:
    * `Request::getReturnAssoc()`
    * `Request::setReturnAssoc()`
    * `SpotifyWebAPI::getReturnAssoc()`
    * `SpotifyWebAPI::setReturnAssoc()`
* Added `fields` option to `SpotifyWebAPI::getUserPlaylist()`.
* All methods now automatically send authorization headers (if a access token is supplied), increasing rate limits.
* Lots of inline documentation improvements.

## 0.6.0 (2014-10-26)
* **This release contains breaking changes, read through this list before updating.**
* All static methods on `Request` have been removed. `Request` now needs to be instantiated before using.
* All methods that accepted the `limit` option now uses the correct Spotify default value if nothing has been specified.
* It's now possible to specify your own `Request` object in `SpotifyWebAPI` and `Session` constructors.
* `SpotifyWebAPI::getArtistAlbums()` now supports the `album_type` option.
* `Request::send()` will only modify URLs when needed.

## 0.5.0 (2014-10-25)
* The following methods has been added
    * `Session::getExpires()`
    * `Session::getRefreshToken()`
    * `Session::setRefreshToken()`
    * `SpotifyWebAPI::getFeaturedPlaylists()`
    * `SpotifyWebAPI::getNewReleases()`
* The following options has been added
    * `offset` and `limit` to `SpotifyWebAPI::getUserPlaylists()`
    * `offset` and `limit` to `SpotifyWebAPI::getUserPlaylistTracks()`
    * `fields` to `SpotifyWebAPI::getUserPlaylistTracks()`
    * `market` to `SpotifyWebAPI::getArtistAlbums()`
    * `market` to `SpotifyWebAPI::search()`
* Better handling of HTTP response codes in `Request::send()`.
* Fixed a bug where `SpotifyWebAPIException` messages weren't correctly set.
* Fixed various issues related to user playlists.

## 0.4.0 (2014-09-01)
* **This release contains lots of breaking changes, read through this list before updating.**
* All methods which previously required a Spotify URI now just needs an ID.
* `deletePlaylistTrack()` has been renamed to `deletePlaylistTracks()`.
* When something goes wrong, a `SpotifyWebAPIException` is thrown.
* The `SpotifyWebAPI` methods are no longer static, you'll need to instantiate the class now.

## 0.3.0 (2014-08-23)
* Added new methods to
    * Get Current User’s Saved Tracks.
    * Check Current User’s Saved Tracks.
    * Save Tracks for Current User.
    * Remove Tracks for Current User.
    * Change a Playlist’s Details.
    * Remove Tracks from a Playlist.
    * Replace a Playlist’s Tracks.
* Added support for the Client Credentials Authorization Flow.
* Added support for more HTTP methods in `Request::send()`.

## 0.2.0 (2014-07-26)
* Added Artist’s Related Artists endpoint.
* Added `offset` and `limit` options for `SpotifyWebAPI::getAlbumTracks()` and `SpotifyWebAPI::getArtistAlbums()`.
* Replaced PSR-0 autoloading with PSR-4 autoloading.
* Changed method signature of `Session::getAuthorizeUrl()` and added `show_dialog` option.
* Added missing returns for `SpotifyWebAPI::getUserPlaylist()` and `SpotifyWebAPI::getUserPlaylistTracks()`.
* Fixed a bug where search terms were double encoded.

## 0.1.0 (2014-06-28)
* Initial release
