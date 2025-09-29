#  Employee Survey Analysis - Capstone Project

## Project Overview

This project analyzes employee engagement survey data from **Pierce County, Washington** to uncover insights about workplace satisfaction, identify patterns across departments, and provide actionable recommendations for improving employee experience.

###  Key Deliverables
- **14,725** survey responses analyzed
- **10** engagement metrics evaluated
- **21** departments assessed
- **3** strategic questions answered
- **5** key recommendations provided

### Business Questions
1. Which survey questions did respondents agree with or disagree with most?
2. Do you notice any patterns or trends within departments or roles?
3. What steps should be taken to improve employee satisfaction?



##  Project Structure

```
employee-survey-analysis/
│
├──  data/
│   ├── raw/
│   │   └── Employee_Survey_Responses.xlsx
│   └── processed/
│       └── Clean_Survey_Data.xlsx
│
├──  analysis/
│   ├── 01_data_cleaning.xlsx
│   ├── 02_pivot_analysis.xlsx
│   └── 03_visualizations.xlsx
│
├──  reports/
│   ├── Executive_Summary.pdf
│   └── Final_Report.docx
│
└──  README.md
```

# Dataset
(https://docs.google.com/spreadsheets/d/1nbhfp2ModgqDAPveYQG9CknRw2PYJQxbOTs3xSKOB8E/edit#gid=61186505)

### Tools Used
- **Excel Power Query** - Data cleaning and transformation
- **Power Pivot** - Advanced data modeling
- **Pivot Tables** - Data aggregation and analysis
- **Conditional Formatting** - Heatmap visualizations
- **Charts**

### Data Cleaning Steps 
-Load Data into Power Query
- Remove Duplicates
- Rename columns for consistency
- Remove special characters
- Apply proper case
- Identify incomplete responses
- Create "Unspecified" category for missing roles
- Preserve valid partial responses
- Consolidate Role Columns
- Load to new worksheet named "Clean_Data"

### Analysis Setup
- Create Response Rate Calculations
- Add Calculated Columns
- Calculate Department Response Rates
- Create Response Rate Summary Table
- Calculate Average Scores
- Department-Level Averages
- Role-Level Averages  

### Create Pivot Tables
- Department Analysis Pivot
- Role Analysis Pivot
- Add Slicers
   - Department slicer for filtering
   - Question category slicer
### Visualizations

#### Create Heatmap

#### Build Key Charts
- Response Rate Bar Chart
- Top/Bottom Performers
- Question Performance Spider Chart
  
###  Key Insights Extraction

####  Identify Engagement Drivers

**Top Performing Questions** (Average > 3.4)
- "I know what is expected of me at work" - 3.48
- "My supervisor seems to care about me" - 3.26
- "I can do what I do best every day" - 3.11

**Top Performing Departments**
- Family Justice Centre - 3.51
- Emergency Management - 3.37
- Economic Development - 3.32

#### Identify Pain Points

**Lowest Scoring Questions** (Average < 2.5)
- "I have a best friend at work" - 2.27
- "I receive recognition for good work" - 2.85
- "Opportunities to learn and grow" - 3.08

**Departments Needing Support**
- Sheriff's Department - 2.40
- Parks and Recreation - 2.90
- District Court - 2.91

##  Key Findings

###  Strengths
1. **99% average response rate** - Strong engagement with survey process
2. **Role clarity** - Employees understand expectations (3.48/5.00)
3. **Supervisor support** - Managers show care for employees (3.26/5.00)

###  Areas for Improvement
1. **Social connections** - Weak interpersonal bonds (2.27/5.00)
2. **Recognition gaps** - Inconsistent praise and feedback (2.85/5.00)
3. **Development opportunities** - Uneven access to growth (3.08/5.00)

###  Pattern Analysis
- **High performers**: Small, specialized departments (Family Justice, Emergency Management)
- **Low performers**: Large operational departments (Sheriff's, Parks & Recreation)
- **Role patterns**: Directors struggle with social connections; Individual contributors lack recognition


##  Strategic Recommendations
- Strengthen Recognition Systems
- Foster Social Connections
- Expand Learning Opportunities
- Improve Change Communication
- Scale Best Practices

##  Expected Outcomes
- **Increase overall satisfaction** from 3.06 to 3.50+ within 12 months
- **Improve retention** in low-scoring departments by 15%
- **Strengthen engagement** scores by 20% in bottom quartile departments

##  Technical Notes
**Formulas Used**
- Response Rate Calculation
- Average Score by Department
- Conditional Formatting for Heatmap

## 👤 Author

**Halimat Ariyo**  
Data Analyst   
[https://www.linkedin.com/in/halimat-ariyo] 

##  License

This project is part of the Digitaley Drive Capstone Program and is for educational purposes.
