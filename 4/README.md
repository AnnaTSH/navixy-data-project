# 4. Working with ETL steps based on API queries.

### Task: 

You work for a company that manages a vehicle fleet. You have a real-time monitoring system with detailed analysis of objects and their statuses. You need to organize a separate online dashboard, which will be available on a separate WEB resource. This dashboard should show summary information (current status) on vehicles in the fleet (for example, how many objects are in motion, how many are parked, and so on). Vehicle statuses and data can be collected using the get_states API call, connecting to https://api.eu.navixy.com/v2 using the key “feed00000000000000000000000cafe”.

### You need to:

Create a dashboard for any BI tool (Power BI, SuperSet, Metabase, etc.) with significant information that will be useful to the fleet manager. So that the created dashboard is located (embedded) on a separate WEB resource.

### Solution

After reading the [Navixy API description](https://developers.navixy.com/backend-api/getting-started/), I performed a series of API calls using Python to collect the most relevant information on the trackers (Navixy key entity, tracking device registered in our GPS monitoring system) available for the provided key. I also retrieved the corresponding tracks for the last month, with regard to the date of the last update for the trackers.

I show the way I requested the data in the [get_data](get_data.ipynb) notebook.

I first obtained the list of all available trackers and their current states. The attributes of interest for visualization are: connection_status, movement_status, latitude, and longitude. Interestingly, only one of the trackers turned out to be active; the others' last update date was 2024-07-23. I also tried to collect information on drivers, vehicles, fuel levels, sensor readings, and inputs ([available in the data folder](data)). However, most of the data is partial and therefore not valuable for visualization.

That's why I decided to use the tracks data to provide more information about the fleet on the dashboard. Although track data is available for only 14 out of 16 trackers, it allows for a detailed view of tracker activity: the number of tracks per day, duration (calculated based on start/end timestamps), distance traveled (to be compared with mileage, accessed through /tracker/stats/mileage endpoint), off-track (idle) time, and average speed. 

I conducted a short research and performed transformations to obtain the main statistics on the trackers' activity for the last month (2024-06-23 to 2024-07-23). See [track_calculations](track_calculations.ipynb) notebook.

I compared the aggregated distances and mileage from the mileage endpoint and found discrepancies between the daily distances traveled and the daily mileage for each tracker. On days with discrepancies, the end address of one track and the start address of the next track don't always match, indicating some vehicle travels may not be recorded as tracks. I decided that mileage data would be redundant and unnecessary for this specific dashboard.

The datasets used for the dashboard are:

- [tracker_label.csv](data/tracker_label.csv): Contains names for each tracker (driver's name and vehicle).
- [trackers_states_viz.csv](data/trackers_states_viz.csv): Contains tracker state data with unnecessary attributes removed.
- [stats.csv](data/stats.csv): Shows aggregated daily track data for each tracker.


![image](dashboard_full.jpg)

When the dashboard was ready in my Power BI Desktop, I published it to Power BI ([see instructions here](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-upload-desktop-files)).
Then I needed to obtain the embed link to [embed the dashboard](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-publish-to-web) into my newly created GitHub web page ([instructions](https://pages.github.com/)).

See the embedded dashboard through the link above: [annatsh.github.io/dashboard](https://annatsh.github.io/dashboard/).