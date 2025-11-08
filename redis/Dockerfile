FROM wordpress:6.8.3-php8.3-fpm

RUN apt-get update && apt-get upgrade -y && pecl install redis \
    && docker-php-ext-enable redis
