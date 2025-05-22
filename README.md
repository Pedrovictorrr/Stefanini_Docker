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

### 4. Acesse a aplicação

- **Frontend:** [http://localhost:8080](http://localhost:8080)
- **Backend (API):** [http://localhost:8000](http://localhost:8000)

### 5. Observações

- O arquivo `.env` da API é gerado automaticamente com as variáveis necessárias.
- O banco de dados é inicializado automaticamente.
- Para instalar dependências PHP manualmente, utilize o serviço `composer`:
  ```bash
  docker-compose run --rm composer install
  ```
- Para rodar as migrations do Laravel manualmente, execute:
  ```bash
  docker exec projetos-api php artisan migrate --seed
  ```

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
