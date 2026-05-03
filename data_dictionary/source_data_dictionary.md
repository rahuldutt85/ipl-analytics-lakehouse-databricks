# Source Data Dictionary

## Purpose

This document describes the four raw source files used in the IPL Analytics Lakehouse project.

The purpose of the data dictionary is to document the meaning of each source file and the important columns used for analytics, transformation, validation, and dashboard reporting.

## Source Files

| File Name | Row Count | Grain | Description |
|---|---:|---|---|
| deliveries.csv | 134,190 | One row per ball/delivery | Ball-by-ball IPL delivery data |
| matches.csv | 1,158 | One row per match | Match-level IPL information |
| players.csv | 580 | One row per player | Player reference/master data |
| seasons.csv | 18 | One row per season | Season-level summary data |

---

# 1. deliveries.csv

## File Purpose

The deliveries file contains ball-by-ball IPL data.

This file is used for batter analysis, bowler analysis, innings analysis, run calculations, wickets, strike rate, and economy rate.

## Grain

One row represents one delivery or ball event in a match.

## Key Columns

| Column Name | Description | Example Use |
|---|---|---|
| delivery_id | Unique identifier for each delivery row | Used to identify each ball event |
| match_id | Match identifier | Used to join deliveries to matches |
| innings | Innings number | Used to separate first and second innings |
| over | Over number | Used for over-level analysis |
| ball | Ball number within the over | Used for delivery sequence |
| batting_team | Team batting on the delivery | Used for team run analysis |
| bowling_team | Team bowling on the delivery | Used for bowling analysis |
| striker | Batter facing the delivery | Used for batter scorecard |
| non_striker | Batter at non-striker end | Used for partnership context |
| bowler | Bowler delivering the ball | Used for bowler scorecard |
| batsman_runs | Runs scored by the batter | Used for batter runs and strike rate |
| extra_runs | Runs from extras | Used for total score calculation |
| total_runs | Total runs from the delivery | Used for innings and season scoring |
| extra_type | Type of extra, if any | Used to handle wides/no-balls/byes |
| is_wicket | Indicates whether wicket fell | Used for wicket analysis |
| dismissal_type | Type of dismissal | Used to classify wicket types |
| dismissed_player | Player dismissed | Used for wicket tracking |
| fielder | Fielder involved in dismissal | Used for fielding analysis |

## Important Analytics Use Cases

- Batter runs
- Batter strike rate
- Bowler economy rate
- Wicket analysis
- Team scoring trends
- Innings-level scoring
- Season total runs

## Data Quality Checks

- delivery_id should not be null.
- match_id should not be null.
- innings should not be null.
- over should not be null.
- ball should not be null.
- striker should not be null.
- bowler should not be null.
- batsman_runs should not be negative.
- total_runs should not be negative.

---

# 2. matches.csv

## File Purpose

The matches file contains match-level IPL data.

This file is used for team performance, toss impact, venue analysis, match results, and season-level match trends.

## Grain

One row represents one IPL match.

## Key Columns

| Column Name | Description | Example Use |
|---|---|---|
| match_id | Unique identifier for each match | Used as primary match key |
| season | IPL season year | Used for season-level reporting |
| match_number | Match number within season | Used for match ordering |
| stage | League/playoff/final stage | Used for stage-level filtering |
| date | Match date | Used for time-based analysis |
| venue | Stadium or ground | Used for venue analysis |
| city | City where match was played | Used for location analysis |
| team1 | First participating team | Used for team participation |
| team2 | Second participating team | Used for team participation |
| toss_winner | Team that won the toss | Used for toss impact analysis |
| toss_decision | Bat or field decision | Used for toss decision analysis |
| first_innings_score | Runs scored in first innings | Used for scoring trend analysis |
| first_innings_wickets | Wickets lost in first innings | Used for innings analysis |
| first_innings_overs | Overs played in first innings | Used for run rate analysis |
| second_innings_score | Runs scored in second innings | Used for chase analysis |
| second_innings_wickets | Wickets lost in second innings | Used for chase analysis |
| second_innings_overs | Overs played in second innings | Used for run rate analysis |
| result | Match result type | Used to identify normal/no-result matches |
| winner | Match winning team | Used for win percentage |
| win_by | Win type, such as runs or wickets | Used for result analysis |
| win_margin | Win margin value | Used for margin analysis |
| player_of_match | Best player of the match | Used for player recognition analysis |
| umpire1 | First umpire | Optional reference field |
| umpire2 | Second umpire | Optional reference field |
| is_day_night | Indicates day/night match | Used for match condition analysis |

## Important Analytics Use Cases

- Team win percentage
- Toss-to-match win percentage
- Venue chasing advantage
- Season match count
- Win margin analysis
- Day/night match comparison

