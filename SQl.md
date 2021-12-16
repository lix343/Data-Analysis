# 1. SQL-Data change statements

### Four Main types of change statements

- INSERT:  Insert row(s) into a table
- DELETE: Delete row(s) into a table
- UPDATE: Update row(s) into a table
- SELECT: Retrieve data from tables.

![image-20211216050310558](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216050310558.png)

```sql
SELECT *
FROM courses
```

This returns exact table as it shown above.

### SELECT 用法

```sql
SELECT lecturer
FROM courses
```

returns lecturer (have duplicates):

![image-20211216050646253](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216050646253.png)

 

```sql
SELECT DISTINCT lecturer
FROM courses	
```

![image-20211216050756986](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216050756986.png)

```sql
SELECT *
FROM courses
WHERE lecturer = 2;
```

![image-20211216050835623](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216050835623.png)

```SQL
SELECT *
FROM courses
WHERE cid < lecturer;
```

![image-20211216050947775](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216050947775.png)



```sql
SELECT *
FROM courses
WHERE title = 'databases';
```

![image-20211216051053654](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216051053654.png)



```sql
SELECT *
FROM courses
WHERE title LIKE '%databases%';
```

![image-20211216051133224](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216051133224.png)



```sql
SELECT *, cid + 5 AS one, cid * lecturer as two
FROM courses
```

![image-20211216051248343](C:\Users\lixin\AppData\Roaming\Typora\typora-user-images\image-20211216051248343.png)



