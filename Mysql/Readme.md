# What is MySQL
MySQL is a popular open-source relational database management system (RDBMS). It is used to manage databases, including tasks such as storing, retrieving, updating, and deleting data. MySQL is a powerful, reliable, and scalable database system that is used in many applications and websites.

### MySQL Installation Steps

```sql
wget https://dev.mysql.com/get/mysql-apt-config_0.8.29-1_all.deb
```

```sql
apt install ./mysql-apt-config_0.8.29-1_all.deb
```

```sql
apt update
```

```sql
apt install mysql-community-server
```

```sql
systemctl restart mysql.service
```

#### Root User Password Command

```sql
mysql_secure_installation
```

#### Login Mysql

```sql
mysql -u root -p
```

## Mysql Databases Command

This command is used to display a list of all databases on the MySQL server.
```sql
SHOW DATABASES;
```

This command is used to create a new database with the specified name.
```sql
CREATE DATABASE database_name;
```

This command is used to switch to the specified database, making it the current active database for subsequent operations.
```sql
USE database_name;
```

This command is used to delete a database and all its associated tables and data. It's important to exercise caution when using this command as it permanently removes the database and its contents.
```sql
DROP DATABASE database_name;
```

 This command is used to display a list of all tables in the currently selected database.
```sql
SHOW TABLES;
```

This command is used to create a new table named "user" with columns for id, name, email, password, and enable. Each column has a specified data type (int, varchar) and maximum length (50 characters).
```sql
CREATE TABLE user (id int, name varchar(50), email varchar(50), password varchar(50), enable INT(1));
```

This command is used to describe the structure of the "user" table, displaying information about its columns, data types, and any constraints.
```sql
DESC user;
```

This command is used to delete the "user" table from the database.
```sql
DROP TABLE user;
```

This command is used to retrieve all rows and columns from the "user" table, effectively selecting all data stored in the table.
```sql
SELECT * FROM user;
```

## SQL INSERT (Create)

This command is used to insert a new row of data into the "user" table. It specifies values for each column (id, name, age, email, password, enable) for the new row being inserted. In this example, a user with an id of 1, name "admin", age 20, email "admin@gmail.com", password "password123", and enable status of 1 is being inserted into the table.
```sql
INSERT INTO user(id,name,age,email,password,enable) VALUES(1,'admin',20,'admin@gmail.com','password123',1);
```

This command is used to create a new table named "user2". It defines several columns (id, name, age, email, password, course_name, enable) along with their data types and constraints:

- id: An auto-incrementing integer field which serves as the primary key for the table.
- name: A varchar field which stores the name of the user.
- age: An integer field which stores the age of the user. It includes a constraint (CHECK (age >= 16)) to ensure that the age is at least 16.
- email: A varchar field which stores the email address of the user. It has a unique constraint to ensure that each email is unique in the table.
- password: A varchar field which stores the password of the user.
- course_name: A varchar field which stores the name of the course. It has a default value of "IT Security".
- enable: An integer field indicating whether the user is enabled or disabled.

The PRIMARY KEY (id) statement specifies that the "id" column serves as the primary key for the table, uniquely identifying each row.
```sql
CREATE TABLE user2(id INT(11) NOT NULL AUTO_INCREMENT, name VARCHAR(255) NOT NULL, age INT NOT NULL CHECK (age >= 16), email VARCHAR(255) NOT NULL UNIQUE, password VARCHAR(255) NOT NULL, course_name VARCHAR(255) NOT NULL DEFAULT "IT Security", enable INT(1) NOT NULL, PRIMARY KEY (id));
```

## SQL SELECT (Read)

This query selects all columns from the "user2" table, effectively retrieving all rows and all columns of data stored in the table.
```sql
SELECT * FROM user2;
```

This query selects only the "id" and "name" columns from the "user2" table. It retrieves all rows, but only includes data from the specified columns.
```sql
SELECT id,name FROM user2;
```
This query selects specific columns from the "user2" table: "id", "name", and "email". It also uses aliases to rename the columns in the result set:

- "id" column is aliased as "ID".
- "name" column is aliased as "student name".
- "email" column is aliased as "Email ADD".
```sql
SELECT id AS ID,name AS "student name",email AS "Email ADD" FROM user2;
```

### SQL Comparison Operator

