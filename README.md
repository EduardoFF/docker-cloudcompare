# CloudCompare on Docker

[CloudCompare] in a container...just to play around.


## How to
To run CC container & host must communicate X11 (Linux X window system) info, and so we need to run our container accordingly.
There is a small tool to help us doing it that works pretty smooth for Linux and MacOS hosts -- never tested in Windows; looking for testers actually :) -- the tool is called [dockeri] and should be strightforward to have it running CC:

```
$ dockeri -w /path/to/data/ chbrandt/cloudcompare
```
This will mount your host `/path/to/data` directory into container's `/work`.


### I like it ugly
If you are into pure `docker` command line, you should do something along the line (Linux host example):
```
$ docker run --rm -it -v /path/to/data:/work -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix:0 chbrant/cloudcompare
```

[CloudCompare]: http://www.cloudcompare.org/
[dockeri]: https://github.com/chbrandt/dockeri

/.\
