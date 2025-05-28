# A-B-testing
This repository contains a portfolio project focused on A/B testing using Python, with data visualization in Tableau. The goal of this study is to perform a statistical analysis of the impact of changes in a web product based on A/B test results.

🔍 **Project Overview**
The file Portfolio_Project_2.ipynb includes the following steps:

* Loading and preprocessing of A/B test data

* Analysis of user metrics across control and test groups

* Statistical hypothesis testing using a proportions Z-test

* Conclusions regarding the effectiveness of the tested changes

🛠️ **Technologies Used**
* Python: pandas, numpy, scipy, matplotlib, seaborn

* Statistical methods: proportions Z-test, significance testing

* Data visualization: Tableau

* Flexible analysis: Calculations are performed dynamically using arrays and loops, without hardcoding metric names or values.

📊 **View: Aggregated Event-Level A/B Test Data**
This view prepares the foundational dataset for statistical analysis of multiple A/B tests across various behavioral metrics. It includes:

`test_number`: identifier of the test

`metric`: name of the metric being analyzed in the form of <numerator_event>/<denominator_event> 

`numerator_event`:	name of the numerator event

`denominator_event`: name of the denominator event

`numerator_count`: 	number of times the numerator event occurred in the test group

`denominator_count`: number of denominator events in the test group

`numerator_count_control`: 	number of numerator events in the control group

`denominator_count_control`: number of denominator events in the control group

*How it works:*
This view is created by filtering and aggregating raw event logs by event_name and test_group, grouped per test number and metric. It uses Python’s pandas operations for flexible, dynamic grouping without hardcoded metric handling.  


📊 **Query: Statistical Comparison of Conversion Rates**
The query layer operates on top of the view and calculates the statistical impact of each tested metric:

`conversion_rate`: 	calculated conversion rate (numerator / denominator) for the test group

`conversion_rate_control`: calculated conversion rate for the control group

`metric_change`: 	relative change in conversion rate (test vs. control)

`z_stat`: 	z-statistic value for the proportions test

`p_value`: 	p-value from the statistical test

`significant`: boolean string ("TRUE"/"FALSE") indicating whether p_value < 0.05

*How it works:*
The calculations are performed inside nested loops — iterating first over A/B test numbers and then over a dictionary of compound metrics. Statistical testing is handled using statsmodels' proportions_ztest() function. This dynamic structure allows scalability to additional metrics or test iterations without modifying core logic.
