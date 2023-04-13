![Blue White Minimalist Travel Vlog Youtube Thumbnail](https://user-images.githubusercontent.com/100056450/231661893-49988f19-51af-4485-bfc6-4cc7230f3045.jpg)

## Problem Overview
<p align="justify">The Garment Industry is one of the key examples of the industrial globalization of this modern era. It is a highly labour-intensive industry with lots of manual processes. Satisfying the huge global demand for garment products is mostly dependent on the production and delivery performance of the employees in the garment manufacturing companies. The main problem often faced by the garment industry is that employees cannot meet the productivity that has been targeted, causing losses such as the number of good products produced is less than the target, delays in completing products from a predetermined time period, and the level of customer satisfaction decreases. So, it is highly desirable among the decision makers in the garments industry to track, analyse and predict the productivity performance of the working teams in their factories using data driven approach. Through the data approach, predictive models can be made using one of the machine learning algorithms, namely regression. With this predictor of employee productivity, management can carry out production planning more accurately and efficiently in terms of costs.</p>

## Objective & Method
1. Create garment employee's productivity predictor
   
   Create predictive model using regression machine learning algorithm. In this project we will use several method of regression, compare  their performance, and choose one of the best model. The method that we use are :
   * Multiple Linear Regression
   * Ridge Regression
   * Lasso Regression
   * Random Forest Regression
   * Deep Learning
2. Analyze the variable that affect garment employee's productivity 
   
   Perform exploratory data analysis processes to analyze :
   * Correlation among other variables
   * Determine effective and efficient variable standard to achieve high productivity (> targeted productivity)

## Business Benefit
1. Predict garment employee's productivity with an accuracy rate more than 90% by taking consideration of various factors that determine employee productivity
2. Productivity determinant variable planning can be determined effectively and efficiently so it can minimize labor costs, overtime costs, and incentive costs by more than 50%

## Dataset 
<p align="justify">This project using productivity prediction of garment employee dataset from kaggle (https://www.kaggle.com/datasets/ishadss/productivity-prediction-of-garment-employees). This dataset contains 1197 rows and 15 columns. This dataset includes important attributes of the garment manufacturing process and the productivity of the employees which had been collected manually and also been validated by the industry experts. Here is features description : </p>

1. date : date in MM-DD-YYYY
2. quarter : a portion of the month (A month was devided into five quarters)
3. department : associated department with the instance
4. day : day of the week
5. team : associated team number with the instance
6. targeted_productivity : targeted productivity set by the authority for each team for each day
7. smv : standard minute value, it is the allocated time for a task
8. wip : work in progress. includes the number of unfinished items for products 
9. over_time : represents the amount of overtime by each team in minutes
10. incentives : represents the amount of financial incentive (in BDT) that enables or motivates a particular course of action
11. idle_time : the amount of time when the production was interrupted due to several reasons
12. idle_men : the number of workers who were idle due to production interruption
13. no_of_style_change : number of changes in the style of a particular product 
14. no_of_worker : number of workers in each team
15. actual_productivity : The actual % of productivity that was delivered by the workers. It ranges from 0-1

## Requirement Packages

```
pandas, numpy, sklearn, statsmodels, seaborn, matplotlib
```
## Analysis Flow
1. Data Profiling
   * Categorical data consists of quarter, department, and day features
   * Numerical data consists of team, targeted_productivity, smv, wip, over_time, incentive, idle_time, idle_men, no_of_style_change, no_of_workers, actual_productivity features
   * No_of_workers feature type is float and we find some abnormal value on it (example : 30.5)
   * Minimum and maximum values for all column seem reasonable because there are no negative values, but we can find an outlier in maximum values of actual productivity (> 1)
   * There is a wrong type in value counts of department column 'sweing'. We can change it into sewing
   * Department of finishing separated into 2 value counts. We can combine the data
   * Extract the month of the date feature. All of data were taken in 2015 (not in different year), so we can ignore it and we have already quarter and day features to replace the day of the date feature
   
2. Feature Engineering
   a. Extract month from date feature
   b. Correcting the wrong type
   c. Round up the value of no_of_workers & change the data type into integer
   d. Change the value of actual_productivity > 1 become 1
   
3. Data Cleaning
   a. There is a missing value in wip features
