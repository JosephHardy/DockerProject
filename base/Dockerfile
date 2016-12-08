FROM ubuntu:16.04
MAINTAINER JosephPaulHardy

# Update Ubuntu
RUN apt-get update

# Install wget
RUN apt-get install -y wget

# Install tar
RUN apt-get install -y tar

#Download Java Tarball
RUN wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz

# Extract tarball into /opt
RUN tar -zxf jdk-8u5-linux-x64.tar.gz -C /opt/

# Install Java and Javac
RUN update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_05/bin/java 100
RUN update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_05/bin/javac 100


# Install apache
RUN apt-get install -y apache2

# Automate MySQL Installation
RUN echo "mysql-server mysql-server/root_password password rootpass" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password rootpass" | debconf-set-selections

# Install MySQL
RUN apt-get install -y mysql-server

# Install PHP
RUN apt-get install php7.0 php7.0-cli php7.0-common php7.0-mysql libapache2-mod-php7.0 php7.0-cgi php7.0-xmlreader php7.0-xmlwriter php7.0-bcmath php7.0-mbstring -y
