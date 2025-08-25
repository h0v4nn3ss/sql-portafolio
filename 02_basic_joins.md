# 02 — Consultas Básicas con `JOINS`

## Objetivo

Aprender a combinar datos de múltiples tablas utilizando la cláusula JOIN.
Este capítulo cubre:

- Comprender la diferencia entre INNER JOIN, LEFT JOIN, RIGHT JOIN y FULL JOIN.
- Relacionar tablas mediante claves primarias y foráneas.
- Seleccionar columnas de distintas tablas en una sola consulta.
- Aplicar filtros a los resultados combinados con WHERE.
- Ordenar y limitar resultados provenientes de múltiples tablas.

## Ejemplo 1: Obtener IDs únicos y nombres de empleados

```sql
SELECT u.unique_id, e.name
FROM employees AS e
LEFT JOIN employeeUNI AS u
    ON e.id = u.id 
ORDER BY e.name;
```

### explicación del ejemplo 1

- `SELECT u.unique_id, e.name` indica que se devolverán dos columnas: el identificador único de cada empleado (si existe en la tabla employeeUNI) y el nombre del empleado desde la tabla employees.
- `FROM employees AS e` define que la tabla principal de la consulta es employees, y se le asigna el alias e para simplificar la escritura.
- `LEFT JOIN employeeUNI AS u ON e.id = u.id` hace una unión externa (LEFT JOIN) entre la tabla employees (e) y la tabla employeeUNI (u). Esto asegura que todos los registros de la tabla employees aparezcan en el resultado, incluso si no tienen un unique_id correspondiente en la tabla employeeUNI (en ese caso, el valor será NULL).
- `ORDER BY e.name` ordena el resultado alfabéticamente según el nombre de los empleados.

## Ejemplo 2: Obtener información de productos con sus ventas anuales

```sql
SELECT p.product_name, s.year, s.price
FROM sales AS s
JOIN product AS p
    on s.product_id = p.product_id
ORDER BY year; 
```

### Explicación del ejemplo 2

- `SELECT p.product_name, s.year, s.price` indica que se devolverán tres columnas: el nombre del producto desde la tabla product, el año de la venta y el precio de la venta desde la tabla sales.
- `FROM sales AS s` define que la tabla principal de la consulta es sales, y se le asigna el alias s para simplificar la escritura.
- `JOIN product AS p ON s.product_id = p.product_id` hace una unión interna (INNER JOIN) entre la tabla sales (s) y la tabla product (p). Esto significa que solo se mostrarán los registros que tengan coincidencias en ambas tablas, es decir, ventas que correspondan a productos existentes.
- `ORDER BY year` ordena el resultado cronológicamente según el año de las ventas, mostrando primero las ventas más antiguas.

## Ejemplo 3: Obtener clientes que visitaron pero no realizaron transacciones

```sql
SELECT  v.customer_id, 
        COUNT(v.visit_id) AS count_no_trans 
FROM visits AS v
LEFT JOIN transactions AS t
    ON v.visit_id = t.visit_id
WHERE t.transaction_id IS NULL
GROUP BY v.customer_id
ORDER BY count_no_trans;
```

### Explicación del ejemplo 3

- `SELECT v.customer_id, COUNT(v.visit_id) AS count_no_trans` indica que se devolverán dos columnas: el ID del cliente y el conteo de visitas sin transacciones, renombrado como "count_no_trans".
- `FROM visits AS v` define que la tabla principal de la consulta es visits, y se le asigna el alias v para simplificar la escritura.
- `LEFT JOIN transactions AS t ON v.visit_id = t.visit_id` hace una unión externa (LEFT JOIN) entre la tabla visits (v) y la tabla transactions (t). Esto asegura que todas las visitas aparezcan en el resultado, incluso si no tienen transacciones asociadas.
- `WHERE t.transaction_id IS NULL` filtra únicamente las visitas que no tienen transacciones asociadas (donde el campo transaction_id es NULL).
- `GROUP BY v.customer_id` agrupa los resultados por cliente para poder contar las visitas sin transacciones de cada uno.
- `ORDER BY count_no_trans` ordena el resultado según el número de visitas sin transacciones, mostrando primero los clientes con menos visitas sin compras.
