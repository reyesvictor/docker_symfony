# ./docker/php/Dockerfile
# FROM composer:2.0 as composer
# FROM php:7.4-fpm

# # Install dependencies
# RUN docker-php-ext-install pdo_mysql
# RUN pecl install apcu
# RUN apt-get update && \
# apt-get install -y \
# libzip-dev
# RUN docker-php-ext-install pdo pdo_mysql zip
# RUN docker-php-ext-enable apcu

# WORKDIR /usr/src/app

# COPY --chown=1000:1000 apps/my-symfony-app /usr/src/app

# RUN PATH=$PATH:/usr/src/app/vendor/bin:bin

# # Install composer
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# RUN composer install --no-scripts --prefer-dist \
#   && rm -rf "$(composer config cache-dir)" "$(composer config data-dir)"

# EXPOSE 9000

# # Loading images
# FROM ubuntu:21.04
# FROM php:8.0-fpm

# # Update
# RUN apt-get update && \
#   apt-get install -y \
#   libzip-dev

# # Installing php dependencies
# RUN docker-php-ext-install zip \ 
#   && pecl install apcu \
#   && docker-php-ext-enable apcu

# # Symfony Repository
# WORKDIR /usr/src/app
# COPY --chown=1000:1000 apps/my-symfony-app/ /usr/src/app/
# RUN PATH=$PATH:/usr/src/app/vendor/bin:bin

# # Installing composer
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
#   && composer install --no-scripts --prefer-dist \
#   && rm -rf "$(composer config cache-dir)" "$(composer config data-dir)"

# # Exposing public port
# EXPOSE 9000

# ./docker/php/Dockerfile

FROM composer:2.0 as composer

FROM php:7.4-fpm

RUN docker-php-ext-install pdo_mysql

RUN pecl install apcu

RUN apt-get update && \
  apt-get install -y \
  libzip-dev

RUN docker-php-ext-install zip
RUN docker-php-ext-enable apcu

WORKDIR /usr/src/app

COPY --chown=1000:1000 apps/my-symfony-app /usr/src/app

RUN PATH=$PATH:/usr/src/app/vendor/bin:bin
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer install --no-scripts --prefer-dist \
  && rm -rf "$(composer config cache-dir)" "$(composer config data-dir)"

EXPOSE 9000