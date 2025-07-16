# ByteShop

**ByteShop** é um projeto de e‑commerce de eletrônicos desenvolvido com Angular no frontend e NestJS + TypeORM + PostgreSQL no backend, containerizado com Docker. O objetivo deste repositório é servir como base didática para aprendizado dos fluxos e tecnologias de um e‑commerce real.

---

## 📦 Stack Tecnológico

* **Frontend**: Angular 16
* **Backend**: NestJS 10, TypeORM
* **Banco de Dados**: PostgreSQL
* **Containerização**: Docker & Docker Compose
* **APIs**: REST e GraphQL (Apollo Server)
* **Autenticação**: JWT (Passport)
* **CI/CD**: GitHub Actions (opcional)

---

## 🚀 Funcionalidades Principais

1. **Listagem e Detalhe de Produtos** (filtros por categoria, preço, marca)
2. **Carrinho de Compras** (adicionar, remover, atualizar quantidades)
3. **Checkout e Pedidos** (simulação de pagamento via API)
4. **Autenticação de Usuário** (JWT) e módulo de autorização
5. **Painel Administrativo** (CRUD de produtos, categorias, pedidos)
6. **Wishlist** (lista de desejos)
7. **Avaliação de Produtos** (notas e comentários)
8. **Cupons de Desconto**
9. **Relatórios** (vendas por período, produtos mais vendidos)

---

## 📂 Estrutura do Repositório

```
/                     # Raiz do monorepo (Nx Workspace)
├── frontend/         # Aplicação Angular
│   ├── src/
│   ├── angular.json
│   ├── package.json
│   └── ...
├── backend/          # Aplicação NestJS
│   ├── src/
│   ├── Dockerfile
│   ├── tsconfig.json
│   ├── package.json
│   └── ...
├── libs/             # Bibliotecas compartilhadas (opcionais)
│   └── shared-models/
├── docker-compose.yml
├── .env.example      # Variáveis de ambiente de exemplo
└── README.md
```

---

## 🔧 Requisitos

* Node.js v18+
* Docker & Docker Compose
* Git

---

## ⚙️ Configuração e Execução

1. **Clone o repositório**

   ```bash
   git clone https://github.com/seu-usuario/byteshop.git
   cd byteshop
   ```

2. **Configure as variáveis de ambiente**

   ```bash
   cp .env.example .env
   # Edite .env e defina:
   #  - POSTGRES_HOST, POSTGRES_PORT, POSTGRES_USER, POSTGRES_PASSWORD, POSTGRES_DB
   #  - JWT_SECRET, FRONTEND_URL
   ```

3. **Inicie os containers Docker**

   ```bash
   docker-compose up --build
   ```

   * **frontend** em: `http://localhost:4200`
   * **backend REST** em: `http://localhost:3000/api`
   * **GraphQL Playground** em: `http://localhost:3000/graphql`
   * **Adminer (DB)** em: `http://localhost:8080`

4. **Em desenvolvimento**

   * **Frontend**: no diretório `frontend/`

     ```bash
     npm install
     npm start
     ```
   * **Backend**: no diretório `backend/`

     ```bash
     npm install
     npm run start:dev
     ```

---

## 📡 Endpoints

### REST

* `POST /api/auth/login` — Autenticação JWT
* `POST /api/auth/register` — Cadastro de usuário
* `GET  /api/products` — Listar produtos
* `GET  /api/products/:id` — Detalhe de produto
* `POST /api/cart` — Adicionar ao carrinho
* `POST /api/orders` — Criar pedido
* **...** (Documentação Swagger em `/api/docs`)

### GraphQL

Acesse o Playground em `/graphql` e use queries/mutations como:

```graphql
# Exemplo de consulta de produto + avaliações
query {
  product(id: 1) {
    id
    name
    price
    reviews {
      rating
      comment
    }
  }
}
```

---

## 🐳 Docker

O `docker-compose.yml` define 3 serviços:

* **db**: PostgreSQL
* **backend**: NestJS (porta 3000)
* **frontend**: Angular (porta 4200)

Você pode escalar, adicionar serviços (Redis, Elasticsearch) ou configurar volumes conforme desejar.

---

## ☁️ Deploy

Sugestão de fluxo:

1. **Frontend** no Vercel (ou Netlify) apontando para `frontend/`.
2. **Backend** Docker no Render, Railway ou Heroku.
3. Defina variáveis de ambiente nos serviços de deploy.
4. Habilite CI/CD para deploy automático a cada push.

---

## 🤝 Contribuições

1. Faça um fork deste repositório
2. Crie uma branch `feature/nome-da-sua-feature`
3. Faça suas alterações e commit (`git commit -m 'feat: descrição'`)
4. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para detalhes.
