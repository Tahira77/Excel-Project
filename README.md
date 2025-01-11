# Healthcare Data Analysis and Insights

## Project Description

### Problem Statement:
The healthcare industry generates vast amounts of data daily, providing valuable insights for healthcare providers and policymakers to improve patient care, allocate resources effectively, and manage healthcare costs. This project aims to analyze a comprehensive healthcare dataset comprising medical examinations, hospitalization details, and customer profiles to extract insights into patient health profiles, medical histories, and healthcare costs. By exploring relationships between various health metrics, identifying trends, and visualizing key patterns, the aim is to deliver actionable insights to healthcare stakeholders for informed decision-making through rigorous data cleaning, transformation, exploration, and analysis.

---

## Project Steps and Objectives:

### 1. Data Cleaning:

- **Identify Missing Values:**
  - **Medical Examinations Table:** 2 missing values.
  - **Hospitalization Details Table:** 15 missing values.

- **Filling Missing Values:**
  - Replace missing `month` values with "Sep": `=IF(ISBLANK(C2),"Sep",C2)`.
  - Replace missing `year` values with average rounded to nearest integer: `=IF(ISBLANK(B2),AVERAGE($B$2:$B$2344),B2)`.
  - Replace missing values in `smoker`, `Hospital tier`, and `City tier` columns with their most frequent values using `COUNTIF`.
  - Replace missing `State ID` values with "Unknown": `=IF(ISBLANK(I2),"Unknown",I2)`.

### 2. Data Transformation:

- **Split `names` Column:**
  - Split into `Title`, `First Name`, and `Last Name`: `=TEXTSPLIT(B2," ")` and `=TEXTSPLIT(D2,".")`.

- **Convert `NumberOfMajorSurgeries` Column:**
  - Replace non-numeric characters with the average value: `=AVERAGE(G2:G2336)`.

- **Correct Inconsistencies:**
  - Standardize `Heart Issues` and `smoker` columns using `ctrl+h` to ensure consistent "Yes/No" values.

- **Add Derived Columns:**
  - **Weight Status:** Categorize BMI:
    ```excel
    =IF(B2 < 18.5,"Underweight",IF(B2 < 24.9,"NormalWeight",IF(B2 < 30,"Overweight","Obesity")))
    ```
  - **Diabetes Status:** Classify based on HBA1C levels:
    ```excel
    =IF(C2<5.7,"Normal",IF(C2<6.4,"Prediabetes",IF(C2<6.5,"Prediabetes","Diabetes")))
    ```

- **Merge and Format Date Columns:**
  - Combine `year`, `month`, and `date` into `Date of Birth` in `DD-MMM-YYYY` format:
    ```excel
    =CONCATENATE(B2," ",C2," ",D2)
    ```

- **Calculate Age:**
  - Compute age as of 8th June 2023:
    ```excel
    =DATEDIF(J2,DATE(2023,6,8),"Y")
    ```

- **Format `charges` Column:**
  - Apply currency format.

### 3. Data Exploration:

- **Customer Names Table:**
  - **Duplicate Customer IDs:** No duplicates found using `COUNTIF`.
  - **Total Customers:** 2,335.

- **Medical Examination Table:**
  - **Customers with Cancer History:** 391 (`=COUNTIF(F2:F2336,"Yes")`).
  - **Obese Customers with Heart Issues:** 926 (`=COUNTIF(D2:D2336,"Yes")`).
  - **Total Major Surgeries:** 2,922.4 (`=SUM(G2:G2336)`).
  - **Percentage of Customers with Transplants:** ~6.17% (`=COUNTIF(E2:E2336,"Yes")/COUNTA(E2:E2336)*100`).
  - **Average HBA1C for Smokers:** 6.62 (`=AVERAGEIF(H2:H2336,"Yes",C2:C2336)`).

- **Hospitalization Details Table:**
  - **Summary Statistics for `charges`:**
    - Count: 2,343
    - Total: $3,17,68,896
    - Average: $13,559.07
    - Min: $563.84, Max: $63,770.43
    - Std Dev: $11,920.11
  - **Average Charges for Customers > 50 Years:** $17,856.80 (`=AVERAGEIF(K2:K2344,">50",F2:F2344)`).
  - **Compare Charges Across Tiers:**
    - Tier 1: $8,629,189.23
    - Tier 2: $15,738,000.45
    - Tier 3: $6,558,983.10
  - **Average Charges for Customers with > 2 Children:** $14,217.50 (`=AVERAGEIF(E2:E2344,">2",F2:F2344)`).
  - **Average Integer Number of Children for Customers < 40 Years:** 1 (`=AVERAGEIF(K2:K2344,"<40",E2:E2344)`).

### 4. Data Analysis:

- **Visual Analysis:**
  - Create pivot tables and visualize insights using:
    - **Pie/Donut Charts:** Distribution of hospital tiers.
    - **Column/Bar Charts:** Comparison of charges by tiers.
    - **Line/Scatter Plots:** Trends in hospitalization charges over age groups.



## Summary:
This project cleanses, transforms, explores, and analyzes healthcare data to derive actionable insights. The findings are visualized using advanced Excel tools for better decision-making by healthcare stakeholders. Future work could involve integrating predictive modeling for more advanced analytics.
