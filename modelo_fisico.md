### Criando a tabela

```sql
CREATE DATABASE tecinternet_escola_heloisa CHARACTER SET utf8mb4;
```
## criando tabela cursos

```sql
CREATE TABLE cursos  (
   id INT NULL  PRIMARY KEY AUTO_INCREMENT,
   nome VARCHAR(45) NOT NULL,
   carga_horaria INT NOT NULL,
   professor_id INT NULL

);
```

## criando tabela professores

```sql
 CREATE TABLE professores (
   id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
   curso_id VARCHAR (200) NOT NULL,
   area_de_atuacao ENUM('design','desenvolvimento','infra') NOT NULL,
   nome VARCHAR(100) NOT NULL,

);
```
## Criando tabela aluno

```sql
 CREATE TABLE alunos (
   id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
   data_de_nascimento DATE NOT NULL,
   primeira_nota DECIMAL(4,2) NOT NULL,
   segunda_nota DECIMAL(4,2) NOT NULL,
   curso_id INT NOT NULL,
   nome VARCHAR(100)

 
);
```

### Criando Relacionamentos

```sql
ALTER TABLE cursos
   ADD CONSTRAINT fk_curso_professor

    FOREIGN KEY (professor_id) REFERENCES professores(id);
```

```sql
ALTER TABLE professores
   ADD CONSTRAINT fk_professor_curso

    FOREIGN KEY (curso_id) REFERENCES cursos(id);
```

```sql
ALTER TABLE alunos
   ADD CONSTRAINT fk_alunos_curso

    FOREIGN KEY (curso_id) REFERENCES cursos(id);
```
