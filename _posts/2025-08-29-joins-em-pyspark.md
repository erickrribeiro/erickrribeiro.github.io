---
title: "Joins em PySpark: Entendendo as diferentes formas de unir DataFrames"
date: 2025-08-29T00:00-03:00
last_modified_at: 2025-08-29T00:00:00-03:00
categories:
  - big-data
  - pyspark
  - engenharia-de-dados
  - dataframes
permalink: /pyspark/joins-em-pyspark
classes: wide
excerpt: Aprenda como funcionam os diferentes tipos de joins no PySpark, incluindo inner, outer, left, right, semi e anti join. Veja exemplos práticos de como unir DataFrames e aplicar filtros em joins para otimizar análises em Big Data.
tags:
  - pyspark
  - joins
  - dataframes
  - big data
  - spark sql
  - engenharia de dados
  - inner join
  - outer join
  - left join
  - right join
  - semi join
  - anti join
  - cross join
---

Neste artigo, vamos explorar como o Spark permite unir diferentes fontes de dados ou linhas de uma mesma tabela, explicando o funcionamento das junções e como o Spark as executa na prática. Como bônus, abordaremos o tipo CROSS JOIN e o uso de filtros juntamente com a cláusula JOIN.

---

## Por dentro de um join

Um join nada mais é do que a união de dois ou mais conjuntos de dados, denominados esquerda e direita, a partir da avaliação de uma ou mais expressões, que determinam se um registro de um lado deve ser combinado com o do outro:

```
esquerda.join(direita, expressão, tipo)
```

A expressão de junção mais comum é a igualdade, que compara se as chaves do DataFrame da esquerda coincidem com as do DataFrame da direita. Se essa comparação for verdadeira, o Spark combina os registros.

É possível criar junções ainda mais avançadas, inclusive utilizando métodos como `where` ou `filter`, desde que a expressão avaliada retorne um valor booleano.


## Os tipos de joins

Se você já tem familiaridade com bancos de dados relacionais, ou mesmo planilhas, o conceito de unir diferentes conjuntos de dados deve lhe soar familiar. Ainda assim, para facilitar o entendimento, usaremos exemplos práticos com cada tipo de join do PySpark. Para isso, criaremos dois DataFrames: um representando o lado esquerdo e outro o lado direito.

### 1. DataFrame representando o lado esquerdo:

```python
from pyspark.sql.session import SparkSession

spark = SparkSession.builder.appName('Joins').getOrCreate()

schema = ['id', 'nome', 'gênero', 'dept_id']
data = [
    (1, 'Robert', 'M', '10'),
    (2, 'Bill', 'M', '20'),
    (3, 'Brooke', 'F', '30'),
    (4, 'Matei', 'M', '40'),
    (5, 'Fulano', 'M', '50')
]

left_df = spark.createDataFrame(data=data, schema=schema)
left_df.show()
```

Saída esperada:

```
+---+------+------+-------+
| id|  nome|gênero|dept_id|
+---+------+------+-------+
|  1|Robert|     M|     10|
|  2|  Bill|     M|     20|
|  3|Brooke|     F|     30|
|  4| Matei|     M|     40|
|  5|Fulano|     M|     50|
+---+------+------+-------+
```

### 2. DataFrame representando o lado direito:

```python
schema = ['dept_id', 'dept_nome']
data = [
    (10, 'Data Engineer'),
    (20, 'Product Manager'),
    (30, 'Machine Learning Lead'),
    (40, 'Chief Technologist'),
    (60, 'Engineering Director')
]

right_df = spark.createDataFrame(data=data, schema=schema)
right_df.show(truncate=False)
```

Saída esperada:

```
+-------+---------------------+
|dept_id|dept_nome           |
+-------+---------------------+
|10     |Data Engineer        |
|20     |Product Manager      |
|30     |Machine Learning Lead|
|40     |Chief Technologist   |
|60     |Engineering Director |
+-------+---------------------+
```

## Inner Join

O inner join é o padrão do Spark e, provavelmente, o mais utilizado. Ele cria uma interseção, retornando apenas os registros que possuem correspondência em ambos os DataFrames, descartando aqueles sem chave equivalente.

Exemplo:

```python
inner_df = (
    left_df
    .join(right_df, left_df.dept_id == right_df.dept_id, 'inner')
    .drop(right_df.dept_id)
)
inner_df.show(truncate=False)
```

Apenas os registros com valores iguais em `dept_id` nos dois DataFrames aparecem no resultado. Quando não há correspondência, esses registros são ignorados.

Você também pode fazer um inner join de forma mais enxuta:

```python
inner_df = (
    left_df
    .join(right_df, on=['dept_id'])
    .orderBy('dept_id')
)
inner_df.show(truncate=False)
```

Saída esperada:

```
+-------+---+------+------+---------------------+
|dept_id| id|nome  |gênero|dept_nome           |
+-------+---+------+------+---------------------+
|10     | 1 |Robert|M     |Data Engineer        |
|20     | 2 |Bill  |M     |Product Manager      |
|30     | 3 |Brooke|F     |Machine Learning Lead|
|40     | 4 |Matei |M     |Chief Technologist   |
+-------+---+------+------+---------------------+
```

## Outer Join

Conhecido também como full join, esse tipo de junção retorna todos os registros dos dois DataFrames, combinando onde houver correspondência. Onde não houver, os campos recebem valor nulo.

