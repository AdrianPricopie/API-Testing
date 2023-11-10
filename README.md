
## Introduction

### API reference
The Spotify Web API provides a wide range of functionality for developers, including:
 Retrieve data from your favourite artist, album or show.
 Search for Spotify content.
 Control and interact with the playback, play and resume, Seek to a position or retrieve your queue.
 Manage your personal library, by creating a new playlist and adding your favourite tracks to it.
 Get recommendations based on the music you listen the most.
 And much more! You can find a complete list of available endpoints in the API Reference.
 For more details about documentation ,visit this website https://developer.spotify.com/documentation/web-api/tutorials/getting-started.

### Token creation

First steps:
Go to spotify.com and create a new user account.
Access the dashboard and log in with the user account you created.
Click on the "Create an app" button.
Enter a name and description for the new aplication created.
Accept the terms and conditions and click on the create button.
In the opened window, click on "Edit Settings."
In the Redirect URIs textbox, enter a link. It doesn't have to be specific, but one that can be used later. Example: http://applicationcourse/callback.
Click on the SAVE button at the bottom.
second steps:
Open Postman and create a new collection named "Spotify."
Within the collection, create a new POST request
Click on authorization and select from  dropbow type OAuth2.0
In Callback URL field put Redirect URIs from frist steps,if you using  postman web app you don't need to set it.
Copy client ID and Client secret from your application and put in postman 
We will use these links only as variables, so we will give them names and set them as global variables instead of links.
in Acces Token URL field put this link https://accounts.spotify.com/api/token





 

### types available for testing

In this section, you can explore and perform tests on various types of operations supported by the Spotify Web API. Some examples include:

- GET Requests: Retrieve information about artists, albums, playlists, etc.
- POST Requests: Create new playlists, add tracks, etc.
- PUT and PATCH Requests: Update existing data, modify playlists, etc.
- DELETE Requests: Remove playlists, tracks, etc.


### Tests used for validation

In this section, the following tests were conducted to validate the functionality and reliability of the Spotify Web API:

GET Requests:

Tested the ability to retrieve information about favorite artists, albums, playlists, etc. Verified the correctness of the data returned.

POST Requests:

Conducted tests to create new playlists and add tracks to them. Ensured that the creation process and addition of tracks function as expected.

PUT and PATCH Requests:

Verified the capability to update existing data, including modifying playlists. Checked if the modifications were applied accurately.
DELETE Requests:

Tested the removal of playlists, tracks, etc., using the DELETE request. Ensured that the deletion process was successful and reflected the desired changes.


### requests with params and respons together with message 
