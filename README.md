# PyBer_Analysis
## Overview
In this study,two csv documents are merged and analyzed. First document, ![city_data.csv](./Resources/city_data.csv), contains name of 120 cities, the number of drivers of each city and the type (urban, suburban or rural) of each city. Second document, ![ride_data.csv](./Resources/ride_data.csv), contains name of cities, date, fare in each date and ride_id.

In the work, a summary DataFrame of the ride-sharing data by city type is created. Then, using Pandas and Matplotlib, a multiple-line graph that shows the total weekly fares, within the dates 01/01/2019 and 04/28/2019, for each city type is created. 

Finally, based on the findings in the work a written report in which the findings of the study are discussed, how the data differs by city type is summarized and how those differences can be used by decision-makers at PyBer is prepared and presented.

### Purpose

The purpuse of the analysis is to find out how data concerning fare differs by city type and how to use these findings to make decision.

## Results of Analysis and Essential Points of the Code
In the code, the corresponding methods the python librories; pandas, matplotlib and numpy; such as merge, groupby, reset_index, pivot, loc and resample thods are used consonantly. You can find the complete code in the name

![PyBer_Challenge_code.ipynb](./PyBer_Challenge_code.ipynb).


### Analysis of Average Fare per Ride and Average Fare Per Driver for Each Type of City

First buy using groupby method of pandas, total number of rides, total number of drivers, total amaount of fare, the average fare per ride and the average fare per driver for each cyty type are calculated as a series. The codes are as follows
> total_rides=pyber_data_df.groupby(["type"]).count()["ride_id"]
> 
> total_drivers=city_data_df.groupby(["type"]).sum()["driver_count"]
> 
> total_amount_of_fares=pyber_data_df.groupby(["type"]).sum()["fare"]
> 
> average_fare_per_ride=total_amount_of_fares/total_rides
> 
> average_fare_per_driver=total_amount_of_fares/total_drivers

and then by using theses series, a dataframe is built by the code

> pyyber_summary_df=pd.DataFrame({
> 
>                "Total Rides":total_rides,
>                
>                "Total Drivers":total_drivers,
>                
>                "Total Fares":total_amount_of_fares,
>                
>                "Average Fare Per Ride":average_fare_per_ride,
>                
>                "Average Fare Per Driver":average_fare_per_driver
>                  
> })

the data frame is is formatted by 

> pyber_summary_df["Total Rides"] = pyber_summary_df["Total Rides"].map("{:,}".format)
> 
> pyber_summary_df["Total Drivers"] = pyber_summary_df["Total Drivers"].map("{:,}".format)
> 
> pyber_summary_df["Total Fares"] = pyber_summary_df["Total Fares"].map("${:,.2f}".format)
> 
> pyber_summary_df["Average Fare Per Ride"] = pyber_summary_df["Average Fare Per Ride"].map("{:.2f}".format)
> 
> pyber_summary_df["Average Fare Per Driver"] = pyber_summary_df["Average Fare Per Driver"].map("{:.2f}".format)

The outcome of the data farame can be displayed as follow:

![](./Resources/Average_Fare_Per_Ride_Driver.png)

### Analysis of the Total Weekly Fares for Each Type of City




## Summary
