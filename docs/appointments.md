# Tabela: appointments

## Descrição
Gerencia os agendamentos de serviços para os pets dos clientes.

## Estrutura da Tabela

| Coluna | Tipo | Nullable | Default | Descrição |
|--------|------|----------|---------|-----------|
| id | uuid | NO | gen_random_uuid() | Identificador único do agendamento |
| client_id | integer | NO | - | Referência ao cliente (FK para dados_cliente) |
| pet_name | text | NO | - | Nome do pet |
| service_type | text | NO | - | Tipo de serviço (banho, tosa, veterinário, etc) |
| appointment_date | timestamptz | NO | - | Data e hora do agendamento |
| status | text | NO | 'scheduled' | Status do agendamento (scheduled, completed, cancelled) |
| notes | text | YES | - | Observações adicionais |
| created_at | timestamptz | NO | now() | Data de criação do registro |
| updated_at | timestamptz | NO | now() | Data da última atualização |

## Chaves

### Primary Key
- `id`

### Foreign Keys
- `client_id` → `dados_cliente(id)` ON DELETE CASCADE

## Índices
- Index em `client_id` para queries rápidas por cliente
- Index em `appointment_date` para filtros por data
- Index em `status` para filtros por status

## Row Level Security (RLS)

### Políticas
1. **select_appointments**: Usuários autenticados podem ver todos os agendamentos
2. **insert_appointments**: Usuários autenticados podem criar agendamentos
3. **update_appointments**: Usuários autenticados podem atualizar agendamentos
4. **delete_appointments**: Usuários autenticados podem deletar agendamentos

## Triggers
- `update_appointments_updated_at`: Atualiza automaticamente o campo `updated_at` em cada modificação

## Exemplos de Uso

### Consultar agendamentos de um cliente
```sql
SELECT * FROM appointments 
WHERE client_id = 123 
ORDER BY appointment_date DESC;
```

### Consultar agendamentos por período
```sql
SELECT * FROM appointments 
WHERE appointment_date BETWEEN '2024-01-01' AND '2024-01-31'
ORDER BY appointment_date;
```

### Consultar agendamentos pendentes
```sql
SELECT * FROM appointments 
WHERE status = 'scheduled'
AND appointment_date >= NOW()
ORDER BY appointment_date;
```

## Valores Comuns

### Status possíveis
- `scheduled`: Agendado
- `completed`: Completado
- `cancelled`: Cancelado

### Service Types comuns
- `banho`: Banho
- `tosa`: Tosa
- `veterinario`: Consulta veterinária
- `vacina`: Vacinação
