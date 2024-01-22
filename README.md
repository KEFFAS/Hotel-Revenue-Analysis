# Hotel-Revenue-Analysis
A project to develop a SQL database and to analyze and visualize hotel booking data using Power BI

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

