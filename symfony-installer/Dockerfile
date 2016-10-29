FROM alpine:edge

MAINTAINER Lars Nieuwenhuizen <l.nieuwenhuizen@developers.nl>

RUN apk --no-cache --update add \
    curl \
    php7 \
    php7-common \
    php7-json \
    php7-xml \
    php7-zlib \
    php7-phar \
    php7-ctype \
    php7-session \
    php7-iconv \
    php7-curl

RUN curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
RUN chmod a+x /usr/local/bin/symfony
RUN ln -s /usr/bin/php7 /usr/bin/php
RUN chmod a+x /usr/bin/php

VOLUME [ "/app" ]
WORKDIR /app

ENTRYPOINT [ "symfony" ]