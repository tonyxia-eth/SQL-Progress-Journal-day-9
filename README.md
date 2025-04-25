# SQL-Progress-Journal-day-9

# ⚾ CS50 Moneyball SQL Project 

## ✅ Project Overview

This is part of my journey through CS50's Introduction to Databases with SQL.  
In this project, I'm analyzing real MLB player and team data using SQL to make strategic decisions — just like a baseball team's general manager.


## 📂 Tasks Completed Today (5.sql to 8.sql)

### ✅ Task 5 – Teams Satchel Paige Played For

SELECT DISTINCT t.name
FROM players p
JOIN performances pf ON p.id = pf.player_id
JOIN teams t ON pf.team_id = t.id
WHERE p.first_name = 'Satchel' AND p.last_name = 'Paige';

cat 5.sql | sqlite3 moneyball.db > "5.sql - results.txt"

✅ Task 6 – Top 5 Teams by Total Hits (2001)

SELECT t.name, SUM(pf.H) AS "total hits"
FROM performances pf
JOIN teams t ON pf.team_id = t.id
WHERE pf.year = 2001
GROUP BY t.name
ORDER BY "total hits" DESC
LIMIT 5;
Terminal command:

cat 6.sql | sqlite3 moneyball.db > "6.sql - results.txt"

✅ Task 7 – Highest Paid Player in MLB History

SELECT pl.first_name, pl.last_name
FROM players pl
JOIN salaries s ON pl.id = s.player_id
WHERE s.salary = (SELECT MAX(salary) FROM salaries);
Terminal command:

cat 7.sql | sqlite3 moneyball.db > "7.sql - results.txt"

✅ Task 8 – 2001 Home Run Leader and Their Salary (w/ Player Name)

SELECT players.first_name, players.last_name, salaries.salary
FROM players
JOIN salaries ON players.id = salaries.player_id
JOIN performances ON players.id = performances.player_id
WHERE salaries.year = 2001
  AND performances.year = 2001
  AND performances.HR = (
      SELECT MAX(HR)
      FROM performances
      WHERE year = 2001
  );
Terminal command:

cat 8.sql | sqlite3 moneyball.db > "8.sql - results.txt"

🧠 Key Takeaways
💡 SQL Concepts Practiced
JOIN, DISTINCT, SUM(), MAX(), filtering by year

Subqueries inside WHERE

Multi-table queries and value matching

Organized sorting and output management

🧰 Workflow Highlights
I used a repeatable command-line pattern to run and store each query:

cat <task>.sql | sqlite3 moneyball.db > "<task>.sql - results.txt"
For example:

cat 7.sql | sqlite3 moneyball.db > "7.sql - results.txt"
Wrapping file names in quotes allowed me to keep everything clean, consistent, and super efficient. This has become a key part of my daily workflow.

🌱 Reflections
Although I wasn’t feeling 100% today, I showed up and knocked out four more tasks. I’m now confident joining multiple tables, writing subqueries, and formatting professional SQL results from the command line.

