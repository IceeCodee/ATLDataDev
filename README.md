# ATL Data Dev

The purpose of thhis repository is

## File Index
[Main Database](https://github.com/IceeCodee/ATLDataDev/blob/main/main) --> the database file (uses sqlite database) that contains three tables. 
> [!NOTE]
> The structure for these tables can be found in the database structure section


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

[Jupyter Notebook](https://github.com/IceeCodee/ATLDataDev/blob/main/Question2.ipynb) --> A jupyter notebook 


## Three tables
**War**
*A table of yearly batting WAR values by player from 2000-2005 (primary key: playerID/yearID)*

**PERF**
*A table of aggregated stint-level pitching performance by player (primary key:
playerID/teamID/yearID)*

**PITCHBYPITCH**
*A table of pitch-level data (primary key: GameKey, INNING, PA_OF_INNING, TOP_BOT ,PITCH_OF_PA) that contains 1=yes and 0=no flag columns for whether different outcomes occurred on that pitch (single, double, triple, home run, hit, out, strikeout), information about the count before the pitch (BALLS, STRIKES), and a flag column for whether that pitch was the last pitch of the plate appearance.*

