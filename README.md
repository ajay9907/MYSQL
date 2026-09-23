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

mysql> SELECT*FROM CUSTOMER  GROUP BY BALANCE ASC;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ASC' at line 1
mysql> SELECT*FROM CUSTOMER  GROUP BY BALANCE ;
ERROR 1055 (42000): Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'bank.CUSTOMER.ID' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
mysql>
