---
layout: post
title:      "Learning from project 1 - how to decide what variables to use"
date:       2019-06-27 05:32:35 +0000
permalink:  learning_from_project_1_-_how_to_decide_what_variables_to_use
---


It is inevitable that a data scientist has to deal with a lot of data, and these data come with a lot of variables that may help with predicting a dependent variable. Even if it is only a small number of independent variables, there are still many ways do decide what to keep or drop when doing the regression analysis. Each combination of the independent valuables will affect the accuracy of the prediction model. Through the first project, I got to work with King County House Sales dataset which comes with 20 independent variables. Other than using common sense for making judgement on what to do with each variable, another important foundation is each variable’s theoretical relevance. For each decision you made, there need to be sound theoretical reasoning supporting it. There is no right or wrong way to decide what to keep or drop, as long as it can be explained. 

When I looked at the King County House Sales dataset, the first thing I did is trying to understand what each column (i.e. independent variable) refers to and its meaning (Fig 1). Based on my assumption / understanding of what they mean, I then try to look at their datatype (Fig 2) to see if it made sense or if it is consistent with my understanding of the definition. 


From the overall information provided by each of the columns, these are the sort of house sales information that would be available from a real estate agent company and they appear legitimate and we could rely on these data to run our price prediction analysis. After the general analysis at the top level, we should now explore each variable in detail.

Price

From the histrogram in Fig 3, we can see that Price is a normal distributed variable with a very long tail. This made sense as the median price is $450,000 and mean price is $540,000. When a house in King County hits the $1,000,000 mark, there are less amount of people buying, thus creating the long tail. Since this is a variable we need to predict, we will keep this column.

Bedrooms

When we look at the statistics table for this column, there is a number that seems quite odd. It has a mean of 3.3 bedrooms, with minimum of 1 bedroom and median of 3 bedrooms, but the maximum is 33 bedrooms. There is only one row of data with this information and by using common sense, it can be understood that this is a typo, and this created an outlier. Given that all the remaining data make sense, we will keep this variable, but we need to remove the row which contains the abnormal information of 33 bedrooms.

Floors

This variable has a mean of 1.5 and a median of 1.5, with a maximum of 3.5. The half values make sense in this case as there could be mezzanine floors involved. The scatter plot of Floors shows that it has verticality in the data, so we should keep this variable, view it as a categorical data and bin this variable.

Waterfront

This variable contains 18,921 “0” values, 2,353 “null” values, and 146 “1” values. I assume “1” means with a waterfront, “0” means without waterfront, and “null” means missing value. 
 
From the box plot above, we can see that “0” and “null” have similar median values, and the median value for “1” is much higher. I have decided to keep this column but will clean the waterfront data and replace all the “null” with “0”.

View

The column definition is “has been viewed”, and the data come in different categories: null, 0, 1, 2, 3, 4. I would have assumed that this category tells people whether a property has been viewed, but I  couldn’t understand how the categories should be explained. After replacing the “null” with “0”, there are total of 19,316 “0” values which is the majority amount (90%). Given majority is null and the definition is unclear, and there is no recognizable pattern in the box plot, I have decided that this column will be dropped.

Yr_renovated

This records the year when the house was renovated. The scatter plot indicates a similar n price for houses with “not renovated” and “null”. After we clean the data by replacing “null” with “not renovated”, it shows that almost 96% of the data have a 0 which means they have not been renovated. This percentage is too high, and I have doubt on the accuracy of this data. Given this concern, I have decided to remove this column from the analysis.

Longitude and Latitude

These two columns provided coordinates for each of the properties sold. Even though location is very important in real estate market, I had difficulty in deciding whether to keep these two columns. At the first glance, I believe these two columns provide duplicated information with zip code. However, when I removed these and run my multivariate regression analysis, the R squared value is lowered. My R squared value is higher if I keep these two columns.

To sum up, some of the variables can be kept or can be removed. The decision you made on each of these variables will influence other variables and the accuracy of the multivariate regression model. Multiple takes should be experimented to see how each combination of the variables work. In the future, I would like to spend more time on looking at the location of each of the properties, such as longitude, latitude and zip code in detail, and analyze location’s effect on price better.






