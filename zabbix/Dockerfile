FROM ubuntu:16.04
MAINTAINER JosephPaulHardy

# Update Ubuntu
RUN apt-get update

# Install apache
RUN apt-get install -y apache2

# Automate MySQL Installation
RUN echo "mysql-server mysql-server/root_password password rootpass" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password rootpass" | debconf-set-selections

# Install MySQL
RUN apt-get install -y mysql-server

# Download Zabbix
WORKDIR /opt/
RUN wget http://repo.zabbix.com/zabbix/3.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.0-1+xenial_all.deb
RUN dpkg -i zabbix-release_3.0-1+xenial_all.deb
RUN apt-get update

# Install Zabbix Frontend
RUN apt-get install zabbix-server-mysql zabbix-frontend-php

RUN service mysql-server start \
&& echo "CREATE DATABASE zabbix CHARACTER SET utf8 COLLATE utf8_bin;" | mysql -uroot -prootpass\
&& echo "GRANT ALL PRIVILEGES ON zabbix.* TO zabbix@localhost IDENTIFIED BY 'rootpass';" | mysql -uroot -prootpass\
&& echo "FLUSH ALL PRIVILEGES ON zabbix.*;" | mysql -uroot -prootpass

RUN zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uroot -p rootpass

RUN service zabbix-server start
RUN service apache2 restart
