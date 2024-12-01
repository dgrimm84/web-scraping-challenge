# web-scraping-challenge
# Analysis
#### <ins>How many months exist on Mars?</ins>

- Since Mars doesn't have one moon to measure a month by like the Earth, there are no officially recognized ways to divide a Martian year into a certain number of months.  The general consensus to measure a Martian year as closely to an Earth year as possible is to divide a Martian year into 24 months.
- In this dataset however, there are 12 unique months in the Martian year of data collection. 
- This is captured by printing the number of unique month values with the nunique() function.  The code and print function are below:

  ![image](https://github.com/user-attachments/assets/da67c83a-9e84-4eff-98bc-c82f3f51063e)

#### <ins>How many Martian days worth of data are there?</ins>
- A sol is the measurement of one day on Mars (the time is takes for it to complete one full rotation on its axis)
- To calculate the number of sols in this dataset, I used the nuniquie() function on the "sol" column.  This returns the number of unique numbers in this column
- The code & print function are below:

  ![image](https://github.com/user-attachments/assets/66446a03-1096-44ca-a12f-35e1bbbb84ae)

#### <ins>Which month, on average, has the lowest temperature? The highest?</ins>
- In order to capture this data, I first needed to get the average temperature for each month in the dataset
- To do this, I used the group_by function to group the data by month, then, I took the mean() of min_temp for each month grouping
- Once I captured this, I sorted the min_temp results in a new dataframe in ascending order so that the lowest temperature was first and the highest was last
- Then, to capture the month with the lowest temperature, I took the ['month'].iloc[0] of the newly-sorted dataframe to get the first month in the column (which is the month with the lowest average temperature because I sorted the temp data).  And, to get the lowest temperature, I used ['min_temp'].min() to get the lowest value in the min_temp column.
- To capture the month with the lowest temperature, I took the ['month'].iloc[-1] of this newly-sorted dataframe to get the last month in the column (which is the month with the highest average temperature because I sorted the temp data). And, to get the highest temperature, I used ['min_temp'].max() to get the highest value in the min_temp column. 
- This is expressed with print functions and graphically below:

  ![image](https://github.com/user-attachments/assets/b87531b1-e489-4015-801f-a35dc8448037)

#### <ins>Which month, on average, has the lowest atmospheric pressure? The highest?</ins>
- In order to capture this data, I first needed to get the average atmospheric pressure for each month in the dataset
- To do this, I used the group_by() function to group the data by month, then, I took the mean() of pressure values for each month grouping
- Once I captured this, I sorted the pressure results in a new dataframe in ascending order so that the lowest average atmospheric pressure was first and the highest was last
- Then, to capture the month with the lowest average atmospheric pressure, I took the ['month'].iloc[0] of the newly-sorted dataframe to get the first month in the column (which is the month with the lowest average atmospheric pressure because I sorted the pressure values).  And, to get the lowest average atmospheric pressure, I used ['pressure'].min() to get the lowest value in the pressure column.
- Then, to capture the month with the highest average atmospheric pressure, I took the ['month'].iloc[-1] of the newly-sorted dataframe to get the last month in the column (which is the month with the highest average atmospheric pressure because I sorted the pressure values).  And, to get the highest average atmospheric pressure, I used ['pressure'].max() to get the highest value in the pressure column.
- This is expressed with print functions and graphically below:

  ![image](https://github.com/user-attachments/assets/d8b50087-b139-49bf-8366-2c494641a35e)

#### <ins>How many terrestrial days exist in a Martian year? A visual estimate within 25% was made.</ins>
- In order to give an accurate estimate based on graphical data, I first needed to create a plot of the number of terrestrial days (Earth days) as they relate to the Minimum Temperature values captured by the Curiosity Rover
- To do this, I created a pandas plot using the pd.plot() function with the "sol" column as the x-axis and "min_temp" as the y-axis
- In this plotted graph, it is easy to see a clear cycle of temperatures.  This dataset begins in the 6th month of the Martian calendar, completes two full 12 month cycles, and then shows a 5 month period at the end.
- A Martian year is calculated by Mars making a full orbit around the sun.  This means that where the Curiosity Rover is capturing temperature data will be facing the sun during the "summer" for that part of the planet, and facing away from the sun during the "winter" for that part of the planet.
- So, in the graphical data, a valley of low temperatures at the beginning of the full 12 month cycle can be seen (winter), then a peak of high temperatures can be seen halfway through the cycle (summer), and then the temperature readings go back down to approximately the same level as the first valley of low temperatures (winter again). 
- Knowing this, we can draw a visual estimate of how many terrestrial days exist in a martian year. These are represented by the black lines drawn on the graph below.
- 1200 terrestrial days MINUS 510 terrestrial days = 690 terrestrial days in one temperature cycle (year).  
- Looking up on NASA's site, the actual measured value of Earth days in a Martian year is approximately 687 days.  This shows that our visual / graphical estimate of this value was very accurate

  ![image](https://github.com/user-attachments/assets/a661cbf1-73c3-45f9-b20e-ebf969625cfd)


