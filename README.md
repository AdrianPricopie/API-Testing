# API-Testing

 ## Introduction

### API reference
The Spotify Web API provides a wide range of functionality for developers, including:
 Retrieve data from your favourite artist, album or show.
 Search for Spotify content.
 Control and interact with the playback, play and resume, Seek to a position or retrieve your queue.
 Manage your personal library, by creating a new playlist and adding your favourite tracks to it.
 Get recommendations based on the music you listen the most.
 And much more! You can find a complete list of available endpoints in the API Reference.

### Getting started
This is where the magic begins! The following steps will help you to get started with your journey towards creating some awesome music apps using the API:
 Log into the dashboard using your Spotify account.
 Create an app and select "Web API" for the question asking which APIs are you planning to use. Once you have created your app, you will have access to the app credentials. These will be required for API 
 authorization to obtain an access token.
 Use the access token in your API requests.
 You can follow the Getting started tutorial to learn how to make your first Web API call.

### Getting started with Web API
This tutorial will help you to make your first Web API call by retriving an artist's metadata. The steps to do so are the following:

Create an app, if you haven't done so.
Request an access token.
Use the access token to request the artist data.
Here we go, let's rock & roll!

Prerequisites
This tutorial assumes you have a Spotify account (free or premium).
We will use cURL to make API calls. You can install it from here our using the package manager of your choice.
Set Up Your Account
Login to the Spotify Developer Dashboard. If necessary, read the latest Developer Terms of Service to complete your account set up.

### Create an app

An app provides the Client ID and Client Secret needed to request an access token by implementing any of the authorization flows.
To create an app, go to your Dashboard, click on the Create an app button and enter the following information:

App Name: My App
App Description: This is my first Spotify app
Redirect URI: You won't need this parameter in this example, so let's use http://localhost:3000.
Finally, check the Developer Terms of Service checkbox and tap on the Create button.

### Request an access token

The access token is a string which contains the credentials and permissions that can be used to access a given resource (e.g artists, albums or tracks) or user's data (e.g your profile or your playlists).
In order to request the access token you need to get your Client_ID and Client Secret:

Go to the Dashboard
Click on the name of the app you have just created (My App)
Click on the Settings button
The Client ID can be found here. The Client Secret can be found behind the View client secret link.

With our credentials in hand, we are ready to request an access token. This tutorial uses the Client Credentials, so we must:
- Send a POST request to the token endpoint URI.
- Add the Content-Type header set to the application/x-www-form-urlencoded value.
- Add a HTTP body containing the Client ID and Client Secret, along with the grant_type parameter set to client_credentials.

        curl -X POST "https://accounts.spotify.com/api/token" \
       -H "Content-Type: application/x-www-form-urlencoded"
       -d "grant_type=client_credentials&client_id=your-client-id&client_secret=your-client-secret"


The response will return an access token valid for 1 hour:
  
    {"access_token": "BQDBKJ5eo5jxbtpWjVOj7ryS84khybFpP_lTqzV7uV-T_m0cTfwvdn5BnBSKPxKgEb11",
     "token_type": "Bearer",
      "expires_in": 3600}


### Request artist data

- For this example, we will use the Get Artist endpoint to request information about an artist. According to the API Reference, the endpoint needs the Spotify ID of the artist.
- An easy way to get the Spotify ID of an artist is using the Spotify Desktop App:

Search the artist
Click on the three dots icon from the artist profile
Select Share > Copy link to artist. The Spotify ID is the value that comes right after the open.spotify.com/artist URI.
Our API call must include the access token we have just generated using the Authorization header as follows:

    curl "https://api.spotify.com/v1/artists/4Z8W4fKeB5YxbusRsdQVPb" \
       -H "Authorization: Bearer  BQDBKJ5eo5jxbtpWjVOj7ryS84khybFpP_lTqzV7uV-T_m0cTfwvdn5BnBSKPxKgEb11"

If everything goes well, the API will return the following JSON response:

    {
    "external_urls": {
    "spotify": "https://open.spotify.com/artist/4Z8W4fKeB5YxbusRsdQVPb"
     },
     "followers": {
    "href": null,
    "total": 7625607
     },
     "genres": [
    "alternative rock",
    "art rock",
    "melancholia",
    "oxford indie",
    "permanent wave",
    "rock"
     ],
     "href": "https://api.spotify.com/v1/artists/4Z8W4fKeB5YxbusRsdQVPb",
     "id": "4Z8W4fKeB5YxbusRsdQVPb",
     "images": [
      {
       "height": 640,
      "url": "https://i.scdn.co/image/ab6761610000e5eba03696716c9ee605006047fd",
      "width": 640
      },
      {
      "height": 320,
      "url": "https://i.scdn.co/image/ab67616100005174a03696716c9ee605006047fd",
      "width": 320
      },
      {
      "height": 160,
      "url": "https://i.scdn.co/image/ab6761610000f178a03696716c9ee605006047fd",
      "width": 160
    }
     ],
    "name": "Radiohead",
    "popularity": 79,
    "type": "artist",
    "uri": "spotify:artist:4Z8W4fKeB5YxbusRsdQVPb"
     }

### Summary

The Spotify Web API provides different endpoints depending on the data we want to access. The API calls must include the Authorization header along with a valid access token.
This tutorial makes use of the client credentials grant type to retrieve the access token. That works fine in scenarios where you control the API call to Spotify, for example where your backend is connecting to the Web API. It will not work in cases where your app will connect on behalf of a specific user, for example when getting private playlist or profile data.

### What's next?

The tutorial used the Spotify Desktop App to retrieve the Spotify ID of the artist. The ID can also be retrieved using the Search endpoint. An interesting exercise would be to extend the example with a new API call to the /search endpoint. Do you accept the challenge?
The authorization guide provides detailed information about which authorization flow suits you best. Make sure you read it first!
You can continue your journey by reading the API calls guide which describes in detail the Web API request and responses.


