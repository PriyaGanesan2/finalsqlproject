What are your risk areas? Identify and describe them.



QA Process:
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
	 
