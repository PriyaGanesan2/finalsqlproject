Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
- Create CTE. 
- Fetch fullvisitorid,city,country,prodrevenue for each user,country and city combination from visitor table and analytics table using inner join.
- In this same join, calculate total transactio revenue for each fulluserid,county and city combination
- From the above cte, write a select query to fetch country and sum(revenue) for each country
- Reuse the same cte and write a select query to fetch city and sum(revenue) for each city.
```
with tran_cte as (
	--Fetch visitorid,city,country,sum(revenue) for each user.
	--assumption: User and city , country combination is unique. one user can reside only in one country, city at any given time.
	select  v.fullvisitorid,v.city,v.country,
	aq.prodrevenue,sum(aq.prodrevenue)
	over(partition by v.fullvisitorid) as totalrev
	from visitor_q1 v
	inner join analytics_q2 aq on 
	v.fullvisitorid=aq.fullvisitorid
	order by totalrev DESC)
-- Fetch top 5 Countries that have the higest transaction revenue
select country,sum(prodrevenue) as revenue
from tran_cte
group by country 
order by revenue desc
limit 5
```
- Fech cities that have the highest transactions
```
with tran_cte as (
	select  v.fullvisitorid,v.city,v.country,
	aq.prodrevenue,sum(aq.prodrevenue)
	over(partition by v.fullvisitorid) as totalrev
	from visitor_q1 v
	inner join analytics_q2 aq on 
	v.fullvisitorid=aq.fullvisitorid
	order by totalrev DESC)
select city,sum(prodrevenue) as revenue
```


Answer:

<img width="222" alt="Screenshot 2023-10-30 at 10 44 58 PM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/f5a8c9b4-4a9d-4a00-b2ce-c3e9070313ec">
<img width="267" alt="Screenshot 2023-10-30 at 10 47 07 PM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/795a5c3a-d196-4e42-afcc-050758c31948">


**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```
with tran_cte as (
	select  v.fullvisitorid,v.city,v.country,
	aq.units_sold,sum(aq.units_sold)
	--fetch total products ordered for each county,city
	over(partition by v.fullvisitorid) as productsordered
	from visitor_q1 v
	inner join analytics_q2 aq on 
	v.fullvisitorid=aq.fullvisitorid
	where aq.units_sold!=0
	order by productsordered DESC)
-- Fetch Countries that have the higest transactions
select country,round(avg(productsordered),0) as avgproductsordered
from tran_cte
group by country 
order by avgproductsordered desc

```
- Fetch city details

```
with tran_cte as (
	select  v.fullvisitorid,v.city,v.country,
	aq.units_sold,sum(aq.units_sold)
	over(partition by v.fullvisitorid) as productsordered
	from visitor_q1 v
	inner join analytics_q2 aq on 
	v.fullvisitorid=aq.fullvisitorid
	where aq.units_sold!=0	
	order by productsordered DESC)
-- Fetch Cities that have the higest product sold
select city,round(avg(productsordered),0) as avgproductsordered
from tran_cte
where city!='NA' --- Excluding CITY that are null
group by city 
order by avgproductsordered desc

```


Answer:

![image](https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/60ed0500-24d0-4440-8cd4-7f6af7f08d36)


<img width="135" alt="Screenshot 2023-10-30 at 10 40 23 PM" src="https://github.com/PriyaGanesan2/finalsqlproject/assets/110922792/a8ab4bfb-8d30-4124-abbf-0a2fc61ac5b8">

**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







