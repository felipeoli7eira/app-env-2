FROM php:8-apache

USER root

ENV APACHE_DOCUMENT_ROOT=/var/www/public

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
RUN a2enmod rewrite

RUN docker-php-ext-install pdo pdo_mysql

RUN apt-get update && apt-get install -y \
    git \
    curl

RUN chown -R www-data:www-data /var/www
RUN chmod -R 777 /var/www

# CMD bash -c "composer install"
# CMD bash -c "composer install && php artisan serve --host 0.0.0.0 --port 5001"

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/

WORKDIR /var/www
