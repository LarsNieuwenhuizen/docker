FROM alpine:edge
MAINTAINER Lars Nieuwenhuizen<lars.nieuwenhuizen@me.com>

RUN adduser -D -h /home/php -u 9001 php
RUN echo "@testing http://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories

RUN apk add --no-cache libpng-dev \
    && apk add --no-cache php7 git \
    && apk add --no-cache \
          php7-fpm \
          php7-openssl \
          php7-pdo \
          php7-pdo_mysql \
          php7-pdo_sqlite \
          php7-ctype \
          php7-mbstring \
          php7-gd \
          php7-gettext \
          php7-iconv \
          php7-json \
          php7-exif \
          php7-curl \
          php7-xml \
          php7-xsl \
          php7-opcache \
          php7-phar \
          php7-gd \
          php7-redis@testing \
          php7-xdebug \
          php7-tokenizer \
          php7-simplexml

RUN apk add --no-cache \
          xvfb \
          ttf-freefont \
          fontconfig

RUN ln -s /usr/bin/php7 /usr/local/bin/php
RUN chown php /usr/local/bin/php

RUN mkdir -p /var/www/html && \
  chown -R php /var/log/php7 && \
  chmod -R g+w /var/log/php7

RUN mkdir -p /var/www/html && \
  chown -R php /var/www/html && \
  chmod -R g+w /var/www/html

RUN chown -R php /var/www/html

USER php

WORKDIR /var/www/html

EXPOSE 9000

ENTRYPOINT ["/usr/sbin/php-fpm7","--nodaemonize"]