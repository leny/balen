# debian-dev-mariadb: mariadb container
FROM leny/debian-dev-base
MAINTAINER Pierre-Antoine "leny" Delnatte <info@flatland.be>

# install
RUN apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xcbcb082a1bb943db
RUN add-apt-repository 'deb http://mariadb.mirror.nucleus.be//repo/5.5/debian wheezy main'
RUN apt-get update && apt-get -y install mariadb-server && apt-get clean && rm -rf /var/lib/apt/lists/*

# Modify mariadb config to access it from outside the container
RUN sed -i 's/^\(bind-address\s.*\)/# \1/' /etc/mysql/my.cnf

# Allow root user to connect from anywhere
RUN service mysql start && mysqladmin --silent --wait=30 ping && mysql -e 'GRANT ALL PRIVILEGES ON *.* TO "root"@"%" WITH GRANT OPTION;'

# Create the default command for the container
# It allows to rebuild a database if /var/lib/mysql is empty
# Useful when using a volume with "docker run -v /path/on/host:/var/lib/mysql"
COPY ./start-service /usr/local/bin/start-service
RUN chmod +x /usr/local/bin/start-service

# Define mountable directories
VOLUME ["/var/lib/mysql"]

# Expose mysql port
EXPOSE 3306

CMD ["start-service"]
