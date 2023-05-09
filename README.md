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
2. Determine effective and efficient variable standard to achieve high productivity (> targeted productivity)

## Business Benefit
1. Predict garment employee's productivity with an accuracy rate more than 90% by taking consideration of various factors that determine employee productivity
2. Productivity determinant variable planning can be determined effectively and efficiently so it can minimize labor costs, overtime costs, and incentive costs by more than 50%

## Dataset 
<p align="justify">This project using productivity prediction of garment employee dataset from kaggle (https://www.kaggle.com/datasets/ishadss/productivity-prediction-of-garment-employees). This dataset contains 1197 rows and 15 columns. This dataset includes important attributes of the garment manufacturing process and the productivity of the employees which had been collected manually and also been validated by the industry experts. This dataset taken from one of the garment industry in Bangladesh.Here is features description : </p>

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
   * Extract month from date feature
   * Correcting the wrong type
   * Round up the value of no_of_workers & change the data type into integer
   * Change the value of actual_productivity > 1 become 1
   
3. Data Cleaning
   * There is a missing value in wip features with percentage 42,27%. We can handle it by drop the wip column
   * There is no duplicated value

4. Exploratory Data Analysis
5. Preprocessing Model
   * Encoding categorical data
   * Split data
   * Multicollinearity
   * Drop redundant features
6. Modelling
   * Multiple linear regression
   * Ridge regression with hyperparameter tuning 
   * Lasso regression with hyperparameter tuning 
   * Random forest regression
   * Deep learning
7. Evaluate The Model
8. Choose The Best Model
9. Deep Dive Analysis 

   The objective is to determine effective & efficient standard variable to achieve high productivity with smv based.  here is the steps :
   * filter data with positive margin value and actual productivity > 0,90
   * find the unique value of the smv, we will determine effective & efficient standard variable with smv based
   * filter the data by it's smv value, compare the data that have smv value
   * choose the data that has the smallest value of number of workers, over time, & incentive
     
## Project Result

1. The best model has smallest R2, RMSE, MAE, MAPE values. from the several regression methods used, multiple linear regression is the best model

   | Metric | Multiple Linear Regression | Lasso Regression | Ridge Regression | Random Forest Regression | Deep Learning |
   | :---: | :---: | :---: | :---: | :---: | :---: |
   | R2 | 1 | 0,999 | 0,999 | 0,9983 | - | 
   | RMSE | 5,4517e<sup>-13</sup> | 0,0001517 | 2,0053e<sup>-8</sup> | 0,0173518 | 0,0085 | 
   | MAE | 4,9505e<sup>-13</sup> | 0,0001108 | 1,4063e<sup>-8</sup> | 0,0055825 | 0,0733 | 
   | MAPE | 7,1979e<sup>-13</sup> | 0,0001787| 2,2657e<sup>-8</sup> | 0.0097527 | 11,4380 | 
 
 2. Effective and efficient variable standard to achieve high productivity (> targeted productivity) with smv based
 
 * Sewing Department
    
      | SMV (minutes) | Number of Worker| Over Time (minutes) | Incentive (BDT) | Idle Time (minutes) | Idle Men | Number of Style Change |
      | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
      | 2,9 | 8 | 960 | 0 | 0 | 0 | 0 |
      | 3,9 | 8 | 960 | 0 | 0 | 0 | 0 |
      | 3,94 | 8 | 960 | 0 | 0 | 0 | 0 | 
      | 4,08 | 9 | 1080 | 0 | 0 | 0 | 0 | 
      | 4,15 | 12 | 1440 | 0 | 0 | 0 | 0 | 
      | 4,6 | 8 | 960 | 0 | 0 | 0 | 0 | 
      | 5,13 | 8 | 960 | 0 | 0 | 0 | 0 |
      | 18,79 | 52 | 6240 | 56 | 0 | 0 | 0 | 
      | 22,52 | 58 | 0 | 90 | 0 | 0 | 0 | 
      | 22,94 | 59 | 3060 | 113 | 0 | 0 | 0 | 
      | 25,90 | 57 | 10170 | 70 | 0 | 0 | 0 |
      | 26,16 | 59 | 7080 | 98 | 0 | 0 | 0 |
      | 26,82 | 59 | 7080 | 75 | 0 | 0 | 0 |
      
 * Finishing Department
    
      | SMV (minutes) | Number of Worker| Over Time (minutes) | Incentive (BDT) | Idle Time (minutes) | Idle Men | Number of Style Change |
      | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
      | 2,9 | 9 | 1620 | 0 | 0 | 0 | 0 |
      | 3,94 | 2 | 240 | 0 | 0 | 0 | 0 |
      | 4,08 | 9 | 1080 | 0 | 0 | 0 | 0 | 
      | 4,15 | 8 | 960 | 0 | 0 | 0 | 0 | 
      | 4,30 | 10 | 1200 | 0 | 0 | 0 | 0 | 
      
## Conclusion & Recommendation
1. Compared to the other four models, the multiple linear regression method has the smallest error value and a perfect R2 score of 1. It means that 100% of variability of actual_productivity is perfectly explained using all the features in the model. The standard deviation of prediction errors is 5.4517e<sup>-13</sup>. From the regression line, the residuals mostly deviate between +- 5.4517e<sup>-13</sup>. On average, our prediction using multiple linear regression model deviates the true actual_productivity by 4.950e<sup>-13</sup> Moreover, this by 4.950e<sup>-13</sup> is equivalent to 7,197e<sup>-11</sup> % deviation relative to the true actual_productivity I recommend to use this model as prediction model.

    
    
    
