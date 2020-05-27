This requires Rocker https://github.com/osrf/rocker to enable OpenGL support and simplify the running. 
See more detailed instructions from the homepage.

Running:

rocker --devices /dev/dri/card0 --x11 --user --home  --pulse nameofthis /tmp/gerbil/bin/qgerbil 

Building:
docker build -t nameofthis .

