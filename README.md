# tenfourty.com
The source for http://www.tenfourty.com/

This is a hugo site, hosted on and automatically built by Netlify.

To create a new post:
> $ hugo -s site new post/good-to-great.md

To run this site locally:
> $ docker-compose up

Or to build the image run:
> $ docker build -t tenfourty/tenfourty-com .

And then to run it as a daemon run:
> $ docker run -d -p 1313:1313 -v [path to this dir]/site/:/site tenfourty/tenfourty-com
