# SQL-Inicial


### Ejercicio 1:
~~~
Cree una tabla llamada CURSO con los atributos: 
Código de curso (clave primaria, entero no nulo)
Nombre (varchar no nulo)
Descripcion (varchar)
Turno (varchar no nulo)
~~~
```sql
CREATE TABLE CURSO (
	codigo INT PRIMARY KEY NOT NULL,
  	nombre VARCHAR(15) NOT NULL,
  	descripcion VARCHAR(200),
  	turno VARCHAR(15) NOT NULL
);
```
### Ejercicio 2:
~~~
Agregue un campo “cupo” de tipo numérico
~~~
```sql
ALTER TABLE CURSO ADD cupo INT;
```
### Ejercicio 3:
~~~
Inserte datos en la tabla:

(101, “Algoritmos”,”Algoritmos y Estructuras de Datos”,”Mañana”,35)

(102, “Matemática Discreta”,””,”Tarde”,30)
~~~
```sql
INSERT INTO CURSO (codigo, nombre, descripcion, turno, cupo) VALUES (101, 'Algoritmos','Algoritmos y Estructuras de Datos','Mañana',35);

INSERT INTO CURSO (codigo, nombre, descripcion, turno, cupo) VALUES (102, 'Matemática Discreta','','Tarde',30);
```
### Ejercicio 4 
~~~
Cree un registro con el nombre nulo y verifique que no funciona.
~~~
```sql
INSERT INTO CURSO (codigo, descripcion, turno, cupo) VALUES (109,'','Tarde',30);
```
#### Output
![Output](images/ejercicio4-output.png)
### Ejercicio 5
~~~
Cree un registro con la clave primaria repetida y verifique que no funciona.
~~~
```sql
INSERT INTO CURSO (codigo, nombre, descripcion, turno, cupo) VALUES (102, 'Programacion','','Tarde',20);
```
#### Output
![Output](images/ejercicio5-output.png)
### Ejercicio 6
~~~
Actualice, para todos los cursos, el cupo en 25.
~~~
```sql
UPDATE CURSO SET cupo = 25;
```
### Ejercicio 7
~~~
Elimine el curso Algoritmos
~~~
```sql
DELETE FROM CURSO WHERE nombre = 'Algoritmos';
```

