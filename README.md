# API Testing project for spotify

The scope of this project is to use all API knowledge gained throught the Software Testing course and apply them in practice, using a live application.

Application under test:
The **Spotify** Web API provides a wide range of functionality for developers, including:
- Retrieve data from your favorite artist, album, or show.
- Search for Spotify content.
- Control and interact with the playback, play and resume, seek to a position, or retrieve your queue.
- Manage your personal library by creating a new playlist and adding your favorite tracks to it.
- Get recommendations based on the music you listen to the most.
- And much more! You can find a complete list of available endpoints in the [API Reference](https://developer.spotify.com/documentation/web-api/tutorials/getting-started).
For more details about documentation, visit this [website](https://developer.spotify.com/documentation/web-api/tutorials/getting-started).

Tools used: Postman, Newman.

 Link to collection :[API postman spotify collection ](https://github.com/legendadr/API-Testing/blob/main/Spotify.postman_collection.json).

## How the token was created
### First Steps:

- Go to [Spotify](https://www.spotify.com/) and create a new user account.
- Access the dashboard and log in with the user account you created.
- Click on the "Create an app" button.
- Enter a name and description for the new application created.
- Accept the terms and conditions and click on the create button.
- In the opened window, click on "Edit Settings."
- In the Redirect URIs textbox, enter a link. It doesn't have to be specific, but one that can be used later. Example: `http://applicationcourse/callback`.
- Click on the SAVE button at the bottom.

### Second Steps:

- Open Postman aplication,you can download this  [Postman](https://www.postman.com/) and create a new collection named "Spotify."
- Within the collection, create a new POST request.
- Click on authorization and select from the dropdown type OAuth 2.0.
- In the Callback URL field, enter the Redirect URIs from the first steps. If you are using the Postman web app, you don't need to set it.
- Copy the Client ID and Client Secret from your application and paste them into Postman.
- Treat these links as variables; assign them names and set them as global variables instead of using the actual links.
- In the Access Token URL field, enter the link `https://accounts.spotify.com/api/token`. After that, put the link `https://accounts.spotify.com/authorize` in the Auth URL field, and enter the text "playlist-modify-public playlist-read-private playlist-modify-private" in the Scope field.
- Finally, press "Get New Access Token". The token has been created.

The response will return an **access token valid for 1 hour**

## Types available for testing

HTTP methods supported by this API are GET, POST, PUT, PATCH, and DELETE. In this section, you can explore and perform tests on various types of operations supported by the Spotify Web API. Some examples include:

- **GET Requests:** Retrieve information about artists, albums, playlists, etc.
- **POST Requests:** Create new playlists, add tracks, etc.
- **PUT and PATCH Requests:** Update existing data, modify playlists, etc.
- **DELETE Requests:** Remove playlists, tracks, etc.

## Tests used for validation

For this API, an authentication token is needed.
#### I send responses to some endpoints:
- `https://api.spotify.com/v1/users/{user_id}/playlists` (Create playlist)
- `https://api.spotify.com/v1/playlists/{playlist_id}/tracks` (Add Item to playlist)
- `https://api.spotify.com/v1/playlists/{playlist_id}/tracks` (Update Item to playlist)
- `https://api.spotify.com/v1/playlists/{playlist_id}` (Get playlist)
- `https://api.spotify.com/v1/playlists/{playlist_id}/tracks` (Remove playlistItem)
- `https://api.spotify.com/v1/playlists/{playlist_id}` (Change playlist details)
- `https://api.spotify.com/v1/playlists/{playlist_id}/tracks` (Add item in playlist)
- `https://api.spotify.com/v1/playlists/{playlist_id}/followers` (Follow playlist)
- Using all available HTTP methods.
- The expected HTTP responses are received together with the HTTP messages following the requests (200, 201, 204,404 and 401).
- I wrote test-cases through which I validated the answer coming from the available templates that Postman offers.
  Here you can find the list of [Test conditions](https://github.com/legendadr/API-Testing/blob/main/API_CheckList_TestCondition.xlsx) in Postman.


## Tests performed

1.**Create Playlist**
- HTTP method for request:POST.
- Request description:Create a playlist for a Spotify user. (The playlist will be empty until you add tracks.) Each user is generally limited to a maximum of 11000 playlists.
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:201 Created.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/post%20create%20playlist%20request.png)
![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/request%20create%20playlist%20response%20.png)

JavaScript Tests:

![Screennhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/Test%20java%20script%20post%20create%20playlist.png)
![Screenshot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/java%20script%20test%20result%20for%20create%20playlist.png)

2.**Add Item in playlist**
- HTTP method for request:POST.
- Request description:Add one or more items to a user's playlist.
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:201 Created.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/addItemInPlaylist%20request.png)

JavaScript Tests:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/Java%20script%20test%20result%20additeminplaylist.png)


After retesting on the 11.03.2024 I found two bugs,"Verify that Status code is 201 Created | AssertionError: expected response to have status code 201 but got 200 " and 
"Verify that snapshot_id exists and has 60 characters | AssertionError: expected 'AAAAATmEmsKBy5L0X3xNY7e/F/r+QmfC' to have a length of 60 but got 32 "

- response body
![Screenhot api request with response body ](https://github.com/AdrianPricopie/API-Testing/blob/main/addItemInPlaylist%20request(2).png)

-javascript test code:

![Screenhot api request with response body ](https://github.com/AdrianPricopie/API-Testing/blob/main/addItemInPlaylist%20request(3).png)


3.**Update Playlist Items**
- HTTP method for request:PUT.
- Request description:Either reorder or replace items in a playlist depending on the request's parameters. To reorder items, include range_start, insert_before, range_length and snapshot_id in the request's body. To replace items, include uris as either a query parameter or in the request's body. Replacing items in a playlist will overwrite its existing items. This operation can be used for replacing or clearing items in a playlist.
Note: Replace and reorder are mutually exclusive operations which share the same endpoint, but have different parameters. These operations can't be applied together in a single request.
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/UpdatPlaylistItem%20request.png)

JavaScript Tests:
![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/test%20java%20script%20updateitemplaylist.png)



4.**Get Playlist**
- HTTP method for request:GET.
- Request description:Get a playlist owned by a Spotify user.
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:201 Created.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/Get%20playlist%20item.png)

JavaScript Tests:

![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/get%20playlist%20item%20test%20javascript.png)
![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/javascript%20test%20result%20getplaylistitem.png)

5.**Change Playlist Details**
- HTTP method for request:PUT.
- Request description:Change a playlist's name and public/private state. (The user must, of course, own the playlist.)
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/changePlaylistDetails.png)

JavaScript Tests:

![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/changePlaylistDetails%20Test%20Java.png)


6.**Get Artist**
- HTTP method for request:GET.
- Request description:Get Spotify catalog information for a single artist identified by their unique Spotify ID.This endpoint makes an HTTP GET request to retrieve information about a specific artist from the Spotify API. The response will include details such as the artist's external URLs, number of followers, genres, images, name, and popularity. The response will be in JSON format with a status code of 200.
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/GetAnArtist.png)

JavaScript Tests:

![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/Test%20Java%20script%20GetArtist.png)
![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/Test%20Java%20script%20GetArtist%20%232.png)
![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/Test%20Java%20script%20GetArtist%20%233.png)


7.**Follow Playlist**
- HTTP method for request:PUT.
- Request description:Add the current user as a follower of a playlist.This endpoint allows you to follow a playlist on Spotify by sending an HTTP PUT request to the specified URL. The request should include a payload with the "public" key set to a boolean value to indicate whether the playlist should be made public.
The response to the request will have a status code of 200 and a content type of text/xml. However, the response body will be null.
- Test types / techniques used:Functional testing,performance testing,positive testing.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/FollowPlaylist.png)

