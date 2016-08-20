# Docker Nginx Rtmp Stream Service
Dockerfile(s) and scripts to create a simplistic stream service using Nginx Rtmp and ffmpeg.

Current projected features:
- Standard Nginx Rtmp server to provide custom streams
- Simple player page based on [hls.js](https://github.com/dailymotion/hls.js) (most likely copy/pasting a basic example with the right stream url)
- Stream re-encoding and auto pushing to external services (such as [Twitch](https://twitch.tv))
- Multi-source stream using the redirection controls based on [this blog post](http://nginx-rtmp.blogspot.de/2014/01/redirecting-streams-in-version-111.html), sourcing from videos and past broadcasts.
- Python Flask + Javascript framework to be determined app to create an interactive page to control both of the above (running/stopping the stream, chosing the source from a dynamic list), possibly including the above HLS player. 
  Configuration based on [this example](https://hub.docker.com/r/p0bailey/docker-flask/).

Additional considered features:
- Authentication system for both publishers and subscribers as demonstrated [here](https://github.com/Nesseref/nginx-rtmp-auth)
- Load balancer and proxy containers based on [this](https://github.com/deluxor/nodejs-nginx-rtmp-balancer), and included in the simple player page.
