mysql> show databases;
+------------------------+
| Database               |
+------------------------+
| company                |
| company_db             |
| information_schema     |
| java_practice          |
| liabrary               |
| mysql                  |
| performance_schema     |
| student_skill_exchange |
| sys                    |
+------------------------+
9 rows in set (0.01 sec)

mysql> create database bank;
Query OK, 1 row affected (0.01 sec)

mysql> show databases;
+------------------------+
| Database               |
+------------------------+
| bank                   |
| company                |
| company_db             |
| information_schema     |
| java_practice          |
| liabrary               |
| mysql                  |
| performance_schema     |
| student_skill_exchange |
| sys                    |
+------------------------+
10 rows in set (0.00 sec)

mysql> use bank;
Database changed
mysql>
mysql> show tables;
Empty set (0.00 sec)

mysql> CREATE TABLE CUSTOMER(
    -> ID INT PRIMARY KEY,
    -> NAME VARCHAR(30),
    -> AGE INT ,
    -> BALANCE DECIMAL(10,2),
    -> CITY VARCHAR(45),
    -> EMAIL VARCHAR(30)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> SELECT*FROM CUSTOMER;
Empty set (0.00 sec)

mysql> DESC CUSTOMER;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| ID      | int           | NO   | PRI | NULL    |       |
| NAME    | varchar(30)   | YES  |     | NULL    |       |
| AGE     | int           | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
| CITY    | varchar(45)   | YES  |     | NULL    |       |
| EMAIL   | varchar(30)   | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(1,'AJAY',21,25000,'BEED','ajay@gmail.com');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(2,'SAKSHII',20,45000,'BEED','sakshi@gmail.com');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(3,'Amay',22,42000,'pune','amay@gmail.com');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(4,'amar',21,41000,'Chinchwad','amar@gmail.com');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(5,'mahesh',30,47000,'mumbai','mahesh@gmail.com');
Query OK, 1 row affected (0.01 sec)

mysql> select*from Customer;
+----+---------+------+----------+-----------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL            |
+----+---------+------+----------+-----------+------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com   |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com |
+----+---------+------+----------+-----------+------------------+
5 rows in set (0.00 sec)

mysql> Select*from Customer where balance >30,000;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',000' at line 1
mysql> Select*from Customer where balance >30000;
+----+---------+------+----------+-----------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL            |
+----+---------+------+----------+-----------+------------------+
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com |
+----+---------+------+----------+-----------+------------------+
4 rows in set (0.01 sec)

mysql> select*from customer where city IN (pune,mumbai);
ERROR 1054 (42S22): Unknown column 'pune' in 'where clause'
mysql> select*from customer where (pune,mumbai) IN City;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'City' at line 1
mysql> select*from customer where city IN('pune');
+----+------+------+----------+------+----------------+
| ID | NAME | AGE  | BALANCE  | CITY | EMAIL          |
+----+------+------+----------+------+----------------+
|  3 | Amay |   22 | 42000.00 | pune | amay@gmail.com |
+----+------+------+----------+------+----------------+
1 row in set (0.00 sec)

mysql> select*from customer where city  NOT IN ('beed');
+----+--------+------+----------+-----------+------------------+
| ID | NAME   | AGE  | BALANCE  | CITY      | EMAIL            |
+----+--------+------+----------+-----------+------------------+
|  3 | Amay   |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar   |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
|  5 | mahesh |   30 | 47000.00 | mumbai    | mahesh@gmail.com |
+----+--------+------+----------+-----------+------------------+
3 rows in set (0.00 sec)

mysql> select*from customer where balance between 20000 AND 60000;
+----+---------+------+----------+-----------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL            |
+----+---------+------+----------+-----------+------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com   |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com |
+----+---------+------+----------+-----------+------------------+
5 rows in set (0.01 sec)

mysql> select*from customer where balance between 20000 OR 60000;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'OR 60000' at line 1
mysql> select*from customer where balance NOT between 20000 AND 60000;
Empty set (0.00 sec)

mysql> select*from Customer where name LIKE '%R';
+----+------+------+----------+-----------+----------------+
| ID | NAME | AGE  | BALANCE  | CITY      | EMAIL          |
+----+------+------+----------+-----------+----------------+
|  4 | amar |   21 | 41000.00 | Chinchwad | amar@gmail.com |
+----+------+------+----------+-----------+----------------+
1 row in set (0.00 sec)

mysql> select * from customer where email is null;
Empty set (0.00 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(1,'ASHVINI',23,'67000','ashini@gmail.com');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(5,'ASHVINI',23,'67000','ashini@gmail.com');
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(5,'ASHVINI',23,'67000','Nashik','ashini@gmail.com');
ERROR 1062 (23000): Duplicate entry '5' for key 'customer.PRIMARY'
mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(6,'ASHVINI',23,'67000','Nashik','ashini@gmail.com');
Query OK, 1 row affected (0.01 sec)

mysql> select*from Customer;
+----+---------+------+----------+-----------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL            |
+----+---------+------+----------+-----------+------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com   |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashini@gmail.com |
+----+---------+------+----------+-----------+------------------+
6 rows in set (0.00 sec)

mysql> update Customer set Email ashvini@gmail.com where id=6;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ashvini@gmail.com where id=6' at line 1
mysql> update Customer set Email 'ashvini@gmail.com' where id=6;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''ashvini@gmail.com' where id=6' at line 1
mysql> update Customer set Email ='ashvini@gmail.com' where id=6;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select*from customer;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
+----+---------+------+----------+-----------+-------------------+
6 rows in set (0.00 sec)

mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(6,'ASHVINI',23,'67000','Nashik',NULL);
ERROR 1062 (23000): Duplicate entry '6' for key 'customer.PRIMARY'
mysql> INSERT INTO CUSTOMER (ID,NAME,AGE,BALANCE,CITY,EMAIL)VALUES(7,'ASHVINI',23,'67000','Nashik',NULL);
Query OK, 1 row affected (0.01 sec)

mysql> SELECT*FROM CUSTOMER;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
|  7 | ASHVINI |   23 | 67000.00 | Nashik    | NULL              |
+----+---------+------+----------+-----------+-------------------+
7 rows in set (0.00 sec)

mysql> UPDATE CUSTOMER SET EMAIL=NULL ,NAME='XYZ' WHERE ID=7;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
|  7 | XYZ     |   23 | 67000.00 | Nashik    | NULL              |
+----+---------+------+----------+-----------+-------------------+
7 rows in set (0.00 sec)

mysql> UPDATE CUSTOMER SET AGE=18,BALANCE=20000,CITY='GOA',NULL WHERE ID=7;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'NULL WHERE ID=7' at line 1
mysql> UPDATE CUSTOMER SET AGE=18,BALANCE=20000,CITY='GOA' WHERE ID=7;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
|  7 | XYZ     |   18 | 20000.00 | GOA       | NULL              |
+----+---------+------+----------+-----------+-------------------+
7 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE EMAIL IS NOT NULL;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
+----+---------+------+----------+-----------+-------------------+
6 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY IN ('PUNE') AND BALANCE >30000;
+----+------+------+----------+------+----------------+
| ID | NAME | AGE  | BALANCE  | CITY | EMAIL          |
+----+------+------+----------+------+----------------+
|  3 | Amay |   22 | 42000.00 | pune | amay@gmail.com |
+----+------+------+----------+------+----------------+
1 row in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY IN ('PUNE') AND BALANCE >=30000;
+----+------+------+----------+------+----------------+
| ID | NAME | AGE  | BALANCE  | CITY | EMAIL          |
+----+------+------+----------+------+----------------+
|  3 | Amay |   22 | 42000.00 | pune | amay@gmail.com |
+----+------+------+----------+------+----------------+
1 row in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY IN ('PUNE') OR BALANCE >=30000;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
+----+---------+------+----------+-----------+-------------------+
5 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY IN 'PUNE' OR CITY IN 'DELHI';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''PUNE' OR CITY IN 'DELHI'' at line 1
mysql> SELECT*FROM CUSTOMER WHERE CITY IN ('PUNE') OR CITY IN ('DELHI');
+----+------+------+----------+------+----------------+
| ID | NAME | AGE  | BALANCE  | CITY | EMAIL          |
+----+------+------+----------+------+----------------+
|  3 | Amay |   22 | 42000.00 | pune | amay@gmail.com |
+----+------+------+----------+------+----------------+
1 row in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY NOT IN('PUNE');
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
|  7 | XYZ     |   18 | 20000.00 | GOA       | NULL              |
+----+---------+------+----------+-----------+-------------------+
6 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY NOT IN('BEED');
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
|  7 | XYZ     |   18 | 20000.00 | GOA       | NULL              |
+----+---------+------+----------+-----------+-------------------+
5 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE CITY NOT ('BEED');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '('BEED')' at line 1
mysql> SELECT*FROM CUSTOMER WHERE CITY NOT IN ('BEED');
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
|  7 | XYZ     |   18 | 20000.00 | GOA       | NULL              |
+----+---------+------+----------+-----------+-------------------+
5 rows in set (0.00 sec)

mysql> SELECT *FROM CUSTOMER LIMIT 1 OFFSET 3;
+----+------+------+----------+-----------+----------------+
| ID | NAME | AGE  | BALANCE  | CITY      | EMAIL          |
+----+------+------+----------+-----------+----------------+
|  4 | amar |   21 | 41000.00 | Chinchwad | amar@gmail.com |
+----+------+------+----------+-----------+----------------+
1 row in set (0.00 sec)

mysql> SELECT *FROM CUSTOMER LIMIT 0 OFFSET 3;
Empty set (0.00 sec)

mysql> SELECT *FROM CUSTOMER LIMIT 3 OFFSET 1;
+----+---------+------+----------+-----------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL            |
+----+---------+------+----------+-----------+------------------+
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
+----+---------+------+----------+-----------+------------------+
3 rows in set (0.00 sec)

mysql> SELECT *FROM CUSTOMER LIMIT 3 OFFSET 0;
+----+---------+------+----------+------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY | EMAIL            |
+----+---------+------+----------+------+------------------+
|  1 | AJAY    |   21 | 25000.00 | BEED | ajay@gmail.com   |
|  2 | SAKSHII |   20 | 45000.00 | BEED | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune | amay@gmail.com   |
+----+---------+------+----------+------+------------------+
3 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER LIMIT 4 OFFSET 1;
+----+---------+------+----------+-----------+------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL            |
+----+---------+------+----------+-----------+------------------+
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com   |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com   |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com |
+----+---------+------+----------+-----------+------------------+
4 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER LIMIT 4 OFFSET 4;
+----+---------+------+----------+--------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY   | EMAIL             |
+----+---------+------+----------+--------+-------------------+
|  5 | mahesh  |   30 | 47000.00 | mumbai | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik | ashvini@gmail.com |
|  7 | XYZ     |   18 | 20000.00 | GOA    | NULL              |
+----+---------+------+----------+--------+-------------------+
3 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER LIMIT 3 OFFSET 3;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
+----+---------+------+----------+-----------+-------------------+
3 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER LIMIT 3 OFFSET 3;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
+----+---------+------+----------+-----------+-------------------+
3 rows in set (0.00 sec)

mysql> SELECT*FROM CUSTOMER WHERE ORDER BY BALANCE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ORDER BY BALANCE' at line 1
mysql> SELECT*FROM CUSTOMER WHERE ORDER BY ASC BALANCE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ORDER BY ASC BALANCE' at line 1
mysql> SELECT*FROM CUSTOMER WHERE ORDER BY ASCENDING BALANCE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ORDER BY ASCENDING BALANCE' at line 1
mysql> SELECT*FROM CUSTOMER WHERE  BALANCE ORDER BY ASCENDING;
ERROR 1054 (42S22): Unknown column 'ASCENDING' in 'order clause'
mysql>
mysql> SELECT*FROM CUSTOMER WHERE  BALANCE ORDER BY ASC;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ASC' at line 1
mysql> SELECT*FROM CUSTOMER  ORDER BY WHERE BALANCE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE BALANCE' at line 1
mysql> SELECT*FROM CUSTOMER  ORDER BY WHERE BALANCE ASC;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE BALANCE ASC' at line 1
mysql> SELECT*FROM CUSTOMER  ORDER BY BALANCE ASC;
+----+---------+------+----------+-----------+-------------------+
| ID | NAME    | AGE  | BALANCE  | CITY      | EMAIL             |
+----+---------+------+----------+-----------+-------------------+
|  7 | XYZ     |   18 | 20000.00 | GOA       | NULL              |
|  1 | AJAY    |   21 | 25000.00 | BEED      | ajay@gmail.com    |
|  4 | amar    |   21 | 41000.00 | Chinchwad | amar@gmail.com    |
|  3 | Amay    |   22 | 42000.00 | pune      | amay@gmail.com    |
|  2 | SAKSHII |   20 | 45000.00 | BEED      | sakshi@gmail.com  |
|  5 | mahesh  |   30 | 47000.00 | mumbai    | mahesh@gmail.com  |
|  6 | ASHVINI |   23 | 67000.00 | Nashik    | ashvini@gmail.com |
+----+---------+------+----------+-----------+-------------------+
7 rows in set (0.00 sec)



mysql> CREATE TABLE PRODUCT1(
    -> P_ID INT PRIMARY KEY,
    -> P_NAME VARCHAR(20),
    -> PRICE DECIMAL(10,2),
    -> QUANTITY INT,
    -> DISCOUNT DECIMAL (5,2),
    -> P_CODE VARCHAR(10),
    -> DESCRIPTION TEXT,
    -> LAUNCH_DATE DATE,
    -> LAUNCH_TIME TIME,
    -> IS_AVAILABLE BOOLEAN
    ->
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> select*from Product1;
Empty set (0.00 sec)

mysql> desc product;
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| P_ID         | int           | NO   | PRI | NULL    |       |
| P_NAME       | varchar(20)   | YES  |     | NULL    |       |
| PRICE        | decimal(10,2) | YES  |     | NULL    |       |
| QUANTITY     | int           | YES  |     | NULL    |       |
| DISCOUNT     | decimal(5,2)  | YES  |     | NULL    |       |
| P_CODE       | varchar(10)   | YES  |     | NULL    |       |
| DESCRIPTION  | text          | YES  |     | NULL    |       |
| LAUNCH_DATE  | date          | YES  |     | NULL    |       |
| LAUNCH_TIME  | time          | YES  |     | NULL    |       |
| IS_AVAILABLE | tinyint(1)    | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
10 rows in set (0.00 sec)

mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(101,'MOTOROLA',45000.00,1,15.00,009,'PRODUCT IS GOOD','2026-09-24','12:45:55',TRUE);
Query OK, 1 row affected (0.01 sec)

mysql> select*from Product1;
+------+----------+----------+----------+----------+--------+-----------------+-------------+-------------+--------------+
| P_ID | P_NAME   | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION     | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+----------+----------+----------+----------+--------+-----------------+-------------+-------------+--------------+
|  101 | MOTOROLA | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD | 2026-09-24  | 12:45:55    |            1 |
+------+----------+----------+----------+----------+--------+-----------------+-------------+-------------+--------------+
1 row in set (0.00 sec)

mysql> desc product;
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| P_ID         | int           | NO   | PRI | NULL    |       |
| P_NAME       | varchar(20)   | YES  |     | NULL    |       |
| PRICE        | decimal(10,2) | YES  |     | NULL    |       |
| QUANTITY     | int           | YES  |     | NULL    |       |
| DISCOUNT     | decimal(5,2)  | YES  |     | NULL    |       |
| P_CODE       | varchar(10)   | YES  |     | NULL    |       |
| DESCRIPTION  | text          | YES  |     | NULL    |       |
| LAUNCH_DATE  | date          | YES  |     | NULL    |       |
| LAUNCH_TIME  | time          | YES  |     | NULL    |       |
| IS_AVAILABLE | tinyint(1)    | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
10 rows in set (0.00 sec)

mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(102,'MOTOROLA EDGE',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CUR_DATE(),CURTIME(),TRUE);
ERROR 1305 (42000): FUNCTION product.CUR_DATE does not exist
mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(102,'MOTOROLA EDGE',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CURDATE(),CURTIME(),TRUE);
Query OK, 1 row affected (0.01 sec)

mysql> desc product;
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| P_ID         | int           | NO   | PRI | NULL    |       |
| P_NAME       | varchar(20)   | YES  |     | NULL    |       |
| PRICE        | decimal(10,2) | YES  |     | NULL    |       |
| QUANTITY     | int           | YES  |     | NULL    |       |
| DISCOUNT     | decimal(5,2)  | YES  |     | NULL    |       |
| P_CODE       | varchar(10)   | YES  |     | NULL    |       |
| DESCRIPTION  | text          | YES  |     | NULL    |       |
| LAUNCH_DATE  | date          | YES  |     | NULL    |       |
| LAUNCH_TIME  | time          | YES  |     | NULL    |       |
| IS_AVAILABLE | tinyint(1)    | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
10 rows in set (0.00 sec)

mysql> select*from Product1;
+------+---------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME        | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+---------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA      | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2026-09-24  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
+------+---------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
2 rows in set (0.00 sec)

mysql> SELECT NOW();
+---------------------+
| NOW()               |
+---------------------+
| 2026-09-24 04:01:55 |
+---------------------+
1 row in set (0.00 sec)

mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(103,'MOTOROLA FUSION',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CUR_DATE(),CURTIME(),TRUE);
ERROR 1305 (42000): FUNCTION product.CUR_DATE does not exist
mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(103,'MOTOROLA FUSION',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CURDATE(),CURTIME(),TRUE);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(NULL,'MOTOROLA FUSION',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CURDATE(),CURTIME(),TRUE);
ERROR 1048 (23000): Column 'P_ID' cannot be null
mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(NULL,'MOTOROLA FUSION',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CURDATE(),CURTIME(),NULL);
ERROR 1048 (23000): Column 'P_ID' cannot be null
mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(104,'MOTOROLA FUSION',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CURDATE(),CURTIME(),NULL);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO PRODUCT1(P_ID,P_NAME,PRICE,QUANTITY,DISCOUNT,P_CODE,DESCRIPTION,LAUNCH_DATE,LAUNCH_TIME,IS_AVAILABLE)VALUES(105,'MOTOROLA FUSION',55000.00,2,20.00,008,'PRODUCT IS EXPENSIVE',CURDATE(),NULL,FALSE);
Query OK, 1 row affected (0.01 sec)

mysql> select*from Product1;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2026-09-24  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
5 rows in set (0.00 sec)

mysql> SELECT PRODUCT WHERE PRICE>50000;
ERROR 1054 (42S22): Unknown column 'PRODUCT' in 'field list'
mysql> SELECT * FROM PRODUCT WHERE PRICE>50000;
Empty set (0.00 sec)

mysql> SELECT * FROM PRODUCT1 WHERE PRICE>50000;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
4 rows in set (0.00 sec)

mysql> SELECT PRODUCT1 WHERE P_NAME,PRICE,DISCOUNT=20.00;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',PRICE,DISCOUNT=20.00' at line 1
mysql> SELECT*FROM PRODUCT1 WHERE P_NAME,PRICE,DISCOUNT=20.00;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',PRICE,DISCOUNT=20.00' at line 1
mysql> SELECT*FROM PRODUCT1 WHERE P_NAME AND PRICE AND DISCOUNT=20.00;
Empty set, 4 warnings (0.01 sec)

mysql> SELECT*FROM PRODUCT1 WHERE P_NAME AND PRICE AND DISCOUNT>=20.00;
Empty set, 5 warnings (0.00 sec)

mysql> SELECT P_NAME,PRICE,DISCOUNT FROM PRODUCT1 WHERE DISCOUNT>=20.00;
+-----------------+----------+----------+
| P_NAME          | PRICE    | DISCOUNT |
+-----------------+----------+----------+
| MOTOROLA EDGE   | 55000.00 |    20.00 |
| MOTOROLA FUSION | 55000.00 |    20.00 |
| MOTOROLA FUSION | 55000.00 |    20.00 |
| MOTOROLA FUSION | 55000.00 |    20.00 |
+-----------------+----------+----------+
4 rows in set (0.00 sec)

mysql> select*from Product1;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2026-09-24  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
5 rows in set (0.00 sec)

mysql> select*from product1 where quantity>=1;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2026-09-24  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
5 rows in set (0.00 sec)

mysql> select*from product1 where quantity>1;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
4 rows in set (0.00 sec)

mysql> select*from product1 where launch_date='2026-09-24';
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2026-09-24  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
5 rows in set (0.01 sec)

mysql>
mysql> select*from product1 where launch_date!='2026-09-24';
Empty set (0.00 sec)

mysql> update product1 set launch_date='2025-04-12'where p_id=101;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select*from product1;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2025-04-12  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
5 rows in set (0.00 sec)

mysql> select*from product1 where launch_date='2026-09-24';
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
|  105 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | NULL        |            0 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
4 rows in set (0.00 sec)

mysql> select*from product1 where launch_time>'04:10:00';
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2025-04-12  | 12:45:55    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
|  104 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:13:23    |         NULL |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
3 rows in set (0.00 sec)

mysql> select*from product1 where is_available=true;
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
| P_ID | P_NAME          | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION          | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
|  101 | MOTOROLA        | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD      | 2025-04-12  | 12:45:55    |            1 |
|  102 | MOTOROLA EDGE   | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:01:14    |            1 |
|  103 | MOTOROLA FUSION | 55000.00 |        2 |    20.00 | 8      | PRODUCT IS EXPENSIVE | 2026-09-24  | 04:12:38    |            1 |
+------+-----------------+----------+----------+----------+--------+----------------------+-------------+-------------+--------------+
3 rows in set (0.00 sec)

mysql> SELECT*FROM PRODUCT1 WHERE P_NAME LIKE '%MOTOROLA';
+------+----------+----------+----------+----------+--------+-----------------+-------------+-------------+--------------+
| P_ID | P_NAME   | PRICE    | QUANTITY | DISCOUNT | P_CODE | DESCRIPTION     | LAUNCH_DATE | LAUNCH_TIME | IS_AVAILABLE |
+------+----------+----------+----------+----------+--------+-----------------+-------------+-------------+--------------+
|  101 | MOTOROLA | 45000.00 |        1 |    15.00 | 9      | PRODUCT IS GOOD | 2025-04-12  | 12:45:55    |            1 |
+------+----------+----------+----------+----------+--------+-----------------+-------------+-------------+--------------+
1 row in set (0.00 sec)
mysql> SELECT*FROM CUSTOMER  GROUP BY BALANCE ASC;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ASC' at line 1
mysql> SELECT*FROM CUSTOMER  GROUP BY BALANCE ;
ERROR 1055 (42000): Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'bank.CUSTOMER.ID' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
mysql>



Microsoft Windows [Version 10.0.19045.6466]
(c) Microsoft Corporation. All rights reserved.

C:\Users\Ajay Popat Agwan>"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p
Enter password: ****
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 142
Server version: 8.0.46 MySQL Community Server - GPL

Copyright (c) 2000, 2026, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+------------------------+
| Database               |
+------------------------+
| bank                   |
| company                |
| company_db             |
| information_schema     |
| java_practice          |
| liabrary               |
| mysql                  |
| performance_schema     |
| product                |
| student_skill_exchange |
| sys                    |
+------------------------+
11 rows in set (0.00 sec)

mysql> use product;
Database changed
mysql> show tables;
+-------------------+
| Tables_in_product |
+-------------------+
| customer          |
| department        |
| emp               |
| employee          |
| product           |
| product1          |
| student           |
+-------------------+
7 rows in set (0.00 sec)

mysql> select*from customer;
Empty set (0.00 sec)

mysql> desc customer;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(40)   | YES  |     | NULL    |       |
| CITY    | varchar(30)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> insert into (c_id,c_name,city,balance)values(101,'ganesh','pune',55000);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(c_id,c_name,city,balance)values(101,'ganesh','pune',55000)' at line 1
mysql> insert into customer(c_id,c_name,city,balance)values(101,'ganesh','pune',55000);
Query OK, 1 row affected (0.01 sec)

mysql> select*from customer;
+------+--------+------+----------+
| C_ID | C_NAME | CITY | BALANCE  |
+------+--------+------+----------+
|  101 | ganesh | pune | 55000.00 |
+------+--------+------+----------+
1 row in set (0.00 sec)

mysql> insert into customer(c_id,c_name,city,balance)values(102,'mahesh','pcmc',15000);
Query OK, 1 row affected (0.01 sec)

mysql> truncate table customer;
Query OK, 0 rows affected (0.05 sec)

mysql> select*from customer;
Empty set (0.00 sec)

mysql> alter table customer modify c_id int auto_increment;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc customer;
+---------+---------------+------+-----+---------+----------------+
| Field   | Type          | Null | Key | Default | Extra          |
+---------+---------------+------+-----+---------+----------------+
| c_id    | int           | NO   | PRI | NULL    | auto_increment |
| C_NAME  | varchar(40)   | YES  |     | NULL    |                |
| CITY    | varchar(30)   | YES  |     | NULL    |                |
| BALANCE | decimal(10,2) | YES  |     | NULL    |                |
+---------+---------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> insert into customer(c_name,city,balance)values('Ganesh','Beed',6000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(c_name,city,balance)values('Ajay','Pune',70000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(c_name,city,balance)values('Snehal','nsk',80000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(c_name,city,balance)values('Amarnath','Pune',90000);
Query OK, 1 row affected (0.02 sec)

mysql> insert into customer(c_name,city,balance)values('Ajit','pcmc',7000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(c_name,city,balance)values('Shiv','Karad',700);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(c_name,city,balance)values('MAnagalam','Satara',30000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(c_name,city,balance)values('munni','goa',7000);
Query OK, 1 row affected (0.01 sec)

mysql> select*from customer;
+------+-----------+--------+----------+
| c_id | C_NAME    | CITY   | BALANCE  |
+------+-----------+--------+----------+
|    1 | Ganesh    | Beed   |  6000.00 |
|    2 | Ajay      | Pune   | 70000.00 |
|    3 | Snehal    | nsk    | 80000.00 |
|    4 | Amarnath  | Pune   | 90000.00 |
|    5 | Ajit      | pcmc   |  7000.00 |
|    6 | Shiv      | Karad  |   700.00 |
|    7 | MAnagalam | Satara | 30000.00 |
|    8 | munni     | goa    |  7000.00 |
+------+-----------+--------+----------+
8 rows in set (0.00 sec)

mysql> select*from emp;
Empty set (0.00 sec)

mysql> desc emp;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| E_ID   | int          | NO   | PRI | NULL    |       |
| E_NAME | varchar(30)  | YES  |     | NULL    |       |
| AGE    | int          | YES  |     | NULL    |       |
| SALARY | decimal(8,2) | YES  |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> desc employee;
+--------+---------------+------+-----+---------+-------+
| Field  | Type          | Null | Key | Default | Extra |
+--------+---------------+------+-----+---------+-------+
| E_ID   | int           | NO   | PRI | NULL    |       |
| E_NAME | varchar(44)   | NO   | UNI | NULL    |       |
| AGE    | int           | YES  |     | NULL    |       |
| SALARY | decimal(10,2) | YES  |     | NULL    |       |
| D_ID   | int           | YES  | MUL | NULL    |       |
| EMAIL  | varchar(55)   | YES  |     | NULL    |       |
+--------+---------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> insert into emp(e_id,e_name,age,salary)values(12,'Dagdoba',55,4000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into emp(e_id,e_name,age,salary)values(11,'Dhondoba',57,4500);
Query OK, 1 row affected (0.01 sec)

mysql> insert into emp(e_id,e_name,age,salary)values(13,'Gyandev',59,3500);
Query OK, 1 row affected (0.01 sec)

mysql> select*from emp;
+------+----------+------+---------+
| E_ID | E_NAME   | AGE  | SALARY  |
+------+----------+------+---------+
|   11 | Dhondoba |   57 | 4500.00 |
|   12 | Dagdoba  |   55 | 4000.00 |
|   13 | Gyandev  |   59 | 3500.00 |
+------+----------+------+---------+
3 rows in set (0.00 sec)

mysql> alter table emp modify e_id int auto_increment;
Query OK, 3 rows affected (0.07 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> insert into emp(e_name,age,salary)values('Ganpat',60,3500);
Query OK, 1 row affected (0.01 sec)

mysql> select*from emp;
+------+----------+------+---------+
| e_id | E_NAME   | AGE  | SALARY  |
+------+----------+------+---------+
|   11 | Dhondoba |   57 | 4500.00 |
|   12 | Dagdoba  |   55 | 4000.00 |
|   13 | Gyandev  |   59 | 3500.00 |
|   14 | Ganpat   |   60 | 3500.00 |
+------+----------+------+---------+
4 rows in set (0.00 sec)

mysql> show tables;
+-------------------+
| Tables_in_product |
+-------------------+
| customer          |
| department        |
| emp               |
| employee          |
| product           |
| product1          |
| student           |
+-------------------+
7 rows in set (0.00 sec)

mysql> select*from department;
Empty set (0.00 sec)

mysql> desc department;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| D_ID   | int         | NO   | PRI | NULL    |       |
| D_NAME | varchar(40) | NO   |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> insert into department(d_id,d_name)values(456,'it');
Query OK, 1 row affected (0.01 sec)

mysql> insert into department(d_id,d_name)values(45,'cs');
Query OK, 1 row affected (0.01 sec)

mysql> alter table department d_id int auto_increment;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'd_id int auto_increment' at line 1
mysql> alter table department modify d_id int auto_increment;
ERROR 1833 (HY000): Cannot change column 'D_ID': used in a foreign key constraint 'employee_ibfk_1' of table 'product.employee'
mysql> select*from department;
+------+--------+
| D_ID | D_NAME |
+------+--------+
|   45 | cs     |
|  456 | it     |
+------+--------+
2 rows in set (0.00 sec)

mysql> insert into department(d_id,d_name)values(457,'mechanicle');
Query OK, 1 row affected (0.01 sec)

mysql> insert into department(d_id,d_name)values(454,'AI');
Query OK, 1 row affected (0.01 sec)

mysql> select*from department;
+------+------------+
| D_ID | D_NAME     |
+------+------------+
|   45 | cs         |
|  454 | AI         |
|  456 | it         |
|  457 | mechanicle |
+------+------------+
4 rows in set (0.00 sec)

mysql> select*from employee;
Empty set (0.00 sec)

mysql> select distinct city from customer;
+--------+
| city   |
+--------+
| Beed   |
| Pune   |
| nsk    |
| pcmc   |
| Karad  |
| Satara |
| goa    |
+--------+
7 rows in set (0.00 sec)

mysql> alter table customer rename city to address;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'to address' at line 1
mysql> alter table customer rename column  city to address;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> selcet*from customer;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'selcet*from customer' at line 1
mysql> select*from customer;
+------+-----------+---------+----------+
| c_id | C_NAME    | address | BALANCE  |
+------+-----------+---------+----------+
|    1 | Ganesh    | Beed    |  6000.00 |
|    2 | Ajay      | Pune    | 70000.00 |
|    3 | Snehal    | nsk     | 80000.00 |
|    4 | Amarnath  | Pune    | 90000.00 |
|    5 | Ajit      | pcmc    |  7000.00 |
|    6 | Shiv      | Karad   |   700.00 |
|    7 | MAnagalam | Satara  | 30000.00 |
|    8 | munni     | goa     |  7000.00 |
+------+-----------+---------+----------+
8 rows in set (0.00 sec)

mysql> alter table customer add column email varchar(45);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> selcet*from customer;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'selcet*from customer' at line 1
mysql> select*from employee;
Empty set (0.00 sec)

mysql> select*from customer;
+------+-----------+---------+----------+-------+
| c_id | C_NAME    | address | BALANCE  | email |
+------+-----------+---------+----------+-------+
|    1 | Ganesh    | Beed    |  6000.00 | NULL  |
|    2 | Ajay      | Pune    | 70000.00 | NULL  |
|    3 | Snehal    | nsk     | 80000.00 | NULL  |
|    4 | Amarnath  | Pune    | 90000.00 | NULL  |
|    5 | Ajit      | pcmc    |  7000.00 | NULL  |
|    6 | Shiv      | Karad   |   700.00 | NULL  |
|    7 | MAnagalam | Satara  | 30000.00 | NULL  |
|    8 | munni     | goa     |  7000.00 | NULL  |
+------+-----------+---------+----------+-------+
8 rows in set (0.00 sec)

mysql> alter table customer add mo_No after c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'after c_name' at line 1
mysql> alter table customer add mo_No first c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'first c_name' at line 1
mysql> alter table customer add mo_No int first c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'c_name' at line 1
mysql> alter table customer add  column mo_No int  first c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'c_name' at line 1
mysql> alter table customer add  column mo_No int  first c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'c_name' at line 1
mysql>
mysql>
mysql>
mysql>
mysql>
mysql>
mysql>
mysql>
mysql>
mysql>
mysql>
mysql> alter table customer add column  ph_no bigint after c_id;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select*from customer;
+------+-------+-----------+---------+----------+-------+
| c_id | ph_no | C_NAME    | address | BALANCE  | email |
+------+-------+-----------+---------+----------+-------+
|    1 |  NULL | Ganesh    | Beed    |  6000.00 | NULL  |
|    2 |  NULL | Ajay      | Pune    | 70000.00 | NULL  |
|    3 |  NULL | Snehal    | nsk     | 80000.00 | NULL  |
|    4 |  NULL | Amarnath  | Pune    | 90000.00 | NULL  |
|    5 |  NULL | Ajit      | pcmc    |  7000.00 | NULL  |
|    6 |  NULL | Shiv      | Karad   |   700.00 | NULL  |
|    7 |  NULL | MAnagalam | Satara  | 30000.00 | NULL  |
|    8 |  NULL | munni     | goa     |  7000.00 | NULL  |
+------+-------+-----------+---------+----------+-------+
8 rows in set (0.00 sec)

mysql> insert into customer(ph_no)values(3456789067);
Query OK, 1 row affected (0.01 sec)

mysql> select*from customer;
+------+------------+-----------+---------+----------+-------+
| c_id | ph_no      | C_NAME    | address | BALANCE  | email |
+------+------------+-----------+---------+----------+-------+
|    1 |       NULL | Ganesh    | Beed    |  6000.00 | NULL  |
|    2 |       NULL | Ajay      | Pune    | 70000.00 | NULL  |
|    3 |       NULL | Snehal    | nsk     | 80000.00 | NULL  |
|    4 |       NULL | Amarnath  | Pune    | 90000.00 | NULL  |
|    5 |       NULL | Ajit      | pcmc    |  7000.00 | NULL  |
|    6 |       NULL | Shiv      | Karad   |   700.00 | NULL  |
|    7 |       NULL | MAnagalam | Satara  | 30000.00 | NULL  |
|    8 |       NULL | munni     | goa     |  7000.00 | NULL  |
|    9 | 3456789067 | NULL      | NULL    |     NULL | NULL  |
+------+------------+-----------+---------+----------+-------+
9 rows in set (0.00 sec)

mysql> insert into customer(ph_no)values(3456789054);
Query OK, 1 row affected (0.01 sec)

mysql> select*from customer;
+------+------------+-----------+---------+----------+-------+
| c_id | ph_no      | C_NAME    | address | BALANCE  | email |
+------+------------+-----------+---------+----------+-------+
|    1 |       NULL | Ganesh    | Beed    |  6000.00 | NULL  |
|    2 |       NULL | Ajay      | Pune    | 70000.00 | NULL  |
|    3 |       NULL | Snehal    | nsk     | 80000.00 | NULL  |
|    4 |       NULL | Amarnath  | Pune    | 90000.00 | NULL  |
|    5 |       NULL | Ajit      | pcmc    |  7000.00 | NULL  |
|    6 |       NULL | Shiv      | Karad   |   700.00 | NULL  |
|    7 |       NULL | MAnagalam | Satara  | 30000.00 | NULL  |
|    8 |       NULL | munni     | goa     |  7000.00 | NULL  |
|    9 | 3456789067 | NULL      | NULL    |     NULL | NULL  |
|   10 | 3456789054 | NULL      | NULL    |     NULL | NULL  |
+------+------------+-----------+---------+----------+-------+
10 rows in set (0.00 sec)

mysql> insert into customer(ph_no)values(9876543254);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(ph_no)values(87654321654);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(ph_no)values(8765432345);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(ph_no)values(9876543456);
Query OK, 1 row affected (0.01 sec)

mysql> insert into customer(ph_no)values(87654323456789);
Query OK, 1 row affected (0.01 sec)

mysql> select*from customer;
+------+----------------+-----------+---------+----------+-------+
| c_id | ph_no          | C_NAME    | address | BALANCE  | email |
+------+----------------+-----------+---------+----------+-------+
|    1 |           NULL | Ganesh    | Beed    |  6000.00 | NULL  |
|    2 |           NULL | Ajay      | Pune    | 70000.00 | NULL  |
|    3 |           NULL | Snehal    | nsk     | 80000.00 | NULL  |
|    4 |           NULL | Amarnath  | Pune    | 90000.00 | NULL  |
|    5 |           NULL | Ajit      | pcmc    |  7000.00 | NULL  |
|    6 |           NULL | Shiv      | Karad   |   700.00 | NULL  |
|    7 |           NULL | MAnagalam | Satara  | 30000.00 | NULL  |
|    8 |           NULL | munni     | goa     |  7000.00 | NULL  |
|    9 |     3456789067 | NULL      | NULL    |     NULL | NULL  |
|   10 |     3456789054 | NULL      | NULL    |     NULL | NULL  |
|   11 |     9876543254 | NULL      | NULL    |     NULL | NULL  |
|   12 |    87654321654 | NULL      | NULL    |     NULL | NULL  |
|   13 |     8765432345 | NULL      | NULL    |     NULL | NULL  |
|   14 |     9876543456 | NULL      | NULL    |     NULL | NULL  |
|   15 | 87654323456789 | NULL      | NULL    |     NULL | NULL  |
+------+----------------+-----------+---------+----------+-------+
15 rows in set (0.00 sec)

mysql> alter table customer add column ph_no int  after c_name;
ERROR 1060 (42S21): Duplicate column name 'ph_no'
mysql> alter table customer add column gender char  after c_name;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select*from customer;
+------+----------------+-----------+--------+---------+----------+-------+
| c_id | ph_no          | C_NAME    | gender | address | BALANCE  | email |
+------+----------------+-----------+--------+---------+----------+-------+
|    1 |           NULL | Ganesh    | NULL   | Beed    |  6000.00 | NULL  |
|    2 |           NULL | Ajay      | NULL   | Pune    | 70000.00 | NULL  |
|    3 |           NULL | Snehal    | NULL   | nsk     | 80000.00 | NULL  |
|    4 |           NULL | Amarnath  | NULL   | Pune    | 90000.00 | NULL  |
|    5 |           NULL | Ajit      | NULL   | pcmc    |  7000.00 | NULL  |
|    6 |           NULL | Shiv      | NULL   | Karad   |   700.00 | NULL  |
|    7 |           NULL | MAnagalam | NULL   | Satara  | 30000.00 | NULL  |
|    8 |           NULL | munni     | NULL   | goa     |  7000.00 | NULL  |
|    9 |     3456789067 | NULL      | NULL   | NULL    |     NULL | NULL  |
|   10 |     3456789054 | NULL      | NULL   | NULL    |     NULL | NULL  |
|   11 |     9876543254 | NULL      | NULL   | NULL    |     NULL | NULL  |
|   12 |    87654321654 | NULL      | NULL   | NULL    |     NULL | NULL  |
|   13 |     8765432345 | NULL      | NULL   | NULL    |     NULL | NULL  |
|   14 |     9876543456 | NULL      | NULL   | NULL    |     NULL | NULL  |
|   15 | 87654323456789 | NULL      | NULL   | NULL    |     NULL | NULL  |
+------+----------------+-----------+--------+---------+----------+-------+
15 rows in set (0.00 sec)

mysql> alter table customer modify ph_no int after c_name;
ERROR 1264 (22003): Out of range value for column 'ph_no' at row 9
mysql> alter table customer modify column ph_no int c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'c_name' at line 1
mysql> alter table customer modify ph_no  after c_name;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'after c_name' at line 1
mysql>
mysql>
mysql>
mysql>
mysql> ALTER TABLE CUSTOMER MODIFY PH_NO BIGINT AFTER C_NAME;
Query OK, 0 rows affected (0.13 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select*from customer;
+------+-----------+----------------+--------+---------+----------+-------+
| c_id | C_NAME    | PH_NO          | gender | address | BALANCE  | email |
+------+-----------+----------------+--------+---------+----------+-------+
|    1 | Ganesh    |           NULL | NULL   | Beed    |  6000.00 | NULL  |
|    2 | Ajay      |           NULL | NULL   | Pune    | 70000.00 | NULL  |
|    3 | Snehal    |           NULL | NULL   | nsk     | 80000.00 | NULL  |
|    4 | Amarnath  |           NULL | NULL   | Pune    | 90000.00 | NULL  |
|    5 | Ajit      |           NULL | NULL   | pcmc    |  7000.00 | NULL  |
|    6 | Shiv      |           NULL | NULL   | Karad   |   700.00 | NULL  |
|    7 | MAnagalam |           NULL | NULL   | Satara  | 30000.00 | NULL  |
|    8 | munni     |           NULL | NULL   | goa     |  7000.00 | NULL  |
|    9 | NULL      |     3456789067 | NULL   | NULL    |     NULL | NULL  |
|   10 | NULL      |     3456789054 | NULL   | NULL    |     NULL | NULL  |
|   11 | NULL      |     9876543254 | NULL   | NULL    |     NULL | NULL  |
|   12 | NULL      |    87654321654 | NULL   | NULL    |     NULL | NULL  |
|   13 | NULL      |     8765432345 | NULL   | NULL    |     NULL | NULL  |
|   14 | NULL      |     9876543456 | NULL   | NULL    |     NULL | NULL  |
|   15 | NULL      | 87654323456789 | NULL   | NULL    |     NULL | NULL  |
+------+-----------+----------------+--------+---------+----------+-------+
15 rows in set (0.01 sec)

mysql> ALTER TABLE CUSTOMER MODIFY EMAIL VARCHAR(20) FIRST C_ID;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'C_ID' at line 1
mysql> ALTER TABLE CUSTOMER MODIFY EMAIL VARCHAR(20) FIRST;
Query OK, 15 rows affected (0.07 sec)
Records: 15  Duplicates: 0  Warnings: 0

mysql> select*from customer;
+-------+------+-----------+----------------+--------+---------+----------+
| EMAIL | c_id | C_NAME    | PH_NO          | gender | address | BALANCE  |
+-------+------+-----------+----------------+--------+---------+----------+
| NULL  |    1 | Ganesh    |           NULL | NULL   | Beed    |  6000.00 |
| NULL  |    2 | Ajay      |           NULL | NULL   | Pune    | 70000.00 |
| NULL  |    3 | Snehal    |           NULL | NULL   | nsk     | 80000.00 |
| NULL  |    4 | Amarnath  |           NULL | NULL   | Pune    | 90000.00 |
| NULL  |    5 | Ajit      |           NULL | NULL   | pcmc    |  7000.00 |
| NULL  |    6 | Shiv      |           NULL | NULL   | Karad   |   700.00 |
| NULL  |    7 | MAnagalam |           NULL | NULL   | Satara  | 30000.00 |
| NULL  |    8 | munni     |           NULL | NULL   | goa     |  7000.00 |
| NULL  |    9 | NULL      |     3456789067 | NULL   | NULL    |     NULL |
| NULL  |   10 | NULL      |     3456789054 | NULL   | NULL    |     NULL |
| NULL  |   11 | NULL      |     9876543254 | NULL   | NULL    |     NULL |
| NULL  |   12 | NULL      |    87654321654 | NULL   | NULL    |     NULL |
| NULL  |   13 | NULL      |     8765432345 | NULL   | NULL    |     NULL |
| NULL  |   14 | NULL      |     9876543456 | NULL   | NULL    |     NULL |
| NULL  |   15 | NULL      | 87654323456789 | NULL   | NULL    |     NULL |
+-------+------+-----------+----------------+--------+---------+----------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER MODIFY EMAIL VARCHAR(20) AFTER C_ID;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select*from customer;
+------+-------+-----------+----------------+--------+---------+----------+
| c_id | EMAIL | C_NAME    | PH_NO          | gender | address | BALANCE  |
+------+-------+-----------+----------------+--------+---------+----------+
|    1 | NULL  | Ganesh    |           NULL | NULL   | Beed    |  6000.00 |
|    2 | NULL  | Ajay      |           NULL | NULL   | Pune    | 70000.00 |
|    3 | NULL  | Snehal    |           NULL | NULL   | nsk     | 80000.00 |
|    4 | NULL  | Amarnath  |           NULL | NULL   | Pune    | 90000.00 |
|    5 | NULL  | Ajit      |           NULL | NULL   | pcmc    |  7000.00 |
|    6 | NULL  | Shiv      |           NULL | NULL   | Karad   |   700.00 |
|    7 | NULL  | MAnagalam |           NULL | NULL   | Satara  | 30000.00 |
|    8 | NULL  | munni     |           NULL | NULL   | goa     |  7000.00 |
|    9 | NULL  | NULL      |     3456789067 | NULL   | NULL    |     NULL |
|   10 | NULL  | NULL      |     3456789054 | NULL   | NULL    |     NULL |
|   11 | NULL  | NULL      |     9876543254 | NULL   | NULL    |     NULL |
|   12 | NULL  | NULL      |    87654321654 | NULL   | NULL    |     NULL |
|   13 | NULL  | NULL      |     8765432345 | NULL   | NULL    |     NULL |
|   14 | NULL  | NULL      |     9876543456 | NULL   | NULL    |     NULL |
|   15 | NULL  | NULL      | 87654323456789 | NULL   | NULL    |     NULL |
+------+-------+-----------+----------------+--------+---------+----------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER MODIFY EMAIL VARCHAR(20) AFTER BALANCE;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select*from customer;
+------+-----------+----------------+--------+---------+----------+-------+
| c_id | C_NAME    | PH_NO          | gender | address | BALANCE  | EMAIL |
+------+-----------+----------------+--------+---------+----------+-------+
|    1 | Ganesh    |           NULL | NULL   | Beed    |  6000.00 | NULL  |
|    2 | Ajay      |           NULL | NULL   | Pune    | 70000.00 | NULL  |
|    3 | Snehal    |           NULL | NULL   | nsk     | 80000.00 | NULL  |
|    4 | Amarnath  |           NULL | NULL   | Pune    | 90000.00 | NULL  |
|    5 | Ajit      |           NULL | NULL   | pcmc    |  7000.00 | NULL  |
|    6 | Shiv      |           NULL | NULL   | Karad   |   700.00 | NULL  |
|    7 | MAnagalam |           NULL | NULL   | Satara  | 30000.00 | NULL  |
|    8 | munni     |           NULL | NULL   | goa     |  7000.00 | NULL  |
|    9 | NULL      |     3456789067 | NULL   | NULL    |     NULL | NULL  |
|   10 | NULL      |     3456789054 | NULL   | NULL    |     NULL | NULL  |
|   11 | NULL      |     9876543254 | NULL   | NULL    |     NULL | NULL  |
|   12 | NULL      |    87654321654 | NULL   | NULL    |     NULL | NULL  |
|   13 | NULL      |     8765432345 | NULL   | NULL    |     NULL | NULL  |
|   14 | NULL      |     9876543456 | NULL   | NULL    |     NULL | NULL  |
|   15 | NULL      | 87654323456789 | NULL   | NULL    |     NULL | NULL  |
+------+-----------+----------------+--------+---------+----------+-------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER DROP PRIMARY KEY;
ERROR 1075 (42000): Incorrect table definition; there can be only one auto column and it must be defined as a key
mysql> ALTER TABLE CUSTOMER DROP PRIMARY KEY(C_ID);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(C_ID)' at line 1
mysql> ALTER TABLE CUSTOMER DROP PRIMARY KEY;
ERROR 1075 (42000): Incorrect table definition; there can be only one auto column and it must be defined as a key
mysql> DESC CUSTOMER;
+---------+---------------+------+-----+---------+----------------+
| Field   | Type          | Null | Key | Default | Extra          |
+---------+---------------+------+-----+---------+----------------+
| c_id    | int           | NO   | PRI | NULL    | auto_increment |
| C_NAME  | varchar(40)   | YES  |     | NULL    |                |
| PH_NO   | bigint        | YES  |     | NULL    |                |
| gender  | char(1)       | YES  |     | NULL    |                |
| address | varchar(30)   | YES  |     | NULL    |                |
| BALANCE | decimal(10,2) | YES  |     | NULL    |                |
| EMAIL   | varchar(20)   | YES  |     | NULL    |                |
+---------+---------------+------+-----+---------+----------------+
7 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER DROP CONSTRAINT AUTO_INCREMENT;
ERROR 3940 (HY000): Constraint 'AUTO_INCREMENT' does not exist.
mysql> ALTER TABLE CUSTOMER DROP  AUTO_INCREMENT;
ERROR 1091 (42000): Can't DROP 'AUTO_INCREMENT'; check that column/key exists
mysql> ALTER TABLE CUSTOMER DROP PRIMARY KEY;
ERROR 1075 (42000): Incorrect table definition; there can be only one auto column and it must be defined as a key
mysql> ALTER TABLE CUSTOMER DROP PRIMARY KEY (C_ID);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(C_ID)' at line 1
mysql> ALTER TABLE CUSTOMER DROP CONSTRAINT AUTO_INCREMENT(C_ID);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(C_ID)' at line 1
mysql>
mysql>
mysql>
mysql>
mysql> ALTER TABLE CUSTOMER DROP AUTO_INCREMENT;
ERROR 1091 (42000): Can't DROP 'AUTO_INCREMENT'; check that column/key exists
mysql> SELECT*FROM CUSTOMER;
+------+-----------+----------------+--------+---------+----------+-------+
| c_id | C_NAME    | PH_NO          | gender | address | BALANCE  | EMAIL |
+------+-----------+----------------+--------+---------+----------+-------+
|    1 | Ganesh    |           NULL | NULL   | Beed    |  6000.00 | NULL  |
|    2 | Ajay      |           NULL | NULL   | Pune    | 70000.00 | NULL  |
|    3 | Snehal    |           NULL | NULL   | nsk     | 80000.00 | NULL  |
|    4 | Amarnath  |           NULL | NULL   | Pune    | 90000.00 | NULL  |
|    5 | Ajit      |           NULL | NULL   | pcmc    |  7000.00 | NULL  |
|    6 | Shiv      |           NULL | NULL   | Karad   |   700.00 | NULL  |
|    7 | MAnagalam |           NULL | NULL   | Satara  | 30000.00 | NULL  |
|    8 | munni     |           NULL | NULL   | goa     |  7000.00 | NULL  |
|    9 | NULL      |     3456789067 | NULL   | NULL    |     NULL | NULL  |
|   10 | NULL      |     3456789054 | NULL   | NULL    |     NULL | NULL  |
|   11 | NULL      |     9876543254 | NULL   | NULL    |     NULL | NULL  |
|   12 | NULL      |    87654321654 | NULL   | NULL    |     NULL | NULL  |
|   13 | NULL      |     8765432345 | NULL   | NULL    |     NULL | NULL  |
|   14 | NULL      |     9876543456 | NULL   | NULL    |     NULL | NULL  |
|   15 | NULL      | 87654323456789 | NULL   | NULL    |     NULL | NULL  |
+------+-----------+----------------+--------+---------+----------+-------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER DROP COLUMN EMAIL VARCHAR(50);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VARCHAR(50)' at line 1
mysql> ALTER TABLE CUSTOMER DROP COLUMN EMAIL;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+------+-----------+----------------+--------+---------+----------+
| c_id | C_NAME    | PH_NO          | gender | address | BALANCE  |
+------+-----------+----------------+--------+---------+----------+
|    1 | Ganesh    |           NULL | NULL   | Beed    |  6000.00 |
|    2 | Ajay      |           NULL | NULL   | Pune    | 70000.00 |
|    3 | Snehal    |           NULL | NULL   | nsk     | 80000.00 |
|    4 | Amarnath  |           NULL | NULL   | Pune    | 90000.00 |
|    5 | Ajit      |           NULL | NULL   | pcmc    |  7000.00 |
|    6 | Shiv      |           NULL | NULL   | Karad   |   700.00 |
|    7 | MAnagalam |           NULL | NULL   | Satara  | 30000.00 |
|    8 | munni     |           NULL | NULL   | goa     |  7000.00 |
|    9 | NULL      |     3456789067 | NULL   | NULL    |     NULL |
|   10 | NULL      |     3456789054 | NULL   | NULL    |     NULL |
|   11 | NULL      |     9876543254 | NULL   | NULL    |     NULL |
|   12 | NULL      |    87654321654 | NULL   | NULL    |     NULL |
|   13 | NULL      |     8765432345 | NULL   | NULL    |     NULL |
|   14 | NULL      |     9876543456 | NULL   | NULL    |     NULL |
|   15 | NULL      | 87654323456789 | NULL   | NULL    |     NULL |
+------+-----------+----------------+--------+---------+----------+
15 rows in set (0.01 sec)

mysql> ALTER TABLE CUSTOMER DROP PH_NO;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+------+-----------+--------+---------+----------+
| c_id | C_NAME    | gender | address | BALANCE  |
+------+-----------+--------+---------+----------+
|    1 | Ganesh    | NULL   | Beed    |  6000.00 |
|    2 | Ajay      | NULL   | Pune    | 70000.00 |
|    3 | Snehal    | NULL   | nsk     | 80000.00 |
|    4 | Amarnath  | NULL   | Pune    | 90000.00 |
|    5 | Ajit      | NULL   | pcmc    |  7000.00 |
|    6 | Shiv      | NULL   | Karad   |   700.00 |
|    7 | MAnagalam | NULL   | Satara  | 30000.00 |
|    8 | munni     | NULL   | goa     |  7000.00 |
|    9 | NULL      | NULL   | NULL    |     NULL |
|   10 | NULL      | NULL   | NULL    |     NULL |
|   11 | NULL      | NULL   | NULL    |     NULL |
|   12 | NULL      | NULL   | NULL    |     NULL |
|   13 | NULL      | NULL   | NULL    |     NULL |
|   14 | NULL      | NULL   | NULL    |     NULL |
|   15 | NULL      | NULL   | NULL    |     NULL |
+------+-----------+--------+---------+----------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER ADD CITY VARCHAR(55),EMAIL VARCHAR(50);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'EMAIL VARCHAR(50)' at line 1
mysql> ALTER TABLE CUSTOMER ADD  COLUMN  CITY VARCHAR(55),EMAIL VARCHAR(50);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'EMAIL VARCHAR(50)' at line 1
mysql> ALTER TABLE CUSTOMER ADD  COLUMN  CITY VARCHAR(55),ADD EMAIL VARCHAR(50);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+------+-----------+--------+---------+----------+------+-------+
| c_id | C_NAME    | gender | address | BALANCE  | CITY | EMAIL |
+------+-----------+--------+---------+----------+------+-------+
|    1 | Ganesh    | NULL   | Beed    |  6000.00 | NULL | NULL  |
|    2 | Ajay      | NULL   | Pune    | 70000.00 | NULL | NULL  |
|    3 | Snehal    | NULL   | nsk     | 80000.00 | NULL | NULL  |
|    4 | Amarnath  | NULL   | Pune    | 90000.00 | NULL | NULL  |
|    5 | Ajit      | NULL   | pcmc    |  7000.00 | NULL | NULL  |
|    6 | Shiv      | NULL   | Karad   |   700.00 | NULL | NULL  |
|    7 | MAnagalam | NULL   | Satara  | 30000.00 | NULL | NULL  |
|    8 | munni     | NULL   | goa     |  7000.00 | NULL | NULL  |
|    9 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   10 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   11 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   12 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   13 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   14 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   15 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
+------+-----------+--------+---------+----------+------+-------+
15 rows in set (0.00 sec)

mysql> SELECT*FROM EMPLOYEE;
Empty set (0.00 sec)

mysql> DESC EMPLOYEE;
+--------+---------------+------+-----+---------+-------+
| Field  | Type          | Null | Key | Default | Extra |
+--------+---------------+------+-----+---------+-------+
| E_ID   | int           | NO   | PRI | NULL    |       |
| E_NAME | varchar(44)   | NO   | UNI | NULL    |       |
| AGE    | int           | YES  |     | NULL    |       |
| SALARY | decimal(10,2) | YES  |     | NULL    |       |
| D_ID   | int           | YES  | MUL | NULL    |       |
| EMAIL  | varchar(55)   | YES  |     | NULL    |       |
+--------+---------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE MODIFY E_NAME VARCHAR(45) TO E_NAME VARCHAR(55);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO E_NAME VARCHAR(55)' at line 1
mysql> ALTER TABLE EMPLOYEE MODIFY E_NAME VARCHAR(45) TO  VARCHAR(55);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO  VARCHAR(55)' at line 1
mysql> ALTER TABLE EMPLOYEE MODIFY E_NAME VARCHAR(55);
Query OK, 0 rows affected (0.08 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM EMPLOYEE;
Empty set (0.00 sec)

mysql> SELECT*FROM CUSTOMER;
+------+-----------+--------+---------+----------+------+-------+
| c_id | C_NAME    | gender | address | BALANCE  | CITY | EMAIL |
+------+-----------+--------+---------+----------+------+-------+
|    1 | Ganesh    | NULL   | Beed    |  6000.00 | NULL | NULL  |
|    2 | Ajay      | NULL   | Pune    | 70000.00 | NULL | NULL  |
|    3 | Snehal    | NULL   | nsk     | 80000.00 | NULL | NULL  |
|    4 | Amarnath  | NULL   | Pune    | 90000.00 | NULL | NULL  |
|    5 | Ajit      | NULL   | pcmc    |  7000.00 | NULL | NULL  |
|    6 | Shiv      | NULL   | Karad   |   700.00 | NULL | NULL  |
|    7 | MAnagalam | NULL   | Satara  | 30000.00 | NULL | NULL  |
|    8 | munni     | NULL   | goa     |  7000.00 | NULL | NULL  |
|    9 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   10 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   11 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   12 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   13 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   14 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   15 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
+------+-----------+--------+---------+----------+------+-------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER RENAME C_NAME TO CUSTOMER_NAME;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO CUSTOMER_NAME' at line 1
mysql> ALTER TABLE CUSTOMER RENAME C_NAME TO CUSTOMER_NAME VARCHAR(44);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO CUSTOMER_NAME VARCHAR(44)' at line 1
mysql> ALTER TABLE CUSTOMER RENAME C_NAME VARCHAR(20) TO CUSTOMER_NAME VARCHAR(44);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VARCHAR(20) TO CUSTOMER_NAME VARCHAR(44)' at line 1
mysql> ALTER TABLE CUSTOMER RENAME  COLUMN  C_NAME VARCHAR(20) TO CUSTOMER_NAME VARCHAR(44);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VARCHAR(20) TO CUSTOMER_NAME VARCHAR(44)' at line 1
mysql> ALTER TABLE CUSTOMER RENAME  COLUMN  C_NAME VARCHAR(20) TO CUSTOMER_NAME;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VARCHAR(20) TO CUSTOMER_NAME' at line 1
mysql> ALTER TABLE CUSTOMER RENAME  COLUMN  C_NAME TO CUSTOMER_NAME;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+------+---------------+--------+---------+----------+------+-------+
| c_id | CUSTOMER_NAME | gender | address | BALANCE  | CITY | EMAIL |
+------+---------------+--------+---------+----------+------+-------+
|    1 | Ganesh        | NULL   | Beed    |  6000.00 | NULL | NULL  |
|    2 | Ajay          | NULL   | Pune    | 70000.00 | NULL | NULL  |
|    3 | Snehal        | NULL   | nsk     | 80000.00 | NULL | NULL  |
|    4 | Amarnath      | NULL   | Pune    | 90000.00 | NULL | NULL  |
|    5 | Ajit          | NULL   | pcmc    |  7000.00 | NULL | NULL  |
|    6 | Shiv          | NULL   | Karad   |   700.00 | NULL | NULL  |
|    7 | MAnagalam     | NULL   | Satara  | 30000.00 | NULL | NULL  |
|    8 | munni         | NULL   | goa     |  7000.00 | NULL | NULL  |
|    9 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
|   10 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
|   11 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
|   12 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
|   13 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
|   14 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
|   15 | NULL          | NULL   | NULL    |     NULL | NULL | NULL  |
+------+---------------+--------+---------+----------+------+-------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER RENAME CUSTOMER_NAME TO C_NAME;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO C_NAME' at line 1
mysql> ALTER TABLE CUSTOMER RENAME COLUMN  CUSTOMER_NAME TO C_NAME;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+------+-----------+--------+---------+----------+------+-------+
| c_id | C_NAME    | gender | address | BALANCE  | CITY | EMAIL |
+------+-----------+--------+---------+----------+------+-------+
|    1 | Ganesh    | NULL   | Beed    |  6000.00 | NULL | NULL  |
|    2 | Ajay      | NULL   | Pune    | 70000.00 | NULL | NULL  |
|    3 | Snehal    | NULL   | nsk     | 80000.00 | NULL | NULL  |
|    4 | Amarnath  | NULL   | Pune    | 90000.00 | NULL | NULL  |
|    5 | Ajit      | NULL   | pcmc    |  7000.00 | NULL | NULL  |
|    6 | Shiv      | NULL   | Karad   |   700.00 | NULL | NULL  |
|    7 | MAnagalam | NULL   | Satara  | 30000.00 | NULL | NULL  |
|    8 | munni     | NULL   | goa     |  7000.00 | NULL | NULL  |
|    9 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   10 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   11 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   12 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   13 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   14 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
|   15 | NULL      | NULL   | NULL    |     NULL | NULL | NULL  |
+------+-----------+--------+---------+----------+------+-------+
15 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER REMOVE COLUMN EMAIL;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'COLUMN EMAIL' at line 1
mysql> ALTER TABLE CUSTOMER DROP COLUMN EMAIL;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM CUSTOMER;
+------+-----------+--------+---------+----------+------+
| c_id | C_NAME    | gender | address | BALANCE  | CITY |
+------+-----------+--------+---------+----------+------+
|    1 | Ganesh    | NULL   | Beed    |  6000.00 | NULL |
|    2 | Ajay      | NULL   | Pune    | 70000.00 | NULL |
|    3 | Snehal    | NULL   | nsk     | 80000.00 | NULL |
|    4 | Amarnath  | NULL   | Pune    | 90000.00 | NULL |
|    5 | Ajit      | NULL   | pcmc    |  7000.00 | NULL |
|    6 | Shiv      | NULL   | Karad   |   700.00 | NULL |
|    7 | MAnagalam | NULL   | Satara  | 30000.00 | NULL |
|    8 | munni     | NULL   | goa     |  7000.00 | NULL |
|    9 | NULL      | NULL   | NULL    |     NULL | NULL |
|   10 | NULL      | NULL   | NULL    |     NULL | NULL |
|   11 | NULL      | NULL   | NULL    |     NULL | NULL |
|   12 | NULL      | NULL   | NULL    |     NULL | NULL |
|   13 | NULL      | NULL   | NULL    |     NULL | NULL |
|   14 | NULL      | NULL   | NULL    |     NULL | NULL |
|   15 | NULL      | NULL   | NULL    |     NULL | NULL |
+------+-----------+--------+---------+----------+------+
15 rows in set (0.00 sec)

mysql> DESC CUSTOMER;
+---------+---------------+------+-----+---------+----------------+
| Field   | Type          | Null | Key | Default | Extra          |
+---------+---------------+------+-----+---------+----------------+
| c_id    | int           | NO   | PRI | NULL    | auto_increment |
| C_NAME  | varchar(40)   | YES  |     | NULL    |                |
| gender  | char(1)       | YES  |     | NULL    |                |
| address | varchar(30)   | YES  |     | NULL    |                |
| BALANCE | decimal(10,2) | YES  |     | NULL    |                |
| CITY    | varchar(55)   | YES  |     | NULL    |                |
+---------+---------------+------+-----+---------+----------------+
6 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER MODIFY CONSTRAINT ON C_NAME;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'CONSTRAINT ON C_NAME' at line 1
mysql> ALTER TABLE CUSTOMER MODIFY CONSTRAINT C_NAME;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'CONSTRAINT C_NAME' at line 1
mysql> ALTER TABLE CUSTOMER MODIFY CONSTRAINT NOT NULL C_NAME;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'CONSTRAINT NOT NULL C_NAME' at line 1
mysql> ALTER TABLE CUSTOMER MODIFY  C_NAME NOT NULL;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'NOT NULL' at line 1
mysql> ALTER TABLE CUSTOMER MODIFY  COLUMN C_NAME NOT NULL;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'NOT NULL' at line 1
mysql> ALTER TABLE CUSTOMER MODIFY  C_NAME VARCHAR(66) NOT NULL;
ERROR 1265 (01000): Data truncated for column 'C_NAME' at row 9
mysql> ALTER TABLE CUSTOMER MODIFY  COLUMN C_NAME VARCHAR(25) NOT NULL;
ERROR 1265 (01000): Data truncated for column 'C_NAME' at row 9
mysql> show databases;
+------------------------+
| Database               |
+------------------------+
| bank                   |
| company                |
| company_db             |
| information_schema     |
| java_practice          |
| liabrary               |
| mysql                  |
| performance_schema     |
| product                |
| student_skill_exchange |
| sys                    |
+------------------------+
11 rows in set (0.00 sec)

mysql> create database bank_db;
Query OK, 1 row affected (0.01 sec)

mysql> show databases;
+------------------------+
| Database               |
+------------------------+
| bank                   |
| bank_db                |
| company                |
| company_db             |
| information_schema     |
| java_practice          |
| liabrary               |
| mysql                  |
| performance_schema     |
| product                |
| student_skill_exchange |
| sys                    |
+------------------------+
12 rows in set (0.00 sec)

mysql> use bank_db;
Database changed
mysql> show tables;
Empty set (0.00 sec)

mysql> drop database company_db;
Query OK, 1 row affected (0.03 sec)

mysql> show tables;
Empty set (0.00 sec)

mysql> show databases;
+------------------------+
| Database               |
+------------------------+
| bank                   |
| bank_db                |
| company                |
| information_schema     |
| java_practice          |
| liabrary               |
| mysql                  |
| performance_schema     |
| product                |
| student_skill_exchange |
| sys                    |
+------------------------+
11 rows in set (0.00 sec)

mysql> use company;
Database changed
mysql> show tables;
+-------------------+
| Tables_in_company |
+-------------------+
| employee          |
+-------------------+
1 row in set (0.00 sec)

mysql> select*from employee;
+-----+--------+------+--------+---------+---------+
| ID  | FNAME  | AGE  | SALARY | DEPT    | EMAIL   |
+-----+--------+------+--------+---------+---------+
| 101 | RAHUL  |   23 |  30000 | IT      | NULL    |
| 102 | AMIT   |   25 |  40000 | HR      | AJAY@12 |
| 103 | PRIYA  |   22 |  35000 | IT      | XYZ@345 |
| 104 | RAHUL  |   23 |  50000 | FINANCE | XYZ@345 |
| 105 | ROHIT  |   24 |  45000 | IT      | XYZ@345 |
| 106 | SAMUUU |   24 |  55000 | IT      | SDEZ@35 |
+-----+--------+------+--------+---------+---------+
6 rows in set (0.02 sec)

mysql> use bank_db;
Database changed
mysql> show tables;
Empty set (0.00 sec)

mysql> CREATE TABLE ACCOUNT();
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql>
mysql> CREATE TABLE ACCOUNT(A_ID INT PRIMARY KEY,A_NAME VARCHAR(45) NOT NULL,BALANCE DECIMAL(10,2)CHECK (BALANCE>=0));
Query OK, 0 rows affected (0.03 sec)

mysql> DESC ACCOUNT;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| A_ID    | int           | NO   | PRI | NULL    |       |
| A_NAME  | varchar(45)   | NO   |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT ADD COLUMN  PHONE BIGINT ,ADD ACC_TYPE VARCHAR(40);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(45)   | NO   |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| PHONE    | bigint        | YES  |     | NULL    |       |
| ACC_TYPE | varchar(40)   | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT MODIFY COLUMN  A_NAME TO A_NAME VARCHAR(50);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO A_NAME VARCHAR(50)' at line 1
mysql> ALTER TABLE ACCOUNT MODIFY COLUMN  A_NAME VARCHAR(35) TO A_NAME VARCHAR(50);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO A_NAME VARCHAR(50)' at line 1
mysql> ALTER TABLE ACCOUNT MODIFY COLUMN  A_NAME TO A_NAME VARCHAR(50)NOT NULL ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TO A_NAME VARCHAR(50)NOT NULL' at line 1
mysql> ALTER TABLE ACCOUNT MODIFY COLUMN A_NAME VARCHAR(50)NOT NULL ;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(50)   | NO   |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| PHONE    | bigint        | YES  |     | NULL    |       |
| ACC_TYPE | varchar(40)   | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT
    -> MODIFY COLUMN A_NAME VARCHAR(50) NOT NULL;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE ACCOUNT
    -> CHANGE A_NAME CUSTOMER_NAME VARCHAR(50);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+---------------+---------------+------+-----+---------+-------+
| Field         | Type          | Null | Key | Default | Extra |
+---------------+---------------+------+-----+---------+-------+
| A_ID          | int           | NO   | PRI | NULL    |       |
| CUSTOMER_NAME | varchar(50)   | YES  |     | NULL    |       |
| BALANCE       | decimal(10,2) | YES  |     | NULL    |       |
| PHONE         | bigint        | YES  |     | NULL    |       |
| ACC_TYPE      | varchar(40)   | YES  |     | NULL    |       |
+---------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT CHANGE CUSTOMER_NAME A_NAME VARCHAR(60);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| PHONE    | bigint        | YES  |     | NULL    |       |
| ACC_TYPE | varchar(40)   | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE RENAME COLUMN PHONE TO MOBILE_NO BIGINT;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'RENAME COLUMN PHONE TO MOBILE_NO BIGINT' at line 1
mysql> ALTER TABLE ACCOUNT RENAME COLUMN PHONE TO MOBILE_NO BIGINT;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'BIGINT' at line 1
mysql> ALTER TABLE ACCOUNT RENAME COLUMN PHONE MOBILE_NO BIGINT;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'MOBILE_NO BIGINT' at line 1
mysql> ALTER TABLE ACCOUNT RENAME COLUMN PHONE MOBILE_NO BIGINT;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'MOBILE_NO BIGINT' at line 1
mysql> ALTER TABLE ACCOUNT RENAME COLUMN PHONE TO MOBILE_NO ;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| A_ID      | int           | NO   | PRI | NULL    |       |
| A_NAME    | varchar(60)   | YES  |     | NULL    |       |
| BALANCE   | decimal(10,2) | YES  |     | NULL    |       |
| MOBILE_NO | bigint        | YES  |     | NULL    |       |
| ACC_TYPE  | varchar(40)   | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT CHANGE COLUMN ACC_TYPE ACCOUNT_TYPE VARCHAR(30);
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| A_ID         | int           | NO   | PRI | NULL    |       |
| A_NAME       | varchar(60)   | YES  |     | NULL    |       |
| BALANCE      | decimal(10,2) | YES  |     | NULL    |       |
| MOBILE_NO    | bigint        | YES  |     | NULL    |       |
| ACCOUNT_TYPE | varchar(30)   | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT CHANGE ACCOUNT_TYPE ACC_TYPE VARCHAR(30);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| A_ID      | int           | NO   | PRI | NULL    |       |
| A_NAME    | varchar(60)   | YES  |     | NULL    |       |
| BALANCE   | decimal(10,2) | YES  |     | NULL    |       |
| MOBILE_NO | bigint        | YES  |     | NULL    |       |
| ACC_TYPE  | varchar(30)   | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT DROP COLUMN MOBILE_NO;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT  ADD COLUMN EMAIL VARCHAR(40) UNIQUE;
Query OK, 0 rows affected (0.08 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  | UNI | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT MODIFY CONSTRAINT A_NAME VARCHAR(20)NOT NULL;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'CONSTRAINT A_NAME VARCHAR(20)NOT NULL' at line 1
mysql> ALTER TABLE ACCOUNT MODIFY COLUMN  A_NAME VARCHAR(20)NOT NULL;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(20)   | NO   |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  | UNI | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT MODIFY COLUMN A_NAME VARCHAR(60);
Query OK, 0 rows affected (0.08 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  | UNI | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT MODIFY COLUMN A_NAME VARCHAR(60);\
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  | UNI | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT DROP CONSTRAINT EMAIL VARCHAR(40) UNIQUE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'VARCHAR(40) UNIQUE' at line 1
mysql> ALTER TABLE ACCOUNT MODIFY COLUMN EMAIL VARCHAR(40);
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  | UNI | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> ALTER TABLE ACCOUNT DROP INDEX EMAIL;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> CREATE TABLE CUSTOMER3(C_ID INT PRIMARY KEY,C_NAME VARCHAR(30),CITY VARCHAR(30),BALANCE DECIMAL(10,2));
Query OK, 0 rows affected (0.03 sec)

mysql> DESC ACCOUNT;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| A_ID     | int           | NO   | PRI | NULL    |       |
| A_NAME   | varchar(60)   | YES  |     | NULL    |       |
| BALANCE  | decimal(10,2) | YES  |     | NULL    |       |
| ACC_TYPE | varchar(30)   | YES  |     | NULL    |       |
| EMAIL    | varchar(40)   | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(30)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 MODIFY COLUMN CITY VARCHAR(45) DEFAULT 'PUNE';
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(45)   | YES  |     | PUNE    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 MODIFY COLUMN CITY VARCHAR(50);
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(50)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 MODIFY COLUMN BALANCE DECIMAL(10,2) CHECK (BALANCE>=0);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(50)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> SHOW CREATE TABLE CUSTOMER3;
+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table     | Create Table                                                                                                                                                                                                                                                                                                         |
+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CUSTOMER3 | CREATE TABLE `customer3` (
  `C_ID` int NOT NULL,
  `C_NAME` varchar(30) DEFAULT NULL,
  `CITY` varchar(50) DEFAULT NULL,
  `BALANCE` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`C_ID`),
  CONSTRAINT `customer3_chk_1` CHECK ((`BALANCE` >= 0))
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 DROP customer3_chk_1;
ERROR 1091 (42000): Can't DROP 'customer3_chk_1'; check that column/key exists
mysql> ALTER TABLE CUSTOMER3 DROP  CHECK customer3_chk_1;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW CREATE TABLE CUSTOMER3;
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table     | Create Table                                                                                                                                                                                                                                                |
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CUSTOMER3 | CREATE TABLE `customer3` (
  `C_ID` int NOT NULL,
  `C_NAME` varchar(30) DEFAULT NULL,
  `CITY` varchar(50) DEFAULT NULL,
  `BALANCE` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`C_ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(50)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 RENAME TO CUSTOMER_DETAILS ;
Query OK, 0 rows affected (0.02 sec)

mysql> DESC CUSTOMER3;
ERROR 1146 (42S02): Table 'bank_db.customer3' doesn't exist
mysql> SHOW CREATE TABLE CUSTOMER_DETAILS;
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table            | Create Table                                                                                                                                                                                                                                                       |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CUSTOMER_DETAILS | CREATE TABLE `customer_details` (
  `C_ID` int NOT NULL,
  `C_NAME` varchar(30) DEFAULT NULL,
  `CITY` varchar(50) DEFAULT NULL,
  `BALANCE` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`C_ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER_DETAILS RENAME TO CUSTOMER3;
Query OK, 0 rows affected (0.02 sec)

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(50)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 ADD COLUMN PHONE BIGINT ADD COLUMN EMAIL VARCHAR(50);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ADD COLUMN EMAIL VARCHAR(50)' at line 1
mysql> ALTER TABLE CUSTOMER3 ADD COLUMN PHONE BIGINT , ADD COLUMN EMAIL VARCHAR(50);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(50)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
| PHONE   | bigint        | YES  |     | NULL    |       |
| EMAIL   | varchar(50)   | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 DROP COLUMN PHONE ,DROP COLUMN EMAIL;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC CUSTOMER3;
+---------+---------------+------+-----+---------+-------+
| Field   | Type          | Null | Key | Default | Extra |
+---------+---------------+------+-----+---------+-------+
| C_ID    | int           | NO   | PRI | NULL    |       |
| C_NAME  | varchar(30)   | YES  |     | NULL    |       |
| CITY    | varchar(50)   | YES  |     | NULL    |       |
| BALANCE | decimal(10,2) | YES  |     | NULL    |       |
+---------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> ALTER TABLE CUSTOMER3 CHANGE COLUMN CITY LOCATION VARCHAR(60);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> create table employee2(e_id int primary key,e_name varchar(55),salary decimal(8,2));
Query OK, 0 rows affected (0.03 sec)

mysql> desc employee2'
    '> ;
    '> desc employee2;
    '> select*from employee2;
    '>
    '> show tables;
    '> exit;
    '>
    '>
    '>
    '>
    '>
    '>
    '>
    '>
    '>
    '> exit;
    '> ^C
mysql> show tables;
+-------------------+
| Tables_in_bank_db |
+-------------------+
| account           |
| customer3         |
| employee2         |
+-------------------+
3 rows in set (0.00 sec)

mysql> alter table employee2 modify column e_name varchar(55) unique;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee2;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| e_id   | int          | NO   | PRI | NULL    |       |
| e_name | varchar(55)  | YES  | UNI | NULL    |       |
| salary | decimal(8,2) | YES  |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE2 ADD CONSTRAINT E_NAME UNIQUE (E_NAME);
ERROR 1061 (42000): Duplicate key name 'E_NAME'
mysql> ALTER TABLE EMPLOYEE2 ADD CONSTRAINT E_NAME UNIQUE (E_NAME);
ERROR 1061 (42000): Duplicate key name 'E_NAME'
mysql>
mysql> ALTER TABLE EMPLOYEE2 DROP INDEX E_NAME;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee2;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| e_id   | int          | NO   | PRI | NULL    |       |
| e_name | varchar(55)  | YES  |     | NULL    |       |
| salary | decimal(8,2) | YES  |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> SHOW CREATE TABLE EMPLOYE2;
ERROR 1146 (42S02): Table 'bank_db.employe2' doesn't exist
mysql> SHOW CREATE TABLE EMPLOYEE2;
+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table     | Create Table                                                                                                                                                                                                           |
+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| EMPLOYEE2 | CREATE TABLE `employee2` (
  `e_id` int NOT NULL,
  `e_name` varchar(55) DEFAULT NULL,
  `salary` decimal(8,2) DEFAULT NULL,
  PRIMARY KEY (`e_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE2 MODIFY COLUMN E_NAME VARCHAR(44)NOT NULL;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW CREATE TABLE EMPLOYE2;
ERROR 1146 (42S02): Table 'bank_db.employe2' doesn't exist
mysql> SHOW CREATE TABLE EMPLOYEE2;
+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table     | Create Table                                                                                                                                                                                                       |
+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| EMPLOYEE2 | CREATE TABLE `employee2` (
  `e_id` int NOT NULL,
  `E_NAME` varchar(44) NOT NULL,
  `salary` decimal(8,2) DEFAULT NULL,
  PRIMARY KEY (`e_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> desc employee2;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| e_id   | int          | NO   | PRI | NULL    |       |
| E_NAME | varchar(44)  | NO   |     | NULL    |       |
| salary | decimal(8,2) | YES  |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE2 MODIFY COLUMN SALARY DECIMAL(10,2);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE EMPLOYEE2 RENAME COLUMN E_NAME TO EMP_NAME;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee2;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| e_id     | int           | NO   | PRI | NULL    |       |
| EMP_NAME | varchar(44)   | NO   |     | NULL    |       |
| SALARY   | decimal(10,2) | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE2 MODIFY COLUMN EMP_NAME VARCHAR(100);
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee2;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| e_id     | int           | NO   | PRI | NULL    |       |
| EMP_NAME | varchar(100)  | YES  |     | NULL    |       |
| SALARY   | decimal(10,2) | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE2 MODIFY COLUMN SALARY DEFAULT 5000;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'DEFAULT 5000' at line 1
mysql> ALTER TABLE EMPLOYEE2 MODIFY COLUMN SALARY DEFAULT '5000';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'DEFAULT '5000'' at line 1
mysql> ALTER TABLE EMPLOYEE2 MODIFY COLUMN SALARY DECIMAL (10,2) DEFAULT '5000';
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee2;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| e_id     | int           | NO   | PRI | NULL    |       |
| EMP_NAME | varchar(100)  | YES  |     | NULL    |       |
| SALARY   | decimal(10,2) | YES  |     | 5000.00 |       |
+----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> ALTER TABLE EMPLOYEE2 MODIFY  COLUMN SALARY DECIMAL(10,2);
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc employee2;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| e_id     | int           | NO   | PRI | NULL    |       |
| EMP_NAME | varchar(100)  | YES  |     | NULL    |       |
| SALARY   | decimal(10,2) | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql>
