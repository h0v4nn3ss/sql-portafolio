# 01 — Consultas Básicas con `SELECT`
## Objetivo

Aprender a usar la sentencia SELECT para obtener datos de una tabla.
Este capítulo cubre:
- Selección de columnas específicas.
- Filtrado de registros con WHERE.
- Ordenamiento de resultados con ORDER BY.
- Limitación de filas con LIMIT.

## Ejemplo 1: Seleccionar productos bajos en grasa y reciclables
```sql
SELECT product_id
FROM products
WHERE low_fats = 'Y' 
    AND recyclable = 'Y';
```
### Explicación:
- `SELECT product_id` devuelve únicamente el identificador de cada producto.
- `FROM products` indica que los datos se extraen de la tabla products.
- `WHERE low_fats = 'Y' AND recyclable = 'Y'` filtra solo los productos que cumplen ambas condiciones: ser bajos en grasa y reciclables.
- Útil para obtener un listado de productos que combinan criterios de salud y sostenibilidad.

## Ejemplo 2: Seleccionar clientes que no fueron referidos por el cliente 2
```sql
SELECT name
FROM customer
WHERE referee_id != 2 
    OR referee_id IS null;
```
### Explicación:
- `SELECT name` devuelve solo la columna con el nombre de cada cliente.
- `FROM customer` indica que los datos se obtienen de la tabla customer.
- `WHERE referee_id != 2` filtra a todos los clientes cuyo referee_id (quien los refirió) no sea el cliente con id = 2.
- `OR referee_id IS NULL` incluye además a los clientes que no tienen ningún referente registrado.
- Útil para obtener un listado de clientes que no dependen de un referido específico (el cliente 2), incluyendo los que llegaron por cuenta propia.

## Ejemplo 3: Seleccionar países con gran población o gran extensión territorial
```sql
SELECT name, population, area
FROM world
WHERE population >= 25000000
    OR area >= 3000000;
```
### Explicación:
- `SELECT name`, population, area devuelve tres columnas: el nombre del país, su población y su superficie.
- `FROM world` indica que los datos se extraen de la tabla world.
- `WHERE population >= 25000000` filtra los países con una población de 25 millones o más.
- `OR area >= 3000000` agrega además a los países cuya superficie es de 3 millones de km² o más, incluso si no cumplen el requisito de población.
- Útil para identificar países que son relevantes por tamaño demográfico o geográfico, sin necesidad de que ambas condiciones se cumplan simultáneamente.
