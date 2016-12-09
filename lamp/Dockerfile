FROM ubuntu:16.04
MAINTAINER JosephPaulHardy

# Update Ubuntu
RUN apt-get update

# Install wget
RUN apt-get install -y wget

# Install apache
RUN apt-get install -y apache2

# Automate MySQL Installation
RUN echo "mysql-server mysql-server/root_password password rootpass" | debconf-$
RUN echo "mysql-server mysql-server/root_password_again password rootpass" | de$

# Install MySQL
RUN apt-get install -y mysql-server

# Install PHP
RUN apt-get install php7.0 php7.0-cli php7.0-common php7.0-mysql libapache2-mod$
