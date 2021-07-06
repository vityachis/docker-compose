FROM php:8.0-fpm-alpine

MAINTAINER Viktor Chistyakov <vityachis@gmail.com>

RUN apk add --no-cache freetype-dev libjpeg-turbo-dev libpng-dev libssh-dev \
    zsh nano git nodejs npm rabbitmq-c-dev ${PHPIZE_DEPS}

RUN docker-php-ext-install -j$(nproc) sockets exif pdo_mysql opcache
RUN docker-php-ext-configure gd --with-freetype --with-jpeg

RUN pecl install xdebug-3.0.4 redis-5.3.4 amqp-1.11.0beta #PHP == 8.0
#RUN pecl install xdebug-3.0.4 redis-5.3.4 amqp-1.10.2     #PHP >= 7.2
#RUN pecl install xdebug-2.7.2 redis-5.3.4 amqp-1.10.2     #PHP <= 7.1
RUN docker-php-ext-enable xdebug redis amqp

COPY custom.ini ${PHP_INI_DIR}/conf.d/
COPY aliases.sh /root/.zshrc

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN chown -R www-data:www-data /var/www

WORKDIR /var/www
