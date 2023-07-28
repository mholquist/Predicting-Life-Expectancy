[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-8d59dc4de5201274e310e4c54b9627a8934c3b88527886e3b421487c677d23eb.svg)](https://classroom.github.com/a/Hf055y1F)
# Final Project - Data Cleaning
### Machine Learning Foundations with Python (90-803)
#### Spring 2023


**DUE DATE: Thursday, March 30th, 2023 before 11:59 PM**


---

Please read the following instructions carefully and do one submission per team!

Same as in Lab 8, make sure to join this submission as a team. In this case name your teams as follows: `team#_initalsMember1_initalsMember2_initalsMember3`

- For example: If I'm team 1 (on Canvas) and my initials are `GGS`, and my team member 2's initials are `JF`, we would name our group for this assignment: `team1_GGS_JF`.

**Remember that one of you has to create the team name on GitHub classroom and then the rest of you must join the same team**

---

### Tasks To Do

For this delivery, you must dive deeper into your datasets, by performing three main tasks:

1. Reading and Cleaning your dataset/s 

	- Explore if your dataset/s has NAs and deal with them (or provide an explanation for keeping them and how you will deal with them moving forward)
	- If you are doing a classifier take note of how many data points per class you have (and what are you going to do with them).
	- Any other necessary conversation such as dealing with categorical variables, verifying each variable is the right type.
	-  If you have more than one dataset make sure to clean ALL of your datasets!

2. Decide whether you are merging your datasets or keeping them separate.
	- If you are keeping your datasets separate provide a brief explanation of how you are going to use each dataset.
	- If you are joining your datasets check that you are not losing relevant data and you are joining your dataset correctly.

3. Provide at least two initial visualizations that describe your data. These can be a correlation plot of all the variables, a boxplot or density plots of the variables, or even a plot specific to any of the questions you are trying to tackle.

4. Define your classification or prediction variables (or none if you're doing unsupervised learning). 

5. Refine the 2-3 questions you want to answer with your datasets (based on the feedback you received from your previous assignment)

6. Do a pre-liminary test. Train a model (prediction or classification) with your clean dataset. Report how good is this initial test. You only need to do this for one of your questions.



The idea - by the end of this delivery - is to have a clean source of data that the whole team can use moving forward. If you discover you don't have enough data or the specific problem you choose is not enough for modeling then use this assignment to change your topic and datasets. You still need to submit a cleaned dataset by the end of this assignment.

---

### Submission

- Include your Jupyter Notebook/s in this repo
- Include your data inside the `data` folder
- Modify the last section of this README to include your revised questions and any additional instructions.

In each Jupyter notebook include:

- The class and assignment (first cell)
- The name of your team (first cell)
- The full names of your teammates (first cell)
- Explanations where needed for your tasks. Include enough comments and markdown cells for use to follow your cleaning process.
- Remember to only use packages we have seen in this class (or 90-800)
- A section with References at the end of the notebook


### Warnings (read carefully):

- You will receive 0 points if you do not submit your Jupyter notebook (.ipynb) and/or I'm not able to run it.
- List any references you used, even if they are one of the books assigned for this class. If this section is incomplete you will be deducted 30% of your final grade.
- If there are no comments to explain your code you will receive 0 in this assignment.

---

### Revised Questions - Please fill in
1. **How can we predict life expectancy and which factors are most influential in this prediction?**

    - The target variable for this question is 'life expectancy raw value'
    
    
2. **How can we predict quality of life and which factors are most influential in this prediction (i.e., physical and mental health)?**

    - Within our dataset, there are a few variables that indicate quality of life (Based on the data documention). We will choose to create an average of the two variables that factor in both mental and physical health as our measure for quality of life. Hence our outcome here is the variable 'quality of life'
    
    
3. **How do predictors differ across states and years? Are there groups of states with similar characteristics/factors?**

    - This question does not have a target variable as we will be using unsupervised models.


---

### Notes - Please fill in

- In this section, include any last clarification notes about your project.
- If you have more than one notebook include instructions as to how to run them (in which order) and a brief description of what each notebook has.

- **Instructions:** We have 4 relevant notebooks in total. One is for data cleaning/eda and then one for each question. Please ensure you have the relevant datasets in your directory as well as any image files from the repo. 


#### Team Notes:
- **Data Location (Google Drive)**: https://drive.google.com/drive/folders/18QuC5ONvBzFLPlFB3zF3bODFnMvrzY4N?usp=sharing
- **Folder Structure**: Since we had to move our data out of our git repos, our folder structure for reading in data meant that we would have a `./data` folder and a `./figures` folder in the same directory as the `final-project---data-cleaning-team18_ks_mh_qa` directory you will get when you clone our repo. That is why you will see our relative paths reference, for example, `../data/[filename]`.
- **NA Imputation**: As discussed in our notebook, one of the primary issues with our dataset is that there are many columns with missing values at the county level. 
- For columns with > 20% missing values: For those columns with a high percentaage of missing values, we examined if they were missing on a county level and whether it was the same counties consistently missing the data. Unfortunately we found that it was the same counties with these missing values each year, but some counties are not missing all of these columns they're only missing 1. For example it might just be they are missing homicides and have full data for the rest of the columns. Therefore, If we were to drop specific counties based on which had missing values, it would remove too much data. For these reasons we are deciding to completely drop those columns with > 20% missing values, and base our models only on the data we have. This way we preserve most of the original structure of our data.

- For columns with < 20% missing values: We are choosing to impute these missing values with the average from each county.
We have data for each county in the US across 5 years. If a county is missing a particular value, they likely are missing that value for the rest of the years as well. However, not all of these counties have all years missing for every column. For those that have at least one year of data per column, we are filling with the average from other years. The alternative would be to fill the county-level missing value with the state average. However, this is an issue because counties are not necesarily representative of the rest of the state, and vice versa. We believe it would be making too many assumtions to fill the county-level data with state-level data. However, if there are counties that do not have any data for that column in any year, we will need to fill it with the state average.


- **Overall Conclusions and Future Work**
- Based on our analysis, more than general health behaviors have an impact on individuals' health. Our models found that various socioeconomic-related factors have an influence on life expectancy and quality of life. Although these results are not causal, it helps provide policymakers with an idea for where to target their policies in order to improve the overall health of their constituents. Future work related to this could involve developing more econometric (causal) models to determine exactly how some variables impact life expectancy. 
