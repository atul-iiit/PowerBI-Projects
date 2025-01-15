This project examines healthcare data across three distinct patient categories to explore variations in waitlist times across various medical specialties, types of patients, and age demographics

Waitlist: The duration you wait before consulting the specialist

### 1. Problem Definition

Hospital management seeks insights into "waitlist variations". Our objective is to analyze the provided healthcare data to offer information and insights on waitlist management.

Following is the necessary information asked by the healthcare provider:
- Monitor current waitlists and track historical trends for Inpatient and Outpatient categories.
- Analyze wait times by specialty and age.
- Calculate average, median, and total waitlists.
### 2. Data Exploration
Range of Data Span: January 2018 to March 2021
Inpatients are categorized as either Inpatients or Day Cases.

Key field definitions in the datasets include:

- **Outpatient:** A patient who visits for a brief consultation.
- **Inpatient:** A patient admitted overnight or longer.
- **Day Case:** A patient treated for more complex issues than an Outpatient but discharged the same day.
- **Archive_Date:** The record date.
- **Specialty_HIPE:** The specialty code.
- **Specialty:** The medical field of the wait.
- **Case_Type:** The patient category.
- **Age_Profile:** The patient's age group.
- **Time_Bands:** The intervals of waiting time.

### 3. Data Preparation

To prepare the data, We checked if there exists any uniformity between the files.
There are eight patient waitlist files for the years 2018 to 2021. A preliminary examination reveals that all inpatient files share the same structure, as do the outpatient files. This uniformity allows us to merge the four files for each patient type using Power BI(Power Query Editor).

However, there are some minor discrepancies between the inpatient and outpatient files :
Column label doesn't match
- The fields "Specialty_Name" in inpatient data and "Speciality" in outpatient data represent the same information but have different labels.
A column is present in records of a particular category and absent in other
- "Case_Type" is absent in outpatient data because "Outpatient" is the only category applicable.

To unify these datasets in Power BI, some adjustments are necessary:
- The "Speciality" field in outpatient files has been renamed to "Specialty_Name" to align with the inpatient terminology.
- A "Case_Type" column was introduced in the outpatient data, with all entries labeled as "Outpatient."

Additional modifications included:
- Converting the "Archive_Date" from text to an appropriate date format.
- Standardizing the "Time_Band" and "Age_Profile" fields to eliminate inconsistencies and duplicates, such as consolidating entries like "18 Months +" and "18+ Months."

After these corrections, the files were combined into a single dataset named All_data.

The dataset contains numerous specialty names, 
It is a better idea to categorize them into groups for easier analyis.
We have created a file in MS Excel named Mapping_Speciality, where we have group the specialities with relevant groups and then loaded that file into Power BI

Afterwards, We established a relationship between our All_Data table and the Mapping_Specialty data, enabling us to utilize these specialty groupings for our analysis.

This concludes our preparation for data, Enabling us to delve into analysis part.


### 4. Analyzing the Data

We need to create two pages in Power BI:

- Summary page
	1. **_Total Current Month Waitlist vs. Total Previous Month Waitlist_**
	2. **_Average vs. Median Toggle buttons_**
	3. **_Donut chart of case type_**
	4. **_Stacked column chart to show us the relationship between Time Band and each Age profile_**
	5. **_Create a Top 5 specialty list using a multi-row card, based on Avg/Med waitlist_**
	6. **_Create separate line charts for Inpatients and Outpatients for Total Waitlist over Archive_Date_**
	
* Detail Page
	1. **_A matrix of the total patient wait list using Case_Type, Age_Profile, Time_Band, Specialty, and Archive_Date_**

### 5. Insights Shared Key observations from analyzing average and median waitlist data over recent years include:

- There has been a significant rise in waitlist numbers from last year (640K to 709K this year).
- A majority of those waiting are outpatients.
- The most common waitlist durations are from 0 to 3 months and over 18 months, according to median waitlist figures.
- The waitlists for Inpatients and Day Cases have been relatively stable over time, whereas the waitlist for Outpatients has been progressively increasing.
- The specialties with the highest median waitlists are Accident & Emergency, Dermatology, Clinical Genetics, Cardiology, and Pain Relief.

Given these findings, it is recommended that these five specialties focus on recruiting additional doctors and nurses to address the high wait times, particularly for outpatients.
