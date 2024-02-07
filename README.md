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

**Build a Database** --> **Develop SQL Query(&Analysis using SQL)** --> **Connect to Power BI to the database** --> **Visualize** --> **Summarize findings**

**1. Build a Database:**
   
Creating a database named "HotelDataAnalysis" and imported with the data consisting of multiple tables and renamed as '2018$', '2019$', '2020$', 'market_segment$', 'meal_cost$'

![image](https://github.com/MaharajSrinath/HotelDataAnalysis/assets/146663011/d71903e8-cc1e-4029-8567-5e1dbb23ffc0)


**2. Develop SQL Query:**

**a) Taking a look at the data**

- Total number of columns in table 2018,2019 & 2020: 32 
- Total number of rows in 2018 table:   21,996
- Total number of rows in 2019 table:   79,264
- Total number of rows in 2020 table:   40,687
- Total number of rows in all tables: 1,41,947
   
```SQL
  use HotelDataAnalysis
  select * from dbo.[2018$]
```
```sql
-- OUTPUT

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

**b) Cleaning the data**
   1. REMOVING DUPLICATE ROWS IF ANY

Union of multiple table as Hoteldata: It is observed that all tables for year 2018, 2019, 2020 have same number of columns with similar datatypes and in same order, UNION operator is used to combine. Total number of rows reduced to 1,00,756 after removing duplicates.

```sql
with hoteldata as (
select * from dbo.[2018$]
union /* union operator removes all duplicates, if not required we can use UNION ALL operator */
select * from dbo.[2019$]
union
select * from dbo.[2020$])

select count(*) as total_rows from Hoteldata
```
```sql
-- OUTPUT
100756
```

   2. HANDLING NULL VALUES

First we will see the datatypes of all the columns and try to understand what unique values the columns hold. With that we can handle the missing/Null values and change the datatypes incase required.

Datatype of Columns

```sql
select TABLE_SCHEMA,TABLE_NAME,COLUMN_NAME,DATA_TYPE, CHARACTER_MAXIMUM_LENGTH
from INFORMATION_SCHEMA.COlUMNS
where TABLE_NAME = '2018$'
```

![image](https://github.com/MaharajSrinath/HotelDataAnalysis/assets/146663011/886206ad-0840-494d-9c36-21adf42cc258)


Checking the unique values the columns hold

```sql
select distinct hotel from Hoteldata
```
```sql
-- OUTPUT
City Hotel
Resort Hotel
```

```sql
select distinct is_canceled from Hoteldata
```
```sql
-- OUTPUT
0
1
```

```sql
select distinct children from Hoteldata
```
```sql
-- OUTPUT
NULL
0
1
2
3
10
```
Note: This column 'children' has 0 as value which mean no children were present in the customers, so NULL values are the missing values or 0. We can replace the null values with mean value of children but mean is between 0 & 1 so we replace with 0.

```sql
select avg(children) from Hoteldata
```
```sql
-- OUTPUT
0.133680073053559
```

```sql
Update dbo.[2020$] /* also 2018$ & 2019$ */
SET children = 0
Where children IS NULL;
-- all NULL values are replaced with 0 now.
```

```sql
select country, count(country) from Hoteldata
where country = 'NULL'
group by country  
```
```sql
-- OUTPUT
NULL	561  /* replaced all the values written as NULL to OTHERS */
```

```sql
Update dbo.[2020$]  /* also 2018$ & 2019$ */
SET country = 'OTHERS'
where country = 'NULL'
```
```sql
-- OUTPUT
(83 rows affected) 
```

Similarly we have NULL values in agent & company columns which are now replaced by 0.

```sql
Update dbo.[2020$]
SET company = 0
where company = 'NULL'

