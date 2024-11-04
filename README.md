# New York Airbnb Listing EDA: 2008-2021


### Overview

Using Python and popular libraries such as Pandas, Numpy, Matplotlib and Seaborn, I did Exploratory Data Analysis (EDA) on New York's AirBnB Listings and discovered valuable insights. The data ranged from 2008 to 2021. 

## Steps:

Here's a breakdown of the steps I followed and the insights uncovered:

## 1. Data Collection and Cleaning:
I got the raw data from Maven Analytics containing AirBnB Listings of different cities in the world.
- Using Pandas, I explored that the Listings contained data of different cities and I am interested only in New York, I filtered down the data using slicing on city column.
- As I cleaned and analyzed data using describe and info methods, I discovered that host_since column data type is 'object'. I changed it to 'date' data type using pd.to_datetime function.
  
## 2. Data Analysis and Transformation
- Further I analyzed that there are 220 neighbourhoods in New York and many have only one count, so I filtered to only include neighbourhoods where count is 500 or more.
  ![image](https://github.com/user-attachments/assets/6f85818b-cd69-4110-be12-7a3c88e0c0eb)

- By performing further Exploratory steps on each columns, I discovered that there are 11 missing host_since values. As the count is quite low compared to the total data set of 22811, it can be ignored and it will not impact the analysis.
- For "accomodates" column, I found min value 0, but having 0 for accomodate in Airbnb context doesnt make sense, so I queries the data set with condition of accomodates == 0, and discovered these rows have price == 0 as well. There were 8 such rows only, and given the total count of data set, I filtered them out.
  

For further analysis and creating visuals, I created few tables which could be used.
  1. **NYork_neighbourhood** table created which grouped by neighbourhood and aggregated mean price against them. 
  2. **NYork_accomodates** table created which after filtering only **Harlem** neighbourhood grouped by number of accomodations and aggregated mean price against them
  3. **NYork_over_time** table created where I used resample method for Year and aggregated the neighbourhood counts and mean price for each host_since year.


With these tables created, I moved to visualization phase.

## 3. Visualization of Trends

To present the findings, I utilized Matplotlib and Seaborn to create a series of visualizations that highlight key insights.


### - Average Listing Price by New York Accomodation Number

Using bar plot on NYork_accomodates table created above which only considers Harlem neighbourhood, visualizes Price per night against the number of accomodation. From this, it was discovered that although the price increases as the accomodation group count increases, but if the group is 10 or more, it may result in cheaper price. The most expensive group is 12 with 800 USD per night. 

![image](https://github.com/user-attachments/assets/071412bc-e9f2-4285-8720-59c344cceccd)


### - New AirBnB Hosts in New York Over time

Using line chart on previously created NYork_over_time table, I displayed number of new host and its trend across years. From this, we can analyzed that since 2016, there is a sharp decline in the number of new hosts in New York, and it could largely be due to new Airbnb policies launched in 2016, and due to market saturation.

![image](https://github.com/user-attachments/assets/64dd358d-840e-4cd8-ad87-96dbfb5f479b)


### - Average AirBnB Price in New York Over time

Using line chart on previously created NYork_over_time table, I displayed number of average Airbnb Price and its trend across years. From this, we can analyzed that the average price peaked in 2011 and till Covid it is largely consistent.

![image](https://github.com/user-attachments/assets/43d20884-63b3-4c61-8503-f6fb8292876f)

### - Dual Axis Chart for new hosts and average price over time

Using line charts created above, I merged them into one dual axis line chart so we could analyze if there is any correlation between the new hosts count and the average prices. We can see that as the count of new hosts declined since 2016, the average prices remained stable and only was impacted in 2020 due to Covid.

![image](https://github.com/user-attachments/assets/d0f3305e-9dd9-4ddf-876e-201338e4d98b)


## Conclusion

This report demonstrates the power of data visualization in analyzing and forecasting AirBnB Listings for New York City, offering clear insights into the links between counts of new hosts and the average price in the city as well as the prices against the number of accomodation groups.
