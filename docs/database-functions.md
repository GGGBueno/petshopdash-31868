# Funções do Banco de Dados

## match_documents

### Descrição
Função de busca semântica que encontra documentos similares usando embeddings vetoriais.

### Assinatura
```sql
match_documents(
  query_embedding: string,
  match_count?: number,
  filter?: Json
)
```

### Parâmetros

| Parâmetro | Tipo | Obrigatório | Padrão | Descrição |
|-----------|------|-------------|--------|-----------|
| query_embedding | string | Sim | - | Vetor de embedding da consulta |
| match_count | number | Não | - | Número máximo de resultados |
| filter | Json | Não | - | Filtros adicionais para a busca |

### Retorno
```typescript
Array<{
  id: number          // ID do documento
  content: string     // Conteúdo do documento
  metadata: Json      // Metadados do documento
  similarity: number  // Score de similaridade (0-1)
}>
```

### Exemplo de Uso

```typescript
// Buscar documentos similares a uma query
const { data, error } = await supabase
  .rpc('match_documents', {
    query_embedding: embeddingVector, // Vetor gerado pela API de embeddings
    match_count: 5,
    filter: { category: 'veterinaria' }
  })

// Processar resultados
data?.forEach(doc => {
  console.log(`Documento: ${doc.content}`)
  console.log(`Similaridade: ${doc.similarity}`)
})
```

### Casos de Uso
- Busca semântica em base de conhecimento
- RAG (Retrieval-Augmented Generation) para chatbots
- Recomendação de documentos relacionados
- FAQ automatizado por similaridade
- Busca contextual em documentação

### Observações
- Requer embeddings pré-computados na tabela `documents`
- Usa algoritmos de busca vetorial (cosine similarity)
- Resultados ordenados por similaridade (maior para menor)
- Performance otimizada com índices HNSW ou IVFFlat
- Suporta filtros adicionais via parâmetro `filter`

## Outras Funções Disponíveis

As seguintes funções são internas do PostgreSQL com extensão pgvector:

- `binary_quantize` - Quantização binária de vetores
- `halfvec_*` - Funções para vetores de meia precisão
- `hnsw_*` - Funções de suporte para índices HNSW
- `ivfflat_*` - Funções de suporte para índices IVFFlat
- `l2_norm` - Cálculo de norma L2
- `l2_normalize` - Normalização L2
- `sparsevec_*` - Funções para vetores esparsos
- `vector_*` - Funções utilitárias para vetores

Estas funções são utilizadas internamente pela extensão pgvector e não precisam ser chamadas diretamente na maioria dos casos.
