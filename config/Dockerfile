FROM php:7.4.3-apache

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysqli
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git

COPY --from=composer /usr/bin/composer /usr/bin/composer

ADD ./sites-enabled/vhost.conf /etc/apache2/sites-available/

RUN a2enmod rewrite
RUN a2enmod ssl
RUN a2ensite vhost.conf
