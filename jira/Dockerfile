FROM base
MAINTAINER JosephPaulHardy

WORKDIR /opt/
RUN wget https://downloads.atlassian.com/software/jira/downloads/atlassian-jira-software-7.2.3-x64.bin
RUN chmod 755 atlassian-jira-software-7.2.3-x64.bin
RUN printf "o\n2\n/opt/atlassian/jira\n/var/atlassian/application-data/jira\n2\n8081\n8006\ny\ni\nn\n" | ./atlassian-jira-software-7.2.3-x64.bin
CMD service jira start && bash
