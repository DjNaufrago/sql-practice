**BD:** northwind.db

**TABLE:** categories
| Column | Type |
| --- | --- |
| category_id* | INT |
| category_name | TEXT |
| description | TEXT |


**TABLE:** customers
| Column | Type |
| --- | --- |
| customer_id* | TEXT |
| company_name | TEXT |
| contact_name | TEXT |
| contact_title | TEXT |
| address | TEXT |
| city | TEXT |
| region | TEXT |
| region | TEXT |
| postal_code | TEXT |
| country | TEXT |
| phone | TEXT |
| fax | TEXT |


**TABLE:** orders
| Column | Type |
| --- | --- |
| order_id* | INT |
| customer_id* | TEXT |
| employee_id* | INT |
| order_date | DATE |
| required_date | DATE |
| shipped_date | DATE |
| ship_via | INT |
| freight | DECIMAL |
| ship_name | TEXT |
| ship_address | TEXT |
| ship_city | TEXT |
| ship_region | TEXT |
| ship_postal_code | TEXT |
| ship_country | TEXT |


**TABLE:** employees
| Column | Type |
| --- | --- |
| employee_id* | INT |
| last_name | TEXT |
| first_name | TEXT |
| title | TEXT |
| title_of_courtesy | TEXT |
| birth_date | DATE |
| hire_date | DATE |
| address | TEXT |
| city | TEXT |
| region | TEXT |
| postal_code | TEXT |
| country | TEXT |
| home_phone | TEXT |
| extension | TEXT |
| reports_to* | TEXT |


**TABLE:** products
| Column | Type |
| --- | --- |
| product_id* | INT |
| product_name | TEXT |
| supplier_id* | INT |
| category_id* | INT |
| quantity_per_unit | TEXT |
| unit_price | DECIMAL |
| units_in_stock | INT |
| units_on_order | INT |
| reorder_level | INT |
| discontinued | INT |

*Primary key

**1.** Show the category_name and description from the categories table sorted by category_name.
```
SELECT category_name, description
FROM categories
ORDER BY category_name;
```

**SELECT:** https://www.w3schools.com/sql/sql_select.asp </br>
**FROM:** https://www.w3schools.com/sql/sql_ref_from.asp </br>
**ORDER BY:** https://www.w3schools.com/sql/sql_ref_order_by.asp

**2.** Show all the contact_name, address, city of all customers which are not from 'Germany', 'Mexico', 'Spain'
```
SELECT contact_name, address, city
FROM customers
WHERE country NOT IN ('Germany', 'Mexico', 'Spain');
```

**NOT:** https://www.w3schools.com/sql/sql_not.asp </br>
**IN:** https://www.w3schools.com/sql/sql_in.asp

**3.** Show order_date, shipped_date, customer_id, Freight of all orders placed on 2018 Feb 26
```
SELECT order_date, shipped_date, customer_id, freight
FROM orders
WHERE order_date = '2018-02-26';
```

**SQL OPERATORS:** https://www.w3schools.com/sql/sql_operators.asp </br>
**WORKING WITH DATES:** https://www.w3schools.com/sql/sql_dates.asp

**4.** Show the employee_id, order_id, customer_id, required_date, shipped_date from all orders shipped later than the required date
```
SELECT employee_id, order_id, customer_id, required_date, shipped_date
FROM orders
WHERE shipped_date > required_date;
```

**5.** Show all the even numbered Order_id from the orders table
```
SELECT order_id
FROM orders
WHERE MOD(order_id, 2) = 0;
```

```
SELECT order_id
FROM orders
WHERE order_id % 2 = 0;
```

**MOD:** https://www.w3schools.com/sql/func_mysql_mod.asp

**6.** Show the city, company_name, contact_name of all customers from cities which contains the letter 'L' in the city name, sorted by contact_name
```
SELECT city, company_name, contact_name
FROM customers
WHERE city LIKE '%L%'
ORDER BY contact_name;
```

**LIKE:** https://www.w3schools.com/sql/sql_like.asp

**7.** Show the company_name, contact_name, fax number of all customers that has a fax number. (not null)
```
SELECT company_name, contact_name, fax
FROM customers
WHERE fax IS NOT NULL;
```

**NULL:** https://www.w3schools.com/sql/sql_null_values.asp

**8.** Show the first_name, last_name. hire_date of the most recently hired employee.
```
SELECT first_name, last_name, MAX(hire_date) AS hire_date
FROM employees;
```

**MIN/MAX:** https://www.w3schools.com/sql/sql_min_max.asp

**9.** Show the average unit price rounded to 2 decimal places, the total units in stock, total discontinued products from the products table.
```
SELECT ROUND(AVG(unit_price), 2) AS avg_unit_price,
SUM(units_in_stock) AS total_stock,
SUM(discontinued) AS total_discontinued
FROM products;
```

**AVG:** https://www.w3schools.com/sql/sql_avg.asp </br>
**ROUND:** https://www.w3schools.com/sql/func_sqlserver_round.asp
**AS:** https://www.w3schools.com/sql/sql_ref_as.asp
**SUM:** https://www.w3schools.com/sql/sql_sum.asp
