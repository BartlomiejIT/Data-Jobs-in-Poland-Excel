# Data Jobs Analysis

## Objective

As a former job seeker, I’ve always been surprised by the lack of data exploring the most optimal jobs and skills in the data science market. I set out to understand what skills top employers request and how to land more pay.

## Key Questions

To understand the data science job market, I asked the following:

1. Do more skills get you better pay?
2. What are the top skills of data professionals in Poland?
3. What’s the pay for the top 10 skills in Poland?

## Excel tools:

The following Excel skills were utilized for analysis:

- Pivot Tables
- Pivot Charts
- DAX (Data Analysis Expressions)
- Power Query
- Power Pivot

## Data Source and Contain

The dataset used for this project contains real-world data science job information from 2023. The dataset is from [hugginface](https://huggingface.co/datasets/lukebarousse/data_jobs).   

It includes detailed information on:

- Job titles
- Salaries
- Countries
- Skills

## Analysis

### 1. Do more skills get you better pay?

#### Power Query (ETL)

**Extract**:

- I first used Power Query to extract the original data `data_salary_all.xlsx` and create two queries:
- First one with all the data jobs information.
- The second listing the skills for each job ID.
  
**Transform**:

- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.

  - data_jobs_salary:

  ![image](https://github.com/user-attachments/assets/2dc14dbd-d227-48ca-b504-614e4fca1c11)


  - data_jobs_skills:

  ![image](https://github.com/user-attachments/assets/e5cd241a-4ac2-4e56-bc8a-ecc4e0022da2)


**Load**:

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.

  - data_jobs_salary:

  ![image](https://github.com/user-attachments/assets/43b7aaba-9ab6-4f8c-a7eb-5f85b863215d)

  - data_jobs_skills:

  ![image](https://github.com/user-attachments/assets/ccdc3b58-8d05-463f-b847-cb53a2b7e87f)

#### Key Insights:

- There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.

- Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.

  ![image](https://github.com/user-attachments/assets/41f7c2ae-605e-42c1-bf6a-bc5b282fb2c2)


  - This trend emphasizes the value of acquiring multiple relevant skills, particularly for individuals aiming for higher-paying roles.

### 2. What are the top skills of data professionals in Poland?

#### Power Pivot:

I created a data model by integrating the ```data_jobs_salary``` and ```data_jobs_skills``` tables into one model.
Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

- Data Model:

    - I created a relationship between my two tables using the ```job_id``` column.

    ![image](https://github.com/user-attachments/assets/e3d42a07-d466-4dc8-bcf0-d600234917a4)


- Power Pivot Menu:

    - The Power Pivot menu was used to refine my data model and makes it easy to create measures.

    ![image](https://github.com/user-attachments/assets/35bb6f3e-2fc2-4697-991b-63aa58e7a724)

#### Key Insights:

- SQL and Tableau or Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing, analysis and visualization.

- Emerging technologies like Azure and AWS also show significant presence, underlining the industry's shift towards cloud services and big data technologies.
  
  ![image](https://github.com/user-attachments/assets/c51c98d7-37c7-47c1-8cf6-7fa8c748515c)

  - Understanding prevalent skills in the industry not only helps professionals stay competitive but also guides training and educational programs to focus on the most impactful technologies.

### 3. What's the pay of the top 10 skills in Poland?

#### PivotTables & DAX:

**Pivot Table**

- I created a PivotTable using the Data Model I created with Power Pivot.
- I moved the ```job_title_short``` to the rows area and ```salary_year_avg``` into the values area.
- Then I added new measure to calculate the median salary for Poland jobs.

  ```
  =CALCULATE(
      [Median Salary],
      CROSSFILTER(data_job_salary[job_id], data_job_skills[job_id], Both),
      data_job_salary[job_country] = "Poland"
  )
  ```

**DAX**

- To calculate the median year salary I used DAX.

  ```
  Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
  ```

#### Key Insights:

- Higher median salaries are associated with skills like Azure, AWS, Power BI or Tableau suggesting their critical role in high-paying tech jobs.

- Skills like Excel and SAS have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.

  ![image](https://github.com/user-attachments/assets/5383ab03-7d83-4426-9fe9-ecfbdf9ada47)

  - This chart highlights the importance of investing time in learning high-value skills like AWS and Power BI which are evidently tied to higher paying roles, especially for those looking to maximize their salary in the tech industry.

## Conclusion

As a data enthusiast and former job seeker, I embarked on this Excel-based project to uncover valuable insights about the data science job market. Using a dataset I've curated from real-world job postings, I analyzed job titles, salaries, locations and essential skills. By leveraging Excel features like Power Query, PivotTables, DAX and charts, I discovered key correlations between multiple skills and higher salaries particularly in Azure, Power BI or Tableau and cloud technologies.















