# Railway_Management_System_-MySQL-

🚆 Railway Management System (MySQL)
📌 Project Overview

The Railway Management System is a relational database project built using MySQL to model real-world railway operations such as station management, train routes, passenger bookings, seat allocation, payments, and cancellations.

The project focuses on database design, normalization, referential integrity, and analytical SQL queries, making it suitable for backend, data, and software engineering roles.

🎯 Key Objectives

Design a normalized relational schema (3NF)

Implement foreign key relationships

Store and manage realistic railway data

Perform business-driven SQL analytics

Demonstrate interview-grade SQL skills

🛠️ Tech Stack

Database: MySQL (Community Edition)

Tooling: MySQL Workbench

Language: SQL

🗂️ Database Schema
Tables Implemented

stations – railway station details

trains – train information

train_routes – ordered station stops per train

passengers – passenger details

bookings – ticket booking records

seat_allocations – seat and coach assignment

payments – ticket payment transactions

cancellations – cancelled bookings & refunds

All tables are connected using foreign keys to enforce data integrity.

🔗 Entity Relationships (High Level)

One train → many route stops

One passenger → many bookings

One booking → one payment

One booking → optional cancellation

Stations act as source & destination nodes

📊 Sample Analytical Queries
1️⃣ Confirmed Bookings with Passenger & Train Info
SELECT p.full_name, t.train_name, b.journey_date, b.seat_class
FROM bookings b
JOIN passengers p ON b.passenger_id = p.passenger_id
JOIN trains t ON b.train_id = t.train_id
WHERE b.booking_status = 'CONFIRMED';

2️⃣ Revenue Generated per Train
SELECT t.train_name, SUM(p.amount) AS total_revenue
FROM payments p
JOIN bookings b ON p.booking_id = b.booking_id
JOIN trains t ON b.train_id = t.train_id
GROUP BY t.train_name;

3️⃣ Cancelled Tickets with Refund Amount
SELECT p.full_name, b.journey_date, c.refund_amount
FROM cancellations c
JOIN bookings b ON c.booking_id = b.booking_id
JOIN passengers p ON b.passenger_id = p.passenger_id;

4️⃣ Station-wise Train Stop Count
SELECT s.station_name, COUNT(tr.route_id) AS total_stops
FROM train_routes tr
JOIN stations s ON tr.station_id = s.station_id
GROUP BY s.station_name;

✅ Features Demonstrated

Normalized schema design (3NF)

Multi-table joins

Foreign key constraints

Real-world data modeling

Revenue & cancellation analytics

Clean insert sequencing respecting dependencies

🚀 Future Enhancements

Indexing for query optimization

Stored procedures for booking & cancellation

Triggers for automated seat allocation

Integration with backend APIs (FastAPI / Spring Boot)

BI dashboard (Power BI / Tableau)

📌 How to Run

Open MySQL Workbench

Create database railway_management

Execute schema creation scripts

Insert dummy data

Run analytical queries
