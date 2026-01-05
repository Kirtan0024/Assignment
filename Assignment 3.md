**\*\*1.write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer\\\_id, cust\\\_name, city, grade, and salesman\\\_id\*\***







mysql> create database Assignment;



Query OK, 1 row affected (0.06 sec)







mysql> show databases;



+--------------------+



| Database           |



+--------------------+



| assignment         |



| data               |



| information\\\_schema |



| mdb                |



| mysql              |



| ndb                |



| performance\\\_schema |



| sakila             |



| sys                |



| world              |



+--------------------+



10 rows in set (0.00 sec)







mysql> use assignment;



Database changed



mysql> show tables;



Empty set (0.04 sec)







mysql> create table data;



ERROR 4028 (HY000): A table must have at least one visible column.



mysql> create table customer(customer\\\_id int primary key, customer\\\_name varchar(60) not null, city varchar(100) not null);



Query OK, 0 rows affected (0.12 sec)







mysql> describe data;



ERROR 1146 (42S02): Table 'assignment.data' doesn't exist



mysql> describe assignment;



ERROR 1146 (42S02): Table 'assignment.assignment' doesn't exist



mysql> describe customer;



+---------------+--------------+------+-----+---------+-------+



| Field         | Type         | Null | Key | Default | Extra |



+---------------+--------------+------+-----+---------+-------+



| customer\\\_id   | int          | NO   | PRI | NULL    |       |



| customer\\\_name | varchar(60)  | NO   |     | NULL    |       |



| city          | varchar(100) | NO   |     | NULL    |       |



+---------------+--------------+------+-----+---------+-------+



3 rows in set (0.03 sec)







mysql> alter table customer add column grade float not null;



Query OK, 0 rows affected (0.17 sec)



Records: 0  Duplicates: 0  Warnings: 0







mysql> alter table customer add column salesman\\\_id int not null;



Query OK, 0 rows affected (0.09 sec)



Records: 0  Duplicates: 0  Warnings: 0







mysql> describe customer;



+---------------+--------------+------+-----+---------+-------+



| Field         | Type         | Null | Key | Default | Extra |



+---------------+--------------+------+-----+---------+-------+



| customer\\\_id   | int          | NO   | PRI | NULL    |       |



| customer\\\_name | varchar(60)  | NO   |     | NULL    |       |



| city          | varchar(100) | NO   |     | NULL    |       |



| grade         | float        | NO   |     | NULL    |       |



| salesman\\\_id   | int          | NO   |     | NULL    |       |



+---------------+--------------+------+-----+---------+-------+



5 rows in set (0.00 sec)







mysql> insert into customer vallues(3002, "jay", "New York", 100, 5001);



ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'vallues(3002, "jay", "New York", 100, 5001)' at line 1



mysql> insert into customer values(3002, "jay", "New York", 100, 5001);



Query OK, 1 row affected (0.02 sec)







mysql> insert into customer values(3007, "Nilan", "Clifornia", 200, 5001);



Query OK, 1 row affected (0.01 sec)







mysql> insert into customer values(3005, "Raj", "New York", 200, 5002);



Query OK, 1 row affected (0.01 sec)







mysql> insert into customer values(3008, "Dev", "London", 300, 5002);



Query OK, 1 row affected (0.01 sec)







mysql> insert into customer values(3004, "Jalp", "Paris", 300, 5006);



Query OK, 1 row affected (0.01 sec)







mysql> insert into customer values(3009, "Meet", "Berlin", 100, 5003);



Query OK, 1 row affected (0.01 sec)







mysql> insert into customer values(3003, "Ajay", "Moscow", 200, 5007);



Query OK, 1 row affected (0.01 sec)







mysql> insert into customer values(3001, "Yash", "London", 100, 5005);



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from customer;



+-------------+---------------+-----------+-------+-------------+



| customer\\\_id | customer\\\_name | city      | grade | salesman\\\_id |



+-------------+---------------+-----------+-------+-------------+



|        3001 | Yash          | London    |   100 |        5005 |



|        3002 | jay           | New York  |   100 |        5001 |



|        3003 | Ajay          | Moscow    |   200 |        5007 |



|        3004 | Jalp          | Paris     |   300 |        5006 |



|        3005 | Raj           | New York  |   200 |        5002 |



|        3007 | Nilan         | Clifornia |   200 |        5001 |



|        3008 | Dev           | London    |   300 |        5002 |



|        3009 | Meet          | Berlin    |   100 |        5003 |



+-------------+---------------+-----------+-------+-------------+



8 rows in set (0.00 sec)







**\*\*2. write a SQL query to find all the customers in ‘New York’ city who have a grade value above 100. Return customer\\\_id, cust\\\_name, city, grade, and salesman\\\_id.\*\***







mysql> select \\\* from customer where city = "New York";



+-------------+---------------+----------+-------+-------------+



| customer\\\_id | customer\\\_name | city     | grade | salesman\\\_id |



+-------------+---------------+----------+-------+-------------+



|        3002 | jay           | New York |   100 |        5001 |



|        3005 | Raj           | New York |   200 |        5002 |



+-------------+---------------+----------+-------+-------------+



2 rows in set (0.01 sec)







mysql> select \\\* from customer where city = "New York" and grade > 100;



