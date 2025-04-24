# Desenvolvimento-estudos
create database empresa1;
use empresa1;
create table cliente ( 
matricula int primary key auto_increment, 
nome varchar (60) not null,
 telefone char (14),
 email varchar (30),
 nascimento date not null
);
insert into cliente (nome,telefone,email,nascimento)
values
('Ana Beatriz Souza', '(21)91234-5678', 'ana.souza@email.com', '1990-04-15'),
('Lucas Fernandes', '(21)99876-5432', 'lucas.f@email.com', '1988-06-23'),
('Mariana Costa', '(21)98765-4321', 'mariana.c@email.com', '1995-02-10'),
('João Pedro Lima', '(21)99988-7766', 'joao.lima@email.com', '1992-08-30'),
('Carla Menezes', '(21)98877-6655', 'carla.m@email.com', '1985-11-19'),
('Gabriel Rocha', '(21)97766-5544', 'gabriel.r@email.com', '1991-03-07'),
('Fernanda Alves', '(21)96655-4433', 'fernanda.a@email.com', '1996-01-22'),
('Thiago Oliveira', '(21)95544-3322', 'thiago.o@email.com', '1989-07-13'),
('Beatriz Martins', '(21)94433-2211', 'beatriz.m@email.com', '1993-12-05'),
('Ricardo Gomes', '(21)93322-1100', 'ricardo.g@email.com', '1987-10-18'),
('Juliana Pereira', '(21)92211-0099', 'juliana.p@email.com', '1994-09-09'),
('Felipe Andrade', '(21)91100-9988', 'felipe.a@email.com', '1990-05-27'),
('Letícia Lima', '(21)90099-8877', 'leticia.l@email.com', '1997-06-14'),
('Vinícius Barros', '(21)98888-7766', 'vinicius.b@email.com', '1986-02-02'),
('Amanda Duarte', '(21)97777-6655', 'amanda.d@email.com', '1998-03-29');

create table funcionario (
codfun integer not null primary key,
nome varchar (40) not null,
depto char (2),
funcao char(20),
salario decimal (10,2),
filhos char (2),
admissao date 

);

insert into funcionario (codfun, nome, depto, funcao, salario, filhos, admissao)
values
(1, 'Carlos Andrade', 'RH', 'Analista', 3500.00, 1, '2022-01-10'),
(2, 'Fernanda Moura', 'TI', 'Desenvolvedor', 4500.50, 2, '2021-03-15'),
(3, 'João Vitor', 'TI', 'Suporte', 2800.00, 3, '2020-06-20'),
(4, 'Marina Silva', 'FI', 'Contadora', 5200.00, 4, '2019-11-01'),
(5, 'Lucas Martins', 'TI', 'Analista', 4300.00, 5, '2022-08-08'),
(6, 'Beatriz Gomes', 'RH', 'Coordenadora', 6000.00, 3, '2020-02-12'),
(7, 'Rafael Souza', 'MK', 'Designer', 3900.75, 4, '2021-10-30'),
(8, 'Juliana Dias', 'FI', 'Assistente', 2600.00, 2, '2023-04-18'),
(9, 'Pedro Henrique', 'TI', 'Desenvolvedor', 4800.00, 4, '2018-07-05'),
(10, 'Amanda Rocha', 'RH', 'Recrutadora', 3100.50, 3, '2022-09-22'),
(11, 'Renato Lima', 'MK', 'Analista', 3700.00, 1, '2021-01-01'),
(12, 'Larissa Melo', 'TI', 'Scrum Master', 5500.00, 2, '2020-05-11'),
(13, 'Thiago Costa', 'FI', 'Contador', 5100.00, 2, '2019-03-27'),
(14, 'Natália Ramos', 'MK', 'Social Media', 3300.00, 3, '2023-02-14'),
(15, 'Gustavo Nunes', 'TI', 'Arquiteto', 7000.00, 4, '2022-12-03');


