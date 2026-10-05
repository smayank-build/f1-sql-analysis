# 1. Navigate to your project directory
cd M:\5-Projects\AI_ML\f1-sql-analysis

# 2. Configure GitHub language recognition to show SQL
Set-Content -Path .gitattributes -Value "* linguist-detectable=true`n*.sql linguist-language=SQL`n*.sh linguist-vendored`n*.awk linguist-vendored"

# 3. Create the comprehensive README.md file
@'
# Formula 1 Race Performance & Historical Analytics (SQL)

## Executive Summary
This project delivers an end-to-end relational data analysis of 70+ years of Formula 1 World Championship history (1950–present). Utilizing advanced SQL techniques—including Window Functions, Common Table Expressions (CTEs), Subqueries, and Gaps-and-Islands logic—this repository analyzes driver consistency, qualifying impact, pit-stop strategies, and decade-over-decade dominance.

Data is sourced from the **Ergast F1 Database** mirror provided by the [Grand Prix Stats](https://www.grandprixstats.org) initiative.

---

## Dataset & Architecture
The underlying database consists of **14 relational tables** tracking historical races, driver statistics, constructor standings, lap times, pit stops, and qualifying performances.

* **Key Entities:** `drivers`, `constructors`, `races`, `results`, `qualifying`, `pit_stops`, `lap_times`, `status`.
* **Scale:** Over 100K+ lap-time entries, 1,000+ Grand Prix events, and 800+ drivers.

---

## Analytical Scope & Key SQL Concepts

The analysis is organized into modular `.sql` scripts covering specific operational and strategic dimensions:

### 1. Driver & Constructor Dominance
* **Metrics:** Wins, podium finishes, and cumulative career points progression.
* **SQL Techniques:** `SUM() OVER(PARTITION BY ... ORDER BY ...)` running totals, multi-table `INNER JOIN` operations.

### 2. Grid Position vs. Final Outcome
* **Metrics:** Impact of qualifying position on race outcomes; average positions gained/lost per circuit.
* **SQL Techniques:** Conditional aggregation, `CASE WHEN`, positional delta calculations.

### 3. Lap-Time Consistency & Strategy
* **Metrics:** Lap-time variance during races, tire wear proxies, and pit-stop performance per constructor.
* **SQL Techniques:** CTEs, `AVG()`, `STDDEV()`, and time-delta conversions.

### 4. Reliability & DNF Tracking
* **Metrics:** Did Not Finish (DNF) rates grouped by era, mechanical failure trends, and constructor breakdown.
* **SQL Techniques:** Status code mapping, filtering aggregated groups with `HAVING`.

### 5. Historical Rankings & Win Streaks
* **Metrics:** Top drivers per decade and longest consecutive winning streaks.
* **SQL Techniques:** `RANK()`, `DENSE_RANK()`, and Gaps-and-Islands pattern matching using `ROW_NUMBER()`.

---

## Key Insights & Findings

1. **Qualifying Advantage:** Pole-sitters win approximately **40%+** of all Grand Prix races, with street circuits like Monaco displaying an even higher correlation between grid position and victory.
2. **Pit Strategy:** Top-tier constructors consistently maintain lower average pit-stop durations and lower variance across a season compared to midfield teams.
3. **Era Dominance:** Using window ranking across decades highlights distinct eras of single-driver dominance (e.g., 1950s, 2000s, 2010s).

---

## Repository Structure
