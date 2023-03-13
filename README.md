# TOKYO-_OLYMPICS2020_SQL


This project was performed in MySQL Workbench with using the data. i have cleaned the data in excel. it has 5 tables containing different columns such as NOC(Country), Name of athelete,medals(Gold,Silver,Bronze), Disciplines and many other.During this project i used DISTINCT function, COUNT function, SUM function, JOINS, WHERE statements, ORDER BY, GROUP BY, LIMIT, and created a ERD in order to outline the tables with primary and Foreign keys.

# Analysis of The Project

# 1. Countries participation in total discipline and total medals won

   SELECT a.NOC, COUNT(Discipline) AS Total_Discipline , m.Total AS Total_Medals
   from athletes1 a
   INNER JOIN 
   medals1 m ON a.NOC = m.NOC
   group by 3,1
   order by COUNT(Discipline) DESC;

  <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(31).png" alt = "MLBC">

# 2. Total decipline each country participated

   SELECT NOC, COUNT(Discipline)AS Total_Discipline
   from athletes1
   group by 1
   order by COUNT(Discipline) DESC;
   
   <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL" alt = "MLBC">
   
# 3. Total Gold medals, Total Silver medals, Total Bronze medals won in olympics
   
   SELECT SUM(Gold) AS TOTAL_GOLD, SUM(Silver) AS TOTAL_SILVER, SUM(Bronze) AS TOTAL_BRONZE
   FROM medals1;

  <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(35).png" alt = "MLBC">
  
# 4. Top 10 countries who won highest medals

   SELECT NOC, Gold, Silver, Bronze, Total
   FROM medals1
   ORDER BY Total desc
   LIMIT 10;
   
   <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(37).png" alt = "MLBC">

# 5. Countries participation in different discipline

   SELECT DISTINCT(NOC) AS country, Discipline
   FROM athletes1
   GROUP BY country, Discipline
   ORDER BY country ASC;
   
  <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(39).png" alt = "MLBC">
   
# 6. Total medals won by Male and Female

   SELECT SUM(Female) AS Total_Female, SUM(Male) AS Total_Male
   FROM entriesgender1;
   
   <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(41).png" alt = "MLBC">
   
# 7. Male and female winning percentage

   SELECT ROUND(SUM(Female)/Sum(Total)*100) AS Femalepercentage, round(SUM(Male)/SUM(Total)*100) AS Malepercentage
   FROM entriesgender1;
   
   <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(44).png" alt = "MLBC">
   
# 8. Top 10 countries who win highest medals(Gold, Silver, Bronze) 

   SELECT NOC, Gold, Silver, Bronze, Total, Rankbytotal 
   FROM medals1
   ORDER BY Rankbytotal ASC
   LIMIT 10;

   <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(46).png" alt = "MLBC">
   
# 9. Joining all the tables together to do exploratory analysis

   SELECT a.Name AS Athlete_Name, a.NOC AS Country, a.Discipline, c.Name AS Coach_Name, e.Female, e.Male, e.Total AS Total_Male_female, m.Gold, m.Silver, m.Bronze,
   m.Total AS Total_Medals, m.Rankbytotal, t.Gender  
   FROM athletes1 a
   JOIN coaches1 c ON a.NOC = c.NOC
   JOIN entriesgender1 e ON c.Discipline = e.Discipline
   JOIN medals1 m ON c.NOC = m.NOC
   JOIN teams1 t ON m.NOC = t.NOC
   ORDER BY 2 ASC;
     
  <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(49).png" alt = "MLBC">  
   
   
# 10. Extracting USA information by joining tables
 
   Select * 
   from athletes1 a
   JOIN coaches1 c ON a.NOC = c.NOC
   JOIN entriesgender1 e ON c.Discipline = e.Discipline
   JOIN medals1 m ON c.NOC = m.NOC
   JOIN teams1 t ON m.NOC = t.NOC
   WHERE a.NOC = "United States of America"
   ORDER BY a.Discipline;

  <img src = "https://github.com/abhilashapanchal22/TOKYO-_OLYMPICS2020_SQL/blob/main/Screenshot%20(52).png" alt = "MLBC">  
  
# 11. Disciplines in which United States participated

   SELECT DISTINCT(Discipline), NOC AS Country
   FROM athletes1
   WHERE NOC = "United States of America"
   GROUP BY 1
   ORDER BY 1 ASC;
   
   <img src = "" alt = "MLBC">

      
