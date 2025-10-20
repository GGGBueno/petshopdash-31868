# Tabela: pausa_bot

## Descrição
Controla a pausa/ativação do bot para números de telefone específicos, permitindo desativar temporariamente o atendimento automático.

## Estrutura

| Coluna | Tipo | Nullable | Descrição |
|--------|------|----------|-----------|
| id | number | NOT NULL | Identificador único do registro (auto-incremento) |
| number | string | NULL | Número de telefone |
| status | string | NULL | Status da pausa (ativo/pausado) |
| data | string | NULL | Data/hora da pausa ou dados adicionais |

## Chave Primária
- `id`

## Relacionamentos
- Nenhum relacionamento direto (FK)

## Operações

### Insert
```typescript
{
  number?: string | null
  status?: string | null
  data?: string | null
}
```

### Update
```typescript
{
  id?: number
  number?: string | null
  status?: string | null
  data?: string | null
}
```

## Casos de Uso
- Pausar atendimento automático para números específicos
- Permitir atendimento humano temporário
- Controlar quando o bot deve/não deve responder
- Gerenciar exceções no atendimento automatizado

## Valores Comuns

### Status
- `"ativo"` - Bot ativo para este número
- `"pausado"` - Bot pausado, atendimento manual
- `"desativado"` - Bot desativado permanentemente

## Exemplo de Uso
```typescript
// Pausar bot para um número específico
const { data, error } = await supabase
  .from('pausa_bot')
  .insert({
    number: '+5511999999999',
    status: 'pausado',
    data: new Date().toISOString()
  })

// Verificar se bot está pausado
const { data: pausa } = await supabase
  .from('pausa_bot')
  .select('status')
  .eq('number', phone)
  .eq('status', 'pausado')
  .maybeSingle()

if (pausa) {
  // Bot está pausado, não responder automaticamente
}
```

## Observações
- Útil para transferir conversas para atendimento humano
- Pode incluir duração da pausa no campo `data`
- Permite controle granular por número de telefone
- Essencial para sistemas híbridos (bot + humano)
