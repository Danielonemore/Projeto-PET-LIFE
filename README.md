# Projeto {CLÍNICA VETERINÁRIA- PET LIFE} - Backend (trabalho-api)

## Descrição

{API para o Sistema de Gerenciamento da Clínica Veterinária - PetLife. Essa API permite o gerenciamento de animais, donos, médicos veterinários, consultas, exames, agendamentos e muito mais.
}

## Tecnologias Utilizadas

- Spring Boot: 3.3.4
- H2 Database: 2.1.214
- Lombok: 1.18.24
- MapStruct: 1.6.2
- Springdoc OpenAPI: 2.6.0
- Therapi Runtime Javadoc: 0.15.0
- Jacoco: 0.8.12
- Maven Compiler Plugin: 3.8.1

## Pré-requisitos

- JDK: 17
- Maven: 3.8.6

## Instalação

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/Danielonemore/Projeto-PET-LIFE.git
   ```

2. **Navegue até o diretório do projeto:**

   ```bash
   cd diretorio-do-projeto
   ```

3. **Configure o banco de dados:**

   Edite o arquivo [application.yaml](src/main/resources/application.yaml) com as configurações do seu banco de dados.

4. **Compile e execute o projeto:**

   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

   A API estará disponível em `http://localhost:8080`.

## Documentação da API (Swagger)

A documentação da API pode ser acessada por meio do Swagger. Após iniciar o backend, você pode acessar a documentação por meio da seguinte URL:

[/swagger-ui/index.html](https://app.swaggerhub.com/apis/DANIELFPDOSSANTOS17/PetLife/1.0.0#/Veterinario)

## Endpoints

Abaixo está a descrição dos principais endpoints da API:

### **Pacientes (Animais)**
### **1. GET /api/pacientes**

- **Descrição:** Retorna uma lista de pacientes (animais).
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK**
    ```json
    [
      {
         "nome": "Rex",
         "especie": "Cachorro",
         "raca": "Labrador",
         "idade": 3,
         "sexo": "Macho",
         "historicoMedico": "Histórico de vacina e consultas."
      },
      // ...
    ]
    ```

### **2. POST /api/pacientes**

- **Descrição:** Cadastra um novo paciente (animal).
- **Corpo da Requisição:**
- **Resposta:**
  - **200 OK** Lista de pacientes.
  ```json
  {
     "nome": "Rex",
     "especie": "Cachorro",
     "raca": "Labrador",
     "idade": 3,
     "sexo": "Macho",
     "historicoMedico": "Histórico de vacina e consultas."
  }
  ```
- **Resposta:**
  - **201 Created** Paciente cadastrado com sucesso.
    ```json
    {

      "nome": "Rex",
      "especie": "Cachorro",
      "raca": "Labrador",
      "idade": 3,
      "sexo": "Macho",
      "historicoMedico": "Histórico de vacina e consultas."
    }
    ```

### **3. GET /api/pacientes/{id}**

- **Descrição:** Retorna os detalhes de um paciente específico.
- **Parâmetros de Caminho:**`id`- ID do paciente.
- **Resposta:**
  - **200 OK** (Detalhes do paciente.)
    ```json
    {
      "nome": "Rex Atualizado",
      "especie": "Cachorro",
      "raca": "Labrador",
      "idade": 4
    }
    ```
  - **404 Not Found** (Caso o paciente não seja encontrado.)

### **4. PUT /api/pacientes/{id}**

- **Descrição:** Atualiza as informações de um paciente existente.
- **Corpo da Requisição:**
  ```json
  {
    "nome": "Rex",
    "especie": "Cachorro",
    "raca": "Labrador",
    "idade": 3
  }
  ```
- **Parâmetros de Caminho:**
- **Resposta:**
  - **200 OK**
    ```json
    {
      "nome": "Rex Atualizado",
      "especie": "Cachorro",
      "raca": "Labrador",
      "idade": 4
    }
    ```
  - **404 Not Found** (se o paciente não for encontrado)


### **5.DELETE /api/pacientes/{id}**

- **Descrição:** Remove um paciente (animal) pelo ID.
- **Parâmetros de Caminho:**
  - `id`: ID do paciente.
- **Resposta:**
  - **204 No Content**
   ```json
   {
      "id": 1,
      "nome": "Rex",
      "especie": "Cachorro",
      "raca": "Labrador",
      "idade": 4
    }
    ```
  - **404 Not Found** (se o paciente não for encontrado)

### **Donos (Responsáveis)**
### **1.GET /api/donos**

- **Descrição:**  Retorna uma lista de donos.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Lista de donos.)
    ```json
    [
      {
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```

    ### **2.GET /api/donos**

