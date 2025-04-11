Practical 1

Perform the analysis for the following:
a. Import the data warehouse data in Microsoft Excel and create the Pivot table and Pivot
Chart.

Step 1: Open Excel → Go to Data tab → Click Get Data → From Database → From SQL Server Database.

Step 2: Enter:

Server Name: DESKTOP-010F9HT (or your server name)

Database: Sales_DW

Step 3: Select tables (e.g., FactProductSales, DimProduct) → Click Load.

2. Create a Pivot Table
Step 1: Select the imported data → Go to Insert → PivotTable → Choose New Worksheet.

Step 2: Drag fields into areas:

Rows: Product (from DimProduct)

Columns: SalesTimeKey (or any date/time field)

Values: Sales_Amount (sum/average)

Step 3: Customize calculations (e.g., Sum, Count, Average) in Value Field Settings.

3. Create a Pivot Chart
Step 1: Click inside the PivotTable → Go to Insert → PivotChart.

Step 2: Choose chart type (e.g., Column, Line, Pie).

Step 3: Format chart (titles, colors, legends) using Chart Tools.

4. Refresh Data (If Updated in SQL Server)
Right-click PivotTable → Refresh (or go to Data → Refresh All).

Key Shortcuts & Tips
✅ Quick PivotTable: Select data → Press Alt + N + V (Excel shortcut).
✅ Slicers for Filtering: Insert → Slicer (for interactive filtering).
✅ Group Dates: Right-click dates in PivotTable → Group → By Months/Quarters.

Final Output:

A summarized PivotTable (e.g., sales by product).

A visual PivotChart (e.g., trend analysis).



b. Import the cube in Microsoft Excel and create the Pivot table and Pivot Chart to
perform data analysis.

1. Connect Excel to SSAS Cube
Step 1: Open Excel → Data tab → Get Data → From Database → From Analysis Services.

Step 2: Enter:

Server Name: DESKTOP-010F9HT (or your SSAS server)

Credentials: Use Windows Authentication (default) or SQL login.

Step 3: Select the Cube (e.g., SalesDW2) → Click Next → Finish.

2. Choose Data View (PivotTable Report)
Select PivotTable Report → Place in New Worksheet or existing sheet → Click OK.

3. Build PivotTable from Cube
Step 1: In the PivotTable Fields pane:

Measures: Drag (e.g., Sales_Amount) to Values.

Dimensions: Drag (e.g., Product Name, Date) to Rows/Columns.

Step 2: Use Hierarchies (e.g., Year → Quarter → Month for dates).

4. Create PivotChart
Click inside PivotTable → Insert → PivotChart → Choose type (e.g., Column, Line).

Customize with Chart Tools (titles, colors, filters).

5. Analyze with Cube Functions
Drill Down: Click +/- icons to expand/collapse hierarchies.

Slicers/Timelines: Insert from PivotTable Analyze tab for interactive filtering.

Key Features of Cube-Based PivotTables
✅ MDX Measures: Use cube calculations (e.g., [Measures].[Profit Margin]).
✅ Hierarchy Navigation: Drill into dimensions (e.g., Country → City → Store).
✅ Real-Time Refresh: Right-click → Refresh to update from SSAS.

Final Output:

Dynamic PivotTable with OLAP cube data.

Interactive PivotChart for visual analysis (e.g., sales trends by product/region).





Practical 2

Apply the what – if Analysis for data visualization. Design and generate necessary reports
based on the data warehouse data. Use Excel.(on hold)


Practical 3

Perform the data classification using classification algorithm using R/Python.

rainfall <- c(799,1174.8,865.1,1334.6,635.4,918.5,685.5,784.2,985,882.8,1071)
rainfall.timeseries <- ts(rainfall,start = c(2021,1),frequency = 12)
print(rainfall.timeseries)
png(file = "rainfall.png")
 plot(rainfall.timeseries)
dev.off()
plot(rainfall.timeseries)








Practical 4

Perform the data clustering using a clustering algorithm using R/Python.

newiris <- iris
newiris$Species <- NULL
(kc <- kmeans(newiris,3))
table(iris$Species,kc$cluster)
plot(newiris[c("Sepal.Length","Sepal.Width")],col=kc$cluster)
points(kc$centers[,c("Sepal.Length","Sepal.Width")],col=1:3,pch=8,cex=2)

Practical 5

Perform the Linear regression on the given data warehouse data using R/Python.

x <- c(151,174,138,186,128,136,179,163,152,131)
y <- c(63,81,56,91,47,57,76,72,62,48)
relation <- lm(y~x)
png(file = "linearregression.png")
plot(y,x,col = "blue",main = "Height & Weight Regression",abline(lm(x~y)),cex=1.3, pch=16,
xlab="Weight in Kg", ylab="Height in cm")
dev.off()






