UPDATE dbo.[2020$]
SET agent = 0
where agent IS NULL
```

Note: It was observed with below query that sum of adults, children & babies i.e., total customers against booking is 0, for few of the rows. So we will remove scuh rows.

```sql
select distinct (adults + children + babies), count(adults + children + babies) as count from Hoteldata
group by (adults + children + babies)
```
```sql
-- OUTPUT
0	195   /* 195 rows has 0 adults 0 children 0 babies */
6	2
3	11060
40	2
55	2
20	4
10	4
50	2
4	4314
1	18970
27	4
12	3
26	10
5	156
2	66028
```

Deleting the rows with 0 total no of customers againt booking

```sql
delete from dbo.[2018$]   /* also for 2019$ & 2020$ */ 
where (adults + children + babies) = 0
```
```sql
-- OUTPUT
(29 rows affected)  /* (114 rows affected) (67 rows affected) */
```
   3. CONVERTING COLUMNS TO APPROPRIATE DATATYPE

Observed columns like adults, children, babies, agent, company have 'float' or 'nvarchar' as shown above in table_schema but appropriate datatype is 'int'

```sql
ALTER TABLE dbo.[2018$]
ALTER COLUMN company INT /* altering the datatype of company column to INT */
```

Observed the 'reservation_status_date' column datatype as 'datetime' while no time being recorded, shown 5 outputs below.

```sql
SELECT TOP 5 reservation_status_date
FROM Hoteldata
```
```sql
-- OUTPUT
2018-05-06 00:00:00.000
2018-04-22 00:00:00.000
2018-06-23 00:00:00.000
2018-05-11 00:00:00.000
2018-05-29 00:00:00.000
```
Now, converting the datatype to 'DATE' - 'YYYY-MM-DD'

```sql
ALTER TABLE dbo.['2019$']
ALTER COLUMN reservation_stats=us_date DATE
```
```sql
select TOP 5 reservation_status_date from Hoteldata
-- OUTPUT
2018-05-06
2018-04-22
2018-06-23
2018-05-11
2018-05-29
```

   4. REMOVING OUTINERS

While checking for outliers in the dataset, found one in 'adr' column. By using simple max(), min(), avg(), std() functions once can identify the exteme values/outlier

```sql
select max(adr), min(), avg(adr)
from Hoteldata
-- OUTPUT
5400	-6.38	104.624615407561
```

min(adr) has a negative value, which is not possible for average daily revenue = total daily revenue / total rooms sold. So we simply drop it.

   5. ADDING COLUMNS

- total_stays = (stays_in_weekend_nights + stays_in_week_nights) (datatype - FLOAT)
- total_people = (adults + children + babies) (datatype - INT)
- revenue = adr * total_stays (datatype - FLOAT)

```sql
ALTER TABLE dbo.[2018$] /* adding column with datatype float */
ADD total_stays FLOAT

