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

