FROM alpine:3.11
LABEL author="Serge NOEL <serge.noel@net6a.com>"

RUN adduser -D -s /sbin/nologin nginx \
    && apk add --no-cache nginx \
    && mkdir /run/nginx \
    && rm /etc/nginx/conf.d/default.conf

COPY Files/ /

EXPOSE 80
VOLUME /var/www

# Cleaning up
# RUN mkdir /www \
#     && apk del tzdata \
#     && rm -rf /var/cache/apk/*

# STOPSIGNAL SIGTERM

CMD ["/usr/local/bin/launch-nginx"]
