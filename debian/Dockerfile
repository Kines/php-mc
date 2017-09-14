FROM php:7.1-fpm
MAINTAINER alexp@postika.eu

# Install PHP extensions and PECL modules.
RUN buildDeps=" \
        libbz2-dev \
        libmemcached-dev \
    " \
    runtimeDeps=" \
        libfreetype6-dev \
        libicu-dev \
        libjpeg-dev \
        libwebp-dev \
        libgeoip-dev \
        libmagickwand-dev \
        libmcrypt-dev \
        libxslt1-dev \
    " \
&& apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y $buildDeps $runtimeDeps \
&& pecl -q install geoip-1.1.1 imagick memcached redis \
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-webp-dir=/usr/include/ \
&& docker-php-ext-install bz2 calendar exif gd gettext mcrypt pcntl pdo_mysql shmop sockets wddx xsl \
&& docker-php-ext-enable geoip imagick memcached redis \
&& rm -r /var/lib/apt/lists/*