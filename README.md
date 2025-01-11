# Project-Title-Healthcare Data Analysis and Insights


# Project Description
- Problem Statement:-
The healthcare industry generates vast amounts of data daily, providing valuable insights for
healthcare providers and policymakers to improve patient care, allocate resources effectively,
and manage healthcare costs. This project aims to analyze a comprehensive healthcare dataset
comprising medical examinations, hospitalization details, and customer profiles to extract
insights into patient health profiles, medical histories, and healthcare costs. By exploring
relationships between various health metrics, identifying trends, and visualizing key patterns.

Aim is to deliver actionable insights to healthcare stakeholders for informed decision-making
through rigorous data cleaning, transformation, exploration, and analysis.

# Project Steps and Objectives:
- Data Cleaning
- Data Transformation
- Data Exploration
- Data Analysis

## 1.Data Cleaning:-
Check for the number of missing values marked with '?' in each column of the “Medical Examinations” Table and "Hospitalization Details" Table.											
Soln:											
1. 2 missing values where found in 'medical Examinations'											
2. 15 where found in 'Hospitalization Details'											
											
 Fill in the missing values of ‘month’ with Sep and ‘year’ with its average rounded to the nearest integer.		
 
Soln: 1. Missing values in month column is replaced by sep - using formula "=IF(ISBLANK(C2),"Sep",C2)"											
2.Missing values in year column is replaced by their average- using formula- "=IF(ISBLANK(B2),AVERAGE($B$2:$B$2344),B2)"											
											
Determine the most frequently occurring values in the ‘smoker’, 'Hospital tier' and 'City tier' columns, and fill in the missing values accordingly											

Soln: I used COUNTIF for getting the counts of each tier in Hospital tier column., Tier1=309,Tier 2=1339,Tier3=694., so conclude that Tier2 is most frequently occuring value. 											
InCityTier, Tier1=734,Tier2=812,Tier3=796, so tier 2 is most frequently occuring value.											
In Smoker column,yes=488, no=1847. therefore, no is the most frequent value.											
I have replaced all missing/empty values in those 3 columns by most frequent values In that respective columns.											
											
If any 'State ID' values are missing, consider filling them with 'Unknown' or using another appropriate strategy											
Soln:  Using the formula "=IF(ISBLANK(I2),"Unknown",I2)", replaced all missing values in 'State ID' column with 'Unknown'		

## 2. Data Transformation:-
Split the ‘names’ column in the “Customer Names” Table into 3 meaningful columns:										
‘Title’, ‘First Name’, and ‘Last Name’.										
										
Soln: using TEXTSPLIT function, I have splitted the names column into First name , Title & Name("=TEXTSPLIT(B2," ")), then Title & Name into Title, Lastname columns. ("=TEXTSPLIT(D2,"."))										
										
"Convert the ""NumberOfMajorSurgeries"" column in the “Medical Examinations” Table to
numerical data by replacing non-numeric characters with meaningful numerical values"

Soln: First I have calculated the average of "NumberOfMajorSurgeries" column, by using formula "=AVERAGE(G2:G2336)". i.e, 1.252, then replaced all Non-numeric characters by this average value.										
										
"Check for inconsistencies in the 'Heart Issues' and 'smoker' columns and propose
corrective actions if necessary."										

Soln: After selecting the column, click ctrl+h, then find for inconsistencies, then replaced it with Correct typos, "Yes/No".										
										
"Create a new column named “Weight Status” that categorizes BMI into different
categories as below"										

Soln:After creating the 'Weight status" column,  using the formula "IF(B2 < 18.5,"Underweight", IF(B2 < 24.9,"NormalWeight", IF(B2 < 30,"Overweight", "Obesity"))",			

 I have created the result as shown table 										
										
"Create a new column named “Diabetes Status” and fill it as per the information given
below:"										
Soln:First, created a new column "Diabetes status", then using the formula : "=IF(C2<5.7,"Normal",IF(C2<6.4,"Prediabetes",IF(C2<6.5,"Prediabetes","Diabetes")))". 										
created the table as shown										
										
