# Banco de dados

## SGBD (*Sistema de Gerenciamento de Banco de Dados*)
## Comandos DDL (*Data Definition Language*): São usados para definir a estrutura de um Banco de Dados.

## Logar no MYSQL:
```bash
mysql –u root -p
```	
	
## Databases:

- `show databases` - **lista Base de  Dados contida no Banco.**
- `create database` - **Cria uma Base de Bados no Banco.**
- `use livraria`;  - **você entra na Base de Dados para poder usa-lá.**
- `drop database`  - **excluir  a Base de Dados**

## Tables:

```sql
show tables;  #exibe as tabelas;
show index from professores; # mostra os indices contidos na Tabela.
describe livros;  # exibe a estrutura da Tabela.
drop table livros;   # deleta a tabela;
ALTER TABLE escola RENAME TO colegio;  # renomeia a tabela.
ALTER TABLE aluno ADD sexo char(10);  # adiciona o campo.
ALTER TABLE aluno ADD sexo char(10) AFTER data_nasc;  # adiciona o campo podendo ser after OU first.
ALTER TABLE aluno ADD primary key(cod);  # adiciona chave primaria ou se usar drop deleta.
ALTER TABLE funcionarios MODIFY cargo varchar(200); # mudou cargo de char para varchar.
ALTER TABLE aluno CHANGE idade datanasc date;  # Troca o campo idade por datanasc.
ALTER TABLE aluno DROP sexo;  # exclui o campo sexo.
CREATE TABLE aluno(
	codigo INT NOT NULL AUTO_INCREMENT,
	nome varchar(200),
	sexo char(1),
	data_nasc date,
	PRIMARY KEY (codigo))  ENGINE=INNODB;
CREATE TABLE matricula(
	id_alu INT NOT NULL,
	id_tur INT NOT NULL, 
	data_matricula date,
	INDEX id_alu(id_alu),
	INDEX id_tur(id_tur),
	FOREIGN KEY (id_alu) REFERENCES aluno(codigo),
	FOREIGN KEY (id_tur) REFERENCES turma(id_turma)) ENGINE=INNODB;
```

## Restrições da CHAVE ESTRANGEIRA:
### Depois de **REFERENCES** colocamos suas restrições ex:
```sql
REFERENCES pai(id) ON DELETE SET NULL) ENGINE=INNODB;
ON  DELETE SET NULL # Determina que quando um resgistro for excluido na tabela pai, a coluna associada na tabela filho será alterada para NULL.
ON DELETE CASCADE # A exclusão do registro na tabela pai propaga-se abrangendo também todas as ocorrencias da tabela filho.
ON DELETE NO ACTION # Caso existam referências ao registro em outras tabelas, a exclusão é cancelada. Para excluir o resgistro da tabela pai primeiro devemos excluir na tabela filho.
ON DELETE RESTRICT # Efetuaa exclusão somente se não houver referências ao resgistro em  outras tabelas filhas. Um registro na tabela pai só poderá ser excluído se não houver em referências  a ela na tabela filho. 
Tipos de Dados
CHAR # Caracteres (1 à 255) alfa numericos. “Consome todo o espaço alocado”
VARCHAR # Caracteres (1 à 255) alfa numericos. “Consome só  o espaço que usar preenchido ”
INT # números inteiros.
FLOAT # números decimais “com .”.
DATE # Referente a data. Fomato AAAA-MM-DD.
TEXT # Grande quantidades de caracteres
```

