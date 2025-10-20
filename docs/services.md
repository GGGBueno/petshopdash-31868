# Tabela: services

## Descrição
Catálogo de serviços oferecidos pela clínica/pet shop.

## Estrutura da Tabela

| Coluna | Tipo | Nullable | Default | Descrição |
|--------|------|----------|---------|-----------|
| id | uuid | NO | gen_random_uuid() | Identificador único do serviço |
| name | text | NO | - | Nome do serviço |
| description | text | YES | - | Descrição detalhada do serviço |
| price | numeric(10,2) | NO | - | Preço do serviço |
| duration_minutes | integer | NO | - | Duração estimada em minutos |
| active | boolean | NO | true | Se o serviço está ativo/disponível |
| created_at | timestamptz | NO | now() | Data de criação do registro |

## Chaves

### Primary Key
- `id`

## Índices
- Index em `active` para filtrar serviços disponíveis
- Index em `name` para buscas por nome

## Row Level Security (RLS)

### Políticas
1. **select_services**: Usuários autenticados podem ver todos os serviços
2. **insert_services**: Usuários autenticados podem criar serviços
3. **update_services**: Usuários autenticados podem atualizar serviços
4. **delete_services**: Usuários autenticados podem deletar serviços

## Exemplos de Uso

### Listar todos os serviços ativos
```sql
SELECT * FROM services 
WHERE active = true 
ORDER BY name;
```

### Buscar serviços por faixa de preço
```sql
SELECT * FROM services 
WHERE price BETWEEN 50 AND 150
AND active = true
ORDER BY price;
```

### Calcular total de serviços oferecidos
```sql
SELECT COUNT(*) as total_services 
FROM services 
WHERE active = true;
```

## Serviços Comuns

Exemplos de serviços típicos:
- Banho (R$ 50-80, 60 minutos)
- Tosa (R$ 80-120, 90 minutos)
- Banho + Tosa (R$ 120-180, 120 minutos)
- Consulta Veterinária (R$ 150-300, 30 minutos)
- Vacinação (R$ 80-150, 15 minutos)
- Exames (R$ 100-500, 30 minutos)
