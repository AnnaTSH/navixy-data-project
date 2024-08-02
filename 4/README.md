# 4. Working with ETL steps based on API queries.

After reading the [Navixy API description](https://developers.navixy.com/backend-api/getting-started/), I performed a series of API calls using Python to collect the most relevant information on the trackers (Navixy key entity, tracking device registered in our GPS monitoring system) available for the provided key. I also retrieved the corresponding tracks for the last month, with regard to the date of the last update for the trackers.

I show the way I requested the data in the [get_data notebook](get_data.ipynb)

Unfortunately, the data on the available trackers is insufficient: 

That's why I decided to use the tracks data to provide more information about the fleet on the dashboard. I conducted a short research and performed transformations to obtain the main statistics on the trackers' activity for the last month. Tracks data is available for only 14 out of the 16 trackers of the user.