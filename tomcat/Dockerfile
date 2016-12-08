FROM base
MAINTAINER JosephPaulHardy

# Create Tomcat user
RUN groupadd tomcat
RUN useradd -s /bin/false -g tomcat -d /opt/apache-tomcat-8.5.8 tomcat

# Download Tomcat Tarball
WORKDIR /opt
RUN wget http://mirrors.ukfast.co.uk/sites/ftp.apache.org/tomcat/tomcat-8/v8.5.8/bin/apache-tomcat-8.5.8.tar.gz

RUN tar xzvf apache-tomcat-8.5.8.tar.gz
RUN chgrp -R tomcat /opt/apache-tomcat-8.5.8

RUN chmod -R g+rx apache-tomcat-8.5.8

WORKDIR /opt/apache-tomcat-8.5.8/bin

RUN chmod a+x startup.sh
ENTRYPOINT ./startup.sh && bash


