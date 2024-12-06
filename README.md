# Hi there 👋

I'm Tracy Lee,
# Studying MBA from University Canada West,
# Vancouver, BC.

# Project 1.

# Project Introduction

The primary objective of this project is to develop a comprehensive Data Analytics Platform (DAP) using AWS services to analyze the Public Art – Artists dataset from Vancouver's open data portal. The project focuses on applying structured processes for data ingestion, profiling, cleaning, and creating a robust ETL pipeline to generate actionable insights. By leveraging AWS tools such as S3, Glue DataBrew, and Glue, the platform is designed to streamline data preparation and visualization, ultimately enabling a deeper understanding of artists' contributions across various nations represented in Vancouver.

---

# Objectives

The main objectives of the project are as follows:
1. **Data Ingestion**: To collect and organize structured datasets from the source into a raw bucket for processing.
2. **Data Profiling**: To evaluate the quality and completeness of the dataset using AWS Glue DataBrew and address inconsistencies.
3. **Data Cleaning**: To clean and transform the dataset by handling missing values, removing duplicates, and ensuring format standardization.
4. **Pipeline Design**: To create an ETL pipeline that groups and analyzes data based on specific parameters such as country, providing insightful outputs stored in a curated bucket.
5. **Exploratory Analysis**: To gain detailed insights into a specific subset of the data (e.g., Canadian artists) by filtering and visualizing relevant patterns.

---

# DAP Design and Implementation (Individual work – Tracy)

