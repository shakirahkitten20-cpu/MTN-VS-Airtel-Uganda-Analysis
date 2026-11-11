# MTN Uganda vs Airtel Uganda - Financial Analysis 2022-2025

## Source - My Method
I did NOT copy from news. I downloaded the full Annual Reports (about 200 pages each) from MTN Uganda and Airtel Uganda official websites, released at end of financial year.
I extracted only the key elements I needed: Total Revenue, Total Expenses, Profit After Tax, Voice, Data, Fintech, Subscribers.

Raw Data -> Clean Spreadsheet -> SQL Server -> Tableau

## 1. Raw vs Clean Data
Raw: Mixed formats - "UGX 3.6tn", "Shs 3,600bn", "3,600,000,000,000", spaces, mixed case MTN / mtn / Mtn.
Clean: File `2022-2025 mtn vs airtel clean`
All values in same unit, no text, no spaces. Columns: Year, Company, TotalRevenue, TotalRevenue_YoY, TotalExpenses, ProfitAfterTax, Subscribers.

## 2. My 6 SQL Syntaxes - Database: TelecomUgandaDB, Table: TelecomPerformance

SYNTAX 1 - Total 4-Year Revenue
SELECT Company, SUM(TotalRevenue) AS Total_4Year_Revenue
FROM TelecomPerformance GROUP BY Company ORDER BY Total_4Year_Revenue DESC;
Result: MTN 11,752,000,000,000 | Airtel 7,807,000,000,000

SYNTAX 2 - Total 4-Year Profit
SELECT Company, SUM(ProfitAfterTax) AS Total_4Year_Profit
FROM TelecomPerformance GROUP BY Company ORDER BY Total_4Year_Profit DESC;
Result: MTN 2,214,000,000,000 | Airtel 1,382,000,000,000

SYNTAX 3 - Year by Year Detail
SELECT Year, Company, TotalRevenue, ProfitAfterTax
FROM TelecomPerformance ORDER BY Year DESC, TotalRevenue DESC;

SYNTAX 4 - Revenue Growth %
SELECT Company, Year, TotalRevenue_YoY AS Revenue_Growth_Percent
FROM TelecomPerformance ORDER BY TotalRevenue_YoY DESC;

SYNTAX 5 - Latest Subscribers 2025
SELECT Company, SUM(TotalSubscribers) AS Latest_Subscribers_2025
FROM TelecomPerformance GROUP BY Company ORDER BY Latest_Subscribers_2025 DESC;
Result: MTN 24,200,000 | Airtel 15,500,000

SYNTAX 6 - Full Summary
SELECT Company, SUM(TotalRevenue) AS Total_Revenue, SUM(ProfitAfterTax) AS Total_Profit, SUM(TotalSubscribers) AS Total_Subscribers
FROM TelecomPerformance GROUP BY Company ORDER BY Total_Revenue DESC;

## My Tableau Visual - ONE Visual
File: 2022-2025 mtn vs airtel visual
Title: Total Revenue Trend MTN VS Airtel 2022-2025
One line chart, 2 lines. MTN on top, Airtel below.

Company Side: MTN leads revenue in all 4 years.
MTN 4-Year Total: 11,752,000,000,000
Airtel 4-Year Total: 7,807,000,000,000
Customer Side: Both lines go up every year, customers spending more.
MTN Subscribers 2025: 24,200,000
Airtel Subscribers 2025: 15,500,000

## 4. Main Finding 2022-2025
MTN outperformed Airtel in ALL 4 years overall.
MTN leads Total Revenue, Total Profit, and Subscribers in every year.
Airtel is growing, but MTN is still bigger in shillings.

## 5. Skills
Excel Cleaning, SQL Server (SSMS), Tableau, Financial Analysis, Data Extraction from PDF Annual Reports

## 6. Files in this Repo
- 2022-2025 mtn vs airtel clean (Excel)
- SYNTAX 1 to SYNTAX 6 screenshots
- Tableau Visual - Total Revenue Trend
