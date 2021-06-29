FROM php:8.0-fpm-alpine

MAINTAINER Viktor Chistyakov <vityachis@gmail.com>

RUN apk add --no-cache \
    freetype-dev libjpeg-turbo-dev libpng-dev \
    nano git nodejs npm $PHPIZE_DEPS \
    && pecl install xdebug-3.0.4 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
    exif pdo_mysql opcache

COPY custom.ini ${PHP_INI_DIR}/conf.d/

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN chown -R www-data:www-data /var/www

WORKDIR /var/www
