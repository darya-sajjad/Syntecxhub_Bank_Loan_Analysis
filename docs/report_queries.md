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
SELECT COUNT(id) AS MTD_Total_Applic|----|-----|-----|----|----ations 
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

# Good Loan Issued:

- Good Loan Percentage
```
SELECT
    (COUNT(CASE WHEN loan_status = 'Fully Paid' OR loan_status = 'Current' THEN id END) * 100.0) / 
	COUNT(id) AS Good_Loan_Percentage
FROM bank_loan
```
|Good_Loan_Percentage|
|----------------------|
|86.175342181667|

- Good Loan Applications
```
SELECT COUNT(id) AS Good_Loan_Applications FROM bank_loan
WHERE loan_status = 'Fully Paid' OR loan_status = 'Current'
```
|Good_Loan_Applications|
|----------------------|
|33243|

- Good Loan Funded Amount
```
SELECT SUM(loan_amount) AS Good_Loan_Funded_amount FROM bank_loan
WHERE loan_status = 'Fully Paid' OR loan_status = 'Current'
```
|Good_Loan_Funded_amount|
|----------------------|
|370224850|

# Bad Loan Issued

- Bad Loan Percentage
```
SELECT
    (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / 
	COUNT(id) AS Bad_Loan_Percentage
FROM bank_loan
```
|Bad_Loan_Percentage|
|----------------------|
|13.824657818332|

- Bad Loan Applications
```
SELECT COUNT(id) AS Bad_Loan_Applications FROM bank_loan
WHERE loan_status = 'Charged Off'
```
|Bad_Loan_Applications|
|----------------------|
|5333|

- Bad Loan Funded Amount
```
SELECT SUM(loan_amount) AS Bad_Loan_Funded_amount FROM bank_loan
WHERE loan_status = 'Charged Off'
```
|Bad_Loan_Funded_amount|
|----------------------|
|65532225|

- Bad Loan Amount Received
```
SELECT SUM(total_payment) AS Bad_Loan_amount_received FROM bank_loan
WHERE loan_status = 'Charged Off'
```
|Bad_Loan_amount_received|
|----------------------|
|37284763|

# Loan Status

```
SELECT
        loan_status,
        COUNT(id) AS LoanCount,
        SUM(total_payment) AS Total_Amount_Received,
        SUM(loan_amount) AS Total_Funded_Amount,
        AVG(int_rate * 100) AS Interest_Rate,
        AVG(dti * 100) AS DTI
    FROM
        bank_loan
    GROUP BY
        loan_status
```
| loan_status | LoanCount | Total_Amount_Received | Total_Funded_Amount | Interest_Rate | DTI |
|----|-----|-----|----|----|----|
| Fully Paid |	32145 |	411586256 |	351358350 |	11.6410707918092 |	13.1673507557434 |
| Charged Off |	5333 |	37284763 |	65532225 |	13.8785749318289 |	14.0047328005517 |
| Current |	1098 |	24199914 |	18866500 |	15.0993260800947 |	14.7243442736843 |

```
SELECT 
	loan_status, 
	SUM(total_payment) AS MTD_Total_Amount_Received, 
	SUM(loan_amount) AS MTD_Total_Funded_Amount 
FROM bank_loan
WHERE MONTH(issue_date) = 12 
GROUP BY loan_status
```
| loan_status | MTD_Total_Amount_Received | MTD_Total_Funded_Amount |
|----|-----|-----|
| Fully Paid |	47815851 |	41302025 |
| Charged Off |	5324211 |	8732775 |
| Current |	4934318 |	3946625 |

---

## Bank Loan Report | Overview

### MONTH
```
SELECT 
	MONTH(issue_date) AS Month_Number, 
	DATENAME(MONTH, issue_date) AS Month_name, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan
GROUP BY MONTH(issue_date), DATENAME(MONTH, issue_date)
ORDER BY MONTH(issue_date)
```
| Month_Number | Month_name | Total_Loan_Applications |Total_Funded_Amount | Total_Funded_Amount | Total_Amount_Received |
|----|-----|-----|----|----|----|
| 1	| January |	2332 | 25031650	| 27578836 |
| 2	| February | 2279	24647825	| 27717745 |
| 3	| March	| 2627 | 28875700	| 32264400 |
| 4	| April |	2755 |	29800800 |	32495533 |
| 5	| May |	2911 | 31738350	| 33750523 |
| 6	| June |	3184 |	34161475 |	36164533 |
| 7	| July |	3366 |	35813900 |	38827220 |
| 8	| August |	3441 |	38149600 |	42682218 |
| 9	| September |	3536 |	40907725 |	43983948 |
| 10 |	October	| 3796	| 44893800	| 49399567 | 
| 11 |	November |	4035 |	47754825 |	50132030 |
| 12 |	December |	4314 |	53981425 |	58074380 |

