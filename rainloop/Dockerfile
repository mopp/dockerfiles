FROM php:7.1-fpm

RUN apt-get update && \
    apt-get --yes upgrade && \
    apt-get --yes install nginx wget

RUN mkdir -p /var/www/rainloop && \
    cd /var/www/rainloop && \
    curl -sL https://repository.rainloop.net/installer.php | php && \
    find . -type d -exec chmod 755 {} \; && \
    find . -type f -exec chmod 644 {} \; && \
    chown -R www-data:www-data .

RUN rm /etc/nginx/sites-enabled/default
COPY rainloop.conf /etc/nginx/sites-enabled/rainloop.conf

COPY www.conf /usr/local/etc/php-fpm.d/zzz-ww.conf

EXPOSE 80

ENTRYPOINT ["/usr/local/sbin/php-fpm", "-D && ", "/usr/sbin/nginx", "-g", "daemon off;"]
