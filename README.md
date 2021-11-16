# Surfs_Up
Module 9, Surf's Up with Advanced Data Storage and Retrieval. Surf's Up bruh!!

## Overview of the analysis: Explain the purpose of this analysis.
This analysis is to examine the feasibility of opening a Surf/Ice Cream Shop in Oahu Hawaii. We will take into account the temeperatures and percipitation amounts over 9 weather staions acattered around the area.

## Results
- First we queried the data base to get the date and the tobs (Temperature Observations) data from those columns. We then used the `.filter(extract)` method to extract only the dates that occured in June and December respectively.
- 
`june_temps = session.query(Measurement.date, Measurement.tobs).filter(extract("month", Measurement.date)==6).all()`

`dec_temps = session.query(Measurement.date, Measurement.tobs).filter(extract("month", Measurement.date)==12).all()`

- We then converted that information into a DataFrame, to make it easier to manupulate and visualize. We set the column names to Date and June/Dec Temperature.

`june_df = pd.DataFrame(june_temps, columns=['Date', 'June Temperature'])`

`dec_df = pd.DataFrame(dec_temps, columns=['Date', 'Dec Temperature'])`

- We then used the `.describe` method to generate the Statistical summary (the count of the data used, the average, the standard deviation, minimum, quarterlies and maximum).

![june_temps](https://github.com/chefcramer/surfs_up/blob/main/resources/June%20Temperatures.PNG)
![dec_temps](https://github.com/chefcramer/surfs_up/blob/main/resources/Dec%20Temperatures.PNG)

## Summary
- The data shows that there is very little difference in the temperatures recorded in 
Summary: Provide a high-level summary of the results and two additional queries that you would perform to gather more weather data for June and December. (two additional queries would be percip for june and december (too rainy to have icecream or surf??) and 

