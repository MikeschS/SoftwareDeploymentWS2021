FROM debian:jessie

RUN apt-get update
RUN echo "mysql-server mysql-server/root_password password root" | debconf-set-selections && echo "mysql-server mysql-server/root_password_again password root" | debconf-set-selections && apt-get -y install mysql-server

RUN service mysql start && mysql --user=root --password=root -e "CREATE USER 'user'@'%' IDENTIFIED BY 'password';" && \
mysql --user=root --password=root -e "CREATE DATABASE testdb;" && \
mysql --user=root --password=root -e "GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, INDEX, DROP, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON testdb.* TO 'user'@'%';"

RUN sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

VOLUME /var/lib/mysql

EXPOSE 3306

CMD ["mysqld"]