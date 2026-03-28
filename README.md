# AV1 - AutoManager

Microserviço Spring Boot para gerenciamento de clientes, documentos, endereços e telefones, utilizando persistência em banco de dados MySQL.

---

## Como executar o projeto

### 1. Clone o repositório

---

### 2. Configuração do banco de dados

#### 2.1 Configure o arquivo `application.properties`
Certifique-se de que as credenciais do seu banco de dados local estejam corretas:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/automanager?createDatabaseIfNotExist=true
spring.datasource.username=SEU_USUARIO
spring.datasource.password=SUA_SENHA
spring.jpa.hibernate.ddl-auto=create
spring.jpa.show-sql=true
```

* O banco de dados `automanager` será criado automaticamente na primeira execução, caso não exista.
* Sempre que vc rodar novamente o banco será criado do ZERO, então lembre-se disso.

---

### 3. Execução da aplicação

Execute o Application através da sua IDE de preferência:
`src/main/java/com/autobots/automanager/AutomanagerApplication.java`

A API estará disponível localmente na porta padrão (8080).

---

### 4. Teste das rotas

Ferramentas recomendadas para teste: Insomnia ou Postman.
<br>
Atenção: Para as rotas de atualização (PUT) e exclusão (DELETE), os IDs devem ser enviados obrigatoriamente dentro do corpo da requisição (JSON).

---

# Cliente
Base URL: `/cliente`

### GET (Listar e Buscar)
* Listar todos: `GET localhost:8080/cliente`
* Buscar por ID: `GET localhost:8080/cliente/{id}`

### POST (Cadastrar)
`POST localhost:8080/cliente/cadastro`

```json
{
  "nome": "Ana Clara da Silva",
  "nomeSocial": "Ana",
  "dataNascimento": "1995-08-22T00:00:00.000+00:00"
}
```

### PUT (Atualizar)
`PUT localhost:8080/cliente/atualizar`

```json
{
  "id": 1,
  "nome": "Ana Clara da Silva Souza"
}
```

### DELETE (Excluir)
`DELETE localhost:8080/cliente/excluir`

```json
{
  "id": 1
}
```

---

# Documento
Base URL: `/documento`

### GET (Listar e Buscar)
* Listar todos: `GET localhost:8080/documento`
* Buscar por ID: `GET localhost:8080/documento/{id}`

### POST (Cadastrar)
`POST localhost:8080/documento/cadastro`

```json
{
  "tipo": "CNH",
  "numero": "98765432100"
}
```

### PUT (Atualizar)
`PUT localhost:8080/documento/atualizar`

```json
{
  "id": 1,
  "numero": "11223344556"
}
```

### DELETE (Excluir)
`DELETE localhost:8080/documento/excluir`

```json
{
  "id": 1
}
```

---

# Endereço
Base URL: `/endereco`

### GET (Listar e Buscar)
* Listar todos: `GET localhost:8080/endereco`
* Buscar por ID: `GET localhost:8080/endereco/{id}`

### POST (Cadastrar)
`POST localhost:8080/endereco/cadastro`

```json
{
  "estado": "PR",
  "cidade": "Curitiba",
  "bairro": "Centro Cívico",
  "rua": "Avenida Cândido de Abreu",
  "numero": "420",
  "codigoPostal": "80530000",
  "informacoesAdicionais": "Sala 15"
}
```

### PUT (Atualizar)
`PUT localhost:8080/endereco/atualizar`

```json
{
  "id": 1,
  "informacoesAdicionais": "Sala 15 - Bloco B"
}
```

### DELETE (Excluir)
`DELETE localhost:8080/endereco/excluir`

```json
{
  "id": 1
}
```

---

# Telefone
Base URL: `/telefone`

### GET (Listar e Buscar)
* Listar todos: `GET localhost:8080/telefone`
* Buscar por ID: `GET localhost:8080/telefone/{id}`

### POST (Cadastrar)
`POST localhost:8080/telefone/cadastro`

```json
{
  "ddd": "41",
  "numero": "999887766"
}
```

### PUT (Atualizar)
`PUT localhost:8080/telefone/atualizar`

```json
{
  "id": 1,
  "numero": "988776655"
}
```

### DELETE (Excluir)
`DELETE localhost:8080/telefone/excluir`

```json
{
  "id": 1
}
```

---

## Observações Finais
* O cadastro e a exclusão em cascata (Cascade) estão configurados. Tenha cuidado ao excluir registros independentes que já estejam vinculados a um Cliente.
