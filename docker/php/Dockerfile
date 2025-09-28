FROM php:8.2-fpm

WORKDIR /var/www/html

RUN apt-get update && apt-get install -y \
    libfreetype-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    bash \
    git \
    zip \
    unzip \
    vim \
    curl \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install bcmath
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer self-update

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN rm -rf /var/cache/apk/* /tmp/*  