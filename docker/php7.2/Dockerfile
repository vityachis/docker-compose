FROM php:7.2-fpm-alpine

MAINTAINER Viktor Chistyakov <vityachis@gmail.com>

RUN apk add --no-cache freetype-dev libjpeg-turbo-dev libpng-dev \
    libssh-dev rabbitmq-c-dev libmemcached-dev
RUN apk add --no-cache zsh nano git npm ${PHPIZE_DEPS}

RUN docker-php-ext-install -j$(nproc) sockets exif pdo_mysql opcache
RUN docker-php-ext-configure gd --with-freetype-dir --with-jpeg-dir

RUN pecl install xdebug-3.0.4 redis-5.3.4 memcached-3.1.5 amqp-1.10.2
RUN docker-php-ext-enable xdebug redis memcached amqp

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY custom.ini ${PHP_INI_DIR}/conf.d/
COPY zshrc.sh /root/.zshrc

RUN chown -R www-data:www-data /var/www
WORKDIR /var/www
