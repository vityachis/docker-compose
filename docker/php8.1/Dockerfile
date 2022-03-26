FROM php:8.1-fpm-alpine

MAINTAINER Viktor Chistyakov <vityachis@gmail.com>

RUN apk add --no-cache freetype-dev libjpeg-turbo-dev libpng-dev \
    libssh-dev rabbitmq-c-dev libmemcached-dev
RUN apk add --no-cache zsh nano git npm ${PHPIZE_DEPS}

RUN docker-php-ext-install -j$(nproc) sockets exif pdo_mysql opcache
RUN docker-php-ext-configure gd --with-freetype --with-jpeg

RUN pecl install xdebug-3.1.3 redis-5.3.7 memcached-3.2.0 amqp-1.11.0
RUN docker-php-ext-enable xdebug redis memcached amqp

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY custom.ini ${PHP_INI_DIR}/conf.d/
COPY zshrc.sh /root/.zshrc

RUN chown -R www-data:www-data /var/www
WORKDIR /var/www
