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

# Files present in this repository and their function

- <ins>part_1_mars_news.ipynb</ins>
  - This file begins by using splinter to import the Browser function, assigning the ChromeDriver to this browser object, and visiting a static website created by edX for educational purposes.
  - The html from this site is parsed and assigned to a Beautiful Soup object
  - The main news element container which includes all the titles and text previews of these news articles is assigned to an object
  - All rows which contain each news article is captured as well
  - The code loops through these rows creating a dictionary of the title and preview text for each news article
  - These dictionaries are appended to a list to hold all of them
  - This data is outputted to an easiliy-read JSON file format
  - This list of dictionaries is displayed to confirm success

    ![image](https://github.com/user-attachments/assets/54f83d0a-cd2f-4be3-99a6-4791d8592133)

- <ins>part_2_mars_weather.ipynb</ins>
  - This file begins by using splinter to import the Browser function, assigning the ChromeDriver to this browser object, and visiting a static website created by edX for educational purposes.
  - The html from this site is parsed and assigned to a Beautiful Soup object
  - The main table which includes all the Mars weather measurement data is captured and assigned to Python object
  - Using Chrome html inspect, it is determined that all the Mars data is contained in a table called table, the row headers are found in the 'tr' container and their names are in the 'th' class, and the row_data is all in the 'tr' class
  - Each of these is captured in a variable and then loops are created to go through each value appending them into their appropriate lists
  - A Pandas DataFrame called mars_data_df is created to store this data and make it much easier to analyze and calculate
    
      ![image](https://github.com/user-attachments/assets/e05accc2-26bd-427d-ae8d-6abd5448b6ef)
    
  - datatypes of these dataframe columns are checked, changed to their proper values in order to do data, and then checked again to make sure they properly updated
    
      ![image](https://github.com/user-attachments/assets/624e6892-1ee7-4adc-b7cf-fe2934c38638)
    
  - To answer the question How Many Months are there on Mars in this dataset?
  - Since Mars doesn't have one moon to measure a month by like the Earth, there are no officially recognized ways to divide a Martian year into a certain number of months.  The general consensus to measure a Martian year as closely to an Earth year as possible is to divide a Martian year into 24 months.
  - In this dataset however, there are 12 unique months in the Martian year of data collection. 
  - This is captured by printing the number of unique month values with the nunique() function.  The code and print function are below:

    ![image](https://github.com/user-attachments/assets/da67c83a-9e84-4eff-98bc-c82f3f51063e)

  - To answer the question How many Martian days worth of data are there?
  - A sol is the measurement of one day on Mars (the time is takes for it to complete one full rotation on its axis)
  - To calculate the number of sols in this dataset, I used the nuniquie() function on the "sol" column.  This returns the number of unique numbers in this column
  - The code & print function are below:

    ![image](https://github.com/user-attachments/assets/66446a03-1096-44ca-a12f-35e1bbbb84ae)

  - To answer the question What is the average temperature by month?
  - I grouped the dataframe by the 'month' column and then took the mean of the min_temp column

    ![image](https://github.com/user-attachments/assets/4996ddab-f477-4428-924f-b81179170865)

  - To plot the average minimum temperature by month, I plotted to a bar graph the 'month' column from this average min_temp dataframe as the x-axis and the min_temp as the y-axis
 
    ![image](https://github.com/user-attachments/assets/d25625fb-2234-4b65-bf07-af3f1dc2f94f)

  - To find the coldest month, warmest month, and their average temperature values, I sorted the min_temp column into a new dataframe, then used iloc[0] and iloc[-1] to get the first and last month value from this sorted list, then min() and max() to get the highest and lowest average temperature value from this list

    ![image](https://github.com/user-attachments/assets/93b133bf-88e3-4cdb-b457-a1ba54be37bb)

  - Then, the average atmospheric pressure values are sorted by month by using the group_by() function on the 'month' column and taking the mean() of the 'pressure' column

    ![image](https://github.com/user-attachments/assets/2e900f65-3ca3-4a74-92d0-0dd053cd0ec3)

  - This data is displayed graphically on a bar plot with the 'month' values on the x-axis and the average pressure values on the y-axis

    ![image](https://github.com/user-attachments/assets/9761f51d-fb1f-447e-9584-f007d03e988e)

  - Then, the pressure column is sorted in ascending order so that the lowest and highest average atmospheric values can be determined.  This is done by using the iloc[0] and iloc[-1] functions on the 'month' column to find the first and last month in this sorted dataset which are the months with the lowest and highest pressure values.  Then, min() and max() are used to return the lowest and highest pressure values in this sorted dataset

    ![image](https://github.com/user-attachments/assets/0c8160d7-cd76-4342-a489-17dcd227cb6e)

  - In order to properly estimate the number of Earth days in a Martian year, all of the temperature values are plotted compared to their sol (terrestrial days) on the x-axis.  This shows trends of temperature values taken by curiosity over the entire dataset period of time.
  - Knowing that a year is Mars completing an orbit around the sun, a valley and peak of temperature measurements can be deduced as a proper way to find a cycle in these plotted data points and finding a year "cycle".
  - In this case,the cycle in the center of the plot begins right around 510 terrestrial days and ends right around 1200 terrestrial days.  This equals 690 terrestrial days.  This is extremely close to the actaully-measured 687 Earth days that NASA calculated as very close to the exact number of Earty days in a Martian year.
 
    ![image](https://github.com/user-attachments/assets/35fafd78-dc9c-465f-b94b-859e94a70710)

  - Analysis of the data can be found in this section of the file
  - the dataframe is then saved into a CSV file
 
- <ins>news_data.json</ins>
  - This is simply an outputted JSON file of the title and text preview list of dictionaries scraped from the website in the first file called part_1_mars_news.ibynb

- <ins>mars_data.csv</ins>
   - This it the outputted CSV file of the dataframe saved from the scraped data captured in the file called part_2_mars_weather.ipynb