Practical 6

Perform the logistic regression on the given data warehouse data using R/Python.

Code:
quality<-read.csv("C:/quality.csv")
str(quality)
table(quality$PoorCare)
install.packages("caTools")
library(caTools)
qualityTrain = subset(quality,split==TRUE)
qualityTest =subset(quality,split==FALSE)
nrow(qualityTrain)
nrow(qualityTest)
QualityLog=glm(PoorCare~OfficeVisits + Narcotics,data=qualityTrain,family = binomial) >
summary(QualityLog)
predictTrain=predict(QualityLog,type = "response")
summary(predictTrain)
tapply(predictTrain, qualityTrain$PoorCare, mean)
table(qualityTrain$PoorCare,predictTrain>0.5)
table(qualityTrain$PoorCare,predictTrain>0.7)
table(qualityTrain$PoorCare,predictTrain<0.2)
install.packages("ROCR")
library(ROCR)
ROCRpred=prediction(predictTrain,qualityTrain$PoorCare)
ROCRperf=performance(ROCRpred,"tpr","fpr")
plot(ROCRperf)
plot(ROCRperf,colorize=TRUE)
plot(ROCRperf,colorize=TRUE,print.cutoffs.at=seq(0,1,by=0.1),text.adj=c(-0.2,10.7))














Practical 7

Write a Python program to read data from a CSV file, perform simple data analysis, and
generate basic insights. (Use Pandas is a Python library).

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
file_path = 'C:\WineQT.csv'
df = pd.read_csv(file_path)
summary_stats = df.describe()
print("Summary Statistics")
print(summary_stats)
correlation_matrix = df.corr()
print("\nCorrelation Matrix: ")
print(correlation_matrix)
quality_distribution = df['quality'].value_counts().sort_index()
print("\nQuality Distribution: ")
print(quality_distribution)
quality_correlation = correlation_matrix['quality'].sort_values(ascending=False)
print("\nQuality Correlation: ")
print(quality_correlation)
quality_correlation = correlation_matrix ['quality'].sort_values (ascending=False)
print("\nCorrelation with Quality:")
print (quality_correlation)
plt.figure (figsize=(10, 6))
plt.subplot (2, 2, 1)
sns.countplot (x='quality', data=df, palette='viridis')
plt.title('Quality Distribution')
plt.subplot(2, 2, 2)
sns.heatmap (correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f', linewidths=0.5)
plt.title('Correlation Matrix Heatmap')
plt.subplot (2, 2, 3)
sns.boxplot (x='quality', y='alcohol', data=df, palette='viridis')
plt.title('Alcohol vs Quality')
plt.subplot (2, 2, 4)
sns.boxplot (x='quality', y='density', data=df, palette='viridis')
plt.title('Density vs Quality')
plt.tight_layout ()
plt.show()





Practical 8
(a.Perform data visualization)


a. Perform data visualization using Python on any sales data.

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

def load_data(csv_file):
try:
data = pd.read_csv('C:\sales_data.csv', encoding="ISO-8859-1")
print("Data loaded successfully!")
print(data)
return data
except Exception as e:
print(f"Error loading data: {e}")
return None
def data_summary(data):
print("\nFirst 5 rows of the data:")
print(data.head()) # Displays the first 5 rows
print("\nData Structure:")
print(data.info()) # Get information on the DataFrame such as column types and non-null
counts
print("\nStatistical summary of numeric columns:")
print(data.describe()) # Gives summary statistics for numeric columns
def plot_sales_over_time(data):
data['Date'] = pd.to_datetime(data['Date'])
sales_by_date = data.groupby('Date')['Sales_Amount'].sum().reset_index()
plt.figure(figsize=(10, 6))
sns.lineplot(x='Date', y='Sales_Amount', data=sales_by_date, marker='o')
plt.title('Total Sales Over Time')
plt.xlabel('Date')
plt.ylabel('Total Sales ($)')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
def plot_sales_by_region(data):
plt.figure(figsize=(10, 6))
sns.boxplot(x='Region', y='Sales_Amount', data=data)
plt.title('Sales Distribution by Region')
plt.xlabel('Region')
plt.ylabel('Sales Amount ($)')
plt.tight_layout()
plt.show()
def plot_sales_vs_quantity(data):
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Quantity_Sold', y='Sales_Amount', data=data, hue='Product',
palette='viridis')
plt.title('Sales Amount vs Quantity Sold')
plt.xlabel('Quantity Sold')
plt.ylabel('Sales Amount ($)')
plt.tight_layout()
plt.show()
def plot_top_products_by_sales(data):
top_products = data.groupby('Product')['Sales_Amount'].sum().reset_index()
top_products = top_products.sort_values('Sales_Amount', ascending=False).head(10)
plt.figure(figsize=(10, 6))
sns.barplot(x='Sales_Amount', y='Product', data=top_products, palette='Blues_d')
plt.title('Top 10 Products by Sales Amount')
plt.xlabel('Sales Amount ($)')
plt.ylabel('Product')
plt.tight_layout()
plt.show()
def main():
csv_file = 'sales_data.csv' # Replace with your actual CSV file path
data = load_data(csv_file)
if data is not None:
data_summary(data)
plot_sales_over_time(data)
plot_sales_by_region(data)
plot_sales_vs_quantity(data)
plot_top_products_by_sales(data)
if __name__ == "__main__":
main()











