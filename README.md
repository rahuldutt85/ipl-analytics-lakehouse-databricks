# IPL Analytics Lakehouse using Databricks

## Project Overview

This project analyzes IPL data from 2008 to 2025 using GitHub, Databricks, PySpark, SQL, and a lakehouse-style architecture.

The goal is to convert raw Kaggle CSV files into trusted analytics tables for match, team, player, venue, and season performance.

## Dataset Files

The Kaggle dataset contains:

- deliveries.csv
- matches.csv
- players.csv
- seasons.csv

Large raw CSV files are not stored in this GitHub repository.

Raw data should be downloaded from Kaggle and uploaded into Databricks or cloud storage.

## Business Goal

Build a sports analytics lakehouse that helps answer questions such as:

- Which teams have the highest win percentage?
- Does winning the toss improve the chance of winning the match?
- Which batters have the best strike rate?
- Which bowlers have the best economy rate?
- Which venues favor chasing teams?
- How has scoring changed across IPL seasons?

## Planned Lakehouse Architecture

```text
Raw Kaggle CSV Files
        ↓
Bronze Layer
Raw ingested data
        ↓
Silver Layer
Cleaned and standardized data
        ↓
Gold Layer
Business-ready KPI tables
