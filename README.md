# Estudos em Docker para Concurso Público 013/2019 (UNICAMP)
Este projeto destina-se para estudos tecnico cientificos com finalidade de aprovacao em concurso publico em universidade publica no interior do estado de sao paulo.

## Objetivo
Criação de imagens e container usando tecnologia Docker em ambiente Linux. Nesse teste os avaliadores irao avaliar toda a capacidade de criação de arquitetura, qualidade do código, validações, elaboração de layout e usabilidade.

## Criação de databases diretas
- sudo docker container run -d --name mysqlsrv -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 mysql:latest
- sudo docker container run -d --name pgsrv -e POSTGRES_PASSWORD=123456 -p 5432:5432 postgres:latest

## Configurando timeout da database mySQL
- SET GLOBAL connect_timeout=28800;
- SET GLOBAL interactive_timeout=28800;
- SET GLOBAL wait_timeout=28800;

## Criação de Apache Local na porta 80
- sudo apt -y install software-properties-common
- sudo add-apt-repository ppa:ondrej/php
- sudo apt-get update
- sudo apt-get -y install php7.4 php7.4-cli php7.4-mbstring php7.4-gd php7.4-mysql php7.4-pgsql php7.4-sqlite php7.4-bcmath php7.4-bz2 php7.4-intl php7.4-zip php7.4-xml php7.4-curl php7.4-imap apache2
- sudo a2enmod php7.4
- sudo a2enmod rewrite

## Criação de aplicação pgAdmin4 na porta 5050
- docker pull dpage/pgadmin4
- docker run --name pgadmin4 -p 5050:5050 -e 'PGADMIN_DEFAULT_EMAIL=admin@admin.com' -e 'PGADMIN_DEFAULT_PASSWORD=123456' -e 'PGADMIN_LISTEN_PORT=5050' -d dpage/pgadmin4

## Copiando dump export do pgAdmin4 para máquina host
- docker cp pgadmin4:/var/lib/pgadmin/storage/admin_admin.com/dumps/arquivo.csv
- obs: admin_admin.com é o nome de usuário tranformado em caminho, o arroba se transforma em underline. "Dumps" é a pasta criada usando pgadmin4. Ex: admin@admin.com torna-se admin_admin.com
