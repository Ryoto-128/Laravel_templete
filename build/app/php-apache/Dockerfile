FROM php:7.4.29-apache

# install locales
RUN apt clean \
    && apt update \
    && apt install -y locales locales-all \
    # compile local file
    && locale-gen ja_JP.UTF-8

# set lang=Ja.utf-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:en
ENV LC_ALL ja_JP.UTF-8

# change TZ to Ja
RUN ln -sf /usr/share/zoneinfo/Japan /etc/localtime

# install comporser
RUN apt install -y curl git unzip
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html/
RUN composer create-project laravel/laravel .