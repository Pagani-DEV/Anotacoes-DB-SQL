# Comandos DML(Data Manipulation Language):  São usados para minupular as estruturas de um banco de dados.(INSERT, UPDATE, DELETE, SELECT)

```SQL
INSERT
INSERT INTO funcionarios(nome, sexo, data_nasc) VALUES(‘Carlos’, ‘m’, 19920314);  USAR
INSERT INTO funcionarios VALUES (‘’,’Carlos’, ‘M’,19920314);

DELETE (OR, AND, XOR, <, >, <=, >=, = ,!=) (BETWEEN, IN)
DELETE FROM funcionarios;
DELETE FROM funcionarios WHERE cargo= ‘gerente’;
DELETE FROM funcionarios WHERE idade  BETWEEN 20 AND 25;
DELETE FROM funcionarios WHERE idade IN (20, 21, 22, 23, 24, 25);

UPDATE (OR, AND, XOR, <, >, <=, >=, = ,!=) (BETWEEN, IN)
UPDATE funcionarios SET nome = ‘Carlos’,  where id=10;
UPDATE funcionarios SET preco = (preco+(preco*01)) WHERE id=10 ;

SELECT (NOT,OR, AND, XOR, <, >, <=, >=, = ,!=) (IS NULL, IS NOT NULL) (DESC, LIMIT)
(CONCAT, BETWEEN, DISTINCT)(GROUP BY, COUNT, MIN, MAX, AVG, ROUND, HAVING)

SELECT * FROM mesa;
SELECT item, preco_unitario FROM cardapio ORDER BY item; 
SELECT item,  FROM cardapio ORDER BY item DESC LIMIT 5;  (MOSTRA 5 EM DECRESCENTE)
SELECT CONCAT (nome, ‘’, sobrenome) AS ‘Nome Completo’,  setor, cargo FROM funcionario ORDER BY setor, cargo;
SELECT DISTINCT setor FROM funcionarios;  (esse comando nao repete o registro de setor EX 2 vezes mesmo setor)
SELECT CONT(*) AS ‘registros’ FROM funcionarios;  (conta todos os registros da tabela) 
SELECT CONT(*) AS ‘mulheres’ FROM funcionarios WHERE sexo= ‘f’ ;   (conta todos os registros da tabela que forem mulheres)
SELECT setor, SUM(salario) AS ‘total salarios’ FROM  funcionarios GROUP BY setor; (MOSTRA OS SALARIOS SOMADOS POR SETOR, MAS COM CASAS MUITAS CASAS  DECIMAIS) 
SELECT setor,  ROUND(SUM(salario), 2) AS ‘total salarios’ FROM  funcionarios GROUP BY setor;    (MOSTRA OS SALARIOS SOMADOS MAS COM POUCAS CASAS DECIMAIS FACILITANDO A COMPREENSAO)
SELECT setor, COUNT(setor) as ‘pessoas’ FROM funcionarios GROUP BY setor HAVING (Pessoas=2);  (EXIBE DADOS APENAS DOS SETORES QUE TEM(HAVING) 2 FUNCIONARIOS)
CLAUSULAS JOIN
SELECT medicos.nome_pac, consultas.hora, consultas.data FROM pacientes, consultas WHERE pacientes.codigo=consultas.Id_paciente;
SELECT medicos.nome_med, convenios.nome_conv FROM consultas, medicos,convenios WHERE consultas.ID_medico=medicos.ID  AND consultas.ID_convenio=convenios.ID_conv AND medicos ID=1;
SELECT mesa.numero AS ‘Mesa Numero’, COUNT(*) AS ‘Vezes que foram usadas’ FROM mesa.conta WHERE conta.nr_mesa=mesa.numero GROUP BY mesa.numero ORDER BY 1;
SELECT cardapio.item, SUM(pedido.quantidade) FROM cardpio, pedido WHERE cardapio.codigo=pedido.codigo_cardapio AND pedido.codigo_cardapio=12; 
```