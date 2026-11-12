# API de Download - Upload (Flask)

API REST em Python com Flask, além de um formulário para armazenar e gerenciar dados pessoais vinculados a cada usuário. O projeto também conta com funcionalidades de Download e Upload de arquivos, utilizando SQLite como banco de dados.

## Tecnologias

- Python 3
- Flask
- SQLite (módulo `sqlite3`)
- Gunicorn (para execução em produção)

## Estrutura do projeto

```
Teste_corrigido/
├── app.py                  # Cria o app, registra os blueprints e inicia o servidor
├── config.py               # Configurações (chave JWT e nome do banco)
├── requirements.txt        # Dependências
├── database.db             # Banco SQLite
├── database/
│   └── db.py               # Conexão e criação das tabelas
├── models/                 # Acesso ao banco (consultas SQL)
│   ├── download_model.py
│   └── upload_model.py
├── controllers/            # Regras de negócio e validações
│   ├── download_controller.py
│   └── upload_controller.py
└── routes/                 # Rotas da API (blueprints)
    ├── download_routes.py
    └── upload_routes.py
```

O projeto segue uma divisão em camadas: **routes → controllers → models → database**.

## Como executar

1. Crie e ative um ambiente virtual (opcional, mas recomendado):

   ```bash
   python -m venv venv
   source venv/bin/activate      # Linux/macOS
   venv\Scripts\activate         # Windows
   ```

2. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

3. Inicie a aplicação:

   ```bash
   python app.py
   ```

   A API ficará disponível em `http://127.0.0.1:5000`. As tabelas são criadas automaticamente na primeira execução.

   ```

## Endpoints

###  Upload (`/ uploads`)

| Método | Rota              | Protegida | Descrição                          |
|--------|-------------------|-----------|------------------------------------|
| POST   | `/ uploads/ upload` | Não       | Cadastra um novo usuário           |


### Download (`/downloads`)

| Método | Rota                | Protegida | Descrição                              |
|--------|---------------------|-----------|----------------------------------------|
| GET    | `/downloads/download`     | não      | Retorna o formulário do usuário logado |

## Exemplos de uso

**Cadastro**

```bash
curl -X POST http://127.0.0.1:5000/users/register \
  -H 
```

Resposta (201): `{"message": "Usuário registrado com sucesso"}`

**Login**

```bash
curl -X POST http://127.0.0.1:5000/users/login \
  
```

Resposta (200): `{"access_token": "<token>"}`




## Códigos de resposta

| Código | Significado                                              |
|--------|----------------------------------------------------------|
| 200    | Operação realizada com sucesso                           |
| 201    | Recurso criado                                           |
| 400    | Dados obrigatórios ausentes ou usuário já existente      |


## Banco de dados

**uploads**: `id`, `filename` (único), `filepath` 

** download**: `filename`


