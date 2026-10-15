# Bank Loan Report Queries

## Bank Loan Report | Summary

### KPI's:

- Total Loan Appliactions
```
SELECT COUNT(id) AS Total_Applications FROM bank_loan
```
|Total_Appliactions|
|------------------|
|38576|

- Month to Date Loan Applications
```
SELECT COUNT(id) AS MTD_Total_Applications 
FROM bank_loan
WHERE MONTH(issue_date) = 12
```
|MTD_Total_Applications|
|----------------------|
|4314|

- Previous Month to Date Loan Applications
```
SELECT COUNT(id) AS PMTD_Total_Applications 
FROM bank_loan
WHERE MONTH(issue_date) = 11
```
|PMTD_Total_Applications|
|-----------------------|
|4035|

---

- Total Funded Amount
```
SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan
```
|Total_Funded_Amount|
|-------------------|
|435757075|

- Month to Date Total Funded Amount
```
SELECT SUM(loan_amount) AS MTD_Total_Funded_Amount FROM bank_loan
WHERE MONTH(issue_date) = 12
```
|MTD_Total_Funded_Amount|
|-----------------------|
|53981425|

- Previous Month to Date Total Funded Amount
```
SELECT SUM(loan_amount) AS PMTD_Total_Funded_Amount FROM bank_loan
WHERE MONTH(issue_date) = 11
```
|PMTD_Total_Funded_Amount|
|------------------------|
|47754825|

---

- Total Amount Received
```
SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan
```
|Total_Amount_Collected|
|----------------------|
|473070933|

- MTD Total Amount Received
```
SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan
WHERE MONTH(issue_date) = 12
```
|Total_Amount_Collected|
|----------------------|
|58074380|

- PMTD Total Amount Received
```
SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan
WHERE MONTH(issue_date) = 11
```
|Total_Amount_Collected|
|----------------------|
|50132030|

---

- Average Interest Rate
```
SELECT AVG(int_rate)*100 AS Avg_Int_Rate FROM bank_loan
```
|Avg_Int_Rate|
|------------|
|12.0488314172048|

- MTD Average Interest
```
SELECT AVG(int_rate)*100 AS MTD_Avg_Int_Rate FROM bank_loan
WHERE MONTH(issue_date) = 12
```
|MTD_Avg_Int_Rate|
|-----------------|
|12.3560408676042|

- PMTD Average Interest
```
SELECT AVG(int_rate)*100 AS PMTD_Avg_Int_Rate FROM bank_loan
WHERE MONTH(issue_date) = 11
```
|PMTD_Avg_Int_Rate|
|-----------------|
|11.9417175498261|

---

- Avg DTI
```
SELECT AVG(dti)*100 AS Avg_DTI FROM bank_loan
```
|Avg_DTI|
|--------------|
|13.3274331211432|

- MTD Avg DTI
```
SELECT AVG(dti)*100 AS MTD_Avg_DTI FROM bank_loan
WHERE MONTH(issue_date) = 12
```
|MTD_Avg_DTI|
|----------------|
|13.6655377880425|

- PMTD Avg DTI
```
SELECT AVG(dti)*100 AS PMTD_Avg_DTI FROM bank_loan
WHERE MONTH(issue_date) = 11
```
|PMTD_Avg_DTI|
|----------------|
|13.3027335836364|



