# 📊 Employee Survey Analysis - Capstone Project

## Project Overview

This project analyzes employee engagement survey data from **Pierce County, Washington** to uncover insights about workplace satisfaction, identify patterns across departments, and provide actionable recommendations for improving employee experience.

### 📌 Key Deliverables
- **14,725** survey responses analyzed
- **10** engagement metrics evaluated
- **21** departments assessed
- **3** strategic questions answered
- **5** key recommendations provided

### 🎯 Business Questions
1. Which survey questions did respondents agree with or disagree with most?
2. Do you notice any patterns or trends within departments or roles?
3. What steps should be taken to improve employee satisfaction?

---

## 📁 Project Structure

```
employee-survey-analysis/
│
├── 📊 data/
│   ├── raw/
│   │   └── Employee_Survey_Responses.xlsx
│   └── processed/
│       └── Clean_Survey_Data.xlsx
│
├── 📈 analysis/
│   ├── 01_data_cleaning.xlsx
│   ├── 02_pivot_analysis.xlsx
│   └── 03_visualizations.xlsx
│
├── 📄 reports/
│   ├── Executive_Summary.pdf
│   └── Final_Report.docx
│
└── 📝 README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Microsoft Excel with Power Query and Power Pivot
- Basic understanding of pivot tables and data analysis
- Access to the [dataset](https://docs.google.com/spreadsheets/d/1nbhfp2ModgqDAPveYQG9CknRw2PYJQxbOTs3xSKOB8E/edit#gid=61186505)

### Tools Used
- **Excel Power Query** - Data cleaning and transformation
- **Power Pivot** - Advanced data modeling
- **Pivot Tables** - Data aggregation and analysis
- **Conditional Formatting** - Heatmap visualizations

---

## 📋 Step-by-Step Implementation Guide

### Phase 1: Data Acquisition & Setup

#### Step 1.1: Download the Dataset
1. Access the [Pierce County Employee Survey Dataset](https://docs.google.com/spreadsheets/d/1nbhfp2ModgqDAPveYQG9CknRw2PYJQxbOTs3xSKOB8E/edit#gid=61186505)
2. Download as Excel file (.xlsx)
3. Save to your `data/raw/` folder

#### Step 1.2: Initial Data Review
1. Open the dataset in Excel
2. Review the structure:
   - **14,725 rows** (responses)
   - **10 columns** (fields)
3. Note the key fields:
   - Department
   - Role (Manager, Supervisor, Individual Contributor, Director, Others)
   - Survey questions (Likert scale 1-5)

---

### Phase 2: Data Cleaning with Power Query

#### Step 2.1: Load Data into Power Query
```excel
Data Tab → Get Data → From File → From Workbook
```

#### Step 2.2: Apply Cleaning Transformations
1. **Remove Duplicates**
   ```
   Home → Remove Rows → Remove Duplicates
   ```

2. **Standardize Column Headers**
   - Rename columns for consistency
   - Remove special characters
   - Apply proper case

3. **Handle Missing Values**
   - Identify incomplete responses
   - Create "Unspecified" category for missing roles
   - Preserve valid partial responses

4. **Consolidate Role Columns**
   ```powerquery
   = Table.AddColumn(Source, "Role", each 
     if [Manager] = 1 then "Manager"
     else if [Supervisor] = 1 then "Supervisor"
     else if [Director] = 1 then "Director"
     else if [Individual_Contributor] = 1 then "Individual Contributor"
     else "Others")
   ```

5. **Close & Load**
   - Load to new worksheet named "Clean_Data"

---

### Phase 3: Analysis Setup

#### Step 3.1: Create Response Rate Calculations

1. **Add Calculated Columns**
   ```excel
   =COUNTIFS(Department_Range, A2, Status_Range, "Completed")
   ```

2. **Calculate Department Response Rates**
   ```excel
   Response_Rate = Completed / Total_Invited * 100
   ```

3. **Create Response Rate Summary Table**

| Department | Answered | Completed | Response Rate |
|------------|----------|-----------|---------------|
| Human Resources | 270 | 269 | 100% |
| Finance | 1095 | 1093 | 100% |
| District Court | 420 | 418 | 100% |

#### Step 3.2: Calculate Average Scores

1. **Department-Level Averages**
   ```excel
   =AVERAGEIFS(Score_Range, Department_Range, "Department_Name", 
               Question_Range, "Question_Text")
   ```

2. **Role-Level Averages**
   ```excel
   =AVERAGEIFS(Score_Range, Role_Range, "Role_Name", 
               Question_Range, "Question_Text")
   ```

---

### Phase 4: Create Pivot Tables

#### Step 4.1: Department Analysis Pivot

1. **Insert Pivot Table**
   ```
   Insert → PivotTable → Select "Clean_Data"
   ```

2. **Configure Fields**
   - Rows: Department
   - Columns: Survey Questions
   - Values: Average of Response (Likert Score)

3. **Apply Formatting**
   - Number format: 2 decimal places
   - Apply color scale (Red-Yellow-Green)

#### Step 4.2: Role Analysis Pivot

1. **Create Second Pivot**
   - Rows: Role
   - Columns: Survey Questions
   - Values: Average of Response

2. **Add Slicers**
   - Department slicer for filtering
   - Question category slicer

---

### Phase 5: Visualizations

#### Step 5.1: Create Heatmap

1. **Select Pivot Table Data**
2. **Apply Conditional Formatting**
   ```
   Home → Conditional Formatting → Color Scales → Red-Yellow-Green
   ```
3. **Adjust Scale**
   - Minimum: 1.0 (Red)
   - Midpoint: 3.0 (Yellow)
   - Maximum: 5.0 (Green)

#### Step 5.2: Build Key Charts

1. **Response Rate Bar Chart**
   ```
   Insert → Charts → Clustered Bar
   X-axis: Department
   Y-axis: Response Rate %
   ```

2. **Top/Bottom Performers**
   ```
   Insert → Charts → Horizontal Bar
   Show top 5 and bottom 5 departments
   ```

3. **Question Performance Spider Chart**
   ```
   Insert → Charts → Radar Chart
   Categories: Survey Questions
   Series: Department Averages
   ```

---

### Phase 6: Key Insights Extraction

#### Step 6.1: Identify Engagement Drivers

**Top Performing Questions** (Average > 3.4)
- "I know what is expected of me at work" - 3.48
- "My supervisor seems to care about me" - 3.26
- "I can do what I do best every day" - 3.11

**Top Performing Departments**
- Family Justice Centre - 3.51
- Emergency Management - 3.37
- Economic Development - 3.32

#### Step 6.2: Identify Pain Points

**Lowest Scoring Questions** (Average < 2.5)
- "I have a best friend at work" - 2.27
- "I receive recognition for good work" - 2.85
- "Opportunities to learn and grow" - 3.08

**Departments Needing Support**
- Sheriff's Department - 2.40
- Parks and Recreation - 2.90
- District Court - 2.91

---

### Phase 7: Recommendations Dashboard

#### Step 7.1: Create Summary Tables

1. **Pain Points Summary**
   ```excel
   | Question | Avg Score | Lowest Dept | Action Required |
   |----------|-----------|-------------|-----------------|
   | Best friend at work | 2.27 | Assessor's Office | Team building |
   | Recognition | 2.85 | Sheriff's Dept | Recognition program |
   ```

2. **Strengths Summary**
   ```excel
   | Question | Avg Score | Top Dept | Best Practice |
   |----------|-----------|----------|---------------|
   | Role clarity | 3.48 | Emergency Mgmt | Document process |
   | Purpose alignment | 3.09 | Medical Examiner | Scale approach |
   ```

---

## 📊 Key Findings

### ✅ Strengths
1. **99% average response rate** - Strong engagement with survey process
2. **Role clarity** - Employees understand expectations (3.48/5.00)
3. **Supervisor support** - Managers show care for employees (3.26/5.00)

### ⚠️ Areas for Improvement
1. **Social connections** - Weak interpersonal bonds (2.27/5.00)
2. **Recognition gaps** - Inconsistent praise and feedback (2.85/5.00)
3. **Development opportunities** - Uneven access to growth (3.08/5.00)

### 🎯 Pattern Analysis
- **High performers**: Small, specialized departments (Family Justice, Emergency Management)
- **Low performers**: Large operational departments (Sheriff's, Parks & Recreation)
- **Role patterns**: Directors struggle with social connections; Individual contributors lack recognition

---

## 💡 Strategic Recommendations

### 1. Strengthen Recognition Systems
- Implement monthly one-on-one check-ins
- Launch peer recognition platform
- Train managers on feedback delivery

### 2. Foster Social Connections
- Organize quarterly team mixers
- Create cross-departmental projects
- Establish mentorship programs

### 3. Expand Learning Opportunities
- Develop department-specific training roadmaps
- Promote internal mobility programs
- Offer role-specific development paths

### 4. Improve Change Communication
- Implement bi-weekly strategy bulletins
- Host department-level briefings
- Maintain centralized change log

### 5. Scale Best Practices
- Document success stories from top departments
- Conduct leadership workshops
- Share internal case studies

---

## 📈 Expected Outcomes

By implementing these recommendations:
- **Increase overall satisfaction** from 3.06 to 3.50+ within 12 months
- **Improve retention** in low-scoring departments by 15%
- **Strengthen engagement** scores by 20% in bottom quartile departments

---

## 🔄 Next Steps

1. **Month 1-2**: Present findings to leadership
2. **Month 3-4**: Pilot interventions in 3 departments
3. **Month 5-6**: Measure initial impact
4. **Month 7-8**: Scale successful initiatives
5. **Month 9-12**: Conduct follow-up survey

---

## 📝 Technical Notes

### Formulas Used

**Response Rate Calculation**
```excel
=COUNTIFS(Table1[Department],A2,Table1[Status],"Completed")/
 COUNTIFS(Table1[Department],A2,Table1[Status],"<>")
```

**Average Score by Department**
```excel
=AVERAGEIFS(Table1[Score],Table1[Department],A2,Table1[Question],B$1)
```

**Conditional Formatting for Heatmap**
```excel
Rule Type: 3-Color Scale
Minimum: =1, Red
Midpoint: =3, Yellow
Maximum: =5, Green
```

---

## 📚 Resources

- [Original Dataset](https://docs.google.com/spreadsheets/d/1nbhfp2ModgqDAPveYQG9CknRw2PYJQxbOTs3xSKOB8E/edit#gid=61186505)
- [Excel Power Query Documentation](https://support.microsoft.com/en-us/office/about-power-query-in-excel-7104fbee-9e62-4cb9-a02e-5bfb1a6c536a)
- [Pivot Table Best Practices](https://support.microsoft.com/en-us/office/create-a-pivottable-to-analyze-worksheet-data-a9a84538-bfe9-40a9-a8e9-f99134456576)

---

## 👤 Author

**Halimat Ariyo**  
Data Analyst | Digitaley Drive  
[LinkedIn Profile] | [Portfolio]

---

## 📄 License

This project is part of the Digitaley Drive Capstone Program and is for educational purposes.

---

*Last Updated: 2024*