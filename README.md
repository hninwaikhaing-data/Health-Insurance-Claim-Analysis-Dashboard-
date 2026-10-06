# Health-Insurance-Claim-Analysis-Dashboard-
# Health Insurance Claims Cost Driver Analysis | Power BI

## Project Overview

A health insurance company is experiencing financial pressure from healthcare claims and needs better visibility into where claims spending is concentrated.

This project uses **Power BI** to analyze healthcare claims and member data to identify the major drivers of claims expenditure across claim types, procedures, diagnoses, members, insurance plans, and demographic segments.

The final solution is a **five-page interactive Power BI report** designed to help management monitor claims spending, investigate high-cost areas, and support data-driven cost-management decisions.

---

## Business Problem


A health insurance company is experiencing financial pressure from healthcare claims and needs better visibility into where claims spending is concentrated.

C-level executives need to understand which healthcare services, procedures, diagnoses, and members are driving the greatest costs and how provider-billed amounts compare with actual claim payments.

This project analyzes healthcare claims and member data to identify the key drivers of healthcare spending, including claim types, medical procedures (CPT), diagnoses (ICD), and high-cost members, while evaluating the relationship between billed and paid amounts.

The goal is to develop an executive Power BI dashboard that provides clear visibility into healthcare claims spending, highlights major cost drivers and areas of cost concentration, and supports data-driven cost-management decisions.

---

## Project Objective

The objective is to analyze health insurance claims and member data to:

- Identify the most expensive claim types.
- Determine which CPT procedure codes drive the highest claims spending.
- Identify ICD diagnosis codes associated with high claims costs.
- Identify members responsible for the largest share of expenditure.
- Distinguish high-cost members from high-utilization members.
- Compare billed and paid amounts across claim types and insurance plans.
- Evaluate payment ratios across plan types.
- Examine claims spending across member age groups.
- Translate analytical findings into actionable business recommendations.

---

## Business Questions

The analysis focuses on four primary business questions:

1. Which claim types are the most expensive?
2. Which CPT and ICD codes drive the highest spending?
3. Which members account for the largest share of total costs?
4. How do billed amounts compare to paid amounts?

---
## Supporting Analysis

To provide additional context around the primary business questions, the dashboard also examines:

- Average paid amount per claim
- Claim volume and utilization
- Paid-to-billed ratio
- Claims spending by insurance plan
- Claims spending by member age group
- High-cost versus high-utilization members
  
## Dataset

The project uses two synthetic health insurance datasets.

### `claims.csv`

Contains claim-level healthcare service and financial information.

| Field | Description |
|---|---|
| `claim_id` | Unique identifier for each claim |
| `member_id` | Member associated with the claim |
| `provider_id` | Healthcare provider identifier |
| `claim_date` | Date associated with the claim |
| `claim_type` | Healthcare service category |
| `cpt_code` | Procedure/service code |
| `icd_code` | Diagnosis code |
| `billed_amount` | Amount billed by the healthcare provider |
| `paid_amount` | Amount paid on the claim |

### `members.csv`

Contains member demographic, insurance plan, and enrollment information.

| Field | Description |
|---|---|
| `member_id` | Unique member identifier |
| `member_age` | Member age |
| `member_gender` | Recorded gender |
| `plan_type` | Health insurance plan |
| `enrollment_start_date` | Insurance enrollment start date |
| `enrollment_end_date` | Insurance enrollment end date |

### Dataset Size

- **449 claims**
- **100 members**
- **134 unique CPT codes**
- **117 unique ICD codes**

---

## Tools & Technologies

- **Power BI Desktop** — data preparation, modeling, DAX, analysis, and dashboard development
- **Power Query** — data cleaning and type transformation
- **DAX** — KPI and analytical measure development
- **Power BI Service** — report publishing and online viewing

---

## Data Preparation

Data preparation was completed in Power Query before analysis.

Key preparation steps included:

