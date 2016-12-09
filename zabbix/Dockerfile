FROM base
MAINTAINER JosephPaulHardy

# Download Zabbix
WORKDIR /opt/
RUN wget http://repo.zabbix.com/zabbix/3.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.0-1+xenial_all.deb
RUN dpkg -i zabbix-release_3.0-1+xenial_all.deb
RUN apt-get update

# Install Zabbix Frontend
RUN apt-get install -y zabbix-server-mysql zabbix-frontend-php

# Create MySQL user and set privileges
RUN service mysql start \
&& echo "CREATE USER zabbix" | mysql -uroot -prootpass\
&& echo "CREATE DATABASE zabbixdb CHARACTER SET utf8 COLLATE utf8_bin;" | mysql -uroot -prootpass\
&& echo "GRANT ALL ON zabbixdb.* TO zabbix@localhost IDENTIFIED BY 'zpass';" | mysql -uroot -prootpass\
&& echo "FLUSH PRIVILEGES;" | mysql -uroot -prootpass

# Import schema and data
WORKDIR /usr/share/doc/zabbix-server-mysql
RUN service mysql start && zcat create.sql.gz | mysql zabbixdb -u zabbix -pzpass

# Restart apache and zabbix
RUN service zabbix-server start && service apache2 restart

# Add configuration details
RUN sed -i '82 i DBHost=localhost' /etc/zabbix/zabbix_server.conf
RUN sed -i '92 c DBName=zabbixdb' /etc/zabbix/zabbix_server.conf
RUN sed -i '108 c DBUser=zabbix' /etc/zabbix/zabbix_server.conf
RUN sed -i '118 i DBPassword=zpass' /etc/zabbix/zabbix_server.conf

# Set PHP timezone
RUN sed -i '912 c date.timezone="Europe/London"' /etc/php/7.0/apache2/php.ini

# Start zabbix
RUN service apache2 restart && service zabbix-server restart
ENTRYPOINT service apache2 start && service mysql start && service zabbix-server start && bash
