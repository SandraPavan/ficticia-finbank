# 🏦 FinBank API

## 📋 Sobre

API planejada pela FinBank para gerenciamento de contas e transações bancárias. Este documento detalha os principais recursos a serem cobertos pela automação, incluindo testes de regressão, smoke tests e testes de contrato.

## 🚀 Endpoints

### 1. Criação de Conta

> **POST** `/accounts`

Cria uma nova conta no sistema, vinculada a um cliente.

#### Request

```json
{
  "customerId": "CUST-001",
  "type": "checking",
  "initialDeposit": 500.00,
  "currency": "BRL"
}
```

#### Response (201 Created)

```json
{
  "accountId": "ACC-10001",
  "customerId": "CUST-001",
  "type": "checking",
  "balance": 500.00,
  "status": "ACTIVE",
  "createdAt": "2025-10-16T20:00:00Z"
}
```

#### ⚠️ Pontos de Atenção para Automação

- Duplicidade sob carga alta / problemas de idempotência (reexecução de POST)
- Validação de campos obrigatórios e tipos numéricos

### 2. Transferência entre Contas

> **POST** `/transactions`

Executa uma transação entre contas (PIX ou TED).

#### Request

```json
{
  "fromAccount": "ACC-10001",
  "toAccount": "ACC-10002",
  "amount": 250.00,
  "currency": "BRL",
  "transactionType": "PIX",
  "description": "Pagamento de serviço"
}
```

#### Response (200 OK)

```json
{
  "transactionId": "TXN-8752301",
  "status": "COMPLETED",
  "timestamp": "2025-10-16T20:05:12Z",
  "balanceAfter": 250.00
}
```

#### ⚠️ Pontos de Atenção para Automação

- Corrida de transações (race conditions) com múltiplos threads
- Validação de rollback em caso de falha parcial

### 3. Consulta de Saldo

> **GET** `/balance/{accountId}`

Retorna o saldo atual de uma conta.

#### Response (200 OK)

```json
{
  "accountId": "ACC-10001",
  "availableBalance": 250.00,
  "currency": "BRL",
  "lastUpdated": "2025-10-16T20:10:00Z"
}
```

#### ⚠️ Pontos de Atenção para Automação

- Sincronização com base replicada (delay de replicação)
- Comparar saldo pós-transação em múltiplos endpoints

### 4. Histórico de Transações

> **GET** `/transactions?accountId=ACC-10001&limit=5`

Retorna o histórico de transações de uma conta específica.

#### Response (200 OK)

```json
{
  "accountId": "ACC-10001",
  "transactions": [
    // Lista de transações
  ]
}
```

## 📝 Notas

- Todos os endpoints requerem autenticação via Bearer token
- As respostas seguem o padrão REST com códigos HTTP apropriados
- Os valores monetários são sempre representados com 2 casas decimais

## ⚙️ Executando o Projeto

### Pré-requisitos

- Node.js instalado
- NPM ou Yarn

### Instalação

1. Instale o json-server globalmente:

```bash
npm install -g json-server
```

### Executando a API Mock

1. Na pasta do projeto, inicie o json-server:

```bash
json-server --watch db.json --port 3000
```

### Testando os Endpoints

Você pode testar os endpoints usando cURL ou qualquer cliente HTTP (Postman, Insomnia, etc.), pode importar esse cURL nas ferramentas citadas:

#### Criar uma conta

```bash
curl -X POST http://localhost:3000/accounts \
  -H "Content-Type: application/json" \
  -d '{
    "customerId": "CUST-001",
    "type": "checking",
    "initialDeposit": 500.00,
    "currency": "BRL"
  }'
```

#### Realizar uma transferência

```bash
curl -X POST http://localhost:3000/transactions \
  -H "Content-Type: application/json" \
  -d '{
    "fromAccount": "ACC-10001",
    "toAccount": "ACC-10002",
    "amount": 250.00,
    "currency": "BRL",
    "transactionType": "PIX",
    "description": "Pagamento de serviço"
  }'
```

#### Consultar saldo

```bash
curl http://localhost:3000/balance/ACC-10001
```

#### Listar transações

```bash
curl http://localhost:3000/transactions?accountId=ACC-10001
```


