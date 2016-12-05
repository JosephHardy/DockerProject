# Jenkins Dockerfile

FROM ubuntu:latest
MAINTAINER JosephPaulHardy

# Update ubuntu
RUN apt-get update
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
RUN apt-get update
RUN apt-get install -y jenkins
