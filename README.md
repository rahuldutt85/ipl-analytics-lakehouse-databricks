# IPL Analytics Lakehouse using Databricks

## Project Overview

This project builds an end-to-end IPL analytics lakehouse using GitHub, Databricks, PySpark, SQL, Delta Lake concepts, and dashboard reporting.

The goal is to convert raw IPL CSV files into trusted analytics-ready tables that can answer business questions about team performance, player performance, toss impact, venue behavior, and season scoring trends.

## Business Problem

IPL data is available in raw CSV format, but raw files are not directly useful for business reporting.

This project solves that problem by creating a structured analytics pipeline:

Raw CSV Files  
→ Bronze Tables  
→ Silver Tables  
→ Gold KPI Tables  
→ SQL Dashboard

The final dashboard helps answer questions such as:

- Which teams have the highest win percentage?
- Does winning the toss improve the chance of winning the match?
- Which batters have the best strike rate?
- Which bowlers have the best economy rate?
- Which venues favor chasing teams?
- How has scoring changed across IPL seasons?

## Source Data

The project uses four source files:

| File Name | Description |
|---|---|
| deliveries.csv | Ball-by-ball delivery-level IPL data |
| matches.csv | Match-level IPL data |
| players.csv | Player reference data |
| seasons.csv | Season-level IPL summary data |

Large raw CSV files are not stored directly in this GitHub repository.

Raw files should be uploaded into Databricks or cloud storage before running the notebooks.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| GitHub | Version control and project documentation |
| Databricks | Lakehouse development platform |
| PySpark | Data ingestion and transformation |
| SQL | KPI creation, validation, and analytics |
| Delta Lake | Reliable lakehouse table storage concept |
| Databricks SQL Dashboard | Business reporting and visualization |

## Lakehouse Architecture

This project follows a Medallion Architecture pattern.

### Bronze Layer

The Bronze layer stores raw ingested data from the original CSV files.

Bronze tables:

- bronze_deliveries
- bronze_matches
- bronze_players
- bronze_seasons

Purpose:

- Preserve raw source data
- Add ingestion metadata
- Keep a historical raw copy
- Support traceability back to source files

### Silver Layer

The Silver layer stores cleaned and standardized data.

Silver tables:

- silver_deliveries
- silver_matches
- silver_players
- silver_seasons

Purpose:

- Standardize column names
- Clean nulls and duplicates
- Standardize team, player, and venue names
- Create trusted data for analysis

### Gold Layer

The Gold layer stores business-ready KPI tables.

Gold tables:

- gold_team_season_performance
- gold_batter_scorecard
- gold_bowler_scorecard
- gold_toss_impact_analysis
- gold_venue_chasing_analysis
- gold_season_scoring_trends

Purpose:

- Support dashboard reporting
- Provide business-friendly metrics
- Enable SQL-based analysis
- Create trusted executive-ready outputs

## Key KPIs

This project calculates the following KPIs:

| KPI | Description |
|---|---|
| Win Percentage | Percentage of matches won by a team |
| Toss-to-Match Win Percentage | How often toss winners also win the match |
| Batter Strike Rate | Runs scored per 100 balls faced |
| Bowler Economy Rate | Runs conceded per over |
| Venue Chase Win Percentage | Percentage of matches won by chasing teams at a venue |
| Average Runs by Season | Scoring trend across IPL seasons |

## Dashboard Pages

The final dashboard will include:

1. Executive Overview
2. Team Performance
3. Batter Analytics
4. Bowler Analytics
5. Toss Impact
6. Venue Analysis
7. Season Trends

## Project Outcome

At the end of this project, the raw IPL CSV files are transformed into clean, trusted, analytics-ready tables.

The project demonstrates:

- Business problem framing
- Data source understanding
- Lakehouse architecture
- PySpark data engineering
- SQL KPI development
- Data validation
- Dashboard design
- Business analytics storytelling

## Interview Summary

I built an end-to-end IPL analytics lakehouse using GitHub, Databricks, PySpark, SQL, Delta Lake concepts, and dashboard reporting.

I ingested four raw CSV files into Bronze tables, cleaned and standardized the data into Silver tables, created Gold KPI tables for business reporting, validated the results using SQL, and designed a dashboard to analyze team, player, venue, toss, and season-level performance.
