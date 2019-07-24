FROM php:7.2-apache

COPY ./source.list /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y wget \
    && mkdir -p /tmp/gearmand /tmp/gearman /tmp/libuuid \
    && wget -c https://github.com/gearman/gearmand/releases/download/1.1.18/gearmand-1.1.18.tar.gz \
    && tar -xf gearmand-1.1.18.tar.gz -C /tmp/gearmand --strip-components=1 \
    && wget -c https://github.com/wcgallego/pecl-gearman/archive/gearman-2.0.3.tar.gz \
    && tar -xf gearman-2.0.3.tar.gz -C /tmp/gearman --strip-components=1 \
    && wget -c http://nchc.dl.sourceforge.net/project/libuuid/libuuid-1.0.3.tar.gz \
    && tar -xf libuuid-1.0.3.tar.gz -C /tmp/libuuid --strip-components=1 \
    && cd /tmp/libuuid \
    && ./configure \
    && make \
    && make install \
    && ( \
        cd /tmp/gearmand \
        && ./configure \
        && make \
        && make install \
    ) \
    && /sbin/ldconfig \
    && docker-php-ext-configure /tmp/gearman --with-php-config=/usr/local/bin/php-config \
    && docker-php-ext-install /tmp/gearman \
    && apt-get clean \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
