FROM php:7
MAINTAINER shchedrin <ilya.shchedrin@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -yqq \
    && apt-get install git zlib1g-dev libsqlite3-dev -y \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo_sqlite

#Path to Composer autoload.php - /root/.composer/vendor/autoloader.php
RUN curl -fsSL https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer global require phpunit/phpunit ^6.2 --no-progress --no-scripts --no-interaction

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

ENV PATH /root/.composer/vendor/bin:$PATH
WORKDIR /var/www/
CMD ["php -v"]
