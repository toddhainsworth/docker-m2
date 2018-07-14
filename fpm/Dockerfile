FROM php:7.1-fpm

RUN apt-get update
RUN apt-get install -y \
  build-essential apt-utils sudo zip unzip \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev \
  libcurl4-gnutls-dev \
  libxml2 libxml2-dev \
  zlib1g-dev \
  libicu-dev \
  libxslt-dev \
  g++ \
  mysql-client

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) iconv mcrypt bcmath curl intl mbstring soap gd xsl zip pdo_mysql

COPY php.ini /usr/local/etc/php/conf.d/zz-magento.ini

RUN usermod -s /bin/bash www-data
RUN chown www-data:www-data /var/www -R

RUN mkdir -p /var/www/.composer
COPY ./auth.json /var/www/.composer/auth.json

