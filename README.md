# SmartRide – PL/SQL (MySQL) Window Functions Assignment

## Business Problem
SmartRide is a ride-hailing platform operating in Kigali and nearby cities.  
The company wants to analyze ride and payment data to:  
- Find top drivers per city and quarter  
- Track monthly revenue growth  
- Segment customers into quartiles for loyalty programs  
- Measure ride durations to optimize pricing  

---

## Success Criteria
1. **Top-5 drivers per city & quarter** using `ROW_NUMBER`, `RANK`, `DENSE_RANK`, `PERCENT_RANK`.  
2. **Running monthly revenue totals** using `SUM() OVER`.  
3. **Month-over-month ride growth** using `LAG()`.  
4. **Customer quartiles** using `NTILE(4)` and spending levels.  
5. **3-month moving average of ride duration** using `AVG() OVER`.  

---

## Database Schema
**Entities and Attributes:**
- **Cities** (city_id, city_name)  
- **Drivers** (driver_id, full_name, phone, rating, join_date, city_id)  
- **Vehicles** (vehicle_id, driver_id, plate_no, model, capacity, year_made)  
- **Customers** (customer_id, full_name, phone, join_date, city_id)  
- **Rides** (ride_id, customer_id, driver_id, start_time, end_time, distance_km, duration_min, fare, city_id)  
- **Payments** (payment_id, ride_id, amount, method, status)

Detailed Entity Relationships:
1. CITIES to DRIVERS (1:M)
One city can have many drivers
One driver belongs to one city
Foreign Key: city_id in DRIVERS table
2. CITIES to CUSTOMERS (1:M)
One city can have many customers
One customer belongs to one city
Foreign Key: city_id in CUSTOMERS table
3. DRIVERS to VEHICLES (1:1)
One driver has one vehicle
One vehicle belongs to one driver
Foreign Key: driver_id in VEHICLES table
4. DRIVERS to RIDES (1:M)
One driver can have many rides
One ride is handled by one driver
Foreign Key: driver_id in RIDES table
5. CUSTOMERS to RIDES (1:M)
One customer can have many rides
One ride belongs to one customer
Foreign Key: customer_id in RIDES table
6. RIDES to PAYMENTS (1:1)
One ride has one payment
One payment corresponds to one ride
Foreign Key: ride_id in PAYMENTS table
Primary Keys:
city_id (CITIES)
driver_id (DRIVERS)
vehicle_id (VEHICLES)
customer_id (CUSTOMERS)
ride_id (RIDES)
payment_id (PAYMENTS)
Foreign Key Relationships:
DRIVERS: city_id → CITIES(city_id)
CUSTOMERS: city_id → CITIES(city_id)
VEHICLES: driver_id → DRIVERS(driver_id)
RIDES: customer_id → CUSTOMERS(customer_id)
RIDES: driver_id → DRIVERS(driver_id)
RIDES: city_id → CITIES(city_id)
PAYMENTS: ride_id → RIDES(ride_id)

 Queries and Results Along with their Explanations

 Top-5 Drivers per City & Quarter

Functions used: ROW_NUMBER, RANK, DENSE_RANK, PERCENT_RANK

SQL Code:  


Screenshot:
--	
Explanation:  
This query ranks drivers by total revenue per city and quarter. It shows top performers like Alice Uwera in Kigali and Grace Mukamana in Musanze, helping identify who to reward each quarter.

 Q5. Running Monthly Revenue

Functions used: SUM OVER

SQL Code:  

Screenshot:  


Explanation:  
The query calculates cumulative revenue month by month. Revenue grew steadily from January to June, reaching a total of 43,600 by the end of the period.

Q5. Month-over-Month Ride Growth

Functions used: LAG

SQL Code:  


Screenshots:  

Explanation:  
This query compares monthly ride counts with the previous month. The results show a consistent number of rides each month, with no growth or decline during this period.

 Q 5. Customer Quartiles by Spend

Functions used: NTILE, CUME_DIST

SQL Code:  


Screenshot:  


Explanation:  
Customers are divided into four spending quartiles. Eric Mugisha is in the top quartile, while Josephine Ingabire is in the bottom, helping target loyalty promotions effectively.

Q 5. 3-Month Moving Average Ride Duration

Functions used: AVG OVER

SQL Code:  


Screenshot:  

Explanation:  
This query smooths out monthly fluctuations in ride duration. The moving average helps identify trends, such as the dip in May followed by a recovery in June.

6. Results Analysis

The analysis of the SmartRide dataset provided insights into different aspects of the business:

- Descriptive Analysis: We identified which drivers performed best in different quarters and cities. We also saw how revenues and ride counts changed over time.

- Diagnostic Analysis: By comparing monthly changes, we could see where growth slowed down or spiked, and link these trends to specific cities or driver activity.

- Prescriptive Analysis: Based on customer quartiles and driver performance, management can now decide who to reward, which customers to target with promotions, and how to adjust pricing strategies based on ride durations.

Academic Integrity Statement

Every source that contributed to this work has been carefully acknowledged and referenced. While I drew upon diverse learning materials and official documentation to deepen my grasp of SQL window functions and their syntax, the adaptation of these ideas to the Smart rides case study is an entirely original undertaking. Mysql references, online tutorials, and course content served as the foundation for technical comprehension, but the creative application of these concepts to a real-world Rwandan retail context arose from my own reasoning and structured analysis.

References

1. MySQL 8.0 Documentation – Window Functions  
2. TutorialsPoint – SQL Window Functions  
3. GeeksforGeeks – SQL Analytic Functions  
4. Course Lecture Notes
5.W3Schools – SQL Window Functions Tutorial
6.IBM Knowledge Center – OLAP and Analytic Functions
7.Microsoft SQL Server Documentation – Ranking Functions (Transact-SQL)
8.Mode Analytics SQL Tutorial – Window Functions
9.DataCamp – SQL Window Functions Tutorial
10.Khan Academy – Introduction to SQL Queries and Analysis
11.Journal of Database Management – Articles on SQL Analytics

