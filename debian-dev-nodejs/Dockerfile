# debian-dev-nodejs: node.js container
FROM leny/debian-dev-base
MAINTAINER Pierre-Antoine "leny" Delnatte <info@flatland.be>

# Install basic packages.
RUN curl -sL https://deb.nodesource.com/setup_0.12 | bash - && apt-get update && apt-get -y install nodejs && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/www

# Install npm packages globally with user dev
RUN npm install -g n
RUN n stable
RUN npm install -g grunt-cli
RUN npm install -g gulp
RUN npm install -g supervisor
RUN npm install -g node-inspector --unsafe-perm

WORKDIR /var/www

CMD ["node"]
