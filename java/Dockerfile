FROM ubuntu:latest
MAINTAINER JosephPaulHardy

# Update ubuntu
RUN apt-get update

# Install wget
RUN apt-get install -y wget
RUN apt-get install -y tar

#Download Java Tarball
RUN wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz

# Extract tarball into /opt
RUN tar -zxf jdk-8u5-linux-x64.tar.gz -C /opt/

# Install Java and Javac
RUN update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_05/bin/java 100
RUN update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_05/bin/javac 100