- Reviewing missing and invalid values
- Correcting data types
- Converting financial fields to numeric formats
- Converting claim and enrollment fields to date types
- Preserving CPT and ICD codes as categorical/text fields
- Validating member and claim identifiers
- Preparing clean claims and member tables for modeling

---

## Data Model

The report uses a simple analytical model consisting of:

- `claims` — claim-level fact table
- `members` — member dimension
- `Date` — dedicated calendar table
- `Measure Table` — centralized DAX measures

### Data Modeling

```text
members
   │
   │ member_id
   │ 1 : *
   ▼
claims
   ▲
   │ * : 1
   │ claim_date
   │
 Date
```

This model enables analysis across time, member demographics, plan types, claim types, procedures, and diagnoses.

---

## Core KPIs

The report includes measures such as:

- Total Paid Amount
- Total Billed Amount
- Total Claims
- Total Members
- Members with Claims
- Average Paid per Claim
- Paid Ratio
- Unique CPT Codes
- Unique ICD Codes
- % of Total Paid
- CPT Share of Paid Amount
- ICD Share of Paid Amount



# Dashboard Pages

## 1. Executive Claims Overview

**Business Question:**  
*Where is claims spending concentrated?*

The executive overview provides a high-level assessment of claims expenditure and identifies the primary claim-type cost drivers.

### Analysis

- Total Paid Amount
- Total Billed Amount
- Total Claims
- Paid Ratio
- Total Paid Amount by Claim Type
- Average Paid per Claim by Claim Type
- Billed vs Paid Amount by Claim Type
- Claim Type Cost Summary
- % of Total Paid by Claim Type

### Key Finding

**Inpatient claims are the dominant cost driver**, generating approximately **$1.09M** and accounting for **70.4% of total paid claims**.

Although inpatient represented only **99 claims**, the average paid amount was approximately **$11.03K per claim**, indicating that high spending is driven primarily by **claim severity rather than claim volume**.

---

## 2. CPT & ICD Cost Drivers

**Business Question:**  
*Which procedures and diagnoses are driving claims costs?*

This page provides procedure- and diagnosis-level analysis to identify areas where spending is concentrated.

### Analysis

- Total Paid Amount
- Total Claims
- Unique CPT Codes
- Unique ICD Codes
- Average Paid per Claim
- Top 10 CPT Codes by Total Paid Amount
- Top 10 ICD Codes by Total Paid Amount
- CPT Cost Driver Details
- ICD Cost Driver Details
- Average Paid per Claim by Code
- % of Paid Amount by CPT and ICD

### Key Findings

- **CPT 67890** is the largest procedure-level cost driver, contributing approximately **$242.7K (15.7%)** of total paid amount.
- **CPT 23456** contributed approximately **$203.8K (13.1%)**.
- **CPT 00123** recorded a high average cost of approximately **$10.17K per claim**.
- **ICD I10** is the largest diagnosis-level cost driver at approximately **$259.6K (16.7%)** of total paid amount.

These findings demonstrate that claims expenditure is concentrated among a relatively small group of procedure and diagnosis codes.

---

## 3. Member & Payment Analysis

**Business Question:**  
*Which members drive the largest costs, and how do payments vary?*

This page analyzes member-level cost concentration, utilization patterns, demographics, and plan-level payment performance.

### Analysis

- Total Members
- Members with Claims
- Total Claims
- Total Paid Amount
- Average Paid per Claim
- Top 10 Members by Total Paid Amount
- Top 10 Members by Claim Count
- Total Paid Amount by Age Group
- Total Paid Amount by Plan Type
- Billed vs Paid Amount by Plan Type
- Paid Ratio by Plan Type
- High-Cost Member Details

### Key Findings

**Member 6** generated the highest member-level expenditure at approximately **$43.3K from only 4 claims**, averaging approximately **$10.8K per claim**.

The members with the highest claim counts were not necessarily the members with the highest expenditure, demonstrating that **claim frequency and claim severity represent different cost patterns**.

