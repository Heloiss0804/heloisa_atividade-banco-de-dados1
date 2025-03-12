
```sql
INSERT INTO cursos (nome,carga_horaria,professor_id)
VALUES(
    'Front-End', 40, NULL
),
(
    'Back-End', 80, NULL
),
(
    'UX,UI', 30, NULL
),
(
    'Figma', 10, NULL
),
(
    'Rede de computadores', 100, NULL
)
;
```

```sql
INSERT INTO professores (nome,area_de_atuacao,curso_id)
VALUES(
    'Jon Oliva', 'infra', 5  
),
(
    'Lemmy Kilmister', 'design', 4
),
(
    'Neil Peart','design' , 3
),
(
    'Ozzy Osbourne', 'desenvolvimento', 2
),
(
    'David Gilmour', 'desenvolvimento', 1
)
;
```

```sql
UPDATE cursos SET professor_id = 1
WHERE id = 5;
UPDATE cursos SET professor_id = 2
WHERE id = 4;
UPDATE cursos SET professor_id = 3
WHERE id = 3;
UPDATE cursos SET professor_id = 4
WHERE id = 2;
UPDATE cursos SET professor_id = 5
WHERE id = 1;

```

```sql
INSERT INTO alunos (nome,data_de_nascimento,primeira_nota,segunda_nota,curso_id)
VALUES  ('Ana Souza', '2000-05-12', 8.5, 7.0, 2),
('Bruno Lima', '1999-08-25', 6.0, 7.5, 4),
('Carlos Mendes', '2001-02-10', 9.0, 8.5, 5),
('Daniela Rocha', '2000-11-03', 7.5, 6.5, 3),
('Eduardo Martins', '1998-07-21', 5.5, 6.0, 4),
('Fernanda Alves', '2002-03-15', 8.0, 9.0, 1),
('Gustavo Ribeiro', '2000-09-30', 7.0, 7.5, 3),
('Helena Castro', '1999-12-14', 6.5, 5.5, 4),
('Igor Nunes', '2001-06-05', 9.5, 8.0, 1),
('Juliana Freitas', '1998-04-20', 7.0, 7.0, 5);

```

### Etapa 4 Final

### Exercicio 1
```sql
SELECT nome, data_de_nascimento 
FROM alunos 
WHERE data_de_nascimento < '2009-01-01';
```

### Exercicio 2
```sql
SELECT nome, 
       (primeira_nota + segunda_nota) AS soma_notas,
       ROUND((primeira_nota + segunda_nota) / 2, 2) AS media_notas
FROM alunos;

```
### Exercicio 3
```sql
SELECT 
    nome AS curso, 
    carga_horaria, 
    (carga_horaria * 0.25) AS limite_faltas
FROM cursos
ORDER BY nome ASC;

```
### Exercicio 4
```sql
SELECT nome 
FROM professores 
WHERE area_de_atuacao = 'Desenvolvimento';

```
### Exercicio 5
```sql
SELECT area_de_atuacao, COUNT(*) AS quantidade_professores FROM professores WHERE area_de_atuacao IN ('Design', 'Infra', 'Desenvolvimento') GROUP BY area_de_atuacao;

```
### Exercicio 6
```sql
SELECT 
    a.nome AS aluno, 
    c.nome AS curso, 
    c.carga_horaria 
FROM alunos a
JOIN cursos c ON a.curso_id = c.id;

```
### Exercicio 7

```sql
SELECT 
    p.nome AS professor, 
    c.nome AS curso 
FROM professores p
JOIN cursos c ON p.curso_id = c.id
ORDER BY p.nome ASC;

```

### Exercicio 8

```sql
SELECT 
    a.nome AS aluno, 
    c.nome AS curso, 
    p.nome AS professor
FROM alunos a
JOIN cursos c ON a.curso_id = c.id
JOIN professores p ON c.professor_id = p.id;


```

### Exercicio 9

```sql
SELECT 
  c.nome AS curso, COUNT(a.id) AS quantidade_alunos 
FROM cursos c LEFT JOIN alunos a 
ON c.id = a.curso_id GROUP BY c.nome 
ORDER BY quantidade_alunos DESC;


```


