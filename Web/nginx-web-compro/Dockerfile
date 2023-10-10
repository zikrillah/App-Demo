FROM nginx:mainline-alpine3.18-slim

MAINTAINER zikrillah

# We need to give all user groups write permission on folder /var/cache/nginx/ and file /var/run/nginx.pid.
# So users with random uid will be able to run NGINX.

RUN apk update && \
    apk add --no-cache tzdata

RUN chmod -R a+w /var/cache/nginx/ \
        && touch /var/run/nginx.pid \
        && chmod a+w /var/run/nginx.pid \
        && rm /etc/nginx/conf.d/*

ENV TZ="Asia/Jakarta"

COPY *.conf /etc/nginx/conf.d/
COPY main.css /usr/share/nginx/html/
COPY *.html /usr/share/nginx/html/
EXPOSE 80
USER nginx
