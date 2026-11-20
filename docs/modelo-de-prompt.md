# Modelo de prompt para tarefas de desenvolvimento

Copie o prompt abaixo e preencha os campos entre colchetes antes de iniciar uma tarefa com um agente.

---

Você está trabalhando no projeto Ferragista. Antes de alterar arquivos, leia o `AGENTS.md` da raiz e os documentos relevantes em `docs/`.

## Tarefa

- Issue do GitHub: [número e título]
- Serviço ou parte do sistema: [nome]
- Objetivo e critérios de conclusão: [copie da issue]

## Regras

- Trabalhe somente no escopo desta issue e nos arquivos necessários para concluí-la.
- Siga o padrão em `docs/padrao-dos-servicos.md` e as decisões documentadas do projeto.
- Não invente requisitos nem altere contratos ou decisões arquiteturais. Se encontrar uma lacuna ou contradição, explique e pare antes de tomar essa decisão.
- Não inclua credenciais, tokens ou outros segredos nos arquivos versionados.
- Não faça alterações em outros serviços, a menos que a issue peça explicitamente.
- Não faça merge do Pull Request.

## Forma de trabalho

1. Resuma o que entendeu da tarefa e indique quais arquivos pretende alterar.
2. Faça a menor alteração que cumpra os critérios da issue.
3. Explique as mudanças de forma simples.
4. Execute as verificações ou testes definidos na issue e informe os resultados. Se não conseguir executá-los, explique o motivo.
5. Ao terminar, liste os arquivos alterados, os comandos executados e qualquer pendência para revisão humana.

Aguarde minha confirmação do plano antes de começar a editar arquivos.