## Data Quality Checks

- match_id should not be null.
- match_id should be unique.
- season should not be null.
- team1 should not be null.
- team2 should not be null.
- team1 and team2 should not be the same.
- toss_winner should be either team1 or team2.
- winner should be either team1 or team2 for completed matches.
- date should be a valid date.

---

# 3. players.csv

## File Purpose

The players file contains player reference data.

This file is used as player master data for enriching batter and bowler analytics.

## Grain

One row represents one player.

## Key Columns

| Column Name | Description | Example Use |
|---|---|---|
| player_id | Unique player identifier | Used as player reference key |
| player_name | Player name | Used to join with batter/bowler names |
| nationality | Player nationality | Used for nationality analysis |
| dob_year | Year of birth | Used for age-related analysis |
| batting_style | Batting style | Used for player profile |
| bowling_style | Bowling style | Used for bowler profile |
| playing_role | Main playing role | Used for role-based analysis |
| ipl_debut_season | First IPL season played | Used for career timeline |
| last_season_played | Last IPL season played | Used for active/history analysis |
| is_capped_international | International experience flag | Used for player profile segmentation |
| base_price_lakh | Auction base price in lakh | Used for auction/value analysis |
| highest_auction_price_lakh | Highest auction price in lakh | Used for player value analysis |

## Important Analytics Use Cases

- Batter profile enrichment
- Bowler profile enrichment
- Player role analysis
- Nationality analysis
- Auction price analysis

## Data Quality Checks

- player_id should not be null.
- player_id should be unique.
- player_name should not be null.
- dob_year should be reasonable.
- ipl_debut_season should not be after last_season_played.
- highest_auction_price_lakh should not be negative.

---

# 4. seasons.csv

## File Purpose

The seasons file contains season-level IPL summary information.

This file is used for season trend analysis and high-level dashboard context.

## Grain

One row represents one IPL season.

## Key Columns

| Column Name | Description | Example Use |
|---|---|---|
| season | IPL season year | Used as season key |
| total_matches | Number of matches in the season | Used for season summary |
| num_teams | Number of teams in the season | Used for competition structure |
| champion | Season winner | Used for champion analysis |
| runner_up | Season runner-up | Used for final outcome analysis |
| orange_cap_winner | Top run scorer of the season | Used for season awards |
| purple_cap_winner | Top wicket taker of the season | Used for season awards |
| most_valuable_player | MVP of the season | Used for season awards |
| total_runs_scored | Total runs scored in season | Used for scoring trends |
| total_sixes | Total sixes hit in season | Used for batting trend analysis |
| total_fours | Total fours hit in season | Used for batting trend analysis |
| avg_first_innings_score | Average first innings score | Used for scoring trend dashboard |
| highest_team_total | Highest team total in season | Used for season records |
| lowest_team_total | Lowest team total in season | Used for season records |

## Important Analytics Use Cases

- Season scoring trends
- Champion history
- Award winner history
- Boundary trends
- Average first innings score trend

## Data Quality Checks

- season should not be null.
- season should be unique.
- total_matches should be greater than zero.
- num_teams should be greater than zero.
- total_runs_scored should not be negative.
- highest_team_total should be greater than or equal to lowest_team_total.

---

# Relationship Between Files

## Primary Relationships

| From File | Column | To File | Column | Relationship |
|---|---|---|---|---|
| deliveries.csv | match_id | matches.csv | match_id | Many deliveries belong to one match |
| matches.csv | season | seasons.csv | season | Many matches belong to one season |
| deliveries.csv | striker | players.csv | player_name | Batter name maps to player master |
| deliveries.csv | bowler | players.csv | player_name | Bowler name maps to player master |

## Important Relationship Notes

- matches.csv is the main match-level table.
- deliveries.csv is the most detailed fact table.
- players.csv is reference/master data.
- seasons.csv is season-level summary data.
- The strongest join key is match_id between deliveries and matches.
- Player joins may require name standardization before matching.

---

# Source-to-Layer Mapping

| Source File | Bronze Table | Silver Table | Main Gold Output |
|---|---|---|---|
| deliveries.csv | bronze_deliveries | silver_deliveries | gold_batter_scorecard, gold_bowler_scorecard |
| matches.csv | bronze_matches | silver_matches | gold_team_season_performance, gold_toss_impact_analysis, gold_venue_chasing_analysis |
| players.csv | bronze_players | silver_players | Player profile enrichment |
| seasons.csv | bronze_seasons | silver_seasons | gold_season_scoring_trends |

---

# Interview Explanation

I created a source data dictionary to document the meaning, grain, key fields, relationships, and data quality rules for each raw file.

This helped me understand the data before building Bronze, Silver, and Gold tables, and it also made the analytics pipeline easier to explain, validate, and maintain.
