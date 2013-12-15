# Faye push server for Curri

The way that HTTP works is that a client(e.g. web browser) makes a request and a server responds with HTML or data like JSON. In order to add real-time features to our app we need almost the reverse to happen. We need the server to say "hey data changed, here's what's changed" and the client(browser) just listens to some channel where these messages go out.

A third component (Faye) is added to support this. When server data changes, it publishes to Faye and clients listen to Faye channels for changes.

In development we run both Faye and Rails on the same machine. If we keep doing this in production and say use 2 servers to scale the app then things won't work as expected. There would be duplicate channels.

Anyway tl;dr... Faye needs its own dedicated server. This repo is an "extraction". 