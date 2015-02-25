FROM php:5.6-fpm

RUN echo "date.timezone = Europe/Paris" >> /usr/local/etc/php/php.ini

RUN apt-get clean
RUN apt-get update
RUN apt-get -y install sudo php5-mysql

# Required by Symfony

## Disable Short Open Tag
RUN echo "short_open_tag = Off" >> /usr/local/etc/php/php.ini

## APC
RUN apt-get -qqy install php-apc
RUN echo "extension=/usr/lib/php5/20131226/apcu.so" >> /usr/local/etc/php/php.ini

## INTL / MB_STRING
RUN apt-get -qqy install libicu-dev g++
RUN docker-php-ext-install intl mbstring

#

RUN apt-get clean

RUN echo "extension=/usr/lib/php5/20131226/pdo.so" >> /usr/local/etc/php/php.ini
RUN echo "extension=/usr/lib/php5/20131226/pdo_mysql.so" >> /usr/local/etc/php/php.ini
RUN echo "extension=/usr/lib/php5/20131226/mysql.so" >> /usr/local/etc/php/php.ini

RUN echo "memory_limit = 512M" >> /usr/local/etc/php/php.ini
RUN apt-get -qqy install libpng12-dev
RUN docker-php-ext-install gd