| Operator | Description                                 | Operates on             |
|----------|---------------------------------------------|-------------------------|
| =        | Equal to                                    | Any compatible data types |
| >        | Greater than                                | Any compatible data types |
| <        | Less than                                   | Any compatible data types |
| >=       | Greater than or equal to                    | Any compatible data types |
| <=       | Less than or equal to                       | Any compatible data types |
| <> Or != | Not equal to                                | Any compatible data types |
| BETWEEN  | Between a certain range                     | Any compatible data types |
| LIKE     | Search for a pattern                        | Any compatible data types |
| IN       | To specify multiple possible values for a column | Any compatible data types |


This query selects all columns from the "user2" table where the "id" column is equal to 1.
```sql
select * from user2 where id=1;
```

This query selects all columns from the "user2" table where the "id" column is greater than 1.
```sql		
select * from user2 where id>1;
```

This query selects all columns from the "user2" table where the "id" column is less than 3.
```sql		
select * from user2 where id<3;
```

This query selects all columns from the "user2" table where the "id" column is greater than or equal to 3.
```sql			
select * from user2 where id>=3;
```

This query selects all columns from the "user2" table where the "id" column is less than or equal to 3.
```sql
select * from user2 where id<=3;
```

This query selects all columns from the "user2" table where the "id" column is not equal to 3. The <> operator is the same as the != operator and means "not equal to".
```sql	
select * from user2 where id<>3;
```

This query selects all columns from the "user2" table where the "id" column is not equal to 1.
```sql
select * from user2 where id!=1;
```


### AND Operator

This SQL query selects the "id" and "name" columns from the "user2" table where the value in the "age" column is greater than 20 and the value in the "enable" column is equal to 1.

Here's the breakdown:

- SELECT id, name: Specifies the columns to be selected from the table.
- FROM user2: Specifies the table from which to select the data.
- WHERE age > 20: Specifies a condition where the value in the "age" column must be greater than 20.
- AND enable=1: Specifies an additional condition where the value in the "enable" column must be equal to 1.

This query will retrieve rows where both conditions are true, meaning the age is greater than 20 and the user is enabled.
```sql
SELECT id,name FROM user2 WHERE age > 20 AND enable=1;
```

### OR Operator
This SQL query selects all columns from the "user2" table where either of the two conditions is met:

- The value in the "age" column is less than 20.
- The value in the "enable" column is equal to 1.
Here's the breakdown:

- SELECT *: Specifies that all columns should be selected from the table.
- FROM user2: Specifies the table from which to select the data.
- WHERE age < 20 OR enable = 1: Specifies the conditions for selecting rows:
    - age < 20: This condition selects rows where the value in the "age" column is less than 20.
    - OR: This logical operator means that if either condition before or after it is true, the row will be selected.
    - enable = 1: This condition selects rows where the value in the "enable" column is equal to 1.

This query will retrieve rows where either the age is less than 20 or the user is enabled.
```sql
SELECT * FROM user2 WHERE age < 20 OR enable = 1;
```

### NOT Operator

This SQL query selects all columns from the "user2" table where the value in the "enable" column is not equal to 1.

Here's the breakdown:

- SELECT *: Specifies that all columns should be selected from the table.
- FROM user2: Specifies the table from which to select the data.
- WHERE NOT enable = 1: Specifies the condition for selecting rows:
    - NOT: This logical operator negates the condition that follows it.
    - enable = 1: This condition selects rows where the value in the "enable" column is equal to 1.

Therefore, the NOT enable = 1 condition selects rows where the value in the "enable" column is not equal to 1. In other words, it selects rows where the user is disabled (if "enable" column represents user status, where 1 typically means enabled and 0 means disabled).
```sql
SELECT * FROM user2 WHERE NOT enable = 1;
```

### IN Operator

This SQL query selects all columns from the "user2" table where the value in the "id" column is either 5 or 6.

Here's the breakdown:

- SELECT *: Specifies that all columns should be selected from the table.
- FROM user2: Specifies the table from which to select the data.
- WHERE id IN (5,6): Specifies the condition for selecting rows:
    - id: Refers to the "id" column.
    - IN (5,6): This condition selects rows where the value in the "id" column matches any of the values listed within the parentheses (5 or 6 in this case).

Therefore, this query will retrieve rows where the "id" is either 5 or 6.
```sql
SELECT * FROM user2 WHERE id IN (5,6);
```

### BETWEEN Operator

This query selects all columns from the "user2" table where the value in the "id" column falls within the range from 3 to 6 (inclusive). It retrieves rows where the "id" is 3, 4, 5, or 6.
```sql
SELECT * FROM user2 WHERE id BETWEEN 3 AND 6;
```