UPDATE dbo.[2018$]
SET total_stays = (stays_in_weekend_nights + stays_in_week_nights)
WHERE total_stays IS NULL  /* update the values of total_stays */
```
similary all the columns are updated

**c) Data analysis using SQL**

Using data analysis we will try to answer few questions.

Q 1) Is hotel revenue growing by year?

```sql
select arrival_date_year, count(distinct arrival_date_month) as No_of_distinct_months, sum(revenue) as Total_revenue from Hoteldata
group by arrival_date_year
order by Total_revenue asc
```
```sql
-- OUTPUT
2018	6	4885499.06
2020	8	14281776.01
2019	12	20181595.25
```
The hotel revenue is increasing year on year, you can see year 2020 is between 2018 & 2019 since the revenue recorded is only for 8 months.

Q 2) What is the percentage of booking in each hotel & which generates highest adr?

```sql
select hotel, count(hotel) as No_of_bookings, 
ROUND((count(hotel) * 100 / (select count(*) from Hoteldata)),2) as percentage, FORMAT(avg(adr),'N2') as AVG_ADR
from Hoteldata
group by hotel
```
```sql
-- OUTPUT
City Hotel	59800	59	108.97
Resort Hotel	40760	40	98.26
```

   Around 60% bookings are for City Hotel and 40% bookings are for Resort Hotel. Average ADR of City Hotel is slightly higher than that of Resort Hotel, City hotel seems to be making slightly more revenue.

Q 3) How long do people stay at the hotels?

```sql
select hotel, max(total_stays) as maximun_stay, ROUND(avg(total_stays),2) as average_stay
from Hoteldata
group by hotel
```
```sql
-- OUTPUT
City Hotel	48	3.12
Resort Hotel	69	4.43
```
Maximun & Average stay in City hotel is 48 & 3.12 nights/days respectively & in Resort Hotel it is 69 & 4.43 nights respectively.

```sql
select hotel, total_stays as num_of_days, count(total_stays) as count 
from Hoteldata
group by total_stays, hotel
order by total_stays asc, count desc
```
```sql
-- OUTPUT
Resort Hotel	0	456
City Hotel	0	277
City Hotel	1	11620
Resort Hotel	1	8143
City Hotel	2	12373
Resort Hotel	2	5846
City Hotel	3	15139
Resort Hotel	3	5096
City Hotel	4	10664
Resort Hotel	4	4704
City Hotel	5	4624
Resort Hotel	5	3100
Resort Hotel	6	2020
City Hotel	6	1825
Resort Hotel	7	6862
City Hotel	7	2001
Resort Hotel	8	912
City Hotel	8	397
Resort Hotel	9	714
City Hotel	9	227
Resort Hotel	10	1080
City Hotel	10	205
Resort Hotel	11	351
City Hotel	11	85
Resort Hotel	12	169
City Hotel	12	62
Resort Hotel	13	131
City Hotel	13	46
Resort Hotel	14	916
City Hotel	14	91
Resort Hotel	15	42
City Hotel	15	39
Resort Hotel	16	21
City Hotel	16	17
Resort Hotel	17	14
City Hotel	17	10
Resort Hotel	18	21
City Hotel	18	7
City Hotel	19	15
Resort Hotel	19	15
City Hotel	20	16
Resort Hotel	20	1
Resort Hotel	21	50
City Hotel	21	10
Resort Hotel	22	10
City Hotel	22	7
Resort Hotel	23	5
City Hotel	23	2
City Hotel	24	6
Resort Hotel	25	12
City Hotel	25	2
City Hotel	26	3
Resort Hotel	26	3
City Hotel	27	4
Resort Hotel	27	1
Resort Hotel	28	36
City Hotel	28	4
City Hotel	29	10
Resort Hotel	29	4
City Hotel	30	8
Resort Hotel	30	6
City Hotel	33	2
Resort Hotel	33	1
City Hotel	34	1
Resort Hotel	35	5
Resort Hotel	38	1
Resort Hotel	42	4
Resort Hotel	45	1
Resort Hotel	46	2
City Hotel	48	1
Resort Hotel	56	2
Resort Hotel	60	2
Resort Hotel	69	1
```
Most common stay length is 3 days/nights and we can observe here that for shorter stays say <=4 days City Hotel is preferred the most, whereas for longer stays Resort Hotel is preferred.

**3. Connect to Power BI to the database** --> **4. Visualize** --> **5. Summarize findings**

Now we import this data from SQL server to PowerBI for further analyzing the data and try to answer following questions.

 Q1) Which agent makes the most no. of bookings? done
 Q2) Which room type is in most demand and which room type generates the highest adr? done
 Q3) Which meal type is the most preffered meal of customers? done
 Q4) What is the percentage of bookings in each hotel? done
 Q5) Which is the most common channel for booking hotels? done
 Q6) Which are the most busy months? 
 Q7) From which country most of the guests are coming ? done
 Q8) How long do people stay at the hotels? done
 Q9) Which hotel seems to make more revenue? done
 Q10) Which hotel has a  higher lead time? done
 Q11) What is preferred stay length in each hotel? done
 Q12) Which hotel has higher bookings cancellation rate. done
 Q13) Which hotel has a high chance that its customer will return for another stay? done
 Q14) Which channel is mostly used for the early booking of hotels? done
 Q15) Which channel has a longer average waiting time? done 
 Q16) Which distribution channel brings better revenue-generating deals for hotels? done
 Q17) Which significant distribution channel has the highest cancellation percentage? 
 Q18) Doesa  longer waiting period or longer lead time causes the cancellation of bookings?
 Q19) Whether not getting allotted the same room type as demand is the main cause of cancellation for bookings?
 Q20) Does not alloting the  same room as demanded affect adr? 
 Q21) What is the trend of bookings within a month?
 Q22) Which types of customers mostly make bookings?


-- We load the Hoteldata table along with market_segment$ and meal_cost$ table and establishing relationship in PowerBI.

```sql
-- SHowing table schema of tables
select TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, DATA_TYPE, CHARACTER_MAXIMUM_LENGTH
from INFORMATION_SCHEMA.COLUMNS
where TABLE_NAME = 'meal_cost$' /* and 'market_segment$' */
-- market_segment$ table
dbo	market_segment$	Discount	float	NULL
dbo	market_segment$	market_segment	nvarchar	255

-- meal_cost$ table
dbo	meal_cost$	Cost	float	NULL
dbo	meal_cost$	meal	nvarchar	255
```

```sql
-- we can also join the tables in SQL
select h.*, ms.Discount, mc.Cost
from Hoteldata h
LEFT JOIN dbo.market_segment$ ms
on h.market_segment = ms.market_segment
left join dbo.meal_cost$ mc
on h.meal = mc.meal
```

![image](https://github.com/MaharajSrinath/HotelDataAnalysis/assets/146663011/dab850bd-e2ce-44dc-8874-7e12c10fbc80)














   

