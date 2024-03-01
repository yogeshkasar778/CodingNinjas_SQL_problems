
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
  |----------|------|--------|------|----------|--------|
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
    
##  :dart: `Difficulty Level - Moderate`

 ### Q.1 From the IMDb dataset, print the title and rating of those movies that have a genre starting from 'C' released in 2014 with a budget higher than 4 Crore.
   **IMDB Rating**:
   `Company - Thought Works`
   
 ###  Solution - 
    
    Select i.Title,i.Rating 
    from IMDB as i
    left join genre as g on i.movie_id=g.movie_id
    where g.genre like'C%' and i.Title like'%2014%' and i.Budget>40000000;
    





    