JavaScript Tests:

![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/Test%20Java%20script%20FollowPlaylist.png)


8.**Follow Playlist With invalid token**
- HTTP method for request:PUT.
- Request description:Add the current user as a follower of a playlist.The API responds with a status code of 401 and a JSON object containing an error status and message.
- Test types / techniques used:Functional testing,performance testing,negative testing.
- Response status code:401 Unauthorized.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/FollowPlaylistWithInvalidToken.png)


JavaScript Tests:

![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/java%20script%20test%20FollowPlaylistWithinvalidtoken.png)


9.**UnFollow Playlist**
- HTTP method for request:DELETE.
- Request description:Remove the current user as a follower of a playlist.
- Test types / techniques used:Functional testing,performance testing,pozitive testing.
- Response status code:200 OK.

Below you can find a picture of the API request from Postman:

![Screenhot api request with response body ](https://github.com/legendadr/API-Testing/blob/main/UnFollowPlaylist.png)


JavaScript Tests:

![Screenhot JavaScript Tests ](https://github.com/legendadr/API-Testing/blob/main/Java%20script%20test%20UnFollowPlaylist.png)



## Execution report for the created API collection

Below you can find the execution report that was generated through the Postman collection runner:

![Postman collection runner](https://github.com/legendadr/API-Testing/blob/main/test%20result%20postman%20spotify.png)

[Link collection runner postman](https://github.com/legendadr/API-Testing/blob/main/Spotify.postman_test_run.json)

The collection was also run through newman directly from the terminal, and the results can be found below:

![Newman collection](https://github.com/legendadr/API-Testing/blob/main/run%20collection%20with%20newman.png)

Retesting on the 11.03.2024:

![Newman collection](https://github.com/AdrianPricopie/API-Testing/blob/main/newman13.03.2024(2).png)


## Defects found

The following issues were identified while running the postman tests:

[Bug reports](https://github.com/legendadr/API-Testing/blob/main/APT-66.pdf).

## Conclusions

**Test Coverage:** A comprehensive set of 48 API tests was created, covering diverse functionalities in the Spotify Web API. Tests included various HTTP methods (GET, POST, PUT, DELETE) for thorough coverage.

**Test Execution:** Successful execution of the entire collection using both Postman's runner and Newman. Detailed execution reports were generated, providing insights into each test case's performance and status.

**Functionalities Covered:** Extensive testing of playlist operations, item management, artist information retrieval, and playlist following. A variety of scenarios, including positive, negative, and performance testing, were explored.

**Issues Identified:** Multiple defects were discovered and documented in bug reports. Addressing these issues is crucial before considering a production release to ensure a stable and reliable API.

**Lessons Learned:**
**Documentation Impact:** Clear documentation on creating access tokens was valuable for establishing a robust testing environment.
**Collaboration Significance:** Continuous collaboration with the development team is vital to align testing efforts with ongoing API changes, ensuring the testing process remains effective and relevant.







