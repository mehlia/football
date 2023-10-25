# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```
SELECT * FROM matches WHERE season = '2017' ;
```

2) Find all the matches featuring Barcelona.

```
SELECT * FROM matches WHERE awayteam = 'Barcelona' AND hometeam = 'Barcelona';
```

3) What are the names of the Scottish divisions included?
<!-- Scottish Premiership, Championship & League One -->

```
SELECT * FROM divisions WHERE country = 'Scotland';
```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables
<!-- code for Bundesliga = D1 -->

```
SELECT code FROM divisions WHERE name = 'Bundesliga';

SELECT * FROM matches WHERE division_code = 'D1' AND hometeam = 'Freiburg' AND awayteam = 'Freiburg';
```

5)  Find the teams which include the word "City" in their name. HINT: Not every team has been entered into the database with their full name, eg. `Norwich City` are listed as `Norwich`. If your query is correct it should return four teams.

```
SELECT * FROM matches WHERE hometeam LIKE '%City%' AND awayteam LIKE '%City%';
```

6) How many different teams have played in matches recorded in a French division?

```
SELECT * FROM divisions WHERE country = 'France';
SELECT * FROM matches WHERE division_code = 'F1' AND division_code = 'F2';
```

7) Have Huddersfield played Swansea in any of the recorded matches?
<!-- 12 matches -->

```
SELECT COUNT(*) FROM matches WHERE (hometeam = 'Huddersfield' AND awayteam = 'Swansea') OR (hometeam = 'Swansea' AND awayteam = 'Huddersfield');

```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```
SELECT * FROM matches WHERE ftr = 'D' AND season BETWEEN '2010' AND '2015';
```

9) Select the matches played in the Premier League in order of total goals scored (`fthg` + `ftag`) from highest to lowest. When two matches have the same total the match with more home goals (`fthg`) should come first. 

```
SELECT * FROM divisions WHERE name = 'Premier League';
SELECT * FROM matches WHERE division_code = 'E0' ORDER BY (fthg + ftag) DESC, fthg DESC;
```

10) Find the name of the division in which the most goals were scored in a single season and the year in which it happened.

```
SELECT name FROM divisions WHERE SUM(fthg + ftag);
```
