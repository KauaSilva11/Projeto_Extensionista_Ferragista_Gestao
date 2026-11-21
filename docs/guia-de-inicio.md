# Guia de início para integrantes

Este guia ajuda cada integrante a encontrar a documentação do projeto, pegar uma tarefa existente e começar a desenvolver.

Trabalhe sempre a partir de uma issue atribuída. Se a issue e a documentação aprovada não esclarecerem uma decisão necessária, alinhe com o grupo antes de implementá-la.

## Onde encontrar as informações

- `README.md`: visão geral, tecnologias e como o projeto está organizado.
- `AGENTS.md`: instruções permanentes para trabalhar no código.
- `plan.md`: estado e próximos passos registrados para o projeto.
- `docs/requisitos.md`: funcionalidades incluídas e fora do MVP.
- `docs/regras-de-negocio.md`: regras que o sistema deve cumprir.
- `docs/arquitetura-servicos`: responsabilidades dos serviços, bancos e comunicação entre eles.
- `services/`: código dos serviços backend.
- `frontend/`: aplicação web.
- `infrastructure/postgres/`: configuração do banco local.

Antes de começar, leia a issue atribuída e os documentos relacionados à sua tarefa.

## Frentes de desenvolvimento

| Frente | Issue | Escopo inicial |
|---|---:|---|
| Auth/Users | #11 | Estrutura inicial do serviço de autenticação e usuários. |
| Produtos e estoque | #12 | Estrutura inicial do serviço de produtos e estoque. |
| Vendas | #13 | Estrutura inicial do serviço de vendas. |
| Financeiro | #14 | Estrutura inicial do serviço financeiro. |
| API Gateway | #15 | Estrutura inicial do ponto de entrada das APIs. |
| Mapeamento do Figma | #17 | Relacionar o protótipo ao escopo aprovado do MVP. |
| Frontend | #18 | Implementar a estrutura visual prevista na issue. |

Atribua as frentes de implementação aos integrantes no GitHub Projects. A #16 serve como referência aprovada. Antes de começar cada frente, confira se a issue está aberta e leia suas dependências e critérios de conclusão.


Atribua cada issue a uma pessoa ou dupla no GitHub Projects. Antes de começar, confira se a issue está aberta e leia suas dependências e critérios de conclusão.

## Como obter o repositório

1. Abra o GitHub Desktop e entre na sua conta.
2. Selecione **File > Clone repository**.
3. Escolha a aba **URL** e informe:
   `https://github.com/KauaSilva11/Projeto_Extensionista_Ferragista_Gestao.git`
4. Escolha onde salvar o projeto no computador e clique em **Clone**.
5. No GitHub Desktop, abra o projeto no VS Code.

Se o repositório não aparecer ou pedir acesso, confirme com o responsável se sua conta GitHub tem permissão.

## Como começar uma tarefa

1. Abra a issue atribuída e leia o objetivo, as dependências e os critérios de conclusão.
2. No GitHub Desktop, selecione **Fetch origin** e depois **Pull origin** para atualizar o repositório.
3. Crie uma branch a partir da `main`, com um nome ligado à issue. Exemplo: `feat/11-auth-service`.
4. No VS Code, leia `AGENTS.md` e os documentos relacionados à tarefa.
5. Implemente o escopo da issue. Se faltar uma decisão necessária, alinhe com o grupo.
6. Ao terminar, envie a branch e abra um Pull Request para revisão.

Não envie senhas, tokens ou arquivos `.env` ao GitHub.

## Áreas do GitHub

- **Code:** arquivos e pastas do projeto.
- **Issues:** tarefas, responsáveis e critérios de conclusão.
- **Projects:** quadro para acompanhar o andamento das tarefas.
- **Pull requests:** revisão e integração das alterações na `main`.

## Criar e iniciar a estrutura de um serviço

Cada responsável deve gerar o serviço da sua issue com o mesmo padrão.

### 1. Configurações no Spring Initializr

Acesse [start.spring.io](https://start.spring.io/) e selecione:

- Project: Maven
- Language: Java
- Spring Boot: 4.2.0
- Packaging: Jar
- Configuration: Properties
- Java: 21
- Dependencies: Spring Web, Spring Data JPA, PostgreSQL Driver e Validation

Use o mesmo `Group` nos quatro projetos: `br.com.ferragista`.

Preencha `Artifact` e `Package name` conforme o serviço:

| Serviço | Artifact | Package name |
|---|---|---|
| Auth/Users | `auth-service` | `br.com.ferragista.auth` |
| Produtos e estoque | `product-stock-service` | `br.com.ferragista.productstock` |
| Vendas | `sales-service` | `br.com.ferragista.sales` |
| Financeiro | `financial-service` | `br.com.ferragista.financial` |

O campo `Name` deve ser igual ao `Artifact`.

Não adicione Spring Security na estrutura inicial do Auth: a issue #11 não inclui implementar login ou autorização nesta etapa.

### 2. Colocar os arquivos no repositório

1. Gere e baixe o projeto ZIP pelo Spring Initializr.
2. Extraia o conteúdo diretamente na pasta correspondente:
   - `services/auth-service/`
   - `services/product-stock-service/`
   - `services/sales-service/`
   - `services/financial-service/`
3. Preserve o README que já existe na pasta e atualize-o para explicar como compilar e iniciar o serviço.
4. Confira se os arquivos `pom.xml`, `mvnw.cmd` e `src/` ficaram diretamente dentro da pasta do serviço, sem criar uma pasta duplicada dentro dela.

### 3. Configurar e iniciar

1. Confira a issue atribuída e configure a conexão ao banco usando variáveis de ambiente, sem incluir credenciais no código.
2. Use o banco lógico correspondente ao serviço: `ferragista_auth`, `ferragista_estoque`, `ferragista_vendas` ou `ferragista_financeiro`.
3. Para iniciar o PostgreSQL local, siga `infrastructure/postgres/README.md`.
4. No terminal do VS Code, entre na pasta do serviço e execute:

   ```powershell
   .\mvnw.cmd spring-boot:run

## Prompt para iniciar uma tarefa

Copie o prompt e preencha os campos entre colchetes com as informações da issue:

> Vou trabalhar na issue #[número] — [título], na frente [área].
>
> Leia `AGENTS.md`, a issue e os documentos relevantes em `docs/`. Confira o código existente antes de propor alterações.
>
> Implemente somente o escopo e os critérios de conclusão da issue. Não invente requisitos ou decisões de arquitetura. Se faltar uma decisão necessária ou houver conflito com a documentação, explique o ponto e peça orientação ao grupo antes de implementar essa parte.
>
> Ao terminar, informe o que alterou e quais verificações executou. Não faça merge.