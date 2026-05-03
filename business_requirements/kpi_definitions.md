# KPI Definitions

## Purpose

This document defines the business metrics used in the IPL Analytics Lakehouse project.

The goal is to make sure every dashboard number has a clear meaning, formula, and source table.

## Why KPI Definitions Matter

KPI definitions help make dashboard results trustworthy.

Without clear definitions, different people may calculate the same metric differently.

For example, one person may calculate batter strike rate using all balls, while another person may exclude wides. This document explains the agreed rule.

---

## KPI 1: Total Matches

### Business Question

How many matches did each team play?

### Formula

Total Matches = Count of matches where the team appeared as Team 1 or Team 2

### Source File

matches.csv

### Final Gold Table

gold_team_season_performance

---

## KPI 2: Wins

### Business Question

How many matches did each team win?

### Formula

Wins = Count of matches where winner = team name

### Source File

matches.csv

### Final Gold Table

gold_team_season_performance

---

## KPI 3: Win Percentage

### Business Question

Which teams have the best winning performance?

### Formula

Win Percentage = Wins / Total Matches * 100

### Source File

matches.csv

### Final Gold Table

gold_team_season_performance

---

## KPI 4: Toss-to-Match Win Percentage

### Business Question

Does winning the toss improve the chance of winning the match?

### Formula

Toss-to-Match Win Percentage = Matches where toss winner also won match / Matches with valid winner * 100

### Source File

matches.csv

### Final Gold Table

gold_toss_impact_analysis

---

## KPI 5: Batter Runs

### Business Question

Which batters scored the most runs?

### Formula

Batter Runs = Sum of batsman_runs

### Source File

deliveries.csv

### Final Gold Table

gold_batter_scorecard

---

## KPI 6: Batter Strike Rate

### Business Question

Which batters scored runs the fastest?

### Formula

Batter Strike Rate = Batter Runs / Balls Faced * 100

### Source File

deliveries.csv

### Final Gold Table

gold_batter_scorecard

### Business Rule

Wides should not count as balls faced by the batter.

---

## KPI 7: Bowler Economy Rate

### Business Question

Which bowlers gave away the fewest runs per over?

### Formula

Bowler Economy Rate = Runs Conceded / Overs Bowled

### Source File

deliveries.csv

### Final Gold Table

gold_bowler_scorecard

### Business Rule

Only legal balls should count toward overs bowled.

---

## KPI 8: Venue Chase Win Percentage

### Business Question

Which venues favor teams batting second?

### Formula

Venue Chase Win Percentage = Matches won by chasing team / Completed matches at venue * 100

### Source File

matches.csv

### Final Gold Table

gold_venue_chasing_analysis

---

## KPI 9: Season Average Runs

### Business Question

How has scoring changed across IPL seasons?

### Formula

Season Average Runs = Total Runs in Season / Matches Played in Season

### Source Files

deliveries.csv  
matches.csv  
seasons.csv

### Final Gold Table

gold_season_scoring_trends

---

## Data Quality Rules

- Match ID should not be null.
- Match ID should be unique in the matches table.
- Team 1 and Team 2 should not be the same.
- Winner should be available for completed matches.
- Batter name should not be null.
- Bowler name should not be null.
- Runs should not be negative.
- Dashboard should use Gold tables, not raw CSV files.

---

## Interview Explanation

I created KPI definitions before building the dashboard so every metric had a clear business meaning, formula, source file, and target Gold table.

This helps ensure the dashboard is trustworthy and easy to validate.
