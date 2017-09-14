FROM php:7.1-fpm-alpine
MAINTAINER alexp@postika.eu

# Install dependencies
RUN apk --no-cache --update add \
    bzip2-dev \
    memcached-dev \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    icu-dev \
    libwebp-dev \
    geoip-dev \
    imagemagick-dev \
    libmcrypt-dev \
    libxslt-dev \
    libtool \
    cyrus-sasl-dev \
    gettext-dev \
&& pecl -q install geoip-1.1.1 imagick memcached redis \
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-webp-dir=/usr/include/ \
&& docker-php-ext-install bz2 calendar exif gd gettext mcrypt pcntl pdo_mysql shmop sockets wddx xsl \
&& rm -rf /tmp/* \
&& rm -rf /var/cache/apk/*



