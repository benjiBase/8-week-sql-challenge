# Case Study #1 : Danny's Diner
![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/6b3e0934-4fd4-4bef-9b3b-a5b206e48e95)

## ER Diagram
![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/eb76a777-f7c9-4959-bae0-4b8781c648bb)

## Problem Statement
Danny wants to use the data to answer a few simple questions about his customers, especially about their visiting patterns, how much money they’ve spent and also which menu items are their favourite. 

You can visit [here] (https://8weeksqlchallenge.com/case-study-1/) to view the dataset

## Solution

**1. What is the total amount each customer spent at the restaurant?**

```sql
SELECT
   customer_id,
   SUM(price) as total_sum
FROM dannys_diner.sales s
INNER JOIN dannys_diner.menu m
   ON s.product_id = m.product_id
GROUP BY 1
ORDER BY 1 ASC;
```

![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/829c5f76-cff2-42f7-8b28-45faf93cac9d)
 
**Remarks**
1. Looking at ER diagram we know to do **JOIN** query as the customer_id and price is of different table 
2. to get total we use **SUM** function and **GROUP BY 1** just means grouping by the **SELECT ORDER**
   1. customer_id
   2. SUM(price) as total_sum
3. Finally **ORDER BY 1 ASC** is just sorting it by customer in Ascending order as **JOIN** scrambles the row to make the query run faster

**2. How many days has each customer visited the restaurant?**
```sql
SELECT
   customer_id,
   COUNT(DISTINCT order_date)
FROM sales
GROUP BY 1
```
![image](https://github.com/benjiBase/8-week-sql-challenge/assets/70194504/4dd24719-b15a-4511-b407-995cbb91b70a)

**Remarks**
1. to count days we can just use **COUNT** function BUT
   1. Looking at sales table, we know that the order_date have duplicates meaning that a customer can visit the restuarant for lunch and dinner
   2. **BUT** the question we are trying to answer is number of days each customer has visited and **NOT** total times visited
   3. Hence we use the keyword DISTINCT that only return 1 unique entry of any particular date
2. **GROUP BY** is **needed** because when **COUNT/aggregate functions of SQL** requires us base it of a certain grouping logic
   1. else u see a warning like ```ERROR:  column "sales.customer_id" must appear in the GROUP BY clause or be used in an aggregate function```


**3. What was the first item from the menu purchased by each customer?**


**4. What is the most purchased item on the menu and how many times was it purchased by all customers?**


**5. Which item was the most popular for each customer?**


**6. Which item was purchased first by the customer after they became a member?**


**7. Which item was purchased just before the customer became a member?**


**8. What is the total items and amount spent for each member before they became a member?**


**9. If each $1 spent equates to 10 points and sushi has a 2x points multiplier - how many points would each customer have?**


**10. In the first week after a customer joins the program (including their join date) they earn 2x points on all items, not just sushi - how many points do customer A and B have at the end of January?**

