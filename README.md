# Assignment-1
**Part A**
Answers
1.	First create a staging table. By this I mean a different excel sheet so that your original data remains the same way it was incase you want to make references later on. So copy the original data and paste into a new sheet and label it as staging table
   • Remove exact duplicate rows (define and document your duplicate criteria).
First select the entire sheet and click on format on the ribbon and then auto-fit column width so that your data fits well on the columns.
Now identify the columns with unique identities. One column is not enough. In this case we use order ID, Order date and SKU. 
We select the columns, click on data on the ribbon and then remove duplicates as shown below.
 
<img width="582" height="475" alt="image" src="https://github.com/user-attachments/assets/3e834618-33be-4109-b2e7-d58aac67e7a3" />


In this case, no duplicates were found. 
   • Fix data types (dates as Dates, numeric fields as numbers).
-Select every column,
-Right click
-Format cells. 
-For the cells with digits/numbers, format as numbers.
-For the sales with text, format as text,
-For the sales with date ie Order and required date, format as date
-The order ID and SKU should be formatted as text. 
-The Discount percentage should be formatted as % as shown below
<img width="453" height="330" alt="image" src="https://github.com/user-attachments/assets/878ff057-7341-42a4-ab6a-c509b75d572c" />

 
**Handle missing values for City, Salesperson, and Channel using reasonable business logic (document your approach)**
.Select the Column with the missing value
.Click control +G
.Click on Special >Blanks>Ok. 
.Then on any blank cell on that column, write a placeholder Ie, 
.For sales Person> Unassigned. 
.City>Not indicated
.Channel>Unknown
.Click on Control+Enter as shown below
<img width="449" height="502" alt="image" src="https://github.com/user-attachments/assets/65529dd7-d0dc-4c36-af31-57e0d9e6fd33" />

 
**Flag and correct suspicious UnitPrice values (e.g., negative prices) and discounts (e.g., > 30%).**
***Negative Prices***
For negative Prices, we make them positive. This is by making them absolute values as shown below


<img width="313" height="276" alt="image" src="https://github.com/user-attachments/assets/300d098f-7493-48d7-a9dc-6184c28bc705" />

 
.Do this for both the unit price and cost 
**Discounts**
For the discounts, Any discount price that is higher than 30%, should be decreased to 30%, otherwise, it should remain as it is. We therefore employ the If function. This is as shown below.


 <img width="404" height="259" alt="image" src="https://github.com/user-attachments/assets/a6d8f8b5-a6cd-43cd-a57c-3345e2265411" />

**Ensure Required Date is not earlier than Order Date; where it is, impute a corrected RequiredDate (explain your rule).**
3 working days is the standard working and delivery time unless and otherwise.
So if the required date is lesser than the order date, add 3 working days to the order date. Otherwise, let the required date remain as it is as shown below

<img width="517" height="91" alt="image" src="https://github.com/user-attachments/assets/d83d9173-2728-4ad0-bdeb-d0d694384de2" />



  Add a derived 'LeadTimeDays' = RequiredDate − OrderDate (in days).
This is as shown. Changed the dates to numbers.


 <img width="776" height="85" alt="image" src="https://github.com/user-attachments/assets/0c4c9acd-b041-4706-bf3f-2ee4dae3ea3f" />


**Question 2**
***2) Create calculated columns (do these in Excel, not by formula in the data source):
  GrossRevenue = UnitPrice × Quantity × (1 − DiscountPct).***
This is direct and as shown


 	<img width="729" height="107" alt="image" src="https://github.com/user-attachments/assets/f1ec45ff-62df-4492-823f-5fcf9895f774" />


	
   CostOfGoods = UnitCost × Quantity.	

   
<img width="939" height="110" alt="image" src="https://github.com/user-attachments/assets/f766e53f-4c90-40ec-827a-db9a81f3db98" />

 

  Gross Profit = Gross Revenue − CostOfGoods.
This is direct and as shown below


<img width="445" height="95" alt="image" src="https://github.com/user-attachments/assets/76d7bc09-842b-4c22-8937-c76c7681ac0f" />

 
MarginPct = IF(Gross Revenue=0, 0, Gross Profit / Gross Revenue).
This is direct and as shown below
 
<img width="638" height="82" alt="image" src="https://github.com/user-attachments/assets/763a6f51-330f-476e-8834-dca5be72e169" />


**Question 3**
**3) Create standardized dimensions:
   Month (MMM-YYYY) from OrderDate.**
With this I used the Text() Command which converts a date into a text string in the format you specify which in my case is MMM-YYYY. This is as shown below

 
	<img width="372" height="88" alt="image" src="https://github.com/user-attachments/assets/020229d9-426c-4094-b064-38f070598cfe" />

   
   
   • Quarter (e.g., Q1-2024).
With this, we apply the Roundup formula
We divide by 3 because each quarter has 3 months
This is as shown below

<img width="757" height="82" alt="image" src="https://github.com/user-attachments/assets/3039c3d9-02c3-469c-9973-157a101bae00" />

 
This returns the quarter and the year.
  Region hierarchy: Region → Country → City.
Select the three columns, go to insert, insert pivot table, drag the fields into row in order. Start with region, then country then city. The result is as shown below
 

<img width="273" height="370" alt="image" src="https://github.com/user-attachments/assets/44af8c52-d6d5-4a1d-93ce-e3d111a1eb8b" />



**ProductCategory and a derived 'PriceBand' (e.g., Low/Medium/High using quantiles).**
Because the categories are 3, divide 100/3. Which results in 33.3%, 66.6% and 99.9%
Create a new column , and then apply the following formula while referencing the absolute unit price column. The result is as shown



 <img width="354" height="244" alt="image" src="https://github.com/user-attachments/assets/31ee5388-4896-4261-900b-83582544a9b0" />