- **Descrição:**  Cadastra um novo dono.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **201 Created** (Dono cadastrado com sucesso.)
    ```json
    [
      {
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    ### **3.GET /api/donos/{id}**


- **Descrição:**   Retorna os detalhes de um dono específico.
- **Parâmetros de Consulta:** `id`- ID do dono.
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Detalhes do dono.)
    ```json
    [
      {
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** (Dono não encontrado.)


     ### **4.PUT /api/donos/{id}**

- **Descrição:**  Atualiza os dados de um dono existente.
- **Parâmetros de Consulta:** 
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Dono atualizado com sucesso.)
    ```json
    [
      {
        "nome": "João Atualizado",
        "endereco": "Rua das Palmeiras, 456"
      },
      // ...
    ]
    ```
    - **404 Not Found** (Dono não encontrado.)

    ### **5.DELETE /api/donos/{id}**

- **Descrição:**  Remove um dono pelo ID.
- **Parâmetros de Consulta:** 
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Content** (Dono removido.)
    ```json
    [
      {
        "id": 1,
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** ( Dono não encontrado.)
    
### **Consultas**
### **1.GET /api/consultas**

- **Descrição:**  Retorna uma lista de consultas agendadas.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Lista de consultas.)
    ```json
    [
      {
        "pacienteId": 1,
        "veterinarioId": 1,
        "dataHora": "2024-10-20T10:00:00",
        "descricaoConsulta": "Consulta de rotina"
      },
      // ...
    ]
    ```

  ### **2.OST /api/consultas**

- **Descrição:**  Agenda uma nova consulta.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Created** (Consulta agendada com sucesso.)
    ```json
    [
      {
        "pacienteId": 1,
        "veterinarioId": 1,
        "dataHora": "2024-10-20T10:00:00",
        "descricaoConsulta": "Consulta de rotina"
      },
      // ...
    ]
    ```
    
    ### **3.GET /api/consultas/{id}**

- **Descrição:**  Retorna os detalhes de uma consulta específica.
- **Parâmetros de Consulta:** `id` - ID do consulta.
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Detalhes da consulta.)
    ```json
    [
      {
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** (Consulta não encontrada.)


     ### **4.PUT /api/consultas/{id}**

- **Descrição:**   Atualiza os dados de uma consulta existente.
- **Parâmetros de Consulta:** 
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Consulta atualizada.)
    ```json
    [ 
      {
        "dataHora": "2024-10-20T15:00:00",
        "descricaoConsulta": "Consulta de retorno"
      },
      // ...
    ]
    ```
    - **404 Not Found** (Consulta não encontrada)


     ### **5.DELETE /api/consultas/{id}**

- **Descrição:**  Remove uma consulta pelo ID.
- **Parâmetros de Consulta:** 
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Content** (Consulta removida.)
    ```json
    [
      {
        "id": 1 ,
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** ( Consulta não encontrada.)

### **Serviços**
### **1.GET /api/servicos**

- **Descrição:**  Retorna uma lista de serviços oferecidos pela clínica.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Lista de serviços.)
    ```json
    [
      {
        "nome": "Banho",
        "preco": 50.00,
        "descricao": "Banho completo para animais de pequeno porte."
      },
      // ...
    ]
    ```

     ### **2.POST /api/servicos**

- **Descrição:** Cadastra um novo serviço.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Created** ( Serviço cadastrado com sucesso.)
    ```json
    [
      {
         "nome": "Tosa",
         "preco": 90.00,
         "descricao": "Tosa completa para animais de pequeno porte."
      },
      // ...
    ]
    ´´´

### **3.GET /api/servicos/{id}**

- **Descrição:**  Retorna os detalhes de um serviço específico.
- **Parâmetros de Consulta:** `id` - ID do serviço.
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Detalhes do serviço.)
    ```json
    [
      {
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** (Serviço não encontrado.)

    ### **4.PUT /api/servicos/{id}**

- **Descrição:**  Atualiza os dados de um serviço existente.
- **Parâmetros de Consulta:** 
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Serviço atualizado com sucesso.)
    ```json
    [ 
      {
        "nome": "Banho Completo",
        "preco": 55.00
      },
      // ...
    ]
    ```
    - **404 Not Found** (Serviço não encontrado.)

    ### **5.DELETE /api/servicos/{id}**

- **Descrição:**  Remove um serviço pelo ID.
- **Parâmetros de Consulta:** 
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Content** (Serviço removido.)
    ```json
    [
      {
        "id": 1 ,
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** ( Serviço não encontrado.)

    ### **Estoque**
### **1.GET /api/estoque**

- **Descrição:**  Retorna uma lista de itens no estoque.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Lista de serviços.)
    ```json
    [
      {
         "id": 1,
         "nome": "Ração para Cães",
         "quantidade": 50,
         "preco": 120.00
      },
         {
          "id": 2,
          "nome": "Vacina Antirrábica",
          "quantidade": 30,
          "preco": 70.00
       }


      // ...
    ]
    ```

    ### **2.POST /api/estoque**

- **Descrição:**  Adiciona um novo item ao estoque.
- **Parâmetros de Consulta:**
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Created** ( Serviço cadastrado com sucesso.)
    ```json
    [
      {
         "nome": "Ração para Gatos",
         "quantidade": 20,
         "preco": 80.00
      },
      // ...
    ]

### **3.GET GET /api/estoque/{id}**

- **Descrição:**  Retorna os detalhes de um item específico do estoque.
- **Parâmetros de Consulta:** `id` - ID do  item.
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Detalhes do serviço.)
    ```json
    [
      {
          "id": 1,
          "nome": "Ração para Cães",
          "quantidade": 50,
          "preco": 120.00
      },
      // ...
    ]
    ```
    - **404 Not Found** (se o item não for encontrado.)

     ### **4.PUT PUT /api/estoque/{id}**

- **Descrição:**  Atualiza as informações de um item existente no estoque.
- **Parâmetros de Consulta:** `id`- ID do item.
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 OK** (Estoque atualizado com sucesso.)
    ```json
    [ 
      {
          "id": 1,
          "nome": "Ração para Cães - Premium",
          "quantidade": 45,
          "preco": 150.00

      },
      // ...
    ]
    ```
    - **404 Not Found** (se o item não for encontrado.)

### **5.DELETE /api/servicos/{id}**

- **Descrição:**  Remove um item do estoque pelo ID.
- **Parâmetros de Consulta:** `id`- ID do item.
  - `page` (opcional): Número da página.
  - `size` (opcional): Número de itens por página.
- **Resposta:**
  - **200 Content** (Item removido.)
    ```json
    [
      {
        "id": 1 ,
        "nome": "João Silva",
        "endereco": "Rua das Flores, 123, São Paulo",
        "contato": "contato@exemplo.com",
        "informacoesPagamento": "Cartão de Crédito"
      },
      // ...
    ]
    ```
    - **404 Not Found** ( se o item não for encontrado.)