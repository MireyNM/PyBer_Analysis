# PyBer_Analysis
Module 5 in CU Bootcamp
## Project Overview 
In this project, we are working for a Python-based ridesharing app company. Our first assignment was to analyze all the rideshare data from January to early May of 2019 and create a compelling visualization for the CEO, V. Isualize. Our second assignment was to do the following tasks: </br>
1. Use Python and Pandas to create a summary DataFrame of the ride-sharing data by city type. </br>
2. Use Pandas and Matplotlib to create a multiple-line graph that shows the total weekly fares for each city type. 

### Purpose
The aim of this work is to understand how the data differs by city type and how those differences could be used by decision-makers at PyBer.

## Resources 
- Data Source: city_data.csv and ride_data.csv
- Software: Python 3.7.13, Conda 4.14.0, Jupyter Notebook. 
- Libraries: Matplotlib and Pandas.

## Analysis of Data
The first major piece of our code is to import required dependencies: <br /> 
``` import matplotlib.pyplot as plt ``` <br /> 
```import pandas as pd``` <br /> 
Now we can start our analysis in order to complete our task. <br /> 


To check the full code please go to the following link:
https://github.com/MireyNM/PyBer_Analysis/blob/main/PyBer_Challenge.ipynb

**Collect the city and ride data into a DataFrame.** <br />
To collect the city and ride data, we need to import it into a structure that Python and Pandas can work on. Therefore, we have created file paths, to the external files ``` city_data.csv ```  and ``` ride_data.csv ```  saved in the "Resources" folder. And we used ```pd.read_csv``` to be able to read the file. <br />
After that, we have used ```pd.merge``` to merge both files together and using the ```head()``` function, we have displayed the first 5 rows in order to verify that the data was properly imported (See Table 1)

<p align = "center">
<img width="499" alt="Outcomes_vs_Goals" src="https://user-images.githubusercontent.com/109363759/192002258-d8993248-3c22-43b8-ad9d-10a7100dc068.png">
</p>
<p align = "center">
Table 1 - Display the first 5 rows of the PyBer Data.
</p>


### Get a ride-sharing summary DataFrame by city type
Using the Pandas ```groupby()``` function with the ```count()``` and ```sum()``` methods on PyBer DataFrame columns we have calculated for each city type: 
- The total number of rides
- The total number of drivers.
 - The total amount of fares.
- The average fare per ride 
- The average fare per driver.

Finally, we have created the PyBer summary DataFrame with all the data gathered above and we have formated the columns and removed the index name ("type"). (See Table 2)

<p align = "center">
<img width="499" alt="Outcomes_vs_Goals" src="https://user-images.githubusercontent.com/109363759/192002362-8864cc3e-287f-46c3-923d-1f2be825a7b8.png">
</p>
<p align = "center">
Table 2 - PyBer summary DataFrame.
</p>


### Draw a multiple-line chart of total fares for each city type
- Using ```groupby()``` we have created a new DataFrame showing the sum of the fares 
for each date where the indices are the city type and date. Then we have reset the index.

- To get the total fares for each type of city by the date, we have created a pivot table with the 'date' as the index, the columns ='type', and values='fare' (See Table 3)

<p align = "center">
<img width="499" alt="Outcomes_vs_Goals" src="https://user-images.githubusercontent.com/109363759/192002421-a62b3db1-fcac-4a73-a2e0-6024f33cedb6.png">
</p>
<p align = "center">
Table 3 - Pivot table showing the total fares for each type of city by the date.
</p>

- Using ```.loc['2019-01-01':'2019-04-29'] ```  we have created a new DataFrame from the pivot table in order to get the total fares for each type of city from January till April. (See Table 4)
<p align = "center">
<img width="499" alt="Outcomes_vs_Goals" src="https://user-images.githubusercontent.com/109363759/192002520-4b4dab9b-a39a-42bb-b759-99d5e1314236.png">
</p>
<p align = "center">
Table 4 - New DataFrame showing the total of the fares from January till April.
</p>

**Note** 
In the Challenge they asked for a date range "2019-01-01 through 2019-04-28" while in the code's notes it was written till 2019-04-29. I chose to create the data till 29 as its 1 more day in April (not a new month).