+-------------+---------------+----------+-------+-------------+



| customer\\\_id | customer\\\_name | city     | grade | salesman\\\_id |



+-------------+---------------+----------+-------+-------------+



|        3005 | Raj           | New York |   200 |        5002 |



+-------------+---------------+----------+-------+-------------+



1 row in set (0.01 sec)







mysql> select \\\* from customer where city = "New York" and not grade > 100;



+-------------+---------------+----------+-------+-------------+



| customer\\\_id | customer\\\_name | city     | grade | salesman\\\_id |



+-------------+---------------+----------+-------+-------------+



|        3002 | jay           | New York |   100 |        5001 |



+-------------+---------------+----------+-------+-------------+



1 row in set (0.00 sec)







mysql> select \\\* from customer where city = "New York" and not grade < 100;



+-------------+---------------+----------+-------+-------------+



| customer\\\_id | customer\\\_name | city     | grade | salesman\\\_id |



+-------------+---------------+----------+-------+-------------+



|        3002 | jay           | New York |   100 |        5001 |



|        3005 | Raj           | New York |   200 |        5002 |



+-------------+---------------+----------+-------+-------------+



2 rows in set (0.00 sec)











**\*\*3. Write a SQL query that displays order number, purchase amount, and the achieved and unachieved percentage (%) for those orders that exceed 50%of thetarget value of 6000.\*\***







mysql> show databases;



+--------------------+



| Database           |



+--------------------+



| assignment         |



| information\\\_schema |



| mdb                |



| mysql              |



| performance\\\_schema |



| sakila             |



| sys                |



| world              |



+--------------------+



8 rows in set (0.00 sec)







mysql> use assignment;



Database changed



mysql> show tables;



+----------------------+



| Tables\\\_in\\\_assignment |



+----------------------+



| customer             |



+----------------------+



1 row in set (0.00 sec)







mysql> create table orders(order\\\_number int primary key, customer\\\_id int not null, purchase\\\_amount decimal(10,2), order\\\_date date, salesman\\\_id int not null);



Query OK, 0 rows affected (0.10 sec)







mysql> describe orders;



+-----------------+---------------+------+-----+---------+-------+



| Field           | Type          | Null | Key | Default | Extra |



+-----------------+---------------+------+-----+---------+-------+



| order\\\_number    | int           | NO   | PRI | NULL    |       |



| customer\\\_id     | int           | NO   |     | NULL    |       |



| purchase\\\_amount | decimal(10,2) | YES  |     | NULL    |       |



| order\\\_date      | date          | YES  |     | NULL    |       |



| salesman\\\_id     | int           | NO   |     | NULL    |       |



+-----------------+---------------+------+-----+---------+-------+



5 rows in set (0.01 sec)







mysql> insert into orders values(1001, 101, 650.50, 2025-01-01, 5001);



ERROR 1292 (22007): Incorrect date value: '2023' for column 'order\\\_date' at row 1







mysql> insert into orders values(1001, 101, 650.50, "2025-01-01", 5001);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1002, 102, 152.75, "2025-02-01", 5002);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1003, 103, 255.75, "2025-03-02", 5003);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1004, 101, 555.75, "2025-03-03", 5004);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1005, 104, 75.75, "2025-05-15", 5002);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1006, 103, 7500.75, "2025-08-05", 5001);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1007, 106, 650.75, "2025-12-25", 5003);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1008, 103, 9680, "2025-12-25", 5004);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1009, 107, 2500, "2025-05-08", 5005);



Query OK, 1 row affected (0.01 sec)







mysql> insert into orders values(1010, 108, 265.35, "2025-11-11", 5005);



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from orders;



+--------------+-------------+-----------------+------------+-------------+



| order\\\_number | customer\\\_id | purchase\\\_amount | order\\\_date | salesman\\\_id |



+--------------+-------------+-----------------+------------+-------------+



|         1001 |         101 |          650.50 | 2025-01-01 |        5001 |



|         1002 |         102 |          152.75 | 2025-02-01 |        5002 |



|         1003 |         103 |          255.75 | 2025-03-02 |        5003 |



|         1004 |         101 |          555.75 | 2025-03-03 |        5004 |



|         1005 |         104 |           75.75 | 2025-05-15 |        5002 |



|         1006 |         103 |         7500.75 | 2025-08-05 |        5001 |



|         1007 |         106 |          650.75 | 2025-12-25 |        5003 |



|         1008 |         103 |         9680.00 | 2025-12-25 |        5004 |



|         1009 |         107 |         2500.00 | 2025-05-08 |        5005 |



|         1010 |         108 |          265.35 | 2025-11-11 |        5005 |



+--------------+-------------+-----------------+------------+-------------+



10 rows in set (0.00 sec)







**\*\*4. write a SQL query to calculate the total purchase amount of all orders. Return total purchase amount.\*\***







mysql> select sum(purchase\\\_amount) as Total\\\_Amount from orders;



+--------------+



| Total\\\_Amount |



+--------------+



|     22287.35 |



+--------------+



1 row in set (0.01 sec)







mysql> select max(purchase\\\_amount) as Maximum\\\_Amount from orders;



+----------------+



| Maximum\\\_Amount |



+----------------+



|        9680.00 |



