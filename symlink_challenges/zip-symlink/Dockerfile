FROM php:7.3-apache

RUN apt-get update

RUN apt install unzip -y

RUN a2enmod headers

COPY ./configs/apache2.conf /etc/apache2/apache2.conf
COPY ./configs/000-default.conf /etc/apache2/sites-available/000-default.conf

COPY ./src .

RUN chown -R root:www-data /var/www/html
RUN chmod 750 /var/www/html

WORKDIR /var/www/html/
RUN find . -type f -exec chmod 640 {} \;
RUN find . -type d -exec chmod 750 {} \;

# add write permission for upload file
RUN chown -R root:www-data /var/www/html/upload/
RUN chmod g+w /var/www/html/upload/

# add write permission for exploit ~~
RUN chmod g+w /var/www/html/

# prevent delete
RUN chmod +t -R /var/www/html/


RUN echo "FLAG{f736685446ee00b70ba55824f3618a73}" >> /etc/passwd
RUN echo "FLAG{96d5f81281a138b1b59f2859caf5dec9}" >> /secret.txt
