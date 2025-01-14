# LiterAlura - Catálogo de Livros

Bem-vindo ao projeto **LiterAlura**, uma aplicação desenvolvida em Java com o framework Spring Boot para criar um catálogo de livros. O projeto permite realizar buscas de livros na API externa **Gutendex**, salvar os resultados em um banco de dados relacional PostgreSQL e realizar consultas a partir dos dados armazenados.

---

## **Sumário**

1. [Objetivos do Projeto](#objetivos-do-projeto)
2. [Funcionalidades](#funcionalidades)
3. [Tecnologias Utilizadas](#tecnologias-utilizadas)
4. [Configuração do Ambiente](#configuração-do-ambiente)
5. [Instalação e Configuração](#instalação-e-configuração)
6. [Endpoints da API](#endpoints-da-api)
7. [Exemplos de Uso](#exemplos-de-uso)
8. [Contribuições](#contribuições)

---

## **Objetivos do Projeto**

O projeto tem como objetivo consolidar conceitos como:

- Consumo de APIs externas com Java e Spring Boot.
- Persistência de dados em banco de dados relacional utilizando Spring Data JPA.
- Manipulação de dados em uma aplicação Spring Boot RESTful.
- Integração com o banco PostgreSQL.

---

## **Funcionalidades**

1. Buscar livros pelo título diretamente na API Gutendex e salvá-los no banco de dados.
2. Listar todos os livros cadastrados no banco de dados.
3. Listar autores registrados e seus respectivos livros.
4. Buscar autores ativos em um determinado ano.
5. Filtrar livros pelo idioma.

---

## **Tecnologias Utilizadas**

- **Linguagem:** Java 17
- **Framework:** Spring Boot
- **Dependências:**
  - Spring Web
  - Spring Data JPA
  - PostgreSQL Driver
  - Spring Boot DevTools
- **Banco de Dados:** PostgreSQL
- **Ferramentas:**
  - IntelliJ IDEA
  - Postman (para testar a API)

---

## **Configuração do Ambiente**

1. **Instalar o JDK 17:**
   - Baixe e instale o JDK 17 no site oficial da Oracle ou do OpenJDK.
   - Configure a variável de ambiente `JAVA_HOME`.

2. **Instalar o PostgreSQL:**
   - Baixe e instale o PostgreSQL a partir do [site oficial](https://www.postgresql.org/).
   - Configure um banco de dados chamado `literalura`.

3. **Instalar o Maven:**
   - Verifique se o Maven já está configurado corretamente no seu ambiente.
   - Para testar, execute o comando `mvn -v`.

4. **Configuração do IntelliJ IDEA:**
   - Importe o projeto e configure o SDK para Java 17.
   - Certifique-se de que o Maven esteja configurado como gerenciador de dependências.

---

## **Instalação e Configuração**

1. Clone o repositório do projeto:

   ```bash
   git clone https://github.com/seu-usuario/literalura.git
   cd literalura
   ```

2. Configure o arquivo `application.properties` localizado em `src/main/resources/` com as credenciais do seu banco PostgreSQL:

   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/literalura
   spring.datasource.username=seu_usuario
   spring.datasource.password=sua_senha
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
   spring.jpa.show-sql=true
   server.port=8080
   ```

3. Compile e execute o projeto:

   ```bash
   mvn spring-boot:run
   ```

4. Acesse a aplicação em: [http://localhost:8080](http://localhost:8080)

---

## **Endpoints da API**

### **1. Buscar Livro pelo Título**
- **Rota:** `POST /livros/buscar`
- **Descrição:** Consome a API Gutendex e salva o livro no banco de dados.
- **Corpo da Requisição:**

  ```json
  {
    "titulo": "Dom Casmurro"
  }
  ```

- **Resposta:**

  ```json
  {
    "id": 1,
    "titulo": "Dom Casmurro",
    "autor": "Machado de Assis",
    "idioma": "PT",
    "downloads": 12000
  }
  ```

---

### **2. Listar Todos os Livros**
- **Rota:** `GET /livros`
- **Descrição:** Retorna todos os livros cadastrados no banco de dados.
- **Resposta:**

  ```json
  [
    {
      "id": 1,
      "titulo": "Dom Casmurro",
      "autor": "Machado de Assis",
      "idioma": "PT",
      "downloads": 12000
    }
  ]
  ```

---

### **3. Listar Livros por Idioma**
- **Rota:** `GET /livros/idioma/{idioma}`
- **Exemplo:** `/livros/idioma/PT`
- **Descrição:** Retorna todos os livros cadastrados no idioma especificado.

---

## **Exemplos de Uso**

### **Buscar Livro na API Gutendex**
1. Envie uma requisição `POST` para `/livros/buscar` com o título desejado.
2. O livro será retornado e automaticamente salvo no banco de dados.

### **Listar Todos os Livros**
1. Envie uma requisição `GET` para `/livros`.
2. A resposta conterá todos os livros cadastrados.

### **Filtrar Livros por Idioma**
1. Envie uma requisição `GET` para `/livros/idioma/{idioma}` substituindo `{idioma}` pelo código do idioma (por exemplo, `PT`, `EN`).
2. A resposta listará os livros correspondentes ao idioma solicitado.

---

## **Contribuições**

Fique à vontade para contribuir com melhorias neste projeto. Abra uma *issue* ou envie um *pull request* no repositório.
Quem achar interessante e quiser utilizar o código, fique a vontade para utiliza-lo

---

