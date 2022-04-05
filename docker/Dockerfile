FROM composer:2.0.12 AS composer

FROM drupal:8.4-apache

COPY --from=composer /usr/bin/composer /usr/bin/

ENV COMPOSER_ALLOW_SUPERUSER 1


RUN apt-get update && apt-get install -y \
	curl \
	git \
	mysql-client \
	vim \
	wget

#RUN wget -O drush.phar https://github.com/drush-ops/drush-launcher/releases/download/0.4.2/drush.phar && \
#	chmod +x drush.phar && \
#	mv drush.phar /usr/local/bin/drush

RUN rm -rf /var/www/html/*

COPY apache-drupal.conf /etc/apache2/sites-enabled/000-default.conf

WORKDIR /app