+----------------+



1 row in set (0.01 sec)







**\*\*5. write a SQL query to find the highest purchase amount ordered by each customer. Return customer ID, maximum purchase amount.\*\***







mysql> select max(purchase\\\_amount) as Maximum\\\_Amount from orders group by(customer\\\_id);



+----------------+



| Maximum\\\_Amount |



+----------------+



|         650.50 |



|         152.75 |



|        9680.00 |



|          75.75 |



|         650.75 |



|        2500.00 |



|         265.35 |



+----------------+



7 rows in set (0.01 sec)







mysql> select customer\\\_id, max(purchase\\\_amount) as Maximum\\\_Amount from orders group by(customer\\\_id);



+-------------+----------------+



| customer\\\_id | Maximum\\\_Amount |



+-------------+----------------+



|         101 |         650.50 |



|         102 |         152.75 |



|         103 |        9680.00 |



|         104 |          75.75 |



|         106 |         650.75 |



|         107 |        2500.00 |



|         108 |         265.35 |



+-------------+----------------+



7 rows in set (0.00 sec)











**\*\*6. write a SQL query to calculate the average product price. Return average product price.\*\***











mysql> create table products(product\\\_id int primary key auto\\\_increment, product\\\_name varchar(100), product\\\_price decimal(10, 2), purchase\\\_date date);



Query OK, 0 rows affected (0.04 sec)







mysql> describe products;



+---------------+---------------+------+-----+---------+----------------+



| Field         | Type          | Null | Key | Default | Extra          |



+---------------+---------------+------+-----+---------+----------------+



| product\\\_id    | int           | NO   | PRI | NULL    | auto\\\_increment |



| product\\\_name  | varchar(100)  | YES  |     | NULL    |                |



| product\\\_price | decimal(10,2) | YES  |     | NULL    |                |



| purchase\\\_date | date          | YES  |     | NULL    |                |



+---------------+---------------+------+-----+---------+----------------+



4 rows in set (0.00 sec)







mysql> insert into products(product\\\_id, product\\\_name, product\\\_price, purchase\\\_date) values(1, "Laptop", 85299.99, 2022-03-02);



ERROR 1292 (22007): Incorrect date value: '2017' for column 'purchase\\\_date' at row 1



mysql> insert into products(product\\\_id, product\\\_name, product\\\_price, purchase\\\_date) values(1, "Laptop", 85299.99, "2022-03-02");



Query OK, 1 row affected (0.01 sec)







mysql> insert into products(product\\\_name, product\\\_price, purchase\\\_date) values("Vivo Phone", 25000.00, "2021-12-12");



Query OK, 1 row affected (0.01 sec)







mysql> insert into products(product\\\_name, product\\\_price, purchase\\\_date) values("Headphone", 2500.00, "2023-02-15");



Query OK, 1 row affected (0.01 sec)







mysql> insert into products(product\\\_name, product\\\_price, purchase\\\_date) values("Keyboard", 650.00, "2020-05-02");



Query OK, 1 row affected (0.01 sec)







mysql> insert into products(product\\\_name, product\\\_price, purchase\\\_date) values("PowerBank", 950.00, "2025-04-20");



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from products;



+------------+--------------+---------------+---------------+



| product\\\_id | product\\\_name | product\\\_price | purchase\\\_date |



+------------+--------------+---------------+---------------+



|          1 | Laptop       |      85299.99 | 2022-03-02    |



|          2 | Vivo Phone   |      25000.00 | 2021-12-12    |



|          3 | Headphone    |       2500.00 | 2023-02-15    |



|          4 | Keyboard     |        650.00 | 2020-05-02    |



|          5 | PowerBank    |        950.00 | 2025-04-20    |



+------------+--------------+---------------+---------------+



5 rows in set (0.00 sec)







mysql> select avg(products\\\_price) as Total\\\_Price from products;



ERROR 1054 (42S22): Unknown column 'products\\\_price' in 'field list'



mysql> select avg(product\\\_price) as Total\\\_Price from products;



+--------------+



| Total\\\_Price  |



+--------------+



| 22879.998000 |



+--------------+



1 row in set (0.00 sec)











**\*\*7. write a SQL query to find those employees whose department is located at ‘Toronto’. Return first name, last name, employee ID, job ID.\*\***











mysql> create table employees(employee\\\_id int primary key auto\\\_increment, firstname varchar(50), lastname varchar(50), department varchar(50), job\\\_id int unique);



Query OK, 0 rows affected (0.15 sec)







mysql> describe employees;



+-------------+-------------+------+-----+---------+----------------+



| Field       | Type        | Null | Key | Default | Extra          |



+-------------+-------------+------+-----+---------+----------------+



| employee\\\_id | int         | NO   | PRI | NULL    | auto\\\_increment |



| firstname   | varchar(50) | YES  |     | NULL    |                |



| lastname    | varchar(50) | YES  |     | NULL    |                |



| department  | varchar(50) | YES  |     | NULL    |                |



| job\\\_id      | int         | YES  | UNI | NULL    |                |



+-------------+-------------+------+-----+---------+----------------+



5 rows in set (0.03 sec)







mysql> alter table employees add column city varchar(50);



Query OK, 0 rows affected (0.13 sec)



