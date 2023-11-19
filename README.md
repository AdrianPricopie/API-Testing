
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

##  How was created the token
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

- Open [Postman](https://www.postman.com/) and create a new collection named "Spotify."
- Within the collection, create a new POST request.
- Click on authorization and select from the dropdown type OAuth 2.0.
- In the Callback URL field, enter the Redirect URIs from the first steps. If you are using the Postman web app, you don't need to set it.
- Copy the Client ID and Client Secret from your application and paste them into Postman.
- Treat these links as variables; assign them names and set them as global variables instead of using the actual links.
- In the Access Token URL field, enter the link `https://accounts.spotify.com/api/token`. After that, put the link `https://accounts.spotify.com/authorize` in the Auth URL field, and enter the text "playlist-modify-public playlist-read-private playlist-modify-private" in the Scope field.
- Finally, press "Get New Access Token". The token has been created.












 

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


#### GET Requests:

1. Retrieve information about an artist:
Request:
GET  
Endpoint:https://api.spotify.com/v1/artists/{id}

 - Parameters:
   artist_id: The unique identifier of the artist.
 - Response:
   Successful response: 200 OK
 - Example response body json:


       {
       "external_urls": {
       "spotify": "string"
       },
       "followers": {
       "href": "string",
       "total": 0
        },
       "genres": ["Prog rock", "Grunge"],
       "href": "string",
       "id": "string",
       "images": [
       {
        "url": "https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228",
        "height": 300,
        "width": 300
       }
       ],
       "name": "string",
       "popularity": 0,
       "type": "artist",
         "uri": "string"
        }
Message:
Successfully retrieved information about the artist.

#### GET Requests:
Retrieve information about a playlist:
Request:
GET
Endpoint:https://api.spotify.com/v1/playlists/{playlist_id}
Parameters:
 - playlist_id: The unique identifier of the playlist.
Response:
 - Successful response: 200 OK
Example response body json:
 
Copy code:

     {
    "collaborative": false,
    "description": "string",
    "external_urls": {
    "spotify": "string"
    },
    "followers": {
    "href": "string",
    "total": 0
    },
    "href": "string",
    "id": "string",
    "images": [
    {
      "url": "https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228",
      "height": 300,
      "width": 300
    }
    ],
    "name": "string",
    "owner": {
    "external_urls": {
      "spotify": "string"
    },
    "followers": {
      "href": "string",
      "total": 0
    },
    "href": "string",
    "id": "string",
    "type": "user",
    "uri": "string",
    "display_name": "string"
    },
    "public": false,
    "snapshot_id": "string",
    "tracks": {
    "href": "https://api.spotify.com/v1/me/shows?offset=0&limit=20",
    "limit": 20,
    "next": "https://api.spotify.com/v1/me/shows?offset=1&limit=1",
    "offset": 0,
    "previous": "https://api.spotify.com/v1/me/shows?offset=1&limit=1",
    "total": 4,
    "items": [
      {
        "added_at": "string",
        "added_by": {
          "external_urls": {
            "spotify": "string"
          },
          "followers": {
            "href": "string",
            "total": 0
          },
          "href": "string",
          "id": "string",
          "type": "user",
          "uri": "string"
        },
        "is_local": false,
        "track": {
          "album": {
            "album_type": "compilation",
            "total_tracks": 9,
            "available_markets": ["CA", "BR", "IT"],
            "external_urls": {
              "spotify": "string"
            },
            "href": "string",
            "id": "2up3OPMp9Tb4dAKM2erWXQ",
            "images": [
              {
                "url": "https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228",
                "height": 300,
                "width": 300
              }
            ],
            "name": "string",
            "release_date": "1981-12",
            "release_date_precision": "year",
            "restrictions": {
              "reason": "market"
            },
            "type": "album",
            "uri": "spotify:album:2up3OPMp9Tb4dAKM2erWXQ",
            "artists": [
              {
                "external_urls": {
                  "spotify": "string"
                },
                "href": "string",
                "id": "string",
                "name": "string",
                "type": "artist",
                "uri": "string"
              }
            ]
          },
          "artists": [
            {
              "external_urls": {
                "spotify": "string"
              },
              "followers": {
                "href": "string",
                "total": 0
              },
              "genres": ["Prog rock", "Grunge"],
              "href": "string",
              "id": "string",
              "images": [
                {
                  "url": "https://i.scdn.co/image/ab67616d00001e02ff9ca10b55ce82ae553c8228",
                  "height": 300,
                  "width": 300
                }
              ],
              "name": "string",
              "popularity": 0,
              "type": "artist",
              "uri": "string"
            }
          ],
          "available_markets": ["string"],
          "disc_number": 0,
          "duration_ms": 0,
          "explicit": false,
          "external_ids": {
            "isrc": "string",
            "ean": "string",
            "upc": "string"
          },
          "external_urls": {
            "spotify": "string"
          },
          "href": "string",
          "id": "string",
          "is_playable": false,
          "linked_from": {
          },
          "restrictions": {
            "reason": "string"
          },
          "name": "string",
          "popularity": 0,
          "preview_url": "string",
          "track_number": 0,
          "type": "track",
          "uri": "string",
          "is_local": false
        }
      }
    ]
     },
    "type": "string",
    "uri": "string"
    }

Message:
Successfully retrieved information about the playlist.


