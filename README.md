docker-nginx
============
NGINX is a popular lightweight web application that is used for developing server-side applications. It is an open-source web server that is developed to run on a variety of operating systems. Since nginx is a popular web server for development, Docker has ensured that it has support for nginx.

A simple Nginx image for Docker to serve static websites. It will serve anything in the directory `/var/www`.

You'll need to use a `Dockerfile` to build an image with your site in it. For example, if your site is in a directory called `src/`, you could create this `Dockerfile`:

    FROM orchardup/nginx
    ADD src/ /var/www
    CMD 'nginx'

Then build and run it:

    $ docker build -t mysite .
    ...
    Successfully built 5ae2fb5cf4f8
    $ docker run -p 80:80 -d mysite
    da809981545f
    $ curl localhost
    ...

SSL
---

To use SSL, put your certs in `/etc/nginx/ssl` and enable the `default-ssl` site:

    ADD server.crt /etc/nginx/ssl/
    ADD server.key /etc/nginx/ssl/
    RUN ln -s /etc/nginx/sites-available/default-ssl /etc/nginx/sites-enabled/default-ssl


