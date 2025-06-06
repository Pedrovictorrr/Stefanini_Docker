# Stefanini Docker

Este projeto orquestra a aplicação Stefanini (API + Cliente Web) utilizando Docker Compose.

## Repositórios

- API: [Stefanini_API](https://github.com/Pedrovictorrr/Stefanini_API.git)
- Cliente Web: [Stefanini_Client](https://github.com/Pedrovictorrr/Stefanini_Client.git)
- Docker Compose: [Stefanini_Docker](https://github.com/Pedrovictorrr/Stefanini_Docker.git)

## Passos para rodar o projeto

### 1. Clone os repositórios

```bash
git clone https://github.com/Pedrovictorrr/Stefanini_API.git StefaniniAPI
git clone https://github.com/Pedrovictorrr/Stefanini_Client.git StefaniniWEB
git clone https://github.com/Pedrovictorrr/Stefanini_Docker.git StefaniniDocker
```

Certifique-se de que as pastas estejam assim:
```
.
├── StefaniniAPI
├── StefaniniWEB
└── StefaniniDocker
```

### 2. Acesse a pasta do Docker Compose

```bash
cd StefaniniDocker
```

### 3. Suba os containers

```bash
docker-compose up -d --build   
```

Isso irá:
- Construir e rodar a API Laravel (PHP) em `localhost:8000`
- Subir o banco de dados MySQL em `localhost:3306`
- Construir e rodar o cliente Flutter Web em `localhost:8080`

### 4. Rode as migrations do Laravel

Após subir os containers, execute o comando abaixo para rodar as migrations e popular o banco de dados:

```bash
docker exec projetos-api php artisan migrate --seed
```

### 5. Acesse a aplicação

- **Frontend:** [http://localhost:8080](http://localhost:8080)
- **Backend (API):** [http://localhost:8000](http://localhost:8000)

### 6. Observações

- O arquivo `.env` da API é gerado automaticamente com as variáveis necessárias.
- O banco de dados é inicializado automaticamente, mas é necessário rodar as migrations manualmente após subir os containers.

---

## Mini vídeo explicativo

Assista um vídeo rápido demonstrando o uso do projeto:

[https://youtu.be/Y57sX9abaXw](https://youtu.be/Y57sX9abaXw)

---

## Deploy e Monitoramento

### API Laravel

- **Deploy:** Realizado via [Laravel Forge](https://forge.laravel.com/) com URL de acesso: [https://stfiapi.pedrovfabreu.com.br](https://stfiapi.pedrovfabreu.com.br)
- **Testes Automatizados:** Os testes unitários são executados automaticamente via GitHub Actions a cada commit na branch `main`.
- **Painel Administrativo (Filament PHP):** Acesse o painel para visualizar logs e exceções:
  - URL: [https://stfiapi.pedrovfabreu.com.br](https://stfiapi.pedrovfabreu.com.br)
  - Usuário: `suporte@stefanini.com`
  - Senha: `suporte123`
  - > No painel Filament é possível visualizar projetos, usuários, arquivos de log e exceções.
- **Monitoramento de Erros:** O projeto está integrado ao [Sentry](https://stefanini-test.sentry.io) para captura e monitoramento de erros.

### Cliente Flutter

- **Hospedagem:** O frontend Flutter está hospedado no Firebase Hosting.
- **URL de acesso:** [https://stefanini.pedrovfabreu.com.br/](https://stefanini.pedrovfabreu.com.br/)
- **Credenciais de Teste:**
  - Usuário: `test@example.com`
  - Senha: `password`
- O frontend consome todas as rotas da API Laravel.

---

## Coleção Postman da API

Acesse a coleção Postman da API Laravel por este link:

[https://www.postman.com/security-saganist-39110096/stefanini-api/collection/k6uyyij/projetos-api](https://www.postman.com/security-saganist-39110096/stefanini-api/collection/k6uyyij/projetos-api)

---

## Testes Unitários da API Laravel

Para rodar os testes unitários da API, utilize o comando abaixo:

```bash
docker exec projetos-api php artisan test
```

Os testes estão localizados na pasta `tests/` do projeto Laravel.

---

## Organização do Projeto (Scrum/Sprint)

A organização das sprints e tarefas do teste foi realizada utilizando o GitHub Projects:

- [Quadro do Projeto no GitHub Projects](https://github.com/users/Pedrovictorrr/projects/6)

---
