# 🏥 US Healthcare Patient Readmission Analysis

An end-to-end data analytics project analyzing **100,000+ patient records** from 130 US hospitals to identify readmission risk factors using Python, MySQL, and Power BI.

---

## 📌 Problem Statement

Hospital readmissions are a major healthcare challenge — costing billions annually and indicating gaps in patient care. This project analyzes diabetic patient data to uncover which demographic groups, treatment patterns, and clinical indicators are most associated with hospital readmission.

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|---|---|
| Python (Pandas, Seaborn, Matplotlib) | Data cleaning & EDA |
| MySQL Workbench | SQL analysis & business queries |
| Power BI | Interactive dashboard |
| Jupyter Notebook | Development environment |

---

## 📁 Project Structure

```
HEALTHCARE_ANALYSIS/
├── Dashboard_Screenshots/
│   ├── Page1.png
│   ├── Page2.png
│   └── Page3.png
├── diabetes+130-us+hospitals+for+years+1999-2008/
│   ├── Cleaned_data/
│   │   └── diabetic_data_clean.csv
│   └── Raw Data/
│       ├── diabetic_data.csv
│       └── IDS_mapping.csv
├── EDA_Findings/
│   ├── chart1_age_readmission.png
│   ├── chart2_gender_readmission.png
│   ├── chart3_hospital_stay.png
│   ├── chart4_medications_readmission.png
│   ├── chart5_race_readmission.png
│   └── chart6_top_diagnoses.png
├── SQL_Exports/
│   ├── q1_age_readmission.csv
│   ├── q2_hospital_stay.csv
│   ├── q3_race_age_ranking.csv
│   ├── q4_risk_segmentation.csv
│   └── q5_cumulative_age.csv
├── US Healthcare Patient Readmission Analysis.pdf
├── US_HealthCare_Dashboard.pbix
├── US_Healthcare_Presentation.pptx
└── US_healthcare.ipynb
```

---

## 📊 Dataset

