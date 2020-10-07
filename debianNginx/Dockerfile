FROM debian:latest
LABEL owner 'andre'
ENV DEBIAN_FRONTEND = noninteractive
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install nginx
RUN apt-get -y install php
EXPOSE 80
COPY teste.php /usr/share/nginx/html/
CMD ["nginx", "-g", "daemon off;"]
