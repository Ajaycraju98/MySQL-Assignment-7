# MySQL-Assignment-7
This  Assignment explains about the Functions in MySQL
-- Consider the Country table and Persons table that you created earlier and perform the following: 
-- 1. Add a new column called DOB in Persons table with data type as Date. 
alter table persons  Add  column  DOB DATE ;
select * from persons ;
-- 2. Write a user-defined function to calculate age using DOB. 
DELIMITER $$

CREATE FUNCTION Age (DOB DATE)
RETURNS INT
DETERMINISTIC
BEGIN
DECLARE age INT;
SET age = TIMESTAMPDIFF(YEAR, DOB, CURDATE());
RETURN age;
END $$

DELIMITER ;
SELECT AGE ('1998-04-02') AS AGE_OF_PERSONS ; 
-- 3. Write a select query to fetch the Age of all persons using the function that has been created. 
Update persons set DOB='1998-04-02'where Id=2;
Update persons set DOB='1997-01-05'where Id=1;
Update persons set DOB='1998-06-02'where Id=3;
Update persons set DOB='1994-02-06'where Id=4;
Update persons set DOB='1995-01-07'where Id=5;
Update persons set DOB='1999-01-07'where Id=6;
Update persons set DOB='1998-02-07'where Id=7;
Update persons set DOB='1998-05-01'where Id=8;
Update persons set DOB='1993-09-10'where Id=9;
Update persons set DOB='1992-01-04'where Id=10;
Update persons set DOB='1992-04-03'where Id=11;
Update persons set DOB='1992-07-04'where Id=12;

SELECT F_name, DOB, Age(DOB) AS Age FROM persons;

-- 4. Find the length of each country name in the Country table. 
SELECT Country_name, LENGTH(Country_name) AS Length_of_country_name
FROM country;
-- 5. Extract the first three characters of each country's name in the Country table. 
SELECT Country_name, SUBSTRING(Country_name, 1, 3) AS First_three_characters_of_country_name
FROM Country;

-- 6. Convert all country names to uppercase and lowercase in the Country table.
SELECT Country_name, UPPER(Country_name) AS Uppercase_country_Name FROM country;
SELECT Country_name, lower(Country_name) AS Lowercase_country_Name FROM country;

