FROM ubuntu:18.04
Label maintainer "Andre Freitas"

# Ignora qualquer interação do usuário com o ambiente
ENV DEBIAN_FRONTEND=noninteractive

# Install apache, PHP, and supplimentary programs. openssh-server, curl, and lynx-cur are for debugging the container.
RUN apt-get update
RUN apt-get -y install nano
RUN apt -y install software-properties-common 
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install php7.4
RUN apt-get -y install php7.4-cli
RUN apt-get -y install php7.4-mbstring
RUN apt-get -y install php7.4-gd
RUN apt-get -y install php7.4-mysql
RUN apt-get -y install php7.4-pgsql 
RUN apt-get -y install php7.4-sqlite
RUN apt-get -y install php7.4-bcmath
RUN apt-get -y install php7.4-bz2
RUN apt-get -y install php7.4-intl
RUN apt-get -y install php7.4-zip
RUN apt-get -y install php7.4-xml
RUN apt-get -y install apache2
RUN apt-get -y install mysql-server 

# Enable Remote Access MySQL
RUN   echo "[mysqld]" >> /etc/mysql/my.cnf
RUN   echo "bind-address = 0.0.0.0" >> /etc/mysql/my.cnf

# Enable apache mods.
RUN a2enmod php7.4
RUN a2enmod rewrite

# Update the PHP.ini file, enable <? ?> tags and quieten logging.
RUN sed -i "s/short_open_tag = Off/short_open_tag = On/" /etc/php/7.4/apache2/php.ini
RUN sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/7.4/apache2/php.ini

# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

# Expose apache.
EXPOSE 80

# Copy this repo into place.
#ADD www /var/www/site

# Update the default apache site with the config we created.
ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf

# By default start up apache in the foreground, override with /bin/bash for interative.
CMD /usr/sbin/apache2ctl -D FOREGROUND
