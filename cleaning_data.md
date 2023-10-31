What issues will you address by cleaning the data?
- Remove NULL and replace with 'NA' for varchar column type
- Remove NULL and replace with 0 for numeric column type
- The unit cost , product revennue, transaction revenue in the data needs to be divided by 1,000,000.
- wherever, unit cost and product quaktity is mentioned and product revenue is null, it can be calculated as unitcost*productquantity
- update all_sessions_q1 table and set v2productcategory='NA' where v2productcategory='(not set)'
- remove duplicate rows




Queries:
Below, provide the SQL queries you used to clean your data.
```
UPDATE  all_sessions_q1
SET ITEMQUANTITY=0 WHERE ITEMQUANTITY ISNULL
```
```
UPDATE  all_sessions_q1
SET TRANSACTIONREVENUE=TOTALTRANSACTIONREVENUE WHERE TRANSACTIONS=1 AND TRANSACTIONREVENUE=0
```
```
UPDATE all_sessions_q1 KSET COUNTRY='Myanmar' WHERE COUNTRY='Myanmar (Burma)'
```
```
UPDATE all_sessions_q1SET COUNTRY='NA' WHERE COUNTRY='(not set)'
```
```
UPDATE all_sessions_q1 SET COUNTRY='China' WHERE fullvisitorid='7199240861547271746'
```
```
update all_session_q1 set productrevenue=(productunitprice*productquantity) 
```
```
create table temp_cat_prod as (
  WITH sku_CTE AS (SELECT PRODUCTSKU,V2PRODUCTCATEGORY, ROW_NUMBER() OVER
  (PARTITION BY PRODUCTSKU,V2PRODUCTCATEGORY ORDER BY PRODUCTSKU,V2PRODUCTCATEGORY)
   rownum FROM temp )
select * FROM sku_CTE  WHERE rownum=1)
```
