FROM php:7.3-fpm-alpine
RUN apk update
RUN apk --update add \
    && apk add build-base curl git zip unzip vim curl-dev
RUN cd /usr/bin && curl -sS https://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apk add libxml2-dev $PHPIZE_DEPS
RUN pecl install xdebug
RUN docker-php-ext-install pdo_mysql mbstring xml curl session tokenizer json
RUN docker-php-ext-enable pdo_mysql mbstring xml curl session tokenizer json xdebug
WORKDIR /var/www/html