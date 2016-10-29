FROM alpine:edge
MAINTAINER Lars Nieuwenhuizen <l.nieuwenhuizen@developers.nl>

RUN apk --no-cache --update add \
    openssl \
    curl \
    php7 \
    php7-json \
    php7-xml \
    php7-zlib \
    php7-mbstring \
    php7-phar \
    php7-ctype \
    php7-zip \
    php7-openssl \
    php7-iconv \
    php7-curl \
    php7-pdo \
    php7-dom

RUN ln -s /usr/bin/php7 /usr/bin/php
RUN chmod a+x /usr/bin/php

RUN wget http://getcomposer.org/installer
RUN mv installer composer-setup.php
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

RUN composer global require "laravel/installer"

RUN ln  -s ~/.composer/vendor/bin/laravel /usr/bin/laravel
RUN chmod +x /usr/bin/laravel

VOLUME [ "/app" ]

WORKDIR /app

ENTRYPOINT ["laravel"]