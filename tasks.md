# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE season = '2017';

```

2) Find all the matches featuring Barcelona.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE awayteam = 'Barcelona'  or hometeam = 'Barcelona';

```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here -->
SELECT name, country FROM divisions WHERE country = 'Scotland';

```

4) Find the division code for the Bundesliga. Use that code to find out how many matches Freiburg have played in the Bundesliga since the data started being collected.

```sql
<!-- Copy solution here -->
SELECT * FROM divisions WHERE name LIKE 'Bundesliga';
-- division_code = D1, total 374

SELECT COUNT(division_code) FROM matches WHERE division_code = 'D1' and hometeam = 'Freiburg' or division_code = 'D1' and  awayteam = 'Freiburg';

```

5) Find the unique names of the teams which include the word "City" in their name (as entered in the database)

```sql
<!-- Copy solution here -->
SELECT DISTINCT hometeam FROM matches WHERE hometeam LIKE '%City%';

```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here -->
-- division_code = F1/F2, count = 61
SELECT COUNT(DISTINCT hometeam) FROM matches WHERE division_code = 'F1' or division_code = 'F2';

```

7) Have Huddersfield played Swansea in the period covered?

```sql
<!-- Copy solution here -->
--YES
SELECT * FROM matches WHERE  hometeam = 'Huddersfield' and  awayteam = 'Swansea';

```

8) How many draws were there in the Eredivisie between 2010 and 2015?

```sql
<!-- Copy solution here -->
--code = N1 , ans= 1114
SELECT COUNT(division_code) FROM matches WHERE division_code = 'N1' and ftr = 'D';

```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. Where there is a tie the match with more home goals should come first.

```sql
<!-- Copy solution here -->
--code=E0, 6080 rows
SELECT hometeam, SUM(fthg)+SUM(ftag) FROM matches WHERE division_code = 'E0' GROUP BY hometeam ORDER BY SUM(fthg) DESC;

```

10) In which division and which season were the most goals scored?

```sql
<!-- Copy solution here -->
--ans = 2013,EC
SELECT DISTINCT (season, division_code), SUM(fthg)+SUM(ftag) FROM matches GROUP BY division_code, season ORDER BY SUM(fthg)+SUM(ftag) DESC;


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)