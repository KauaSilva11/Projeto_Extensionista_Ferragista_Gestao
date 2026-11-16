# Plano do projeto — Ferragista Mundial

## Objetivo
Entregar o MVP descrito em `docs/requisitos.md` e `docs/regras-de-negocio.md`, respeitando a arquitetura aprovada em `docs/arquitetura-servicos`.

## Estado confirmado
- Arquitetura aprovada pelo grupo, sem alterações substantivas; o cabeçalho do documento registra esse estado.
- Pull Request #21, **“docs: adicionar instruções e plano do projeto”**, aguarda revisão. Estado no GitHub Projects: **Em revisão**; prioridade: **Média**.
- PostgreSQL Compose e script de criação dos quatro bancos lógicos estão no repositório.
- Frontend contém apenas o scaffold padrão do Vite.
- Auth, Product/Stock, Sales e Financial contêm apenas READMEs; código dos serviços ainda não começou.

## Stack
Java 21, Spring Boot, Maven, Spring Cloud Gateway, React, TypeScript, Vite, PostgreSQL, JWT e APIs REST com JSON.

## Próximas frentes
1. **Auth/Users — fundação:** criar o esqueleto do serviço e sua configuração para `ferragista_auth`. Não depende da decisão de como será criado o primeiro proprietário.
2. **Auth/Users — usuários e login:** implementar cadastro autorizado, perfis e JWT. Definir a criação do primeiro proprietário antes de expor o cadastro.
3. **Product/Stock:** CRUD de produtos; operação interna que valida todos os itens e baixa estoque; compensação idempotente por `saleId`.
4. **Financial:** receitas, despesas e pagamento; fluxo de caixa e relatórios com acesso restrito ao proprietário.
5. **Sales:** coordenar estoque e financeiro, guardar preços históricos e tratar cancelamento/reconciliação. Depende dos contratos dos serviços de estoque e financeiro.
6. **Gateway e frontend:** definir a localização do Gateway, configurar as rotas e implementar as telas usando os contratos dos serviços.
7. **Integração:** percorrer os fluxos do MVP e atualizar a documentação de operação.

## Pendências de implementação
- Definir a localização do API Gateway na árvore do repositório.
- Definir como o primeiro usuário proprietário será criado.
- Especificar as rotas REST de receitas manuais, despesas, pagamentos, fluxo de caixa e relatórios ao iniciar o Financial Service.

## Próxima ação
Concluir a revisão e integração do PR #21. Em seguida, iniciar a fundação do Auth/Users em branch própria, em uma tarefa por Pull Request.

## Atualização
Ao concluir uma tarefa, marque-a no GitHub Projects e atualize aqui somente o estado e a próxima ação. Mantenha decisões permanentes em `AGENTS.md` e regras detalhadas nos documentos de `docs/`.
