# Tabela: chats

## Descrição
Armazena as sessões de conversas/chats entre usuários e o sistema.

## Estrutura

| Coluna | Tipo | Nullable | Descrição |
|--------|------|----------|-----------|
| id | number | NOT NULL | Identificador único do chat (auto-incremento) |
| conversation_id | string | NULL | ID único da conversa |
| phone | string | NULL | Número de telefone do usuário |
| app | string | NULL | Aplicativo/canal de origem do chat |
| created_at | string | NULL | Data e hora de criação do chat |
| updated_at | string | NULL | Data e hora da última atualização |

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
  app?: string | null
  created_at?: string | null
  updated_at?: string | null
}
```

### Update
```typescript
{
  id?: number
  conversation_id?: string | null
  phone?: string | null
  app?: string | null
  created_at?: string | null
  updated_at?: string | null
}
```

## Casos de Uso
- Gerenciar sessões de conversa
- Agrupar mensagens por conversa
- Rastrear canais de origem dos chats
- Monitorar atividade de conversas por telefone

## Observações
- O `conversation_id` deve ser único para cada sessão
- O campo `app` pode indicar o canal (WhatsApp, Telegram, etc.)
- `updated_at` é atualizado a cada nova mensagem na conversa
- Usado em conjunto com `chat_messages` para histórico completo
