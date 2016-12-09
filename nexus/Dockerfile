FROM base
MAINTAINER JosephPaulHardy

# Download and unzip Nexus tarball
WORKDIR /opt/
RUN wget http://download.sonatype.com/nexus/3/latest-unix.tar.gz
RUN tar zxvf latest-unix.tar.gz

# Run Nexus as service
WORKDIR /opt/nexus-3.1.0-04/bin
RUN ./nexus run &
CMD ./nexus start && bash
