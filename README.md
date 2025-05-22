# SQL Database Project - 100 Dates for 100 Riyals

This SQL project solves a classic logic problem using query-based simulation.  
It demonstrates how to find all possible combinations of purchasing 100 date items (of three types) such that both the **quantity** and **total cost** equal 100.

## Description
The challenge:
- Buy 100 units of dates (bags, boxes, and cartons)
- Total cost must be exactly 100 riyals
- Each type has a fixed price:
  - Box = 5 SAR
  - Carton = 3 SAR
  - Bag = 1 SAR

The project includes:
- Generating combinations using SQL
- Applying math logic inside SQL conditions
- Using `CONNECT BY` and `DUAL` in Oracle

## Technologies Used
- SQL (Oracle)
- SQL*Plus

## Sample Query
```sql
SELECT x AS Boxes, y AS Cartons, 100 - x - y AS Bags
FROM (
    SELECT LEVEL - 1 AS x FROM dual CONNECT BY LEVEL <= 100
) A,
(
    SELECT LEVEL - 1 AS y FROM dual CONNECT BY LEVEL <= 100
) B
WHERE x + y + (100 - x - y) = 100
  AND (5 * x + 3 * y + (100 - x - y)) = 100;
