FROM debian:testing

MAINTAINER Javier Ocampo version 1.2

# Install apache, php and libraries needed.
RUN apt-get update && \
    apt-get install -y \
        nginx \
        curl \
        vim \
        php \
        php-fpm \
        php-mysql \
        php-mcrypt \
        php-curl \
        php-gd \
        php-mbstring \
        php-xml && \

    rm -rf /var/lib/apt/lists/* && \
    echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
    chown -R www-data:www-data /var/lib/nginx

# Install some utils
RUN \
    # Install composer
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \

    # Install drush
    php -r "readfile('https://s3.amazonaws.com/files.drush.org/drush.phar');" > /usr/local/bin/drush && \
    chmod +x /usr/local/bin/drush


EXPOSE 80 443

# Update the default apache site with the config we created.
ADD nginx.conf /etc/nginx/sites-enabled/default

CMD ["nginx"]
