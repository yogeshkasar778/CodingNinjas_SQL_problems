
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
    
##  :dart: `Difficulty Level - Moderate`

 ### Q.1 From the IMDb dataset, print the title and rating of those movies that have a genre starting from 'C' released in 2014 with a budget higher than 4 Crore.
   **IMDB Rating**:
   `Company - Thought Works`
   
 ###  Solution - 
    
    Select i.Title,i.Rating 
    from IMDB as i
    left join genre as g on i.movie_id=g.movie_id
    where g.genre like'C%' and i.Title like'%2014%' and i.Budget>40000000;
    





    
