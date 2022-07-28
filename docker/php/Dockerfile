FROM --platform=linux/amd64 php:7.4-fpm

RUN apt-get update && apt-get install -y libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev 

RUN docker-php-ext-configure gd --enable-gd --with-webp --with-jpeg \
    --with-xpm --with-freetype 

RUN docker-php-ext-install gd mysqli opcache pdo pdo_mysql


RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# Sendmail
RUN apt-get update &&\
    apt-get install --no-install-recommends --assume-yes --quiet ca-certificates curl git qemu-user-static &&\
    rm -rf /var/lib/apt/lists/*

ADD ./php.ini /usr/local/etc/php/conf.d/php.ini
ADD ./opcache.ini /usr/local/etc/php/conf.d/opcache.ini
ADD ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
ADD ./memcached.ini /usr/local/etc/php/conf.d/memcached.ini

RUN usermod -u 1000 www-data
RUN chmod 777 -R /tmp && chmod o+t -R /tmp

WORKDIR /var/www/bitrix