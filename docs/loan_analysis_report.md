# Bank Loan Analysis Report

This is a detailed analysis report, it analyzes bank loan data to understand how many loans were issued, how much money went out, how much came back, and which loans performed good or bad.

---

## 1. Overview

The report covers every funded loan, from application through repayment.

| Metric | Value |
| :--- | :---: |
| **Total Loan Applications** | **38,576** |
| **Total Funded Amount** | **$435.8M** |
| **Total Amount Received** | **$473.1M** |
| **Net Gain (Received − Funded)** | **+$37.3M** |
| **Return on Funded Amount** | **8.6%** |
| **Average Interest Rate** | 12.05% |
| **Average DTI (Debt-to-Income)** | 13.33% |

### Key Observations:
- **Profitable Overall**: The bank got back **$473.1M** on **$435.8M** lent, a net gain of about **$37.3M**. This is despite a meaningful share of loans going bad.
- **Repayments Are Outpacing Lending**: In the latest month, funding grew **13.0%** month over month while money received grew **15.8%**. Collections are growing faster than new lending, which is a healthy sign.
- **Risk Indicators Are Creeping Up**: Average interest rate rose **3.5%** and average DTI rose **2.7%** month over month. Borrowers are slightly more leveraged and being charged slightly more, which is worth monitoring.
- **Average Loan Size**: The typical loan is about **$11,296** (funded amount ÷ applications).

---

## 2. Good Loan vs Bad Loan Analysis

Loans were classified by status. **Good loans** are those that are **Fully Paid** or **Current**. **Bad loans** are those that were **Charged Off**.

| Metric | Good Loans | Bad Loans |
| :--- | :---: | :---: |
| **Share of Applications** | **86.18%** | **13.82%** |
| **Applications** | ~33K (33,243) | ~5K (5,333) |
| **Funded Amount** | $370.2M | $65.5M |
| **Amount Received** | $436M | $37M |
| **Net Result** | **+$65.6M (+17.7%)** | **−$28.2M (−43.1%)** |
| **Recovery on Funded Amount** | 117.7% | 56.9% |

### Key Good vs Bad Loan Observations:
- **Core Insight**: About **86 of every 100 loans** are good. These loans return nearly **18% more** than was lent out.
- **The Cost of Bad Loans**: Charged-off loans recover only about **57%** of the money lent, a loss of roughly **$28.2M**.
- **Bad Loans Are Bigger Than Average**: Bad loans are 13.82% of applications but about **15%** of funded dollars. Defaulted loans tend to be larger than the typical loan.
- **Good Loans Cover the Losses Comfortably**: Profit from good loans (**$65.6M**) is more than **double** the loss from bad loans (**$28.2M**). Cutting the bad loan rate even slightly would noticeably raise total profit.

---

## 3. Loan Status & Repayment Analysis

| Loan Status | Applications | Funded Amount | Amount Received | Avg Interest Rate | Avg DTI | Avg Loan Size |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Fully Paid** | 32,145 | $351,358,350 | $411,586,256 | 12% | 13% | ~$10,931 |
| **Charged Off** | 5,333 | $65,532,225 | $37,284,763 | 14% | 14% | ~$12,288 |
| **Current** | 1,098 | $18,866,500 | $24,199,914 | 15% | 15% | ~$17,182 |

### Key Repayment Observations:
- **Most Loans Are Repaid in Full**: **83%** of all loans (32,145) are Fully Paid, and they generated **$411.6M** in repayments on **$351.4M** funded.
- **Defaulters Carry Higher Rates and Higher DTI**: Charged-off loans average **14% interest and 14% DTI**, against **12% and 13%** for fully paid loans. Borrowers who were already more stretched, and charged more, were the ones who failed to repay.
- **"Current" Loans Need Watching**: The 1,098 active loans have the **highest rate (15%), highest DTI (15%) and largest average size (~$17K)**. They have already returned $24.2M on $18.9M funded, but their risk profile looks like the charged-off group, so some may turn bad later.

---

## 4. Trend Analysis by Time

Monthly funded amount (rounded, in $M):

| Month | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec |
| :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **Funded ($M)** | 25 | 25 | 29 | 30 | 32 | 34 | 36 | 38 | 41 | 45 | 48 | 54 |

| Quarter | Q1 | Q2 | Q3 | Q4 |
| :--- | :-: | :-: | :-: | :-: |
| **Approx. Funded ($M)** | ~79 | ~96 | ~115 | ~147 |

### Key Time Trend Observations:
- **Lending More Than Doubled**: Monthly funding grew from **$25M in January to $54M in December**, an increase of about **116%**.
- **Steady, Consistent Growth**: Funding rose in almost every month, with no major dips after February. This points to steady demand and not a one-off seasonal spike.
- **Growth Accelerated Late in the Year**: Q4 funding (~$147M) was about **86% higher** than Q1 (~$79M) and made up roughly **one third** of the full-year total.
- **December Is the Peak**: December hit **$54M**, the highest month, with about **$58.1M** received in the same period.

---

## 5. Trend Analysis by Region

### Key Regional Observations:
- **Funding Is Geographically Concentrated**: **California** has the highest funded amount by a clear margin. **New York**, **Texas** and **Florida** form the next tier.
- **Wide Spread of Low-Volume States**: Most Midwest and Mountain states show light activity, which suggests room to grow outside the big four.
- **No Activity in North Dakota**: It is the only state with no funding.
- **Dependence Risk**: Heavy reliance on a few states means the portfolio is exposed to economic conditions in California, New York, Texas and Florida.

