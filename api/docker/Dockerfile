FROM php:8-apache

RUN a2enmod rewrite
RUN docker-php-ext-install pdo pdo_mysql
RUN apt-get update && apt-get install -y \
    git \
    curl

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer