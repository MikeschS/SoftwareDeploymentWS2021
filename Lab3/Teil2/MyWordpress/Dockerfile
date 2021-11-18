FROM debian:jessie
RUN apt update
RUN apt install apache2 -y
RUN apt install -y php5 php-pear php5-mysql
RUN apt install -y wget tar

RUN wget http://wordpress.org/latest.tar.gz  && tar -xzvf latest.tar.gz && rm -rf latest.tar.gz

RUN rm -f /var/www/html/index.html
RUN cp -a /wordpress/* /var/www/html
RUN chown -R www-data:www-data /var/www/html
RUN chmod -R 755 /var/www/html

EXPOSE 80

VOLUME [ "/var/www/html" ]

ENTRYPOINT apachectl -D FOREGROUND