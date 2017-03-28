FROM debian:testing

MAINTAINER Javier Ocampo version 1.3

# Install apache, php and libraries needed.
RUN apt-get update && \
    apt-get install -y \
        apache2 \
        php \
        php-mysql \
        php-mcrypt \
        php-curl \
        php-gd \
        php-mbstring \
        php-xml \
        php-zip \
        libapache2-mod-php

# Install some utils
RUN apt-get install -y \
        curl \
        vim \
        supervisor \
        zip \
        unzip

RUN \
    # Install composer
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Enable apache mods
RUN a2enmod rewrite

# Expose apache
EXPOSE 80

# Update the default apache site with the config we created.
ADD apache.conf /etc/apache2/sites-enabled/000-default.conf

RUN service apache2 restart

CMD /usr/sbin/apache2ctl -D FOREGROUND
