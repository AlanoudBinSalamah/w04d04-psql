
# DATA

## What is data ? 
 It is information processed or stored by a computer. Data can power business decisions through data analysis like never before. Have you ever wondered how you get such accurate shopping ?

## What does it look like ?
may be in the form of text documents, images, audio clips, software programs, or other types of data.

> when someone ask you show me data ask back what type of data ? :p  

---

# DATABASE

Database is a tool for storing massive amounts of information that can be retrieved at a later point in time. It represents a collection of individual pieces of data stored in a highly structured and searchable way; and the most important thing is to keep your data president which means it will be always there when you need them 

Inside a database, we do basic actions like create, read, update, and destroy data – these operations are commonly referred to by the acronym CRUD and are essential to modern web development.

Databases are everywhere. They drive the mobile applications and the websites you use everyday.  without databases many of the services we rely on wouldn't be able to operate as they do today. 

## Database Types   
* noSQL (no relational or document base database) 
* SQL  relational database where we can represent or data on columns and rows  )

---

# SQL
SQL stands for Structured Query Language, and it is a language universally used and adapted to interact with relational databases. When you use a SQL client and connect to a relational database that contains tables with data, the scope of what you can do with SQL commands includes:

* Inserting data
* Querying or retrieving data
* Updating or deleting data
* Creating new tables and entire databases
* Control permissions of who can have access to our data

There are many databases that understand SQL, such as MySQL, PostgreSQL, MS SQL, Oracle and SQLite. Each of these databases can be read or queried using the SQL programming language.

## Understanding of both databases and the SQL language.
 There are two important components to each data base. The information that's stored in it called data, and how the data is organized called the schema. 

 The schema establishes how that data should be stored and divided into different sections. The schema further determines how each of the sections relates to other sections. These sections are called tables.

```
// CUSTOMERS
 id  |     name      | phone_number 
-----+---------------+--------------
   6 | Jackie Casper | 0505555458
   7 | Ghadeer       | 0503333553
   8 | YAHYA         | 050000078
   9 | SAMAR         | 00007866
 100 | JUMANAH       | 050300078
 101 | OMAR          | 05063346

// ORDERS
id | phone_numbers |     order_date      |  status   | delivery_date | quantity | total 
----+---------------+---------------------+-----------+---------------+----------+-------
  1 | 509940822     | 2018-12-03 04:05:06 | delivered | 2018-12-05    |       12 |      
  2 |               | 2018-12-03 04:05:06 | delivered | 2018-12-05    |       12 |      
  3 | 509940822     | 2018-12-03 04:05:06 | delivered | 2018-12-05    |       12 |      
  4 | 500220836     | 2018-12-05 04:05:06 | pending   | 2018-12-10    |       10 |      

// INVENTORY
 id |     item     | cost | stock | unit 
----+--------------+------+-------+------
  1 | Grabe Leaves |   20 |    15 | JAR
  1 | RICE         |   40 |    30 | CUP
  2 | LEMON        |   80 |   100 | KILO
```

For example : in our grapebusiness database we can have customer table , order table , inventory table  Each row represents a single thing. In the case of inventory it's a particular item type. If we look at the orders table Each row in this case is an individual order.

Database tables contain data with each table containing one type of thing. depending on the SQL you write, you can filter information.  For example, you could filter the table to get all of the items in the inventory table that have the stock count greater than 15.

You don't even have to show all columns. In fact, you can arrange the columns in any order you want. When you filter data in this way, no data has been deleted from the table. You're just selecting what information you want to bring back from the table with that query. All information is still in the database table. You can bring it all back with no trouble.

## Types of Data
* Text Type Examples
	* TEXT
	* VARCHAR
* Numeric Type Examples
	* INT
	* DOUBLE 

* Date Type Examples
	* DATETIME
	* DATE
	* TIMESTAMP

## Further Reading
* www.sqlstyle.guide
* PostgreSQL tutorial
* PSQL datatypes

```
\d customers
                                      Table "public.customers"
    Column    |         Type          | Collation | Nullable |                Default                
--------------+-----------------------+-----------+----------+---------------------------------------
 id           | integer               |           | not null | nextval('customers_id_seq'::regclass)
 name         | text                  |           |          | 
 phone_number | character varying(11) |           |          | 

```

Table columns are defined in the schema to have certain data types. A data type describes the value to be stored.

There are several data types you'll come across on a regular basis. There are text types, numeric types and data types. Text types are good for storing names or descriptions of things. Numeric types are good for storing prices, ages, and quantities of things. Dates are good for anything time related. While this isn't a comprehensive list of data types, text, numeric, and date types are a good starting point.

## why dataType

```
// INVENTORY
 id |     item     | cost | stock | unit 
----+--------------+------+-------+------
  1 | Grabe Leaves |   20 |    15 | JAR
  1 | RICE         |   40 |    30 | CUP
  2 | LEMON        |   80 |   100 | KILO
```

Imagine everything in this inventory table was just text. The item, cost, stock  are all text. If I wanted to sort by the current stock count, what result do you think I'd get? It won't be sorted properly This is because the stock count is sorted alphabetically, and not numerically.

