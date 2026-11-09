# Requisitos do Sistema de Gestão da Ferragista

**Versão:** documento de trabalho consolidado  
**Base:** `trabalho.pdf`, proposta técnica elaborada com o grupo e decisões confirmadas nas conversas do projeto.

> Os requisitos e as pendências que constavam no documento-base foram confirmados pelo responsável do projeto. Este arquivo atualiza os pontos que mudaram, principalmente a equipe do Extensionista, o processo de trabalho e a regra de despesas pagas.

## 1. Problema

A gestão da ferragista é realizada de forma manual, dificultando a organização de produtos, estoque, vendas e movimentações financeiras. O sistema deve reunir essas operações em uma ferramenta simples de usar, acessível e adequada à rotina do estabelecimento.

## 2. Objetivo

Desenvolver um sistema para apoiar a gestão comercial e financeira da ferragista, permitindo controlar usuários, produtos, estoque, vendas, receitas, despesas pagas, fluxo de caixa e relatórios financeiros.

## 3. Usuários e permissões

### Proprietário

Pode acessar todas as funcionalidades, inclusive usuários, fluxo de caixa e relatórios financeiros.

### Funcionário

Pode operar produtos, estoque e vendas, além de registrar e editar receitas e despesas. Não pode consultar o fluxo de caixa nem os relatórios financeiros.

## 4. Escopo do MVP

### Incluído

- Cadastro e autenticação de usuários autorizados.
- Cadastro, consulta, edição e remoção de produtos.
- Consulta e atualização do estoque.
- Registro e consulta de vendas com um ou mais produtos, quantidades e valores.
- Registro e consulta de receitas.
- Lançamento, consulta, edição e remoção de despesas, com indicação de pagamento.
- Consulta visual e simples de entradas, saídas e saldo por período.
- Relatórios financeiros baseados nas movimentações registradas.

### Fora do escopo inicial

- Emissão de notas fiscais.
- Integração com bancos ou meios de pagamento.
- Gestão completa de fornecedores e compras.
- Folha de pagamento.
- Contabilidade completa.
- Aplicativo móvel.

## 5. Requisitos funcionais

| Código | Requisito | Descrição |
|---|---|---|
| RF01 | Cadastro de usuários | Permitir cadastrar usuários autorizados, com perfil de proprietário ou funcionário. |
| RF02 | Autenticação | Exigir identificação do usuário antes de liberar funcionalidades protegidas. |
| RF03 | Produtos | Permitir cadastrar, consultar, editar e remover produtos. |
| RF04 | Estoque | Registrar e consultar a quantidade disponível de cada produto. |
| RF05 | Vendas | Registrar vendas com um ou mais produtos, quantidades e valores. |
| RF06 | Receitas | Registrar e consultar receitas, incluindo a receita gerada por vendas concluídas. |
| RF07 | Despesas | Lançar, consultar, editar e remover despesas, registrando se foram pagas. |
| RF08 | Fluxo de caixa | Exibir visualmente entradas, despesas pagas e saldo para um período. Disponível ao proprietário. |
| RF09 | Relatórios financeiros | Apresentar relatórios das movimentações registradas. Disponível ao proprietário. |

## 6. Requisitos não funcionais

| Código | Categoria | Requisito |
|---|---|---|
| RNF01 | Segurança | Funcionalidades protegidas exigem autenticação; permissões respeitam os perfis de proprietário e funcionário. |
| RNF02 | Desempenho | Consultas e relatórios devem responder adequadamente ao uso diário do estabelecimento. |
| RNF03 | Manutenibilidade | Código e serviços devem ter responsabilidades claras e organização compreensível pela equipe. |
| RNF04 | Testabilidade | As funcionalidades principais devem possuir testes automatizados; tipos e cobertura são definidos durante o desenvolvimento. |
| RNF05 | Facilidade de uso | Telas e mensagens devem ser simples para apoiar o uso cotidiano da ferragista. |

## 7. Arquitetura e tecnologias

A solução será organizada em serviços com responsabilidades específicas e comunicação por APIs REST. A proposta técnica prevê API Gateway e serviços de autenticação/usuários, produtos/estoque, vendas, financeiro e relatórios. A separação final deve permanecer simples o suficiente para a equipe implementar e manter.

Tecnologias acordadas pelo grupo:

- **Backend:** Java 21, Spring Boot e Maven.
- **Gateway:** Spring Cloud Gateway.
- **Autenticação:** JWT.
- **Persistência:** PostgreSQL.
- **Frontend:** React, TypeScript e Vite.

A comunicação entre os serviços será feita por APIs REST. Detalhes de contratos, dados e implantação serão especificados junto à modelagem técnica.

## 8. Metodologia e colaboração

O grupo adotará Scrum de forma compatível com o projeto acadêmico. O GitHub Projects será usado para acompanhar o backlog e o trabalho da equipe. As tarefas serão priorizadas e desenvolvidas incrementalmente, com branches e Pull Requests para revisão antes da integração.

A composição de seis integrantes corresponde ao Projeto Extensionista. Os materiais da disciplina que descrevem o grupo de três pessoas não alteram essa composição.

## 9. Referências e decisões

- O `trabalho.pdf` é preservado como documento-base; este arquivo consolida seus requisitos para a etapa atual.
- A proposta técnica e as decisões confirmadas pelo grupo nesta conversa complementam o documento-base.
- O protótipo do Figma é uma referência visual estática, não uma demonstração de funcionalidades implementadas.
