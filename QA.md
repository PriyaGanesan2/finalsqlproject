What are your risk areas? Identify and describe them.



QA Process:
-   Example 1 - to check for duplicates and removing them before creating a table and then doing further QA to remove all duplicates.
Describe your QA process and include the SQL queries used to execute it.
- Created a table visitor_q1 to maintain fullvisitorid , city and county details
-  STPE 1: SELECT * INTO TEMP FROM all_sessions_back
-  DELETE ALL COULUMNS FROM THIS TABLE OTHER THAN THE 3 COLUMNS AS MENTIONED IN STEP1
-  Do a select to check the count
   ```
   select count(*) from all_sessions_back
   --fetched 15134
   SELECT COUNT(DISTINCT(FULLVISITORID)) FROM VISITOR
   -- Fetched 14201
   ```
-  DELETE DUPLICATE ROWS
  -   STEP1
  ```
SELECT VISITOR_TEMP AS(  
    WITH VISITOR_CTE AS (SELECT fullVisitorId,city,country, ROW_NUMBER() OVER
    (PARTITION BY fullVisitorId,city,country ORDER BY fullVisitorId,city,country )
     rownum FROM VISITOR )
select * FROM VISITOR_CTE WHERE rownum=1)
  ```

  
-    Step 2 : city and county null. delete both
-    Step3 : Multiple columns with same countyname and city as na. delete the duplicates
-    step4:  DELETE where COUNTRY='NA' AND CITY='NA'
-    Step 5: Valiodate to check the counts 
-    
  ```
  
  SELECT COUNT(*) FROM VISITOR
  14201

  SELECT COUNT(DISTINCT(FULLVISITORID)) FROM VISITOR
  14201
```
- step5: Alter table to make fullvisitoris as Primary key
```
ALTER TABLE visitor_q1
ADD PRIMARY KEY (fullvisitorid);
```
- Step 6: Remove city ad county fields from aa_sessions_back table 
	 
- Example 2: To check if joint query is fetching the correct rows as expected
```
select count(*) from all_sessions_q1
--- 15134

-to validate my join is fetching only the rows from the first table, part of the sql code was commented out and only a part was  run to check if the rows cout matches

<img width="785" alt="Screenshot 2023-10-31 at 1 02 05 AM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/b2596297-ae36-41b1-bbec-663754d0be4c">

- Since both returned 15134, i could safely validate my query.
- 
