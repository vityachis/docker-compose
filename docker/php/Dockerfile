FROM php:8.0-fpm-alpine

MAINTAINER Viktor Chistyakov <vityachis@gmail.com>

RUN apk add --no-cache \
    freetype-dev libjpeg-turbo-dev libpng-dev \
    libssh-dev rabbitmq-c-dev \
    zsh nano git nodejs npm $PHPIZE_DEPS \
    && docker-php-ext-install -j$(nproc) \
    sockets exif pdo_mysql opcache \
    && pecl install xdebug-3.0.4 redis-5.3.4 amqp-1.11.0beta \
    && docker-php-ext-enable xdebug redis amqp \
    && docker-php-ext-configure gd --with-freetype --with-jpeg

COPY custom.ini ${PHP_INI_DIR}/conf.d/
COPY aliases.sh /root/.zshrc

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN chown -R www-data:www-data /var/www

WORKDIR /var/www
