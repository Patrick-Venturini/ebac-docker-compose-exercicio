# 🐳 Docker Compose com Cypress

Projeto desenvolvido para estudos e prática de **Docker, Docker Compose e automação de testes com Cypress**, utilizando uma aplicação integrada com testes de API e interface.

## 📋 O que é este projeto?

O objetivo deste projeto é praticar a criação de um ambiente de testes containerizado, onde aplicação e testes são executados de forma integrada através do Docker Compose.

O ambiente é composto por:

- ✅ Aplicação Hub de Leitura
- ✅ Testes automatizados de API com Cypress
- ✅ Testes automatizados de UI com Cypress
- ✅ Dockerfiles para criação das imagens
- ✅ Docker Compose para orquestração dos containers
- ✅ Comunicação entre containers através de uma rede Docker
- ✅ Persistência de vídeos e screenshots dos testes

---

## 🛠️ Tecnologias utilizadas

- Docker
- Docker Compose
- Cypress
- JavaScript
- Cucumber / Gherkin
- Git
- GitHub

---

## 📂 Estrutura do projeto

```text
ebac-docker-compose-exercicio/
│
├── ebac-hub-de-leitura-integrado/
│   └── Aplicação utilizada nos testes
│
├── task-hub-de-leitura-api-cypress-test/
│   └── Testes automatizados de API com Cypress
│
├── ebac-cypress-bdd-cucumber/
│   └── Testes automatizados de UI com Cypress + Cucumber
│
├── cypress-videos/
│   ├── api/
│   └── ui/
│
├── cypress-screenshots/
│   ├── api/
│   └── ui/
│
└── docker-compose.yml
```

---

## 🐳 Docker Compose

O arquivo `docker-compose.yml` é responsável por construir e executar os serviços necessários para o ambiente de testes.

São utilizados três serviços principais:

### `backend-frontend`

Responsável por executar a aplicação utilizada durante os testes.

```text
http://localhost:3000
```

### `cypress-api`

Executa os testes automatizados da API.

Dentro da rede Docker, os testes acessam a aplicação através de:

```text
http://backend-frontend:3000/api/
```

### `cypress-ui`

Executa os testes automatizados de interface após a conclusão dos testes de API.

Dentro da rede Docker, os testes utilizam:

```text
http://backend-frontend:3000/
```

---

## 🔗 Comunicação entre containers

Os containers utilizam uma rede Docker do tipo `bridge` chamada:

```text
hub-network
```

A estrutura simplificada do ambiente é:

```text
                hub-network
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
 backend-frontend  cypress-api  cypress-ui
      :3000
```

Dessa forma, os testes não precisam acessar a aplicação através de `localhost`, utilizando diretamente o nome do serviço Docker.

---

## 🚀 Executando o projeto

Na raiz do projeto, execute:

```bash
docker compose up --build
```

O Docker Compose irá:

1. Construir a imagem da aplicação
2. Iniciar a aplicação
3. Executar os testes de API
4. Executar os testes de UI após a conclusão dos testes de API

Para encerrar e remover os containers:

```bash
docker compose down
```

---

## 📹 Evidências dos testes

Os resultados dos testes são disponibilizados através de volumes Docker.

### Testes de API

```text
cypress-videos/api/
cypress-screenshots/api/
```

### Testes de UI

```text
cypress-videos/ui/
cypress-screenshots/ui/
```

Isso permite acessar vídeos e screenshots gerados pelo Cypress mesmo após a finalização dos containers.

---

## 🎯 Principais conceitos praticados

Este projeto foi utilizado para praticar conceitos relacionados a:

- Criação de imagens Docker
- Criação e utilização de `Dockerfile`
- Orquestração de múltiplos containers com Docker Compose
- Comunicação entre containers
- Redes Docker
- Variáveis de ambiente
- Volumes
- Dependência entre serviços
- Execução de testes Cypress dentro de containers
- Testes automatizados de API
- Testes automatizados de UI
- Integração entre aplicação e automação de testes

---

## 👨‍💻 Autor

**Patrick Venturini**

Projeto desenvolvido durante os estudos de **Quality Assurance, Automação de Testes e Docker**.

**Repositório:**  
https://github.com/Patrick-Venturini/ebac-docker-compose-exercicio
