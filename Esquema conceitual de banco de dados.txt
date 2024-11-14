# Sistema de Controle de Ordens de Serviço - Oficina Mecânica

Este projeto é um sistema de controle e gerenciamento de ordens de serviço (OS) para uma oficina mecânica. Ele foi desenvolvido para otimizar o processo de execução de serviços de manutenção em veículos, incluindo a gestão de clientes, veículos, mecânicos, serviços e peças.

## Esquema Conceitual

O sistema envolve as seguintes entidades principais:

- **Cliente**: Responsável pela solicitação dos serviços.
- **Veículo**: O veículo que será atendido pela oficina.
- **Mecânico**: Os profissionais que executam os serviços.
- **Serviço**: Tipos de serviços oferecidos pela oficina.
- **Peça**: Peças utilizadas nos serviços.
- **Ordem de Serviço (OS)**: Registra os detalhes de cada solicitação de serviço.
- **Equipe**: Equipes responsáveis pela execução dos serviços.
- **Peça na OS**: Relacionamento entre as peças e a ordem de serviço.

### Relacionamentos

- Um **cliente** pode ter vários **veículos**.
- Um **veículo** pode ter várias **ordens de serviço**.
- Um **mecânico** pode ser designado para várias **ordens de serviço**.
- Uma **ordem de serviço** pode ter várias **peças**.
- Uma **ordem de serviço** pode ter várias **equipes**.

### Estrutura do Banco de Dados

O banco de dados foi modelado com base no diagrama entidade-relacionamento (ER) e está pronto para ser implementado. As tabelas incluem todas as informações necessárias para registrar clientes, veículos, serviços, peças e ordens de serviço.

## Como Executar

1. Clone o repositório.
2. Importe o esquema do banco de dados para o seu sistema de gerenciamento de banco de dados (SGBD) favorito.
3. Insira os dados de exemplo e execute as consultas SQL para testar o sistema.

## License

Este projeto está licenciado sob a MIT License.

