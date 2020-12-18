# Images
FROM composer:2.0 as composer
FROM php:7.4-fpm
ARG SYMFONY_PATH

# Installation
RUN docker-php-ext-install pdo_mysql
RUN pecl install apcu

RUN apt-get update && \
  apt-get install -y \
  libzip-dev \
  sudo \
  dpkg \
  curl \
  wget

RUN docker-php-ext-install zip
RUN docker-php-ext-enable apcu

# Setting root user
RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo
USER docker

# Symfony path
WORKDIR $SYMFONY_PATH
COPY --chown=1000:1000 symfony $SYMFONY_PATH

# Composer
# CMD /bin/bash
RUN PATH=$PATH:/usr/src/app/vendor/bin:bin
# CMD bash -c "curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
#   && composer install --no-scripts --prefer-dist \
#   && rm -rf \"\$(composer config cache-dir)\" \"\$(composer config data-dir)\""
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# RUN wget https://raw.githubusercontent.com/composer/getcomposer.org/1b137f8bf6db3e79a38a5bc45324414a6b1f9df2/web/installer -O - -q | php -- --quiet
# RUN mv composer.phar /usr/local/bin/composer
# RUN composer install --no-scripts --prefer-dist \
#   && rm -rf "$(composer config cache-dir)" "$(composer config data-dir)"

EXPOSE 9001
EXPOSE 9000