# Portafolio de Consultas SQL

## Introducción

Este repositorio contiene ejemplos prácticos de consultas SQL resueltas
y explicadas.
El objetivo es mostrar el manejo de **consultas básicas, intermedias y
avanzadas**, aplicadas a diferentes escenarios de bases de datos.

------------------------------------------------------------------------

## Estructura del Repositorio

    /SQL-Portfolio
    │── README.md
    │── 01_select_basics.md
    │── 02_joins.md
    │── 03_subqueries.md
    │── 04_window_functions.md

Cada archivo `.md` contiene consultas con su explicación detallada.

------------------------------------------------------------------------

## Ejemplos de Consultas

### 1. Selección Básica

``` sql
SELECT nombre, edad 
FROM clientes
WHERE edad > 30
ORDER BY edad DESC;
```

**Explicación:**
- `SELECT` elige las columnas `nombre` y `edad`.\
- `FROM clientes` indica la tabla.\
- `WHERE edad > 30` filtra solo clientes mayores de 30 años.\
- `ORDER BY edad DESC` ordena de mayor a menor.

------------------------------------------------------------------------

### 2. JOIN entre Tablas

``` sql
SELECT c.nombre, p.producto, p.precio
FROM clientes c
JOIN compras co ON c.id = co.cliente_id
JOIN productos p ON co.producto_id = p.id;
```

**Explicación:**
- Se hace un `JOIN` entre **clientes**, **compras** y **productos**.\
- El resultado muestra qué producto compró cada cliente y su precio.\
- Uso de **alias (c, co, p)** para simplificar.

------------------------------------------------------------------------

## Cómo Usar

1.  Clona el repositorio:

    ``` bash
    git clone https://github.com/tuusuario/sql-portfolio.git
    cd sql-portfolio
    ```

2.  Abre los archivos `.md` para ver ejemplos.

3.  Ejecuta las consultas en tu motor SQL favorito (MySQL, PostgreSQL,
    SQLite).
------------------------------------------------------------------------

## Fuente del material

Las consultas y ejemplos desarrollados en este repositorio se extraen 
del plan de estudio **[Top SQL 50 de
LeetCode](https://leetcode.com/studyplan/top-sql-50/)**.

Este recurso recopila problemas clásicos de SQL que permiten practicar
desde lo más básico hasta consultas avanzadas, asegurando una cobertura
amplia de funciones, operadores y estructuras comunes en bases de datos.
------------------------------------------------------------------------

## Autor

Creado por Andrés Ohannessian (https://github.com/h0v4nn3ss) --- apasionado por
los datos y la optimización de consultas.
