# Bikes_SQL_CLEANING
use bikes;

## UPDATING A COLUMN NAME
ALTER TABLE bikes_1 change ï»¿ID Id VARCHAR(10);


## UPDATE COLUMN VALUES
UPDATE bikes_1 SET Marital_Status = "Married" WHERE Marital_Status = "M";
UPDATE bikes_1 SET Marital_Status = "SIngle" WHERE Marital_Status = "S";
UPDATE bikes_1 SET Gender = "Male" WHERE Gender = "M";
UPDATE bikes_1 SET Gender = "Female" WHERE Gender = "F";

UPDATE bikes_1 SET `Commute Distance` = "11+ Miles" WHERE `Commute Distance` = "10+ Miles";
ALTER TABLE bikes_1 CHANGE `Commute Distance` Commute_Distance VARCHAR(20);
UPDATE bikes_1 SET Commute_Distance = "More than 10 Miles" WHERE Commute_Distance = "11+ Miles";


## CREATING A NEW TABLE WITH THE HELO OF THE CASE FUNCTION
select distinct*,
CASE
	WHEN Age BETWEEN 25 AND 35 THEN "Young"
	WHEN Age BETWEEN 36 AND 50 THEN "Middle Age"
	ELSE "Adult"
END AS Age_Category 
FROM bikes_1;


## USING CTE TO COUNT THE UNIQUE VALUES IN THIS TABLE
WITH uniques AS
(
	select distinct* from bikes_1
)
select count(Id)
from uniques
