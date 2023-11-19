
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












 

### Types available for testing

HTTP methods supported by this API are GET, POST, PUT, PATCH and DELETE.
 In this section, you can explore and perform tests on various types of operations supported by the Spotify Web API. Some examples include:

- GET Requests: Retrieve information about artists, albums, playlists, etc.
- POST Requests: Create new playlists, add tracks, etc.
- PUT and PATCH Requests: Update existing data, modify playlists, etc.
- DELETE Requests: Remove playlists, tracks, etc.


### Tests used for validation

for this API  autenthication token is needed
 #### I send responses to some endpoints:
- https://api.spotify.com/v1/users/{user_id}/playlists (Create playlist)
- https://api.spotify.com/v1/playlists/{playlist_id}/tracks (Add Item to playlist)
- https://api.spotify.com/v1/playlists/{playlist_id}/tracks (Update Item to playlist)
- https://api.spotify.com/v1/playlists/{playlist_id} (Get playlist)
- https://api.spotify.com/v1/playlists/{playlist_id}/tracks (Remove playlistItem)
- https://api.spotify.com/v1/playlists/{playlist_id} (Change playlist details)
- https://api.spotify.com/v1/playlists/{playlist_id}/tracks (Add item in playlist)
- https://api.spotify.com/v1/playlists/{playlist_id}/followers (Follow playlist)
- using all available HTTP methods
- the expected HTTP responses are received together with the HTTP messages following the requests (200, 201, 204 and 404).
- I wrote test-cases through which I validated the answer coming from the available templates that Postman offers.

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
   
 -Example response body json:
 
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

#### POST Requests:
Create a new playlist:
 - Request body:
 
        {
       "name": "New Playlist",
       "description": "New playlist description",
       "public": false
        }

POST
Endpoint:
https://api.spotify.com/v1/users/{user_id}/playlists
Parameters
 - user_id: The unique identifier of the user creating the playlist.
#### Response:
 - Successful response: 201 Created
 - Example response body json:
   
    
        {
       "collaborative": false,
       "description": "Noua descriere",
       "external_urls": {
        "spotify": "https://open.spotify.com/playlist/0bRMJdlcZYQxmNGXWdKHFC"
        },
        "followers": {
        "href": null,
        "total": 0
       },
       "href": "https://api.spotify.com/v1/playlists/0bRMJdlcZYQxmNGXWdKHFC",
       "id": "0bRMJdlcZYQxmNGXWdKHFC",
       "images": [],
       "name": "New playlist",
       "owner": {
        "display_name": "Adrian Pricopie",
        "external_urls": {
            "spotify": "https://open.spotify.com/user/31klgihdqmygxigfetdciouflnfu"
        },
        "href": "https://api.spotify.com/v1/users/31klgihdqmygxigfetdciouflnfu",
        "id": "31klgihdqmygxigfetdciouflnfu",
        "type": "user",
        "uri": "spotify:user:31klgihdqmygxigfetdciouflnfu"
       },
       "primary_color": null,
       "public": false,
       "snapshot_id": "MSxkYzg3ZjExYTBlOWY3YWY2MjJjN2U2OTJhZDg5NjJlMzU5MDQ2NjM4",
       "tracks": {
        "href": "https://api.spotify.com/v1/playlists/0bRMJdlcZYQxmNGXWdKHFC/tracks",
        "items": [],
        "limit": 100,
        "next": null,
        "offset": 0,
        "previous": null,
        "total": 0
        },
       "type": "playlist",
       "uri": "spotify:playlist:0bRMJdlcZYQxmNGXWdKHFC"
       }