### STATE
```
SELECT 
	address_state AS State, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan
GROUP BY address_state
ORDER BY address_state
```
| State | Total_Loan_Applications | Total_Funded_Amount | Total_Amount_Received |
|----|-----|-----|----|
|AK|	78	|1031800	|1108570|
|AL| 432	|4949225	|5492272|
|AR|	236	|2529700	|2777875|
|AZ|	833	|9206000	|10041986|
|CA|	6894 |	78484125|	83901234|
|CO|	770	|8976000	|9845810|
|CT|	730	|8435575	|9357612|
|DC|	214	|2652350	|2921854|
|DE|	110	|1138100	|1269136|
|FL|	2773|	30046125|	31601905|
|GA|	1355|	15480325|	16728040|
|HI|	170	|1850525	|2080184|
|IA|	5	|56450	|64482|
|ID|	6	|59750	|65329|
|IL|	1486|	17124225|	18875941|
|IN|	9	|86225	|85521|
|KS|	260	|2872325|	3247394|
|KY|	320	|3504100|	3792530|
|LA|	426	|4498900|	5001160|
|MA|	1310|	15051000|	16676279|
|MD|	1027|	11911400|	12985170|
|ME|	3	|9200	|10808|
|MI|	685	|7829900|	8543660|
|MN|	592	|6302600|	6750746|
|MO|	660	|7151175|	7692732|
|MS|	19	|139125	|149342|
|MT|	79	|829525	|892047|
|NC|	759	|8787575|	9534813|
|NE|	5	|31700	|24542|
|NH|	161	|1917900|	2101386|
|NJ|	1822|	21657475|	23425159|
|NM|	183	|1916775	|2084485|
|NV|	482	|5307375	|5451443|
|NY|	3701|	42077050|	46108181|
|OH|	1188|	12991375|	14330148|
|OK|	293	|3365725	|3712649|
|OR|	436	|4720150	|4966903|
|PA|	1482|	15826525|	17462908|
|RI|	196	|1883025	|2001774|
|SC|	464	|5080475	|5462458|
|SD|	63	|606150	|656514|
|TN|	17	|162175	|141522|
|TX|	2664|	31236650|	34392715|
|UT|	252	|2849225	|2952412|
|VA|	1375|	15982650|	17711443|
|VT|	54	|504100	|534973|
|WA|	805	|8855525|	9531739|
|WI|	446	|5070450|	5485161|
|WV|	167	|1830525|	1991936|
|WY|	79	|890750	|1046050|

### TERM
```
SELECT 
	term AS Term, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan
GROUP BY term
ORDER BY term
```
| Term | Total_Loan_Applications | Total_Funded_Amount | Total_Amount_Received |
|----|-----|-----|----|
| 36 months |	28237 |	273041225 |	294709458 |
| 60 months	| 10339	| 162715850	| 178361475 |

### EMPLOYEE LENGTH
```
SELECT 
	emp_length AS Employee_Length, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan
GROUP BY emp_length
ORDER BY emp_length
```
| Employee_Length | Total_Loan_Applications | Total_Funded_Amount | Total_Amount_Received |
|----|-----|-----|----|
| <1 year |	4575 |	44210625	| 47545011 |
| 1 year	| 3229	| 32883125	| 35498348 |
| 10+ years | 8870	| 116115950 |	125871616 |
| 2 years |	4382 |	44967975	| 49206961 |
| 3 years |	4088 |	43937850	| 47551832 |
| 4 years |	3428 |	37600375	| 40964850 |
| 5 years |	3273 |	36973625	| 40397571 |
| 6 years |	2228 |	25612650	| 27908658 |
| 7 years |	1772 |	20811725	| 22584136 |
| 8 years |	1476 |	17558950	| 19025777 |
| 9 years |	1255 |	15084225	| 16516173 |

### PURPOSE
```
SELECT 
	purpose AS PURPOSE, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan
GROUP BY purpose
ORDER BY purpose
```
| PURPOSE | Total_Loan_Applications | Total_Funded_Amount | Total_Amount_Received |
|----|-----|-----|----|
|car	| 1497	| 10223575 |	11324914 |
|credit card	| 4998	| 58885175	| 65214084 |
|Debt consolidation	| 18214	| 232459675	| 253801871 |
|educational |	315	| 2161650	| 2248380 |
|home improvement | 2876	| 33350775	| 36380930 |
|house	| 366	| 4824925	|5185538 |
|major purchase	| 2110	| 17251600	| 18676927 |
|medical |	667	| 5533225 |	5851372 |
|moving	| 559	| 3748125	| 3999899 |
|other	| 3824	| 31155750	| 33289676 |
|renewable_energy	| 94	845750 |	898931 |
|small business	| 1776 |	24123100	| 23814817 |
|vacation	| 352	| 1967950	| 2116738 |
|wedding	| 928	| 9225800	| 10266856 |

### HOME OWNERSHIP
```
SELECT 
	home_ownership AS Home_Ownership, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan
GROUP BY home_ownership
ORDER BY home_ownership
```
| Home_Ownership | Total_Loan_Applications | Total_Funded_Amount | Total_Amount_Received |
|----|-----|-----|----|
| MORTGAGE	| 17198	| 219329150	| 238474438 |
| NONE	| 3	| 16800	| 19053 |
| OTHER	| 98 |	1044975 |	1025257 |
| OWN	| 2838 |	29597675 |	31729129 |
| RENT	| 18439	| 185768475	| 201823056 |

> **NOTE:** The analysis is not limited to these queries, various filters are applied on all the dashboards