This query selects all columns from the "user2" table where the value in the "id" column falls outside the range from 3 to 6 (exclusive). It retrieves rows where the "id" is less than 3 or greater than 6.
```sql
SELECT * FROM user2 WHERE id NOT BETWEEN 3 AND 6;
```

This query selects all columns from the "user2" table where the value in the "name" column falls within the alphabetical range from "a" to "u" (inclusive). It retrieves rows where the "name" begins with any letter between "a" and "u", inclusive of "a" and "u". Keep in mind that alphabetical ordering in SQL is case insensitive, so both uppercase and lowercase letters are considered.
```sql
SELECT * FROM user2 WHERE name BETWEEN "a" AND "u";
```

### LIKE Operator

| Pattern   | Description                               |
|-----------|-------------------------------------------|
| LIKE 'a%' | Start with "a"                            |
| LIKE '%a' | End with "a"                              |
| LIKE '%ai%'| Have "ai" in any position                 |
| LIKE 'a%i'| Start with "a" and end with "i"           |
| LIKE '_r%' | "r" in the second position                |
| LIKE '__m%'| "m" in the third position                 |
| LIKE '_rm' | "r" in the second and "m" in the third position |

This query selects all columns from the "user2" table where the value in the "name" column starts with the letter "u".
```sql
select * from user2 where name LIKE "u%";
```

This query selects all columns from the "user2" table where the value in the "name" column ends with the letter "n".
```sql		
select * from user2 where name LIKE "%n";
```

This query selects all columns from the "user2" table where the value in the "name" column:

- Starts with any single character (represented by the underscore _).
- Followed by the letter "a".
- Followed by any number of characters.
```sql	
select * from user2 where name LIKE "_a%";
```

This query selects all columns from the "user2" table where the value in the "name" column:

- Starts with any two characters.
- Followed by the letter "a".
- Followed by any number of characters.

The % symbol in the LIKE clause is a wildcard that matches zero or more characters. The _ symbol matches exactly one character. Therefore, "_%" matches any single character followed by "_", while "__%" matches any two characters followed by any number of characters.
```sql		
select * from user2 where name LIKE "__a%";
```

### Regular Expression

| Pattern | What the pattern matches                            |
|---------|----------------------------------------------------|
| ^       | Beginning of string                                 |
| $       | End of string                                       |
| .       | Any single character                                |
| [...]   | Any character listed between the square brackets    |
| [^...]  | Any character not listed between the square brackets |
| p1\|p2\|p3 | Alternation; matches any of the patterns p1, p2, or p3 |
| *       | Zero or more instances of preceding element         |
| +       | One or more instances of preceding element          |
| {n}     | n instances of preceding element                    |
| {m,n}   | m through n instances of preceding element          |


This query selects all columns from the "user2" table where the value in the "name" column matches the regular expression "ad".
```sql
select * from user2 WHERE name REGEXP "ad";						
```

This query selects all columns from the "user2" table where the value in the "name" column starts with the letter "a".
```sql
select * from user2 WHERE name REGEXP "^a";
```

This query selects all columns from the "user2" table where the value in the "name" column ends with the digit "1".
```sql
select * from user2 WHERE name REGEXP "1$";							
```

This query selects all columns from the "user2" table where the value in the "name" column contains zero or more occurrences of the letter "a".
```sql
select * from user2 WHERE name REGEXP "a*";
```

This query selects all columns from the "user2" table where the value in the "name" column matches "admin", "user", or "rahul".
```sql
select * from user2 WHERE name REGEXP "admin|user|rahul";
```

This query selects all columns from the "user2" table where the value in the "name" column ends with a digit (0-9).
```sql
select * from user2 WHERE name REGEXP "[0-9]$";				
```

This query selects all columns from the "user2" table where the value in the "name" column contains the letter "u" or ends with a digit (0-9).
```sql
select * from user2 WHERE name REGEXP "u|[0-9]$ ";
```
This query selects all columns from the "user2" table where the value in the "name" column contains one or more occurrences of the letter "a" followed by the letter "d"
```sql
select * from user2 WHERE name REGEXP "a+d";		
```

This query sorts the result set of the "user2" table by the "age" column in ascending order.
```sql
select * from user2 ORDER by age;			
```

This query sorts the result set of the "user2" table by the "name" column in ascending order.
```sql
select * from user2 ORDER by name;
```

This query sorts the result set of the "user2" table by the "name" column in descending order.
```sql						 		
select * from user2 ORDER by name DESC;								 
```

This query sorts the result set of the "user2" table by the "age" column in descending order.
```	sql		
select * from user2 ORDER by age DESC;								 
```

