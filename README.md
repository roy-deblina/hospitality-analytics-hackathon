# hospitality-analytics-hackathon
This project is part of Data Analytics Bootcamp hackathon.
The project is to provide Insights to Revenue Team in Hospitality Domain, where GDS Grands owns multiple five-star hotels across India for the past 20 years. Due to strategic moves from other competitors and ineffective decision-making in management, GDS Grands are losing its market share and revenue in the luxury/business hotels category. 

The problem statement provided with metric list to get an  idea about:
1) Revenue - sum of revenue_realised
The revenue_realised column represents the final amount of money that goes to the hotel based on booking status. If the booking status is cancelled, then 40% of the revenue generated is deducted and the remaining is refunded to the customer. If the booking status is Checked Out/No show, then full revenue generated will goes to hotels.
2) Total Bookings - Count of booking_id in fact_bookings 
3) Average Rating - Average of ratings_given 
4) Total Capacity - Sum of capacity 
5) Total Succesful bookings - Sum of successful_bookings from fact_bookings 
6) Occupancy % - Ratio of Total Successful Bookings to Total Capacity 
7) Total Cancelled Bookings - Count of booking_id in which booking_status = "Cancelled" 
8) Cancellation Rate Ratio of 'Total Cancelled Bookings' to 'Total Bookings


## Transform the excel file in power bi 
From Get data in POWER BI five excel files were opened for cleaning and transformation,
then check all the column of the different tables well, check the column quality and duplicates and null values. In the fact_bookings table the rating_given is null in most of the rows that is most of the customers haven't given any rating. 

## From([ratings_given]) replace the null values with 0
which is needed to calculate the average rating.

## Remove duplicates from booking_id column 
as the booking id must be unique to get insightful data.

in dim_rooms make the rows as column.
to find a correlation between the non rater and raters with number of days stayed. in the fact_booking table
## find out the difference between check in and check out date by adding new column. 
DAX query for this: 
Days_stayed = DATEDIFF ([check_in_date], [check_out_date], DAY)

## another three new column is made to find out the checkin_day and booking_day 
by using the DAX queries:
Booking_day = FORMAT ( fact_bookings[booking_date], "dddd" ) 
checkin_day = FORMAT ( fact_bookings[check_in_date], "dddd" )


then after checking all the table close and apply.

in visualisation part:
## dd cards - add all calculation in merit list
change the font size of call out values to 25, change the card shapre with rounded rectangle.

1) total revenue by property name 
2) total revenue by city
3) total revenue by booking platform- donut chart
general - effects - visual border on - increase the rounded corners.
format - visual - in data label - category, data labels and turn off labels.

4) total stay period by diff hotel location - column chart
turn off the x axis title, y axis title and value, and from general switch off the title.

5) add the revenue_realised by checking day to understand the maximum checking on which day of the week through histogram.
do the customisation as needed.

6) add the revenue_realised by checking day to understand the maximum checking on which day of the week through histogram.
do the customisation as needed.


## Add text box and givwe the title increase and change the font size as you like font size - calibria math, and font size 36

Once the adjusted_revenue column is filled, we can calculate the total revenue by summing the values in this column. You can do this using the SUM function, like so:

1. Create a measure named Total Revenue using the following DAX formula:

Total Revenue = SUM(fact_bookings[revenue_realized])
This measure sums up the values in the revenue_realized column of the fact_bookings table.

2. Total Bookings:
Create a measure named Total Bookings using the following DAX formula:
Total Bookings = COUNTROWS(fact_bookings)
This measure counts the number of rows (bookings) in the fact_bookings table.

3. Average Rating:
Create a measure named Average Rating using the following DAX formula:

Average Rating = AVERAGE(fact_bookings[ratings_given])
This measure calculates the average of the ratings_given column in the fact_bookings table.

4. Total Capacity:
Create a measure named Total Capacity using the following DAX formula:

Total Capacity = SUM(fact_aggregated_bookings[capacity])
This measure sums up the values in the capacity column of the fact_aggregated_bookings table.
5. Total Successful Bookings:
Create a measure named Total Successful Bookings using the following DAX formula:


Total Successful Bookings = SUM(fact_aggregated_bookings[successful_bookings])
This measure sums up the values in the successful_bookings column of the fact_aggregated_bookings table.

6. Occupancy %:
Create a measure named Occupancy % using the following DAX formula:

Occupancy % = DIVIDE([Total Successful Bookings], [Total Capacity], 0)
This measure calculates the ratio of total successful bookings to total capacity, handling potential division by zero errors.

7. Total Cancelled Bookings:
Create a measure named Total Cancelled Bookings using the following DAX formula:

Total Cancelled Bookings = CALCULATE(COUNTROWS(fact_bookings), fact_bookings[booking_status] = "Cancelled")
This measure counts the number of rows (bookings) in the fact_bookings table where the booking_status is "Cancelled".

## Visulization Dashboard
### Apr
![alt text](apr.png)

### May
![alt text](may.png)

### Jun 
![alt text](jun.png)

### Jul
![alt text](july.png)