-- 1)	Faça uma simulação para apresentar uma consulta com as colunas CODFUN, NOME, SALARIO com o salário somado a R$250,00.
select 
codfun,
nome, 
salario + 250.00 as salario_bonus
 from funcionario ;

-- 2)	Faça uma simulação para apresentar uma consulta com as colunas CODFUN, NOME, SALARIO com uma redução de salário de 7,5%.
select 
codfun,
nome,
salario * 0.925 as salario_reduzido
from funcionario ;

-- 3)	Apresente uma consulta de todas as colunas de todos os registros cuja função seja igual a ANALISTA.
select * from funcionario where funcao = 'Analista' ;


-- 4)	Apresentar uma consulta de todas as colunas de todos os registros cujo salário seja maior ou igual a R$1700,00.

select *  from funcionario where salario >= 1700.00;


-- 5)	Apresentar uma consulta de todas as colunas de todos os registros cujo salário seja maior ou igual a R$2000,00 dos funcionários do departamento 'RH'.

select * from funcionario where depto = 'RH' and salario >= 2000.00 ;

-- 6)	Apresentar uma consulta de todas as colunas de todos os registros dos funcionários com função Desenvolvedor ou Analista 
select * from funcionario where funcao = 'Desenvolvedor' or funcao = 'Analista';

-- 7)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem entre 2 e 4 filhos.

select * from funcionario where filhos between 2 and 4;

-- 8)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem entre 2 e 4 filhos que recebem salário inferior a R$5000,00.
select * from funcionario  where filhos between 2 and 4 and salario < 5.000;

-- 9)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem abaixo de 2 e acima de 3 filhos.
select * from funcionario where filhos< 2 or filhos>3;
-- o operador or  permite considerar  os 3 grupos.

-- 10)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem abaixo de 2 e acima de 3 filhos cuja consulta exiba somente os registros
-- dos funcionários que possuem filhos.
select * from funcionario where filhos <2 or filhos >3 xor filhos>1 ;

-- 11)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem entre 2 e 3 filhos, utilizando o operador IN.
select * from funcionario  where filhos in (2, 3) ;

-- 12)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem o sobrenome Dias.
select * from funcionario where nome like '%Dias%';

-- 13)	Apresentar uma consulta de todas as colunas de todos os registros de todos os funcionários que possuem o nome começando por Thi.
select * from funcionario where nome like 'Thi%';

-- 14)	Quais são os funcionários que possuem a palavra Ramos como parte de seus nomes? Apresentar apenas os nomes completos.
select * from funcionario where nome like '%Ramos%' ;

-- 15)	Qual é o nome (na verdade, o número) do departamento do Contador e do analistas?
select depto from funcionario where funcao ='Contador' and funcao = 'Analista';

-- 16)	Listar os funcionários de códigos 2,5 e 9. Apresentar apenas os códigos, nomes e departamentos.
select codfun,nome,depto from funcionario where codfun in (2, 5,9);

-- 17)	Listar os nomes e departamentos de todos os funcionários que não sejam do departamento MK.
select nome, depto from funcionario where not (depto = 'MK');


-- 18)	Apresentar uma consulta de todos os campos de todos os registros dos funcionários que possuem em qualquer posição de seus nomes a palavra SILVA ou a palavra NUNES.
select * from funcionario where nome like '%Silva%' or '%Nunes%';

-- 19)	Apresentar uma consulta de todos os campos de todos os registros cujo salário seja diferente de R$2000,00.
select * from funcionario where salario  <> 2000.00;

-- 20)	Apresente o comando SELECT que realiza o cálculo de 48 % de 3000.
select 0.48*3000;

use  empresa1;
-- Exercícios sobre Funções do MySQL
-- Responder as questões abaixo com o comando exato no MySQL que traz a resposta correta (Um único comando por questão)


