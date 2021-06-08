FROM php:8.0-fpm

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    && pecl install xdebug-3.0.4 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install -j$(nproc) exif

WORKDIR /var/www

COPY php.ini ${PHP_INI_DIR}/
COPY custom.ini ${PHP_INI_DIR}/conf.d/
