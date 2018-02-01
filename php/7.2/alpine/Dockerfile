FROM alpine:3.7
MAINTAINER Lars Nieuwenhuizen<lars.nieuwenhuizen@me.com>

RUN adduser -D -h /home/php -u 9001 php

RUN apk add --no-cache wget ca-certificates \
    && wget -O /etc/apk/keys/phpearth.rsa.pub https://repos.php.earth/alpine/phpearth.rsa.pub \
    && echo "https://repos.php.earth/alpine/v3.7" >> /etc/apk/repositories

RUN apk add --no-cache libpng-dev \
    && apk add --no-cache php7.2 git \
    && apk add --no-cache \
          php7.2-fpm \
          php7.2-openssl \
          php7.2-pdo \
          php7.2-pdo_mysql \
          php7.2-pdo_sqlite \
          php7.2-ctype \
          php7.2-mbstring \
          php7.2-gd \
          php7.2-gettext \
          php7.2-iconv \
          php7.2-json \
          php7.2-exif \
          php7.2-curl \
          php7.2-xml \
          php7.2-xsl \
          php7.2-opcache \
          php7.2-phar \
          php7.2-gd \
          php7.2-redis \
          php7.2-tokenizer \
          php7.2-simplexml \
          php7.2-pcntl

RUN apk add --no-cache \
          xvfb \
          ttf-freefont \
          fontconfig

COPY ./www.conf /etc/php/7.2/php-fpm.d/www.conf

RUN ln -s /usr/bin/php7.2 /usr/local/bin/php
RUN chown php /usr/local/bin/php

RUN chown -R php /var/log/php/7.2 && \
  chmod -R g+w /var/log/php/7.2

RUN mkdir -p /var/www/html && \
  chown -R php /var/www/html && \
  chmod -R g+w /var/www/html

RUN chown -R php /run/php

USER php

WORKDIR /var/www/html

EXPOSE 9000

ENTRYPOINT ["php-fpm7.2","--nodaemonize"]