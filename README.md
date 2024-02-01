# HotelDataAnalysis (Hotel Booking Exploratory Data Analysis)

## Objective/Goal

Our main goal is to develop a Database to analyze, draw useful conclusion about the trends and how various factors interact with each other in hotel bookings.
Build a visual data story or dashboard using `Power BI` to present to your stakeholders

### Requirements from stakeholders
Is our hotel revenue growing by year? We have two hotel types so it would be good to segment revenue by hotel type.
Should we increase our parking lot size? we want to understand if there is a trend, is guest with personal cars?
what trends can we see in the data? Focus on average daily rate and guests to explore seasonality.

## DATASET

We have hotel booking dataset for the year 2018, 2019 & 2020, this dataset contains the information as follows.

| **Column name** | **Description** |
| ------ | --------- |
| Hotel  | Type of hotel (Resort hotel or City Hotel) |
| is_canceled | Whether a booking is cancelled or not (labelled as 0 for not cancelled and 1 for cancelled) |
| lead_time | time between the booking date and actual arrival date (in days) |
| arrival_date_year | Year of arrival (2018, 2019, 2020) |
| arrival_date_month | Month of arrival (January to December) |
| arrival_date_week_number | Week number of arrival date in year (possible values: 1 to 52 weeks in year) |
| arrival_date_day_of_month | day of month of arrival date (possible values: 1 to 31) |
| stays_in_weekend_nights | number of weekend nights stayed in hotel |
| stays_in_week_nights | number of week nights stayed in hotel |
| adults | No of adults in booking |
| children | No of children in booking |
| babies | No of babies in booking |
| meal | type of meal choosen |
| country | customer country of origin |
| market_segment | Market segment designation (via what segment/purpose booking made) |
| distribution_channel | Booking distribution channel. The term “TA” means “Travel Agents” and “TO” means “Tour Operators” |
| is_repeated_guest | 0 for new guest, 1 for repeated guest |
| previous_cancellations | Number of previous bookings that were cancelled by the customer prior to the current booking |
| previous_bookings_not_canceled | Number of previous bookings not cancelled by the customer prior to the current booking |
| reserved_room_type | Code of room type reserved |
| assigned_room_type |  Code for the type of room assigned to the booking. Sometimes the assigned room type differs from the reserved room type due to hotel operation reasons (e.g. overbooking) or by customer request. Code is presented instead of designation for anonymity reasons |
| booking_changes | number of changes/amendment made to bookings by customers |
| deposit_type | To indicate if customer made a deposit to guarantee booking. No deposit, No Refund, Refundable |
| agent | ID of the travel agency that made the booking |
| company |  ID of the company/entity that made the booking |
| days_in_waiting_list | No of days the booking was in waiting list before it was confirmed to customer |
| customer_type | Type of booking, assuming one of four categories: Contract - when the booking has an allotment or other type of contract associated to it; Group – when the booking is associated to a group; Transient – when the booking is not part of a group or contract, and is not associated to other transient booking; Transient-party – when the booking is transient, but is associated to at least other transient booking
| adr | Average Daily rate as defined by dividing the sum of all lodging transactions by the total number of staying nights |
| required_car_parking_spaces | Number of car parking spaces required by the customer |
| total_of_special_requests | Number of special requests made by the customer (e.g. twin bed or high floor) |
| reservation_status | Reservation last status; Canceled, Check-Out, No-Show |
| reservation_status_date | Date at which the last status was set |


## Data Analysis Project Pipeline

**Build a Database** --> **Develop SQL Query** --> **Connect to Power BI to the database** --> **Visualize** --> **Summarize findings**


1. Build a Database:
   Creating a database named "HotelDataAnalysis" and imported with the data consisting of multiple tables and renamed as '2018$', '2019$', '2020$', 'market_segment$', 'meal_cost$'
   

