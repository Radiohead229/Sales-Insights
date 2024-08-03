# Sales-Insights-of-a-Company
## A Data Analysis project on Sales insights of a Brick and Mortar Company using MySQL and Power BI.
This Data Analysis Project aims to provide the insights into the sales performance of a **Brick and Mortar Company** over the past few years.
By analysing various aspects of the sales data, we seek to **identify trends** and gain a **deeper understanding of the company's performance**.

## Data Sources
The **primary dataset** used for this analysis is the .**sql file** named db_dump.sql in the dataset folder containing all the details as rows ansd coloumns.

## Tools used 
- MySQL [_Analysing the data_]
- Microsoft PowerBI [_Cleaning the data (ETL) and making reports and charts_]


### Data Analysis syntax(s) in MySQL
Show all customer records

`SELECT * FROM customers;`

Show total number of customers

`SELECT count(*) FROM customers;`

Show transactions for Chennai market (market code for chennai is Mark001)

`SELECT * FROM transactions where market_code='Mark001';`

Show distrinct product codes that were sold in chennai

`SELECT distinct product_code FROM transactions where market_code='Mark001';`

Show transactions where currency is US dollars

`SELECT * from transactions where currency="USD"`

Show transactions in 2020 join by date table

`SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

Show total revenue in year 2020

`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`

Show total revenue in year 2020, January Month,

`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

Show total revenue in year 2020 in Chennai

`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";`

### Data Analysis syntax(s) in Power BI
Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`
