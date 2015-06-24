# debian-dev-nginx: nginx container
FROM leny/debian-dev-base

# install nginx
RUN apt-get update && apt-get -y install nginx && apt-get clean && rm -rf /var/lib/apt/lists/*

# setup base config & host
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./default-host.conf /etc/nginx/sites-available/default

WORKDIR /var/www

EXPOSE 80

CMD ["nginx"]