-- 1) Qual é o número médio de filhos por funcionário da empresa?
SELECT AVG(filhos) FROM funcionario;

-- 2) Qual é o número médio de filhos por funcionário da empresa que pertence ao departamento TI?
SELECT AVG(filhos) FROM funcionario where depto = 'TI';

-- 3) Qual é o valor da soma dos salários pagos aos funcionários do departamento TI?
SELECT SUM(salario) FROM funcionario WHERE depto = 'TI';

-- 4) Quantos funcionários estão no departamento Mk?
SELECT COUNT(nome) FROM funcionario WHERE depto = 'MK';

-- 5) Quantos funcionários no departamento TI ganham mais de R$2000,00?
SELECT COUNT(DISTINCT depto ) FROM funcionario where depto = 'TI' and salario > 2000.00;

-- 6) Quantos funcionários no departamento RH ganham  R$3500,00?
select count(depto) from funcionario where depto= 'RH' and salario = 3500.00;

-- 7) Quantos funcionários no departamento MK ganham entre R$1000,00 e R$4000,00?
SELECT COUNT(nome) FROM funcionario WHERE depto = 'MK' and salario between 1000.00 and 4000.00;

-- 8) Quantos funcionários da empresa possuem o sobrenome Silva?
select count(nome) from funcionario where nome like'%Silva%';

-- 9) Qual é o maior valor de salário pago para o departamento TI?
SELECT MAX(salario) FROM funcionario where depto= 'TI';

-- 10) Quanto a empresa paga para todos os analistas?
select sum(salario) from funcionario where funcao = 'Analista';

-- 11) Listar os nomes de todos os funcionários admitidos no dia 10 de qualquer mês. 
SELECT nome
FROM funcionario where day(admissao) = 10; 
select* from funcionario;

-- 12) Listar os nomes e as datas de admissão de todos os funcionários admitidos entre o dia 5 e o dia 10 de qualquer mês. 

select nome, admissao from funcionario where day (admissao) between  5 and 10 ;

-- 13) Listar os nomes e as datas de admissão de todos os funcionários admitidos entre o dia 5 e o dia 10 de qualquer mês ordenado de forma ascendente por data. 
select nome, admissao 
from funcionario
 where day (admissao) between 5 and 10
order by admissao asc ;
 
-- 14) Listar os nomes e as datas de admissão de todos os funcionários admitidos entre o dia 5 e o dia 10 de qualquer mês ordenado de forma descendente por data. 
select nome , admissao from funcionario where day (admissao) between 5 and 10 
order by admissao desc ;
select * from funcionario;

-- 15) Listar todos os funcionários admitidos antes de 20 de junho de 2020. 
select nome from funcionario where day (admissao) < 2020-06-20;

-- 16) Listar os nomes, data de admissão e o nome dos meses de admissão de todos os funcionários do departamento TI. 
select nome,  MONTHNAME(admissao) 
FROM funcionario 
where depto ='TI';

-- 17) Listar os nomes e os departamentos de todos os funcionários em letras minúsculas que pertençam aos departamentos TI e RH. 
select nome, depto from funcionario where depto 'RH' and 'TI'
SELECT LOWER(‘SENAI MARACANÃ’);
-- 18) Listar os nomes, departamentos e as datas de admissão de todos os funcionários admitidos entre o dia 5 e o dia 10 de qualquer mês dos departamentos RH e  MK. 
select nome, depto, admissao from funcionario where day (admissao) between  5 and 10 and depto = 'RH' and 'MK';

-- 19) Listar os nomes , departamentos, funções e as datas de admissão de todos os funcionários admitidos entre o 1º e o dia 15 que sejam analistas. 
 select nome, depto, funcao, admissao from funcionario where day (admissao) between 1 and 15 and funcao = 'Analista';
 
-- 20) Quanto a empresa paga para os analistas do departamento TI? 
select sum(salario) from funcionario where depto = 'TI';







