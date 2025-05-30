# Sistema de Gestão Acadêmica: Professores e Disciplinas

Este repositório contém um gerenciamento integrado de docentes e matrizes curriculares. A solução permite operações CRUD completas, associação dinâmica entre entidades e consultas estruturadas, desenvolvida com Express.js  e persistência de dados em MongoDB.

## Comandos Executados e Saídas

### Criar os Professores

#### Entrada:
```bash
curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec.sp.gov.br\", \"cpf\": \"07494812857\"}"
```

#### Resposta:

```json
{
  "nome": "Henrique Louro",
  "email": "henrique.louro@fatec.sp.gov.br",
  "cpf": "07494812857",
  "_id": "6838f3f31e42910b28566f55",
  "__v": 0
}
```

#### Entrada:

```bash
curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Carlos Silva\", \"email\": \"carlos.silva@fatec.sp.gov.br\", \"cpf\": \"63479695051\"}"
```

#### Resposta:

```json
{
  "nome": "Carlos Silva",
  "email": "carlos.silva@fatec.sp.gov.br",
  "cpf": "63479695051",
  "_id": "6838f5631e42910b28566f57",
  "__v": 0
}
```

#### Entrada:

```bash
curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Odete Roitman\", \"email\": \"odete.roitman@fatec.sp.gov.br\", \"cpf\": \"32082128016\"}"
```

#### Resposta:

```json
{
  "nome": "Odete Roitman",
  "email": "odete.roitman@fatec.sp.gov.br",
  "cpf": "32082128016",
  "_id": "6838f59a1e42910b28566f59",
  "__v": 0
}
```

#### Consultar com CPF ou E-mail já cadastrado:

```bash
curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec.sp.gov.br\", \"cpf\": \"07494812857\"}"
```

#### Resposta:

```json
{
  "message": "CPF ou e-Mail já em uso"
}
```

#### Consultar um CPF inválido:

```bash
curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec.sp.gov.br\", \"cpf\": \"12345678910\"}"
```

#### Resposta:

```json
{
  "message": "12345678910 não é um CPF válido"
}
```

#### Consultar um E-mail inválido:

```bash
curl -X POST http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"nome\": \"Henrique Louro\", \"email\": \"henrique.louro@fatec\", \"cpf\": \"12345678910\"}"
```

#### Resposta:

```json
{
  "message": "henrique.louro@fatec não é um formato de e-mail válido"
}
```

### Consultar o cadastro dos Professores

#### Entrada:

```bash
curl -X GET http://localhost:3001/professor
```

#### Resposta:

```json
[
  {
    "_id": "6838f3f31e42910b28566f55",
    "nome": "Henrique Louro",
    "email": "henrique.louro@fatec.sp.gov.br",
    "cpf": "07494812857",
    "__v": 0
  },
  {
    "_id": "6838f5631e42910b28566f57",
    "nome": "Carlos Silva",
    "email": "carlos.silva@fatec.sp.gov.br",
    "cpf": "63479695051",
    "__v": 0
  },
  {
    "_id": "6838f59a1e42910b28566f59",
    "nome": "Odete Roitman",
    "email": "odete.roitman@fatec.sp.gov.br",
    "cpf": "32082128016",
    "__v": 0
  }
]
```

### Atualizar o cadastro do Professor

#### Entrada:

```bash
curl -X PUT http://localhost:3001/professor -H "Content-Type: application/json" -d "{\"id\":\"6835017c642961ce1b3edb31\",\"nome\": \"Odetinha Roitman\", \"email\": \"odetinha.roitman@fatec.sp.gov.br\", \"cpf\": \"32082128016\"}"
```

#### Resposta:

```json
{
  "message": "Professor inexistente"
}
```

### Adicionar uma Disciplina

#### Entrada:

```bash
curl -X POST http://localhost:3001/disciplina -H "Content-Type: application/json" -d "{\"descricao\": \"Lógica de Programação\"}"
```

#### Resposta:

```json
{
  "descricao": "Lógica de Programação",
  "_id": "6838f6721e42910b28566f61",
  "__v": 0
}
```

#### Consultar as Disciplinas:

```bash
curl -X GET http://localhost:3001/disciplina
```

#### Resposta:

```json
[
  {
    "_id": "6838f6721e42910b28566f61",
    "descricao": "Lógica de Programação",
    "__v": 0
  }
]
```

### Associar um Professor a Disciplina

#### Consulta com IDs incorretos:

```bash
curl -X POST http://localhost:3001/professor_has_disciplina -H "Content-Type: application/json" -d "{\"professor\": \"6834ff01642961ce1b3edb2d\", \"disciplina\": \"68350d5e642961ce1b3edb3c\"}"
```

#### Resposta:

```json
{
  "message": "O ID do professor fornecido não existe"
}
```

#### Consultar as Associações:

```bash
curl -X GET http://localhost:3001/professor_has_disciplina
```

#### Resposta:

```json
[]
```

