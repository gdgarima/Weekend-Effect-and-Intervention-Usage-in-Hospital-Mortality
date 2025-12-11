 # Weekend Effect and Intervention Usage in Hospital Mortality

## 🎯 Overview

[cite_start]This project conducts a comprehensive, two-phase analysis of the "weekend effect" on patient outcomes, specifically mortality and intervention usage, within a large dataset of **cardiovascular hospital admissions**[cite: 1490, 1493].

[cite_start]The study utilizes **Exploratory Data Analysis (EDA)** to establish crude differences, followed by **Multivariate Logistic Regression Modeling** to adjust for confounding variables (such as age, severity of illness, and comorbidities) and isolate the independent effect of weekend admission[cite: 1495, 1496].

---

## 💾 Data and Preparation

[cite_start]The analysis was performed on a massive, cleaned dataset comprising **8,096,311 complete hospital admission records**[cite: 1044, 960].

### Key Variables Analyzed:

* [cite_start]**Outcome:** In-hospital Mortality (`DIED`)[cite: 1036].
* [cite_start]**Primary Predictor:** Weekend Admission (`AWEEKEND`)[cite: 1035, 1049].
* [cite_start]**Hospital Characteristics:** Teaching Hospital Status[cite: 1509].
* [cite_start]**Confounders:** Age, Length of Stay (LOS), Gender (`FEMALE`), Race, Insurance Type (`PAY1`), and Clinical Severity Scores (APRDRG Risk Mortality and Severity of Illness)[cite: 1035, 1511, 1513].
* [cite_start]**Interventions:** Procedures like Percutaneous Coronary Intervention (PCI), Coronary Artery Bypass Graft (CABG), and Thrombolytic therapy[cite: 1498].

### Data Cleaning

[cite_start]Missing values were found to be sparse and inconsequential due to the large scale of the dataset[cite: 1041]. [cite_start]To ensure robust analysis, rows with critical missing data were systematically excluded, and **no artificial imputation techniques were applied**[cite: 1043, 1045].

---

## 📈 Phase 1: Exploratory Data Analysis (EDA) - Crude Findings

[cite_start]Initial, unadjusted comparisons revealed significant differences between weekend and weekday admissions[cite: 894, 915]:

| Feature | Weekday | Weekend | Interpretation (Crude) |
| :--- | :--- | :--- | :--- |
| **Mortality Rate** | 3.98% | 4.72% | [cite_start]**Significantly Higher on Weekends** [cite: 894] |
| **Mean Age** | 70.32 years | 70.60 years | [cite_start]Patients are slightly older on weekends [cite: 894] |
| **Severity** | Lower | Higher | [cite_start]Weekend admissions were more severe [cite: 894] |
| **LOS (mean)** | 5.60 days | 5.54 days | [cite_start]Slightly shorter stay on weekends [cite: 894] |

[cite_start]**Conclusion:** The EDA supported the existence of the "weekend effect" in crude comparisons, but highlighted that differences in patient severity and age were major confounding variables that required multivariate adjustment[cite: 915, 104].

---

## 🔬 Phase 2: Multivariate Modeling - Adjusted Findings

[cite_start]A **Logistic Regression Model** was employed to determine the independent effect of weekend admission on mortality after adjusting for clinical severity, demographics, and hospital type[cite: 1500, 1507].

### Mortality Model Key Results

| Predictor | Odds Ratio (OR) | p-value | Interpretation (Adjusted) |
| :--- | :--- | :--- | :--- |
| **Weekend Admission** | $\approx 1.00$ | $0.560$ (Not significant) | [cite_start]**No statistically significant independent effect on mortality** after adjustment for confounders[cite: 1563]. |
| **Teaching Hospital** | $\approx 1.07$ | $<0.001$ | [cite_start]Slightly increased mortality odds (significant)[cite: 1563]. |
| **APRDRG Risk Mortality** | $\approx 4.55$ | $<0.001$ | [cite_start]The **most predictive factor** for mortality[cite: 1563]. |
| **APRDRG Severity** | $\approx 2.63$ | $<0.001$ | [cite_start]A strong predictor for mortality[cite: 1563]. |

**Key Finding:** The crude "weekend effect" on mortality largely **disappeared** after controlling for the patient's severity of illness and clinical profile. [cite_start]This indicates that intrinsic patient factors are a greater influence on outcomes than the day of admission alone[cite: 1563, 1495].

### Procedure Usage Analysis

[cite_start]Separate logistic models were used to analyze the odds of receiving time-sensitive interventions[cite: 1429, 1498]:

* [cite_start]**CABG:** Weekend admissions were associated with **lower odds of undergoing CABG surgery**[cite: 1431, 1412]. [cite_start]This suggests potential systemic challenges, such as reduced surgical staffing or limited operating room availability during weekends[cite: 1413].
* [cite_start]**PCI:** Percutaneous Coronary Intervention (PCI) rates showed only minor differences between weekend and weekday admissions, supporting the success of **24/7 PCI protocols** in many hospitals[cite: 1415].
* [cite_start]**Hospital Type:** Teaching hospitals had higher odds of both PCI and CABG utilization, consistent with their expanded procedural capacity[cite: 1432].

### Model Performance

* [cite_start]**Accuracy:** $\approx 95.87\%$[cite: 1386].
* [cite_start]**Area Under the Curve (AUC):** $\approx 0.8856$[cite: 1387].
    * [cite_start]An AUC of $0.88+$ is considered strong for clinical models, indicating the logistic model reliably stratifies risk[cite: 1387].

---

## 📂 Project Files

| File Name | Description |
| :--- | :--- |
| `Independent_Study_Report_Garima.pdf` | **Phase 1:** Exploratory Data Analysis (EDA) Report, focusing on crude mortality and patient characteristic differences. |
| `Independent_Study_Report_Tanuj.pdf` | **Phase 2:** Multivariate Modeling Report, focusing on adjusted logistic regression for mortality and procedure usage. |

### Dependencies

The following Python libraries were used for data manipulation, statistical modeling, and visualization:

* [cite_start]`pandas` [cite: 1488]
* [cite_start]`statsmodels` [cite: 1488]
* [cite_start]`scikit-learn` [cite: 1488]
* [cite_start]`matplotlib` [cite: 1488]
