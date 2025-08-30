# Ecommerce-sales-Dashboard
# 📊 E-commerce Sales Dashboard – Power BI  

## 🚀 Project Overview  
This project presents an **E-commerce Sales Dashboard** created in Power BI.  
The dashboard provides insights into sales performance, customer behavior, product trends, and regional analysis.  

Key business questions answered:  
- What is the overall revenue trend?  
- Who are the top customers and products?  
- Which categories and regions drive the most sales?  
- How do sales vary across months and years?  

---

## 📂 Dataset  
Dataset: **`ecommerce_data.csv`**  

### Columns:  
- **OrderID** – Unique identifier for each order  
- **OrderDate** – Date of the transaction  
- **CustomerID** – Unique customer identifier  
- **CustomerName** – Customer’s name  
- **Region** – Customer region  
- **ProductID** – Unique product identifier  
- **ProductName** – Name of the product  
- **Category** – Product category  
- **Quantity** – Units sold  
- **UnitPrice** – Price per unit  
- **TotalPrice** – Revenue generated (Quantity × UnitPrice)  

---

## 🏗 Data Model  
Structured into **Fact and Dimension tables** in Power BI:  

- **Fact Table:** `Fact_Sales` (transactions)  
- **Dimensions:**  
  - `Dim_Customer` – Customer details  
  - `Dim_Product` – Product details (ProductName, Category)  
  - `Dim_Date` – Extracted from OrderDate  
  - `Dim_Region` – Regional information  

---

## 📈 Dashboard Pages  
1. **Sales Overview** – Revenue trends, KPIs, YoY growth  
2. **Customer Analysis** – Top customers, repeat orders, CLV  
3. **Product Analysis** – Best-selling products, categories  
4. **Regional Analysis** – Sales by region/country (map)  
5. **Time Analysis** – Monthly/Quarterly/Yearly performance  

---

## 🔧 DAX Measures  
Examples of calculated measures:  

```DAX
Total Sales = SUM(Fact_Sales[TotalPrice])  

Total Quantity = SUM(Fact_Sales[Quantity])  

Average Order Value = DIVIDE([Total Sales], DISTINCTCOUNT(Fact_Sales[OrderID]))  

YoY Sales Growth = 
DIVIDE(
    [Total Sales] - CALCULATE([Total Sales], DATEADD(Dim_Date[Date], -1, YEAR)),
    CALCULATE([Total Sales], DATEADD(Dim_Date[Date], -1, YEAR))
)
