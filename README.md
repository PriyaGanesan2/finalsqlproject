# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
- Load the csv fileL
- look into the tables and undestand a bit more abou the data and how they are related
- clean the data
- start answering the questions
- fill in the *.md files

## Process
### (your step 1)
Part 1: Loading csv Files into Database
--PART 1

-- 1. CLONE GIT REPO TO LOCAL MACHINE.
--     CODE --> GET HTTS LINK AND COPY THE LINK
-- 	GO TO THE FOLDER IN LOCAL MACHINE WHERE YOU WANT TO CLONE THIS FOLDER 
-- 	git clone <HTTPS LINK FROM PROVIOUS STEP>
-- 	https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository
-- 2. DOWNLOAD THE CSV FILES AND CRAETE DB ECOMMERCE
--     1. COPY THE HEADER COLOUM OF THE CSV
-- 	2. CONVERT TO TEXT
-- 	3. CREATE TEH SQL QUERY TO CRAETE TABLE
-- 	4. KEEP ALL FIELDS AS VARCHAR
-- 	5. CREATE TABLE
-- 	6.REFRESH
-- 	7. RUN TRUNCATE TABLE QUERY
-- 	8. IMPORT/EXPORT CSV
-- 	9. QUERIES FOR THIS DB AS BELOW.
--  10, https://www.postgresqltutorial.com/postgresql-tutorial/import-csv-file-into-posgresql-table/

PART 2 
```
select count(*) from all_sessions
```
```
Create table analytics(
 visitNumber	varchar,
visitId varchar,	
visitStartTime varchar,	
date1 varchar,
fullvisitorId varchar,	
userid varchar,	
channelGrouping	varchar,
socialEngagementType varchar,	
units_sold varchar,	
pageviews varchar,	
timeonsite varchar,
bounces	varchar,
revenue	varchar,
unit_price varchar)
```

```
TRUNCATE TABLE analytics 
 RESTART IDENTITY;
```
```
select * from analytics
```
```
select * from all_sessions
```

```
Create table products(
SKU	 varchar,
name varchar,	
orderedQuantity varchar,	
stockLevel varchar,	
restockingLeadTime varchar,		
sentimentScore varchar,	
sentimentMagnitude varchar)
```

```
TRUNCATE TABLE products
RESTART IDENTITY;
```

```
select * from products
```
```
Create table sales_by_sku(
productSKU	varchar,
otal_ordered varchar)
```
```
TRUNCATE TABLE sales_by_sku
 RESTART IDENTITY;
```
 
```
select * from sales_by_sku
```
```
Create table sales_report(
productSKU	varchar,
total_ordered	 varchar,
name1 varchar,
stockLevel varchar,
restockingLeadTime varchar,	
 sentimentScore varchar,	
sentimentMagnitude	varchar,
ratio varchar)
```
```
TRUNCATE TABLE sales_report
RESTART IDENTITY;
```
 
```
select * from sales_report
```


## Results
- The data in the ecommerce database helped me understand a part of the flow of this ecommerce website.
- This analysis further helped me in answering the questions required to cpltete this project

## Challenges 
(discuss challenges you faced in the project)
- The data that is provided here is enormus and a lot of time went into understanding them and then cleaning to complete the project.
- If i were to apprpach a problem like this again, I would be directly start with answering the questions first and see how these wpul lool at a high level and then start deep diving , cleaning and then iterating all over to refine the query
- 

## Future Goals
(what would you do if you had more time?)
-1. Analyse the alalytics table a bit more in details and come up with 
      -compute the percentage of visitors to the site that actually makes a purchase
      -find each unique product viewed by each visitor
      -work on the all_sessions table and clean it up a bit more to display category and productname values
      -deep dive a bit more to understan the data in other tables like sales_report and sales_by_sku
      - validate the solution for the  5 questions a bit more
