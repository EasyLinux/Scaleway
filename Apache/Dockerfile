FROM alpine:3.11
LABEL author="Serge NOEL <serge.noel@easylinux.fr>"

RUN apk add --no-cache php7-apache2 php7-json php7-mysqli php7-xml php7-simplexml php7-zip php7-session php7-mbstring php7-curl \ 
           php7-dom php7-exif php7-fileinfo php7-imagick php7-gd php7-iconv php7-mysqli \
    && ln -s /dev/stdout /var/log/apache2/access.log \
    && ln -s /dev/stderr /var/log/apache2/error.log \
    && sed -i 's/upload_max_filesize = 2M/upload_max_filesize = 64M/g' /etc/php7/php.ini \
    && sed -i 's/max_execution_time = 30/max_execution_time = 300/g' /etc/php7/php.ini \
    && sed -i 's/memory_limit = 128M/memory_limit = 512M/g' /etc/php7/php.ini
COPY Files/ /

WORKDIR /var/www/html
VOLUME /var/www/html
EXPOSE 80

CMD ["/usr/sbin/httpd","-D","FOREGROUND"]
