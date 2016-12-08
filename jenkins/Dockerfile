FROM base
MAINTAINER JosephPaulHardy

# Download Jenkins
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | apt-key add -
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

# Install Jenkins
RUN apt-get update -y
RUN apt-get install -y jenkins

# Run Jenkins
CMD service jenkins start && bash
