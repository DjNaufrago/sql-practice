**BD:** hospital.db

**TABLE:** patients
| Column | Type |
| --- | --- |
| patient_id* | INT |
| first_name | TEXT |
| last_name | TEXT |
| gender | CHAR(1) |
| birth_date | DATE |
| city | TEXT |
| province_id* | CHAR(2) |
| allergies | TEXT |
| height | INT |
| weight | INT |

**TABLE:** province_names
| Column | Type |
| --- | --- |
| province_id* | CHAR(2) |
| province_named | TEXT |

**TABLE:** admissions
| Column | Type |
| --- | --- |
| patient_id* | INT |
| admission_date | DATE |
| admission_datee | DATE |
| diagnosis | TEXT |
| attending_doctor_id* | INT |


1. Show first name, last name, and gender of patients whose gender is 'M'
```
SELECT first_name, last_name, gender
FROM patients
WHERE gender = 'M';
```

**SELECT:** https://www.w3schools.com/sql/sql_select.asp
**WHERE:** https://www.w3schools.com/sql/sql_where.asp

2. Show first name and last name of patients who does not have allergies. (null)
```
SELECT first_name, last_name
FROM patients
WHERE allergies IS NULL;
```

**NULL:** https://www.w3schools.com/sql/sql_null_values.asp

3. Show first name of patients that start with the letter 'C'
```
SELECT first_name
FROM patients
WHERE first_name LIKE 'C%';
```

**LIKE:** https://www.w3schools.com/sql/sql_like.asp

4. Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)
```
SELECT first_name, last_name
FROM patients
WHERE weight BETWEEN 100 AND 120;
```

**BETWEEN:** https://www.w3schools.com/sql/sql_between.asp

5. Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'
```
UPDATE patients
SET allergies = 'NKA'
WHERE allergies IS NULL;
```

**UPDATE:** https://www.w3schools.com/sql/sql_update.asp

6. Show first name and last name concatinated into one column to show their full name.
```
SELECT CONCAT(first_name, " ", last_name) AS full_name
FROM patients;
```

**AS:** https://www.w3schools.com/sql/sql_ref_as.asp
**CONCAT:** https://www.w3schools.com/sql/func_sqlserver_concat.asp

7. Show first name, last name, and the full province name of each patient. Example: 'Ontario' instead of 'ON'
```
SELECT first_name, last_name, province_name
FROM patients
JOIN province_names ON patients.province_id = province_names.province_id;
```

**JOINS:** https://www.w3schools.com/sql/sql_join.asp

8. Show how many patients have a birth_date with 2010 as the birth year.
```
SELECT COUNT(*) AS total_patients
FROM patients
WHERE YEAR(birth_date) = 2010;
```

**COUNT:** https://www.w3schools.com/sql/sql_count.asp
**YEAR:** https://www.w3schools.com/sql/func_sqlserver_year.asp

9. Show the first_name, last_name, and height of the patient with the greatest height.
```
SELECT first_name, last_name, MAX(height)
FROM patients;
```

**MAX/MIN:** https://www.w3schools.com/sql/sql_min_max.asp

10. Show all columns for patients who have one of the following patient_ids: 1,45,534,879,1000
```SELECT *
FROM patients
where patient_id IN (1,45,534,879,1000);
```

**IN:** https://www.w3schools.com/sql/sql_in.asp

11. Show the total number of admissions
```
SELECT COUNT(*) AS total_admissions
FROM admissions;
```

12. Show all the columns from admissions where the patient was admitted and discharged on the same day.
```
SELECT *
FROM admissions
WHERE admission_date = discharge_date;
```

13. Show the patient id and the total number of admissions for patient_id 579.
```
SELECT patient_id, COUNT(patient_id) AS total_admissions
FROM admissions
WHERE patient_id = 579;
```

14. Based on the cities that our patients live in, show unique cities that are in province_id 'NS'.
```
SELECT DISTINCT(city) AS unique_cities
FROM patients
WHERE province_id = 'NS';
```

```
SELECT city
FROM patients
group by city
having province_id = 'NS';
```

**DISTINCT:** https://www.w3schools.com/sql/sql_distinct.asp
**GROUP BY:** https://www.w3schools.com/sql/sql_groupby.asp
**HAVING:** https://www.w3schools.com/sql/sql_having.asp

15. Write a query to find the first_name, last name and birth date of patients who has height greater than 160 and weight greater than 70
```
SELECT first_name, last_name, birth_date
FROM patients
WHERE height > 160 AND weight > 70;
```

**AND:** https://www.w3schools.com/sql/sql_and.asp
**OPERATORS:** https://www.w3schools.com/sql/sql_operators.asp

16. Write a query to find list of patients first_name, last_name, and allergies where allergies are not null and are from the city of 'Hamilton'
```
SELECT first_name, last_name, allergies
FROM patients
WHERE allergies IS NOT NULL AND city = 'Hamilton';
```
