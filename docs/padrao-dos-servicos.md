# Padrão técnico dos serviços

**Status:** rascunho para revisão do grupo.

Este documento registra as decisões já confirmadas e as convenções propostas para manter os serviços compatíveis. Itens marcados como **proposta** ainda precisam da revisão do grupo.

## 1. Decisões confirmadas

- Backend em Java 21, Spring Boot e Maven.
- Quatro serviços de negócio: Auth/Users, Product/Stock, Sales e Financial.
- PostgreSQL em uma instância, com quatro bancos lógicos:
  - `ferragista_auth`
  - `ferragista_estoque`
  - `ferragista_vendas`
  - `ferragista_financeiro`
- Comunicação entre serviços por APIs REST síncronas com JSON.
- API Gateway como entrada para as chamadas do frontend.
- JWT para autenticação.
- Auth Service será o serviço piloto para validar o padrão.

## 2. Organização sugerida de cada serviço

**Proposta:** usar a mesma separação de responsabilidades em todos os serviços:

- `controller/`: recebe requisições HTTP.
- `dto/`: contém os dados de entrada e saída da API.
- `service/`: concentra as regras e operações do serviço.
- `repository/`: acessa o banco de dados.
- `entity/`: representa os dados persistidos.
- `exception/`: contém exceções e tratamento de erros.

Os nomes das pastas podem ser ajustados pelo grupo, mas devem permanecer iguais entre os serviços. Cada serviço deve ter seu próprio `pom.xml`, `README.md` e configuração.

## 3. Responsabilidade pelos dados

- Cada serviço acessa somente o banco lógico sob sua responsabilidade.
- Um serviço não consulta diretamente as tabelas de outro serviço.
- Quando precisar de informações de outro serviço, utiliza a API REST correspondente.
- Senhas e tokens não devem ser gravados no repositório.

## 4. Convenções de API propostas

**Proposta para revisão:**

- Usar JSON nas requisições e respostas.
- Agrupar rotas sob `/api/v1`.
- Usar nomes de recursos no plural, por exemplo: `/api/v1/products`.
- Utilizar códigos HTTP de acordo com o resultado da operação.
- Retornar mensagens de erro claras, sem expor detalhes internos ou credenciais.
- Manter DTOs separados das entidades do banco.

O grupo deve confirmar o padrão de rotas e o formato comum das respostas de erro antes de implementá-los.

## 5. Configuração

- Manter configurações específicas fora do código sempre que possível.
- Usar variáveis de ambiente para credenciais e endereços de serviços.
- Cada serviço deve documentar no README como configurar e executar localmente.
- O arquivo `.env` local não deve ser enviado ao Git; o repositório pode conter um exemplo sem segredos.

## 6. Regras de implementação

- Manter controllers focados em HTTP; regras de negócio ficam na camada de serviço.
- Validar dados recebidos pela API.
- Usar nomes claros e consistentes em classes, métodos e variáveis.
- Não adicionar bibliotecas ou decisões arquiteturais sem necessidade para a tarefa.
- Antes de alterar contratos usados por outros serviços, conversar com o grupo e atualizar a documentação.

## 7. Itens que o grupo ainda deve revisar

## 7. Padrões técnicos adotados para o MVP

### Pacotes Java

Usar a mesma raiz de pacote em todos os serviços:

- Auth Service: `br.com.ferragista.auth`
- Product/Stock Service: `br.com.ferragista.productstock`
- Sales Service: `br.com.ferragista.sales`
- Financial Service: `br.com.ferragista.financial`

Os nomes devem ser escritos em minúsculas e sem hífens.

### APIs REST

- As APIs usam JSON.
- As rotas começam com `/api/v1`.
- Os recursos usam nomes no plural, em inglês e em minúsculas, como `/api/v1/products` e `/api/v1/sales`.
- Usar os métodos HTTP conforme a operação: `GET` para consulta, `POST` para criação, `PUT` para atualização completa e `DELETE` para exclusão, quando aplicável.
- Usar códigos HTTP de acordo com o resultado. Como referência: `200` para sucesso, `201` para criação, `204` para sucesso sem conteúdo, `400` para dados inválidos, `401` para falta de autenticação, `403` para falta de permissão, `404` para recurso inexistente e `500` para erro inesperado.

### Respostas de erro

As APIs devem retornar erros em JSON usando os mesmos campos:

- `timestamp`: data e hora do erro.
- `status`: código HTTP.
- `code`: código curto e estável do erro, como `VALIDATION_ERROR`.
- `message`: mensagem compreensível para quem chamou a API.
- `path`: rota que recebeu a requisição.

Não retornar senhas, tokens, stack traces ou detalhes internos na mensagem.

### Autenticação e chamadas entre serviços

- O Auth Service autentica o usuário e emite o JWT.
- O API Gateway é a única entrada do frontend e encaminha as chamadas ao serviço correspondente.
- O Gateway encaminha o cabeçalho `Authorization` nas chamadas.
- Cada serviço valida o JWT recebido e aplica as permissões necessárias às próprias operações.
- As chamadas internas entre serviços encaminham o JWT do usuário.
- Para o MVP, usar uma chave compartilhada configurada por variável de ambiente (`JWT_SECRET`). A chave real não pode ser commitada nem publicada.

### Comunicação entre serviços

- Usar o `RestClient` do Spring para chamadas REST síncronas.
- Manter cada chamada limitada aos dados que o serviço destinatário precisa.
- Tratar falhas de comunicação com respostas de erro claras; não fingir que uma operação integrada foi concluída quando algum serviço necessário falhou.

### Configuração e credenciais

- Manter a configuração de cada serviço em `src/main/resources/application.yml`.
- Obter credenciais e endereços por variáveis de ambiente.
- Manter arquivos `.env` locais fora do Git.
- O repositório pode conter arquivos de exemplo, como `.env.example`, sem senhas ou chaves reais.
- Cada serviço acessa somente o banco lógico sob sua responsabilidade.

### Estrutura comum dos serviços

Todos os serviços devem usar a mesma divisão básica:

- `controller/`: entrada HTTP e respostas da API.
- `dto/`: dados recebidos e enviados pela API.
- `service/`: regras de negócio.
- `repository/`: acesso ao banco de dados.
- `entity/`: dados persistidos.
- `exception/`: erros e tratamento de exceções.

Os controllers não devem concentrar regras de negócio. Os DTOs devem ser separados das entidades persistidas.

### Revisão do padrão

Este padrão será aplicado primeiro no Auth Service. O grupo revisará essa implementação em um Pull Request; após a revisão, o mesmo padrão será usado nos outros serviços. Mudanças posteriores devem ser combinadas pelo grupo e registradas na documentação.

## 8. Serviço piloto

O Auth Service será usado primeiro para testar a estrutura, as configurações e as convenções propostas. Depois da revisão do grupo, o padrão aprovado será replicado nos demais serviços.