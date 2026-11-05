# PostgreSQL local

## Pré-requisitos
- Docker Desktop instalado e com o Engine em execução.

## Configuração
1. Copie `.env.example` e renomeie a cópia para `.env` nesta pasta.
2. Inicie os serviços pelo VS Code usando **Run All Services** no arquivo `docker-compose.yml`.

Na primeira inicialização, o Docker baixa a imagem do PostgreSQL e cria os quatro bancos lógicos definidos em `init/01-create-databases.sql`.

## Bancos criados
- `ferragista_auth`
- `ferragista_estoque`
- `ferragista_vendas`
- `ferragista_financeiro`

O PostgreSQL fica disponível localmente na porta `5432`. O arquivo `.env` contém configuração local e não deve ser enviado ao GitHub.