Records: 0  Duplicates: 0  Warnings: 0







mysql> describe employees;



+-------------+-------------+------+-----+---------+----------------+



| Field       | Type        | Null | Key | Default | Extra          |



+-------------+-------------+------+-----+---------+----------------+



| employee\\\_id | int         | NO   | PRI | NULL    | auto\\\_increment |



| firstname   | varchar(50) | YES  |     | NULL    |                |



| lastname    | varchar(50) | YES  |     | NULL    |                |



| department  | varchar(50) | YES  |     | NULL    |                |



| job\\\_id      | int         | YES  | UNI | NULL    |                |



| city        | varchar(50) | YES  |     | NULL    |                |



+-------------+-------------+------+-----+---------+----------------+



6 rows in set (0.00 sec)







mysql> insert into employees(firstname, lastname, department, job\\\_id, city) values



    -> ("Kirtan", "Parmar", "DS", 101, "New York"),



    -> ("Preet", "Patel", "FS", 102, "Toronto"),



    -> ("Riya", "Desai", "IT", 103, "London"),



    -> ("Yash", "shah", "DS", 104, "Melbourn");



Query OK, 4 rows affected (0.01 sec)



Records: 4  Duplicates: 0  Warnings: 0







mysql> select \\\* from employees;



+-------------+-----------+----------+------------+--------+----------+



| employee\\\_id | firstname | lastname | department | job\\\_id | city     |



+-------------+-----------+----------+------------+--------+----------+



|           1 | Kirtan    | Parmar   | DS         |    101 | New York |



|           2 | Preet     | Patel    | FS         |    102 | Toronto  |



|           3 | Riya      | Desai    | IT         |    103 | London   |



|           4 | Yash      | shah     | DS         |    104 | Melbourn |



+-------------+-----------+----------+------------+--------+----------+



4 rows in set (0.00 sec)







mysql> select employee\\\_id, firstname, lastname, department, job\\\_id from employees where city = "Toronto";



+-------------+-----------+----------+------------+--------+



| employee\\\_id | firstname | lastname | department | job\\\_id |



+-------------+-----------+----------+------------+--------+



|           2 | Preet     | Patel    | FS         |    102 |



+-------------+-----------+----------+------------+--------+



1 row in set (0.01 sec)







mysql> insert into employees(firstname, lastname, department, job\\\_id, city) values



    -> ("Vraj", "Patel", "PHP", 105, "Toronto");



Query OK, 1 row affected (0.01 sec)







mysql> select employee\\\_id, firstname, lastname, department, job\\\_id from employees where city = "Toronto";



+-------------+-----------+----------+------------+--------+



| employee\\\_id | firstname | lastname | department | job\\\_id |



+-------------+-----------+----------+------------+--------+



|           2 | Preet     | Patel    | FS         |    102 |



|           5 | Vraj      | Patel    | PHP        |    105 |



+-------------+-----------+----------+------------+--------+



2 rows in set (0.00 sec)







**\*\*8. write a SQL query to find those employees whose salary is lower than that of employees whose job title is "MK\\\\\\\_MAN". Exclude employees of the Job title ‘MK\\\\\\\\\\\\\\\_MAN’. Return employee ID, first name, last name, job ID.\\\*\\\*\*\***







mysql> create table mrf(employee\\\_id int primary key auto\\\_increment, first\\\_name varchar(50), last\\\_name varchar(50), job\\\_id varchar(50), salary decimal(10,2));



Query OK, 0 rows affected (0.14 sec)







mysql> describe mrf;



+-------------+---------------+------+-----+---------+----------------+



| Field       | Type          | Null | Key | Default | Extra          |



+-------------+---------------+------+-----+---------+----------------+



| employee\\\_id | int           | NO   | PRI | NULL    | auto\\\_increment |



| first\\\_name  | varchar(50)   | YES  |     | NULL    |                |



| last\\\_name   | varchar(50)   | YES  |     | NULL    |                |



| job\\\_id      | varchar(50)   | YES  |     | NULL    |                |



| salary      | decimal(10,2) | YES  |     | NULL    |                |



+-------------+---------------+------+-----+---------+----------------+



5 rows in set (0.03 sec)







mysql> insert into mrf values(01, "Amit", "Shah", "RK\\\_ACC", 50000);



Query OK, 1 row affected (0.02 sec)







mysql> insert into mrf values("Neha", "Patel", "MK\\\_MAN", 70000);



ERROR 1136 (21S01): Column count doesn't match value count at row 1



mysql> insert into mrf values(02, "Neha", "Patel", "MK\\\_MAN", 70000);



Query OK, 1 row affected (0.01 sec)







mysql> insert into mrf values(03, "Rahul", "Patil", "HR\\\_IT", 45000);



Query OK, 1 row affected (0.01 sec)







mysql> insert into mrf values(04, "Priya", "Verma", "RK\\\_ACC", 60000);



Query OK, 1 row affected (0.01 sec)







mysql> insert into mrf values(05, "karan", "Singh", "MK\\\_MAN", 80000);



Query OK, 1 row affected (0.01 sec)







mysql> insert into mrf values(06, "Riya", "Rao", "FR\\\_SAN", 48000);



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from mrf;



+-------------+------------+-----------+--------+----------+



