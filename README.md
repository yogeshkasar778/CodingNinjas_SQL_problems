
# :computer: CodingNinjas SQL  Interview Problems and Solutions - 
- [Easy](https://github.com/yogeshkasar778/CodingNinjas_SQL_problems/new/main?readme=1#dart-difficulty-level---easy)
- [Moderate](https://github.com/yogeshkasar778/CodingNinjas_SQL_problems/new/main?readme=1#dart-difficulty-level---moderate)
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
   `Company - Tata Consultancy Services (TCS`

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
   `Company - Tata Consultancy Services (TCS`

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
   `Company - Tata Consultancy Services (TCS`

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
   `Company - Tata Consultancy Services (TCS`

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

  ### Q.12 Write an SQL query to find all the people who viewed more than one article on the same date, sorted in ascending order by their id.
  
   **Article**:
   `Company - Tata Consultancy Services (TCS`

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
+------------+-----------+-----------+------------|
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
                        
##  :dart: `Difficulty Level - Moderate`

 ### Q.1 From the IMDb dataset, print the title and rating of those movies that have a genre starting from 'C' released in 2014 with a budget higher than 4 Crore.
   **IMDB Rating**:
   `Company - Thought Works`
   
 ###  Solution - 
    
    Select i.Title,i.Rating 
    from IMDB as i
    left join genre as g on i.movie_id=g.movie_id
    where g.genre like'C%' and i.Title like'%2014%' and i.Budget>40000000;
    





    
