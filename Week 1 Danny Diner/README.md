# Case Study #1 : Danny's Diner
![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/6b3e0934-4fd4-4bef-9b3b-a5b206e48e95)

## ER Diagram
![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/eb76a777-f7c9-4959-bae0-4b8781c648bb)

## Problem Statement
Danny wants to use the data to answer a few simple questions about his customers, especially about their visiting patterns, how much money they’ve spent and also which menu items are their favourite. 

You can visit [here] (https://8weeksqlchallenge.com/case-study-1/) to view the dataset

## Solution

**1. What is the total amount each customer spent at the restaurant?**

```SQL
SELECT customer_id,
SUM(price) as total_sum
FROM dannys_diner.sales s
INNER JOIN dannys_diner.menu m
ON s.product_id = m.product_id
GROUP BY 1
ORDER BY 1 ASC;
```
**Remarks**
1. Looking at ER diagram we know to do **JOIN** query as the customer_id and price is of different table 
2. to get total we use **SUM** function and **GROUP BY 1** just means grouping by the **SELECT ORDER**
   1. customer_id
   2. SUM(price) as total_sum
3. Finally **ORDER BY 1 ASC** is just sorting it by customer in Ascending order as **JOIN** scrambles the row to make the query run faster
![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/829c5f76-cff2-42f7-8b28-45faf93cac9d)
 
