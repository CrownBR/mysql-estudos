# 📚 Exercícios de MySQL

Este documento contém anotações e exemplos práticos resolvidos no MySQL.

---

## 1️⃣ Lista com o nome de todas as gafanhotas ou gafanhotos `F` ou `M`
```sql
SELECT nome
FROM gafanhotos
WHERE sexo = 'F';

SELECT nome
FROM gafanhotos
WHERE sexo = 'M';
```

---

## 2️⃣ Dados de quem nasceu entre `01/Jan/2000` e `31/Dez/2015`
```sql
SELECT *
FROM gafanhotos
WHERE data_nascimento >= '2000-01-01'
  AND data_nascimento <= '2015-12-31';
```

---

## 3️⃣ Homens que trabalham como Programadores
```sql
SELECT nome
FROM gafanhotos
WHERE sexo = 'M'
  AND profissao = 'Programador';
```

---

## 4️⃣ Mulheres nascidas no Brasil e cujo nome começa com "J"
```sql
SELECT nome, nacionalidade
FROM gafanhotos
WHERE nome LIKE 'J%' 
  AND nacionalidade = 'Brasil';
```

---

## 5️⃣ Homens com "Silva" no nome, que **não** nasceram no Brasil e pesam menos de 100 kg
```sql
SELECT nome, nacionalidade, peso
FROM gafanhotos
WHERE nome LIKE '%Silva%' 
  AND nacionalidade <> 'Brasil'
  AND peso < 100;
```

---

## 6️⃣ Maior altura entre homens que moram no Brasil
```sql
SELECT nome, altura, nacionalidade
FROM gafanhotos
WHERE sexo = 'M' 
  AND nacionalidade = 'Brasil'
  AND altura = (
    SELECT MAX(altura)
    FROM gafanhotos
    WHERE sexo = 'M' AND nacionalidade = 'Brasil'
);
```

---

## 7️⃣ Média de peso dos gafanhotos cadastrados
```sql
SELECT ROUND(AVG(peso), 2) AS media_peso
FROM gafanhotos;
```

---

## 8️⃣ Menor peso entre mulheres nascidas fora do Brasil entre `01/Jan/1990` e `31/Dez/2000`
```sql
SELECT MIN(peso) AS menor_peso
FROM gafanhotos
WHERE sexo = 'F'
  AND nacionalidade <> 'Brasil'
  AND nascimento BETWEEN '1990-01-01' AND '2000-12-31';
```

---

## 9️⃣ Quantas mulheres têm mais de 1.90 m de altura
```sql
SELECT nome, altura, sexo
FROM gafanhotos
WHERE sexo = 'F'
  AND altura > 1.90;
```

---

## 🔟 Lista de profissões e quantidade de gafanhotos em cada
```sql
SELECT profissao, COUNT(*) AS quantidade
FROM gafanhotos
GROUP BY profissao
ORDER BY quantidade DESC;

SELECT COUNT(DISTINCT profissao) AS total_profissoes
FROM gafanhotos;
```

---

## 1️⃣1️⃣ Quantos homens e mulheres nasceram após `01/Jan/2005`
```sql
SELECT sexo, COUNT(*) AS quantidade
FROM gafanhotos
WHERE nascimento > '2005-01-01'
GROUP BY sexo;
```

---

## 1️⃣2️⃣ Gafanhotos que nasceram fora do Brasil e países com mais de 3 pessoas
```sql
SELECT nacionalidade, COUNT(*) AS quantidade
FROM gafanhotos
WHERE nacionalidade <> 'Brasil'
GROUP BY nacionalidade
HAVING COUNT(*) > 3
ORDER BY quantidade DESC;
```

---

## 1️⃣3️⃣ Agrupar pela altura pessoas acima da média e com mais de 100 kg
```sql
SELECT altura, COUNT(*) AS quantidade
FROM gafanhotos
WHERE peso > 100
  AND altura > (
    SELECT AVG(altura) 
    FROM gafanhotos
  )
GROUP BY altura
ORDER BY altura;
```
