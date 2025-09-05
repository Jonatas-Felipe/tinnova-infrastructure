# Tinnova Teste Infraestrutura

Este repositório contém a configuração do Docker Compose para orquestrar todos os microserviços e frontends da aplicação Tinnova, incluindo bancos de dados.

## Pré-requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/downloads)

## Repositórios necessários

A aplicação é composta por 6 repositórios independentes. Clone cada um deles em um diretório comum (ex.: `tinnova-projects`):

```bash
mkdir tinnova-projects
cd tinnova-projects

git clone https://github.com/Jonatas-Felipe/tinnova-infrastructure;
git clone https://github.com/Jonatas-Felipe/tinnova-backend-top-api-gateway;
git clone https://github.com/Jonatas-Felipe/tinnova-backend-top-users;
git clone https://github.com/Jonatas-Felipe/tinnova-backend-top-finance;
git clone https://github.com/Jonatas-Felipe/tinnova-frontend-main;
git clone https://github.com/Jonatas-Felipe/tinnova-frontend-top-users;
git clone https://github.com/Jonatas-Felipe/tinnova-frontend-top-finance;