# Faye push server

The way that HTTP works is that a UserAgent(e.g. web browser) makes a request to an AppServer, which responds with HTML or data like JSON. In order to add real-time features to your app you need almost the reverse to happen. You need the AppServer to say "hey data changed!" and the UserAgent just listens to some channel where these messages go out.

A third component (PushServer) is added to support this. When AppServer data changes, it publishes to the PushServer and UserAgents listen to PushServer channels for changes.

In development you can run both PushServer and AppServer on the same machine. If you keep doing this in production and say use 2 AppServers to scale the app then things won't work as expected. There would be multiple PushServers.

Anyway tl;dr... PushServer should be on its own dedicated server. If you're using Ruby on Rails and the "PrivatePub" gem then this repo is all that you need.

1. Create a Heroku app and push this code to it.
2. Set an environment variable called `PUSH_SECRET` with `$ heroku config:set PUSH_SECRET="XXXXX". The secret is needed by the Rails application to securily connect to this PushServer.