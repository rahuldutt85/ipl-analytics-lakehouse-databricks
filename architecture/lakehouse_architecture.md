# IPL Analytics Lakehouse Architecture

## Purpose

This document explains the end-to-end architecture for the IPL Analytics Lakehouse project.

The goal of the architecture is to convert raw IPL CSV files into clean, trusted, business-ready analytics tables that can support SQL reporting and dashboard insights.

## High-Level Architecture

The project follows this flow:

Raw IPL CSV Files  
→ Databricks File Storage  
→ Bronze Delta Tables  
→ Silver Delta Tables  
→ Gold KPI Tables  
→ SQL Queries  
→ Dashboard

## Architecture Diagram

```text
Kaggle / Local CSV Files
        |
        v
Databricks File Upload / DBFS
        |
        v
Bronze Layer
Raw ingested tables
        |
        v
Silver Layer
Cleaned and standardized tables
        |
        v
Gold Layer
Business-ready KPI tables
        |
        v
Databricks SQL Queries
        |
        v
Dashboard / Reporting Layer