"Merge ‘year’, ‘month’ and ‘date’ columns in the “Hospitalization Details” Table into one
column named ‘Date of Birth’ and format it in ‘DD-MMM-YYYY’ custom format."										
Soln:using the formula,"=CONCATENTATE(B2," ",C2," ",D2), have merged the year,month,date column into 'Date of Birth' column. Then converted the format into date(dd-mm-yyyy)										
										
"Calculate the ‘Age’ of each customer based on their ‘Date of Birth’ and the date of
collection of the dataset, which is 8thJune 2023."										
Soln: using the formula "=DATEDIF(J2,DATE(2023, 6, 8), "Y")" calculated the age of each customer										
										
Format ‘charges’ column as currency ($)										
Soln: After selecting the 'Charges' column, click on formats from Home tab, then choose 'Currency'.										

## 3. Data Exploration:-
➔ Customer Names Table:												
Are there any duplicate Customer IDs in the dataset? If yes, how many?	

Soln: There are no duplicate Customer IDs in the dataset, as every ID is unique., using the formula "COUNTIF($A$2:$A$2336, A2)" found that no such duplicate ids												
												
How many customers are included in the dataset?								

Soln: In, Customer names dataset, there are 2335 customers.												
												
➔ Medical Examination Table:						
 ➢How many customers have a history of cancer?		
 
Soln: there are 391 customers have a historyof cancer. Formula used: "=COUNTIF(F2:F2336, "Yes")"	

➢How many obese customers have heart issues												

There are  926 customers have heart issues. Formula used: "=COUNTIF(D2:D2366, "Yes")			

➢ What is the total number of major surgeries performed on customers?									

There are 2922.4 number of surgeries performed on customers. Formula used :"=SUM(G2:G2336)"		

➢ Calculate the percentage of customers who have undergone any transplants.						

6.17% - Approximately . Formula used=" =COUNTIF(E2:E2336,"Yes") / COUNTA(E2:E2336)) *100"		

➢ Find the average HBA1C value of customers who are smokers.		

Soln:Average HBA1C value is 6.62, used formula:"=AVERAGEIF(H2:H2336,"Yes",, C2:C2336)"												
												
➔ Hospitalization details Table:												
➢ Calculate all the Summary statistics for the ‘charges’ column												
Soln:[ =COUNT(F2:F2344)]=2343												
[=SUM(F2:F2344)]=₹3,17,68,896												
[=AVERAGE(F2:F2344)]=₹13,559.07												
[=MIN(F2:F2344)=₹563.84												
[=MAX(F2:F2344)]=₹63,770.43												
[=STDEV.P(F2:F2344)]=11920.11383												
[=STDEV.S(F2:F2344)]=11922.65842												
[=VAR.P(F2:F2344)]=142089113.7												
[=VAR.S(F2:F2344)]= 142149783.7												
												
➢ Find the average hospitalization charges for customers who are more than 50 years old.

17856.8 is the average hospitalization charges for customers. Using formula "=AVERAGEIF(K2:K2344, ">50", F2:F2344)"												
												
➢ Compare the total charges across different hospital tiers.												
Hospital tier	Sum of charges											
tier - 1	₹ 8,629,189.23											
tier - 2	₹ 15,738,000.45											
tier - 3	₹ 6,558,983.10											
Grand Total	₹ 30,926,172.78											
												
												
➢ Calculate the average charges for people who have more than 2 children.												
Soln:14217.5 is the average charges for people who's having more than 2 children. Formula used is :[=AVERAGEIF(E2:E2344, ">2", F2:F2344)]												
												
"➢ Find the integer average number of children of customers who are less than 40 years
old."							

Soln:1.11045 is the average number, average integer is 1.												
formula used is:[=AVERAGEIF(K2:K2344, "<40", E2:E2344)]		

## 4. Data Analysis
Finally data is analysed visually using the tools:-
- Create pivot tables to do the following analysis, then visualize through charts:
- Analysis using Pie/Donut Chart:
- Analysis using Column/Bar Chart:
- Analysis using Line/Scatter Plot:






							

						
										
