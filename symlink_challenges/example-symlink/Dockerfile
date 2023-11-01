FROM php:7.3-apache

RUN apt-get update

RUN apt install zip unzip -y

RUN a2enmod headers

COPY ./src/index.php /var/www/html/index.php

RUN chown -R root:www-data /var/www/html
RUN chmod 750 /var/www/html


WORKDIR /var/www/html/
RUN find . -type f -exec chmod 640 {} \;
RUN find . -type d -exec chmod 750 {} \;

# add write permission for exploit ~~
RUN chmod g+w /var/www/html/

# prevent delete
RUN chmod +t -R /var/www/html/


RUN echo "FLAG{5c2613a6f355da43286931bcba1fcf33}" >> /etc/passwd
RUN echo "FLAG{ecb6264816c93ff44a5a0bbbc4f3cdd7}" >> /secret.txt
