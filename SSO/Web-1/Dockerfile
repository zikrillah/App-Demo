FROM nginx:mainline-alpine

RUN rm /etc/nginx/conf.d/*
ADD web-php.conf /etc/nginx/conf.d/

RUN rm /usr/share/nginx/html/index.html
COPY src /usr/share/nginx/html

RUN apk update && apk upgrade
RUN apk add bash
RUN apk add php82 php82-fpm php82-opcache
RUN apk add php82-gd php82-zlib php82-curl php82-session

COPY server/etc/php /etc/php82

RUN mkdir /var/run/php
STOPSIGNAL SIGTERM
CMD ["/bin/bash", "-c", "php-fpm82 && chmod 777 /var/run/php/php82-fpm.sock && chmod 755 /usr/share/nginx/html/* && nginx -g 'daemon off;'"]
