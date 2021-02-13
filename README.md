# Project_Name_Placeholder
*Collaborators: Kate Bessonova-Belmont, Sy Flores, Jade Jimenez, Benjamin Wankmuller*

---

## **Table of Contents**
- [Abstract](#abstract)
- [Body](#body)
  - [Data](#data)
  - [Methodology](#methodology)
  - [Analysis](#analysis)
  - [Results](#results)
- [Conclusion](#conclusion)
- [Sources](#sources)

---

## Abstract
Lifestyle exposure theory posits that persons with certain demographic profiles are more prone to experience criminal victimization because their lifestyles expose risky situations. This logic suggests that the well‐established relationship between demographic characteristics, such as gender, and victimization, is fully mediated by lifestyles and exposure to risk. To date, empirical studies have found consistent support for the theory, particularly with respect to personal and property victimization . (Source: Lifestyle Exposure Theory of Victimization, Aries Madero-Hernandez, Encyclopedia of Women and Crime, First Published 23 August 2019)


## Body

### Data 
1. Bureau of Justice National Crime Victimization Survey (NCVS) API
2. Dow Jones Industrial Average Data from Yahoo Finance
DJI Open, High, Low, Close and Volume data for each day since 1993
Chosen datasets are from well-established sources. Both govwrnment crime datat and stock results have been documented extensively throughout the years.
These data sources are reliable and easily obtainable

### Methodology
1. Importing Data
2. Data Exploration
3. Data Cleaning throughout the EDA process
+++ Data Cleaning Process Description, Creating New Data Frames Process Discription
4. Plotting was created using matplotlib notebook and matplotlib inline 

### Analysis
Research Questions include:
1. Does the performance of the stock market correlate with crime in the United States?
2. Are certain age groups more likely to be victims of certain crimes?
3. Have victimization rates changed over time?

### Results
**Research results and further reasearch development:** 
From what we are able to see, in years where the DJI had a poor performance, victimization rates showed increases at times for the following year for ages 34 to 49
While not apparent as to how these may be related, it suggest sufficient evidence between the two variables to warrant further investigation
Supplemental data sources would be required to properly assess these trends among the observed demographics
Daily victimization rates of a representative sample would be a more appropriate for making strong conclusions.

To better understand what we are seeing, we would have to reassess why stock performance one year would influence victimization rates the following year for ages 34 to 49
Run tests to see if a statistically significant correlation exists
Identify a more appropriate crime dataset:
1. Daily crime rates
2. Balanced aged


## Conclusion
**
---

## Sources
1. Bureau of Justice National Crime Victimization Survey (NCVS) API https://www.bjs.gov/developer/ncvs/personalFields.cfm#ethnic1R
2. Dow Jones Industrial Average (^DJI) Historical Data - Yahoo Financehttps://finance.yahoo.com/quote/%5EDJI/history/

## **Development**
Our analysis will accomplish the following:
- Use Pandas to clean and format our datasets
- Create a Jupyter Notebook describing our data exploration and cleanup process
- Create a Jupyter Notebook illustrating the final data analysis
- Use Matplotlib to create 6-8 visualizations of our data (2 for each question we ask of our data)
- Output our visualizations as PNG images and in include them in our presentation
- We may use at least one API, if you can find an API with data pertinent to our primary research questions.
- Create a write-up summarizing our major findings
  - One heading for each primary research question with a short description of our findings with relevant plots
  
## **Presentation**
Our presentation will adhere to the following guidelines:
- Approximately 10 minutes in length
- Contain the source for the data used to answer our primary research questions
- Contain the data exploration and cleanup process (Jupyter Notebook)
- Contain the analysis process (Jupyter Notebook)
- Contain our conclusions, including a numerical summary and visualizations of that summary
- Contain the implication of our findings and what it means
