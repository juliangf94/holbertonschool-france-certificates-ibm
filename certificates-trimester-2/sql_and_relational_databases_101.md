#   Module 1- SQL and Relational Databases 101
---
#  Introduction to SQL and Relational Database 101
---
-   A language used for relational databases.
-   Query data
## 1. Definiciones Clave
* **Dato (Data):** Colección de hechos en forma de texto, números o imágenes. Es el activo más crítico de las empresas.
* **Base de Datos (Database):** Repositorio o programa que almacena datos y ofrece funciones para añadir, modificar y consultar dicha información de forma rápida y segura.
* **DBMS (Database Management System):** Conjunto de herramientas de software que controlan el acceso, organización y almacenamiento de los datos.

## 2. El Modelo Relacional
Una base de datos se considera **Relacional** cuando los datos se organizan en formato **tabular** (tablas).
* **Tablas:** Colecciones de elementos relacionados (ej. lista de autores).
* **Columnas:** Propiedades de los elementos (ej. nombre, email).
* **Filas (Rows):** Registros individuales de la tabla.
* **RDBMS:** Relational Database Management System (Ejemplos: MySQL, Oracle, DB2).

## 3. SQL (Structured Query Language)
Es el lenguaje estándar diseñado para interactuar con bases de datos relacionales para consultar o extraer datos. Originalmente se llamó *Structured English Query Language* (SEQUEL).

## 4. Los 5 Comandos Básicos de SQL
Para la mayoría de los usuarios, el manejo de datos se resume en estas cinco operaciones:

1. `CREATE`: Crear una tabla.
2. `INSERT`: Insertar datos para poblar la tabla.
3. `SELECT`: Seleccionar/extraer datos de la tabla.
4. `UPDATE`: Actualizar datos existentes.
5. `DELETE`: Borrar datos.

---
#  Information and Data Models
---
## 1. Diferencia entre Modelo de Información y Modelo de Datos
* **Modelo de Información (Nivel Conceptual):** 
    -   Es una representación abstracta y formal de entidades del mundo real (ej. una biblioteca). 
    -   Define qué objetos existen y cómo se relacionan entre sí sin entrar en detalles técnicos.
* **Modelo de Datos (Nivel Físico/Concreto):** 
    -   Es el "plano" (blueprint) del sistema de base de datos. 
    -   Es específico, detallado y describe cómo se implementará la información en el software.

## 2. Tipos de Modelos
* **Modelo Jerárquico:** 
    -   Organiza los datos en una estructura de árbol (como un organigrama). 
    -   Un "hijo" solo puede tener un "padre", pero un padre puede tener muchos hijos. 
    -   Ejemplo: IMS de IBM, usado en el programa Apollo.
* **Modelo Relacional:** 
    -   Es el más utilizado.
    -   Su ventaja principal es la **independencia de datos** (lógica, física y de almacenamiento). 
    -   Los datos se guardan en estructuras simples llamadas **tablas**.

## 3. Modelo Entidad-Relación (ER Model)
    -   No es una base de datos en sí, sino una **herramienta de diseño** para crear bases de datos relacionales. 
    -   Propone ver la base de datos como una colección de entidades.

![Entity-Relationship Model](imagenes/SQL/Module1/image.png)

### Bloques de construcción del ERD:
* **Entidad (Entity):** 
    *   Es un objeto que existe de forma independiente (persona, lugar o cosa). 
    *   Se representa con un **rectángulo**.
    *   *Ejemplo:* Libro, Autor, Prestatario.
    *   *Conversión:* En la base de datos, la Entidad se convierte en una **Tabla**.
* **Atributo (Attribute):** 
    *   Son los elementos de datos que caracterizan o describen a la entidad. Se representan con **óvalos**.
    *    *Ejemplo:* Título del libro, Año de publicación, Nombre del autor.
    *   *Conversión:* En la base de datos, los Atributos se convierten en **Columnas**.

## 4. El Proceso de Diseño
1.  Identificar las **Entidades** (sustantivos como Libro o Autor).
2.  Definir sus **Atributos** (propiedades como el ID o el nombre).
3.  Establecer **Relaciones** (ej. "Autor *escribe* Libro").
4.  Convertir el diagrama final en un conjunto de tablas reales.

![Simplified Library ER Diagram](imagenes/SQL/Module1/image2.png)
---
#  Types of Relationships
---
## 1. Bloques de Construcción de una Relación
Para dibujar cómo interactúan los datos, necesitamos tres elementos:
* **Entidades:** Representadas por **rectángulos** (ej. Libro, Autor).
* **Conjuntos de Relaciones:** Representados tradicionalmente por un **rombo (diamante)**.
* **Líneas de conexión:** Unen las entidades.

## 2. Notación "Crow's Foot" (Pata de Gallo)
Aunque existen varias formas de dibujar relaciones (como usar rombos), este curso y la industria suelen usar la notación **Crow's Foot** para mayor claridad.
* Se usan símbolos al final de las líneas (como `<` o `>`) para indicar cantidad.
* **Atributos:** En estos diagramas de relaciones, a veces se omiten los óvalos de atributos para no saturar el dibujo y enfocarse solo en las conexiones.