| employee\\\_id | first\\\_name | last\\\_name | job\\\_id | salary   |



+-------------+------------+-----------+--------+----------+



|           1 | Amit       | Shah      | RK\\\_ACC | 50000.00 |



|           2 | Neha       | Patel     | MK\\\_MAN | 70000.00 |



|           3 | Rahul      | Patil     | HR\\\_IT  | 45000.00 |



|           4 | Priya      | Verma     | RK\\\_ACC | 60000.00 |



|           5 | karan      | Singh     | MK\\\_MAN | 80000.00 |



|           6 | Riya       | Rao       | FR\\\_SAN | 48000.00 |



+-------------+------------+-----------+--------+----------+



6 rows in set (0.00 sec)







mysql> select employee\\\_id,first\\\_name,last\\\_name,job\\\_id from mrf where salary < job\\\_id = "MK\\\_MAN";



+-------------+------------+-----------+--------+



| employee\\\_id | first\\\_name | last\\\_name | job\\\_id |



+-------------+------------+-----------+--------+



|           1 | Amit       | Shah      | RK\\\_ACC |



|           2 | Neha       | Patel     | MK\\\_MAN |



|           3 | Rahul      | Patil     | HR\\\_IT  |



|           4 | Priya      | Verma     | RK\\\_ACC |



|           5 | karan      | Singh     | MK\\\_MAN |



|           6 | Riya       | Rao       | FR\\\_SAN |



+-------------+------------+-----------+--------+



6 rows in set, 7 warnings (0.01 sec)







**\*\*9. write a SQL query to find all those employees who work in department ID 80 or 40. Return first name, last name, department number and department name.\*\***







mysql> create table ASS(department\\\_number int primary key auto\\\_increment, firstname varchar(50), lastname varchar(50),department\\\_name varchar(50), department\\\_id int);



Query OK, 0 rows affected (0.03 sec)







mysql> describe ASS;



+-------------------+-------------+------+-----+---------+----------------+



| Field             | Type        | Null | Key | Default | Extra          |



+-------------------+-------------+------+-----+---------+----------------+



| department\\\_number | int         | NO   | PRI | NULL    | auto\\\_increment |



| firstname         | varchar(50) | YES  |     | NULL    |                |



| lastname          | varchar(50) | YES  |     | NULL    |                |



| department\\\_name   | varchar(50) | YES  |     | NULL    |                |



| department\\\_id     | int         | YES  |     | NULL    |                |



+-------------------+-------------+------+-----+---------+----------------+



5 rows in set (0.01 sec)







mysql\\\*\\\*>\\\*\\\* insert into ASS(firstname, lastname, department\\\_name, department\\\_id) values



    -> ("Kirtan", "Parmar", "DS", 80),



    -> ("Sappy", "bawa", "FS", 20),



    -> ("Raj", "Shah", "IT", 40),



    -> ("Sneha", "Reddy", "DA", 80),



    -> ("Harshil", "Parmar", "TT", 40),



    -> ("Rishi", "Patel", "DS", 10);



Query OK, 6 rows affected (0.02 sec)



Records: 6  Duplicates: 0  Warnings: 0







mysql> describe ASS;



+-------------------+-------------+------+-----+---------+----------------+



| Field             | Type        | Null | Key | Default | Extra          |



+-------------------+-------------+------+-----+---------+----------------+



| department\\\_number | int         | NO   | PRI | NULL    | auto\\\_increment |



| firstname         | varchar(50) | YES  |     | NULL    |                |



| lastname          | varchar(50) | YES  |     | NULL    |                |



| department\\\_name   | varchar(50) | YES  |     | NULL    |                |



| department\\\_id     | int         | YES  |     | NULL    |                |



+-------------------+-------------+------+-----+---------+----------------+



5 rows in set (0.01 sec)







mysql> select \\\* from ASS;



+-------------------+-----------+----------+-----------------+---------------+



| department\\\_number | firstname | lastname | department\\\_name | department\\\_id |



+-------------------+-----------+----------+-----------------+---------------+



|                 1 | Kirtan    | Parmar   | DS              |            80 |



|                 2 | Sappy     | bawa     | FS              |            20 |



|                 3 | Raj       | Shah     | IT              |            40 |



|                 4 | Sneha     | Reddy    | DA              |            80 |



|                 5 | Harshil   | Parmar   | TT              |            40 |



|                 6 | Rishi     | Patel    | DS              |            10 |



+-------------------+-----------+----------+-----------------+---------------+



6 rows in set (0.00 sec)







mysql> select department\\\_number, firstname, lastname, department\\\_name from ASS where department\\\_id = 80;



+-------------------+-----------+----------+-----------------+



| department\\\_number | firstname | lastname | department\\\_name |



+-------------------+-----------+----------+-----------------+



|                 1 | Kirtan    | Parmar   | DS              |



|                 4 | Sneha     | Reddy    | DA              |



+-------------------+-----------+----------+-----------------+



2 rows in set (0.00 sec)







mysql> select department\\\_number, firstname, lastname, department\\\_name from ASS where department\\\_id = 40;



+-------------------+-----------+----------+-----------------+



| department\\\_number | firstname | lastname | department\\\_name |



