# ESPN CRICKET DATA ANALYSIS

### Dashboard Link :
### Data Source: Web Scraping
## Problem Statement
This dashboard helps sports analysts, cricket fans, and team management understand player and team performance using ESPN cricket match data. It provides insights into batting, bowling, and match outcomes so users can evaluate strengths, weaknesses, and consistency of players across different formats and matches.

Through various performance metrics such as total runs, strike rate, batting average, wickets taken, economy rate, and match results, the dashboard highlights key performance indicators. This allows analysts to identify top-performing players, underperforming players, and areas where teams need improvement.

The dashboard also analyzes match patterns such as venue performance, toss impact, and win percentage based on batting first or chasing. Using this information, teams and analysts can make better strategic decisions for future matches.

Since some players show inconsistent performance across matches, teams need to focus on player form, selection strategy, and role optimization.

Additionally, match statistics such as average runs scored, wickets taken, and performance across venues help identify favorable conditions and improve match planning and team strategy.


### Steps followed 

- Step 1 :I extracted ODI match data for India and South Africa, including batting, bowling, and fielding statistics, by performing web scraping from ESPN Cricinfo.
- Step 2 :Load data into Power BI Desktop.
- Step 3 :Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 4 :Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 5 :Designed and developed three report pages, namely Batting, Bowling, and Fielding, in accordance with the project requirements.
- Step 6 :In the report view, under the view tab, theme was selected.
- Step 7 :To allow users to analyze individual performance, player-based slicers were incorporated into each of the three report pages.
- Step 8 :A time-span (year) selection visual was incorporated to enable users to view performance metrics for selected years.
- Step 9 :Various KPI card visuals were implemented to summarize core batting performance indicators, including Strike Rate, Runs Scored, Not Outs, Matches, Innings, 	  Highest Score, Balls Faced, Batting Average, Boundary Counts (4s and 6s), Centuries, and Ducks.
- Step 10 :The Bowling report page analyzes player bowling performance using multiple KPI visuals and interactive charts. Key bowling metrics such as Wickets Taken, 	   Bowling Average, Economy Rate, Strike Rate, Runs Conceded, Overs Bowled, Maidens, and Best Bowling Figures are displayed to evaluate bowler effectiveness.
- Step 11 :Implemented a Strike Rate dimension table and utilized a DAX LOOKUP function to assign performance categories dynamically based on player strike rate 	   values.
- Step 12 :Following DAX expression was written for to create categories:

		 Category = LOOKUPVALUE('Strike Rate Table'[Category],'Strike Rate Table'[Strike Rate], Batting_Data[Strike Rate])

- Step 13 :Created a Rank column that ranks players according to their Strike Rate, leveraging the DAX RANKX function for dynamic performance comparison.

- Step 14 :Following DAX expression was written for to create Rank column:

		Rank = RANKX(all(Batting_Data), Batting_Data[Strike Rate],,DESC, Dense)

- Step 14 :Created a calculated column to determine the deviation of runs for performance analysis.
- Step 15 :Following DAX expression was written for to create Deviation Runs column:

		Deviation_runs = Batting_Data[Runs] - AVERAGE(Batting_Data[Runs])

- Step 16 :Implemented a calculated column with the DAX ABS function to convert run deviations into absolute values for consistent performance analysis.
- Step 17 :Following DAX expression was written for to create Deviation Runs column:
		Absolute_deviation_runs = ABS(Batting_Data[Deviation_runs])
- Step 18 : The report was then published to Power BI Service.

# Report Snapshot (Power BI DESKTOP)
<img width="885" height="497" alt="Image" src="https://github.com/user-attachments/assets/3a6a7334-d99e-4615-8eae-67d7b5bbe924" />

# Insights:

## 1. Strike Rate-Based Player Segmentation:

Players were segmented into performance categories using strike rate thresholds to understand batting intent and match impact:

Very Low (SR 1–50): Defensive players with slow scoring pace, typically contributing to innings stability but reducing run acceleration.

Normal (SR 50–100): Balanced batters maintaining steady scoring without high risk, suitable for middle-order consolidation.

Aggressive (SR 100–150): Attacking players capable of increasing run rate and building momentum during middle overs.

Explosive (SR 150+): High-impact finishers who significantly accelerate scoring in death overs and short match situations.


## 2.Using deviation and absolute deviation:

Players with lower absolute deviation showed stable performance across matches, while some high run-scorers were highly inconsistent.

Meaning:
	A player with fewer total runs might be more valuable than a player with higher runs.

## 3. Dashboard shows:

Certain players did not rank among top run-scorers but ranked highly when consistency and strike rate were combined, identifying undervalued players.

## Conclusion:
The findings suggest that optimal team selection should consider a balance between consistency and scoring aggression. A well-structured team requires stable accumulators to sustain innings and aggressive finishers to accelerate scoring, rather than relying solely on players with the highest aggregate runs. The dashboard enables data-driven decision-making for player evaluation, role assignment, and strategic team composition.
