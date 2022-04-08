FROM composer:2.0.12 AS composer

FROM drupal:8.8-apache

COPY --from=composer /usr/bin/composer /usr/bin/

ENV COMPOSER_ALLOW_SUPERUSER 1


RUN apt-get update && apt-get install -y \
	curl \
    default-mysql-client\
	git \
	vim \
	wget


RUN rm -rf /var/www/html/*

COPY apache-drupal.conf /etc/apache2/sites-enabled/000-default.conf

WORKDIR /app