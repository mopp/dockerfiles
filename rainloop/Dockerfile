FROM php:7.1-fpm

RUN apt-get update && \
    apt-get --yes upgrade && \
    apt-get --yes install nginx wget

RUN service nginx start
RUN mkdir -p /var/www/rainloop && \
    cd /var/www/rainloop && \
    curl -sL https://repository.rainloop.net/installer.php | php && \
    find . -type d -exec chmod 755 {} \; && \
    find . -type f -exec chmod 644 {} \; && \
    chown -R www-data:www-data .

EXPOSE 80
