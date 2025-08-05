# 📚 Guia Completo de Estudos MySQL

Este guia contém anotações, comandos e exercícios resolvidos para estudos de MySQL.

---

## 📌 Tipos Primitivos
```
Inteiro --> TinyInt, SmallInt, Int, MediumInt, BigInt
```

## 📌 Numérico
```
Real --> Decimal, Float , Double, Real
Lógico --> Bit, Boolean
```

## 📌 Data/Tempo
```
Date, DateTime, TimeStamp, Time, Year
```

## 📌 Texto e Caracteres
```
Caractere --> Char, Varchar
Texto --> TinyText, Text, MediumText, LongText
```

## 📌 Literal
```
Binário --> TinyBlob, Blob, MediumBlob, LongBlob
Coleção --> Enum, Set
```

## 📌 Espacial
```
Geometry, Point, Polygon, MultiPolygon
```

---

## 📌 Códigos para MySQL

### Criar Banco de Dados
```sql
CREATE DATABASE nome_do_banco;
```

### Criar Tabela
```sql
CREATE TABLE clientes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    telefone VARCHAR(20),
    data_cadastro DATE DEFAULT CURRENT_DATE
);
```

### Alterar Estrutura
```sql
ALTER TABLE Pessoas ADD COLUMN profissao VARCHAR(10);
ALTER TABLE Pessoas DROP COLUMN profissao;
ALTER TABLE Pessoas MODIFY COLUMN profissao VARCHAR(20);
ALTER TABLE Pessoas CHANGE COLUMN profissao prof VARCHAR(20);
ALTER TABLE Pessoas RENAME TO Gafanhotos;
```

### Chaves
```sql
ALTER TABLE tabela ADD PRIMARY KEY (id);
ALTER TABLE tabela ADD FOREIGN KEY (coluna) REFERENCES outra_tabela(id);
```

---

## 📌 DDL (Data Definition Language)
```
CREATE, ALTER, DROP
```

## 📌 DML (Data Manipulation Language)
```
INSERT, UPDATE, DELETE, TRUNCATE, SELECT
```

---

## 📌 Exercícios Resolvidos

- **Lista de gafanhotas (F) e gafanhotos (M):**
```sql
SELECT nome FROM gafanhotos WHERE sexo = 'F';
SELECT nome FROM gafanhotos WHERE sexo = 'M';
```

- **Nascidos entre 2000 e 2015:**
```sql
SELECT * FROM gafanhotos
WHERE data_nascimento BETWEEN '2000-01-01' AND '2015-12-31';
```

- **Homens programadores:**
```sql
SELECT nome FROM gafanhotos
WHERE sexo = 'M' AND profissao = 'Programador';
```

- **Mulheres brasileiras com nome iniciando em J:**
```sql
SELECT nome FROM gafanhotos
WHERE nome LIKE 'J%' AND nacionalidade = 'Brasil';
```

- **Homens com 'Silva' no nome, não brasileiros e peso < 100Kg:**
```sql
SELECT nome FROM gafanhotos
WHERE nome LIKE '%Silva%' AND nacionalidade <> 'Brasil' AND peso < 100;
```

- **Maior altura de homens brasileiros:**
```sql
SELECT MAX(altura) FROM gafanhotos
WHERE sexo = 'M' AND nacionalidade = 'Brasil';
```

- **Média de peso:**
```sql
SELECT ROUND(AVG(peso), 2) FROM gafanhotos;
```

- **Menor peso de mulheres estrangeiras nascidas entre 1990 e 2000:**
```sql
SELECT MIN(peso) FROM gafanhotos
WHERE sexo = 'F' AND nacionalidade <> 'Brasil'
AND nascimento BETWEEN '1990-01-01' AND '2000-12-31';
```

- **Profissões e quantitativo:**
```sql
SELECT profissao, COUNT(*) FROM gafanhotos GROUP BY profissao ORDER BY COUNT(*) DESC;
```

---

> ✍️ **Autor:** CrownBR  
> 📅 **Última atualização:** Agosto/2025
