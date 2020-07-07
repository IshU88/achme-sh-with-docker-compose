FROM openresty/openresty:1.15.8.3-alpine-fat
RUN apk add --no-cache --virtual .run-deps \
    bash \
    curl \
    diffutils \
    grep \
    sed \
    openssl \
    && addgroup -S nginx \
    && adduser -D -S -h /var/cache/nginx -s /sbin/nologin -G nginx nginx

RUN apk add --no-cache --virtual .build-deps \
        gcc \
        libc-dev \
        make \
        openssl-dev \
        pcre-dev \
        zlib-dev \
        linux-headers \
        gnupg \
        libxslt-dev \
        gd-dev \
        geoip-dev \
        perl-dev \
        tar \
        unzip \
        zip \
        unzip \
        g++ \
        cmake \
        lua \
        lua-dev \
        make \
        autoconf \
        automake \
    && /usr/local/openresty/luajit/bin/luarocks install lua-resty-acme \
    && /usr/local/openresty/luajit/bin/luarocks install luafilesystem \
    && apk del .build-deps \
    && rm -rf /usr/local/openresty/nginx/conf/* \
    && mkdir -p /var/cache/nginx

COPY ./ssl /etc/ssl
COPY ./nginx.conf /usr/local/openresty/nginx/conf/nginx.conf
# COPY ./mime.types /usr/local/openresty/nginx/conf/mime.types
# COPY ./front-end /usr/local/openresty/nginx/html
