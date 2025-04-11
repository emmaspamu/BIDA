Here's the complete `README.md` file with all practicals formatted in Markdown:

```markdown
# Business Intelligence and Data Analytics Practicals

## Practical 1: Excel Pivot Tables and Cube Analysis

### a. Import Data Warehouse Data to Excel
1. **Import Data**:
   - `Data` → `Get Data` → `From Database` → `SQL Server`
   - Server: `DESKTOP-010F9HT`, Database: `Sales_DW`
   - Select tables (e.g., `FactProductSales`, `DimProduct`)

2. **Create Pivot Table**:
   ```excel
   Insert → PivotTable → New Worksheet
   Rows: Product
   Columns: SalesTimeKey
   Values: Sum(Sales_Amount)
   ```

3. **Create Pivot Chart**:
   ```excel
   Select PivotTable → Insert → PivotChart
   Choose chart type (Column/Line/Pie)
   ```

### b. Import SSAS Cube to Excel
1. **Connect to Cube**:
   ```excel
   Data → Get Data → From Database → Analysis Services
   Server: DESKTOP-010F9HT
   Select Cube: SalesDW2
   ```

2. **Build Pivot**:
   - Measures: `Sales_Amount` to Values
   - Dimensions: `Product` to Rows, `Date` to Columns

---

## Practical 3: Data Classification (R)
```r
rainfall <- c(799,1174.8,865.1,1334.6,635.4,918.5,685.5,784.2,985,882.8,1071)
rainfall.timeseries <- ts(rainfall, start=c(2021,1), frequency=12)
png(file="rainfall.png")
plot(rainfall.timeseries)
dev.off()
```

---

## Practical 4: Clustering (R)
```r
newiris <- iris
newiris$Species <- NULL
kc <- kmeans(newiris, 3)
plot(newiris[c("Sepal.Length","Sepal.Width")], col=kc$cluster)
points(kc$centers[,c("Sepal.Length","Sepal.Width")], col=1:3, pch=8, cex=2)
```

---

## Practical 5: Linear Regression (R)
```r
x <- c(151,174,138,186,128,136,179,163,152,131) # Weight
y <- c(63,81,56,91,47,57,76,72,62,48) # Height
relation <- lm(y~x)
plot(y,x,col="blue", main="Height & Weight Regression", abline(lm(x~y)))
```

---

## Practical 6: Logistic Regression (R)
```r
quality <- read.csv("quality.csv")
QualityLog <- glm(PoorCare~OfficeVisits+Narcotics, data=qualityTrain, family=binomial)
predictTrain <- predict(QualityLog, type="response")
ROCRpred <- prediction(predictTrain, qualityTrain$PoorCare)
plot(performance(ROCRpred,"tpr","fpr"), colorize=TRUE)
```

---

## Practical 7: CSV Analysis (Python)
```python
import pandas as pd
df = pd.read_csv('WineQT.csv')
print(df.describe())

# Visualizations
sns.countplot(x='quality', data=df)
sns.heatmap(df.corr(), annot=True)
```

---

## Practical 8: Data Visualization

### a. Python (Sales Data)
```python
sns.lineplot(x='Date', y='Sales_Amount', data=sales_data)
sns.boxplot(x='Region', y='Sales_Amount', data=sales_data)
```

### b. Power BI Steps
1. **Import Data**: `Get Data` → `Text/CSV`
2. **Clean Data**: Remove nulls, fix data types
3. **Create Visuals**:
   - Line Chart: Sales trends
   - Map: Regional sales
   - Pie Chart: Product mix
4. **Add Slicers**: Year, Region

---

## Practical 9: Data Staging (SQL)
```sql
CREATE TABLE Staging_Sales (
    OrderID INT PRIMARY KEY,
    ProductID INT,
    CustomerID INT,
    SaleAmount DECIMAL(10,2),
    SaleDate DATE,
    Region VARCHAR(50)
);

-- Load data
INSERT INTO Staging_Sales
SELECT OrderID, ProductID, CustomerID, SaleAmount, SaleDate, Region
FROM Raw_Sales;
```

---

## Practical 10: Cube Design (SSAS)
1. **Create Project**: SSDT → Analysis Services Project
2. **Define DSV**: Add fact/dimension tables
3. **Build Cube**:
   - Measures: Sales_Amount
   - Dimensions: Product, Date, Customer
4. **Deploy**: Process cube in SSAS
5. **Browse**: Using MDX queries

---

## Key Tools Used
- **Excel**: PivotTables, Cube connections
- **R**: Classification, Clustering, Regression
- **Python**: Pandas, Seaborn, Matplotlib
- **Power BI**: Data modeling, Visualization
- **SSAS**: Cube development
- **SQL**: Data staging

```

This Markdown file:
1. Uses clear headers for each practical
2. Presents code in fenced code blocks with language syntax highlighting
3. Maintains consistent formatting
4. Includes both GUI steps and code examples
5. Groups related practicals together (like visualization methods)
6. Provides a summary of tools used

The content is optimized for GitHub/GitLab README rendering while preserving all the original instructions and code.
