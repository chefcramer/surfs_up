# Surfs_Up
Module 9, Surf's Up with Advanced Data Storage and Retrieval. Surf's Up bruh!!

## Overview of the analysis: Explain the purpose of this analysis.
This analysis is to examine the feasibility of opening a Surf/Ice Cream Shop in Oahu Hawaii. We will take into account the temeperatures and percipitation amounts over 9 weather staions scattered around the area.

## Results
- First we queried the data base to get the date and the tobs (Temperature Observations) data from those columns. We then used the `.filter(extract)` method to extract only the dates that occured in June and December respectively.

`june_temps = session.query(Measurement.date, Measurement.tobs).filter(extract("month", Measurement.date)==6).all()`

`dec_temps = session.query(Measurement.date, Measurement.tobs).filter(extract("month", Measurement.date)==12).all()`

- We then converted that information into a DataFrame, to make it easier to manupulate and visualize. We set the column names to Date and June/Dec Temperature.

`june_df = pd.DataFrame(june_temps, columns=['Date', 'June Temperature'])`

`dec_df = pd.DataFrame(dec_temps, columns=['Date', 'Dec Temperature'])`

- We then used the `.describe` method to generate the Statistical summary (the count of the data used, the average, the standard deviation, minimum, quarterlies and maximum).

![june_temps](https://github.com/chefcramer/surfs_up/blob/main/resources/June%20Temperatures.PNG)
![dec_temps](https://github.com/chefcramer/surfs_up/blob/main/resources/Dec%20Temperatures.PNG)

## Summary
- The data shows that there is very little difference in the temperatures recorded in June and December. The difference between the two months being around one standard deviation of each other.
  - The Average Temperatures being 74.94 in June and 71.04 in December.
  - The Maxamum Temperatures being 85 in June and 83 in December.
  - The Minimum Temperatures being 64 in June and 56 in December.

- I further analysed this data by examining the precipitation recorded in this same timeframe. Even if its "nice" out, no one will want ice cream or to surf if its too rainy. The data shows that the two months are also very similar in amount of rainfall recorded, with December being SLIGHTLY cooler and wetter overall.

```
june_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract("month", Measurement.date)==6).all()
june_prcp_df = pd.DataFrame(june_prcp, columns=['Date', 'June Precipitation'])
june_prcp_df.describe()
```

```
dec_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract("month", Measurement.date)==12).all()
dec_prcp_df = pd.DataFrame(dec_prcp, columns=['Date', 'Dec Precipitation'])
dec_prcp_df.describe()
```
![june_prcp](https://github.com/chefcramer/surfs_up/blob/main/resources/June%20Precp.PNG)
![Dec_prcp](https://github.com/chefcramer/surfs_up/blob/main/resources/dec%20precp.PNG)

- In conclusion, it's **NICE** in Hawaii. There is no reason that a Surf/Ice Cream shop would not do very well. The weatherman in Oahu must have the easiest job on the planet;
  - "We go live to downtown Honolulu, with our weatherman Bill. How's it looking out there Bill?'
  - "...Nice! Back to you in the studio."
