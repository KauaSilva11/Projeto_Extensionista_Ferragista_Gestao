# Instruções gerais do projeto

## Contexto
Sistema de gestão financeira para uma ferragista, desenvolvido como projeto extensionista. Consulte os documentos em `docs/` antes de propor ou implementar mudanças.

## Decisões atuais
- Backend: Java 21, Spring Boot e Maven.
- Frontend: React, TypeScript e Vite.
- Banco: PostgreSQL, com uma instância local e quatro bancos lógicos.
- Comunicação entre serviços: APIs REST síncronas com JSON.
- Metodologia de trabalho: Scrum.
- Auth Service será o serviço piloto para validar o padrão técnico.

## Regras para alterações
- Trabalhe apenas na tarefa solicitada e nos arquivos necessários para concluí-la.
- Não invente requisitos nem altere decisões do grupo. Registre dúvidas como pendências.
- Preserve a separação de responsabilidades entre os serviços.
- Não inclua senhas, tokens ou outros segredos no Git.
- Não declare uma tarefa concluída sem verificar os critérios de conclusão da issue.
- Explique mudanças relevantes e indique o que precisa de revisão humana.
- Antes de integrar mudanças, abra um Pull Request e solicite revisão de outro integrante.

## Limites do MVP
Implemente somente o que estiver confirmado nos documentos do projeto e nas issues. Se houver conflito ou lacuna, registre a dúvida para o grupo antes de decidir.