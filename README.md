# Home_Sales

In this challenge, you'll use your knowledge of SparkSQL to determine key metrics about home sales data. Then you'll use Spark to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached.

The challenge had the following instructions: 

1. Rename the Home_Sales_starter_code.ipynb file as Home_Sales.ipynb.

2. Import the necessary PySpark SQL functions for this assignment.

3. Read the home_sales_revised.csv data in the starter code into a Spark DataFrame.

4. Create a temporary table called home_sales.

5. Answer the following questions using SparkSQL:

6. What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.

7. What is the average price of a home for each year it was built that has three bedrooms and three bathrooms? Round off your answer to two decimal places.

8. What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.

9. What is the "view" rating for homes costing more than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.

10. Cache your temporary table home_sales.

11. Check if your temporary table is cached.

12. Using the cached data, run the query that filters out the view ratings with an average price of greater than or equal to $350,000. Determine the runtime and compare it to uncached runtime.

13. Partition by the "date_built" field on the formatted parquet home sales data.

14. Create a temporary table for the parquet data.

15. Run the query that filters out the view ratings with an average price of greater than or equal to $350,000. Determine the runtime and compare it to uncached runtime.

16. Uncache the home_sales temporary table.

17. Verify that the home_sales temporary table is uncached using PySpark.

18. Download your Home_Sales.ipynb file and upload it into your "Home_Sales" GitHub repository.


The following code was written with the help of a TA during office hours, with help through ASKBCS and the resources provided: 
avg_price_q1 = """
SELECT YEAR(date) AS YEAR_BUILT, ROUND(AVG(price), 2) AS avg_price
FROM home_sales
WHERE bedrooms == 4
GROUP BY YEAR_BUILT
ORDER BY YEAR_BUILT
"""
spark.sql(avg_price_q1).show()

view_rating_q4 = ("""SELECT view, ROUND(AVG(price), 2) AS avg_price
FROM home_sales
WHERE price >=350000 GROUP BY view order by view DESC""")

Resources:
https://stackoverflow.com/questions/58042644/error-with-sparksession-getorcreate-function 
https://stackoverflow.com/questions/39780792/how-to-build-a-sparksession-in-spark-2-0-using-pyspark
