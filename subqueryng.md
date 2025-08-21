# SUBQUERY
Subquerying significa usar una consulta (query) dentro de otra consulta. Esa consulta interna se llama subquery o subconsulta.

La subquery se ejecuta primero.

Su resultado se pasa a la consulta externa (outer query).


# Subqueryng with semy joins and anti joins
## Semi Join
Filtra filas de la tabla iquierda basándose en la existencia de coincidencias en la tabla derecha
Es como filtrar con un WHERE pero usando una segunda tabla y para esto es necesario usar un SUB QUERY
ESTE SUBQUERY se crea con un WHERE o un IN, No hay tal comando como un SEMIJOIN

## SYNTAX
```sql
SELECT *
FROM users
WHERE country IN
    (SELECT country
    FROM states
    WHERE indep_year <1800 );
```

## ANTI JOIN
al contrario de una SEMI JOIN, este devuelve los valores de la tabla izquierda que no tienen un match con un field de la derecha
USAMOS COMO comando un "NOT IN" en lugar del IN que usamos en el semi join


## SYNTAX
```sql
SELECT *
FROM users
WHERE country NOT IN
    (SELECT country
    FROM states
    WHERE indep_year <1800 );
```

# SUBQUERYNG

## SYNTAX FOR SUBQUERYNG WITH WHERE
Devuelve una simple columna
```sql
SELECT *
FROM users
WHERE some_field IN
    (incluide some query);
```

El subquery debe tener el mismo tipo de dato según el que estamos filtrando


## SYNTAX FOR SUBQUERYNG WITH SELECT
```sql
SELECT field_1, (Subquery)
FROM users
```

## SYNTAX FOR SUBQUERYNG WITH FROM 
Subqueries dentro de FROM puede ayudar a seleccionar columnas de multiples tablas en un solo query

```sql
SELECT field_1, fiel_2
FROM (Subquery) AS subquery
```
-Uno puedo crear multiples subquery's en el FROM y a cada uno hay que darle un ALIAS


# Subqueries and best practices

-siempre hay que formatear los queries
-Dar una descipción de lo que hace el subquery con una frase dentro de /* TEXTO DESCRIPTIVO */
-Tambien podemos poner notas con -- TEXTO DESCRPTIVO, todo despues de un "--" lo toma como un texto
-Ident your queries 
-Leer Holywell's SQL style guide: leer este documento
