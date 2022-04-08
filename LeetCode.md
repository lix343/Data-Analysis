## 181 Employees Earning More Than Their Managers

* We are given the table **Employee** as follows:

  * ```sql
    +-------------+---------+
    | Column Name | Type    |
    +-------------+---------+
    | id          | int     |
    | name        | varchar |
    | salary      | int     |
    | managerId   | int     |
    +-------------+---------+
    ```

  * id is the primary key for the table

* Our expected output is:

  * ```sql
    Input: 
    Employee table:
    +----+-------+--------+-----------+
    | id | name  | salary | managerId |
    +----+-------+--------+-----------+
    | 1  | Joe   | 70000  | 3         |
    | 2  | Henry | 80000  | 4         |
    | 3  | Sam   | 60000  | Null      |
    | 4  | Max   | 90000  | Null      |
    +----+-------+--------+-----------+
    Output: 
    +----------+
    | Employee |
    +----------+
    | Joe      |
    +----------+
    ```

Our expected output is only one column with employee as the name of the column.

1. We first pass all the employee without manager-Id which means they don't have a manager.
2. We only care employee whose manager-Id is not **Null**.
3. We only do the comparison between the employee and its manager.

``` sql
SELECT 
	a.name as Employee
FROM Employee a JOIN Employee b 
	ON a.managerId = b.id
	AND a.salary > b.salary
```



### 1757 Recyclable and Low Fat Products

* We are given a product table to find which product is both recyclable and low fat.

```
Input: 
Products table:
+-------------+----------+------------+
| product_id  | low_fats | recyclable |
+-------------+----------+------------+
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |
+-------------+----------+------------+
Output: 
+-------------+
| product_id  |
+-------------+
| 1           |
| 3           |
+-------------+
```

* This is simple:
* We can use **WHERE** clause to filter out the results.
* Here are several ways to accomplish it:
  * low_fats='Y' **AND** recyclable='Y'
  * low_fats **LIKE** 'Y%' **AND** recyclable **LIKE** 'Y%'
* **LIKE** clause
  * If you use 'Y%', you are looking for string which contains Y as the first element, no matter what's following that
  * If you use '%Y%', you are looking for a string which contains Y in the middle.
  * If you use '%Y_', you are looking for a string which contains Y as the last second element.

``` sql
SELECT
    product_id
FROM
    Products
WHERE
    low_fats LIKE 'Y%' AND recyclable LIKE 'Y%'
```

### 1693. Daily Leads and Partners

* We are given a table Daily-sales

```
Input: 
DailySales table:
+-----------+-----------+---------+------------+
| date_id   | make_name | lead_id | partner_id |
+-----------+-----------+---------+------------+
| 2020-12-8 | toyota    | 0       | 1          |
| 2020-12-8 | toyota    | 1       | 0          |
| 2020-12-8 | toyota    | 1       | 2          |
| 2020-12-7 | toyota    | 0       | 2          |
| 2020-12-7 | toyota    | 0       | 1          |
| 2020-12-8 | honda     | 1       | 2          |
| 2020-12-8 | honda     | 2       | 1          |
| 2020-12-7 | honda     | 0       | 1          |
| 2020-12-7 | honda     | 1       | 2          |
| 2020-12-7 | honda     | 2       | 1          |
+-----------+-----------+---------+------------+
Output: 
+-----------+-----------+--------------+-----------------+
| date_id   | make_name | unique_leads | unique_partners |
+-----------+-----------+--------------+-----------------+
| 2020-12-8 | toyota    | 2            | 3               |
| 2020-12-7 | toyota    | 1            | 2               |
| 2020-12-8 | honda     | 2            | 2               |
| 2020-12-7 | honda     | 3            | 2               |
+-----------+-----------+--------------+-----------------+
```

```sql
SELECT
    date_id, make_name, 
    COUNT(DISTINCT lead_id) AS unique_leads, 
    COUNT(DISTINCT partner_id) AS unique_partners
FROM   
    DailySales
GROUP BY
    date_id,make_name
```

### 1741. Find Total Time Spent by Each Employee

```SQL
Input: 
Employees table:
+--------+------------+---------+----------+
| emp_id | event_day  | in_time | out_time |
+--------+------------+---------+----------+
| 1      | 2020-11-28 | 4       | 32       |
| 1      | 2020-11-28 | 55      | 200      |
| 1      | 2020-12-03 | 1       | 42       |
| 2      | 2020-11-28 | 3       | 33       |
| 2      | 2020-12-09 | 47      | 74       |
+--------+------------+---------+----------+
Output: 
+------------+--------+------------+
| day        | emp_id | total_time |
+------------+--------+------------+
| 2020-11-28 | 1      | 173        |
| 2020-11-28 | 2      | 30         |
| 2020-12-03 | 1      | 41         |
| 2020-12-09 | 2      | 27         |
+------------+--------+------------+
Explanation: 
Employee 1 has three events: two on day 2020-11-28 with a total of (32 - 4) + (200 - 55) = 173, and one on day 2020-12-03 with a total of (42 - 1) = 41.
Employee 2 has two events: one on day 2020-11-28 with a total of (33 - 3) = 30, and one on day 2020-12-09 with a total of (74 - 47) = 27.
```

* Answer

``` SQl
SELECT
    event_day as day, emp_id, SUM(out_time - in_time) AS total_time
FROM
    Employees
GROUP BY
    event_day, emp_id
```

### 182. Duplicate Emails

```sql
Input: 
Person table:
+----+---------+
| id | email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
Output: 
+---------+
| Email   |
+---------+
| a@b.com |
+---------+
```

Answer:

``` sql
SELECT
    email as Email
FROM 
    Person
GROUP BY
    email
HAVING
    COUNT(email) > 1
```

###  176 Second Highest Salary

```sql
Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
```

```sql
Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| null                |
+---------------------+
```

Answer:

``` sql
SELECT
    MAX(salary) AS SecondHighestSalary
FROM
    Employee
WHERE
    salary < (SELECT MAX(salary) FROM Employee)
```

### 183 Customers Who Never Order

```sql
Input: 
Customers table:
+----+-------+
| id | name  |
+----+-------+
| 1  | Joe   |
| 2  | Henry |
| 3  | Sam   |
| 4  | Max   |
+----+-------+
Orders table:
+----+------------+
| id | customerId |
+----+------------+
| 1  | 3          |
| 2  | 1          |
+----+------------+
Output: 
+-----------+
| Customers |
+-----------+
| Henry     |
| Max       |
+-----------+
```

Answer:

``` sql
SELECT
    name as Customers
FROM  
    Customers
WHERE
    id NOT IN (SELECT customerId FROM Orders)
```

777777

### 184. Department Highest Salary



