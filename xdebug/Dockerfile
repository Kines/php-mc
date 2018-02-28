FROM postika/php-mc:alpine
MAINTAINER alexp@postika.eu

RUN apk update && apk add autoconf automake gcc g++ make \
&& pecl -q install xdebug \
&& docker-php-ext-enable xdebug \
&& echo 'xdebug.remote_enable=1' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
&& echo 'xdebug.remote_port=8999' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \ 
&& apk del .build-deps \
&& rm -rf /tmp/* \
&& rm -rf /var/cache/apk/*

CMD "sh"


