# Tabela: n8n_chat_histories

## Descrição
Armazena histórico de conversas gerenciadas pela plataforma de automação N8N.

## Estrutura

| Coluna | Tipo | Nullable | Descrição |
|--------|------|----------|-----------|
| id | number | NOT NULL | Identificador único do registro (auto-incremento) |
| session_id | string | NOT NULL | ID da sessão de chat |
| message | Json | NOT NULL | Dados da mensagem em formato JSON |

## Chave Primária
- `id`

## Relacionamentos
- Nenhum relacionamento direto (FK)

## Operações

### Insert
```typescript
{
  id?: number
  session_id: string  // OBRIGATÓRIO
  message: Json       // OBRIGATÓRIO
}
```

### Update
```typescript
{
  id?: number
  session_id?: string
  message?: Json
}
```

## Casos de Uso
- Integração com workflows N8N
- Histórico de automações de chat
- Rastreamento de sessões de automação
- Armazenamento de contexto para automações

## Observações
- **Campos obrigatórios**: `session_id` e `message`
- O campo `message` contém toda a estrutura da mensagem em JSON
- Usado para integração com automações N8N
- Permite recuperar histórico de conversas automatizadas
- Estrutura JSON flexível para diferentes tipos de mensagens

## Exemplo de Uso
```typescript
// Inserir histórico de chat N8N
const { data, error } = await supabase
  .from('n8n_chat_histories')
  .insert({
    session_id: 'session-123',
    message: {
      role: 'assistant',
      content: 'Olá! Como posso ajudar?',
      timestamp: new Date().toISOString()
    }
  })
```
