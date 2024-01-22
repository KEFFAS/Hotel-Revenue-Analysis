# Hotel-Revenue-Analysis
A project to develop a SQL database and to analyze and visualize hotel booking data using Power BI

# Table of Content
- [Project Overview](#project-overview)
- [Data sources](#data-sources)
- [Tools](#tools)
- [Initial Questions](#initial-questions)
- [Data analysis project pipeline](#data-analysis-project-pipeline)
- [Building a database](#building-a-database)
- [Developing the SQL Query](#developing-the-sql-query)
- [Connecting the Power BI to the database](#connecting-the-power-bi-to-the-database)
- [Visualizations](#visualizations)
- [Summary of the findings](#summary-of-the-findings)
- [Recommendations](#recommendations)
- [References](#references)


## Project Overview

The purpose of this data analysis project is to offer insights on hotel revenue during the previous years. We aim to detect patterns, obtain a more profound comprehension of the hotel's financial performance, and formulate evidence-based suggestions by scrutinizing many facets of the hotel data.

## Data sources

The main dataset included in this analysis is the "hotel_revenue_historical.xlsx" file, which includes comprehensive data regarding hotel reservations and revenue generated.

## Tools

- SQL Server [Download here](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)
- Excel [Download here](https://www.microsoft.com/en/microsoft-365/excel)
- Power BI [Download here](https://www.microsoft.com/en-us/power-platform/products/power-bi)
## Initial Questions
1. Is our hotel revenue growing by year?
2. Should we increase our parking lot size?
3. What trends can we see in the data?
## Data analysis project pipeline
1.	Build a database
2.	Develop the SQL Query
3.	Connect the Power BI to the database
4.	Visualize
5.	Summarize findings

## Building a database
```SQL
CREATE DATABASE [keffaanalytics]
USE [keffaanalytics]
CREATE TABLE [dbo].['2018$'](
	[hotel] [nvarchar](255) NULL,
	[is_canceled] [float] NULL,
	[lead_time] [float] NULL,
	[arrival_date_year] [float] NULL,
	[arrival_date_month] [nvarchar](255) NULL,
	[arrival_date_week_number] [float] NULL,
	[arrival_date_day_of_month] [float] NULL,
	[stays_in_weekend_nights] [float] NULL,
	[stays_in_week_nights] [float] NULL,
	[adults] [float] NULL,
	[children] [float] NULL,
	[babies] [float] NULL,
	[meal] [nvarchar](255) NULL,
	[country] [nvarchar](255) NULL,
	[market_segment] [nvarchar](255) NULL,
	[distribution_channel] [nvarchar](255) NULL,
	[is_repeated_guest] [float] NULL,
	[previous_cancellations] [float] NULL,
	[previous_bookings_not_canceled] [float] NULL,
	[reserved_room_type] [nvarchar](255) NULL,
	[assigned_room_type] [nvarchar](255) NULL,
	[booking_changes] [float] NULL,
	[deposit_type] [nvarchar](255) NULL,
	[agent] [float] NULL,
	[company] [nvarchar](255) NULL,
	[days_in_waiting_list] [float] NULL,
	[customer_type] [nvarchar](255) NULL,
	[adr] [float] NULL,
	[required_car_parking_spaces] [float] NULL,
	[total_of_special_requests] [float] NULL,
	[reservation_status] [nvarchar](255) NULL,
	[reservation_status_date] [datetime] NULL
) ON [PRIMARY]
CREATE TABLE [dbo].['2019$'](
	[hotel] [nvarchar](255) NULL,
	[is_canceled] [float] NULL,
	[lead_time] [float] NULL,
	[arrival_date_year] [float] NULL,
	[arrival_date_month] [nvarchar](255) NULL,
	[arrival_date_week_number] [float] NULL,
	[arrival_date_day_of_month] [float] NULL,
	[stays_in_weekend_nights] [float] NULL,
	[stays_in_week_nights] [float] NULL,
	[adults] [float] NULL,
	[children] [float] NULL,
	[babies] [float] NULL,
	[meal] [nvarchar](255) NULL,
	[country] [nvarchar](255) NULL,
	[market_segment] [nvarchar](255) NULL,
	[distribution_channel] [nvarchar](255) NULL,
	[is_repeated_guest] [float] NULL,
	[previous_cancellations] [float] NULL,
	[previous_bookings_not_canceled] [float] NULL,
	[reserved_room_type] [nvarchar](255) NULL,
	[assigned_room_type] [nvarchar](255) NULL,
	[booking_changes] [float] NULL,
	[deposit_type] [nvarchar](255) NULL,
	[agent] [float] NULL,
	[company] [nvarchar](255) NULL,
	[days_in_waiting_list] [float] NULL,
	[customer_type] [nvarchar](255) NULL,
	[adr] [float] NULL,
	[required_car_parking_spaces] [float] NULL,
	[total_of_special_requests] [float] NULL,
	[reservation_status] [nvarchar](255) NULL,
	[reservation_status_date] [datetime] NULL
) ON [PRIMARY]
CREATE TABLE [dbo].['2020$'](
	[hotel] [nvarchar](255) NULL,
	[is_canceled] [float] NULL,
	[lead_time] [float] NULL,
	[arrival_date_year] [float] NULL,
	[arrival_date_month] [nvarchar](255) NULL,
	[arrival_date_week_number] [float] NULL,
	[arrival_date_day_of_month] [float] NULL,
	[stays_in_weekend_nights] [float] NULL,
	[stays_in_week_nights] [float] NULL,
	[adults] [float] NULL,
	[children] [float] NULL,
	[babies] [float] NULL,
	[meal] [nvarchar](255) NULL,
	[country] [nvarchar](255) NULL,
	[market_segment] [nvarchar](255) NULL,
	[distribution_channel] [nvarchar](255) NULL,
	[is_repeated_guest] [float] NULL,
	[previous_cancellations] [float] NULL,
	[previous_bookings_not_canceled] [float] NULL,
	[reserved_room_type] [nvarchar](255) NULL,
	[assigned_room_type] [nvarchar](255) NULL,
	[booking_changes] [float] NULL,
	[deposit_type] [nvarchar](255) NULL,
	[agent] [float] NULL,
	[company] [nvarchar](255) NULL,
	[days_in_waiting_list] [float] NULL,
	[customer_type] [nvarchar](255) NULL,
	[adr] [float] NULL,
	[required_car_parking_spaces] [float] NULL,
	[total_of_special_requests] [float] NULL,
	[reservation_status] [nvarchar](255) NULL,
	[reservation_status_date] [datetime] NULL
) ON [PRIMARY]
CREATE TABLE [dbo].[market_segment$](
	[Discount] [float] NULL,
	[market_segment] [nvarchar](255) NULL
) ON [PRIMARY]
CREATE TABLE [dbo].[meal_cost$](
	[Cost] [float] NULL,
	[meal] [nvarchar](255) NULL
) ON [PRIMARY]
```
## Developing the SQL Query

```SQL
with hotels as (
select * from [dbo].['2018$'] 
union
select * from [dbo].['2019$']
union
select * from [dbo].['2020$'])

select
arrival_date_year,
hotel,
round (sum((stays_in_week_nights + stays_in_weekend_nights)* adr),2) as revenue 
from hotels
group by arrival_date_year,hotel
```
## Connecting the Power BI to the database

<img width="949" alt="CONNECTING TO DATABASE" src="https://github.com/KEFFAS/Hotel-Revenue-Analysis/assets/89402452/83a9b96f-02ed-46a1-a908-41f90638cfc0">

## Visualizations

<img width="509" alt="both hotels revenue" src="https://github.com/KEFFAS/Hotel-Revenue-Analysis/assets/89402452/b611d23d-592c-4cf2-a0ff-acd293e41f2a">


<img width="509" alt="Resort hotel revenue" src="https://github.com/KEFFAS/Hotel-Revenue-Analysis/assets/89402452/62c4a6db-4a2e-431d-8d6a-4ce7f8ae54dd">

<img width="506" alt="City hotel revenue" src="https://github.com/KEFFAS/Hotel-Revenue-Analysis/assets/89402452/65aba7d2-cab0-4017-b2f6-1a742b1cb6b1">

<img width="509" alt="Revenue by Researvation status date" src="https://github.com/KEFFAS/Hotel-Revenue-Analysis/assets/89402452/90081c3c-a18e-43c2-8bbd-574e149d1608">

<img width="757" alt="car parking trends" src="https://github.com/KEFFAS/Hotel-Revenue-Analysis/assets/89402452/81ff20a9-1e52-4f73-8dc5-685cb663d882">

## Summary of the findings

1. By observing the trend line, it is clear that the hotel revenue is growing by year
2. The data shows that there is no much need to increase the parking lot size as the parking percentage ranges between 2 to 2.5%
3. The city hotel revenue is growing at a higher rate that the resort hotel revenue

## Recommendations

1. Offer promotions and discounts to attract new customers
2. Implement dynamic pricing to adjust room rates based on demand.
3. Offer additional services such as spa treatments, room upgrades, or special packages

## References
 [Kaggle] (https://www.kaggle.com/learn/intro-to-sql)

 

