# 🥟 API REST - Baozi Store

> **Atividade Prática de Desenvolvimento Web Back-End**  
> **Instituição**: Centro Universitário UNINTER  
> **Disciplina**: Desenvolvimento Web Back-End  
> **Professora**: Luciane Kanashiro, Me.  
> **Estudante**: Yuki Fernando Miura  
> **RU**: 4976495  

---

## 📌 Descrição do Estudo de Caso

A **Baozi Store** é uma pequena loja local voltada à venda de pãozinho chinês (*baozi*). Para informatizar o controle de seu negócio, foi desenvolvida uma **API REST** simplificada utilizando a arquitetura MVC do Spring Boot. 

A API permite gerenciar o cadastro de clientes, o catálogo de produtos e o registro de pedidos simples (em que um cliente adquire determinado produto em certa quantidade).

---

## 🚀 Tecnologias Utilizadas

- **Linguagem**: Java 17 / 21
- **Framework**: Spring Boot 4.1.1 (Spring Web MVC)
- **Persistência de Dados**: Spring Data JPA / Hibernate
- **Banco de Dados**: H2 Database (Banco de dados relacional em memória)
- **Gerenciador de Dependências**: Apache Maven
- **Testes de Endpoints**: Postman

---

## 📐 Arquitetura do Projeto

O projeto foi estruturado seguindo as melhores práticas do padrão **MVC (Model-View-Controller)** adaptado para APIs REST:

```text
demo/src/main/java/com/example/demo/
├── model/           # Entidades JPA (Mapeamento Relacional)
│   ├── Cliente.java
│   ├── Produto.java
│   └── Pedido.java
├── repository/      # Interfaces Spring Data JPA (Acesso a Dados)
│   ├── ClienteRepository.java
│   ├── ProdutoRepository.java
│   └── PedidoRepository.java
└── controller/      # REST Controllers (Endpoints HTTP JSON)
    ├── ClienteController.java
    ├── ProdutoController.java
    └── PedidoController.java
```

---

## 📊 Entidades e Atributos

### 1. `Cliente` (`tb_cliente`)
- `id` (`Long`): Chave primária gerada automaticamente por autoincremento (`@Id`, `@GeneratedValue`).
- `nome` (`String`): Nome do cliente (ex: `Yuki4976495`).
- `clienteDesde` (`LocalDate`): Data de cadastro do cliente no sistema.

### 2. `Produto` (`tb_produto`)
- `id` (`Long`): Chave primária gerada automaticamente por autoincremento (`@Id`, `@GeneratedValue`).
- `nome` (`String`): Nome do produto (ex: `Baozi Tradicional`).
- `preco` (`BigDecimal`): Preço unitário do produto (ex: `12.50`).
- `estoque` (`Boolean`): Indicador de disponibilidade em estoque (`true`/`false`).

### 3. `Pedido` (`tb_pedido`)
- `id` (`Long`): Chave primária gerada automaticamente por autoincremento (`@Id`, `@GeneratedValue`).
- `clienteId` (`Long`): ID do cliente que realizou a compra.
- `produtoId` (`Long`): ID do produto comprado.
- `quantidade` (`Integer`): Quantidade de unidades solicitadas.

---

## 🌐 Endpoints da API REST

### Clientes (`/clientes`)
| Método | Endpoint | Descrição | Status HTTP |
| :--- | :--- | :--- | :--- |
| `POST` | `/clientes` | Cadastrar novo cliente | `201 Created` |
| `GET` | `/clientes` | Listar todos os clientes | `200 OK` |
| `GET` | `/clientes/{id}` | Consultar cliente por ID | `200 OK` / `404 Not Found` |
| `DELETE` | `/clientes/{id}` | Apagar cliente por ID | `204 No Content` / `404 Not Found` |

### Produtos (`/produtos`)
| Método | Endpoint | Descrição | Status HTTP |
| :--- | :--- | :--- | :--- |
| `POST` | `/produtos` | Cadastrar novo produto | `201 Created` |
| `GET` | `/produtos` | Listar todos os produtos | `200 OK` |
| `GET` | `/produtos/{id}` | Consultar produto por ID | `200 OK` / `404 Not Found` |
| `DELETE` | `/produtos/{id}` | Apagar produto por ID | `204 No Content` / `404 Not Found` |

### Pedidos (`/pedidos`)
| Método | Endpoint | Descrição | Status HTTP |
| :--- | :--- | :--- | :--- |
| `POST` | `/pedidos` | Registrar novo pedido | `201 Created` |
| `GET` | `/pedidos` | Listar todos os pedidos | `200 OK` |
| `GET` | `/pedidos/{id}` | Consultar pedido por ID | `200 OK` / `404 Not Found` |
| `DELETE` | `/pedidos/{id}` | Apagar pedido por ID | `204 No Content` / `404 Not Found` |

---

## ⚙️ Como Executar o Projeto Localmente

### Pré-requisitos
- **Java Development Kit (JDK 17 ou superior)** instalado.

### Passo a Passo
1. Clone o repositório ou navegue até a pasta do projeto:
   ```bash
   cd demo
   ```
2. Execute o projeto utilizando o Maven Wrapper:
   - **No Windows (PowerShell/CMD)**:
     ```powershell
     .\mvnw.cmd spring-boot:run
     ```
   - **No Linux/Mac**:
     ```bash
     ./mvnw spring-boot:run
     ```
3. A aplicação estará ativa em: **`http://localhost:8080`**.

---

## 🛢️ Acesso ao Console do Banco de Dados H2

Com a aplicação rodando, acesse o painel visual do H2 Console pelo navegador:
- **URL**: [http://localhost:8080/h2-console](http://localhost:8080/h2-console)
- **JDBC URL**: `jdbc:h2:mem:baozidb`
- **User Name**: `sa`
- **Password**: *(deixar em branco)*

---

## 🧪 Exemplos de Requisições JSON para Testes (Postman)

### 1. Cadastrar Cliente (`POST /clientes`)
```json
{
  "nome": "Yuki4976495",
  "clienteDesde": "2026-10-05"
}
```

### 2. Cadastrar Produto (`POST /produtos`)
```json
{
  "nome": "Pãozinho Baozi Tradicional",
  "preco": 12.50,
  "estoque": true
}
```

### 3. Registrar Pedido (`POST /pedidos`)
```json
{
  "clienteId": 1,
  "produtoId": 1,
  "quantidade": 5
}
```
