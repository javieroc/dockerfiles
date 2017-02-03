FROM debian:testing

MAINTAINER Javier Ocampo version 1.0

# Install apache, php and libraries needed.
RUN apt-get update && \
    apt-get install -y apache2 && \
    apt-get install -y php-mysql && \
    apt-get install -y php libapache2-mod-php php-mcrypt

# Enable apache mods
RUN a2enmod rewrite

# Expose apache
EXPOSE 80

# Update the default apache site with the config we created.
ADD apache.conf /etc/apache2/sites-enabled/000-default.conf

RUN service apache2 restart

CMD /usr/sbin/apache2ctl -D FOREGROUND
