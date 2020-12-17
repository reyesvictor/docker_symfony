# Images
FROM composer:2.0 as composer
FROM php:7.4-fpm

# Installation
RUN docker-php-ext-install pdo_mysql
RUN pecl install apcu

RUN apt-get update && \
  apt-get install -y \
  libzip-dev \
  sudo \
  dpkg \
  curl

RUN docker-php-ext-install zip
RUN docker-php-ext-enable apcu

# Setting root user
RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo
USER docker

# Symfony path
WORKDIR $SYMFONY_PATH
COPY --chown=1000:1000 symfony $SYMFONY_PATH
CMD /bin/bash

# Composer
RUN PATH=$PATH:/usr/src/app/vendor/bin:bin
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer install --no-scripts --prefer-dist \
  && rm -rf "$(composer config cache-dir)" "$(composer config data-dir)"

EXPOSE 9001