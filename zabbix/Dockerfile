FROM ubuntu:latest
MAINTAINER JosephPaulHardy

# Update Ubuntu
RUN apt-get update

# Automate MySQL Installation
RUN echo "mysql-server-5.6 mysql-server/root_password password rootpass" | debconf-set-selections
RUN echo "mysql-server-5.6 mysql-server/root_password_again password rootpass" | debconf-set-selections

# Install MySQL
RUN apt-get install mysql-server-5.6