+-------------------+-----------+----------+-----------------+



|                 3 | Raj       | Shah     | IT              |



|                 5 | Harshil   | Parmar   | TT              |



+-------------------+-----------+----------+-----------------+



2 rows in set (0.00 sec)







**\*\*10.write a SQL query to calculate the average salary, the number of employees receiving commissions in that department. Return department name, average salary and number of employees.\*\***







mysql> create table commision(emp\\\_id int primary key auto\\\_increment, name varchar(50), department varchar(50), salary decimal(10,2), commision\\\_percentage decimal(10,2));



Query OK, 0 rows affected (0.09 sec)







mysql> describe commision;



+----------------------+---------------+------+-----+---------+----------------+



| Field                | Type          | Null | Key | Default | Extra          |



+----------------------+---------------+------+-----+---------+----------------+



| emp\\\_id               | int           | NO   | PRI | NULL    | auto\\\_increment |



| name                 | varchar(50)   | YES  |     | NULL    |                |



| department           | varchar(50)   | YES  |     | NULL    |                |



| salary               | decimal(10,2) | YES  |     | NULL    |                |



| commision\\\_percentage | decimal(10,2) | YES  |     | NULL    |                |



+----------------------+---------------+------+-----+---------+----------------+



5 rows in set (0.02 sec)







mysql> insert into commision(name, department, salary, commision\\\_percentage) values



\&nbsp;   -> ("Kirtan", "IT", 99500, null);



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from commision;



+--------+--------+------------+----------+----------------------+



| emp\\\_id | name   | department | salary   | commision\\\_percentage |



+--------+--------+------------+----------+----------------------+



|      1 | Kirtan | IT         | 99500.00 |                 NULL |



+--------+--------+------------+----------+----------------------+



1 row in set (0.00 sec)







mysql> insert into commision(name, department, salary, commision\\\_percentage) values



\&nbsp;   -> ("Preet", "FS", 50000, 0.10),



\&nbsp;   -> ("Vraj", "PHP", 35500, null);



Query OK, 2 rows affected (0.01 sec)



Records: 2  Duplicates: 0  Warnings: 0











mysql> insert into commision(name, department, salary, commision\\\_percentage) values



\&nbsp;   -> ("Pritesh", "DS", 30000, null),



\&nbsp;   -> ("Rishi", "DA", 25000, 0.15),



\&nbsp;   -> ("Ajay", "DS", 45000, null),



\&nbsp;   -> ("Arav", "IT", 40000, 0.25);



Query OK, 4 rows affected (0.01 sec)



Records: 4  Duplicates: 0  Warnings: 0







mysql>  select avg(salary) as Average\\\_Salary from commision;



+----------------+



| Average\\\_Salary |



+----------------+



|   46428.571429 |



+----------------+



1 row in set (0.01 sec)







mysql> select count(commision\\\_percentage) as Employees\\\_with\\\_commision from commision;



+--------------------------+



| Employees\\\_with\\\_commision |



+--------------------------+



|                        3 |



+--------------------------+



1 row in set (0.00 sec)







mysql> select department, avg(salary) as Average\\\_Salary, count(commision\\\_percentage) as employees\\\_with\\\_commision from commision group by department;



+------------+----------------+--------------------------+



| department | Average\\\_Salary | employees\\\_with\\\_commision |



+------------+----------------+--------------------------+



| IT         |   69750.000000 |                        1 |



| FS         |   50000.000000 |                        1 |



| PHP        |   35500.000000 |                        0 |



| DS         |   37500.000000 |                        0 |



| DA         |   25000.000000 |                        1 |



+------------+----------------+--------------------------+



5 rows in set (0.01 sec)







**\*\*11.write a SQL query to find out which employees have the same designations the employee whose ID is 169. Return first name, last name, department ID and job\\\_ID.\*\***











mysql> create table kp(emp\\\_id int primary key, firstname varchar(50), lastname varchar(50), department\\\_id int, job\\\_id varchar(50));



Query OK, 0 rows affected (0.09 sec)







mysql> describe kp;



+---------------+-------------+------+-----+---------+-------+



| Field         | Type        | Null | Key | Default | Extra |



+---------------+-------------+------+-----+---------+-------+



| emp\\\_id        | int         | NO   | PRI | NULL    |       |



| firstname     | varchar(50) | YES  |     | NULL    |       |



| lastname      | varchar(50) | YES  |     | NULL    |       |



| department\\\_id | int         | YES  |     | NULL    |       |



| job\\\_id        | varchar(50) | YES  |     | NULL    |       |



+---------------+-------------+------+-----+---------+-------+



5 rows in set (0.01 sec)







mysql> insert into kp(emp\\\_id, firstname, lastname, department\\\_id, job\\\_id) values



\&nbsp;   -> (165, "Kirtan", "Parmar", 10, "IT\\\_MAC");



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from kp;



+--------+-----------+----------+---------------+--------+



| emp\\\_id | firstname | lastname | department\\\_id | job\\\_id |



+--------+-----------+----------+---------------+--------+



|    165 | Kirtan    | Parmar   |            10 | IT\\\_MAC |



+--------+-----------+----------+---------------+--------+



1 row in set (0.00 sec)







mysql> insert into kp(emp\\\_id, firstname, lastname, department\\\_id, job\\\_id) values



