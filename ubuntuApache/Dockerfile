FROM ubuntu:latest
Label criador 'andre freitas'
ENV DEBIAN_FRONTEND = noninteractive
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install apache2
RUN apt-get -y install php
ADD teste.php /var/www/html/
EXPOSE 80
CMD /usr/sbin/apache2ctl -D FOREGROUND
