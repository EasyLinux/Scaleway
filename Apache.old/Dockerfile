FROM easylinux/scaleway:alpine-3.8
LABEL author="Serge NOEL <serge.noel@easylinux.fr>"

RUN apk add --no-cache php5-apache2 php5-json php5-mysql php5-xml php5-zip php5-gd  php5-openssl php5-curl php5-xsl \
    && sed -i 's|/var/www/localhost/htdocs|/var/www/html|g' /etc/apache2/httpd.conf \ 
    && ln -s /dev/stdout /var/log/apache2/access.log \
    && ln -s /dev/stderr /var/log/apache2/error.log \
    && mkdir /var/run/apache2 \
    && sed -i 's/upload_max_filesize = 2M/upload_max_filesize = 32M/g' /etc/php5/php.ini \
    && sed -i 's/max_execution_time = 30/max_execution_time = 600/g' /etc/php5/php.ini \
    && sed -i 's/memory_limit = 128M/memory_limit = 256M/g' /etc/php5/php.ini 

VOLUME /var/www/html
EXPOSE 80

CMD ["/usr/sbin/httpd","-D","FOREGROUND"]
