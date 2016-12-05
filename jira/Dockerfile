FROM java
MAINTAINER JosephPaulHardy

WORKDIR /opt/
RUN wget https://downloads.atlassian.com/software/jira/downloads/atlassian-jira-software-7.2.3-x64.bin
RUN chmod 755 jira.bin
RUN printf "o\n2\n/opt/atlassian/jira\n/var/atlassian/application-data/jira\n2\n8081\n8006\ny\n" | ./jira.bin'
