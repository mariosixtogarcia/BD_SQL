# SQL
### En SQL, existe un único linguaxe, e 6 sublinguaxes, que son: DQL, DML, DDL, DCL, TCL, SCL.
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

**SELECT:** Usase para seleccionar os datos que queremos que se mostren.

**FROM:** Usase para indicar a tabla na que queremos que se busquen os datos.

**WHERE:** É a clausuala usada para dispoñer as condicións de busqueda, onde lle decimos como queremos que o busque.

### EJEMPLOS:

1. Este exemplo busca na tabla world, a población do pais entre comillas **simples** neste caso: Germany.
```sql
SELECT population
FROM world
WHERE name = 'Germany';
```
