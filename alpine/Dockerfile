FROM php:7.1-fpm-alpine
MAINTAINER alexp@postika.eu

# Install dependencies
RUN apk add --no-cache --update \
    bzip2-dev \
    geoip-dev \
    gettext-dev \
    imagemagick-dev \
    libmcrypt-dev \
    libxslt-dev \
    libmemcached-dev \
&& apk add --no-cache --virtual .build-deps \
    autoconf \
    gcc \
    libc-dev \
    make \
    libtool \
    pcre-dev \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    icu-dev \
    libwebp-dev \
    cyrus-sasl-dev \
&& pecl channel-update pecl.php.net\
&& pecl -q install geoip-1.1.1 imagick memcached redis mongodb\
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-webp-dir=/usr/include/ \
&& docker-php-ext-install bcmath bz2 calendar exif gd gettext pcntl pdo_mysql mcrypt mysqli shmop sockets wddx xsl hash \
&& docker-php-ext-enable bcmath geoip imagick memcached redis mongodb \
&& apk del .build-deps \
&& rm -rf /tmp/* \
&& rm -rf /var/cache/apk/*