Now the next is grouping the Prices as either low , high or medium with reference to the bands as shown below


<img width="554" height="266" alt="image" src="https://github.com/user-attachments/assets/4b104be1-7202-4a7d-a6a7-ca3c8fc40209" />

 
**Part B — Analysis Tasks (show workings with PivotTables / formulas):**					
**4) Build a cohort of first-time sales by Country and Month:	
   • Identify the first month each Country appears and calculate monthly revenue tracked from that start (cohort analysis).
Question 5**

To identify the first month, apply the minifs formula between the order date and the country. This is as shown below


<img width="782" height="100" alt="image" src="https://github.com/user-attachments/assets/43d0133d-7b86-40fe-ac1b-f2027e052e0c" />

.After finding the first month, find the index of every month and convert the column to number. This is as shown



<img width="217" height="101" alt="image" src="https://github.com/user-attachments/assets/a2b9eee5-ecde-48d6-8269-a584878ff052" />

.Proceed to create a pivot table as shown below


<img width="953" height="275" alt="image" src="https://github.com/user-attachments/assets/6af08a5c-f36a-42f2-9b21-ad9ac90f6409" />

**5) ABC analysis by SKU within each ProductCategory using GrossRevenue:
   • Classify SKUs into A (top 80%), B (next 15%), C (last 5%) of revenue per category.**
.First classify the  SKUs into Classes using Percentage INC formula as shown below


<img width="360" height="145" alt="image" src="https://github.com/user-attachments/assets/f389aa6c-aa4e-4ea2-b5ce-e207d0a6ccb1" />

 
.Then create a new column and label it SKU class and use the IF formula with reference to the gross revenue


<img width="473" height="298" alt="image" src="https://github.com/user-attachments/assets/08909f27-8929-4651-8170-b21dee28f650" />


 

6) Salesperson productivity:
   • Compute Revenue/Order, Orders/Month, and GrossProfit/Order by Salesperson; highlight the top and bottom 3.

**7) Channel mix & cannibalization:
   • Compare revenue shares by Channel across Regions; identify where online cannibalizes retail (justify with data).**
.First create a pivot table as show below

<img width="950" height="268" alt="image" src="https://github.com/user-attachments/assets/f274d899-a592-4f9e-8ca7-ea4ea0e81206" />

.with the results being the total revenue per Channel per Region.
.But we want the percentage of total revenue by region.
.Right-click on any value in the Pivot → Show Values As → % of Row Total. This is as shown

<img width="536" height="141" alt="image" src="https://github.com/user-attachments/assets/23102195-f0de-4f51-b642-a02bc9634974" />


we then proceed to identifying cannibalization which  happens when Online revenue increases at the expense of Retail, instead of growing total revenue. This is by filtering the channels and only remaining with online and retail as shown below.
<img width="713" height="266" alt="image" src="https://github.com/user-attachments/assets/c86e590b-0ed0-4d03-9a2f-121ae937ad83" />

we see that Online does well in America>Europe >Asia.

**8) Service level proxy:
   • Using LeadTimeDays, determine % of orders meeting a 7-day target by Country and Category.**

.Insert a new column and name it service level.
.check the orders that meet the 7 day target and those that don't.
This is as shown below.where 1 stands for those that meet and 0 for those that don't

<img width="343" height="146" alt="image" src="https://github.com/user-attachments/assets/ef600e7d-f585-45d6-87d7-6ac04366e6cc" />

Insert a pivot table as shown and a filter showing those that meet. Convert to %


<img width="268" height="267" alt="image" src="https://github.com/user-attachments/assets/2bc747c7-3a27-4605-b7cf-f469e8337c17" />

**9) Price compliance:
   • Share of orders with DiscountPct > 20% by Region and Salesperson; list outliers.**
   .Insert a new column and label it price compliance
   .Give it a condition that if the dicount percentage column is greater or equal to 20%, it should return 1, if not, it should return 0 as shown. 

   <img width="552" height="151" alt="image" src="https://github.com/user-attachments/assets/f13a155e-f1c0-4839-989c-349389a2c516" />

   .we treat 1 as outliers because they are greater than 20
   .insert the pivot table and the results show that we have a total of 90 outliers.

   <img width="929" height="194" alt="image" src="https://github.com/user-attachments/assets/947466da-49c5-47ed-9948-d34f830ec567" />


**Part C — Scenario Modeling (What-If):
10) Build a What-If control panel (slider/cell inputs):
   • Global Discount Cap (e.g., 0%–25%).
   • UnitCost inflation factor (e.g., 0%–15%).
   • Quantity uplift (e.g., 0%–20%).
   Recalculate Revenue and Profit metrics under these scenarios and compare to the baseline.**


**Part D — Interactive Dashboard:
11) Create a single-page dashboard with:
   • Slicers for Region, Country, Channel, ProductCategory, Month, and Salesperson.
   • KPIs: Total Revenue, Gross Profit, Margin %, Avg Order Value, On-Time % (LeadTimeDays ≤ 7).
   • Visuals:
       – Revenue by Month (line chart).
       – Profit by Region and Channel (stacked column).
       – Top 10 SKUs by Revenue (bar).
       – Discount Outliers (box/whisker or scatter) — if Excel version permits, else alternative view.
   • Dynamic titles reflecting applied filters.**
   .First Convert data to an Excel Table by Clicking anywhere inside the dataset> Press Ctrl + T> Check “My table has headers”> Click OK. This will ensure that the slicers and formulas work smoothly
Work on a KPI at a time.
For instance the Revenue per month KPI,
Insert a pivot table with revenue and month.
Insert a line chart and include a trend trend.
Format it to your liking 
Copy the chart and paste it on a new worksheet that you will have labelled Dasboard.
Do this for all the KPIs




