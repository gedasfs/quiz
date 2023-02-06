FROM php:8.1.12-fpm-alpine3.16

RUN apk update \
	apk upgrade

RUN apk add bash

RUN apk add --update \
		$PHPIZE_DEPS \
		freetype-dev \
		git \
		libjpeg-turbo-dev \
		libpng-dev \
	&& docker-php-ext-configure gd --with-jpeg --with-freetype \
	&& docker-php-ext-install gd \
    && docker-php-ext-install mysqli \
    && docker-php-ext-enable mysqli \
    && docker-php-ext-install pdo pdo_mysql

# COPY ./conf/* /usr/local/etc/php/conf.d

COPY --from=composer:2.4.2 /usr/bin/composer /usr/bin/composer