For my contribution, I selected the Public Art – Artists dataset from [Open Data Vancouver](https://opendata.vancouver.ca/explore/dataset/public-art-artists/information/).

## Original Dataset
**Figure 1**  

<img width="656" alt="Screenshot 2024-12-05 at 5 38 57 PM" src="https://github.com/user-attachments/assets/8cce7829-c063-4f5f-9b8e-3e68db59280a">


Original Dataset  

---

## Descriptive Analysis

The primary purpose of doing descriptive analysis on the supplied data was to determine which nation has the most artists in the city of Vancouver. Analyzing this on the Open Data Vancouver website yields the column chart below, with Canada having the most artists (346), followed by the United States (15). This graph should represent the goal of our Data Analytics method, and the results from all four processes should match this graph.

**Figure 2**  

<img width="675" alt="Screenshot 2024-12-05 at 5 39 04 PM" src="https://github.com/user-attachments/assets/e52de962-5512-4f34-93bd-9fe581bc608d">

A column chart indicates the overall number of artists from every country.

---

## Data Storage

Three buckets have been created for storing the data, namely:
- `pa-artists-raw-tracy`
- `pa-artists-trf-tracy`
- `pa-artist-cur-tracy`

**Figure 3**  

<img width="649" alt="Screenshot 2024-12-05 at 5 39 11 PM" src="https://github.com/user-attachments/assets/a0d4688a-9a50-45ab-bf79-50faa9eb1745">

Creation of three buckets

---

## Draw IO
**Figure 4**  

<img width="701" alt="Screenshot 2024-12-05 at 5 48 33 PM" src="https://github.com/user-attachments/assets/7e6faa45-1eb5-4659-bcba-e2c80273351b">

Screenshot of the Data Analytics Platform (DAP) using Draw.io

Amazon S3, AWS Glue DataBrew, and AWS Glue were the AWS services utilized in the development of this DAP. The installation of several buckets and procedures is depicted in the above diagram. Data is first ingested into an AWS raw bucket in this configuration. After that, it is processed using DataBrew, where cleaning and profiling are done. A transformed (`trf`) bucket contains the processed output. This data is then used by an ETL (Extract, Transform, Load) pipeline to generate final outputs, which are then stored in a curated bucket with two folders—system and user—for use in accordance with particular needs.

---

### Step 1: Data Ingestion

The initial step in constructing any DAP is to obtain a structured dataset from the source. Data can be uploaded into the raw bucket using either Excel or CSV format; however, Excel is better suited to our purpose.

**Figure 5**  

<img width="650" alt="Screenshot 2024-12-05 at 5 48 40 PM" src="https://github.com/user-attachments/assets/fe93c1c5-f58d-48b0-9cf2-6abf2b4482a6">

Uploading Excel file into the raw bucket

---

### Step 2: Data Profiling

After feeding the data, the next stage is data profiling, which is performed using the AWS 'Glue Data Brew' service. It is done to understand the quality of the data ingested and make modifications as needed. First, a dataset is constructed to establish a connection between the two services. We then initiate the profiling process by creating projects and recipe jobs.

**Figure 6**  

<img width="644" alt="Screenshot 2024-12-05 at 5 48 47 PM" src="https://github.com/user-attachments/assets/9e7317fb-6185-49c1-a4dc-4c606165c06e">

Creating a Dataset in AWS Data Brew  

**Figure 7**  

<img width="645" alt="Screenshot 2024-12-05 at 5 48 54 PM" src="https://github.com/user-attachments/assets/1a19ec9d-7e3f-40ea-837b-a1c8d9235b34">

Recipe Jobs  

---

### Step 3: Data Cleaning

This method involves cleansing data before analyzing it. This entails multiple processes, including managing missing data, removing duplicates, and resolving formatting difficulties. My dataset contained a large number of 'null' values in the 'Country' columns, as well as a few extra columns that were not required to achieve the intended results. The null values were replaced with 'No Country'. The cleaned data is subsequently placed in the 'data-cleaning' folder of the `trf` bucket.

**Figure 8**  
<img width="639" alt="Screenshot 2024-12-05 at 5 49 02 PM" src="https://github.com/user-attachments/assets/0435f220-13ad-4b7f-b5eb-b2798e4f8d0c">

Cleaning the Data  

**Figure 9**  

<img width="645" alt="Screenshot 2024-12-05 at 5 49 09 PM" src="https://github.com/user-attachments/assets/61ab02cd-9097-4a1d-90a7-e9db6654bbf3">

Storing the clean data in S3  

---

### Step 4: Data Pipeline Design

A pipeline is used to execute ETL (Extract, Transform, Load) operations on the transformed data from Steps 2 and 3. The result of this process is known as analytical data. In our scenario, the first step is to retrieve the cleaned data from the transform bucket and begin the process of removing columns that are unnecessary for the outcomes. Following this, the count function is used to determine the overall number of artists by grouping them by country. This data is kept in two folders generated in the curated bucket: one for the system and one for the user.

**Figure 10**  

<img width="642" alt="Screenshot 2024-12-05 at 5 49 16 PM" src="https://github.com/user-attachments/assets/4487e848-faf1-4ab4-8c29-b8325ea65d6e">


**Figure 11**  

<img width="362" alt="Screenshot 2024-12-05 at 5 49 23 PM" src="https://github.com/user-attachments/assets/4019943c-3e3f-4527-b7ed-e13974443884">

Final Result  

---

## Exploratory Analysis

For the Explanatory Analysis, I gathered a list of artists and their information from a given country. Due to dataset limits, I chose 'Canada'. This would provide information about Canadian artists. This type of study assesses the dataset's quality while also giving light on broader implications for how artists' contributions are appreciated and conserved around the world. The following figure was the intended outcome of my 'Exploratory Analysis'.

**Figure 12**  

<img width="516" alt="Screenshot 2024-12-05 at 5 49 28 PM" src="https://github.com/user-attachments/assets/955d64a1-5631-4748-b921-e7f5f2a9362e">

---

## Draw.io

This DAP platform introduces a new pipeline for comparing artists from specific countries. In this example, Canada.

**Figure 13**  

<img width="715" alt="Screenshot 2024-12-05 at 5 49 34 PM" src="https://github.com/user-attachments/assets/9c57f018-9f0e-483d-ba89-3de677a652a0">


---

### Step 1: Data Ingestion

Fetching and ingesting unprocessed data from the source.

**Figure 14**  

<img width="583" alt="Screenshot 2024-12-05 at 5 49 40 PM" src="https://github.com/user-attachments/assets/ed3c63c6-c128-4b6f-8413-f9d406032c20">

---

### Step 2: Data Profiling

AWS Glue DataBrew does data profiling to determine data quality and saves the results to the modified S3 bucket.

**Figure 15**  

<img width="569" alt="Screenshot 2024-12-05 at 5 49 46 PM" src="https://github.com/user-attachments/assets/1bd4b2f4-9b38-4739-88dc-2d836753c677">

---

### Step 3: Data Cleaning

**Figure 16**  

<img width="543" alt="Screenshot 2024-12-05 at 5 49 53 PM" src="https://github.com/user-attachments/assets/9e7fb2ef-20aa-478e-9d4a-94a8169a380c">


---

### Step 4: Data Pipeline Design

Instead of using ‘Aggregate’ in the ETL pipeline, I used the ‘Filter’ option, and matched the results based on the value ‘Canada’ for exploratory analysis.

**Figure 17**  

<img width="487" alt="Screenshot 2024-12-05 at 5 49 58 PM" src="https://github.com/user-attachments/assets/cea1577c-3ea2-40b0-b683-42b6c848dd5b">


**Figure 18**  

<img width="468" alt="Screenshot 2024-12-05 at 5 50 03 PM" src="https://github.com/user-attachments/assets/ea9859b7-9a79-4cc4-b6fd-fe97ec2420fe">

Final Result

# Results Interpretation

The results of the descriptive analysis revealed that **Canada** has the most significant number of artists contributing to public art in Vancouver, with 346 entries in the dataset. This finding aligns with expectations, given Canada's geographical and cultural proximity to the city. The exploratory analysis further refined this by examining Canadian artists' information, providing a deeper understanding of their contributions. By leveraging AWS services, the platform successfully processed, cleaned, and analyzed the dataset to generate clear visual outputs, such as country-wise artist distributions and focused insights into selected subsets.

The effective design of the ETL pipeline ensured that unnecessary data was excluded, and the structured results were stored in user-friendly formats for future analysis or reporting.

---

# Conclusion

This project demonstrates the power of AWS tools in building an efficient Data Analytics Platform to process and analyze complex datasets. By systematically addressing data ingestion, profiling, cleaning, and transformation, the project achieved its objectives of deriving actionable insights from Vancouver's Public Art – Artists dataset. The analysis highlights the dominance of Canadian artists in the dataset while showcasing the platform's scalability for similar data-driven projects. This methodology can serve as a blueprint for future analytics initiatives, emphasizing the value of integrating technology and structured processes for impactful data exploration.

