# Tabela: dados_cliente

## Descrição
Armazena informações completas dos clientes, incluindo dados pessoais, informações de pets e integrações de pagamento.

## Estrutura

| Coluna | Tipo | Nullable | Descrição |
|--------|------|----------|-----------|
| id | number | NOT NULL | Identificador único do cliente (auto-incremento) |
| nome | string | NULL | Nome completo do cliente |
| email | string | NULL | Endereço de e-mail do cliente |
| telefone | string | NULL | Número de telefone do cliente |
| cpf_cnpj | string | NULL | CPF ou CNPJ do cliente |
| nome_pet | string | NULL | Nome do pet |
| raca_pet | string | NULL | Raça do pet |
| porte_pet | string | NULL | Porte do pet (pequeno, médio, grande) |
| asaas_customer_id | string | NULL | ID do cliente no sistema Asaas |
| payments | Json | NULL | Informações de pagamentos em formato JSON |
| sessionid | string | NULL | ID da sessão associada |
| created_at | string | NULL | Data e hora de criação do registro |

## Chave Primária
- `id`

## Relacionamentos
- Nenhum relacionamento direto (FK)

## Operações

### Insert
```typescript
{
  nome?: string | null
  email?: string | null
  telefone?: string | null
  cpf_cnpj?: string | null
  nome_pet?: string | null
  raca_pet?: string | null
  porte_pet?: string | null
  asaas_customer_id?: string | null
  payments?: Json | null
  sessionid?: string | null
  created_at?: string | null
}
```

### Update
```typescript
{
  id?: number
  nome?: string | null
  email?: string | null
  telefone?: string | null
  cpf_cnpj?: string | null
  nome_pet?: string | null
  raca_pet?: string | null
  porte_pet?: string | null
  asaas_customer_id?: string | null
  payments?: Json | null
  sessionid?: string | null
  created_at?: string | null
}
```

## Casos de Uso
- Gestão de cadastro de clientes
- Armazenamento de informações de pets
- Integração com sistema de pagamentos (Asaas)
- Análise demográfica de clientes
- Segmentação por tipo/porte de pet

## Observações
- **PII (Informações Pessoais)**: Esta tabela contém dados sensíveis (nome, email, telefone, CPF/CNPJ)
- Deve ter políticas RLS (Row Level Security) adequadas
- O campo `payments` contém histórico de pagamentos em JSON
- Integração com Asaas para gestão financeira
- Campo `porte_pet` útil para precificação de serviços
