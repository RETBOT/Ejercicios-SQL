# Curso de SQL: Práctica de Consultas y Joins

¡Bienvenido! Este repositorio contiene ejercicios prácticos de SQL enfocados en consultas y operaciones JOIN. Los ejercicios provienen de un curso que he realizado. Puedes acceder al curso original a través del siguiente [enlace](https://www.udemy.com/certificate/UC-c79990a5-4015-4a59-ba36-d2f2aa9e759b/). 
¡Disfruta aprendiendo y practicando SQL!


[![certificado](./archivos/UC-c79990a5-4015-4a59-ba36-d2f2aa9e759b.jpg)](https://www.udemy.com/certificate/UC-c79990a5-4015-4a59-ba36-d2f2aa9e759b/)

## Descargar Esquema y Datos de Ejemplo

Si deseas seguir los ejercicios con la misma base de datos "sakila", puedes descargar el script SQL que crea las tablas y carga los datos de ejemplo. 

- [Descargar el Esquemas SQL de sakila](./archivos/sakilla%20schema.sql)
- [Descargar los Datos SQL de sakila](./archivos/sakilla%20schema.sql)

## Estructura del Repositorio

Este repositorio contiene una serie de secciones, cada una con ejercicios prácticos y explicaciones paso a paso. Los ejercicios están diseñados para ayudarte a comprender conceptos clave de SQL, como SELECT, DISTINCT, ORDER BY, WHERE, AND, OR, NOT, IN, BETWEEN, LIKE, GROUP BY, HAVING, y diferentes tipos de JOINs.

## Ejercicios SQL
Puedes explorar cada sección y sus ejercicios en orden o saltar a una sección específica según tus necesidades de aprendizaje.

- [Descargar los Ejercicios SQL de sakila](./archivos/ejecticios_practico.sql)

### Sección 2: Select, Distinct, Order by
#### Select Se utiliza para hacer búsquedas en tablas
##### Ejercicio práctico 1 
```SQL
SELECT * FROM actor;
SELECT actor_id AS actor, first_name AS nombre, last_name AS apellido, last_update FROM actor;
SELECT * FROM city;
```

##### Ejercicio práctico 2 
##### Distinct se utiliza para obtener datos únicos o diferentes
```SQL
SELECT DISTINCT customer_id FROM customer;
SELECT DISTINCT customer_id FROM payment;
```

##### Ejercicio práctico 3 - Order by
##### Ordenar elementos ascendente o descendente
```SQL
SELECT * FROM country ORDER BY country_id DESC;
SELECT * FROM country ORDER BY country_id ASC;
SELECT * FROM customer ORDER BY first_name ASC;
```

##### Ejercicio práctico #5
##### Consulta la tabla payment de la base de datos sakila.
##### ¿Cuál es la cantidad más baja y más alta de la columna amount?
```SQL
SELECT MIN(amount) AS cantidadBaja, MAX(amount) AS cantidadAlta FROM payment;
```

### Sección 3: Where
#### Consultar los registros que cumplen una función en específico
##### Ejercicio práctico 6. Where 
```SQL
SELECT * FROM actor WHERE first_name = 'CUBA';
SELECT * FROM city WHERE city = 'London';
SELECT * FROM city WHERE country_id = 102;
SELECT * FROM customer WHERE store_id = 1;
```

##### Ejercicio práctico 7 - Where
```SQL
SELECT * FROM inventory WHERE film_id > 50;
SELECT DISTINCT amount FROM payment WHERE amount < 3;
```

##### Ejercicio práctico 8 - Where
```SQL
SELECT * FROM staff WHERE staff_id != 2;
SELECT * FROM language WHERE name != 'German';
```

##### Ejercicio práctico #9
#### Consulta description, release_year de la tabla film de la base de datos sakila.
#### Filtra la información donde title sea IMPACT ALADDIN
```SQL
SELECT description, release_year FROM film WHERE title = 'IMPACT ALADDIN';
```

##### Ejercicio práctico #10
##### Consulta la tabla payment de la base de datos sakila.
##### Filtra la información donde amount sea mayor a 0.99.
```SQL
SELECT * FROM payment WHERE amount > 0.99;
```

### Sección 4: AND, OR, NOT
#### And se utiliza cuando queremos que dos condiciones sean verdaderas
#### Or se utiliza cuando queremos que una condición sea verdadera
#### Not se utiliza cuando queremos que la condición no sea verdadera

##### Ejercicio práctico 11. And
```SQL
SELECT * FROM country
WHERE country = 'Algeria' AND country_id = 2;
```

##### Ejercicio práctico 12. Or
```SQL
SELECT * FROM country
WHERE country = 'Algeria' OR country_id = 12;

SELECT * FROM language
WHERE language_id = 1 OR name = 'German';
```

##### Ejercicio práctico 13
```SQL
SELECT * FROM category
WHERE NOT name = 'Action';

SELECT * FROM film
WHERE NOT rating = 'PG';
```

##### Ejercicio práctico #14
##### Consulta la tabla payment de la base de datos sakila.
##### Filtra la información donde customer_id sea igual a 36, amount sea mayor a 0.99 y staff_id sea igual a 1.
```SQL
SELECT * FROM payment
WHERE customer_id = 36 AND amount > 0.99 AND staff_id = 1;
```

##### Ejercicio práctico #15
##### Consulta la tabla rental de la base de datos sakila.
##### Filtra la información donde staff_id no sea 1, customer_id sea mayor a 250 y inventory_id sea menor de 100.
```SQL
SELECT * FROM rental
WHERE staff_id != 1 AND customer_id > 250 AND inventory_id < 100;
```

### Sección 5: In
#### Es una variante de múltiples condiciones OR
##### Ejercicio práctico 16
```SQL
SELECT * FROM customer
WHERE first_name IN ('MARY', 'PATRICIA');
```

##### Ejercicio práctico 17
```SQL
SELECT * FROM film
WHERE 
special_features IN ('Trailers,Behind the Scenes', 'Deleted Scenes')
AND 
rating IN ('G', 'NG-17')
AND 
length > 50;
```

##### Ejercicio práctico 18
```SQL
SELECT * FROM category
WHERE 
name NOT IN ('Action', 'Animation', 'Children');
```

##### Ejercicio práctico #19 
##### Consulta la tabla film_text de la base de datos sakila.
##### Filtra la información donde title sea ZORRO ARK, VIRGIN DAISY, UNITED PILOT
```SQL
SELECT * FROM film_text WHERE title IN ('ZORRO ARK', 'VIRGIN DAISY', 'UNITED PILOT');
```

##### Ejercicio práctico #20
##### Consulta la tabla city de la base de datos sakila.
##### Filtra la información donde city sea Chiayi, Dongying, Fukuyama y Kilis.
```SQL
SELECT * FROM city 
WHERE city IN ('Chiayi', 'Dongying', 'Fukuyama', 'Kilis');
```

### Sección 6: Between
#### Seleccionar valores dentro de un rango dado
##### Ejercicio práctico 21
```SQL
SELECT * FROM rental
WHERE (customer_id BETWEEN 300 AND 350) AND (staff_id = 1);
```

##### Ejercicio práctico 22
```SQL
SELECT * FROM payment
WHERE amount NOT BETWEEN 3 AND 5;
```

##### Ejercicio práctico #23
##### Consulta la tabla payment de la base de datos sakila.
##### Filtra la información donde amount esté entre 2.99 y 4.99, staff_id sea igual a 2 y customer_id sea 1 y 2.
```SQL
SELECT * FROM payment 
WHERE (amount BETWEEN 2.99 AND 4.99) 
AND staff_id = 2 
AND customer_id IN (1, 2);
```

##### Ejercicio práctico #24
##### Consulta la tabla address de la base de datos sakila.
##### Filtra la información donde city_id esté entre 300 y 350.
```SQL
SELECT * FROM address 
WHERE city_id BETWEEN 300 AND 350;
```

##### Ejercicio práctico #25
##### Consulta la tabla film de la base de datos sakila.
##### Filtra la información donde rental_rate esté entre 0.99 y 2.99, length sea menor o igual a 50 y replacement_cost sea menor a 20.
```SQL
SELECT * FROM film WHERE 
(rental_rate BETWEEN 0.99 AND 2.99) 
AND length <= 50 
AND replacement_cost < 20;
```

### Sección 7: Like
#### Se utiliza para buscar un patrón específico en una columna
##### Ejercicio práctico 26
```SQL
SELECT * FROM actor 
WHERE first_name LIKE 'A%' AND last_name LIKE 'B%';
```

##### Ejercicio práctico 27
```SQL
SELECT * FROM actor 
WHERE first_name LIKE '%A' AND last_name LIKE '%N';
```

##### Ejercicio práctico 28
```SQL
SELECT * FROM actor 
WHERE first_name LIKE '%NE%' AND last_name LIKE '%RO%';
```

##### Ejercicio práctico 29
```SQL
SELECT * FROM actor 
WHERE first_name LIKE 'C%N' AND last_name LIKE 'G%';
```

##### Ejercicio práctico #30
##### Consulta la tabla film de la base de datos sakila.
##### Filtra la información donde release_year sea igual a 2006 y title empiece con ALI.
```SQL
SELECT * FROM film
WHERE release_year = 2006 AND title LIKE 'ALI%';
```

### Sección 8: Inner join, left join, right join
##### Ejercicio práctico 31
#### Inner join: Mantiene los datos que se encuentran en las dos tablas
#### Left join: Mantiene los datos de la izquierda y los une con los datos de la derecha
#### Right join: Mantiene los datos de la derecha y los une con los datos de la izquierda

##### Ejercicio práctico 32
```SQL
SELECT 
f.title, f.description, 
f.release_year, l.name AS language 
FROM film f 
INNER JOIN language l
ON f.language_id = l.language_id;
```

##### Ejercicio práctico 33
```SQL
SELECT a.address AS Direccion, c.city AS Ciudad 
FROM address a 
INNER JOIN city c 
ON (a.city_id = c.city_id);
```

##### Ejercicio práctico 34
```SQL
SELECT 
c.customer_id, 
c.first_name, 
c.last_name,
a.actor_id,
a.last_name, 
a.last_name 
FROM customer c 
RIGHT JOIN actor a 
ON (c.last_name = a.first_name);
```

##### Ejercicio práctico 35
```SQL
SELECT 
c.customer_id,
c.first_name,
c.last_name,
a.actor_id,
c.first_name,
c.last_name
FROM customer c
LEFT JOIN actor a 
ON (c.last_name = a.last_name);
```

##### Ejercicio práctico #36
##### Consulta la tabla address de la base de datos sakila.
##### Realiza un INNER JOIN con las tablas city y country
##### Mostrar las columnas address, city, country
```SQL
SELECT 
a.address,
c.city,
co.country
FROM address a 
INNER JOIN city c 
ON (a.city_id = c.city_id)
INNER JOIN country co 
ON (c.country_id = co.country_id);
```

##### Ejercicio práctico #37
##### Consulta la tabla customer de la base de datos sakila.
##### Realiza un LEFT JOIN con las tablas store y address
##### Mostrar las columnas first_name, address, store_id
```SQL
SELECT 
c.first_name,
a.address,
s.store_id
FROM customer c
LEFT JOIN store s 
ON (c.store_id = s.store_id)
LEFT JOIN address a 
ON (c.address_id = a.address_id);
```

##### Ejercicio práctico #38
##### Consulta la tabla rental de la base de datos sakila.
##### Realiza un INNER JOIN con la tabla staff
##### Mostrar las columnas rental_id, first_name
```SQL
SELECT r.rental_id, s.first_name 
FROM rental r
INNER JOIN staff s 
ON (r.staff_id = s.staff_id);
```

### Sección 9: Count, AVG, SUM, MAX, MIN
##### Ejercicio práctico 39 SUMA COLUMNA
```SQL
SELECT SUM(amount) FROM payment;

##### Ejercicio práctico 40 SUMA RENGLON
```SQL
SELECT inventory_id + film_id + store_id FROM inventory;
```

##### Ejercicio práctico 41 CUENTA COLUMNAS
```SQL
SELECT COUNT(first_name) FROM actor;
```

##### Ejercicio práctico 42 PROMEDIO
```SQL
SELECT AVG(amount) FROM payment;
SELECT AVG(rental_duration) FROM film;
```

##### Ejercicio práctico 43 MÁXIMOS Y MÍNIMOS
```SQL
SELECT * FROM film;
SELECT MAX(length) FROM film;
SELECT MIN(length) FROM film;
SELECT MAX(replacement_cost) FROM film;
SELECT MIN(replacement_cost) FROM film;
```

##### Ejercicio práctico #44
##### Consulta la tabla rental de la base de datos sakila.
##### Realiza un COUNT de la columna rental_id
```SQL
SELECT COUNT(rental_id) FROM rental;
```

##### Ejercicio práctico #45
##### Consulta la tabla payment de la base de datos sakila.
##### Realiza un MAX de la columna amount
```SQL
SELECT MAX(amount) FROM payment;
```

### Sección 10: Group by
##### Ejercicio práctico 46
```SQL
SELECT last_name, COUNT(*) 
FROM actor
GROUP BY last_name;
```

##### Ejercicio práctico 47
```SQL
SELECT 
c.customer_id, 
c.first_name, 
c.last_name,
SUM(p.amount)
FROM payment p
INNER JOIN customer c 
ON (c.customer_id = p.customer_id)
GROUP BY c.customer_id, c.first_name, c.last_name;
```

##### Ejercicio práctico #48
```SQL
##### Consulta la tabla rental de la base de datos sakila.
##### Realiza un MAX de la columna rental_date
SELECT customer_id, MAX(rental_date)
FROM rental
GROUP BY customer_id;
```

### Sección 11: Having
#### Se agrega porque en la cláusula where no se pueden utilizar funciones de agregación
##### Ejercicio práctico 49
```SQL
SELECT last_name, COUNT(*) 
FROM actor
GROUP BY last_name
HAVING COUNT(*) > 3;
```

##### Ejercicio práctico 50
```SQL
SELECT 
c.customer_id,
c.last_name,
c.first_name,
SUM(p.amount)
FROM payment p 
INNER JOIN customer c 
ON (c.customer_id = p.customer_id)
GROUP BY c.customer_id, c.last_name, c.first_name
HAVING SUM(p.amount) < 100
ORDER BY SUM(p.amount) DESC;
```

##### Ejercicio práctico #51
##### Consulta la tabla actor de la base de datos sakila.
##### Realiza un COUNT de last_name
##### Mostrar cuando el COUNT sea mayor de 2
```SQL
SELECT last_name, COUNT(*) 
FROM actor
GROUP BY last_name
HAVING COUNT(*) > 2;
```

##### Ejercicios complementarios #5
##### ¿Qué actores tienen el primer nombre 'Scarlett'?
```SQL
SELECT actor_id, first_name, last_name 
FROM actor
WHERE first_name LIKE 'Scarlett%';
```

##### ¿Qué actores tienen el apellido "Johansson"?
```SQL
SELECT actor_id, first_name, last_name 
FROM actor
WHERE last_name = 'Johansson';
```

##### ¿Cuántos apellidos de actores distintos hay?
```SQL
SELECT COUNT(DISTINCT last_name) AS total 
FROM actor;
```

##### ¿Qué apellidos no se repiten?
```SQL
SELECT last_name 
FROM actor 
GROUP BY last_name 
HAVING COUNT(*) = 1;
```

##### ¿Qué actor ha aparecido en la mayoría de las películas?
```SQL
SELECT a.actor_id, a.first_name, a.last_name
FROM actor a
INNER JOIN film_actor fa ON a.actor_id = fa.actor_id
GROUP BY a.actor_id, a.first_name, a.last_name
ORDER BY COUNT(fa.actor_id) DESC
LIMIT 1;
```

##### ¿Se puede alquilar ‘Academy Dinosaur’ en la tienda 1?
```SQL
SELECT i.film_id, f.title, i.store_id
FROM inventory i
INNER JOIN film f ON i.film_id = f.film_id
WHERE f.title = 'Academy Dinosaur' AND i.store_id = 1;
```