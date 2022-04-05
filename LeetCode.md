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

