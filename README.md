# School_District_Analysis

## Overview
In this project we are tasked with preparing all standardized test data for analysis, reporting, and presenting insights about performance trends and patterns. These insights may be used to inform discussions and strategic decisions at the school and district level. Our objective is to look for relationships between student funding, and student standardized test scores. Our task is to aggregate the data and showcase trends in the districts performance. 

The PyCitySchools.ipynb file (File1) contains Python code that fulfills all of the tasks determined below. Due to a case of academic dishonesty in Thomas High School's ninth grade class, their reading and math exam scores will be rendered void. A second file, PyCitySchools_(Thomas_High_School).ipynb (File2) accounts for this. We will discuss the change in analysis results throughout this README.md.

### Tasks

-	A high-level snapshot of the district's key metrics, presented in a table format

-	An overview of the key metrics for each school, presented in a table format

-	Tables presenting each of the following metrics:

•	Top 5 and bottom 5 performing schools, based on the overall passing rate

•	The average math score received by students in each grade level at each school

•	The average reading score received by students in each grade level at each school

•	School performance based on the budget per student

•	School performance based on the school size 

•	School performance based on the type of school


### Pandas
Pandas is a Python library used for data manipulation and analysis. Commonly used with Jupyter Notebook, Pandas offers great functionality including reading raw data, cleaning and inspecting the data, merging data sets, performing calculations, and creating tables. All of these tasks are part of the data wrangling, or data “munging” process that data analysists do to clean, sort, and transform data into a format that can be more easily analyzed and used to convey information. The data wrangling process may include changing the data layout and structure, organizing the data by type, formatting rows or columns, and sorting or grouping data. Pandas is very flexible, optimized for performance, and exceeds Excel in terms of functionality.


### Method Used to Remove Data
For File2 I was tasked with removing Thomas High School’s ninth grade class exam grades. To do so, I used Pandas “.loc()” method as so:
```
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "reading_score"] = np.NaN

student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "math_score"] = np.NaN
```


## Results (by task)
Check out the files for in depth explanations of the code used for each task! Again, File1 refers to the original analysis. File2 refers to the analysis where Thomas High School’s ninth grade class exam scores are void.

### A high-level snapshot of the district's key metrics, presented in a table format

