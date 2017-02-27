FROM php:7.1.1-fpm
MAINTAINER xjun <xiongjunceplj@163.com>

######
# 安装PHP扩展
######

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libicu-dev \
                --no-install-recommends

RUN docker-php-ext-install mcrypt zip intl mbstring mysqli pdo_mysql exif \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd
    
RUN apt-get install -y libmemcached-dev zlib1g-dev && apt-get install -y git && git clone -b php7 https://github.com/php-memcached-dev/php-memcached /usr/src/php/ext/memcached \
    && docker-php-ext-configure /usr/src/php/ext/memcached \
        --disable-memcached-sasl \
    && docker-php-ext-install /usr/src/php/ext/memcached \
    && rm -rf /usr/src/php/ext/memcached
