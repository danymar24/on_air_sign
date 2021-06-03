On Air Sign
===========

Automated on air status sign with zoom status using Node Red

### About

The flow receives a post request from a zoom application, then it verifies the presence status and sends a request to a wled powered on air sign to set the color.

### Status

The flow sets 3 status

* Available: Status "Available" - Sets the on air sign to Green
* Busy: Status "In_Meeting, Do_Not_Disturb" - Sets the on air sign to Red and stop Spotify
* Away: Status "Away" - Sets the on air sign to off

### NodeRed configuration

* Install node red and import the project
* Expose the node red machine to the internet with a static ip (In my case I use a raspberry pi zero w)

### Zoom configuration

Follow the next steps to configure Zoom and the flow:
* Create a zoom app following this [link](https://marketplace.zoom.us/docs/guides/build/jwt-app)
* In App features add the url of the machine with node red (in my case I use: http://x.x.x.x:1880/onairsign)
* add an event subscription with the event type "user activity">"User's presence status"
* In node red change the ip of the "On Air Sign" request node for the ip address of the wled sign
* Deploy

### Spotify configuration

Follow the next steps to configure Spotify and the flow:
* Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/applications)
* Create a new application giving the nave and description
* Go to Edit Settings and add a Redirect URI with the exposed ip address in the format http://x.x.x.x:1880/spotify-credentials/auth/callback and save
* Add the Client ID and Client Secret in the spotify node
* Add the "user-modify-playback-state" in the scopes section
* Press Start Authentication and follow the access.