\&nbsp;   -> (166, "Riya", "Desai", 20, "HR\\\_MAN"),



\&nbsp;   -> (167, "Neha", "Mehta", 10, "IT\\\_MAC"),



\&nbsp;   -> (168, "Rahul", "Verma", 20, "HR\\\_MAN"),



\&nbsp;   -> (169, "Pooja", "Patel", 10, "IT\\\_MAC"),



\&nbsp;   -> (170, "Kiya", "Parmar", 20, "HR\\\_MAN");



Query OK, 5 rows affected (0.01 sec)



Records: 5  Duplicates: 0  Warnings: 0







mysql> select \\\* from kp;



+--------+-----------+----------+---------------+--------+



| emp\\\_id | firstname | lastname | department\\\_id | job\\\_id |



+--------+-----------+----------+---------------+--------+



|    165 | Kirtan    | Parmar   |            10 | IT\\\_MAC |



|    166 | Riya      | Desai    |            20 | HR\\\_MAN |



|    167 | Neha      | Mehta    |            10 | IT\\\_MAC |



|    168 | Rahul     | Verma    |            20 | HR\\\_MAN |



|    169 | Pooja     | Patel    |            10 | IT\\\_MAC |



|    170 | Kiya      | Parmar   |            20 | HR\\\_MAN |



+--------+-----------+----------+---------------+--------+



6 rows in set (0.00 sec)







mysql> select firstname, lastname, department\\\_id, job\\\_id from kp where emp\\\_id = 169;



+-----------+----------+---------------+--------+



| firstname | lastname | department\\\_id | job\\\_id |



+-----------+----------+---------------+--------+



| Pooja     | Patel    |            10 | IT\\\_MAC |



+-----------+----------+---------------+--------+



1 row in set (0.00 sec)







**\*\*12.write a SQL query to find those employees who earn more than the average salary. Return employee ID, first name, last name\*\***







mysql> create table employee(emp\\\_id int primary key auto\\\_increment, first\\\_name varchar(100), last\\\_name varchar(100), salary decimal(10, 2));



Query OK, 0 rows affected (0.03 sec)







mysql> describe employee;



+------------+---------------+------+-----+---------+----------------+



| Field      | Type          | Null | Key | Default | Extra          |



+------------+---------------+------+-----+---------+----------------+



| emp\\\_id     | int           | NO   | PRI | NULL    | auto\\\_increment |



| first\\\_name | varchar(100)  | YES  |     | NULL    |                |



| last\\\_name  | varchar(100)  | YES  |     | NULL    |                |



| salary     | decimal(10,2) | YES  |     | NULL    |                |



+------------+---------------+------+-----+---------+----------------+



4 rows in set (0.00 sec)







mysql> insert into values(101, "Kirtan", "Parmar", 85550.50);



ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'values(101, "Kirtan", "Parmar", 85550.50)' at line 1



mysql> insert into employee values(101, "Kirtan", "Parmar", 85550.50);



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from employee;



+--------+------------+-----------+----------+



| emp\\\_id | first\\\_name | last\\\_name | salary   |



+--------+------------+-----------+----------+



|    101 | Kirtan     | Parmar    | 85550.50 |



+--------+------------+-----------+----------+



1 row in set (0.00 sec)







mysql> insert into employee values("Priyank", "Parmar", 45000.00);



ERROR 1136 (21S01): Column count doesn't match value count at row 1



mysql> insert into employee values(102, "Priyank", "Parmar", 45000.00);



Query OK, 1 row affected (0.01 sec)







mysql> insert into employee values(103, "Ajay", "Shah", 50000.20);



Query OK, 1 row affected (0.01 sec)







mysql> insert into employee values(103, "Abhishek", "Kumar", 25000.70);



ERROR 1062 (23000): Duplicate entry '103' for key 'employee.PRIMARY'



mysql> insert into employee values(104, "Abhishek", "Kumar", 25000.70);



Query OK, 1 row affected (0.01 sec)







mysql> insert into employee values(105, "Madhav", "Patel", 52000.80);



Query OK, 1 row affected (0.01 sec)







mysql> select \\\* from employee;



+--------+------------+-----------+----------+



| emp\\\_id | first\\\_name | last\\\_name | salary   |



+--------+------------+-----------+----------+



|    101 | Kirtan     | Parmar    | 85550.50 |



|    102 | Priyank    | Parmar    | 45000.00 |



|    103 | Ajay       | Shah      | 50000.20 |



|    104 | Abhishek   | Kumar     | 25000.70 |



|    105 | Madhav     | Patel     | 52000.80 |



+--------+------------+-----------+----------+



5 rows in set (0.00 sec)







mysql> select avg(salary) as Average\\\_Salary from employee;



+----------------+



| Average\\\_Salary |



+----------------+



|   51510.440000 |



+----------------+



1 row in set (0.01 sec)







mysql> select emp\\\_id, first\\\_name, last\\\_name from employee where salary > (select avg(salary) from employee);



+--------+------------+-----------+



| emp\\\_id | first\\\_name | last\\\_name |



+--------+------------+-----------+



|    101 | Kirtan     | Parmar    |



|    105 | Madhav     | Patel     |



+--------+------------+-----------+



