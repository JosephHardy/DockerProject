FROM base
MAINTAINER JosephPaulHardy

# Install Postfix
RUN echo "postfix postfix/mailname string localhost" | debconf-set-selections
RUN echo "postfix postfix/main_mailer_type string 'Internet Site'" | debconf-set-selections

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y postfix
