# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE season = 2017;

```

2) Find all the matches featuring Barcelona.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE hometeam = 'Barcelona' or awayteam = 'Barcelona';


```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here -->
SELECT * FROM divisions WHERE country = 'Scotland';


```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables

```sql
<!-- Copy solution here -->

SELECT code FROM divisions WHERE name = 'Bundesliga';
SELECT COUNT(*) FROM matches WHERE (hometeam = 'Freiburg' OR awayteam = 'Freiburg') AND division_code = 'D1';


```

5) Find the teams which include the word "City" in their name. 

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE hometeam LIKE '%City%' OR awayteam LIKE '%City%';



```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here -->

SELECT COUNT(*) AS total_different_teams --for some reason, this code would not work unless I add an alias i.e AS...is it because it is nested?
FROM (
    SELECT hometeam FROM matches WHERE division_code IN ('F1', 'F2')

    UNION -- according to research, this keyword allows for nesting of two different queries; using it to get a single output in this case.

    SELECT awayteam FROM matches WHERE division_code IN ('F1', 'F2')
) AS both_homeand_away_teams;


```

7) Have Huddersfield played Swansea in any of the recorded matches?

```sql
<!-- Copy solution here -->
SELECT COUNT(*)
FROM matches
WHERE (hometeam = 'Huddersfield' AND awayteam = 'Swansea')
   OR (hometeam = 'Swansea' AND awayteam = 'Swansea');


```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```sql
<!-- Copy solution here -->
SELECT COUNT(*) AS num_draws FROM matches WHERE division_code = 'N1'
AND season BETWEEN 2010 AND 2015
AND ftr = 'D';


```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. When two matches have the same total the match with more home goals should come first.

```sql
<!-- Copy solution here -->

SELECT * FROM matches WHERE division_code = 'E0' ORDER BY (fthg + ftag) DESC, fthg DESC;



```

10) In which division and which season were the most goals scored?

```sql
<!-- Copy solution here -->


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)