Payment ratios across plan types remained relatively stable at approximately **74.6%–76.9%**, despite differences in total plan spending.

The **31–45 age group** generated the highest claims expenditure at approximately **$580K**.

---

## 4. Key Insights

The analysis identified several major patterns:

### Inpatient Cost Concentration
Inpatient claims account for **70.4% of total paid claims**, making inpatient care the largest overall cost driver.

### Procedure-Level Cost Concentration
A relatively small number of CPT codes contribute disproportionately to total expenditure, with CPT 67890 and CPT 23456 among the largest drivers.

### Diagnosis-Level Cost Concentration
ICD I10 represents the largest diagnosis-level cost driver, contributing approximately **16.7% of total paid amount**.

### Cost vs Utilization
High-cost members are not necessarily high-utilization members. Some members generate significant expenditure through a small number of expensive claims.

### Plan Payment Patterns
Payment ratios are relatively consistent across insurance plans, suggesting that differences in total spending may be more strongly influenced by claim volume, claim mix, and severity.

---

## 5. Business Recommendations

### Prioritize Inpatient Cost Review

Conduct deeper analysis of high-cost inpatient claims by procedure, diagnosis, provider, and member to understand the drivers behind high average claim severity.

### Monitor High-Cost CPT and ICD Codes

Establish regular monitoring of procedure and diagnosis codes with high total spending or high average cost per claim.

### Segment Members by Cost and Utilization

Use a combination of **Total Paid Amount, Claim Count, and Average Paid per Claim** to distinguish frequent healthcare users from members experiencing high-cost episodes of care.

### Investigate Plan-Level Cost Drivers

Analyze claim volume, claim type mix, member composition, procedures, and diagnoses to explain differences in total expenditure across insurance plans.

### Establish Ongoing Claims Cost Monitoring

Use the Power BI report to monitor claims expenditure across:

**Claim Type → CPT → ICD → Member → Plan → Provider**

This enables management to identify emerging areas of cost concentration and prioritize further investigation.

---

## Business Impact

The dashboard provides management with a consolidated view of healthcare claims expenditure and helps identify where financial exposure is concentrated.

The analysis supports:

- Faster identification of high-cost claim categories
- Procedure- and diagnosis-level cost monitoring
- High-cost member identification
- Separation of utilization frequency from claim severity
- Plan-level payment and spending analysis
- More targeted claims cost review and resource allocation

> The analysis identifies cost concentration and areas requiring further review. It does not determine medical necessity, fraud, or avoidable healthcare utilization.

---

## Project Structure

```text
health-insurance-claims-analysis/
│
├── data/
│   ├── claims.csv
│   └── members.csv
│
├── dashboard/
│   └── health_insurance_claim_analysis.pbix
│
├── images/
│   ├── executive_claims_overview.png
│   ├── cpt_icd_cost_drivers.png
│   ├── member_payment_analysis.png
│   ├── key_insights.png
│   └── recommendations.png
│
└── README.md
```

---

## Dashboard Preview

### Executive Claims Overview

![Executive Claims Overview](images/executive_claims_overview.png)

### CPT & ICD Cost Drivers

![CPT & ICD Cost Drivers](images/cpt_icd_cost_drivers.png)

### Member & Payment Analysis

![Member & Payment Analysis](images/member_payment_analysis.png)

### Key Insights

![Key Insights](images/key_insights.png)

### Business Recommendations

![Business Recommendations](images/recommendations.png)

---

## Conclusion

The project demonstrates how **Power BI, Power Query, data modeling, and DAX** can be used to transform health insurance claims data into actionable business insights.

The analysis found that claims spending is highly concentrated, particularly in **inpatient care, selected CPT and ICD codes, and specific high-cost members**. It also showed that high expenditure is not always associated with high claim frequency, emphasizing the importance of analyzing both **utilization and claim severity**.

The resulting dashboard provides an interactive decision-support tool for monitoring claims costs, investigating high-cost areas, and supporting targeted cost-management analysis.
