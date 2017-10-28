FROM php:7.1-fpm
MAINTAINER liguo.song@jfz.com

RUN apt-get update  && apt-get install -y libjpeg62-turbo-dev \
    libfreetype6-dev \
    libmcrypt-dev \
    libpng-dev \
    libxml2-dev \
    libxml2 \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include \
    && docker-php-ext-install -j$(nproc) gd mbstring mysqli pdo pdo_mysql shmop \
    && docker-php-ext-install -j$(nproc) bcmath soap sockets sysvsem

RUN pecl install redis \
    && docker-php-ext-enable redis

RUN apt-get install -y libmemcached-dev zlib1g-dev \
    && pecl install memcached \
    && docker-php-ext-enable memcached
RUN docker-php-ext-install -j$(nproc) zip pcntl
RUN apt-get install -y libmagickwand-dev \
    && rm -rf /var/lib/apt/lists/* \
    && pecl install imagick \
    && docker-php-ext-enable imagick

RUN docker-php-ext-install -j$(nproc) mcrypt
