# Plano do projeto — Ferragista Mundial

## Objetivo
Entregar um MVP web para gestão de usuários, produtos, estoque, vendas e finanças da Ferragista Mundial. Escopo e regras detalhados em `docs/requisitos.md` e `docs/regras-de-negocio.md`.

## Stack e arquitetura confirmadas
- Frontend: React, TypeScript e Vite.
- Backend: Java 21, Spring Boot, Maven; gateway com Spring Cloud Gateway.
- Persistência: PostgreSQL; autenticação JWT; APIs REST com JSON.
- Serviços previstos: Auth/Users, Product/Stock, Sales e Financial; API Gateway encaminha requisições.
- Scrum simplificado; GitHub Projects, branches e Pull Requests.
- Uma instância PostgreSQL com bancos lógicos `ferragista_auth`, `ferragista_estoque`, `ferragista_vendas` e `ferragista_financeiro`.
- Localização do gateway na estrutura do repositório ainda precisa ser definida conforme o padrão documentado.

## Estado
- Requisitos, regras e arquitetura estão documentados em `docs/`.
- Estrutura inicial de frontend, serviços e infraestrutura existe; isso não confirma implementação de endpoints.
- Conforme o último resumo do notebook: Java 21, Node/npm, Git, WSL 2 e Docker Desktop estão instalados; PostgreSQL no Docker Compose foi confirmado em execução.
- Ainda falta confirmar no GitHub Desktop se `main` está sincronizada com `origin/main`, se há alterações locais e se a branch de trabalho foi criada.

## Próxima ação
- No GitHub Desktop, selecionar este repositório, conferir a branch e as alterações locais e executar **Fetch origin**.
- Após confirmar sincronização, criar a branch para a primeira tarefa do Auth Service, seguindo o nome definido pelo grupo. Não iniciar implementação antes de conferir os documentos de arquitetura e o padrão de serviço.

## Checklist do MVP
- [ ] Preparar e revisar o Auth/Users Service (cadastro, login, perfis e JWT).
- [ ] Implementar Product/Stock Service.
- [ ] Implementar Sales Service com validação e baixa de estoque e geração da receita.
- [ ] Implementar Financial Service: receitas, despesas pagas, fluxo de caixa e relatórios.
- [ ] Definir a localização do API Gateway e implementar o encaminhamento REST.
- [ ] Implementar frontend e permissões de proprietário e funcionário.
- [ ] Integrar os serviços e validar os fluxos do MVP conforme os documentos.

## Atualização
Ao concluir uma tarefa, marque o item correspondente e atualize somente o estado e a próxima ação. Mantenha decisões permanentes em `AGENTS.md` e os detalhes funcionais nos documentos de `docs/`.