> Having correct data types in your database not only helps with sorting but it also comes in handy for many other applications such as generating the sum of all sales figures.
> 
> Generating a sum and other mathematical operations can only be done by using with a numeric type. Trying to do math with text is impossible. In the case of an orders table  where the new delivery data is added all the time, the data is retrieved in the order it was entered by default.
> 
> Understanding that column date types can affect how data is retrieved helps people design the schema for the database.

While we're not designing the schema ourselves in this lesson, understanding data types will also help us understand how we compose the SQL queries.



# PostgreSql 

## NSTALL POSTGRE SQL ( MAC)

`brew install postgresql `
`brew services start postgresql`

## START THE SHELL COMMAND
` psql databasename `
  
` psql postgres `  

> postgres is the default database

## To see the users installed 
``` 
\du
\du+ 
```

### List all the database 
`\list`

## help to list all the command 
`\?`
`\h`

### CREATE A DATABASE
`CREATE DATABASE ; `
`CREATE DATABASE grapeleaves; `

### connect to the database 
`\connect grapeleaves `

### list tables 
`\dt`

## RENAME DATABASE
```
ALTER DATABASE databasename RENAME TO newdatabasename; 
```

```
ALTER DATABASE grapeleaves RENAME TO awesome_grapeleaves; 
```

### DELETING A TABLE 
`DROP DATABASE grapeleaves;` 

### CREATING A TABLE
```
CREATE TABLE table_name (
 column_name TYPE 
)
```

```
CREATE TABLE inventory(id SERIAL, item text, cost DOUBLE PRECISION , stock int , unit text);

CREATE TABLE customers(id SERIAL, name text, phone_number VARCHAR(10));

CREATE TABLE orders(id SERIAL, phone_number VARCHAR(10), order_date timestamp , status text , delivery_date DATE , quantity int );
```

## GET  TABLE INFO
`\d customers`

## ADDING NEW ROW ( NEW DATA)
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

INSERT INTO table_name VALUES (value1, value2, value3, ...);
```

```
INSERT INTO customers VALUES(DEFAULT,'nada','500220836');

INSERT INTO customers VALUES(DEFAULT,'nada','500220836');

INSERT INTO inventory VALUES(DEFAULT,'RICE' , 40 , 30 , 'CUP');

INSERT INTO inventory VALUES(DEFAULT,'Grabe Leaves' , 20 , 15 , 'JAR');

INSERT INTO inventory VALUES(DEFAULT,'LEMON' , 80 , 100 , 'KILO');

INSERT INTO orders VALUES(DEFAULT, '509940822', '2018-12-03 04:05:06', 'delivered' , '2018-12-05' , 12);

INSERT INTO orders VALUES(DEFAULT, '500220836', '2018-12-05 04:05:06', 'pending' , '2018-12-10' , 10);
```

### UPDATE 

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

```
UPDATE customers SET id=100 where name='JUMANAH';
```

```
UPDATE customers SET phone_number='509940822' WHERE id=1;
```


## READING DATA, QUERYING
```
SELECT column_1 FROM tablename;

SELECT column_1, column_2 … column_n
FROM table_name
WHERE conditions;
```

```
SELECT * FROM customers;
```

```
SELECT NAME, phone_number  FROM customers;
```

### USING SUM 
```
SELECT SUM(cost) from inventory ;
``` 

### QUERYING WITH DATE 
```
SELECT status FROM orders where delivery_date  >  '2018-12-05'
SELECT * from orders where delivery_date <='2018-12-05';
```

### USING LIKE 
```
SELECT * FROM customers where phone_number LIKE '%6'; 
 SELECT phone_number from customers where phone_number LIKE '%458';
SELECT * from customers where name LIKE '%MA%';
```

### USING BETWEEN 
```
SELECT SUM(cost) FROM inventory WHERE cost >= 10 and cost <= 30;
```

### USING LIMIT 
```
SELECT * FROM customers where phone_number LIKE '%6' LIMIT 1;
```

> USE LIMIT ONLY WITH SELECT 

### USING COUNT 

```
SELECT COUNT(*) FROM customers;
```

### USING ORDER 
```
SELECT name from customers ORDER BY name ASC;
SELECT name from customers ORDER BY name DESC;
```

### USING AND
```
SELECT *  FROM orders where phone_numbers like '%9%' and status='delivered';
```

###  GROUP BY 
```
SELECT  id,  SUM(cost)  FROM orders GROUP BY  id;
```

## DELETE
```
DELETE FROM table_name WHERE condition;
```

```
DELETE FROM orders WHERE id=1;
```

```
DELETE FROM customers where phone_number='Ghadeer';
```

```
DELETE FROM customers where phone_number='Jackie' or phone_number='custome' or  phone_number isNull ;
```


## OPERATION ON TABLS

### DELETE TABLE
```
DROP TABLE  orders
```

### ADD NEW COLUMN 
```
ALTER TABLE orders
ADD COLUMN total DOUBLE PRECISION;
```

### EDITE COLUMN TYPE 
```
ALTER TABLE customers ALTER COLUMN phone_number TYPE varchar(11);
```