This query sorts the result set of the "user2" table by the "age" column in ascending order.
```sql	
select * from user2 ORDER by age ASC;										
```

This query selects distinct values from the "name" column of the "user2" table, removing duplicates.
```	sql	
select DISTINCT name from user2;							  			
```

This query selects the first 3 rows from the "user2" table.
```	sql			
select * from user2 LIMIT 3;											 
```

This query selects the first 3 rows from the "user2" table, starting from offset 0 (the first row)
```	sql		
select * from user2 LIMIT 0,3;								
```

This query selects 3 rows from the "user2" table, starting from offset 2 (the third row).
```sql		
select * from user2 LIMIT 2,3;									
```

This query selects 2 rows from the "user2" table, starting from offset 2 (the third row).
```sql
select * from user2 LIMIT 2,2;									
```

This query counts the number of rows in the "user2" table.
```sql		
select COUNT(id) from user2;										
```

This query calculates the sum of the values in the "id" column of the "user2" table.
```sql		
select SUM(id) from user2;											
```

This query retrieves the maximum value in the "id" column of the "user2" table.
```sql		
select MAX(id) from user2;											
```

This query retrieves the minimum value in the "id" column of the "user2" table.
```sql		
select MIN(id) from user2;												
```

This query calculates the average value in the "id" column of the "user2" table.
```sql		
select AVG(id) from user2;
```

## SQL UPDATE 

This SQL query updates the "age" column in the "user2" table. It sets the age to '55' for the row where the value in the "id" column is equal to 1.

Here's the breakdown:

- UPDATE user2: Specifies the table to be updated.
- SET age = '55': Specifies the column to be updated ("age") and the new value to be assigned ('55').
- WHERE id = 1: Specifies the condition to identify the row(s) to be updated. In this case, it updates only the row where the value in the "id" column is equal to 1.
```sql
UPDATE user2 SET age = '55' WHERE id =1;
```

## SQL DELETE 

This query deletes all rows from the "user2" table, effectively removing all data from the table.
```sql
DELETE from user2;
```

This query deletes rows from the "users" table where the value in the "id" column is equal to 6.
```sql
DELETE from users WHERE id = 6;
```

This query deletes rows from the "users" table where the value in the "id" column matches any of the values specified within the parentheses (5 or 8 in this case).
```sql
DELETE from users WHERE id IN (5,8);
```

## ALTER TABLE
						
- Add Column in a TABLE
									 									
- Changing Data Type of a column
									 									
- Change Column Name 
									 								
- Adding Constaints to a column
									 			
- Changing Column Position 
									 								
- Delete Column

- Renaming Tables

This query adds a new column named "enable" to the "user3" table with the data type INT(1). The column is initially allowed to contain NULL values.
```sql									
ALTER TABLE user3 ADD enable INT(1);
```

This query modifies the "enable" column in the "user3" table to disallow NULL values.
```sql
ALTER TABLE user3 MODIFY enable INT(1) NOT NULL;
```

This query modifies the "enable" column in the "user3" table to disallow NULL values.
```sql
ALTER TABLE user3 MODIFY enable INT(1) NOT NULL AFTER email;
```

This query changes the name of the "id" column in the "user3" table to "ID" and modifies its data type to INT(1).
```sql
ALTER TABLE user3 CHANGE id ID INT(1);
```

This query removes the "enable" column from the "user3" table.
```sql
ALTER TABLE user3 DROP COLUMN enable;
```

This query renames the "user3" table to "student". After execution, the table will be known as "student" instead of "user3".
```sql
ALTER TABLE user3 RENAME student;
```									

## GROUP BY Clause

   ```sql
   SELECT name FROM users GROUP BY name;
   ```

   This query selects unique names from the "users" table. The `GROUP BY name` clause groups the rows with the same name together, and then only one row for each unique name is returned in the result set. It effectively removes duplicate names from the result.

   ```sql
   SELECT name, COUNT(name) FROM users GROUP BY name;
   ```

   This query counts the occurrences of each name in the "users" table. The `GROUP BY name` clause groups the rows with the same name together, and then the `COUNT(name)` function counts the number of occurrences of each name. The result set includes two columns: "name" and the count of occurrences for each name.

## HAVING Clause

This SQL statement selects names from the "users" table where the name is equal to "admin". The `HAVING` clause is used to filter groups returned by the `GROUP BY` clause. However, in this query, there is no explicit `GROUP BY` clause, so the `HAVING` clause is essentially functioning as a `WHERE` clause.

In summary, this query retrieves rows from the "users" table where the name column equals "admin".
```sql
select name from users HAVING name = "admin";
```

