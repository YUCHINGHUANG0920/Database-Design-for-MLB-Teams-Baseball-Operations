## Database Design for MLB Teams’ Baseball Operations
### Overview
In Major League Baseball (MLB), data plays a crucial role in enhancing team performance, player development, and strategic decision-making. 

This project focuses on building a normalized MySQL database to store FanGraphs data retrieved via the pybaseball package. The database design encompasses multiple tables, including player biography, player standard statistics, and advanced statistics. These tables have been meticulously crafted based on an Entity-Relationship Diagram (ERD) to relational model conversion, ensuring optimal organization and accessibility of data.

The analysis covers the past decade (2014-2023), allowing us to uncover trends in player and team performance. By consolidating this historical data, we can gain insights into player development pathways and team dynamics within the evolving landscape of baseball operations.

### How to use this MySQL database for futher analysis?
After establishing the tables and defining primary key (PK) and foreign key (FK) relationships in MySQL, we can use SQL queries for analysis.

For example, to explore the correlation between division rankings and pitcher performance, we can extract advanced statistics (such as WAR and BB%) for the top two ranked teams in each division for each year using the following SQL query:

```SQL
SELECT t.team_name, ad.WAR, ad.BB%, s.season, s.div_id, s.rank 
FROM standings s 
JOIN team t ON s.team_id = t.team_id 
JOIN advanced ad ON t.team_id = ad.team_id 
WHERE s.rank <= 2 
ORDER BY s.season, s.div_id, s.rank;
```

This SQL statement retrieves the names of the top two teams in each division for every season, along with their pitchers’ advanced metrics (WAR and BB%). This data provides valuable insights into how team rankings may relate to pitcher performance, enabling us to analyze trends and make informed decisions in baseball operations.