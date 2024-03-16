
# :computer: CodingNinjas SQL  Interview Problems and Solutions - 
- [Easy](https://github.com/yogeshkasar778/CodingNinjas_SQL_problems/new/main?readme=1#dart-difficulty-level---easy)
- [Moderate](https://github.com/yogeshkasar778/CodingNinjas_SQL_problems/new/main?readme=1#dart-difficulty-level---moderate)
- [Ninja](https://github.com/yogeshkasar778/CodingNinjas_SQL_problems/edit/main/README.md#dart-difficulty-level---ninja)
##  :dart: `Difficulty Level - Easy`
  
 ### Q.1 Print the title and ratings of the movies released in 2012 whose metacritic rating is more than 60 and Domestic collections exceed 10 Crores. (Download the dataset from console)
   **IMDB metacritic Rating**:
   `Company - Tata Consultancy Services (TCS)`
   
 ###  Solution - 
    
    Select i.Title,i.Rating 
    from IMDB as i
    left join earning as e on i.movie_id=e.movie_id
    where i.Title like'%2012%' and i.MetaCritic >60and e.Domestic>100000000;

 ### Q.2 Insert below student details in students table and print all data of table.
   **Students DB**:
   `Company - Tata Consultancy Services (TCS)`
   
 ###  Solution - 
    
    insert into students  
    values(3,'Kim ','F'  )
    ,(4,'Molina','F'),
    (5,'Dev','M');

    select * from students
 ### Q.3 Given three tables: salesperson, company, orders. Output all the names in the table salesperson, who didn’t have sales to company 'RED'.
   **Sales Executive**:
   `Company - Wipro

  Table: Salesperson 
  |sales_id | name | salary | commission_rate | hire_date |
  |----------|------|--------|-----------------|-----------|
  |   1      | John | 100000 |     6           | 4/1/2006  |
  |   2      | Amy  | 120000 |     5           | 5/1/2010  |
  |   3      | Mark | 65000  |     12          | 12/25/2008|
  |   4      | Pam  | 25000  |     25          | 1/1/2005  |
  |   5      | Alex | 50000  |     10          | 2/3/2007  |

  The table salesperson holds the salesperson information. Every salesperson has a sales_id and a name.

  Table: Company 
  | com_id  |  name  |    city    |
  |----------|------|--------|
  |   1     |  RED   |   Boston   |
  |   2     | ORANGE |   New York |
  |   3     | YELLOW |   Boston   |
  |   4     | GREEN  |   Austin   |
  
  The table company holds the company information. Every company has a com_id and a name.
  
  Table: Orders 
  
  | order_id | order_date | com_id  | sales_id | amount |
  |----------|------------|-------- |----------|--------|
  | 1        |   1/1/2014 |    3    |    4     | 100000 |
  | 2        |   2/1/2014 |    4    |    5     | 5000   |
  | 3        |   3/1/2014 |    1    |    1     | 50000  |
  | 4        |   4/1/2014 |    1    |    4     | 25000  |
  
  The table orders holds the sales record information, salesperson and customer company are represented by sales_id and com_id.

 ###  Solution - 
    
    select s.name from  Salesperson as s  
    where sales_id not in (select sales_id from  Orders as o 
                          join  Company as c on c.com_id  =o.com_id  
                          where c.name='RED' ); 
 ### Q.4 Problem statement Print the genre and the maximum weighted rating among all the movies of that genre released in 2014 per genre. (Download the dataset from console)
**Note:**
1. Do not print any row where either genre or the weighted rating is empty/null.
2.  weighted_rating = avgerge of (rating + metacritic/10.0)
3. Keep the name of the columns as 'genre' and 'weighted_rating'
4. The genres should be printed in alphabetical order.

   **IMDb Max Weighted Rating**:
   `Company - Thought Works`
   
 ###  Solution - 
    
      select g.genre, max((i.rating+i.metacritic/10.0)/2.0)as weighted_rating 
      from genre as g
      join imdb as i on g.movie_id=i.movie_id
      where g.genre is not null and  (i.rating is not null and i.metacritic is not null) 
          and i.title like '%2014%'
      group by g.genre
      order by g.genre  asc;
      
 ### Q.5 Problem statement: There is a table World
 
   **Big Countries**
   `Company - IBM,Infosys`
   
   | name            | continent  | area       | population   | gdp       |
   |-----------------|------------|------------|--------------|-----------|
   | Afghanistan     | Asia       | 652230     | 25500100     |20343000   | 
   | Albania         | Europe     | 28748      | 2831741      | 12960000  |
   | Algeria         | Africa     | 2381741    | 37100000     | 188681000 |    
   | Andorra         | Europe     | 468        | 78115        | 3712000   |
   | Angola          | Africa     | 1246700    | 20609294     | 100990000 |    
   
 A country is big if it has an area of bigger than 3 million square km or a population of more than 25 million.
 Write a SQL solution to output big countries' name, population and area.  
 
 ###  Solution - 
    
      select name, population, area 
      from World
      where population>25000000 or area>3000000;
      
  ### Q.6 Problem statement: Swap Salary
 
   **Swap Salary**:
   `Company - Cognizant`

   Table: Salary
   
   | Column Name | Type     |
   |-------------|----------|
   | id          | int      |
   | name        | varchar  |
   | sex         | ENUM     |
   | salary      | int      |
   
 id is the primary key for this table.
 The sex column is ENUM value of type ('m', 'f').
 The table contains information about an employee.  
 
 ###  Solution - 
    
      update salary
      set sex=replace('fm',sex,'')  

  ### Q.7 Problem statement: Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people: FirstName, LastName, City, State
 
   **Combine Two Tables**:
   `Company - Tata Consultancy Services (TCS`

   Table: Person
   
| Column Name | Type    |
|-------------|---------|
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |

PersonId is the primary key column for this table.

Table: Address

| Column Name | Type    |
|-------------|---------|
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
AddressId is the primary key column for this table.
 
 ###  Solution - 
    
      select p.FirstName,p.LastName,a.City,a.State 
      from Person as P
      left join Address as a on p.PersonId=a.PersonId

  ### Q.8 Write a SQL query for a report that provides the pairs (actor_id, director_id) where the actor have co-worked with the director at least 3 times.
 
   **Director's Actor**:
   `Company - Infosys`

   Table: ActorDirector
   
| Column Name | Type    |
|-------------|---------|
| actor_id    | int     |
| director_id | int     |
| timestamp   | int     |

Timestamp is the primary key column for this table.

Example:

ActorDirector table:

| actor_id    | director_id | timestamp   |
|-------------|-------------|-------------|
| 1           | 1           | 0           |
| 1           | 1           | 1           |
| 1           | 1           | 2           |
| 1           | 2           | 3           |
| 1           | 2           | 4           |
| 2           | 1           | 5           |
| 2           | 1           | 6           |

 ###  Solution - 
    
      select actor_id, director_id 
      from ActorDirector 
      group by actor_id, director_id
      having count(timestamp)>=3 
      
  ### Q.9 Write a SQL query to rank scores. If there is a tie between two scores, both should have the same ranking. Note that after a tie, the next ranking number should be the next consecutive integer value. In other words, there should be no "holes" between ranks.
 
   **Rank Scores**:
   `Company - VMware Inc`

| Id | Score |
|----|-------|
| 1  | 3.50  |
| 2  | 3.65  |
| 3  | 4.00  |
| 4  | 3.85  |
| 5  | 4.00  |
| 6  | 3.65  |

For example, given the above Scores table, your query should generate the following report (order by highest score):

 ###  Solution - 
    
      select 
           Score, 
            dense_rank() over (order by Score desc) as "Rank"
      from Scores;      

  ### Q.10 Write an SQL query to report all the sessions that did not get shown any ads. Return the result table in any order.
 
   **Spotify Sessions**:
   `Company - LinkedIn, OYO`

Table: Playback

| Column Name | Type |
|-------------|------|
| session_id  | int  |
| customer_id | int  |
| start_time  | int  |
| end_time    | int  |

session_id is the primary key for this table.
customer_id is the ID of the customer watching this session.
The session runs during the inclusive interval between start_time and end_time.
It is guaranteed that start_time <= end_time and that two sessions for the same customer do not intersect.


Table: Ads

 | Column Name | Type |
 |-------------|------|
 | ad_id       | int  |
 | customer_id | int  |
 | timestamp   | int  |

ad_id is the primary key for this table.
Customer_id is the ID of the customer viewing this ad.
Timestamp is the moment at which the ad was shown.

Playback table:

| session_id | customer_id | start_time | end_time |
|------------|-------------|------------|----------|
| 1          | 1           | 1          | 5        |
| 2          | 1           | 15         | 23       |
| 3          | 2           | 10         | 12       |
| 4          | 2           | 17         | 28       |
| 5          | 2           | 2          | 8        |

Ads table:

| ad_id | customer_id | timestamp |
|-------|-------------|-----------|
| 1     | 1           | 5         |
| 2     | 2           | 17        |
| 3     | 2           | 20        |

 ###  Solution - 
    
      select session_id  from Playback as p 
      left join Ads as a on p.customer_id =a.customer_id  and p.start_time<=a.timestamp
      and p.end_time>=timestamp 
      where a.ad_id is null    

  ### Q.11 Write an SQL query to report, How much cubic feet of volume does the inventory occupy in each warehouse. warehouse_name volume Return the result table in any order.
 
   **Warehouse Manager**:
   `Company - JP Morgan,Morgan Stanley`

Table: Warehouse

| Column Name  | Type    |
|--------------|---------|
| name         | varchar |
| product_id   | int     |
| units        | int     |

(name, product_id) is the primary key for this table.
Each row of this table contains the information of the products in each warehouse.

Table: Products

| Column Name   | Type    |
|---------------|---------|
| product_id    | int     |
| product_name  | varchar |
| Width         | int     |
| Length        | int     |
| Height        | int     |

product_id is the primary key for this table.
Each row of this table contains the information about the product dimensions (Width, Lenght and Height) in feets of each product.

The query result format is in the following example.

Warehouse table:

| name       | product_id   | units       |
|------------|--------------|-------------|
| LCHouse1   | 1            | 1           |
| LCHouse1   | 2            | 10          |
| LCHouse1   | 3            | 5           |
| LCHouse2   | 1            | 2           |
| LCHouse2   | 2            | 2           |
| LCHouse3   | 4            | 1           |

Products table:

| product_id | product_name | Width      | Length   | Height    |
|------------|--------------|------------|----------|-----------|
| 1          | LC-TV        | 5          | 50       | 40        |
| 2          | LC-KeyChain  | 5          | 5        | 5         |
| 3          | LC-Phone     | 2          | 10       | 10        |
| 4          | LC-T-Shirt   | 4          | 10       | 20        |

 ###  Solution - 
    
      select w.name as warehouse_name, SUM(p.Width * p.Length * p.Height * w.units) AS volume
      from Warehouse w
      join Products p on w.product_id = p.product_id
      group by w.name; 

  ### Q.12 Write an SQL query to find the customer_number for the customer who has placed the largest number of orders. It is guaranteed that exactly one customer will have placed more orders than any other customer.
  
   **Customer Placing the Largest Number Orders**:
   `Company - Expedia Group`

able: Orders

| Column Name     | Type     |
|-----------------|----------|
| order_number    | int      |
| customer_number | int      |

order_number is the primary key for this table.
This table contains information about the order ID and the customer ID.

The query result format is in the following example:

Orders table:

| order_number | customer_number |
|--------------|-----------------|
| 1            | 1               |
| 2            | 2               |
| 3            | 3               |
| 4            | 3               |

 ###  Solution - 
    
      select customer_number
      from Orders
      group by customer_number
      having count(order_number)>1

  ### Q.13 Write an SQL query to find all the people who viewed more than one article on the same date, sorted in ascending order by their id.
  
   **Article**:
   `Company - Veritas Technologies LLC`

Table: Views

| Column Name   | Type    |
|---------------|---------|
| article_id    | int     |
| author_id     | int     |
| viewer_id     | int     |
| view_date     | date    |

There is no primary key for this table, it may have duplicate rows.
Each row of this table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.

The query result format is in the following example:

Views table:

| article_id | author_id | viewer_id | view_date  |
|------------|-----------|-----------|------------|
| 1          | 3         | 5         | 2019-08-01 |
| 3          | 4         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |

 ###  Solution - 
    
      select distinct viewer_id as id 
      from Views
      where (viewer_id,view_date) in (
                        select viewer_id, view_date
                        from Views
                        group by viewer_id, view_date
                        having count(distinct article_id )>1)
      order by id asc;

  ### Q.14 Write an SQL query to find the npv of all each query of queries table. Return the result table in any order.
  
   **NPV Queries**:
   `Company - CoinDCX`

Table: NPV

| Column Name   | Type    |
|---------------|---------|
| id            | int     |
| year          | int     |
| npv           | int     |

(id, year) is the primary key of this table.
The table has information about the id and the year of each inventory and the corresponding net present value.


Table: Queries

| Column Name   | Type    |
|---------------|---------|
| id            | int     |
| year          | int     |

(id, year) is the primary key of this table.
The table has information about the id and the year of each inventory query.

The query result format is in the following example:

VNPV table:

| id   | year   | npv    |
|------|--------|--------|
| 1    | 2018   | 100    |
| 7    | 2020   | 30     |
| 13   | 2019   | 40     |
| 1    | 2019   | 113    |
| 2    | 2008   | 121    |
| 3    | 2009   | 12     |
| 11   | 2020   | 99     |
| 7    | 2019   | 0      |

Queries table:

| id   | year   |
|------|--------|
| 1    | 2019   |
| 2    | 2008   |
| 3    | 2009   |
| 7    | 2018   |
| 7    | 2019   |
| 7    | 2020   |
| 13   | 2019   |

 ###  Solution - 
    
      select q.id, q.year, COALESCE(n.npv, 0) as npv
      from Queries q
      left join NPV n on q.id = n.id and q.year = n.year;
 
  ### Q.15 Write an SQL query to find the most frequently ordered product(s) for each customer. The result table should have the product_id and product_name for each customer_id who ordered at least one order. Return the result table in any order.
  
   **The Most Frequently Ordered Products for Each Customer**:
   `Company - Amazon`

Table: Customers

| Column Name   | Type    |
|---------------|---------|
| customer_id   | int     |
| name          | varchar |

customer_id is the primary key for this table.
This table contains information about the customers.


Table: Orders

| Column Name   | Type    |
|---------------|---------|
| order_id      | int     |
| order_date    | date    |
| customer_id   | int     |
| product_id    | int     |

order_id is the primary key for this table.
This table contains information about the orders made by customer_id.
No customer will order the same product more than once in a single day.

Table: Products

| Column Name   | Type    |
|---------------|---------|
| product_id    | int     |
| product_name  | varchar |
| price         | int     |

product_id is the primary key for this table.
This table contains information about the products.

The query result format is in the following example:

Customers

| customer_id | name  |
|-------------|-------|
| 1           | Alice |
| 2           | Bob   |
| 3           | Tom   |
| 4           | Jerry |
| 5           | John  |

Orders

| order_id | order_date | customer_id | product_id |
|----------|------------|-------------|------------|
| 1        | 2020-07-31 | 1           | 1          |
| 2        | 2020-07-30 | 2           | 2          |
| 3        | 2020-08-29 | 3           | 3          |
| 4        | 2020-07-29 | 4           | 1          |
| 5        | 2020-06-10 | 1           | 2          |
| 6        | 2020-08-01 | 2           | 1          |
| 7        | 2020-08-01 | 3           | 3          |
| 8        | 2020-08-03 | 1           | 2          |
| 9        | 2020-08-07 | 2           | 3          |
| 10       | 2020-07-15 | 1           | 2          |

Products

| product_id | product_name | price |
|------------|--------------|-------|
| 1          | keyboard     | 120   |
| 2          | mouse        | 80    |
| 3          | screen       | 600   |
| 4          | hard disk    | 450   |


 ###  Solution - 
    
      SELECT subquery1.customer_id,subquery1.product_id,subquery1.product_name
     FROM (
          SELECT subquery.customer_id, subquery.product_id,subquery.product_name,
          RANK() OVER(PARTITION BY subquery.customer_id ORDER BY subquery.Counts DESC) as RANKS 
          FROM
             (select Orders.customer_id, 
                     Orders.product_id,
            CASE When Orders.product_id=3 THEN 'screen' ELSE Products.product_name END, 
            Count(*) AS Counts
           FROM Orders 
           LEFT JOIN Products on Orders.product_id=Products.product_id
           GROUP BY Orders.customer_id,Orders.product_id,Products.product_name)as subquery) as subquery1
        WHERE subquery1.RANKS=1
        order by customer_id,product_id
        
  ### Q.16 You are running an ecommerce site that is looking for imbalanced orders. An imbalanced order is one whose maximum quantity is strictly greater than the average quantity of every order (including itself). The average quantity of an order is calculated as (total quantity of all products in the order) / (number of different products in the order). The maximum quantity of an order is the highest quantity of any single product in the order. Write an SQL query to find the order_id of all imbalanced orders. Return the result table in any order.
  
   **Orders With Maximum Quantity Above Average**:
   `Company - Flipkart`

Table: OrdersDetails

| Column Name | Type |
|-------------|------|
| order_id    | int  |
| product_id  | int  |
| quantity    | int  |

(order_id, product_id) is the primary key for this table.
A single order is represented as multiple rows, one row for each product in the order.
Each row of this table contains the quantity ordered of the product product_id in the order order_id.

The query result format is in the following example:

OrdersDetails table:

| order_id | product_id | quantity |
|----------|------------|----------|
| 1        | 1          | 12       |
| 1        | 2          | 10       |
| 1        | 3          | 15       |
| 2        | 1          | 8        |
| 2        | 4          | 4        |
| 2        | 5          | 6        |
| 3        | 3          | 5        |
| 3        | 4          | 18       |
| 4        | 5          | 2        |
| 4        | 6          | 8        |
| 5        | 7          | 9        |
| 5        | 8          | 9        |
| 3        | 9          | 20       |
| 2        | 9          | 4        |

###  Solution - 
    
      with temp as(
           select order_id, avg(quantity) as avg_quantity, max(quantity) as max_quantity
           from ordersdetails 
           group by order_id 
           order by order_id)
     select distinct order_id
     from temp
     where max_quantity > (select max(avg_quantity) from temp);

### Q.17 A pupil Tim gets homework to identify whether three line segments could possibly form a triangle. However, this assignment is very heavy because there are hundreds of records to calculate. Could you help Tim by writing a query to judge whether these three  sides can form a triangle, assuming table triangle holds the length of the three sides x, y and z.

   **Triangle Judgement**:
   `Company - Oracle`        

| x  | y  | z  |
|----|----|----|
| 13 | 15 | 30 |
| 10 | 20 | 15 |
 
###  Solution - 

     select *, 
           case when x+y>z and y+z>x and z+z>y then 'Yes' else 'No' end as triangle 
     from Triangle 

 For the sample data above, your query should return the follow result:
 | x  | y  | z  | triangle |
 |----|----|----|----------|
 | 13 | 15 | 30 | No       |
 | 10 | 20 | 15 | Yes      |

 ### Q.18 Write a SQL query to find all duplicate emails in a table named Person.
 
   **Duplicate Emails**:
   `Company - IBM`        

| Id | Email   |
|----|---------|
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |


###  Solution - 

     select *, 
           case when x+y>z and y+z>x and z+z>y then 'Yes' else 'No' end as triangle 
     from Triangle 

For example, your query should return the following for the above table:

| Email   |
|---------|
| a@b.com |

 ### Q.19 Write a SQL query to find all duplicate emails in a table named Person.
 
   **Marvel Cities**:
   `Company - Tata Consultancy Services`        

Query all columns for all Marvel cities in the CITY table with populations larger than 100000. The CountryCode for Marvel is Marv.

The CITY table is described as follows:

| Field  |  Type    |
+---------+--------+
|   ID    |  Number  | 
|   Name  | Varchar  |
|   CountryCode | Varchar  |
|   Population |   Number  | 


###  Solution - 

     select * 
     from CITY
     where population >100000 and countrycode = 'Marv'; 

##  :dart: `Difficulty Level - Moderate`

 ### Q.1 From the IMDb dataset, print the title and rating of those movies that have a genre starting from 'C' released in 2014 with a budget higher than 4 Crore.
   **IMDB Rating**:
   `Company - Thought Works`
   
 ###  Solution - 
    
    Select i.Title,i.Rating 
    from IMDB as i
    left join genre as g on i.movie_id=g.movie_id
    where g.genre like'C%' and i.Title like'%2014%' and i.Budget>40000000;

##  :dart: `Difficulty Level - Ninja`

### Q.1 Codestudio Bank (CSB) helps its coders in making virtual payments. Our bank records all transactions in the table Transaction, we want to find out the current balance of all users and check wheter they have breached their credit limit (If their current credit is less than 0). Write an SQL query to report. user_id user_name credit, current balance after performing transactions.   credit_limit_breached, check credit_limit ("Yes" or "No"). Return the result table in any order.

   **IMDB Rating**:
   `Company - Microsoft, Amazon, Google`
   
Table: Users

| Column Name  | Type    |
|--------------|---------|
| user_id      | int     |
| user_name    | varchar |
| credit       | int     |

user_id is the primary key for this table.
Each row of this table contains the current credit information for each user.

Table: Transactions

| Column Name   | Type    |
|---------------|---------|
| trans_id      | int     |
| paid_by       | int     |
| paid_to       | int     |
| amount        | int     |
| transacted_on | date    |

trans_id is the primary key for this table.
Each row of this table contains the information about the transaction in the bank.
User with id (paid_by) transfer money to user with id (paid_to).

The query result format is in the following example.

Users table:

| user_id    | user_name    | credit      |
|------------|--------------|-------------|
| 1          | Moustafa     | 100         |
| 2          | Jonathan     | 200         |
| 3          | Winston      | 10000       |
| 4          | Luis         | 800         | 

Transactions table:

| trans_id   | paid_by    | paid_to    | amount   | transacted_on |
|------------|------------|------------|----------|---------------|
| 1          | 1          | 3          | 400      | 2020-08-01    |
| 2          | 3          | 2          | 500      | 2020-08-02    |
| 3          | 2          | 1          | 200      | 2020-08-03    |

 ###  Solution - 
    
    with cte as 
        (select paid_by as user_id, amount * -1 as amount from Transactions
        union
        select paid_to as user_id, amount from Transactions)
    ,
    cte1 as 
       (select user_id, sum(amount) as all_transaction 
        from cte
        group by user_id)
    ,
    cte2 as 
       (select t1.user_id, t1.user_name, (credit+ coalesce(all_transaction,0)) as credit 
        from Users as t1
        left join cte1 as t2 on t1.user_id=t2.user_id)

   select *, case when credit > 0 then 'No' else 'Yes' end as credit_limit_breached  
   from cte2;

Result table:

| user_id    | user_name  | credit     | credit_limit_breached |
|------------|------------|------------|-----------------------|
| 1          | Moustafa   | -100       | Yes                   | 
| 2          | Jonathan   | 500        | No                    |
| 3          | Winston    | 9900       | No                    |
| 4          | Luis       | 800        | No                    |



    
