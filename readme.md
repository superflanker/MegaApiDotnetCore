# Documentação do Projeto Megaman API

## Visão Geral
O projeto Megaman API é uma aplicação desenvolvida em .NET Core 3.1 que fornece informações sobre os chefes ("bosses") da franquia Megaman. A API retorna dados no formato JSON contendo informações sobre cada chefe, incluindo ID, código, nome, pontos de vida (HP) e imagem.

## Estrutura do Projeto
A estrutura do projeto segue a organização abaixo:

```
.vs/
.vscode/
bin/
Controllers/
Database/
middlewares/
Models/
obj/
Properties/
Services/
appsettings.Development.json
appsettings.json  
global.json
MegamanApi.csproj  
MegamanApi.sln
Program.cs
Startup.cs
```

## Dependências do Projeto

| Pacote | Versão | Link |
|--------|--------|------|
| Microsoft.EntityFrameworkCore | 3.1.8 | [EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/3.1.8) |
| Microsoft.EntityFrameworkCore.Design | 3.1.8 | [EntityFrameworkCore.Design](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Design/3.1.8) |
| Microsoft.EntityFrameworkCore.SqlServer | 3.1.8 | [EntityFrameworkCore.SqlServer](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.SqlServer/3.1.8) |
| Newtonsoft.Json | 12.0.2 | [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/12.0.2) |

## Endpoints da API

### 1. Listar Todos os Robôs
**Endpoint:** `GET api/v1/robots`  
**Descrição:** Retorna todos os robôs cadastrados no sistema.

**Resposta Exemplo:**
```json
[
  {
    "Id": 1,
    "Code": "DLN/DRN-003",
    "Name": "Cutman",
    "HP": 150,
    "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
  }
]
```

### 2. Obter Robô por ID
**Endpoint:** `GET api/v1/robots/{id}`  
**Descrição:** Retorna um robô específico com base no ID.

**Resposta Exemplo:**
```json
{
  "Id": 1,
  "Code": "DLN/DRN-003",
  "Name": "Cutman",
  "HP": 150,
  "Picture": "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
}
```

Caso o robô não seja encontrado:
```json
{
  "message": "Nenhum robo encontrado"
}
```

### 3. Criar um Novo Robô
**Endpoint:** `POST api/v1/robots`  
**Descrição:** Endpoint para a criação de um novo robô (implementação pendente).

## Explicação das Técnicas Utilizadas

### 1. **.NET Core 3.1**
O projeto utiliza .NET Core 3.1 para desenvolvimento da API, garantindo modularidade, segurança e compatibilidade multiplataforma.

### 2. **Entity Framework Core**
O Entity Framework Core (EF Core) é utilizado como ORM (Object-Relational Mapping) para facilitar a interação com o banco de dados SQL Server, permitindo a abstração das consultas SQL.

### 3. **Arquitetura em Camadas**
A organização em pastas segue o padrão de separação de responsabilidades:
- `Controllers/` - Contém os controladores responsáveis por definir os endpoints da API.
- `Database/` - Responsável pela configuração e interação com o banco de dados.
- `Middlewares/` - Contém middlewares personalizados, se necessário.
- `Models/` - Contém as classes de modelo utilizadas pelo EF Core.
- `Services/` - Implementação da lógica de negócio da aplicação.

### 4. **Newtonsoft.Json**
A biblioteca Newtonsoft.Json é utilizada para serialização e desserialização de objetos JSON, garantindo compatibilidade e flexibilidade no manuseio de dados.

### 5. **Dependency Injection**
A API segue os princípios de injeção de dependência (Dependency Injection), permitindo a separação entre a lógica de negócio e a camada de controle, tornando o código mais modular e testável.

### 6. **Data Trasfer Objects**

A API utiliza DTOs (Data Transfer Objects) para garantir que apenas os dados necessários sejam expostos ao cliente, evitando exposição desnecessária de entidades do banco de dados.