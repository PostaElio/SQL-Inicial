# SQL-Intermedio
## Indice
* Tema 1 - Funciones agregadas.
	* [Ejercicios.](#tema-1---funciones-agregadas)
	* [Documentacion.](???)
* Tema 2 - Multiples Tables.
	* [Ejercicios.](#tema-2---multiples-tables)
	* [Documentacion.](???)
* Tema 3 - Indices.
	* [Ejercicios.](#tema-3---???)
	* [Documentacion.](???)
* Tema 4 - Queries anidadas.
	* [Ejercicios.](#tema-3---???)
	* [Documentacion.](???)

---
## Tema 1 - Funciones agregadas
### Ejercicio 1:
~~~
Escriba una consulta para saber cuántos estudiantes son de la carrera Mecánica.
~~~
```sql
SELECT COUNT(*) AS cantidad_de_estudiantes_que_estudian_la_carrera_mecanica
FROM estudiante where carrera LIKE 'Mecánica'
```
### Ejercicio 2:
~~~
Escriba una consulta para saber, de la tabla PROFESOR, el salario mínimo de los profesores nacidos en la década del 80.
~~~
```sql
SELECT MIN(salario) AS salario_minimo FROM profesor WHERE fecha_nacimiento 
BETWEEN '1980-01-01' and '1989-12-31';
```
### Ejercicio 3:
~~~
Para el siguiente modelo relacional:
~~~
![modelo-relacional](images/tema1-MR.png)
### Ejercicio 4:
~~~
Escriba las siguientes consultas:
~~~
~~~
Cantidad de pasajeros por país
~~~
```sql
/*ponemos el nombre del pasajero en el COUNT 
para que detecte los valores null y los tome como 0*/
SELECT DISTINCT p1.nombre, COUNT(p2.nombre) 
AS cantidad_de_pasajeros_por_pais
FROM pais p1 LEFT JOIN pasajero p2 GROUP BY p1.nombre;
```
~~~
Suma de todos los pagos realizados
~~~
```sql
/*DE que depende la suma de todos los pagos?
solo la suma de todos los montos, o de la suma de todos los montos
restando/sumando jeje los impuestos?*/
SELECT SUM(monto) AS suma_de_todos_los_pagos FROM PAGO;
```
~~~
Suma de todos los pagos que realizó un pasajero. El monto debe aparecer 
con dos decimales.
~~~
```sql
/*falta testear, creeria que funciona*/
SELECT idpasajero, ROUND(SUM(monto),2) AS suma_de_todos_los_pagos
FROM PAGO GROUP BY idpasajero;
```
~~~
Promedio de los pagos que realizó un pasajero.
~~~
```sql
/*DEberia de buscar un personaje en especifico?*/
SELECT AVG(monto) FROM PAGO GROUP BY idpasajero;
```
---
## Tema 2 - Multiples Tables
#### Para el siguiente modelo relacional:
![modelo-relacional](images/tema2-MR.png)
### Ejercicio 1:
~~~
Nombre, apellido y cursos que realiza cada estudiante
~~~
```sql
SELECT e.nombre, e.apellido , c.nombre AS nombre_curso FROM ESTUDIANTE e NATURAL JOIN INSCRIPCION i INNER JOIN CURSO c ON i.CURSO_codigo = c.codigo
```
### Ejercicio 2:
~~~
Nombre, apellido y cursos que realiza cada estudiante, ordenados por el nombre del curso
~~~
```sql
SELECT e.nombre, e.apellido , c.nombre AS nombre_curso FROM ESTUDIANTE e NATURAL JOIN INSCRIPCION i INNER JOIN CURSO c ON i.CURSO_codigo = c.codigo ORDER BY c.nombre
```
### Ejercicio 3:
~~~
Nombre, apellido y cursos que dicta cada profesor
~~~
```sql
SELECT p.nombre , p.apellido, c.nombre AS nombre_curso FROM PROFESOR p INNER JOIN CURSO c ON p.id = c.PROFESOR_id 
```
### Ejercicio 4:
~~~
Nombre, apellido y cursos que dicta cada profesor, ordenados por el nombre del curso
~~~
```sql
SELECT p.nombre , p.apellido, c.nombre AS nombre_curso FROM PROFESOR p INNER JOIN CURSO c ON p.id = c.PROFESOR_id 
ORDER BY c.nombre
```
### Ejercicio 5:
~~~
Cupo disponible para cada curso (Si el cupo es de 35 estudiantes y hay 5 inscriptos, el cupo disponible será 30)
~~~
```sql
/*hacemos leftjoin para poder tener los campos null, ya que puede haber
curos con ninguna inscripcion y en ese caso restariamos 0(null) ya que 
la fecha_hora del la inscripcion estaria null */
SELECT c.codigo , c.cupo - COUNT(i.fecha_hora) AS cupo_disponible FROM CURSO c LEFT JOIN INSCRIPCION i ON c.codigo = i.CURSO_codigo GROUP BY c.codigo
```
### Ejercicio 6:
~~~
Cursos cuyo cupo disponible sea menor a 10
~~~
```sql
SELECT * FROM CURSO 
cupo es el cupo maximo CONST o
es una variable que incrementa cuando se inscriben?
```

