# Regras de Negócio da Ferragista

**Versão:** documento de trabalho consolidado  
**Base:** regras registradas no `trabalho.pdf`, proposta técnica e decisões confirmadas para o projeto.

> As regras que estavam marcadas como deduzidas ou pendentes no documento-base foram confirmadas pelo responsável do projeto. As regras abaixo atualizam o texto para refletir as decisões atuais.

| Código | Regra | Descrição |
|---|---|---|
| RN01 | Verificação e baixa de estoque | Antes de concluir uma venda, o sistema verifica se há estoque suficiente de cada produto. Ao concluir a venda, atualiza as quantidades correspondentes no estoque. |
| RN02 | Venda gera receita | Uma venda concluída gera a receita correspondente no controle financeiro. |
| RN03 | Despesa paga compõe a saída | Uma despesa só é contabilizada como saída do fluxo de caixa quando estiver paga. Despesas não pagas não reduzem o saldo do fluxo. |
| RN04 | Cálculo do saldo | Para o período consultado, o saldo corresponde ao total das entradas menos o total das despesas pagas. |
| RN05 | Quantidades vendidas | A venda pode conter vários produtos. As quantidades devem ser positivas e não podem exceder o estoque disponível. |
| RN06 | Valores e datas válidos | Vendas, receitas e despesas devem possuir valores positivos e uma data associada. |
| RN07 | Acesso por perfil | O proprietário pode acessar todas as funcionalidades. O funcionário pode operar vendas e estoque e registrar/editar receitas e despesas, mas não pode consultar fluxo de caixa nem relatórios financeiros. |
| RN08 | Relatórios baseados em registros | Os relatórios consideram apenas vendas, receitas e despesas efetivamente registradas no sistema. |
| RN09 | Valores da venda | A venda registra os valores praticados no momento da operação. Não haverá aplicação de descontos no MVP. |

## Relação com requisitos

- RN01 e RN05 relacionam-se a RF04 e RF05.
- RN02 relaciona-se a RF05 e RF06.
- RN03 e RN04 relacionam-se a RF07 e RF08.
- RN06 relaciona-se a RF05, RF06 e RF07.
- RN07 relaciona-se a RF01, RF02, RF08 e RF09.
- RN08 relaciona-se a RF08 e RF09.
- RN09 relaciona-se a RF05.

## Observação de implementação

A conclusão de uma venda precisa manter coerentes o registro da venda, a atualização do estoque e a criação da receita. O tratamento técnico de falhas entre serviços será detalhado na arquitetura e nas tarefas de implementação, sem alterar as regras de negócio acima.
