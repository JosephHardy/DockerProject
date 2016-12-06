FROM java
MAINTAINER JosephPaulHardy

WORKDIR /opt/
RUN wget https://www.sonatype.com/oss-thank-you-tar.gz
RUN tar zxvf nexus-3.1.0-04-unix.tar.gz

WORKDIR /opt/nexus-3.1.0-04/bin
RUN ./nexus run &
