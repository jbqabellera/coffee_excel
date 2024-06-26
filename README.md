# Coffee Sales Dashboard

The project's goal is to identify potential opportunities that the coffee business can tap into and issues that needs to be resolved. This end-to-end project uses Microsoft Excel from data cleaning to data visualization.

## Task 

The client wants to know:
1. What is our best-selling coffee product?
2. Which region/s show/s a potential opportunity where we can expand to? 
3. Who are our loyal customers? What are the characteristics of people who don't have a loyalty card? We need to develop a different strategy for them.
4. I want to reward our Top 5 customers. Create a list of their names.

## Data

The data includes three sheets:
- Orders - List of coffee orders, when it was bought, who bought it, what they bought, and how many
  - OrderID, Order Date, CustomerID, ProductID, and quantiy
- Customers - Database of customer information
- Products - Information of every product that we offer
  - Coffee Type, Roast Type, Size, Unit Price, Price per 100g, Profit

[Download Link](https://github.com/jbqabellera/Coffee-Sales-Excel-Project/blob/a7f2cf9734e18270d71041b7568d404912d9509b/Coffee%20Sales%20Dashboard.xlsx)
 
## Data Cleaning

Step 1. Duplicate and create a working sheet. This is where the magic will happen.
Step 2. Populate the following columns using XLOOKUP and INDEX(MATCH)

  Customer Name
  ```
  =XLOOKUP(C2,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)
  ```

  Email
  ```
  =IF(XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0, "",XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))
  ```

Country
```
=XLOOKUP(C2,customers!$A$2:$A$1001,customers!$G$2:$G$1001,,0)
```

Step 3. Use INDEX and MATCH to populate the other columns easily. Drag right and down to auto-fill the cells.

Coffee Type
```
=INDEX(products!$A$1:$G$49,MATCH($D2,products!$A$1:$A$49,0),MATCH('Working Sheet'!I$1,products!$A$1:$G$1,0))
```

![Index Match](https://github.com/jbqabellera/coffee_excel/blob/d917f1f9a544d6a34eab0e2427e8813d94f9801b/Coffee%20GIF.gif)

Sales
```
Multiply the quantity bought ("Quantity") with the Unit Price.
```
Step 3. Create a new column for Coffee Type Name and Roast Type Name to make it easy to understand.

Coffee Type Name
```
=IF(I2="Rob", "Robusta",IF(I2="Exc","Excelsa",IF(I2="Ara", "Arabica",IF(I2="Lib","Liberica",""))))
```

Roast Type Name
```
=IF(J2="M", "Medium",IF(J2="L", "Light",IF(J2="D", "Dark")))
```

Step 4. Add a new column for "Loyalty Card."

```
=XLOOKUP([@[Customer ID]],customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)
```

Step 5. Double-check the data. Use Filters.

Step 6. Edit the formatting.


## Data Analysis


Create a pivot table for each of the following:
- Total Sales over Time
- Total Sales by Country
- Top 5 Customers

## Coffee Sales Dashboard

[View the dashboard here](https://1drv.ms/x/c/492367e7aa5d37f3/IQPVE3CJsANqQJb3XG5i-BE6Ae_SZSk9Cbub5wTtysH2WIA)
