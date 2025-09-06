# Tinnova Teste Infraestrutura

[![Status da Build](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com/Jonatas-Felipe/tinnova-infrastructure)

Este repositório contém a configuração do Docker Compose para orquestrar todos os microserviços e frontends da aplicação Tinnova, incluindo os bancos de dados.

## 📋 Pré-requisitos

Antes de começar, garanta que você tem as seguintes ferramentas instaladas:

- [Git](https://git-scm.com/downloads)
- [Docker](https://www.docker.com/products/docker-desktop/)

> **Nota:** Este projeto utiliza o **Docker Compose V2**. Os comandos são executados com `docker compose` (com espaço), e não `docker-compose` (com hífen).

## 📂 Estrutura de Pastas

Para que o Docker Compose funcione corretamente, todos os repositórios da aplicação devem ser clonados dentro de um mesmo diretório, que servirá como a raiz do seu ambiente de desenvolvimento.

A estrutura de pastas final deve ser a seguinte:

```
/workspace/
├── tinnova-infrastructure/        (Este repositório)
├── tinnova-backend-top-api-gateway/
├── tinnova-backend-top-users/
├── tinnova-backend-top-finance/
├── tinnova-frontend-main/
├── tinnova-frontend-top-users/
└── tinnova-frontend-top-finance/
```

---

## 🚀 Guia de Instalação e Execução

Siga os passos abaixo para clonar todos os repositórios e subir a aplicação completa.

### Passo 1: Clonar os Repositórios

Primeiro, crie um diretório para o projeto e clone todos os repositórios necessários dentro dele.

```bash
# Crie e acesse a pasta principal
mkdir tinnova-projects
cd tinnova-projects

# Clone todos os 7 repositórios
git clone https://github.com/Jonatas-Felipe/tinnova-infrastructure.git
git clone https://github.com/Jonatas-Felipe/tinnova-backend-top-api-gateway.git
git clone https://github.com/Jonatas-Felipe/tinnova-backend-top-users.git
git clone https://github.com/Jonatas-Felipe/tinnova-backend-top-finance.git
git clone https://github.com/Jonatas-Felipe/tinnova-frontend-main.git
git clone https://github.com/Jonatas-Felipe/tinnova-frontend-top-users.git
git clone https://github.com/Jonatas-Felipe/tinnova-frontend-top-finance.git
```

### Passo 2: Configurar o Ambiente

O Docker Compose utiliza um arquivo `.env` para gerenciar as variáveis de ambiente, como portas e credenciais de banco de dados.

Dentro da pasta `tinnova-infrastructure`, crie uma cópia do arquivo de exemplo:

```bash
cd tinnova-infrastructure
cp .env.example .env
```
> O arquivo `.env` já contém valores padrão que devem funcionar para o ambiente de desenvolvimento local.

### Passo 3: Subir a Aplicação Completa

Com o Docker em execução na sua máquina, execute o seguinte comando de dentro da pasta `tinnova-infrastructure`:

```bash
docker compose up --build -d
```
- `--build`: Força a reconstrução das imagens Docker de cada serviço. Use-o na primeira vez ou sempre que houver alterações nos `Dockerfile`s.
- `-d` (detached): Executa os contêineres em segundo plano.

Aguarde alguns minutos para que todas as imagens sejam construídas e os contêineres iniciados. As migrações dos bancos de dados serão executadas automaticamente na inicialização dos backends.

---

## 🌐 Acessando os Serviços

Após a inicialização, os serviços estarão disponíveis nos seguintes endereços:

| Serviço | URL de Acesso |
| :--- | :--- |
| 🏠 **Frontend Principal (Host)** | [http://localhost:3000](http://localhost:3000) |
| 👤 **Microfrontend de Usuários** | [http://localhost:3001](http://localhost:3001) |
| 💰 **Microfrontend de Finanças**| [http://localhost:3002](http://localhost:3002) |
|  GATEWAY **API Gateway** | [http://localhost:3333](http://localhost:3333) |

---

## 🛠️ Gerenciando os Contêineres

Use os seguintes comandos (de dentro da pasta `tinnova-infrastructure`) para gerenciar seu ambiente:

- **Para parar todos os serviços:**
  ```bash
  docker compose down
  ```

- **Para ver os logs de um serviço específico em tempo real:**
  ```bash
  # Exemplo para a API de usuários
  docker compose logs -f top-users
  ```

- **Para ver o status de todos os contêineres:**
  ```bash
  docker compose ps
  ```