b. Perform data visualization using PowerBI on any sales data.


Step-by-Step Guide for Analyzing Sales Data in Power BI
Step 1: Install and Open Power BI
Download & Install Power BI Desktop
If you haven't installed it yet, download it from Power BI Download.
Install and open Power BI Desktop.
Step 2: Load the Sales Data
Open Power BI Desktop.
Click on "Home" > "Get Data" > "Text/CSV".
Browse and select the sales_data_sample.csv file you uploaded.
Click Open, then click Load (you can check the data preview before loading).
 
Step 3: Transform Data in Power Query Editor
Before building reports, let's clean and format the data:
Click on "Transform Data" to open Power Query Editor.
Review columns and check for missing values:
ADDRESSLINE2, STATE, TERRITORY have missing values, so you can remove them or fill in with "Unknown".
To remove a column: Right-click on the column header > Click Remove.
Convert ORDERDATE column to Date format:
Select ORDERDATE column.
In the top menu, click Transform > Data Type > Date.
Ensure SALES, PRICEEACH are in Decimal Number format.
Click "Close & Apply".
Step 4: Create Basic Visualizations
1. Sales Performance Overview
●       Total Sales & Orders
1.      Go to Report View (bottom left panel).
2.      Drag SALES to a Card Visual (this shows total revenue).
3.      Drag ORDERNUMBER to another Card Visual (shows total orders).
●   	Sales Trend Over Time
1.      Drag ORDERDATE to X-Axis in a Line Chart.
2.      Drag SALES to Y-Axis (shows sales over time).
2. Sales by Product Line
Insert a Bar Chart.
Drag PRODUCTLINE to X-Axis.
Drag SALES to Y-Axis (shows revenue per product category).
3. Sales by Country
Insert a Map Visual (Globe icon).
Drag COUNTRY to Location field.
Drag SALES to Values field (shows sales by country).
4. Order Status Breakdown
Insert a Pie Chart.
Drag STATUS to Legend.
Drag ORDERNUMBER to Values (shows percentage of orders in each status).
 
Step 5: Add Filters and Slicers
●       Click on "Slicer" and add YEAR_ID to filter by year.
●       Add CUSTOMERNAME to filter by customer.
●       Add DEALSIZE to filter by deal size.
 
Step 6: Save & Publish Report
Click File > Save As and save the Power BI report.
Click Publish to share on Power BI Service (if needed).
 

Steps to Perform Data Visualization in Power BI
Import the Data:
Open Power BI Desktop.
Click on "Get Data" > "Excel" and select the uploaded file.
Load the relevant sheets into Power BI.
Data Preparation:
Check for missing values or inconsistent data.
Apply transformations (if needed) using Power Query Editor.
Create Key Visuals:
Sales Trends: Use a Line Chart to show sales performance over time.
Regional Sales Analysis: Use a Map Visual to display sales by region.
Top Products Sold: Use a Bar Chart to highlight best-selling products.
Revenue Breakdown: Use a Pie Chart or Treemap to show sales by category.
Customer Segmentation: Use Clustered Bar Charts to group customers based on sales.
Add Filters and Slicers:
Include Date Slicers to filter data by month, quarter, or year.
Use Dropdown Filters for region, product category, or customer segment.
Enhance with DAX Measures:
Create calculated measures such as:
o   Total Sales = SUM(Sales[Revenue])
o   Sales Growth = ( [Total Sales] - PREVIOUSMONTH([Total Sales]) ) / PREVIOUSMONTH([Total Sales])
Use KPIs for profit margin and sales targets.
Publish and Share:
Save the report and publish it to Power BI Service.
Share with stakeholders via dashboards.














Practical 9

Create the Data staging area for the selected database using SQL.

1. Load Data into Power BI
Open Power BI Desktop → Home → Get Data → Excel/CSV/SQL Server.

Select your source file (e.g., sales_data_sample.xlsx) → Transform Data (to clean before loading).

2. Clean & Transform Data in Power Query Editor
Remove Unnecessary Columns: Right-click → Remove Columns.

Handle Missing Values:

Replace nulls: Transform → Replace Values (e.g., "Unknown" for text, 0 for numbers).

Remove blank rows: Home → Remove Rows → Remove Blank Rows.

