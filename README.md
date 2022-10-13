# SQL-DVD-rental-database-Power-BI-dashboard
My goal here was to display meaningful information with the use of Power BI.

I started off by importing all the tables from the database schema. I replicated the schema on Power BI to create a data model.

When the data model was completed, I tested it by using the matrix visualisation. I quickly realised that the model couldnt accurately filter data by: film category and address and thus I couldn't filter by city and country either. This was caused by the many-to-many connections I found between several tables in the data model. 

My solution to this was to remove the address table and the address_id from the customer table and replace it with city_id. I didn't need the customers whole address, just their country and city. I also removed the film_category table and film_category_id from the film table and replaced it with category_id from the category table. 

My soluton was acomplished by directly running sql scripts from Power BI. The scripts mainly consited of left joins. For example:

select customer_id, store_id, first_name||' '||last_name as Full_name, email, c.city_id as city_id

from customer a 

left join address b using(address_id)

left join city c using(city_id)


Once the data model was finally completed. I started craeting DAX calculated measures and columns so that performance metrics could be measured from the data 
and then displayed using charts. 
