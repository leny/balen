# debian-dev-base: debian base machine for dev purposes
# base image: debian (wheezy)
FROM debian:wheezy

# basic tools
RUN apt-get update && apt-get install -y software-properties-common python-software-properties curl wget git htop unzip vim telnet nano make build-essential g++ && apt-get clean && rm -rf /var/lib/apt/lists/*

# bash config & settings
COPY ./bashrc /root/tmp_bashrc
RUN cat /root/tmp_bashrc >> ~/.bashrc
RUN rm /root/tmp_bashrc