Standardize Text:

Trim spaces: Transform → Format → Trim.

Proper case: Use Text.Proper([Column]) in Custom Column.

Fix Data Types: Ensure dates, numbers, and text are correctly assigned (e.g., Order_Date as Date).

Duplicate Your Source Table (to make a staging table)
In the left panel (Queries list), right-click your source table

Click Duplicate

3. Create Staging Tables
Fact Table (e.g., FactSales):

Contains transactional data: Order_ID, Product_ID, Quantity, Sales_Amount, Date.

Dimension Tables:

DimProducts: Product_ID, Product_Name, Category.

DimCustomers: Customer_ID, Customer_Name, Region.

DimDates: Create a date table with Date, Year, Quarter, Month.

4. Build a Date Table (If Missing)

let
    StartDate = #date(2020, 1, 1),
    EndDate = #date(2030, 12, 31),
    DateList = List.Dates(StartDate, Duration.Days(EndDate - StartDate) + 1, #duration(1, 0, 0, 0)),
    DateTable = Table.FromList(DateList, Splitter.SplitByNothing(), {"Date"}),
    #"Added Columns" = Table.AddColumn(DateTable, "Year", each Date.Year([Date])),
    #"Added Month" = Table.AddColumn(#"Added Columns", "Month", each Date.Month([Date]))
in
    #"Added Month"

5. Set Relationships in Data Model
Go to Model View → Drag to link:

FactSales[Customer_ID] → DimCustomers[Customer_ID]

FactSales[Product_ID] → DimProducts[Product_ID]

FactSales[Date] → DimDates[Date]

6. Validate Data Quality
DAX Measures:

Total Sales = SUM(FactSales[Sales_Amount])

Missing Customers = COUNTROWS(FILTER(FactSales, ISBLANK(FactSales[Customer_ID])))

7. Save & Publish
File → Save (.pbix).

Publish to Power BI Service (optional for sharing).

Key Benefits of Data Staging
✅ Consistency: Clean, standardized data for accurate reporting.
✅ Performance: Optimized tables improve query speed.
✅ Scalability: Easily add new data sources or dimensions.

Output: A structured dataset ready for dashboards, reports, or further analysis in Power BI or SQL.





Practical 10

Create the cube with suitable dimension and fact tables based on ROLAP, MOLAP and
HOLAP model.

1. Launch SQL Server Data Tools (SSDT) & Create Project
Open SQL Server Data Tools (SSDT) → File → New → Project.

Select Business Intelligence → Analysis Services Project.

Name the project (e.g., Sales_Analysis_Cube) → Click OK.

2. Connect to Data Source (SQL Server Database)
In Solution Explorer, right-click Data Sources → New Data Source.

Click New → Set up a connection to your database:

Server Name: DESKTOP-010F9HT (or your SQL Server instance).

Database: Sales_DW.

Test connection → Click OK.

Choose authentication (Windows or SQL) → Finish.

3. Create Data Source View (DSV)
Right-click Data Source Views → New Data Source View.

Select the Sales_DW data source → Click Next.

Add tables:

Fact Table: FactProductSales.

Dimension Tables: DimProduct, DimDate, DimCustomer, etc.

Click Finish to generate the DSV.

4. Build the Cube Using Cube Wizard
Right-click Cubes → New Cube → Use existing tables.

Select the Fact Table (FactProductSales) → Click Next.

Choose Measures (e.g., Sales_Amount, Quantity) → Click Next.

Select Related Dimensions (e.g., DimProduct, DimDate) → Click Next.

Name the cube (e.g., Sales_Cube) → Click Finish.

5. Define Dimensions & Hierarchies
Double-click dimensions (e.g., DimDate) in Solution Explorer.

Drag attributes (e.g., Year, Quarter, Month) to Hierarchies pane.

Set attribute relationships (e.g., Year → Quarter → Month).

6. Deploy & Process the Cube
Right-click the project → Properties → Set Deployment Server (SSAS instance name).

Right-click project → Deploy (sends cube to SSAS server).

After deployment, right-click cube → Process → Full Process (loads data).

7. Verify in SQL Server Management Studio (SSMS)
Open SSMS → Connect to Analysis Services.

Navigate to Databases → Your cube (Sales_Cube) should appear.

Browse data by right-clicking cube → Browse.

Key Outputs
✅ Cube Structure: Measures (e.g., Sales, Profit) + Dimensions (Product, Time).
✅ Hierarchies: Drill-down paths (e.g., Year → Quarter → Month).
✅ MDX Support: Enables complex queries (e.g., YoY growth calculations).

Tips
🔹 Optimize Performance: Partition large fact tables.
🔹 Use Aggregations: Pre-calculate summaries for faster queries.
🔹 Security: Configure roles in SSAS to restrict data access.
