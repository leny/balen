# debian-dev-mongodb: mongodb container
FROM leny/debian-dev-base
MAINTAINER Pierre-Antoine "leny" Delnatte <info@flatland.be>

# install
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10 && echo "deb http://repo.mongodb.org/apt/debian wheezy/mongodb-org/3.0 main" | tee /etc/apt/sources.list.d/mongodb-org-3.0.list && apt-get update && apt-get install -y mongodb-org && apt-get clean && rm -rf /var/lib/apt/lists/*

# Modify MongoDB config to access it from outside the container and create the data directory
RUN sed -i 's/bind_ip = 127.0.0.1/bind_ip = 0.0.0.0/g' /etc/mongod.conf && mkdir -p /data/db

# Define mountable directories.
VOLUME ["/data/db"]

# Expose MongoDB port
EXPOSE 27017

# Start MongoDB
CMD ["mongod"]
