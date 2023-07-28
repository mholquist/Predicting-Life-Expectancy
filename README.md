
# Final Project: Predicting Life Expectancy and Quality of Life
### Machine Learning Foundations with Python (90-803)
#### Spring 2023

Note: These files were part of a group project with 3 main questions, my work focused primarily on the first question, so that is what is included in this repository. 

### Research Questions
1. **How can we predict life expectancy and which factors are most influential in this prediction?**

    - The target variable for this question is 'life expectancy raw value'
    
    
2. **How can we predict quality of life and which factors are most influential in this prediction (i.e., physical and mental health)?**

    - Within our dataset, there are a few variables that indicate quality of life (Based on the data documention). We will choose to create an average of the two variables that factor in both mental and physical health as our measure for quality of life. Hence our outcome here is the variable 'quality of life'
    
    
3. **How do predictors differ across states and years? Are there groups of states with similar characteristics/factors?**

    - This question does not have a target variable as we will be using unsupervised models.


---
- **Instructions:** We have 4 relevant notebooks in total. One is for data cleaning/eda and then one for each question. Please ensure you have the relevant datasets in your directory as well as any image files from the repo. 


#### Team Notes:
- **Folder Structure**: Since we had to move our data out of our git repos, our folder structure for reading in data meant that we would have a `./data` folder and a `./figures` folder in the same directory as the `final-project---data-cleaning-team18_ks_mh_qa` directory you will get when you clone our repo. That is why you will see our relative paths reference, for example, `../data/[filename]`.
- **NA Imputation**: As discussed in our notebook, one of the primary issues with our dataset is that there are many columns with missing values at the county level. 
- For columns with > 20% missing values: For those columns with a high percentaage of missing values, we examined if they were missing on a county level and whether it was the same counties consistently missing the data. Unfortunately we found that it was the same counties with these missing values each year, but some counties are not missing all of these columns they're only missing 1. For example it might just be they are missing homicides and have full data for the rest of the columns. Therefore, If we were to drop specific counties based on which had missing values, it would remove too much data. For these reasons we are deciding to completely drop those columns with > 20% missing values, and base our models only on the data we have. This way we preserve most of the original structure of our data.

- For columns with < 20% missing values: We are choosing to impute these missing values with the average from each county.
We have data for each county in the US across 5 years. If a county is missing a particular value, they likely are missing that value for the rest of the years as well. However, not all of these counties have all years missing for every column. For those that have at least one year of data per column, we are filling with the average from other years. The alternative would be to fill the county-level missing value with the state average. However, this is an issue because counties are not necesarily representative of the rest of the state, and vice versa. We believe it would be making too many assumtions to fill the county-level data with state-level data. However, if there are counties that do not have any data for that column in any year, we will need to fill it with the state average.


- **Overall Conclusions and Future Work**
- Based on our analysis, more than general health behaviors have an impact on individuals' health. Our models found that various socioeconomic-related factors have an influence on life expectancy and quality of life. Although these results are not causal, it helps provide policymakers with an idea for where to target their policies in order to improve the overall health of their constituents. Future work related to this could involve developing more econometric (causal) models to determine exactly how some variables impact life expectancy. 
