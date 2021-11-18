FROM debian:jessie

ENV DB_USER=user
ENV DB_PASSWORD=password
ENV DB_NAME=testdb

RUN apt-get update
RUN echo "mysql-server mysql-server/root_password password rootpassword" | debconf-set-selections && echo "mysql-server mysql-server/root_password_again password rootpassword" | debconf-set-selections && apt-get -y install mysql-server

RUN 

RUN sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

VOLUME /var/lib/mysql

EXPOSE 3306

CMD service mysql start && mysql --user=root --password=rootpassword -e "CREATE USER '${DB_USER}'@'%' IDENTIFIED BY '${DB_PASSWORD}';" || true && \
mysql --user=root --password=rootpassword -e "CREATE DATABASE IF NOT EXISTS ${DB_NAME};" && \
mysql --user=root --password=rootpassword -e "GRANT all privileges ON ${DB_NAME}.* TO '${DB_USER}'@'%';" \
mysql --user=root --password=rootpassword -e "flush privileges;" && \
mysqld