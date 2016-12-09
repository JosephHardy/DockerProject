FROM base
MAINTAINER JosephPaulHardy

# Download Maven
RUN wget http://mirrors.ukfast.co.uk/sites/ftp.apache.org/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
RUN tar -zxf apache-maven-3.3.9-bin.tar.gz -C /opt/
RUN update-alternatives --install /usr/bin/mvn mvn /opt/apache-maven-3.3.9/bin/mvn 100

# Download Jenkins
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | apt-key add -
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

# Install Jenkins
RUN apt-get update -y
RUN apt-get install -y jenkins

# Run Jenkins
CMD service jenkins start && bash