![Crow's Foot Notation Chart](https://www.researchgate.net/profile/Indrajit-Kaur/publication/323698748/figure/fig1/AS:603175409549312@1520822608466/Crows-Foot-Notation.png)

## 3. Clasificación de las Relaciones
Usando el ejemplo de "Libros" y "Autores", podemos definir tres tipos principales:

### A. Uno a Uno (1:1)
* **Definición:** Una entidad se relaciona únicamente con otra entidad individual.
* **Ejemplo:** Un libro es escrito por **un solo** autor.
* **Representación:** Líneas simples o gruesas que conectan directamente una entidad con la otra.

### B. Uno a Muchos (1:N)
* **Definición:** Una entidad participa en múltiples relaciones con otra.
* **Ejemplo:** Un autor escribe **muchos** libros (pero cada libro tiene solo un autor).
* **Representación:** Se usa el símbolo de "pata de gallo" (o el símbolo `<`) en el lado de "Muchos".

### C. Muchos a Muchos (M:N)
* **Definición:** Múltiples registros de una tabla se relacionan con múltiples registros de otra.
* **Ejemplo:** **Muchos** autores escriben **muchos** libros (un libro tiene coautores y esos autores tienen otros libros).
* **Representación:** Se usan símbolos de "pata de gallo" en **ambos extremos** de la línea.

![Tipos de Relaciones ERD: 1:1, 1:N, M:N](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/ERD-Notation.PNG)


---
#  Mapping Entities to Tables
## 1. El Proceso de Traducción
El Diagrama Entidad-Relación (ERD) es la base para diseñar una base de datos. Para llevarlo a la realidad en un sistema relacional, se sigue un proceso de **mapeo**:

* **La Entidad:** Se traduce directamente al **Nombre de la Tabla**.
* **Los Atributos:** Se convierten en las **Columnas** de dicha tabla.

## 2. Construcción de la Tabla
Una tabla en el modelo relacional es la combinación de filas y columnas. El proceso ocurre en tres pasos:

1.  **Definir la Tabla:** Se toma el nombre de la entidad (ej. *Book*).
2.  **Crear las Columnas:** Se añaden los campos basados en los atributos (ej. *Title, Edition, Price*).
3.  **Poblar con Datos:** Se agregan los valores individuales, lo que crea las **Filas** (también llamadas registros o tuplas).

### Ejemplo práctico:
| Elemento ERD (Diseño) | Elemento SQL (Base de Datos) | Ejemplo (Biblioteca) |
| :--- | :--- | :--- |
| **Entidad** | **Tabla** | Author |
| **Atributo** | **Columna** | First_Name, Last_Name |
| **Valor de dato** | **Fila / Registro** | "J.K.", "Rowling" |

## 3. Conclusión
El mapeo asegura que la estructura lógica que diseñamos en papel (o software de diagramación) se convierta en una estructura física donde el software puede almacenar y recuperar información de manera organizada.

---
---
#  Relational Model Concepts
---
## 1. Origen y Fundamentos
El modelo relacional fue propuesto en **1970** y se basa en la teoría matemática de **Conjuntos (Sets)**.
* **Conjunto (Set):** Colección no ordenada de elementos distintos (sin duplicados) del mismo tipo.
* **Relación (Relation):** Es el término matemático para lo que comúnmente llamamos **Tabla**. Una base de datos relacional es un conjunto de relaciones.

## 2. Componentes de una Relación
Una relación se compone de dos partes fundamentales:

### A. Esquema Relacional (Relational Schema)
Es la estructura o el diseño. Especifica:
* El nombre de la relación (Tabla).
* El nombre de las columnas (Atributos).
* El tipo de dato de cada columna (ej. `CHAR`, `VARCHAR`).
* *Ejemplo:* Definir que la tabla "Autor" tiene una columna "ID" numérica y un "Nombre" de texto.

Author(Author_ID:char, lastname: varchar, firstname: varchar, email: varchar, city: varchar, country:char)

### B. Instancia Relacional (Relational Instance)
Es la tabla con los datos reales en un momento específico.
* Se compone de las columnas (campos) y las filas (tuplas) con información.

| Author_ID | Lastname | Firstname | Email | City | Country |
| :--- | :--- | :--- | :--- | :--- | :--- |
| A1 | Chong | Raul | rfc@ibm.com | Toronto | CA |
| A2 | Ahuja | Rav | ra@ibm.com | Toronto | CA |
| A3 | Hakes | Ian | ih@ibm.com | Toronto | CA |
| A4 | Sharma | Neeraj | ns@ibm.com | Chennai | IN |
| A5 | Perniu | Liviu | lp@univ.com | Transilvania | RO |

-   Rows: Tuples
-   Columns: Attributes or fields
-   Degree: Number of attributes or columns in a relation
-   Cardinality: Number of tuples or rows


## 3. Terminología Clave: Grado y Cardinalidad
Estos dos conceptos suelen ser preguntas de examen para medir el tamaño de una tabla:

* **Grado (Degree):** Número de **Atributos** (Columnas) en una relación.
    * *Si la tabla tiene: ID, Nombre, Apellido, Email $\rightarrow$ El Grado es 4.*
* **Cardinalidad (Cardinality):** Número de **Tuplas** (Filas/Registros) en una relación.
    * *Si tengo 5 autores registrados $\rightarrow$ La Cardinalidad es 5.*

| Término Matemático | Término Común | Métrica Asociada |
| :--- | :--- | :--- |
| **Relación** | Tabla | - |
| **Tupla** | Fila / Registro | **Cardinalidad** (Cantidad de filas) |
| **Atributo** | Columna / Campo | **Grado** (Cantidad de columnas) |

---
##  Assignment 1
In this module, you learned that Entity-Relationship Diagrams are a tool to design relational databases, and the concepts of a relational model including the terms entity, attribute, degree, and cardinality. Now let us try and apply the concepts we have learned in this module to a real world example of a database. We will be working on a relational database schema called Car dealership. The diagram below show the schema diagram for the Car Dealership relational database schema.


![Assignmet1](imagenes/SQL/Module1/assignment1.png)

A database has to be designed to keep track of automobile sales in a car dealership.Please answer the following questions based on the above schema.The answers to these questions are given on the next page.

-   Question 1 : How many relations does the Car dealership Schema contain?
There are 3 defined entities/tables:
    +   Car
    +   Sale
    +   Salesperson
-    Question 2: How many columns does the relation Car contain?
The relation car contain 4 columns:
    +   Serial no
    +   Model
    +   Manufacturer
    +   Price
-   Question 3: What is the degree of the relation Salesperson?
The "Degree" refers to the number of attributes (columns). 
The relation SALESPERSON has: 
    +   Salesperson_id 
    +   Name
    +   Phone

---
---
##  Quiz_1
### Question 1
What is a Database?

-   [ ]A program that stores data
-   [ ]Stores data in tabular form
-   [ ]A repository of data
-   [X]All of the above

### Question 2
Advantages of the relational model include:

-   [ ]Provides logical and physical data independence
-   [ ]Data is stored in simple data structures
-   [ ]It is the most used data model
-   [X]All of the above

### Question 3
In an Entity-Relationship diagram, the Entity Name maps to the Table name, the attributes map to the ...

-   [ ]Table rows and columns
-   [X]Table columns
-   [ ]Table rows
-   [ ]None of the above

---
---
#   Module 2 - Relational Model Constraints and Data Objects
---
#  Relational Model Constraints Introduction
---
## 1. Referencia (Referencing)
En el modelo relacional, los datos deben seguir reglas.  
La **Referencia** es la capacidad de una entidad (tabla) de apuntar a otra para buscar información (ej. un Libro "refiere" a un Autor).
* Esto establece la **Integridad de Datos** entre las relaciones, asegurando que los vínculos sean válidos.

## 2. Tipos de Claves (Keys)
Las claves son los conectores del modelo relacional.

### A. Primary Key (PK) - Clave Primaria
* **Definición:** Es un atributo (columna) que identifica de manera **única** a cada fila en una tabla.
* **Función:** Asegura que no haya registros duplicados.
* **Símbolo:** En los diagramas ER, suele marcarse con un icono especial o subrayado.
* *Ejemplo:* `Author_ID` en la tabla de Autores.

### B. Foreign Key (FK) - Clave Foránea
* **Definición:** Es un conjunto de columnas en una tabla que se refiere a la **Clave Primaria** de *otra* tabla.
* **Función:** Crea el vínculo real entre dos tablas.
* **Símbolo:** En los diagramas, suele aparecer con las siglas `(FK)`.
* *Ejemplo:* `Book_ID` dentro de la tabla "Copias".


## 3. Roles de las Tablas (Parent vs Child)
Dependiendo de dónde estén las claves, las tablas reciben nombres jerárquicos:

* **Parent Table (Tabla Padre):**
    * Es la tabla que contiene la **Clave Primaria**.
    * Es la fuente "original" de los datos.
* **Dependent / Child Table (Tabla Dependiente o Hija):**
    * Es la tabla que contiene la **Clave Foránea**.
    * Se llama "dependiente" porque los datos en su columna FK deben existir primero en la tabla Padre.

---
---
#  Relational Model Constraints Advanced
---
## 1. Referencia (Referencing)
En el modelo relacional, los datos deben seguir reglas. La **Referencia** es la capacidad de una entidad (tabla) de apuntar a otra para buscar información (ej. un Libro "refiere" a un Autor).
* Esto establece la **Integridad de Datos** entre las relaciones, asegurando que los vínculos sean válidos.

## 2. Tipos de Claves (Keys)
Las claves son los conectores del modelo relacional.

### A. Primary Key (PK) - Clave Primaria
* **Definición:** Es un atributo (columna) que identifica de manera **única** a cada fila en una tabla.
* **Función:** Asegura que no haya registros duplicados.
* **Símbolo:** En los diagramas ER, suele marcarse con un icono especial o subrayado.
* *Ejemplo:* `Author_ID` en la tabla de Autores.

### B. Foreign Key (FK) - Clave Foránea
* **Definición:** Es un conjunto de columnas en una tabla que se refiere a la **Clave Primaria** de *otra* tabla.
* **Función:** Crea el vínculo real entre dos tablas.
* **Símbolo:** En los diagramas, suele aparecer con las siglas `(FK)`.
* *Ejemplo:* `Book_ID` dentro de la tabla "Copias".


## 3. Roles de las Tablas (Parent vs Child)
Dependiendo de dónde estén las claves, las tablas reciben nombres jerárquicos:

* **Parent Table (Tabla Padre):**
    * Es la tabla que contiene la **Clave Primaria**.
    * Es la fuente "original" de los datos.
* **Dependent / Child Table (Tabla Dependiente o Hija):**
    * Es la tabla que contiene la **Clave Foránea**.
    * Se llama "dependiente" porque los datos en su columna FK deben existir primero en la tabla Padre.

---
#  Additional Information
---
## 1. Jerarquía de Claves (Keys)
En una tabla pueden existir varias columnas capaces de identificar una fila única. La terminología correcta es:

* **Claves Candidatas (Candidate Keys):** Son todas las claves que *podrían* servir como identificador único.
* **Clave Primaria (Primary Key):** Es la clave candidata que elegimos oficialmente para identificar las filas.
* **Claves Secundarias (Secondary Keys):** Son las claves candidatas que NO fueron elegidas como primarias.

### Reglas de Oro para la Clave Primaria
Para que una Primary Key sea válida en una base de datos relacional, debe cumplir tres condiciones obligatorias:

1.  **Unicidad:** El valor debe ser único para cada instancia (fila); no se puede repetir.
2.  **Not Null (No Nulo):** No puede haber valores faltantes. Si la clave se compone de varios atributos, *todos* deben tener valor.
3.  **Inmutabilidad:** Una vez creado, el valor de la Clave Primaria **no puede cambiarse**.

## 2. Integridad Semántica
Se refiere a la corrección del significado de los datos. Garantiza que el dato introducido sea un "valor permitido" para esa fila.
* El valor debe estar dentro del **dominio** (el conjunto de valores aceptables).
* *Ejemplo:* Si la columna es "Cantidad", la integridad semántica se viola si intentas escribir texto en lugar de números.

## 3. Restricciones Semánticas (Semantic Constraints)
Son reglas más complejas que a veces no se pueden definir solo con el tipo de dato. También se llaman **Reglas de Negocio** (Business Rules) o reglas basadas en la aplicación.

* Son definidas por los usuarios o administradores.
* *Ejemplos:*
    * "Una clase puede tener un máximo de 30 estudiantes".
    * "El salario de un empleado no puede ser mayor que el de su jefe".

### Restricciones de Dominio (Tipos de Datos)
Especifican que el valor de un atributo debe pertenecer a un tipo de dato específico. Los más comunes son:

* **Números:** Enteros (Integer, Long), Reales (Float, Double).
* **Texto:** Caracteres (Char), Cadenas de longitud fija o variable (Varchar).
* **Lógicos:** Booleanos (True/False).
* **Tiempo:** Date, Time, Timestamp.
* **Monetarios:** Money.
* **Enumerados:** Una lista explícita de valores permitidos (ej. "Rojo", "Verde", "Azul").

---

A database has to be designed to keep track of automobile sales in a car dealership.Please answer the following questions based on the above schema.

##  Question 1: Identify the primary key of the relation Car.
The primary key of the relation car is: serial_No
##  Question 2: Identify the foreign key of the relation Sale.
The foreign key of the relation sale is: Serial_No
##  Question 3: How many constraint types are there in relation Sale?
There are 2 constraint types in the relation Sale: Primary key and Foreign Key
---
#   Quiz_2
##  Question 1
Which of the following statements is true?
-   [ ]A table can have a primary key and a foreign key
-   [ ]A Foreign Key is a set of columns referring to a primary key of another table
-   [ ]A primary key uniquely identifies each row in a table
-   [x]All of the above

Explicación: Todas las afirmaciones son correctas: una tabla puede tener ambas claves, la Foreign Key referencia a otra tabla y la Primary Key identifica filas únicas.

##  Question 2
Which Relational Constraint prevents duplicate values in a table?
-   [x]Entity Integrity constraint
-   [ ]Null constraint
-   [ ]Check constraint
-   [ ]All of the above

La "Integridad de Entidad" se refiere a las reglas de la Primary Key.  
Como la Primary Key debe ser única, es la restricción que evita que existan dos filas exactamente iguales (duplicados) en la tabla.

##  Question 3
The Semantic Integrity Constraint defines the relationships between tables. (T/F)
-   [ ]True
-   [x]False

La Integridad Semántica se asegura de que los datos tengan sentido (ej. que no pongas letras en un campo de salario).
Lo que define las relaciones entre tablas es la Integridad Referencial (Referential Integrity) mediante las Foreign Keys.

---
---
#   Module 3
---
#  Types of SQL statements (DDL vs. DML)

Los statements de SQL se usan para interactuar con entidades (tablas), atributos (columnas) y sus tuplas (filas con valores) en bases de datos relacionales.

Se dividen en dos grandes categorías:

## 1. DDL — Data Definition Language
Se usan para **definir, cambiar o eliminar objetos** de la base de datos (como tablas).

| Comando | Descripción |
| :--- | :--- |
| `CREATE` | Crea tablas y define sus columnas |
| `ALTER` | Modifica tablas: agrega/elimina columnas, cambia tipos de datos |
| `TRUNCATE` | Elimina los **datos** de una tabla, pero no la tabla en sí |
| `DROP` | Elimina la tabla completamente |

## 2. DML — Data Manipulation Language
Se usan para **leer y modificar datos** dentro de las tablas.  
También se conocen como operaciones **CRUD** (Create, Read, Update, Delete).

| Comando | Descripción |
| :--- | :--- |
| `INSERT` | Inserta una o varias filas en una tabla |
| `SELECT` | Lee/selecciona una o varias filas de una tabla |
| `UPDATE` | Edita una o varias filas existentes |
| `DELETE` | Elimina una o varias filas de una tabla |

> **Diferencia clave:** DDL trabaja sobre la **estructura** de la base de datos; DML trabaja sobre los **datos** dentro de esa estructura.

---
#   CREATE TABLE statement

Es el DDL statement más común. Se usa para **crear tablas** y definir sus columnas.

## 1. Sintaxis General

```sql
CREATE TABLE nombre_tabla (
    columna1  tipo_dato  [restricciones],
    columna2  tipo_dato  [restricciones],
    ...
);
```

* Cada fila dentro de los paréntesis define una columna: nombre + tipo de dato + restricciones opcionales.
* Las definiciones de columnas se separan por comas.

## 2. Tipos de Datos Comunes

| Tipo | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `CHAR(n)` | Cadena de caracteres de longitud **fija** | `CHAR(2)` → "AB" |
| `VARCHAR(n)` | Cadena de caracteres de longitud **variable**, hasta n caracteres | `VARCHAR(24)` → "Alberta" |

## 3. Restricciones Comunes

| Restricción | Descripción |
| :--- | :--- |
| `PRIMARY KEY` | Identifica de forma única cada fila; no permite duplicados |
| `NOT NULL` | El campo no puede quedar vacío |

## 4. Ejemplos Prácticos

### Ejemplo simple — Tabla de provincias de Canadá:
```sql
CREATE TABLE provinces (
    id    CHAR(2)     PRIMARY KEY NOT NULL,
    name  VARCHAR(24)
);
```
* `id`: almacena el código de dos letras de la provincia (ej. "AB", "BC").
* `name`: almacena el nombre completo (ej. "Alberta", "British Columbia").

### Ejemplo elaborado — Tabla Author (base de datos de biblioteca):
```sql
CREATE TABLE author (
    author_id   CHAR(2)      PRIMARY KEY NOT NULL,
    lastname    VARCHAR(15)  NOT NULL,
    firstname   VARCHAR(15)  NOT NULL,
    email       VARCHAR(40),
    city        VARCHAR(15),
    country     CHAR(2)
);
```
* `author_id` es la **Primary Key** → evita duplicados.
* `lastname` y `firstname` tienen `NOT NULL` → un autor siempre debe tener nombre.
* `email`, `city` y `country` son opcionales (pueden ser nulos).

---
#   INSERT statement

Es un **DML statement** usado para agregar nuevas filas a una tabla ya existente.

## 1. Sintaxis General

```sql
INSERT INTO nombre_tabla (columna1, columna2, ...)
VALUES (valor1, valor2, ...);
```

* `nombre_tabla`: identifica la tabla donde se insertará el dato.
* Lista de columnas: identifica cada columna de la tabla.
* `VALUES`: especifica los valores a agregar para cada columna.

> **Regla importante:** el número de valores en `VALUES` debe ser igual al número de columnas especificadas.

## 2. Método 1 — Insertar una fila a la vez

```sql
INSERT INTO author (author_id, lastname, firstname, email, city, country)
VALUES ('A1', 'Chong', 'Raul', 'rfc@ibm.com', 'Toronto', 'CA');
```

## 3. Método 2 — Insertar múltiples filas a la vez

Cada fila se separa con una coma dentro del `VALUES`:

```sql
INSERT INTO author (author_id, lastname, firstname, email, city, country)
VALUES
    ('A1', 'Chong',  'Raul', 'rfc@ibm.com', 'Toronto', 'CA'),
    ('A2', 'Ahuja',  'Rav',  'ra@ibm.com',  'Toronto', 'CA');
```

---
#  SELECT statement

Es un **DML statement** usado para leer y recuperar datos de una tabla. También se llama **query**, y su salida se llama **result set** o result table.

## 1. Sintaxis General

```sql
SELECT columna1, columna2, ...
FROM nombre_tabla
WHERE condicion;
```

## 2. Formas de usar SELECT

### Seleccionar todas las columnas
```sql
SELECT * FROM book;
```
Devuelve todas las filas y todas las columnas de la tabla.

### Seleccionar columnas específicas
```sql
SELECT book_id, title FROM book;
```
* Solo se muestran las columnas indicadas.
* El orden de las columnas en el resultado sigue el orden del `SELECT`.

## 3. Filtrar resultados con WHERE

La cláusula `WHERE` restringe el result set usando un **predicado**.

> **Predicado:** condición que evalúa a `TRUE`, `FALSE` o `UNKNOWN`.

```sql
SELECT book_id, title
FROM book
WHERE book_id = 'B1';
```
Solo devuelve la(s) fila(s) donde la condición es verdadera.

## 4. Operadores de Comparación

| Operador | Significado |
| :---: | :--- |
| `=` | Igual a |
| `>` | Mayor que |
| `<` | Menor que |
| `>=` | Mayor o igual que |
| `<=` | Menor o igual que |
| `<>` | No igual a |

---
#  UPDATE and DELETE statements

Ambos son **DML statements** usados para modificar datos existentes en una tabla.

## 1. UPDATE — Modificar datos

### Sintaxis
```sql
UPDATE nombre_tabla
SET columna1 = valor1, columna2 = valor2, ...
WHERE condicion;
```

### Ejemplo — Cambiar el nombre del autor con `author_id = 'A2'`:
```sql
UPDATE author
SET lastname = 'Khatta', firstname = 'Lakshmi'
WHERE author_id = 'A2';
```

> **Advertencia:** Si omites el `WHERE`, **todas las filas** de la tabla serán actualizadas.

## 2. DELETE — Eliminar filas

### Sintaxis
```sql
DELETE FROM nombre_tabla
WHERE condicion;
```

### Ejemplo — Eliminar los autores con `author_id` A2 y A3:
```sql
DELETE FROM author
WHERE author_id IN ('A2', 'A3');
```

> **Advertencia:** Si omites el `WHERE`, **todas las filas** de la tabla serán eliminadas (pero la tabla en sí permanece — para eso existe `TRUNCATE`).

## 3. Resumen — La importancia del WHERE

| Statement | Sin WHERE | Con WHERE |
| :--- | :--- | :--- |
| `UPDATE` | Modifica **todas** las filas | Modifica solo las filas que cumplen la condición |
| `DELETE` | Elimina **todas** las filas | Elimina solo las filas que cumplen la condición |

---


---
#   Quiz_3

---
---
#   Module 4
---
#  String Patterns, Ranges, and Sets

Técnicas avanzadas para filtrar datos en un `SELECT` cuando no conocemos el valor exacto del predicado.

## 1. String Patterns — LIKE

Se usa cuando no recordamos el valor exacto de un campo. El operador `LIKE` busca un patrón dentro de una columna usando el **wildcard `%`** (sustituye cualquier cantidad de caracteres).

| Patrón | Significado |
| :--- | :--- |
| `'R%'` | Empieza con R |
| `'%R'` | Termina con R |
| `'%R%'` | Contiene R en cualquier posición |

### Ejemplo — Autores cuyo nombre empieza con "R":
```sql
SELECT firstname FROM author
WHERE firstname LIKE 'R%';
```
Resultado: devuelve "Raul" y "Rav".

## 2. Ranges — BETWEEN AND

Se usa para filtrar valores dentro de un rango numérico (inclusive en ambos extremos). Es equivalente a usar `>=` y `<=` combinados con `AND`, pero más corto.

### Ejemplo — Libros con entre 290 y 300 páginas:
```sql
-- Con operadores de comparación:
SELECT * FROM book WHERE pages >= 290 AND pages <= 300;

-- Con BETWEEN (equivalente y más simple):
SELECT * FROM book WHERE pages BETWEEN 290 AND 300;
```

## 3. Sets — IN

Se usa cuando los valores no pueden agruparse en un rango continuo. El operador `IN` permite especificar una lista de valores posibles en el `WHERE`.

### Ejemplo — Autores de Australia o Brasil:
```sql
SELECT * FROM author
WHERE country IN ('AU', 'BR');
```

> Sin `IN`, habría que escribir: `WHERE country = 'AU' OR country = 'BR'` — y se vuelve muy largo con más valores.

## Resumen

| Técnica | Operador | Cuándo usarla |
| :--- | :---: | :--- |
| String Pattern | `LIKE` | No conocemos el valor exacto, pero sí parte de él |
| Range | `BETWEEN AND` | Queremos valores dentro de un rango numérico |
| Set | `IN` | Queremos comparar contra una lista de valores específicos |

---
#  Sorting Result Sets

La cláusula `ORDER BY` se usa para ordenar el result set por una columna específica.

## 1. Sintaxis

```sql
SELECT columna1, columna2
FROM nombre_tabla
ORDER BY columna [ASC | DESC];
```

* Por defecto (sin especificar), el orden es **ascendente (ASC)**.
* Para orden descendente se usa la keyword **DESC**.

## 2. Ejemplos

### Orden ascendente (por defecto) — títulos de libros en orden alfabético:
```sql
SELECT title FROM book
ORDER BY title;
```

### Orden descendente:
```sql
SELECT title FROM book
ORDER BY title DESC;
```

### Usando número de columna en lugar del nombre:
En vez de escribir el nombre de la columna, se puede indicar su **número de posición** en el `SELECT`.

```sql
SELECT title, pages FROM book
ORDER BY 2;
```
Aquí `2` hace referencia a `pages` (la segunda columna listada). El resultado se ordena por número de páginas en forma ascendente.

## 3. Resumen

| Keyword | Orden |
| :--- | :--- |
| `ORDER BY columna` | Ascendente (A→Z, 1→9) por defecto |
| `ORDER BY columna ASC` | Ascendente (explícito) |
| `ORDER BY columna DESC` | Descendente (Z→A, 9→1) |
| `ORDER BY 2` | Por la segunda columna del SELECT |

---
#  Grouping Result Sets

Técnicas para eliminar duplicados y agrupar resultados en un `SELECT`.

## 1. DISTINCT — Eliminar duplicados

Cuando una columna tiene valores repetidos, `DISTINCT` reduce el result set mostrando cada valor solo una vez.

```sql
-- Sin DISTINCT: devuelve 20 filas (una por autor, con países repetidos)
SELECT country FROM author ORDER BY 1;

-- Con DISTINCT: devuelve solo 6 filas (un país único por fila)
SELECT DISTINCT country FROM author ORDER BY 1;
```

## 2. GROUP BY — Agrupar resultados

Agrupa las filas que tienen el mismo valor en una columna y permite aplicar funciones de agregación como `COUNT`.

### Ejemplo — Contar cuántos autores hay por país:
```sql
SELECT country, COUNT(country)
FROM author
GROUP BY country;
```
* La segunda columna es calculada por `COUNT`, por lo que su nombre aparece como un número genérico.

## 3. AS — Renombrar columnas calculadas

Para darle un nombre legible a una columna calculada se usa la keyword `AS`.

```sql
SELECT country, COUNT(country) AS count
FROM author
GROUP BY country;
```
Ahora la segunda columna se llama `count` en vez de `2`.

## 4. HAVING — Filtrar grupos

`HAVING` es como un `WHERE` pero aplicado **después** del `GROUP BY`. Se usa para filtrar los grupos resultantes.

> **Diferencia clave:**
> * `WHERE` filtra filas **antes** de agrupar (sobre el result set completo).
> * `HAVING` filtra grupos **después** del `GROUP BY`.

### Ejemplo — Países con más de 4 autores:
```sql
SELECT country, COUNT(country) AS count
FROM author
GROUP BY country
HAVING COUNT(country) > 4;
```
Resultado: solo China (6) e India (6).

## 5. Resumen

| Cláusula | Función |
| :--- | :--- |
| `DISTINCT` | Elimina filas duplicadas del result set |
| `GROUP BY` | Agrupa filas con el mismo valor en una columna |
| `AS` | Renombra columnas calculadas |
| `HAVING` | Filtra grupos (solo funciona con `GROUP BY`) |

---
---
#   Course Summary

## Lo que aprendiste en este curso:

### Módulo 1 — Introducción
* Una base de datos relacional almacena datos en forma tabular con relaciones entre tablas.
* Los RDBMS son la base de aplicaciones en industrias como banca, transporte y salud.

### Módulo 2 — Modelos y Restricciones
* **Modelo de Información:** conceptual, define relaciones entre objetos.
* **Modelo de Datos:** específico y detallado, es el blueprint de cualquier sistema de base de datos.
* **Modelo Relacional:** el más usado, permite independencia de datos.
* Diagramas Entidad-Relación (ERD), tipos de relaciones y los 6 tipos de restricciones del modelo relacional.

### Módulo 3 — Los 5 comandos básicos de SQL
* `CREATE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE`
* Diferencia entre DDL (estructura) y DML (datos).

### Módulo 4 — Técnicas avanzadas de consulta
* **String patterns:** `LIKE` con el wildcard `%`
* **Ranges:** `BETWEEN AND`
* **Sets:** `IN`
* **Ordenamiento:** `ORDER BY` (ASC / DESC)
* **Agrupamiento:** `GROUP BY`, `DISTINCT`, `HAVING`, `AS`

### Módulo 5 — JOINs
* Combinar datos de dos o más tablas con el operador `JOIN`.
* **Inner Join:** solo filas coincidentes.
* **Outer Joins:** Left, Right y Full — incluyen también filas sin coincidencia.

---
---
#   Module 5
#  Join Overview

Un **JOIN** combina filas de dos o más tablas basándose en una relación entre ciertas columnas de esas tablas.

## 1. ¿Por qué usar JOINs?

Un `SELECT` simple recupera datos de una sola tabla. Cuando necesitamos datos de **dos o más tablas**, usamos el operador JOIN.

* Ejemplo: saber qué prestatario tiene qué copia de un libro en préstamo requiere datos de las tablas `borrower`, `loan` y `copy` al mismo tiempo.

## 2. El vínculo entre tablas: PK y FK

Para hacer un JOIN, primero hay que identificar la relación entre las tablas:

* **Primary Key (PK):** identifica de forma única cada fila en su tabla.
* **Foreign Key (FK):** columna en una tabla que referencia la PK de otra tabla.

> Ejemplo: la entidad `loan` tiene el atributo `borrower_id (FK)`, que referencia la PK de la entidad `borrower`. Ese `borrower_id` compartido es el **vínculo** que permite hacer el JOIN.

## 3. JOINs con más de dos tablas

Se pueden encadenar múltiples JOINs:

1. Unir `borrower` y `loan` por `borrower_id`.
2. Luego unir `loan` y `copy` por `copy_id`.

Cada JOIN adicional agrega una nueva tabla al resultado.

## 4. Tipos de JOIN

| Tipo | Descripción |
| :--- | :--- |
| **Inner Join** | Devuelve solo las filas que tienen valores coincidentes en **ambas** tablas |
| **Outer Join** | Devuelve las filas coincidentes **y también** las filas de una o ambas tablas que no tienen coincidencia |

> El tipo más común es el **Inner Join**.

---
#  Inner Join

El **Inner Join** devuelve **solo las filas que tienen valores coincidentes** en la columna común de ambas tablas. Las filas sin coincidencia no aparecen en el resultado.

## 1. Sintaxis

```sql
SELECT columnas
FROM tabla1 AS alias1
INNER JOIN tabla2 AS alias2
ON alias1.columna_comun = alias2.columna_comun;
```

* La tabla a la izquierda del `JOIN` se llama **left table**.
* `ON` especifica el predicado del join: la condición de igualdad entre las columnas relacionadas.
* `AS` define un **alias** para cada tabla, evitando escribir el nombre completo repetidamente.

## 2. Ejemplo — Prestatarios con libros en préstamo

Queremos saber qué personas están tomando libros prestados y la fecha del préstamo. Los datos están en las tablas `borrower` y `loan`.

```sql
SELECT B.borrower_id, B.lastname, B.country, L.borrower_id, L.loan_date
FROM borrower AS B
INNER JOIN loan AS L
ON B.borrower_id = L.borrower_id;
```

* `B` es el alias de `borrower` (left table).
* `L` es el alias de `loan`.
* Solo aparecen las filas donde el `borrower_id` existe en **ambas** tablas.

## 3. Comportamiento clave

| Situación | ¿Aparece en el resultado? |
| :--- | :---: |
| Fila con coincidencia en ambas tablas | ✓ Sí |
| Fila sin coincidencia en la otra tabla | ✗ No |

---
#  Outer Join

A diferencia del Inner Join, el **Outer Join** devuelve las filas coincidentes **y también** las filas que no tienen coincidencia en la otra tabla. Existen tres tipos.

## 1. Left Outer Join (LEFT JOIN)

Devuelve **todas las filas de la tabla izquierda** y solo las filas coincidentes de la tabla derecha. Las filas de la izquierda sin coincidencia muestran `NULL` en las columnas de la tabla derecha.

```sql
SELECT B.borrower_id, B.lastname, B.country, L.borrower_id, L.loan_date
FROM borrower AS B
LEFT JOIN loan AS L
ON B.borrower_id = L.borrower_id;
```

* Todos los prestatarios aparecen en el resultado.
* Los que nunca tomaron un libro muestran `NULL` en `loan_date`.

## 2. Right Outer Join (RIGHT JOIN)

Devuelve **todas las filas de la tabla derecha** y solo las filas coincidentes de la tabla izquierda. Las filas de la derecha sin coincidencia muestran `NULL` en las columnas de la tabla izquierda.

```sql
SELECT B.borrower_id, B.lastname, B.country, L.borrower_id, L.loan_date
FROM borrower AS B
RIGHT JOIN loan AS L
ON B.borrower_id = L.borrower_id;
```

* Todos los préstamos aparecen en el resultado.
* Si un préstamo no tiene prestatario registrado, las columnas de `borrower` muestran `NULL` → indica un problema: libro prestado a persona desconocida.

## 3. Full Outer Join (FULL JOIN)

Devuelve **todas las filas de ambas tablas**. Las filas sin coincidencia en cualquiera de los lados muestran `NULL` en las columnas de la otra tabla.

```sql
SELECT B.borrower_id, B.lastname, B.country, L.borrower_id, L.loan_date
FROM borrower AS B
FULL JOIN loan AS L
ON B.borrower_id = L.borrower_id;
```

* Puede generar un result set muy grande.
* Combina los resultados del LEFT JOIN y RIGHT JOIN.

## 4. Resumen Comparativo

| Tipo | Filas de la tabla izquierda | Filas de la tabla derecha |
| :--- | :---: | :---: |
| `INNER JOIN` | Solo coincidentes | Solo coincidentes |
| `LEFT JOIN` | **Todas** | Solo coincidentes |
| `RIGHT JOIN` | Solo coincidentes | **Todas** |
| `FULL JOIN` | **Todas** | **Todas** |

---
---

# COurse Summary

