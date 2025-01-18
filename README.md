# ATL Data Dev

The purpose of thhis repository is

## File Index
[Main Database](https://github.com/IceeCodee/ATLDataDev/blob/main/main) --> the database file (uses sqlite database) that contains three tables. The structure for these tables can be found in the database structure section

[stats.json](https://github.com/IceeCodee/ATLDataDev/blob/main/stats.json) --> contains json data from the following [mlb endpoint](https://statsapi.mlb.com/api/v1/stats?stats=season&group=pitching&playerPool=all&season=2018&teamId=144) 

[SQL Query Text](https://github.com/IceeCodee/ATLDataDev/blob/main/questions.sql.txt) --> contains the sql queries that attempt to answer the following three questions:

1. List all batters that had a single season WAR greater than 3 during the 2002 or 2003 seasons,
or a combined WAR greater than 5 over those two seasons. List in descending order of their
combined WAR for those seasons.

3. Write a query that returns every pitcher who threw at least one pitch for the Atlanta Braves in 2018, along with three 1/0 indicator columns for whether they reached the 1+ WAR, 2+ WAR,
or 3+ WAR cutoff in that year, along with a fourth column for their total yearly WAR

4. How many plate appearances did Luke Jackson have that reached a two-strike count but did
NOT result in a strikeout? Of those plate appearances, how many passed through 0-2, 1-2 or 2-
2 counts?

[statsAPImlb](https://github.com/IceeCodee/ATLDataDev/blob/main/statsAPImlb.xlsx) --> an excel file containing all relevant stats that can be used to reconcile the data with the PITCHBYPITCH table

[Jupyter Notebook](https://github.com/IceeCodee/ATLDataDev/blob/main/Question2.ipynb) --> A jupyter notebook containit a step by step on how I produced the csv file from the mlb API endpoint and any findings I found during EDA when comparing StatsAPI feed with the PITCHBYPITCH table.


## Database Structure
**War** -->
*A table of yearly batting WAR values by player from 2000-2005 (primary key: playerID/yearID)*

|Column Name| Data Type | Contraint |Description | Example| 
|----|-----|----|---|-----|
|playerID| TEXT| PK| Unique identifier for each player  | 119775 |
|name| TEXT| -| The last, first name of the baseball player| Nichting, Chris  |
|year|TEXT| PK | The season year in which the player was listed on the roster| 2001 |
|WAR| TEXT| - |Wins Above Placement | 0.4 |

**PERF** -->
*A table of aggregated stint-level pitching performance by player (primary key:
playerID/teamID/yearID)*

|Column Name| Data Type | Contraint | Description | Example| 
|----|-----|----|----|-----|
|playerID| TEXT|  PK  | Unique identifier for each player  |119775 |
|TeamKey|  TEXT| PK | Unique identifier for each team | 493247 |
|name| TEXT| -  |The last, first name of each player | Moylan, Peter |
|year| TEXT| PK |The season year in which the player was listed on the roster  |  2018|
|GS| TEXT| - | Games started | 18 |
|G|TEXT| -  | Games played| 67 |
|WAR|  TEXT| - | Wins Above Replacement| -0.3 |
|level| TEXT|  - | The league/level of play in which a player is participating | AAA |
|Org| TEXT| - | The organization the player is associcated with | ATL |

**PITCHBYPITCH** -->
*A table of pitch-level data (primary key: GameKey, INNING, PA_OF_INNING, TOP_BOT ,PITCH_OF_PA) that contains 1=yes and 0=no flag columns for whether different outcomes occurred on that pitch (single, double, triple, home run, hit, out, strikeout), information about the count before the pitch (BALLS, STRIKES), and a flag column for whether that pitch was the last pitch of the plate appearance.*

|Column Name| Data Type | Contraint | Description | Example| 
|----|-----|----|----|-----|
|GameKey| TEXT| PK | Unique identifier for the game played| 298505|
|GameDate| TEXT| - | The date in which the game was played | 6/6/2018 |
|PitcherName| TEXT| - | The last, first name of the pitcher on the mound | Venters, Jonnny |
|PitcherID| TEXT| - | Unique identifier for the pitcher on the mound  | 458924 |
|PA_OF_INNING| TEXT| PK | The batters plate appearence of the inning | 5 | 
|PITCH_OF_PA| TEXT| PK | Number of the pitch of the plate appearence | 3 |
|INNING| TEXT| PK | The current inning | 1 |
|TOP_BOT| TEXT| PK | Denotes whether it is the top (1) or bottom (2) of the inning | 2 |
|BALLS| TEXT| - | The number of balls in the count on a givin plate appearence | 2 | 
|STRIKES| TEXT| - | The number of balls in the count on a givin plate appearence | 0 | 
|SWING_TAKE| TEXT| - | Denotes whether the batter swung at a pitch or not | take | 
|IS_SINGLE| TEXT|  - | Denotes whether the outcome of the pitch was a single | 0 | 
|IS_DOUBLE| TEXT| - |  Denotes whether the outcome of the pitch was a double | 1 |
|IS_TRIPLE| TEXT| - |  Denotes whether the outcome of the pitch was a triple | 0 | 
|IS_HOMERUN| TEXT| - |  Denotes whether the outcome of the pitch was a homerun | 0 | 
|IS_HIT| TEXT| - |  Denotes whether the pitch was hit | 1 | 
|IS_OUT| TEXT| - | Denotes whether the batters attempt resulted in an out | 0 |  
|LAST_PITCH_OF_PA| TEXT| - | Denoted whether the pitch is the final pitch of a plate appearance | 
|IS_STRIKEOUT| TEXT | - | Denotes whether the batters attempt resulted in a strikeout | 0|


## Findings

## Conclusion




