# navixy-data-project
# Collection of home assignment solutions for Navixy (SquareGPS)

[Full home assignment (in Russian)](https://github.com/AnnaTSH/navixy-data-project/blob/main/%D0%A2%D0%B5%D1%81%D1%82%D0%BE%D0%B2%D1%8B%D0%B5%20%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D1%8F_%20SquareGPS%20_%20DataAnalyst.pdf)

## 3. Building relationships between data and entities to create customized reports:

### Task: 

You work with big data coming from vehicles that are monitored 24/7. In addition to vehicle telematics data, such as
coordinates, speed, distance traveled, fuel level in the tank, etc., the data base contains other data sets: driver data (name, shift time, driver's license expiration date, etc.) and data on geozones that drivers visit according to issued tasks (location, arrival time, departure time, lateness, task completion status, etc.). It is logical to assume that the same parameters and attributes can be used for analytics on different entities, for example, the speed parameter can be inherent in both the vehicle and the driver.

Moreover, based on some parameters, additional entities with their own attributes can be formed. For example, the entity “speeding event” for a vehicle or driver, or “vehicle status at the current moment in time”: moving or parked.

### You need to:

1) Describe the model for defining relationships between a) monitoring objects, b) their parameters, and c) entities. For instance, present it in the form of a database schema.
2) Provide examples of specific reports that are created based on the created relationships between parameters and entities.

## [4. Working with ETL steps based on API queries.](https://github.com/AnnaTSH/navixy-data-project/tree/main/4#readme)

### Task: 

You work for a company that manages a vehicle fleet. You have a real-time monitoring system with detailed analysis of objects and their statuses. You need to organize a separate online dashboard, which will be available on a separate WEB resource. This dashboard should show summary information (current status) on vehicles in the fleet (for example, how many objects are in motion, how many are parked, and so on). Vehicle statuses and data can be collected using the get_states API call, connecting to https://api.eu.navixy.com/v2 using the key “feed00000000000000000000000cafe”.

### You need to:

Create a dashboard for any BI tool (Power BI, SuperSet, Metabase, etc.) with significant information that will be useful to the fleet manager. So that the created dashboard is located (embedded) on a separate WEB resource.
