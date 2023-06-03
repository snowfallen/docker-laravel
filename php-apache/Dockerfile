FROM php:8.0-apache

RUN apt-get update \
    && apt-get install -y \
        curl \
        libpng-dev \
        libonig-dev \
        libxml2-dev \
        zip \
        unzip \
        git \
        libzip-dev \
        libpq-dev \
        iputils-ping \
        mc \
    && apt-get clean

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN docker-php-ext-install pdo pdo_mysql zip

COPY .. /var/www/html


WORKDIR /var/www/html
RUN chown -R www-data:www-data /var/www/html/storage \
    && chmod -R 775 /var/www/html/storage \
    && composer install

EXPOSE 8000

CMD apache2-foreground



