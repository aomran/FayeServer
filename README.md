# Curri push server (Faye)

The way that HTTP works is that a UserAgent(e.g. web browser) makes a request to an AppServer, which responds with HTML or data like JSON. In order to add real-time features to our app we need almost the reverse to happen. We need the AppServer to say "hey data changed!" and the UserAgent just listens to some channel where these messages go out.

A third component (PushServer) is added to support this. When AppServer data changes, it publishes to the PushServer and UserAgents listen to PushServer channels for changes.

In development we run both PushServer and AppServer on the same machine. If we keep doing this in production and say use 2 AppServers to scale the app then things won't work as expected. There would be multiple PushServers.

Anyway tl;dr... PushServer should be on its own dedicated server. This repo is an "extraction" of the PushServer from the AppServer. 