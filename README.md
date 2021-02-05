# SQLAlchemy Homework - Surfs Up!

This repository was created to explore Python and SQLAlchemy in combination to explore data related to a possible trip.  

## Step 1 - Climate Analysis and Exploration

To begin, use Python and SQLAlchemy to do basic climate analysis and data exploration of your climate database. All of the following analysis should be completed using SQLAlchemy ORM queries, Pandas, and Matplotlib.

### Precipitation Analysis
The following steps were completed for the preciptation analysis:
1) A query was designed to retrieve the last 12 months of precipitation data.
2) Selected only the `date` and `prcp` values.
3) Loaded the query results into a Pandas DataFrame and set the index to the date column.
4) Sorted the DataFrame values by `date`.
5) Ploted the results using the DataFrame `plot` method.
6) Used Pandas to print the summary statistics for the precipitation data.

### Station Analysis
The following steps were completed for the station analysis:
1) Designed a query to calculate the total number of stations.
2) Designed a query to find the most active stations.
3) Listed the stations and observation counts in descending order.
  - Observed which station has the highest number of observations?
4) Designed a query to retrieve the last 12 months of temperature observation data (TOBS).
  - Filtered by the station with the highest number of observations.
  - Ploted the results as a histogram with `bins=12`.

    ![station-histogram](Images/station-histogram.png)

- - -

## Step 2 - Climate App

After the initial analysis, a Flask API was designed based on the queries that were previously developed.

### Routes Made

* `/`

  * Home page.

  * Listed all routes that are available.

* `/api/v1.0/precipitation`

  * Converted the query results to a dictionary using `date` as the key and `prcp` as the value.

  * Returned the JSON representation of your dictionary.

* `/api/v1.0/stations`

  * Returned a JSON list of stations from the dataset.

* `/api/v1.0/tobs`
  * Queryed the dates and temperature observations of the most active station for the last year of data.
  
  * Returned a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

  * Returned a JSON list of the minimum temperature, the average temperature, and the max temperature for a given start or start-end range.

  * When given the start only, calculated `TMIN`, `TAVG`, and `TMAX` for all dates greater than and equal to the start date.

  * When given the start and the end date, calculated the `TMIN`, `TAVG`, and `TMAX` for dates between the start and end date inclusive.

### Temperature Analysis I

* This section explored if there is a temperature difference between months in Hawaii.  

* Identified the average temperature in June at all stations across all available years in the dataset. Do the same for December temperature.

* Used the t-test to determine whether the difference in the means, if any, is statistically significant.

### Temperature Analysis II
* Used the `calc_temps` function to calculate the min, avg, and max temperatures for your trip using the matching dates from the previous year.

* Ploted the min, avg, and max temperature from your previous query as a bar chart.

  * Used the average temperature as the bar height.

  * Used the peak-to-peak (TMAX-TMIN) value as the y error bar (YERR).

    ![temperature](Images/temperature.png)

### Daily Rainfall Average

* Calculated the rainfall per weather station using the previous year's matching dates.

* Calculated the daily normals. Normals are the averages for the min, avg, and max temperatures.

* Created a list of dates for your trip in the format `%m-%d`. Use the `daily_normals` function to calculate the normals for each date string and append the results to a list.

* Loaded the list of daily normals into a Pandas DataFrame and set the index equal to the date.

* Use Pandas to plot an area plot (`stacked=False`) for the daily normals.

  ![daily-normals](Images/daily-normals.png)

### Copyright

Trilogy Education Services © 2020. All Rights Reserved.
