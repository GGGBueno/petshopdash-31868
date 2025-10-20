# Documentação do Banco de Dados

Este diretório contém a documentação completa de todas as tabelas do projeto.

## Tabelas Disponíveis

1. [chat_messages](./chat_messages.md) - Mensagens de conversas do chatbot
2. [chats](./chats.md) - Conversas/sessões de chat
3. [dados_cliente](./dados_cliente.md) - Dados dos clientes e seus pets
4. [documents](./documents.md) - Documentos da base de conhecimento
5. [n8n_chat_histories](./n8n_chat_histories.md) - Histórico de chats N8N
6. [pausa_bot](./pausa_bot.md) - Controle de pausa do bot

## Funções Disponíveis

- **match_documents** - Busca de documentos por similaridade usando embeddings

## Estrutura Geral

O banco de dados suporta:
- Sistema de chat com histórico de mensagens
- Gestão de clientes e informações de pets
- Base de conhecimento com busca por similaridade
- Integração com N8N para automações
- Controle de pausa do bot por número de telefone
