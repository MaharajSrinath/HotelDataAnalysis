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
![image](https://github.com/MaharajSrinath/HotelDataAnalysis/assets/146663011/910c53f1-9ffe-4dc2-acb5-572eeba9e6b2)

2. Develop SQL Query:

* Taking a look at the data
```SQL
  use HotelDataAnalysis
  select * from dbo.[2018$]
```
   OUTPUT
```

Resort Hotel	1	85	2018	July	27	1	0	3	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	82	0	1	Canceled	2018-05-06 00:00:00.000
Resort Hotel	1	75	2018	July	27	1	0	3	2	0	0	HB	PRT	Offline TA/TO	TA/TO	0	0	0	D	D	0	No Deposit	15	NULL	0	Transient	105.5	0	0	Canceled	2018-04-22 00:00:00.000
Resort Hotel	1	23	2018	July	27	1	0	4	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	E	E	0	No Deposit	240	NULL	0	Transient	123	0	0	Canceled	2018-06-23 00:00:00.000
Resort Hotel	1	60	2018	July	27	1	2	5	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	E	E	0	No Deposit	240	NULL	0	Transient	107	0	2	Canceled	2018-05-11 00:00:00.000
Resort Hotel	1	96	2018	July	27	1	2	8	2	0	0	BB	PRT	Direct	Direct	0	0	0	E	E	0	No Deposit	NULL	NULL	0	Transient	108.3	0	2	Canceled	2018-05-29 00:00:00.000
Resort Hotel	1	45	2018	July	27	2	1	3	3	0	0	BB	PRT	Online TA	TA/TO	0	0	0	D	D	0	No Deposit	241	NULL	0	Transient	108.8	0	1	Canceled	2018-05-19 00:00:00.000
Resort Hotel	1	40	2018	July	27	2	1	3	3	0	0	BB	PRT	Online TA	TA/TO	0	0	0	D	D	0	No Deposit	241	NULL	0	Transient	108.8	0	1	Canceled	2018-06-19 00:00:00.000
Resort Hotel	1	43	2018	July	27	2	1	3	3	0	0	BB	PRT	Online TA	TA/TO	0	0	0	D	D	0	No Deposit	241	NULL	0	Transient	108.8	0	0	Canceled	2018-05-23 00:00:00.000
Resort Hotel	1	45	2018	July	27	2	2	3	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	G	G	0	No Deposit	241	NULL	0	Transient	117.81	0	0	Canceled	2018-05-18 00:00:00.000
Resort Hotel	1	47	2018	July	27	2	2	5	2	2	0	BB	PRT	Online TA	TA/TO	0	0	0	G	G	0	No Deposit	240	NULL	0	Transient	153	0	0	Canceled	2018-06-02 00:00:00.000
Resort Hotel	1	3	2018	July	27	2	0	3	2	0	0	HB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	136.33	0	2	Canceled	2018-06-29 00:00:00.000
Resort Hotel	1	71	2018	July	27	3	0	2	3	0	0	BB	PRT	Offline TA/TO	TA/TO	0	0	0	A	A	0	No Deposit	242	NULL	0	Transient	110.3	0	2	Canceled	2018-06-16 00:00:00.000
Resort Hotel	1	63	2018	July	27	3	0	2	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	82	0	2	Canceled	2018-06-18 00:00:00.000
Resort Hotel	1	62	2018	July	27	3	0	2	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	D	D	0	No Deposit	240	NULL	0	Transient	97	0	1	Canceled	2018-07-03 00:00:00.000
Resort Hotel	1	101	2018	July	27	3	0	2	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	73.8	0	1	Canceled	2018-06-12 00:00:00.000
Resort Hotel	1	51	2018	July	27	3	0	2	3	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	242	NULL	0	Transient	110.3	0	0	Canceled	2018-06-09 00:00:00.000
Resort Hotel	1	48	2018	July	27	3	1	2	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	E	E	0	No Deposit	240	NULL	0	Transient	123	0	0	Canceled	2018-05-26 00:00:00.000
Resort Hotel	1	368	2018	July	27	3	3	7	2	0	0	BB	PRT	Offline TA/TO	TA/TO	0	0	0	A	A	0	No Deposit	40	NULL	0	Contract	55.68	0	0	Canceled	2018-05-19 00:00:00.000
Resort Hotel	1	81	2018	July	27	3	3	7	2	0	0	HB	PRT	Direct	Direct	0	0	0	A	A	2	No Deposit	250	NULL	0	Transient	124	0	1	Canceled	2018-06-09 00:00:00.000
Resort Hotel	1	79	2018	July	27	3	6	15	2	1	0	BB	PRT	Offline TA/TO	TA/TO	0	0	0	A	A	0	No Deposit	242	NULL	0	Transient	108.73	0	2	Canceled	2018-04-15 00:00:00.000
Resort Hotel	1	109	2018	July	27	3	0	2	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	123	0	1	Canceled	2018-05-26 00:00:00.000
Resort Hotel	1	72	2018	July	27	3	0	2	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	73.8	0	1	Canceled	2018-06-29 00:00:00.000
Resort Hotel	1	63	2018	July	27	3	2	5	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	F	F	0	No Deposit	242	NULL	0	Transient	117	0	1	Canceled	2018-05-13 00:00:00.000
Resort Hotel	1	26	2018	July	27	4	2	5	2	2	0	BB	PRT	Online TA	TA/TO	0	0	0	H	H	0	No Deposit	240	NULL	0	Transient	163	0	0	Canceled	2018-06-09 00:00:00.000
Resort Hotel	1	73	2018	July	27	4	2	5	3	0	0	HB	PRT	Direct	Direct	0	0	0	D	D	0	No Deposit	250	NULL	0	Transient	172	0	1	Canceled	2018-05-20 00:00:00.000
Resort Hotel	1	102	2018	July	27	4	2	5	2	0	0	BB	PRT	Online TA	TA/TO	0	0	0	A	A	0	No Deposit	240	NULL	0	Transient	110.7	0	1	Canceled	2018-04-22 00:00:00.000
```


   

   

