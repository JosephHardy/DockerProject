FROM base
MAINTAINER JosephPaulHardy

# Create Tomcat user
RUN groupadd tomcat
RUN useradd -s /bin/false -g tomcat -d /opt/apache-tomcat-8.5.8 tomcat

# Download Tomcat Tarball
WORKDIR /opt
RUN wget http://mirrors.ukfast.co.uk/sites/ftp.apache.org/tomcat/tomcat-8/v8.5.8/bin/apache-tomcat-8.5.8.tar.gz

# Extract Tarball
RUN tar xzvf apache-tomcat-8.5.8.tar.gz

# Allow tomcat user permissions
RUN chgrp -R tomcat /opt/apache-tomcat-8.5.8
RUN chmod -R g+rx apache-tomcat-8.5.8

WORKDIR /opt/apache-tomcat-8.5.8/bin

# Convert startup into executable
RUN chmod a+x startup.sh

# Adding users and roles to tomcat-users.xml
RUN sed -i '44 i <user username="admin" password="password" roles="manager-gui,admin-gui"/>' /opt/apache-tomcat-8.5.8/conf/tomcat-users.xml
RUN sed -i '44 i <role rolename="manager-gui"/>' /opt/apache-tomcat-8.5.8/conf/tomcat-users.xml
RUN sed -i '44 i <role rolename="admin-gui"/>' /opt/apache-tomcat-8.5.8/conf/tomcat-users.xml

# Allowing access from outside container
RUN sed -i '113 i <Connector port="9009" protocol="AJP\/1\.3" redirectPort="9443" address="164\.39\.75\.108" useIPVHosts="true" \/>' /opt/apache-tomcat-8.5.8/conf/server.xml
RUN sed -i '20s/allow="/allow="164\\\.39\\\.75\\\.108|/' /opt/apache-tomcat-8.5.8/webapps/manager/META-INF/context.xml
RUN sed -i '20s/allow="/allow="164\\\.39\\\.75\\\.108|/' /opt/apache-tomcat-8.5.8/webapps/host-manager/META-INF/context.xml

ENTRYPOINT ./startup.sh && bash


