# Assignment-1
Part A 
Answers
1.	First create a staging table. By this I mean a different excel sheet so that your original data remains the same way it was incase you want to make references later on. So copy the original data and paste into a new sheet and label it as staging table
   • Remove exact duplicate rows (define and document your duplicate criteria).
First select the entire sheet and click on format on the ribbon and then auto-fit column width so that your data fits well on the columns.
Now identify the columns with unique identities. One column is not enough. In this case we use order ID, Order date and SKU. 
We select the columns, click on data on the ribbon and then remove duplicates as shown below.
 


In this case, no duplicates were found. 
   • Fix data types (dates as Dates, numeric fields as numbers).
	Select every column,
	Right click
	Format cells. 
	For the cells with digits/numbers, format as numbers.
	For the sales with text, format as text,
	For the sales with date ie Order and required date, format as date
	The order ID and SKU should be formatted as text. 
	The Discount percentage should be formatted as % as shown below
 
Handle missing values for City, Salesperson, and Channel using reasonable business logic (document your approach).
Select the Column with the missing value
Click control +G
Click on Special >Blanks>Ok. 
Then on any blank cell on that column, write a placeholder Ie, 
For sales Person> Unassigned. 
City>Not indicated
Channel>Unknown
Click on Control+Enter as shown below
 
   Flag and correct suspicious UnitPrice values (e.g., negative prices) and discounts (e.g., > 30%).
Negative Prices
For negative Prices, we make them positive. This is by making them absolute values as shown below
 

Do this for both the unit price and cost
Discounts
For the discounts, Any discount price that is higher than 30%, should be decreased to 30%, otherwise, it should remain as it is. We therefore employ the If function. This is as shown below.
 
 Ensure Required Date is not earlier than Order Date; where it is, impute a corrected RequiredDate (explain your rule).
3 working days is the standard working and delivery time unless and otherwise.
So if the required date is lesser than the order date, add 3 working days to the order date. Otherwise, let the required date remain as it is as shown below

 

  Add a derived 'LeadTimeDays' = RequiredDate − OrderDate (in days).
This is as shown. I changed the dates to numbers.
 
Question 2
2) Create calculated columns (do these in Excel, not by formula in the data source):
  GrossRevenue = UnitPrice × Quantity × (1 − DiscountPct).
This is direct and as shown
 	

   CostOfGoods = UnitCost × Quantity.	

 

  Gross Profit = Gross Revenue − CostOfGoods.
This is direct and as shown below
 
  MarginPct = IF(Gross Revenue=0, 0, Gross Profit / Gross Revenue).
This is direct and as shown below
 

Question 3
3) Create standardized dimensions:
   Month (MMM-YYYY) from OrderDate.
With this I used the Text() Command which converts a date into a text string in the format you specify which in my case is MMM-YYYY. This is as shown below
 
	
   • Quarter (e.g., Q1-2024).
With this, we apply the Roundup formula
We divide by 3 because each quarter has 3 months
This is as shown below
 
This returns the quarter and the year.
  Region hierarchy: Region → Country → City.
Select the three columns, go to insert, insert pivot table, drag the fields into row in order. Start with region, then country then city. The result is as shown below
 



