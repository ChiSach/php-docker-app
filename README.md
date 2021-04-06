# php-docker-app

Dockerfile
//---------
FROM php:7.1-apache
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
//---------

docker-compose
//---------
# version: '3'

# services:
#   app:
#     container_name: php7
#     image: php:7.1-apache
#     volumes:
#       - ".:/var/www/html"
#       # - ./src:/var/www/html
#     ports:
#       - 8089:80
#     restart: always

version: '3'
services:
    web:
        build: .
        ports:
            - 80:80
        volumes:
          - ".:/var/www/html"
 //--------
