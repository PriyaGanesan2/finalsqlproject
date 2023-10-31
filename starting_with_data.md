Question 1: 

SQL Queries:
1. To find unique record
```
select distinct(fullvisitorid) from all_sessions_q1
```

Answer: 
<img width="785" alt="Screenshot 2023-10-31 at 2 27 38 AM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/05b72330-a377-4e1e-9838-ffc4430e0f59">



Question 2: 
2. To find duplicate records


SQL Queries:
```
WITH sku_CTE AS (SELECT PRODUCTSKU, V2PRODUCTCATEGORY, ROW_NUMBER() OVER
	(PARTITION BY PRODUCTSKU ORDER BY PRODUCTSKU)
	 rownum FROM temp_cat_prod)
select * FROM sku_CTE  WHERE rownum>1

```
Answer:
<img width="785" alt="Screenshot 2023-10-31 at 2 30 52 AM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/82357384-403b-43d1-8b96-9b5345ab8d33">



Question 3: 
3. To find the products sale from paid search and if it was effective

SQL Queries:
```
with cte as(
	select 
	v.fullvisitorid,s.channelgrouping,
	s.productquantity 
	from visitor_q1 v
	left join all_sessions_q1 s
	on v.fullvisitorid=s.fullvisitorid
	where s.productquantity!=0
	order by s.productquantity desc, s.channelgrouping)
```
Answer:
<img width="329" alt="Screenshot 2023-10-31 at 2 31 43 AM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/9310b96e-9032-41cd-b0dc-c3a1f95295d9">



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
