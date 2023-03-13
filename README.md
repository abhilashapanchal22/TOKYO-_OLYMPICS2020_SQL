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
   
# 3. Total Gold Medals, Total Silver Medals, Total Bronze medals won in olympics
   
   SELECT SUM(Gold) AS TOTAL_GOLD, SUM(Silver) AS TOTAL_SILVER, SUM(Bronze) AS TOTAL_BRONZE
   FROM medals1;

  <img src = "" alt = "MLBC">
