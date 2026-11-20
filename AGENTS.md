# Instruções do projeto

## Fonte da verdade
- Antes de implementar requisitos ou arquitetura, consulte `docs/requisitos.md`, `docs/regras-de-negocio.md` e o documento de arquitetura em `docs/arquitetura-servicos`.
- Se este arquivo, o plano ou uma solicitação contradisser esses documentos, sinalize a divergência e peça uma decisão antes de codificar.
- Não presuma que pastas ou READMEs iniciais significam que endpoints ou regras já existem.

## Arquitetura e dados
- Stack acordada: Java 21, Spring Boot, Maven, Spring Cloud Gateway, React, TypeScript, Vite, PostgreSQL e JWT.
- Mantenha as responsabilidades dos serviços e os contratos REST definidos na arquitetura.
- Cada serviço acessa somente seu próprio banco lógico; não leia nem altere diretamente tabelas de outro serviço.
- Aplique autenticação e autorização no backend e nas rotas. Funcionários não podem acessar fluxo de caixa nem relatórios financeiros.
- Venda só pode ser concluída após validar o estoque; a conclusão atualiza o estoque e registra a receita conforme a arquitetura.
- Conte despesas como saída do caixa somente após pagamento.
- Não acrescente funcionalidades fora do MVP sem aprovação registrada.

## Git e configuração
- Não versione credenciais, arquivos `.env` ou segredos. Use `.env.example` sem valores reais.
- Trabalhe em branch própria e proponha alterações por Pull Request para `main`; respeite a proteção da branch e a revisão por outro integrante.
- Preserve os padrões já usados no serviço ou módulo ao qual a tarefa pertence.
