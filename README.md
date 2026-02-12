# ESPN CRICKET DATA ANALYSIS

### Dashboard Link :
## Data Source: Web Scraping
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
