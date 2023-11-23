# Banco-de-dados-II
Exercício - Pratico II

Crie um banco de dados, adicione tabelas e determine quais são os atributos de cada uma. Em seguida, execute um trigger que se relacione com algum comando, como insert, select, delete ou update.



**Crie um banco de dados chamado "Empresa":

CREATE DATABASE Empresa;

Use o banco de dados "Empresa":

USE Empresa;

Crie uma tabela chamada "Funcionarios" com os atributos "id" (chave primária), "nome", "cargo" e "salario":

CREATE TABLE Funcionarios ( id INT PRIMARY KEY, nome VARCHAR(50), cargo VARCHAR(50), salario DECIMAL(10, 2) );

Crie uma tabela chamada "Departamentos" com os atributos "id" (chave primária), "nome" e "localizacao":

CREATE TABLE Departamentos ( id INT PRIMARY KEY, nome VARCHAR(50), localizacao VARCHAR(50) );

Crie um trigger chamado "trigger_novo_funcionario" que é executado após a inserção de um novo funcionário na tabela "Funcionarios". Esse trigger vai atualizar uma tabela chamada "Relatorio" quando um novo funcionário for adicionado:

DELIMITER //

CREATE TRIGGER trigger_novo_funcionario AFTER INSERT ON Funcionarios FOR EACH ROW BEGIN INSERT INTO Relatorio (data, descricao) VALUES (CURDATE(), CONCAT('Novo funcionário adicionado: ', NEW.nome)); END //

DELIMITER ;

A tabela "Relatorio" deve conter os atributos "id" (chave primária), "data" e "descricao":

CREATE TABLE Relatorio ( id INT PRIMARY KEY, data DATE, descricao TEXT );

Agora, sempre que um novo funcionário for adicionado na tabela "Funcionarios", o trigger "trigger_novo_funcionario" será executado automaticamente e adicionará um novo registro na tabela "Relatorio" com a data atual e uma descrição indicando qual foi o novo funcionário adicionado.**