This SQL query retrieves all columns from the "users" table where the value in the "course_name" column matches the course ID associated with the course name "Information Security Expert". 

Here's the breakdown:

- The outer query `SELECT * FROM users` selects all columns from the "users" table.
- The `WHERE` clause filters the rows based on a condition.
- Inside the parentheses, there's a subquery `(SELECT course_id FROM course_name WHERE course_name = "Information Security Expert")`. This subquery retrieves the `course_id` associated with the course name "Information Security Expert".
- The outer query compares the value in the "course_name" column of the "users" table with the result of the subquery to filter the rows.
```sql
SELECT * FROM users WHERE course_name = (SELECT course_id FROM course_name WHERE course_name = "Information Security Expert");
```

## UNION and UNION ALL

UNION 

- This operator is used to combine the result sets of 2 or more SELECT statements.
											 											
- It removes duplicate rows between the various SELECT satements.
											 											
- Each SELECT statement within the UNION operator must have the same number of fields in the result sets with similar data types.
											 											
- The column in each SELECT statement must also be in the same order

This query retrieves all columns from both the "users" and "course" tables and combines the results into a single result set using the UNION operator. The UNION operator removes duplicate rows from the result set.
   ```sql
   select * from users UNION select * from course;
   ```
This query retrieves the "id" and "name" columns from the "users" table and all columns from the "course" table. The UNION operator combines the results into a single result set. However, it's important to note that the number of columns and their data types must match for each SELECT statement within the UNION operation. In this case, since the number of columns and their data types do not match between the two SELECT statements, this query would likely produce an error.
   ```sql
   select id,name from users UNION select * from course;
   ```
											
UNION ALL  
									
- This operator is used to combine the result sets of 2 or more SELECT statements.
											 											
- It returns all rows from the query and it does not remove duplicate rows between the various SELECT statements.
											 											
- Each SELECT statement within the MySQL UNION operator must have the same number of fields in the result sets with similar data types.
									 										
- The column in each SELECT statement must also be in the same order
											

 This query retrieves the "id" column from the "users" table and the "course_id" column from the "course" table. The UNION ALL operator combines the results of both queries into a single result set, including duplicate rows. Unlike UNION, UNION ALL does not remove duplicate rows from the result set.  

   ```sql
   select id from users UNION ALL select course_id from course;
   ```

## IF Clause

This query selects the "id" and "name" columns from the "users" table. It also includes a conditional statement using the `IF` function: if the value in the "city_name" column is greater than or equal to 5, it returns "T", otherwise it returns "F". The result set includes a new column named "CITY" with the result of the conditional statement.

   ```sql
   select id,name,IF(city_name >= 5, "T", "F") AS CITY from users;
   ```

This query selects the "id" column from the "users" table, and it selects the "name" column with all letters converted to uppercase using the `UPPER` function. It also selects the "email" column as it is from the "users" table.

   ```sql
   select id,UPPER(name),email from users;
   ```
This query selects the "id" column from the "users" table, and it selects the "name" column with all letters converted to lowercase using the `LOWER` function. It also selects the "email" column as it is from the "users" table.

   ```sql
   select id,LOWER(name),email from users;
   ```

This query selects the "id" and "name" columns from the "users" table. It also calculates the length of the "name" column using the `CHARACTER_LENGTH` function and renames the result as "Length". The "email" column is also selected as it is from the "users" table.

   ```sql
   select id,name,CHARACTER_LENGTH(name) AS "Length",email from users;
   ```
This query calculates the length of the "name" column using the `LENGTH` function, which counts the number of characters in the string. The result is renamed as "Length".

   ```sql
   select id,name,LENGTH(name) AS "Length",email from users;
   ```

This query returns the current date.
 
   ```sql
   select CURRENT_DATE();
   ```

This query returns the current date and time.

   ```sql
   select SYSDATE();
   ```

This query returns the current date and time, similar to `SYSDATE()`.

   ```sql
   select NOW();
   ```

This query returns the current time.

   ```sql
   select CURRENT_TIME();
   ```
This query returns the name of the currently selected database.

```sql
select database();
```
This query returns the username of the current user.

```sql
select user();
```

This query returns the hostname of the MySQL server.

```sql
select @@hostname;
```
This query returns the version of the MySQL server.

```sql
select VERSION();
```
This query returns the directory where MySQL stores its data.

```sql
select @@datadir;
```
This query pauses the execution for 20 seconds. It's often used for testing or delaying execution in scripts.   

```sql
select sleep(20);
```
