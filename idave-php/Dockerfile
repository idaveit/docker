FROM php:7-fpm-alpine

RUN apk add --update pcre-dev
RUN docker-php-ext-install opcache
RUN docker-php-ext-install mysqli