---
title: "Window Functions em PySpark: Como analisar dados em alto volume"
date: 2025-08-29T00:00-03:00
last_modified_at: 2025-08-29T00:00:00-03:00
categories:
  - big-data
  - pyspark
  - engenharia-de-dados
  - dataframes
permalink: /pyspark/window-functions-em-pyspark
classes: wide
excerpt: Aprenda a usar funções de janela (row_number, rank, dense_rank, lag, lead, first_value, last_value) no PySpark com exemplos práticos e dicas de performance para análise em larga escala.
tags:
  - pyspark
  - window-functions
  - funcoes-de-janela
  - engenharia de dados
  - dataframes
  - rank
  - lag
  - lead
  - row_number
---
![Ilustração sobre Funções de Janela em pyspark](/images/window-functions-pyspark.png)

Ao trabalhar com grandes volumes de dados, uma das necessidades mais comuns é realizar análises que envolvem **comparar registros dentro de um mesmo grupo**. No SQL tradicional, usamos [funções de janela](https://medium.com/comunidadeds/windows-functions-desvendando-o-poder-das-funções-de-janela-no-sql-805cf12bfff2) (window functions) para esse tipo de tarefa. No PySpark, o mesmo conceito se aplica, permitindo análises eficientes em datasets distribuídos.

Neste artigo, vamos explorar como usar funções de janela no PySpark, entender suas diferenças e ver exemplos práticos aplicados em cenários reais.

---

## O que são Window Functions?

As funções de janela permitem aplicar cálculos sobre **partições de dados** sem precisar agregá-los.  
Isso significa que conseguimos calcular métricas **linha a linha**, mas ainda considerando um grupo maior.

Exemplos de uso:  
- Ordenar elementos dentro de cada categoria.  
- Calcular ranking de salários em cada departamento.  
- Descobrir a primeira ou última ocorrência em um grupo.  
- Criar colunas com valores anteriores ou seguintes de uma linha.  

## Criando um DataFrame de Exemplo

Usaremos o seguinte dataset de funcionários e salários:

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col

spark = SparkSession.builder.appName("WindowFunctions").getOrCreate()

data = [
    ("TI", "Maria", 4000),
    ("TI", "João", 4500),
    ("TI", "Ana", 5000),
    ("RH", "Carlos", 3000),
    ("RH", "Beatriz", 3200),
]

df = spark.createDataFrame(data, ["depto", "nome", "salario"])
df.show()
```

**Resultado**:

```
+-------+-------+-------+
| depto | nome  |salario|
+-------+-------+-------+
|   TI  | Maria |  4000 |
|   TI  | João  |  4500 |
|   TI  | Ana   |  5000 |
|   RH  | Carlos|  3000 |
|   RH  | Beatriz| 3200 |
+-------+-------+-------+
```

## Principais Funções de Janela
1. `row_number()` 

Retorna um número sequencial para cada linha dentro da partição.

```python
from pyspark.sql.window import Window
import pyspark.sql.functions as F

windowSpec = Window.partitionBy("depto").orderBy("salario")
df.withColumn("row_num", F.row_number().over(windowSpec)).show()
```

Entrada:
```
+-------+-------+-------+
| depto | nome  |salario|
+-------+-------+-------+
|   TI  | Maria |  4000 |
|   TI  | João  |  4500 |
|   TI  | Ana   |  5000 |
|   RH  | Carlos|  3000 |
|   RH  | Beatriz| 3200 |
+-------+-------+-------+
```

Saída:
```
+-------+-------+-------+-------+
| depto | nome  |salario|row_num|
+-------+-------+-------+-------+
|   TI  | Maria |  4000 |   1   |
|   TI  | João  |  4500 |   2   |
|   TI  | Ana   |  5000 |   3   |
|   RH  | Carlos|  3000 |   1   |
|   RH  | Beatriz| 3200 |   2   |
+-------+-------+-------+-------+
```

2. `rank()` vs `dense_rank()`

- rank(): dá saltos em caso de empates.
- dense_rank(): mantém a sequência contínua.

```python
from pyspark.sql.window import Window
import pyspark.sql.functions as F

windowSpec = Window.partitionBy("depto").orderBy("salario")
df.withColumn("rank", F.rank().over(windowSpec)) \
  .withColumn("dense_rank", F.dense_rank().over(windowSpec)) \
  .show()
```

Exemplo com salários repetidos:

Entrada:
```
+-------+-------+-------+
| depto | nome  |salario|
+-------+-------+-------+
|   TI  | Maria |  4000 |
|   TI  | João  |  4500 |
|   TI  | Pedro |  4500 |
|   TI  | Ana   |  5000 |
+-------+-------+-------+
```

Saída:

```
+-------+-------+-------+------+-----------+
| depto | nome  |salario| rank |dense_rank|
+-------+-------+-------+------+-----------+
|   TI  | Maria |  4000 |  1   |     1     |
|   TI  | João  |  4500 |  2   |     2     |
|   TI  | Pedro |  4500 |  2   |     2     |
|   TI  | Ana   |  5000 |  4   |     3     |
+-------+-------+-------+------+-----------+
```

3. `lag()` e `lead()`

Permitem acessar o valor anterior (lag) ou seguinte (lead) dentro de uma partição.

```python
from pyspark.sql.window import Window
import pyspark.sql.functions as F
df.withColumn("lag", F.lag("salario", 1).over(windowSpec)) \
  .withColumn("lead", F.lead("salario", 1).over(windowSpec)) \
  .show()
```

Saída:

```
+-------+-------+-------+------+------+ 
| depto | nome  |salario| lag  | lead | 
+-------+-------+-------+------+------+ 
|   TI  | Maria |  4000 | null | 4500 | 
|   TI  | João  |  4500 | 4000 | 5000 | 
|   TI  | Ana   |  5000 | 4500 | null | 
|   RH  | Carlos|  3000 | null | 3200 | 
|   RH  | Beatriz| 3200 | 3000 | null | 
+-------+-------+-------+------+------+ 
```

4. `first_value()` e `last_value()`

Retornam o primeiro e o último valor dentro de cada partição.

```python
from pyspark.sql.window import Window
import pyspark.sql.functions as F

df.withColumn("first_sal", F.first("salario").over(windowSpec)) \
  .withColumn("last_sal", F.last("salario").over(windowSpec)) \
  .show()
```


Saída:

```
+-------+-------+-------+----------+---------+
| depto | nome  |salario|first_sal |last_sal |
+-------+-------+-------+----------+---------+
|   TI  | Maria |  4000 |   4000   |   5000  |
|   TI  | João  |  4500 |   4000   |   5000  |
|   TI  | Ana   |  5000 |   4000   |   5000  |
|   RH  | Carlos|  3000 |   3000   |   3200  |
|   RH  | Beatriz| 3200 |   3000   |   3200  |
+-------+-------+-------+----------+---------+
```

### Cenários de Uso (Problemas e Soluções)

Agora que entendemos cada função, vamos aplicar em problemas reais:

Q1. Ranqueie os salários dentro de cada departamento
> Use rank() para saber a posição de cada funcionário.

Q2. Identifique o salário anterior e o próximo
> Use lag() e lead() para criar comparações.

Q3. Descubra o primeiro e o último salário de cada departamento
> Use first_value() e last_value() para verificar extremos.

## Conclusão

As funções de janela no PySpark são ferramentas poderosas para análise em alto volume de dados.
Com elas, é possível responder perguntas como: “Quem tem o maior salário em cada departamento?”, “Qual foi a primeira venda de cada cliente?” ou “Como calcular somas acumuladas sem perder granularidade?”.