```python
outer_df = (
    left_df
    .join(right_df, on=['dept_id'], how='outer')
    .orderBy('dept_id')
)
outer_df.show(truncate=False)
```

Saída esperada:

```
+-------+----+------+------+---------------------+
|dept_id| id |nome  |gênero|dept_nome           |
+-------+----+------+------+---------------------+
|10     | 1  |Robert|M     |Data Engineer        |
|20     | 2  |Bill  |M     |Product Manager      |
|30     | 3  |Brooke|F     |Machine Learning Lead|
|40     | 4  |Matei |M     |Chief Technologist   |
|50     | 5  |Fulano|M     |null                |
|60     |null|null  |null  |Engineering Director |
+-------+----+------+------+---------------------+
```


## Left Outer Join

O left outer join retorna todas as linhas do DataFrame da esquerda e, quando não há correspondência à direita, os campos adicionais recebem valor nulo.

```python
left_joined_df = (
    left_df
    .join(right_df, on=['dept_id'], how='left')
    .orderBy('dept_id')
)
left_joined_df.show(truncate=False)
```

Saída esperada:

```
+-------+---+------+------+---------------------+
|dept_id| id|nome  |gênero|dept_nome           |
+-------+---+------+------+---------------------+
|10     | 1 |Robert|M     |Data Engineer        |
|20     | 2 |Bill  |M     |Product Manager      |
|30     | 3 |Brooke|F     |Machine Learning Lead|
|40     | 4 |Matei |M     |Chief Technologist   |
|50     | 5 |Fulano|M     |null                |
+-------+---+------+------+---------------------+
```


## Right Outer Join

O right join mantém todas as linhas do DataFrame da direita. Quando não há valor correspondente à esquerda, os campos à esquerda recebem valor nulo.

```python
right_joined_df = (
    left_df
    .join(right_df, on=['dept_id'], how='right')
    .orderBy('dept_id')
)
right_joined_df.show(truncate=False)
```

Saída esperada:

```
+-------+----+------+------+---------------------+
|dept_id| id |nome  |gênero|dept_nome           |
+-------+----+------+------+---------------------+
|10     | 1  |Robert|M     |Data Engineer        |
|20     | 2  |Bill  |M     |Product Manager      |
|30     | 3  |Brooke|F     |Machine Learning Lead|
|40     | 4  |Matei |M     |Chief Technologist   |
|60     |null|null  |null  |Engineering Director |
+-------+----+------+------+---------------------+
```


## Left Semi Join

O left semi join é semelhante ao inner join, mas retorna apenas os registros do DataFrame da esquerda que encontram correspondência à direita — sem trazer qualquer coluna do DataFrame direito.

```python
left_semi_df = (
    left_df
    .join(right_df, on=['dept_id'], how='left_semi')
    .orderBy('dept_id')
)
left_semi_df.show(truncate=False)
```

Saída esperada:

```
+-------+---+------+------+
|dept_id| id|nome  |gênero|
+-------+---+------+------+
|10     | 1 |Robert|M     |
|20     | 2 |Bill  |M     |
|30     | 3 |Brooke|F     |
|40     | 4 |Matei |M     |
+-------+---+------+------+
```


## Left Anti Join

O left anti join realiza o oposto do left semi: retorna somente os registros do DataFrame esquerdo que **não** têm chave correspondente no DataFrame direito.

```python
left_anti_df = (
    left_df
    .join(right_df, on=['dept_id'], how='left_anti')
    .orderBy('dept_id')
)
left_anti_df.show(truncate=False)
```

Saída esperada:

```
+-------+---+------+------+ 
|dept_id| id|nome  |gênero| 
+-------+---+------+------+ 
|50     | 5 |Fulano|M     | 
+-------+---+------+------+ 
```


## Bônus

### Cross Join

O cross join, também chamado de produto cartesiano, não utiliza colunas para a junção: cada registro do DataFrame da esquerda será combinado com todos os registros do DataFrame da direita. Atenção: esse tipo de junção pode gerar um número muito grande de registros!

```python
cross_df = (
    left_df
    .crossJoin(right_df)
    .orderBy('nome')
)
cross_df.show()
```

---

## Join com filtro

Você pode aplicar filtros diretamente na cláusula JOIN. Por exemplo, selecione apenas registros do gênero masculino no DataFrame esquerdo e apenas departamentos com id maior ou igual a 20 no direito:

```python
from pyspark.sql.functions import col

join_filter_df = (
    left_df
    .filter(col('gênero') == 'M')
    .join(right_df.filter(col('dept_id') >= 20), on=['dept_id'], how='inner')
)
join_filter_df.show(truncate=False)
```

Saída esperada:

```
+-------+---+-----+------+---------------------+
|dept_id| id|nome |gênero|dept_nome           |
+-------+---+-----+------+---------------------+
|20     | 2 |Bill |M     |Product Manager      |
|40     | 4 |Matei|M     |Chief Technologist   |
+-------+---+-----+------+---------------------+
```


## Conclusão

Neste artigo, você viu como funcionam os joins no PySpark, conheceu os diferentes tipos disponíveis e como utilizá-los na prática.

## Referências

[https://sparkbyexamples.com/pyspark/pyspark-join-explained-with-examples](https://sparkbyexamples.com/pyspark/pyspark-join-explained-with-examples)