2 rows in set (0.01 sec)











**\*\*13.write a SQL query to find all those employees who work in the Finance department. Return department ID, name (first), job ID and department name.\*\***











mysql> create table kgf(department\\\_id int primary key auto\\\_increment, name varchar(50), job\\\_id int, department\\\_name varchar(50));



Query OK, 0 rows affected (0.03 sec)







mysql> describe kgf;



+-----------------+-------------+------+-----+---------+----------------+



| Field           | Type        | Null | Key | Default | Extra          |



+-----------------+-------------+------+-----+---------+----------------+



| department\\\_id   | int         | NO   | PRI | NULL    | auto\\\_increment |



| name            | varchar(50) | YES  |     | NULL    |                |



| job\\\_id          | int         | YES  |     | NULL    |                |



| department\\\_name | varchar(50) | YES  |     | NULL    |                |



+-----------------+-------------+------+-----+---------+----------------+



4 rows in set (0.00 sec)







mysql> insert into kgf(name, job\\\_id, department\\\_name) values



\&nbsp;   -> ("Karan", 101, "Finance"),



\&nbsp;   -> ("Raj", 102, "HR"),



\&nbsp;   -> ("Yash", 103, "IT"),



\&nbsp;   -> ("sonu", 104, "sales");



Query OK, 4 rows affected (0.01 sec)



Records: 4  Duplicates: 0  Warnings: 0







mysql> select \\\* from kgf;



+---------------+-------+--------+-----------------+



| department\\\_id | name  | job\\\_id | department\\\_name |



+---------------+-------+--------+-----------------+



|             1 | Karan |    101 | Finance         |



|             2 | Raj   |    102 | HR              |



|             3 | Yash  |    103 | IT              |



|             4 | sonu  |    104 | sales           |



+---------------+-------+--------+-----------------+



4 rows in set (0.00 sec)







mysql> select department\\\_id, name, job\\\_id from kgf where department\\\_name = "Finance";



+---------------+-------+--------+



| department\\\_id | name  | job\\\_id |



+---------------+-------+--------+



|             1 | Karan |    101 |



+---------------+-------+--------+



1 row in set (0.00 sec)











**\*\*14. From the following table, write a SQL query to find the employees who earn less than the employee of ID 182. Return first name, last name and salary.\*\***







mysql> create table emp(emp\\\_id int primary key, firstname varchar(50), lastname varchar(50), salary decimal(10,2));



Query OK, 0 rows affected (0.05 sec)







mysql> describe emp;



+-----------+---------------+------+-----+---------+-------+



| Field     | Type          | Null | Key | Default | Extra |



+-----------+---------------+------+-----+---------+-------+



| emp\\\_id    | int           | NO   | PRI | NULL    |       |



| firstname | varchar(50)   | YES  |     | NULL    |       |



| lastname  | varchar(50)   | YES  |     | NULL    |       |



| salary    | decimal(10,2) | YES  |     | NULL    |       |



+-----------+---------------+------+-----+---------+-------+



4 rows in set (0.01 sec)







mysql> insert into emp(emp\\\_id, firstname, lastname, salary) values



\&nbsp;   -> (181, "Vrunda", "Parmar", 54000),



\&nbsp;   -> (182, "Heer", "Patel", 60500.10),



\&nbsp;   -> (183, "Charmi", "Patel", 50000),



\&nbsp;   -> (184, "Dhruvi", "Verma", 40000.20),



\&nbsp;   -> (185, "Annu", "Mehta", 35000);



Query OK, 5 rows affected (0.01 sec)



Records: 5  Duplicates: 0  Warnings: 0







mysql> select \\\* from emp;



+--------+-----------+----------+----------+



| emp\\\_id | firstname | lastname | salary   |



+--------+-----------+----------+----------+



|    181 | Vrunda    | Parmar   | 54000.00 |



|    182 | Heer      | Patel    | 60500.10 |



|    183 | Charmi    | Patel    | 50000.00 |



|    184 | Dhruvi    | Verma    | 40000.20 |



|    185 | Annu      | Mehta    | 35000.00 |



+--------+-----------+----------+----------+



5 rows in set (0.00 sec)







mysql> select salary from emp where emp\\\_id = 182;



+----------+



| salary   |



+----------+



| 60500.10 |



+----------+



1 row in set (0.00 sec)







mysql> select firstname, lastname, salary from emp where salary <



\&nbsp;   -> (select salary from emp where emp\\\_id = 182);



+-----------+----------+----------+



| firstname | lastname | salary   |



+-----------+----------+----------+



| Vrunda    | Parmar   | 54000.00 |



| Charmi    | Patel    | 50000.00 |



| Dhruvi    | Verma    | 40000.20 |



| Annu      | Mehta    | 35000.00 |



+-----------+----------+----------+



4 rows in set (0.01 sec)







mysql> select firstname, lastname, salary from emp where salary >



\&nbsp;   -> (select salary from emp where emp\\\_id = 183);



+-----------+----------+----------+



| firstname | lastname | salary   |



+-----------+----------+----------+



| Vrunda    | Parmar   | 54000.00 |



| Heer      | Patel    | 60500.10 |



+-----------+----------+----------+



2 rows in set (0.00 sec)





















