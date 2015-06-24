# debian-dev-nginx: nginx container
FROM leny/debian-dev-base
MAINTAINER Pierre-Antoine "leny" Delnatte <info@flatland.be>

# install nginx
RUN apt-get update && apt-get -y install nginx-extras && apt-get clean && rm -rf /var/lib/apt/lists/*

# setup base config & host
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./default-host.conf /etc/nginx/sites-available/default

WORKDIR /var/www

EXPOSE 80

CMD ["nginx"]
