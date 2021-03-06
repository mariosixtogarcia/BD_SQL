#  Apuntes SQL

## ÍNDICE:
- [Definicion](#Linguaxe-e-sublinguaxes)
- [Estructura](#A-estructura-que-debemos-seguir-é-a-seguinte)
- [Importante](#importante)
- [Cláusulas](#cláusulas)

  a) [SELECT](#select)
  
  b) [FROM](#from)
 
  c) [WHERE](#where)
 
  d) [GROUP BY](#group-by)
 
  e) [HAVING](#having)

  f) [ORDER BY](#order-by)
  
 - [Ejemplos](#ejemplos)

#### Linguaxe e sublinguaxes.
#### En SQL, que é unha linguaxe de programaxión, existe un único linguaxe, e 6 sublinguaxes, que son: DQL, DML, DDL, DCL, TCL, SCL.
- Los 6 sublenguajes
DQL (Data Query Language)

DML (Data Manipulation Language) -> cláusula máis importante: CREATE, ALTER, DROP

DDL (Data Definition Language) -> cláusula máis importante: INSERT, UPDATE, DELETE

DCL (Data Control Language) -> cláusula máis importante: GRANT, REVOKE, (AUDIT, COMMENT)

TCL (Transaction Control Language) -> cláusula máis importante: COMMIT, ROLLBACK, (SAVEPOINT)

SCL (Sesion Control Language) -> cláusula máis importante: ALTER SESION


### As cláusulas serven para poder facer consultas, combinando estas, datos de táboas, e buscando a maneira máis eficiente para mostrar o resultado que nós queremos.
#### A estructura que debemos seguir é a seguinte:
```sql
SELECT [ ALL / DISTINC ] Nombre_objeto [ AS [Expresion] ]
FROM Nombre_Tabla_Vista 
WHERE Condiciones [ AND Condiciones / OR Condiciones ]
GROUP BY Nombre_objeto
HAVING Condiciones [ AND Condiciones / OR Condiciones ]
ORDER BY ListaColumnas [ ASC / DESC ];
```
## IMPORTANTE:

1) É moi importante acabar todas as consultas en ; **(punto e coma)**

2) As cláusulas van sempre en **MAIUSCULAS**

3) Os comentarios para que SQL non reconozca texto como conculta van entre /* e */

## CLÁUSULAS:

### **SELECT:** 
Usase para seleccionar os datos que queremos que se mostren.

-Dentro da cláusula SELECT podense usar distintos operadores. Entre eles:

* **AS:** Sirve para renomear o nome das tablas. (Nombre_objeto AS nombre_que_queremos_poner).
* **REPLACE:** Sirve para reemplazar caracteres.
* **ROUND:** Fórmula ROUND (X/N,D) Seleccionas X, redondeas por N, con d decimales.
* **LENGTH:** Serve para sacar o número de letras da palabra que lle tes que introducir entre parenteses.
* **LEFT(x, n):** Serve para sacar os primeiros n caracteres de x comezando pola esquerda.
* **RIGHT(x, n):** Mismo funcionamento e fórmula que o LEFT, pero comeza pola dereita.
* **CONCAT(x, y):**
* **SUM(x):** Serve para contar todos os valores da consulta.
* **COUNT(x):** Conta o número de tuplas.
* **MAX(x):** Devolve o valor máximo da columna.
* **MIN(x):** Devolve o valor mínimo da columna.
* **AVG(x):** Devolve o valor medio de toda a columna.

### **FROM:** 
Usase para indicar a tabla na que queremos que se busquen os datos.

 -Dentro do FROM, podemos facer **JOIN** / **INNER JOIN** con outras táboas, para poder buscar datos que non están na táboa principal. Para unir táboas é necesario que entre elas exista polo menos 1 dato que esteña nas duas, se non non é posible.A fórmula é:
 táboa1 JOIN táboa2 ON (dato_entáboa1 = dato_entáboa2).
 Existe tamén LEFT JOIN e RIGHT JOIN funcionan igual que o JOIN simple, o único que mostra os NULL, da táboa que lle estamos indicando, se os NULL están a esquerda sería LEFT JOIN, e a dereita, RIGHT JOIN.

### **WHERE:** 
É a clausuala usada para dispoñer as condicións de busqueda, onde lle decimos como queremos que o busque.

 -Dentro da cláusula WHERE podense usar distintos operadores. Entre eles:

  * **IN:** Usase no sitio dun OR. En vez de repetir moitas veces (OR, OR, OR), ponse IN e entre parenteses ( 'objeto' , 'objeto' , 'objeto' )
  * **OR:** Utilizado para poder poñer duas condicions, e filtre sempre que pase **unha ou outra**.
  * **AND:** Serve para poñer varias condicións e que sempre se cumplan **todas**.
  * **BETWEEN:** Serve para elexir valores entre outros dous, para eso temos que usar a fórmula (BETWEEN número1 AND número2).
  * **LIKE:** Serve para buscar datos seguindo un patrón que lle introduzcamos, tendo en conta: % signfica, calquera cantidade de caracteres. E _ significa o mesmo que o porcentaxe, pero sólo **un** carácter.
  * **=:** Serve para que contraste cun valor exacto.
  * **>= <= > >:** Maior igual, menor igual, maior, menor. Serve para contrastar con valores numéricos.
 
  #### SUBCONSULTAS:
  Dentro de o WHERE, podemos facer outras subconsultas, para sacar un dato contrarrestado con outro, por exemplo.
  
### **GROUP BY:** 
Esta cláusula agrupa os valores da maneira que lle introduzcamos nós, para que non se xeneren errores ao levar a cabo outro tipo de operadores.

### **HAVING:** 
Ten un uso similar a WHERE, pero aplicase a un conxunto realizado por un GROUP BY.

### **ORDER BY:** 
Cláusula usada para ordenar os datos, ten que ir seguida de ASC para ordenar de forma ascendente, ou DESC, para descendente.
 
## EJEMPLOS:

1. Este exemplo busca na tabla world, a población do pais entre comillas **simples** neste caso: Germany.
```sql
SELECT population
FROM world
WHERE name = 'Germany';
```

2. Neste exemplo vemos un patrón 'P%'. Nesta consulta vaise buscar algún nome que comece por P, continuado por unha serie de caracteres, levado a cabo poloLIKE, xa que para cumplir a primeira condición do WHERE debería haber un país que se chamase P%.
```sql
SELECT name
FROM world
WHERE name = 'P%'
OR name LIKE 'P%';
   ```
3. Esta consulta filtra a través de un between que a área dos paises mostrados seña maior a 200000 e menos a 300000, e ordene a área de forma ascendente.
```sql
SELECT name AS nombre, area
FROM world
WHERE area BETWEEN 200000 AND 300000
ORDER BY area ASC
```

4. A seguinte consulta mostra a capital que conteña DF, cambiando DF por Distrito Federal.
```sql
SELECT capital
 REPLACE (capital, 'DF', 'Distrito Federal')
FROM world
WHERE name LIKE '%_DF';
```

5. Selecciona rodas as capitales de Europa e Ásia e ordenaas por número ascendente de letras.
```sql
SELECT capital, LENGTH(capital9
FROM world
WHERE continent = 'Europe' OR continent = 'Asia';
```
6. Esta consulta suma toda a poboación da táboa world.
```sql
SELECT SUM(population)
FROM world;
```
7. Nesta consulta existe un exemplo de JOIN.
Nela búscanse elementos de duas tablas, game e goal. Únense mediante un JOIN, e diselle o que teñen idéntico cun ON seguido dunha igualdade.
````sql
SELECT team1, team2, player
  FROM game JOIN goal 
    ON (id=matchid)
WHERE player LIKE 'Mario%'
```
