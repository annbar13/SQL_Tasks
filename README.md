# SQL_Tasks

*SQL Part 2*

## Subtask 1

**11. Incorrect surname in the customers table position 3**

UPDATE customers
SET surname = 'Miler'
WHERE customer_id = '3'

![image](https://user-images.githubusercontent.com/101512808/219773736-6d505518-5bf2-4654-a2a3-abe6d1eb30d2.png)

**12.Too much money was taken from a customer who recently bought a video with id 4. Using the join function, check the customer's name and email. In order to write him a message about the mistake of a fantastic boss.**

SELECT sale.customer_id, sale.movie_id, customers.name, customers.email, movies.price

FROM ((sale

INNER JOIN movies ON sale.movie_id = movies.movie_id)

INNER JOIN customers ON sale.customer_id = customers.customer_id)  

![image](https://user-images.githubusercontent.com/101512808/219791101-3c813ff5-f1c5-45d4-afb2-ee9c31b58e9c.png)

**13. Patrycja, a customer, does not have an e-mail address. Complete the gap by entering pati@mail.com in the appropriate field**

UPDATE customers

SET email = 'pati@mail.com'

WHERE customer_id = 4 

![image](https://user-images.githubusercontent.com/101512808/219876374-95c9116c-ada7-4e26-b8e5-bb38134c33b4.png)

**14.For each purchase, display the name of the customer who made the rental and the title of the rented movie. (use the inner join function for this, think beforehand which tables will be useful for you to perform the exercise).**

SELECT sale.customer_id, sale.movie_id, customers.name, customers.surname, customers.email, movies.title
FROM ((sale

INNER JOIN movies ON sale.movie_id = movies.movie_id)

INNER JOIN customers ON sale.customer_id = customers.customer_id)

![image](https://user-images.githubusercontent.com/101512808/220174044-118036b5-bad6-49e0-9acf-30b74b7af5f0.png)


**15. In order to anonymise the data, you want to create pseudonyms for your customers. - Add a column named 'pseudonym' to the customer table, - Fill in the column so that the nickname is made up of the first two letters of the first name and the last letter of the last name. E.g. Natalie Pilling → Nag**

ALTER TABLE customers
ADD pseudonym varchar(255);

UPDATE customers
SET pseudonym = 'Ols'
WHERE customer_id = '1'; 

UPDATE customers
SET pseudonym = 'Kal'
WHERE customer_id = '2'; 

UPDATE customers
SET pseudonym = 'Anr'
WHERE customer_id = '3';

UPDATE customers
SET pseudonym = 'Par'
WHERE customer_id = '4';

UPDATE customers
SET pseudonym = 'Mao'
WHERE customer_id = '5';

UPDATE customers
SET pseudonym = 'Nag'
WHERE customer_id = '6';

![image](https://user-images.githubusercontent.com/101512808/219882495-c23f08f5-8ec3-42a8-bca7-eaa53bbbfae6.png)

ALTER TABLE customers
ADD pseudonim varchar(255);

UPDATE customers
SET pseudonim = concat(LEFT(name,2),RIGHT(surname,1))

![image](https://user-images.githubusercontent.com/101512808/220994365-f788004d-bc9d-4f3c-b23f-c94dfb93d903.png)


**16. Display the titles of the movies that have been purchased, display the table in such a way that the titles do not repeat.**

SELECT DISTINCT title
FROM movies
JOIN sale ON movies.movie_id = sale.movie_id

![image](https://user-images.githubusercontent.com/101512808/220996578-48f5f23f-f132-48d0-a04b-3b90ebb84f98.png)


**17. Display a common list of names of all actors and clients, and sort the result alphabetically. (Use the UNION function for this)**

SELECT name FROM actors

UNION

SELECT name FROM customers

ORDER BY name

![image](https://user-images.githubusercontent.com/101512808/220175448-914c4355-fe8f-4e02-ba05-4da8b05eaf69.png)

**18.Inflation has taken over Poland and our movie shop has also been affected by this problem. Increase the price of all movies made after 2000 by $2.50 (Remember that the dollar is the default unit - don't use it anywhere).**

UPDATE movies

SET price = '7,5'

WHERE movie_id = 1;


UPDATE movies

SET price = '9'

WHERE movie_id = 3;


UPDATE movies

SET price = '6,5'

WHERE movie_id = 4;


UPDATE movies

SET price = '7,5'

WHERE movie_id = 6;


UPDATE movies

SET price = '12,5'

WHERE movie_id = 7;


UPDATE movies

SET price = '12,5'

WHERE movie_id = 9;

![image](https://user-images.githubusercontent.com/101512808/220180277-8c943c89-bfc5-40c2-ac90-0427203dc112.png)

**19. Display the name of the actor with id 4 and the title of the movie he starred in**

SELECT actors.actor_id, actors.name, actors.surname, movies.title

FROM ((actors

INNER JOIN cast ON actors.actor_id = cast.actor_id)     

INNER JOIN movies ON cast.movie_id = movies.movie_id)

![image](https://user-images.githubusercontent.com/101512808/220183387-0facc401-5329-43de-abf3-13927e2568c7.png)

**20. And where is our HONIA!? Add a new tuple to the customers table, where customer_id = 7, name = Honia, surname = Stuczka-Kucharska, email = honia@mail.com and pseudonym = Hoa**

INSERT INTO customers (customer_id, name, surname, email, pseudonym)

VALUES ('7', 'Honia', 'Stuczka-Kucharska', 'honia@mail.com', 'Hoa');

![image](https://user-images.githubusercontent.com/101512808/220184874-b347df05-841c-4da8-8ec8-190eee826d78.png)

# Task 5

*SQL Part 1*

## Subtask 1

**SELECT** * 

shows all the colummns
The SELECT statement is used to select data from a database.

**FROM** 

the name of the table should be displayed *table_name*

**ORDER BY** 

The ORDER BY keyword is used to sort the result-set in ascending or descending order.
The ORDER BY keyword sorts the records in *ascending* order by default. To sort the records in *descending* order, use the *DESC* keyword.

_Example:_

SELECT column1, column2, ...

FROM table_name

ORDER BY column1, column2, ... ASC|DESC;

**WHERE** 

The WHERE clause is used to filter records.
It is used to extract only those records that fulfill a specified condition.
The WHERE clause can be combined with AND, OR, and NOT operators.

_Example:_

SELECT column1, column2, ...

FROM table_name

WHERE condition;


**AND/OR Operators** 

The AND operator displays a record if all the conditions separated by AND are TRUE.
The OR operator displays a record if any of the conditions separated by OR is TRUE.

_Example_

SELECT column1, column2, ...

FROM table_name

WHERE condition1 AND condition2 AND condition3 ...;

WHERE Color = 'Black' AND Size = 'M'

_Example_

SELECT column1, column2, ...

FROM table_name

WHERE condition1 OR condition2 OR condition3 ...;

WHERE Color = 'Black' OR Color = 'Silver'

**LIKE**

The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

_Example_

SELECT column1, column2, ...

FROM table_name

WHERE columnN LIKE pattern;

WHERE Name LIKE 'B%' name which starts with B

WHERE Name LIKE '%b' name which ends with b

WHERE Name LIKE '%Bike%' finds values that have Bike in any position

**IS NULL**

The IS NULL operator is used to test for empty values (NULL values).

_Example_

SELECT CustomerName, ContactName, Address

FROM Customers

WHERE Address IS NULL;


**IN**

The IN operator allows you to specify multiple values in a WHERE clause.
The IN operator is a shorthand for multiple OR conditions.

_Example_

The following SQL statement selects all customers that are located in "Germany", "France" or "UK":

SELECT * FROM Customers

WHERE Country NOT IN ('Germany', 'France', 'UK');

**BETWEEN**

The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.

_Example_

The following SQL statement selects all products with a price between 10 and 20:

SELECT * FROM Products

WHERE Price BETWEEN 10 AND 20;



## Subtask 3

**1. Display the actors table in alphabetical order by sorting by the surname column.**

SELECT * FROM `actors` 
ORDER BY surname

![image](https://user-images.githubusercontent.com/101512808/218532727-82cd43fe-76fa-489d-8c1e-bbd2d742cb5c.png)

**2. View a movie that was made in 2019.**

SELECT * FROM movies
WHERE year_of_production = '2019'

![image](https://user-images.githubusercontent.com/101512808/218535129-0e472cdf-fcaf-4bd0-8d29-ff63eae5758b.png)

**3. View all movies made between 1900 and 1999.**

SELECT * FROM movies
WHERE year_of_production BETWEEN 1900 AND 1999

![image](https://user-images.githubusercontent.com/101512808/218541497-e99dafba-ab45-4a9a-b2d6-97d40bd848a1.png)

**4. Display ONLY the title and price of movies that cost less than $7**

SELECT title, price
FROM `movies`
WHERE price < '7'

![image](https://user-images.githubusercontent.com/101512808/218545086-128b1fb1-47ac-4f64-b729-1922f62c23cf.png)

**5. Use the logical AND operator to display actors with actor_ids between 4-7 (4 and 7 should display). DO NOT USE BETWEEN operator.**

SELECT *
FROM actors
WHERE (name = 'Jack' OR name = 'Harrison' OR name = 'Anne' OR name = 'Helena') AND actor_id IN (4,5,6,7)

![image](https://user-images.githubusercontent.com/101512808/218806694-d114d366-fb5e-4f0d-9fe8-33720b26117c.png)

SELECT *
FROM actors
WHERE actor_id >= '4' AND actor_id <= '7'

![image](https://user-images.githubusercontent.com/101512808/219449670-cd355a6b-c0f9-4f01-ac5d-4ae579eebbcb.png)


**6. Display customers with id 2,4,6 use logical condition for this.**

SELECT *
FROM customers
WHERE customer_id = '2' OR customer_id = '4' OR customer_id = '6'

![image](https://user-images.githubusercontent.com/101512808/218562030-edbf1aaa-446a-4d64-b6ab-f66aa2542f08.png)

**7. Display customers with id 1,3,5 use IN operator for this.**

SELECT customer_id, name, surname, email
FROM customers
WHERE customer_id IN (1,3,5)

![image](https://user-images.githubusercontent.com/101512808/218564886-56edc2f4-3c8a-4cd6-a3ed-90600e3f2d2c.png)

**8. Display the details of all persons in the 'actors' table whose name starts with 'An'.**

SELECT *
FROM actors
WHERE name LIKE 'An%'

![image](https://user-images.githubusercontent.com/101512808/218565797-63beed07-8204-4bf3-8ed7-8e1820a29010.png)

**9. Display details of a customer who does not have an email address provided.**

SELECT * FROM `customers`
WHERE email IS NULL

![image](https://user-images.githubusercontent.com/101512808/218567275-852c711b-098e-4647-b3c5-958c354c6a74.png)

**10. View all movies priced over $9 and with an ID between 2 and 8 movie_id.**

SELECT *
FROM movies
WHERE price >'9' AND movie_id BETWEEN 2 AND 8

![image](https://user-images.githubusercontent.com/101512808/218568931-206a6480-6b2e-4d1a-9a95-3026fb49ae1d.png)
