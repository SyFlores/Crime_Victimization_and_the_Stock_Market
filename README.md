# Crime Victimization and the Stock Market

*Collaborators: Kate Bessonova-Belmont, Sy Flores, Jade Jimenez, Benjamin Wankmuller*

---
## **Table of Contents**
- [Abstract](#abstract)
- [Repository](#repository)
- [Body](#body)
  - [Data](#data)
  - [Methodology](#methodology)
  - [Analysis](#analysis)
  - [Results](#results)
- [Conclusion](#conclusion)
- [Sources](#sources)
---
## Abstract
We operate under the assumption that economic performance, in some capacity, influences 
demographic outcomes for variables such as employment, access to education, and financial 
mobility. Certain groups of people may be affected more than others, either positively or 
negatively. We hope to investigate the potential relationship between stock market behavior and
rates of victimization. Additionally, we would like to determine which demographic victimization 
rates may be reflected in stock market behavior. While other economic indicators have a direct 
influence on or measure of variables such as unemployment or social security, the stock market's 
behavior has an obscure amount of influence as individuals throughout demographics have varying levels of: 
- Active participation - Intentional investment through active trading or portfolio management
- Passive participation - Residual effects from other market influences or unaware portfolio management through retirement accounts
This dichotomy of participation can lead to varying levels of influence from shifts in the market. 

We are looking to identify which lifestyles will be impacted most heavily by stock market behaviors.

> Lifestyle exposure theory posits that persons with certain demographic profiles are more prone to experience criminal victimization because their lifestyles expose risky situations. This logic suggests that the well‐established relationship between demographic characteristics, such as gender, and victimization, is fully mediated by lifestyles and exposure to risk. To date, empirical studies have found consistent support for the theory, particularly with respect to personal and property victimization.
> **Source: Lifestyle Exposure Theory of Victimization, Aries Madero-Hernandez, Encyclopedia of Women and Crime, First Published 23 August 2019**

## Repository
This section serves as a means to navigate the project/repository.
- **Analysis**
  - Analysis.ipynb
    - This Jupyter Notebook serves as the primary visualization and analysis file
    - This file is dependent on the data files outputted by the 'NCVS Data Cleaning.ipynb' and 'Stock Data Cleaning.ipynb' files
  - Visualization Outputs
    - These .png files are the primary visualizations used in and to drive our analysis
    - These outputs can also be viewed in the the 'Analysis.ipynb'
- **DataCleaning**
  - NCVS Data Cleaning.ipynb
  - Stock Data Cleaning.ipynb
  - Raw Data
    - Truth source .csv files (These contain no changes to data)
    - 'NCVS_Dirty.csv' and 'DowJones_Dirty.csv' files
  - Dataframe Outputs
    - These files are the cleaned as well as the groupby versions of the raw data
    - These are read into the 'Analysis.ipynb' file and serve as usuable data
    - The cleaned datasets end in "_Clean" and the groupby datasets end in "_df"
- .gitattributes
  - This file specifies which large file types we are able to upload and download
  - We currently have .csv files specified in order to upload and download the 'NCVS_Dirty.csv' file
- .gitignore
  - We currently have .py files specified in the case that we may want to obscure API files containing API keys
- README.md
  - This .md file details most documentation needed in order to interpret the project
  - For code specific documentation, .md code segments have been inserted into the 'Analysis.ipynb', 'NCVS Data Cleaning.ipynb', and 'Stock Data Cleaning.ipynb' detailing how the code functions

## Body

### Data 
1. [Personal Victimization 1993-2019 Dataset](https://www.bjs.gov/developer/ncvs/index.cfm) from Bureau of Justice Statistics, National Crime Victimization Survey

**Disclaimer:** We will largely be using definitions as noted by the Bureau of Justice Statistics as to avoid straying from the intended interpretation of the dataset.
  - Description
    - The survey provides data on violent and property victimization by select victim, household, and incident characteristics. The NCVS is the nation's(USA) primary source of information on criminal victimization. It is an annual data collection conducted by the U.S. Census Bureau for the Bureau of Justice Statistics. The NCVS collects information from a nationally representative sample of U.S. households on nonfatal crimes, reported and not reported to the police, against persons age 12 or older.
  - Notable Variables
    - **Age** (ager) - The respondent's age on the last day of the month before the interview. The NCVS collects information on household members age 12 or older.
      - 1 = 12 to 14
      - 2 = 15 to 17
      - 3 = 18 to 20
      - 4 = 21 to 24
      - 5 = 25 to 34
      - 6 = 35 to 49
      - 7 = 50 to 64
      - 8 = 65 or older
    - **Aggregate type of crime** (newcrime) - Personal victimization includes all violent victimization, rape, sexual assault, robbery, assault, and personal theft. This category includes both attempted and completed crimes. Violent victimization is defined as rape, sexual assault, robbery, aggravated assault, or simple assault. Murder is not measured by the NCVS because of an inability to question the victim. Personal theft/larceny includes purse-snatching or pocket-picking.
      - 1 = Violent victimization
      - 2 = Personal theft/larceny
    - **Weight** (weight) - The weight used to calculate an estimate of victimizations. In a calculation of victimization rate, they are used to determine the numerator. This weight also accounts for high-frequency repeat victimizations, or series victimizations, which are six or more similar but separate victimizations that occur with such frequency that the victim is unable to recall each individual event or describe events in detail. BJS has decided to count series victimizations using the victim's estimate of the number of times the victimizations occurred during the prior 6 months, capping the number within each series at a maximum of 10 victimizations. Including series victimizations in national estimates can substantially increase the number and rate of violent victimization. However, trends in violence are generally similar regardless of whether series victimizations are included.
      - For the purposes of our project, we will revisit incorporating weight into our analysis at a later point.
      - While there exists some documentation, we may need to reach out to accurately gauge how to implement using weight to offset values 
    - **Year** (year) - Valid years that have been surveyed
      - 1993-2019
  - Limitations
    - The Age variable treats all groups with equal weight, but the age ranges vary greatly from group to group. This directly causes issues when making any comparisons between these groups.
    - There only exists a Year variable. The lack of granularity doesn't allow us to more precisely identify if either a weekly, monthly or quarterly breakdown is more appropriate.
2. [Dow Jones Industrial Average Data from Yahoo Finance](https://finance.yahoo.com/quote/%5EDJI/history/)
  - The Dow Jones Industrial Average is a stock market index that measures the stock performance of 30 large blue chip companies listed on the New York Stock Exchange and NASDAQ.
    - The DJI Average is weighted such that stocks with higher prices are weighted more heavily.
    - The following are the 30 company tickers included in the DJI Average
*MMM, AXP, AMGN, AAPL, BA, CAT, CVX, CSCO, KO, DOW, GS, HD, HON, IBM, INTC, JNJ, JPM, MCD, MRK, MSFT, NKE, PG, CRM, TRV, UNH, VZ, V, WMT, WBA, DIS*
  - Variables
    - **Date** - All DJI market days from 1993 to 2019
      - Format = **Mmm DD, YYYY**
      - Markets are open Monday through Friday and closed on Saturdays and Sundays. Additionally, the following market holidays were observed and the market was closed:
        - New Year's Day, Martin Luther King Jr. Day, Washington's Birthday, Good Friday, Memorial Day, Independence Day, Labor Day, Thanksgiving Day, and Christmas Day
        - When a holiday falls on a Saturday, the market will close the preceding Friday. When a holiday falls on a Sunday, the market will close the subsequent Monday.
    - **Open** - The index open for the day
    - **High** - The highest index value in any moment of the day
    - **Low** - The lowest index value in any moment of the day
    - **Close** - The index close for the day
      - Adjusted for splits
    - **Adj Close** - The adjusted close for the day
      - Adjusted for both dividends and splits
    - **Volume**
      - The total volume of trades for the day
  - Limitations
    - There isn't a well-established indicator of market fluctation included in the dataset. This would allow us to make stronger conclusions about the effects of market changes.

Chosen datasets are from well-established sources. Both government crime data and stock results have been documented extensively throughout the years.
These data sources are reliable and easily obtainable.

### Methodology
1. Importing data from the primary data sources
2. Cleaning data and creating additional groupby datasets
3. Use cleaned data and groupby datasets to investigate noteworthy relationships between market performance and NCVS survey demographics
4. Plot these relationships using the matplotlib Python library

### Analysis
Research Questions include:
1. Does the performance of the stock market correlate with crime in the United States?
2. Are certain age groups more likely to be victims of certain crimes?
3. Have victimization rates changed over time?

### Results
**Research results and further research development:**
From our visualizations, in years where the DJI had a relatively poor performance, victimization rates often showed increases for the following year for ages 34 to 49.
While not apparent as to how these may be related, this suggests sufficient evidence to further investigate the relationship between the two variables.

## Conclusion
Supplemental data sources would be required to properly assess these trends among the observed demographics for 2 major reasons:
1. Daily victimization rates of a representative sample would be a more appropriate and provide us with a more flexible approach.
2. The age groups are grouped in an imbalanced way, partially obfuscating if which ages might be more reflective of market changes
To better understand what we are seeing, we would have to reassess why stock performance one year would influence victimization rates the following year for ages 34 to 49
Following the introduction of a supplemental data source, we can run tests to see if a statistically significant correlation exists market changes and victimization within an age group.

---

## Sources
1. [Bureau of Justice National Crime Victimization Survey (NCVS) API](https://www.bjs.gov/developer/ncvs/personalFields.cfm#ethnic1R)
2. [Dow Jones Industrial Average (^DJI) Historical Data - Yahoo Finance](https://finance.yahoo.com/quote/%5EDJI/history/)
