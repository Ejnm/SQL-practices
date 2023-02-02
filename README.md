# SQL-practices level Easy
SQL practices from https://www.sql-practice.com/


1.Show first name, last name, and gender of patients who's gender is 'M'

SELECT first_name, last_name, gender
FROM patients
WHERE gender='M';


2.Show first name and last name of patients who does not have allergies. (null)

SELECT first_name, last_name
FROM patients
WHERE allergies is null


4.Show first name of patients that start with the letter 'C'

SELECT first_name
FROM patients
WHERE first_name like 'C%';


5.Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)

select first_name, last_name
from patients
WHERE weight between 100 and 120;


6.Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'

update patients
set allergies ='NKA'
where allergies is null;


7.Show first name and last name concatinated into one column to show their full name.

select concat (first_name,' ', last_name) as full_name
FROM patients;



8.Show first name, last name, and the full province name of each patient.
Example: 'Ontario' instead of 'ON'


select first_name, last_name, province_name
FROM patients
join province_names 
on province_names.province_id = patients.province_id;


9.Show how many patients have a birth_date with 2010 as the birth year.

select count(birth_date)
from patients
where year (birth_date) = 2010;


10.
Show the first_name, last_name, and height of the patient with the greatest height.

select first_name, last_name, MAX(height)
from patients;


11.
Show the total number of admissions

select count(*) total_admissions
from admissions;


12.Show all the columns from admissions where the patient was admitted and discharged on the same day.

select*
from admissions
where admission_date= discharge_date;


13.Show the patient id and the total number of admissions for patient_id 579.

select patient_id,
count(*) AS  total_admissions
from admissions
WHERE patient_id = 579;


14.Show all columns for patients who have one of the following patient_ids:
1,45,534,879,1000

select*
from patients
 where patient_id in (1, 45, 534, 879, 1000);
 
 
 15.Based on the cities that our patients live in, show unique cities that are in province_id 'NS'?
 
 select distinct city
from patients
where province_id = 'NS';


16.Write a query to find the first_name, last name and birth date of patients who have height more than 160 and weight more than 70

select first_name, last_name, birth_date
from patients
where height > 160 and weight > 70;


17.Write a query to find list of patients first_name, last_name, and allergies from Hamilton where allergies are not null

select first_name, last_name, allergies

FROM patients

WHERE city is 'Hamilton' ANd allergies is NOT 'NKA' AND allergies IS NOT NULL;


18.Based on cities where our patient lives in, write a query to display the list of unique city starting with a vowel 
(a, e, i, o, u). Show the result order in ascending by city.

select distinct city

from patients

where
  city like 'a%'
  or city like 'e%'
  or city like 'i%'
  or city like 'o%'
  or city like 'u%'
order by city

