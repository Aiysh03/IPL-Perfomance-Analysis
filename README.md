# IPL Performance Analysis
## Project Objective
The objective of this project is to analyze IPL match data using SQL and Power BI to identify match trends, team performance, and batting vs chasing strategies, while strengthening data analysis fundamentals using real-world data.

## Project Overview
This is a beginner-level data analysis project based on Indian Premier League (IPL) match data. SQL is used to explore and analyze the dataset, and Power BI is used to build interactive dashboards that clearly present insights.

## KPI'S
1. What is the total number of IPL matches played?
2. How many matches were played in each IPL season?
3. How many matches were affected by the Duckworth–Lewis (DL) method?
4. Which team has won the highest number of matches overall?
5. What percentage of matches were won by the toss-winning team?
6. Is batting first or chasing more effective in IPL matches?
7. How many matches were won by chasing versus batting first?
8. Does winning the toss guarantee winning the match?
9. How has match strategy (bat vs field) impacted results over seasons?
10. What insights can be drawn about team performance from match outcomes?

## Dashboard
[📥 View IPL Analysis Report (PDF)](Report/IPL%20Analysis%20PDF.pdf)

## SQL Queries used
-- total matches played
SELECT COUNT(*) AS Total_Matches
FROM raw_match;

-- matches by season
SELECT Season, COUNT(*) AS matches_played
FROM raw_match
GROUP BY Season;

-- DL applied matches
SELECT COUNT(*) AS total_matches, SUM(DL_Applied) AS dl_matches
FROM raw_match;

-- top winning team
SELECT Winner, COUNT(*) AS matches_won
FROM raw_match
WHERE Winner IS NOT NULL
GROUP BY Winner;

-- bat vs chase win strategy
SELECT 
    Toss_Decision,
    CASE
        WHEN Toss_Decision = 'bat' AND Toss_Winner = Winner THEN 1
        WHEN Toss_Decision = 'field' AND Toss_Winner <> Winner THEN 1
        ELSE 0
    END AS Strategy_Win
FROM raw_match
WHERE Winner IS NOT NULL;

## Dashboard Insights (Power BI)
1. Chasing teams tend to win more matches than teams batting first
2. Toss advantage exists but does not guarantee a win
3. A few teams dominate overall wins across seasons
4. Close and high-scoring matches increase fan engagement

## Tools & Technologies Used
1. SQL – Data querying and analysis
2. Power BI – Data visualization and dashboard creation
3. Excel – Data cleaning and preparation

## What I Learned
- Writing basic SQL queries for real datasets
- Analyzing sports data to identify trends and patterns
- Creating interactive dashboards in Power BI
- Converting raw data into meaningful insights



