# Projeto de Controle de Estoque

## Descrição

Este projeto é um sistema de controle de estoque para gerenciar os produtos de uma loja. O sistema permite que os usuários cadastrem, consultem, atualizem e excluam produtos, além de registrar entradas e saídas de estoque e gerar relatórios.

## Estrutura da Base de Dados

### Tabelas

1. **Fornecedores**
    - `fornecedor_id` (INT, AUTO_INCREMENT, PRIMARY KEY)
    - `nome` (VARCHAR(100))
    - `contato` (VARCHAR(100))

2. **Produtos**
    - `produto_id` (INT, AUTO_INCREMENT, PRIMARY KEY)
    - `nome` (VARCHAR(100))
    - `descricao` (VARCHAR(255))
    - `preco` (DECIMAL(10, 2))
    - `quantidade_em_estoque` (INT)
    - `fornecedor_id` (INT, FOREIGN KEY)

3. **Entradas_de_Estoque**
    - `entrada_id` (INT, AUTO_INCREMENT, PRIMARY KEY)
    - `produto_id` (INT, FOREIGN KEY)
    - `data` (DATE)
    - `quantidade` (INT)
    - `preco_unitario` (DECIMAL(10, 2))

4. **Saidas_de_Estoque**
    - `saida_id` (INT, AUTO_INCREMENT, PRIMARY KEY)
    - `produto_id` (INT, FOREIGN KEY)
    - `data` (DATE)
    - `quantidade` (INT)
    - `preco_unitario` (DECIMAL(10, 2))

### Script SQL para Criação das Tabelas

```sql
-- Criação da Tabela de Fornecedores
CREATE TABLE Fornecedores (
    fornecedor_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    contato VARCHAR(100)
);

-- Criação da Tabela de Produtos
CREATE TABLE Produtos (
    produto_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    descricao VARCHAR(255),
    preco DECIMAL(10, 2),
    quantidade_em_estoque INT,
    fornecedor_id INT,
    FOREIGN KEY (fornecedor_id) REFERENCES Fornecedores(fornecedor_id)
);

-- Criação da Tabela de Entradas de Estoque
CREATE TABLE Entradas_de_Estoque (
    entrada_id INT AUTO_INCREMENT PRIMARY KEY,
    produto_id INT,
    data DATE,
    quantidade INT,
    preco_unitario DECIMAL(10, 2),
    FOREIGN KEY (produto_id) REFERENCES Produtos(produto_id)
);

-- Criação da Tabela de Saídas de Estoque
CREATE TABLE Saidas_de_Estoque (
    saida_id INT AUTO_INCREMENT PRIMARY KEY,
    produto_id INT,
    data DATE,
    quantidade INT,
    preco_unitario DECIMAL(10, 2),
    FOREIGN KEY (produto_id) REFERENCES Produtos(produto_id)
);
