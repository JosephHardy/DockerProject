FROM ubuntu:16.04
MAINTAINER JosephPaulHardy

# Update Ubuntu
RUN apt-get update

# Install wget
RUN apt-get install -y wget

# Install apache
RUN apt-get install -y apache2

# Automate MySQL Installation
RUN echo "mysql-server mysql-server/root_password password rootpass" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password rootpass" | debconf-set-selections

# Install MySQL
RUN apt-get install -y mysql-server

# Install PHP
RUN apt-get install php7.0 php7.0-cli php7.0-common php7.0-mysql libapache2-mod-php7.0 php7.0-cgi php7.0-xmlreader php7.0-xmlwriter php7.0-bcmath php7.0-mbstring -y

# Download Zabbix
WORKDIR /opt/
RUN wget http://repo.zabbix.com/zabbix/3.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.0-1+xenial_all.deb
RUN dpkg -i zabbix-release_3.0-1+xenial_all.deb
RUN apt-get update

# Install Zabbix Frontend
RUN apt-get install -y zabbix-server-mysql zabbix-frontend-php

RUN service mysql start \
&& echo "CREATE USER zabbix" | mysql -uroot -prootpass\
&& echo "CREATE DATABASE zabbixdb CHARACTER SET utf8 COLLATE utf8_bin;" | mysql -uroot -prootpass\
&& echo "GRANT ALL ON zabbixdb.* TO zabbix@localhost IDENTIFIED BY 'zpass';" | mysql -uroot -prootpass\
&& echo "FLUSH PRIVILEGES;" | mysql -uroot -prootpass

WORKDIR /usr/share/doc/zabbix-server-mysql
RUN service mysql start && zcat create.sql.gz | mysql zabbixdb -u zabbix -pzpass

RUN service zabbix-server start && service apache2 restart

RUN sed -i '82 i DBHost=localhost' /etc/zabbix/zabbix_server.conf
RUN sed -i '92 c DBName=zabbixdb' /etc/zabbix/zabbix_server.conf
RUN sed -i '108 c DBUser=zabbix' /etc/zabbix/zabbix_server.conf
RUN sed -i '118 i DBPassword=zpass' /etc/zabbix/zabbix_server.conf

RUN sed -i '912 c date.timezone="Europe/London"' /etc/php/7.0/apache2/php.ini

RUN service apache2 restart && service zabbix-server restart
RUN cat -n /etc/php/7.0/apache2/php.ini
ENTRYPOINT service apache2 start && service mysql start && service zabbix-server start && bash