-  Before using the resample method we needed to set the "date" index to datetime data type. After that, we have used  the ```resample()``` function, in order to resample the data in weekly bins so we can get the total fares for each week (See Table 5).
<p align = "center">
<img width="499" alt="Outcomes_vs_Goals" src="https://user-images.githubusercontent.com/109363759/192002598-1ef98d23-5b88-4a88-8e91-69088d761f2d.png">
</p>
<p align = "center">
Table 5 - DataFrame showing the sum of the fares for each week.
</p>

- Finally, we have plotted the resample DataFrame using the ```df.plot()``` function and the object-oriented interface method (See Fig.1)

<p align = "center">
<img width="499" alt="Outcomes_vs_Goals" src="https://user-images.githubusercontent.com/109363759/192002667-b2fe9514-8831-48e2-9f1c-a1e5aec864fd.png">
</p>
<p align = "center">
Fig.1 - Multiple-line chart showing the total fares per city type.
</p>

## Results 
### Ride-sharing summary DataFrame by city type
The ride-sharing summary DataFrame table (See Table 2) shows us the follow:
- The number of total rides is the lowest for rural cities (125 rides) while it is 5 times more for suburban cities (625 rides) and 13 times more for urban cities (1,625 rides). 
- The number of drivers for rural cities is the lowest (78 drivers), while it is around 6 times more for suburban cities (490 drivers) and 30 times more for urban cities (2,405).
- The total amount of fares for rural cities is the lowest ($4,327,93), while it is around 4.5 times more for suburban cities ($19,356.33) and around 9 times more for urban cities ($39,854.38)
- The average fare per ride is the highest for rural cities ($34.62). It drops to $30.97 for suburban cities and to $24.53 for urban cities. 
- The average fare per driver is the highest for rural cities ($55.49). It drops to $39.50 for suburban cities and to $16.57 for urban cities. 
### The multiple-line chart of total fares for each city type
The above multiple-line chart (See Fig.1) show us the following:
- The amount of total fare for urban cities (yellow trend) is higher than the amount of total fares in suburban cities (rend trend) and rural cities (blue trend) for all the duration going from January till end of April.
- The amount of total fare for urban cities (yellow trend) is the highest for all the duration going from January till April. This amount ranges between 1500USD and 2500USD. 
- The amount of total fare for suburban cities (red trend) falls in between urban and rural cities with amount of total fares higher than 500USD but less than 1500USD.
- The amount of total fare for rural cities (blue trend) is the lowest for all the duration going from January till April. The amount of total fares is less than 500USD in the rural cities.
- A small peak is noticed for all 3 cities at the end of February 2019. This could be the result of an event that happened in the country.

## Summary 
The ride-sharing summary DataFrame and the multiple-line chart allow us to make the following analyzes:
- The total number of rides is low in rural cities. This could be due to the low number of drivers in these areas. Therefore, the average fare per ride and per driver is higher. This is good for the drivers, but it will reflect badly on the customers who would not be able to afford their rides.
- The total number of rides is the highest in urban cities. But since the number of drivers is the highest as well, the average fare per ride and per driver is the lowest in these areas, as the competition is higher between drivers. This will have positive impact on the customers as it is making the rides more affordable for them, but the profit will be less for drivers. 
- The total fare is the highest in urban cities (around 2 times more for suburban cities and 9 times more than rural ones). These values show that PyBer revenue occurs mostly from urban cities which may decrease their interest in rural and suburban cities and therefore decrease their chance of a potential revenue grow in these areas. 

I would suggest for the decision-makers in PyBer company the following:
 1. Hiring more drivers in rural and suburban areas in order to increase the competition between drivers and decrease the average fare per ride which will open the possibility of getting new potential customers who are able to afford a lower fare. 
2. Pay attention to the number of drivers in urban cities and the fare per drive they get. In case the average fare per drivers decreases more, we may face a new problem which is drivers leaving work.

3. Gathering more data to find out if there could be another reason behind the low number of total rides in rural and suburban cities. Maybe the distance traveled in each ride is longer therefore the average fare per ride is higher and people prefer to use their cars instead.  
