## Archived - I've moved my hosting over to Ghost.org to take advantage of some of it's features as I pivot this website.

# jeremybrown.tech
The source for https://www.jeremybrown.tech/

This is a hugo site, hosted on and automatically built by Netlify.

To create a new post:
> $ docker-compose run --rm jeremybrown.tech hugo new post/good-to-great.md

To run this site locally:
> $ docker-compose up

The site will be available at http://localhost:1313

To run a similar setup to production locally (nginx) run the following command - **Note: live reload won't work with this option**:
> $ docker-compose -f docker-compose-dev-nginx.yml up

The site will be available at http://localhost:1313/

Or to build the image run:
> $ docker build -t tenfourty/jeremybrown.tech .

And then to run it as a daemon run:
> $ docker run -d -p 1313:1313 -v [path to this dir]/site/:/site -name jeremybrown.tech tenfourty/jeremybrown.tech
