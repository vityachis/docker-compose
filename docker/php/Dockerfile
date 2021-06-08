FROM php:8.0-fpm

RUN apt-get update && apt-get install -y \
    nano git \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    && pecl install xdebug-3.0.4 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
    exif pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ENV XDEBUG_IDEKEY=${XDEBUG_IDEKEY}
ENV XDEBUG_PORT=${XDEBUG_PORT}

WORKDIR /var/www

COPY php.ini ${PHP_INI_DIR}/
COPY custom.ini ${PHP_INI_DIR}/conf.d/
