# School-District-Analysis

## Resources
Data Source: schools_complete.csv, students_complete.csv
Software: Anaconda 4.11.0

'Overview of the school district analysis: Explain the purpose of this analysis.

## Overview
I was tasked with analyzing the school district data for look for trends in students' math and reading scores based on school size, school type (Charter or Public), per-student spending, and grade. After completing the initial analysis of the school district data I learned that the reading and math scores for 9th graders at Thomas High School have been altered and must not be considered in the data analysis.

### Process
The first step in the data analysis was to clean the data. The student data included some erroneous information such as "Mr." or "Dr." before a first name, or "DVM" or "PhD" after the last name. After importing the data, I iterated through the student names, looking for erroneous suffices and prefixes and replacing those with an empty string.

```python
# Add each prefix and suffix to remove to a list.
prefixes_suffixes = ["Dr. ", "Mr. ","Ms. ", "Mrs. ", "Miss ", " MD", " DDS", " DVM", " PhD"]

# Iterate through the words in the "prefixes_suffixes" list and replace them with an empty space, "".
for word in prefixes_suffixes:
    student_data_df["student_name"] = student_data_df["student_name"].str.replace(word,"")
```
Once that was complete, the next step was to remove the math and reading scores for 9th graders at Thomas High School and replace them with "NaN" so they will not be included in the district analysis.

```python
# Use the loc method on the student_data_df to select all the reading scores from the 9th grade at Thomas High School and replace them with NaN.
student_data_df.loc[(student_data_df["grade"]=="9th") & (student_data_df["school_name"]=="Thomas High School"),"reading_score"] = np.nan

#  Refactor the code in the above step to replace the math scores with NaN.
student_data_df.loc[(student_data_df["grade"]=="9th") & (student_data_df["school_name"]=="Thomas High School"),"math_score"] = np.nan
```
I next merged the student data and the school data into a dataframe that included all of the district data. The dataframe looked like this:
****Insert Dataframe.png here



## Results
`Using bulleted lists and images of DataFrames as support, address the following questions.

- By removing the THS 9th graders' math and reading scores, the percent of all kids in the district passing math, passing reading, and the overall passing percentage was lowered by 0.2-0.3 percentage points. The following images show the district summary before and after removing the scores.

*** image of DF before
*** image of DF after

'How is the school summary affected?
'How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?
'How does replacing the ninth-grade scores affect the following:
  'Math and reading scores by grade
  'Scores by school spending
  'Scores by school size
  'Scores by school type

### How the change in data affected the school district metrics
- Include bulleted list addressing how each of the seven school district metrics was affected by the changes in the data

## Summary

'Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.

### Summary of change in analysis
- Include a statement summarizing four changes to the school district analysis after reading and math scores have been replaced
