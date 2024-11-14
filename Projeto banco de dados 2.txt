-- Tabela Clientes
CREATE TABLE Clientes (
    id_cliente INT PRIMARY KEY,
    nome VARCHAR(100),
    telefone VARCHAR(15),
    email VARCHAR(100)
);

-- Tabela Funcionários
CREATE TABLE Funcionarios (
    id_funcionario INT PRIMARY KEY,
    nome VARCHAR(100),
    especialidade VARCHAR(50)
);

-- Tabela Serviços
CREATE TABLE Servicos (
    id_servico INT PRIMARY KEY,
    descricao VARCHAR(255),
    preco DECIMAL(10, 2)
);

-- Tabela Atendimentos
CREATE TABLE Atendimentos (
    id_atendimento INT PRIMARY KEY,
    id_cliente INT,
    id_funcionario INT,
    id_servico INT,
    data_atendimento DATE,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente),
    FOREIGN KEY (id_funcionario) REFERENCES Funcionarios(id_funcionario),
    FOREIGN KEY (id_servico) REFERENCES Servicos(id_servico)
);

-- Tabela Peças
CREATE TABLE Pecas (
    id_peca INT PRIMARY KEY,
    descricao VARCHAR(255),
    preco_unitario DECIMAL(10, 2)
);

-- Tabela Estoque
CREATE TABLE Estoque (
    id_peca INT,
    quantidade_disponivel INT,
    FOREIGN KEY (id_peca) REFERENCES Pecas(id_peca)
);
-- Inserção de Clientes
INSERT INTO Clientes (id_cliente, nome, telefone, email) VALUES
(1, 'Carlos Silva', '123456789', 'carlos@gmail.com'),
(2, 'Ana Costa', '987654321', 'ana@gmail.com');

-- Inserção de Funcionários
INSERT INTO Funcionarios (id_funcionario, nome, especialidade) VALUES
(1, 'João Souza', 'Mecânico'),
(2, 'Maria Oliveira', 'Eletricista');

-- Inserção de Serviços
INSERT INTO Servicos (id_servico, descricao, preco) VALUES
(1, 'Troca de óleo', 50.00),
(2, 'Revisão de motor', 200.00);

-- Inserção de Peças
INSERT INTO Pecas (id_peca, descricao, preco_unitario) VALUES
(1, 'Filtro de óleo', 10.00),
(2, 'Bateria', 150.00);

-- Inserção de Estoque
INSERT INTO Estoque (id_peca, quantidade_disponivel) VALUES
(1, 100),
(2, 50);

-- Inserção de Atendimentos
INSERT INTO Atendimentos (id_atendimento, id_cliente, id_funcionario, id_servico, data_atendimento) VALUES
(1, 1, 1, 1, '2024-11-10'),
(2, 2, 2, 2, '2024-11-12');
SELECT * FROM Clientes;
SELECT nome, telefone FROM Clientes WHERE nome = 'Carlos Silva';

SELECT id_servico, COUNT(id_atendimento) AS num_atendimentos
FROM Atendimentos
GROUP BY id_servico
HAVING COUNT(id_atendimento) > 1;
SELECT p.descricao, SUM(e.quantidade_disponivel) AS total_estoque
FROM Pecas p
JOIN Estoque e ON p.id_peca = e.id_peca
WHERE p.preco_unitario > 50
GROUP BY p.descricao
HAVING SUM(e.quantidade_disponivel) > 20;
SELECT c.nome AS cliente, f.nome AS funcionario, s.descricao AS servico, a.data_atendimento
FROM Atendimentos a
JOIN Clientes c ON a.id_cliente = c.id_cliente
JOIN Funcionarios f ON a.id_funcionario = f.id_funcionario
JOIN Servicos s ON a.id_servico = s.id_servico;