**File1**

 ![image](https://user-images.githubusercontent.com/68082808/97099368-8344e780-165e-11eb-988c-9a84f019913f.png)

**File2**

 ![image](https://user-images.githubusercontent.com/68082808/97099370-88a23200-165e-11eb-80d5-8a34fba65dc9.png)

After removing Thomas High School’s ninth grade class from the pool, the average exam scores drop slightly and so do passing rates.

### An overview of the key metrics for each school, presented in a table format

**File1**

![image](https://user-images.githubusercontent.com/68082808/97099669-da988700-1661-11eb-9302-b4386474155a.png)
 

**File2**

![image](https://user-images.githubusercontent.com/68082808/97099670-df5d3b00-1661-11eb-95cc-8e14d53a6146.png)
 

Considering we only alter exam scores for Thomas High School, metrics for other schools won’t change between files. These rows were taken from the ```per_school_summary_df``` DataFrames in their respective files. Average scores and passing percentages are scaled accordingly. Since the average assessment scores and passing percentages drop after voiding THS’s ninth grade class assessment scores, one can conclude that class was outperforming the schools average.

### Top 5 and bottom 5 performing schools, based on the overall passing rate

**File1**

![image](https://user-images.githubusercontent.com/68082808/97099763-0c5e1d80-1663-11eb-9fb9-0309385f64ef.png)
 
**File2**
 
 ![image](https://user-images.githubusercontent.com/68082808/97099768-11bb6800-1663-11eb-8600-b63dbae94d75.png)
 
Although removing THS’s ninth grade exam scores dropped their average scores and passing percentages, alterations in these metrics did not change enough to effect the districts overall passing percentage ranking. THS remains ranked second in terms of overall passing percentage.

### The average math score received by students in each grade level at each school

**File1**

 ![image](https://user-images.githubusercontent.com/68082808/97099841-fc930900-1663-11eb-994f-0fc954dc9905.png)

**File2**

 ![image](https://user-images.githubusercontent.com/68082808/97099845-0157bd00-1664-11eb-9bcd-e90af557c9d6.png)

These DataFrames are only sorted in alphabetical order of school name, there is no ranking system in these DataFrames. One can notice that THS’s ninth grade math average is “nan”. When using the loc method (find an example above), we assign all matching values to np.nan. Numpy NaN is the IEEE floating point representation of Not a Number. 

### The average reading score received by students in each grade level at each school

**File1**

![image](https://user-images.githubusercontent.com/68082808/97099973-239e0a80-1665-11eb-9487-ad9ec65ad7d7.png)

**File2**

![image](https://user-images.githubusercontent.com/68082808/97099974-28fb5500-1665-11eb-8cb8-fb3f366ff1a1.png)

The same can be said about these two data frames.

### School performance based on the budget per student

**File1**

![image](https://user-images.githubusercontent.com/68082808/97100004-a030e900-1665-11eb-981d-7ddb3ff78000.png)

**File2**

![image](https://user-images.githubusercontent.com/68082808/97100005-a4f59d00-1665-11eb-885f-7d9cd7be8a96.png)

It is interesting to observe how high schools in this district who recieved less funding per student achieved greater average math and reading exam scores, and also have a high passing count.

### School performance based on school size

**File1**

![image](https://user-images.githubusercontent.com/68082808/97100079-4b41a280-1666-11eb-8070-1bd523c71a28.png)

**File2**

![image](https://user-images.githubusercontent.com/68082808/97100083-509eed00-1666-11eb-9207-6d7b181c4662.png)

The alteration in the size of THS's student pool was so insignificant this analysis of school performance based on school size was practically unaffected. Small and Medium sized schools outperform Large schools in every metric.

### School performance based on the type of school

**File1**

![image](https://user-images.githubusercontent.com/68082808/97100240-cbb4d300-1667-11eb-9612-78afbcf0e037.png)

**File2**

![image](https://user-images.githubusercontent.com/68082808/97100234-b63fa900-1667-11eb-8d96-7c0badf11e70.png)

Charter schools outperform District schools on every metric. Based on the results found above, it must be the case that District schools are better funded than Charter schools in this municipality. If one looks at the ```per_school_summary_df``` in either file, District schools are in fact better funded than Charter Schools.

## Summary

When having to clean data, especially when it comes to handling missing data, there are three choices an analyst chooses from.

- **Do Nothing:** If we do nothing, when we sum or take the averages of the reading and math scores, those NaNs will not be considered. However if we multiply or divide with a row that has a NaN, the answer will be NaN. This may cause problems.

- **Drop the rows where there are NaNs:** This can cause problems later if there is data in the other rows that we need. Before dropping rows with NaN, you should ask yourself how much data would be removed if NaNs are dropped, and how it would impact analysis.
```
\# Drop the NaNs
missing_grade_df.dropna()
```

- **Fill in the row:** We can choose to fill in the row. Filling in an empty row must be used with caution, adding irrelevant data may impact arithmetic calculations.
```
\# Fill in the empty rows with "85"
missing_grade_df.fillna(85)
```

In File2 we decide to simply negate an entire grades assessment answers to preserve the integrity of the school districts research. This may not be the most appropriate decision to make in every situation, but it works in this circumstance just fine. Nonetheless, after the change in the dataset, data analysis changed.

1. After removing Thomas High School’s ninth grade class from the pool, the average exam scores drop slightly and so do passing rates.

2. Since the average assessment scores and passing percentages drop after voiding THS’s ninth grade class assessment scores, one can conclude that class was outperforming the schools average.

3. Although removing THS’s ninth grade exam scores dropped their average scores and passing percentages, alterations in these metrics did not change enough to effect the districts overall passing percentage ranking. THS remains ranked second in terms of overall passing percentage.

4. The alteration in the size of THS's student pool was so insignificant this analysis of school performance based on school size was practically unaffected. 

After the alterations, an analyst may find discrepancies in data regarding Thomas High School. However, these changes are too insignificant to create any significant change when observing metrics at a district wide scale. 
