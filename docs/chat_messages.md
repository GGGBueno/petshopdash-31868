# Tabela: chat_messages

## Descrição
Armazena todas as mensagens trocadas entre usuários e o bot em conversas.

## Estrutura

| Coluna | Tipo | Nullable | Descrição |
|--------|------|----------|-----------|
| id | number | NOT NULL | Identificador único da mensagem (auto-incremento) |
| conversation_id | string | NULL | ID da conversa à qual a mensagem pertence |
| phone | string | NULL | Número de telefone do usuário |
| user_message | string | NULL | Mensagem enviada pelo usuário |
| bot_message | string | NULL | Resposta enviada pelo bot |
| message_type | string | NULL | Tipo da mensagem |
| data | string | NULL | Dados adicionais em formato JSON |
| active | boolean | NULL | Indica se a mensagem está ativa |
| created_at | string | NULL | Data e hora de criação da mensagem |

## Chave Primária
- `id`

## Relacionamentos
- Nenhum relacionamento direto (FK)

## Operações

### Insert
```typescript
{
  conversation_id?: string | null
  phone?: string | null
  user_message?: string | null
  bot_message?: string | null
  message_type?: string | null
  data?: string | null
  active?: boolean | null
  created_at?: string | null
}
```

### Update
```typescript
{
  id?: number
  conversation_id?: string | null
  phone?: string | null
  user_message?: string | null
  bot_message?: string | null
  message_type?: string | null
  data?: string | null
  active?: boolean | null
  created_at?: string | null
}
```

## Casos de Uso
- Armazenar histórico completo de conversas
- Análise de interações usuário-bot
- Auditoria de mensagens
- Recuperação de contexto de conversas anteriores

## Observações
- O campo `data` pode conter informações estruturadas em JSON
- O campo `active` permite soft delete de mensagens
- Suporta tanto mensagens do usuário quanto do bot na mesma tabela
