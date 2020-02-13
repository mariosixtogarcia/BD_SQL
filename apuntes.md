# SQL
### En SQL, existe un único linguaxe, e 6 sublinguaxes, que son: DQL, DML, DDL, DCL, TCL, SCL.
- Los 6 sublenguajes
DQL (Data Query Language)

DML (Data Manipulation Language) -> sentencia mais importante: CREATE, ALTER, DROP

DDL (Data Definition Language) -> sentencia mais importante: INSERT, UPDATE, DELETE

DCL (Data Control Language) -> sentencia mais importante: GRANT, REVOKE, (AUDIT, COMMENT)

TCL (Transaction Control Language) -> sentencia mais importante: COMMIT, ROLLBACK, (SAVEPOINT)

SCL (Sesion Control Language) -> sentencia mais importante: ALTER SESION


### As sentencias serven para poder facer consultas, combinando sentencias, datos de taboas, e buscando a maneira mais eficiente para mostrar o resultado que nós queremos.
#### A estructura que debemos seguir é a seguinte:
```sql
SELECT [ ALL / DISTINC ] Nombre_objeto [ AS [Expresion] ]
FROM Nombre_Tabla_Vista 
WHERE Condiciones [ AND Condiciones / OR Condiciones ]
GROUP BY Nombre_objeto
HAVING Condiciones [ AND Condiciones / OR Condiciones ]
ORDER BY ListaColumnas [ ASC / DESC ];