**Source:** [130 US Hospitals Diabetes Dataset — Kaggle](https://www.kaggle.com/datasets/jimschacko/130-us-hospitals-for-years-1999-2008)

- 101,766 patient records from 130 US hospitals (1999–2008)
- 50 features including demographics, diagnoses, medications, and readmission status
- After cleaning: **100,241 rows × 45 columns**

---

## ⚙️ Phase 1 — Data Cleaning (Python)

- Replaced `?` placeholder values with NaN
- Dropped 5 high-missing columns (weight: 97%, max_glu_serum: 95%, A1Cresult: 83%)
- Filled race nulls with 'Unknown'
- Removed 3 invalid gender entries
- Created binary readmission columns for analysis
- Final clean dataset: **100,241 rows × 45 columns**

---

## 📈 Phase 2 — Exploratory Data Analysis

Key charts produced:

| Chart | Key Finding |
|---|---|
| Age vs Readmission | 70–80 age group has highest readmission rate (48.2%) |
| Gender vs Readmission | Female (47.1%) slightly higher than Male (45.4%) |
| Hospital Stay Duration | Most patients stay 1–4 days; avg 4.42 days |
| Medications vs Readmission | Patients on 10–30 medications have ~45–50% readmission rate |
| Race vs Readmission | Caucasian patients have highest readmission rate (47.1%) |
| Top Diagnoses | Heart Failure (428) is most common primary diagnosis (6,853 patients) |

### EDA Charts
Chart 1:
<img width="1122" height="653" alt="Screenshot 2026-06-18 131819" src="https://github.com/user-attachments/assets/35583185-4143-4e4d-ab90-4b41de192244" />

Chart 2:
<img width="682" height="425" alt="Screenshot 2026-06-18 131942" src="https://github.com/user-attachments/assets/58004fae-ec0f-45cb-ad72-ab246c9fda59" />

Chart 3:
<img width="947" height="588" alt="Screenshot 2026-06-18 132048" src="https://github.com/user-attachments/assets/26c3c1c0-518a-432a-bcc8-a4b1493bb023" />

Chart 4:
<img width="1148" height="467" alt="Screenshot 2026-06-18 132140" src="https://github.com/user-attachments/assets/50076fbb-c383-4606-af9e-c27fd7e17250" />

Chart 5:
<img width="952" height="593" alt="Screenshot 2026-06-18 132201" src="https://github.com/user-attachments/assets/78d7fef9-6778-4a9f-b885-3f052faebea7" />

Chart 6:
<img width="1121" height="652" alt="Screenshot 2026-06-18 132231" src="https://github.com/user-attachments/assets/46a36b59-fc74-4da7-afdd-bfbb0c7cc1a5" />

---

## 🗄️ Phase 3 — SQL Analysis (MySQL)

5 business queries written with advanced SQL concepts:

### Query 1 — Readmission Rate by Age Group
`GROUP BY` + aggregate functions
> 80–90 age group has highest readmission rate at **48.26%**

### Query 2 — Hospital Stay vs Readmission (Window Function)
`AVG() OVER()` with sliding window frame (ROWS BETWEEN)
> Readmission rate crosses **50% from day 8** onwards

### Query 3 — Top 3 Risk Groups per Race
`RANK() OVER (PARTITION BY)` inside subquery
> Hispanic patients aged 90–100 have highest readmission rate at **52.63%**

### Query 4 — Patient Risk Segmentation
Chained CTEs + `CASE WHEN`
> Very High Risk patients have **68.58%** readmission rate vs 39.93% for Normal patients

### Query 5 — Cumulative Readmission by Age
`SUM() OVER()` running total + cumulative percentage
> Top 3 age groups (60–90) account for **65%** of all readmissions

---

## 📉 Phase 4 — Power BI Dashboard (3 Pages)

### Page 1 — Executive Overview
<img width="1122" height="653" alt="Screenshot 2026-06-18 131819" src="https://github.com/user-attachments/assets/2da711d8-7f28-45a5-85bf-dfe912d1db8a" />

- Total Patients: 100,241
- Overall Readmission Rate: 46.31%
- Avg Hospital Stay: 4.42 days
- Risk category donut chart
- Cumulative readmission trend by age

### Page 2 — Patient Demographics & Risk Profile
<img width="1281" height="720" alt="Screenshot 2026-06-17 155120" src="https://github.com/user-attachments/assets/cc94acc8-d355-4b45-b143-d1abda21a1d8" />

- Readmission rate by age group (bar chart)
- Top 3 high risk age groups by race (matrix table)
- Interactive gender and readmission status slicers

### Page 3 — Treatment Patterns & Hospital Stay
<img width="1277" height="717" alt="Screenshot 2026-06-17 155203" src="https://github.com/user-attachments/assets/fc363653-505d-49df-8ef2-75bdd1ca0ad3" />

- Hospital stay duration vs readmission rate (combo chart)
- Smoothed readmission trend using moving average
- Top 10 primary diagnoses
- Risk category and race slicers

---

## 🔑 Key Findings

- Patients aged **70–90 have nearly double the readmission risk** compared to patients under 30
- **Very High Risk patients** (long stays + many medications + prior inpatient visits) have a **68.58% readmission rate**
- Just the **top 3 age groups (60–90) account for 65% of all readmissions** — classic Pareto pattern
- Heart Failure (ICD-9: 428) and Coronary Artery Disease (ICD-9: 414) are the most common comorbidities
- Longer hospital stays correlate with higher readmission — rate crosses 50% from day 8 onwards
- Racial disparities exist — Caucasian (47.1%) and African American (46%) patients have higher rates than Asian (35.8%)

---

## 💡 Business Recommendations

1. **Target elderly patients (70–90)** for post-discharge follow-up programs
2. **Flag Very High Risk patients** early using the 3-factor risk model (inpatient visits + medications + stay duration)
3. **Focus cardiac care resources** on Heart Failure and CAD patients — highest volume diagnoses
4. **Intervene before day 8** of hospital stay to reduce long-stay readmission risk
5. **Design race-aware care programs** to address the readmission gap between demographic groups

---

## ⚠️ Limitations

- Dataset is from 1999–2008 and may not reflect current medical practices
- Weight (96.8% missing) and A1C (83.3% missing) — key clinical features had to be dropped
- No temporal analysis — readmission patterns over time were not explored
- Risk thresholds set manually — a machine learning model could improve accuracy

---

## 🚀 How to Run

1. Clone this repository
2. Open `US_healthcare.ipynb` in Jupyter Notebook
3. Run all cells sequentially (Phase 1 & 2)
4. Import `diabetic_data_clean.csv` into MySQL using LOAD DATA command
5. Open `US_HealthCare_Dashboard.pbix` in Power BI Desktop
6. View full report in `US Healthcare Patient Readmission Analysis.pdf`
7. View presentation in `US_Healthcare_Presentation.pptx`

---

## 📦 Deliverables

| File | Description |
|---|---|
| `US_healthcare.ipynb` | Python notebook — cleaning + EDA |
| `US_HealthCare_Dashboard.pbix` | Power BI 3-page dashboard |
| `US Healthcare Patient Readmission Analysis.pdf` | Full project report |
| `US_Healthcare_Presentation.pptx` | Project presentation slides |
| `SQL_Exports/` | 5 SQL query result CSVs |
| `EDA_Findings/` | 6 EDA chart images |
| `Dashboard_Screenshots/` | 3 dashboard page screenshots |

---

## 👤 Author

**Anurag Chawla**
- LinkedIn: www.linkedin.com/in/anurag-chawla-4a0786220
- GitHub: https://github.com/anuragchawla27
- Email: anuragchawla7777@gmail.com