---

## 6. Trend Analysis by Customer Profile

### 6.1 Employment Length

| Employment Length | Funded Amount |
| :--- | :---: |
| **10+ years** | **$116M** |
| 2 years | $45M |
| < 1 year | $44M |
| 3 years | $44M |
| 4 years | $38M |
| 5 years | $37M |
| 1 year | $33M |
| 6 years | $26M |
| 7 years | $21M |
| 8 years | $18M |
| 9 years | $15M |

- **Long-Tenure Borrowers Dominate**: Customers with **10+ years** of employment received **$116M**, about **27%** of all funding and over **2.5x** the next group.
- **Early-Career Borrowers Are Also Big Users**: Customers with under 1 to 3 years of employment each draw $44M to $45M, so newer workers are an important segment.
- **Mid-Tenure Dip**: Funding drops steadily from 6 to 9 years of employment ($26M down to $15M).

### 6.2 Loan Purpose

| Purpose | Funded Amount (approx.) |
| :--- | :---: |
| **Debt Consolidation** | **$0.23bn** |
| Credit Card | $0.06bn |
| Home Improvement | $0.03bn |
| Other | $0.03bn |
| Small Business | $0.02bn |
| Major Purchase | $0.02bn |
| Car, Wedding, Medical | ~$0.01bn each |
| House, Moving | ~$0.00bn |

- **Debt Consolidation Leads by a Mile**: It accounts for roughly **53%** of all funding.
- **Customers Borrow Mainly to Pay Off Other Debt**: Debt consolidation plus credit card loans together make up about **two thirds** of funding. Borrower motivation is mostly refinancing, not new spending.

### 6.3 Home Ownership and Loan Term

| Home Ownership | Funded Amount |
| :--- | :---: | :---: |
| **Mortgage**	| **$219.3M** |
| Rent	| $185.8M |
| Own	| $29.6M |
| Other	| $1.0M |

| Loan Term | Funded Amount | Share |
| :--- | :---: | :---: |
| **36 months** | $273M | 62.66% |
| **60 months** | $163M | 37.34% |

- **Mortgage holders are the largest group, followed by renters.** "Own" and "Other" are very small.
- **Customers Prefer the Shorter Term**: Nearly **two thirds** of funding goes to 36-month loans.

---

## 7. Factors Affecting Approval and Repayment

### 7.1 Factors Linked to Repayment

| Factor | What the Data Shows |
| :--- | :--- |
| **Interest Rate** | Charged-off loans average **14%** vs **12%** for fully paid. Higher rates go with higher default. |
| **DTI** | Charged-off loans average **14%** vs **13%** for fully paid. Higher debt burden goes with higher default. |
| **Loan Size** | Charged-off loans are larger (~$12.3K vs ~$10.9K). |
| **Loan Grade** | In the loan-level records, interest rate rises as grade gets worse: Grade A ≈ 8%, Grade B ≈ 10–12%, Grade C ≈ 11–14%, Grade D ≈ 15%. Lower grades are priced for higher risk. |

### 7.2 Factors Linked to Who Gets Funded

| Factor | What the Data Shows |
| :--- | :--- |
| **Employment Length** | 10+ years has the highest funding ($116M). Stable, long-term employees are funded most. |
| **Home Ownership** | Mortgage and rent holders dominate. |
| **Purpose** | Debt consolidation and credit card refinancing dominate. |
| **Location** | California, New York, Texas and Florida lead. |
| **Term** | 36-month loans are preferred. |

### Key Factor Observations:
- **Risk Is Priced In, but Not Enough**: Higher-risk borrowers do pay higher rates (grades C and D, and "Current" loans at 15%), yet the charged-off group still loses **43%** of funded money. The extra interest does not fully cover the losses.
- **DTI and Rate Together Are the Strongest Warning Signs**: Both are higher in every weaker group (charged off and current), so they work as early indicators.
- **Approval Factors Have a Data Limit**: The dataset only contains loans that were **funded**. There are no rejected applications, so approval rules cannot be measured directly. The findings above show who the bank **chooses to fund most**, not why others were declined.

---

## Recommendations for Optimization

1. **Tighten Screening on High DTI and High-Rate Borrowers**: Set tighter DTI limits or require extra checks for applicants near 14–15% DTI, since this group shows up most in charge-offs.
2. **Review Large Loan Approvals**: Charged-off loans are larger than average. Add stricter checks or loan-size caps for weaker grades.
3. **Closely Monitor the "Current" Loan Book**: The 1,098 active loans ($18.9M) have the highest rate, DTI and size. Early-warning follow-ups on missed payments could prevent future charge-offs.
4. **Reduce Reliance on Four States**: Keep serving California, New York, Texas and Florida, but grow marketing in low-volume states to spread geographic risk.
5. **Target Stable-Income Customers**: Long-tenure employees borrow the most and fit the lower-risk profile. Offer them tailored products and refinancing options.
6. **Build Products Around Debt Consolidation**: It is more than half of all lending, so dedicated consolidation offers and pricing could capture more of this demand.
7. **Track Rate and DTI Trends Monthly**: Both are rising month over month. Watching them now helps catch rising risk before it appears as defaults.