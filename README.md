# Projeto Extensionista — Sistema de Gestão da Ferragista

Sistema web para apoiar a gestão de produtos, estoque, vendas e finanças da Ferragista Mundial.

**Status:** requisitos e regras de negócio consolidados; arquitetura aprovada pelo grupo. O repositório contém a infraestrutura inicial do banco e o scaffold padrão do frontend. Os serviços backend ainda não têm implementação.

## Escopo do MVP

- Usuários autenticados com perfis de proprietário e funcionário.
- Cadastro de produtos e controle de estoque.
- Registro de vendas com verificação e baixa de estoque.
- Registro de receitas e despesas; somente despesas pagas reduzem o fluxo de caixa.
- Fluxo de caixa e relatórios financeiros acessíveis somente ao proprietário.

Consulte `docs/requisitos.md`, `docs/regras-de-negocio.md` e `docs/arquitetura-servicos` para os requisitos e contratos aprovados.

## Tecnologias

- Backend: Java 21, Spring Boot e Maven.
- Gateway: Spring Cloud Gateway.
- Frontend: React, TypeScript e Vite.
- Banco: PostgreSQL, em uma instância com quatro bancos lógicos.
- Integração: APIs REST com JSON; autenticação JWT.

## Estado do repositório

- `infrastructure/postgres/`: Docker Compose, exemplo de configuração e script para criar os quatro bancos lógicos.
- `frontend/`: scaffold inicial do React/Vite, ainda sem as telas do sistema.
- `services/`: cada serviço possui somente um README inicial; endpoints e regras ainda não foram implementados.
- A localização do API Gateway na estrutura do repositório deve ser definida antes da implementação do componente.

## Colaboração

O grupo acompanha o trabalho no GitHub Projects. Desenvolva cada tarefa em uma branch própria, abra um Pull Request para `main` e peça revisão de outro integrante. Integre após aprovação. Não versione credenciais ou arquivos `.env`; use `.env.example` sem segredos.
