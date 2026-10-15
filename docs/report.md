# Bank Loan Report Queries

## Bank Loan Report | Summary

### KPI's:

- Total Loan Appliactions
```
SELECT COUNT(id) AS Total_Loan_Applications FROM bank_loan
```
|Total_Loan_Appliactions|
|-----------------------|
|38576|
-------

>  Month to Date
```
SELECT COUNT(id) AS MTD_Total_Loan_Applications 
FROM bank_loan
WHERE MONTH(issue_date) = 12 AND YEAR(issue_date) = 2021
```
|MTD_Total_Loan_Applications|
|---------------------------|
|4314|
------