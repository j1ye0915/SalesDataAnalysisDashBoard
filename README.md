
# Sales Data Analytics Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/705200dd-ff96-4226-8da0-4a0ff009d0a3/8a5cccb736d01640d4be?experience=power-bi

## Objective
The objective was to analyze and visualize sales performance data to provide actionable insights for decision-makers. The focus was on understanding key performance indicators (KPIs), including sales income, gross profit, gross profit margin, and sales quantity, while offering granular insights by channel, city, product, and time trends.


## Steps followed

1.	Data Preparation:
-   Loaded data into Power BI Desktop, dataset is a csv file.

-	Cleaned and transformed the dataset using Power Query in Power BI.

-	Changed data types of Sales Price and Sales Unit Cost to Fixed Decimal Number for precision.

-	Created additional calculated columns in Sales_Data :

        SalesIncome = SalesPrice * OrderQuantity

        SalesCost = SalesUnitCost * OrderQuantity

Snap of new created columns, 

![image](https://github.com/user-attachments/assets/34b114dd-8f9c-4c95-bdde-3b1ae90006ca)

2.	Data Modeling:
-	Established relationships between data tables to ensure accurate and efficient reporting.

Snap of model relationships,

![image](https://github.com/user-attachments/assets/61eaafaa-cb52-429e-8987-4ea60df7239a)


3.	Date Table Creation:
-	Built a date table to enhance time-based filtering and calculations

        dDate = ADDCOLUMNS (
        CALENDARAUTO (),
        "Year", YEAR ( [Date] ),
        "Quartername", "Q" & QUARTER ( [Date] ),
        "Month", FORMAT ( [Date], "mmmm" ),
        "Month Number", MONTH ( [Date] ),
        "Quarternumber", ROUNDUP(MONTH ( [Date] )/3,0),
        "Yearquartersort", YEAR ( [Date] )*10+ROUNDUP (MONTH ([Date])/3,0),
        "Year-Quarter", YEAR ( [Date] )&"-"&"Q" & QUARTER ( [Date] ),
        "Year-Month",YEAR ( [Date] ) & "-"& FORMAT ( [Date], "mmm" ),
        "Yearmonthsort", YEAR ( [Date] )*100+MONTH ( [Date] )
        )

Snap of dDate table, 

![image](https://github.com/user-attachments/assets/59878f80-8b6d-4e84-be63-27fcb8093107)       

-	Enabled time intelligence functions and optimized DAX performance by referencing the date table for calculations such as daily averages.

4.	KPI Calculation:
-	Identified dashboard audience needs and defined goals.

-	Calculated KPIs using DAX, including sales quantity, sales income, sales cost, gross profit, and gross profit margin, and organized them into a DAX table.
        
        SalesIncome = SUM('Sales_Data'[SalesIncome])
        GrossProfit = [SalesIncome]-[SalesCost]
        GrossProfitMargin = [GrossProfit]/[SalesIncome]
        SalesQuantity = SUM('Sales_Data'[OrderQuantity])
        

5.	Dashboard Design and Development:
-	Incorporated slicers for Year, Product, City, and Sales Channel to enable dynamic filtering.

-	Added visualizations, including cards for key metrics, donut charts for sales distribution by channel, city, and product, and bar charts for product and monthly sales performance.

-	Designed a product analysis bar chart to highlight year-over-year sales growth with color-coded bars.

-	Built a line chart to display a three-year sales income trend.

-	Implemented a reset button for seamless filter management.

Snapshot of the dashboard,

![image](https://github.com/user-attachments/assets/bee0d793-71be-4ad4-a325-59a2a4ec0ec2)
