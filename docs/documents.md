# Tabela: documents

## Descrição
Armazena documentos da base de conhecimento com suporte a busca semântica através de embeddings vetoriais.

## Estrutura

| Coluna | Tipo | Nullable | Descrição |
|--------|------|----------|-----------|
| id | number | NOT NULL | Identificador único do documento (auto-incremento) |
| titulo | string | NULL | Título do documento |
| content | string | NULL | Conteúdo textual do documento |
| embedding | string | NULL | Vetor de embedding para busca semântica |
| metadata | Json | NULL | Metadados adicionais em formato JSON |

## Chave Primária
- `id`

## Relacionamentos
- Nenhum relacionamento direto (FK)

## Operações

### Insert
```typescript
{
  titulo?: string | null
  content?: string | null
  embedding?: string | null
  metadata?: Json | null
}
```

### Update
```typescript
{
  id?: number
  titulo?: string | null
  content?: string | null
  embedding?: string | null
  metadata?: Json | null
}
```

## Funções Relacionadas

### match_documents
Busca documentos por similaridade usando embeddings vetoriais.

**Parâmetros:**
- `query_embedding` (string): Vetor de embedding da consulta
- `match_count` (number, opcional): Número de resultados a retornar
- `filter` (Json, opcional): Filtros adicionais

**Retorno:**
```typescript
{
  id: number
  content: string
  metadata: Json
  similarity: number
}[]
```

## Casos de Uso
- Base de conhecimento para chatbot
- Busca semântica de informações
- FAQ automatizado
- Documentação de produtos/serviços
- Respostas contextuais baseadas em similaridade

## Observações
- O campo `embedding` armazena vetores para busca por similaridade
- A função `match_documents` usa algoritmos de busca vetorial
- Metadados podem incluir categorias, tags, data de criação, etc.
- Ideal para RAG (Retrieval-Augmented Generation) em IA
