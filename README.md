# Estudos em Docker para Concurso Público 013/2019 (UNICAMP)
Este projeto destina-se para estudos tecnico cientificos com finalidade de aprovacao em concurso publico em universidade publica no interior do estado de sao paulo.

## Objetivo
Criação de imagens e container usando tecnologia Docker em ambiente Linux. Nesse teste os avaliadores irao avaliar toda a capacidade de criação de arquitetura, qualidade do código, validações, elaboração de layout e usabilidade.

## Criação de databases diretas
- docker container run -d --name mysqlsrv -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 mysql:latest
- docker container run -d --name pgsrv -e POSTGRES_PASSWORD=123456 -p 5432:5432 postgres:latest
