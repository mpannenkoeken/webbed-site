---
date: 2026-04-13
title: Machine Learning in Python Project
meta_description: Given a set of a little over 13,000 responses to subsets of several UNICEF questionnaires, we were tasked with building a pipeline that could predict childhood depression. 
post_image: /images/projects/mlpy/confused_matrix.png
image_alt: Confusion Matrix of Final Fitted Logistic Regression
sub_heading: 
layout: proj
tags:
    - projects
    - machine learning
---

## Overview
Given a set of a little over 13,000 responses to subsets of several UNICEF questionnaires, we were tasked with building a pipeline that would predict childhood depression based on the answers to the remaining 86 questions. Our exploratory data analysis reduced the feature space to 27 relevant questions. Feature engineering steps were taken to standardize the features and convert them to numerical values. Missingness of features was considered as potentially correlated to the target, so missing answers were assigned the mode of the feature. The target showed high imbalance, which was considered in two approaches. The first involved manually setting class weights such that positives would be treated with a significance equal the number of times over that negatives occured compared to positives, while the second utilized built-in balancing functions. We tried several modelling approaches to predict depression based on the given data, namely logistic regression, classification trees, bagging trees, support vector machines, and random forests. Using Recall as our primary performance evaluation metric, we found a Logistic Regression to be the most suitable approach for the application. Recall was selected as the primary performance evaluation metric due to the high cost of false negatives in this application, i.e. the vastly negative effects of failing to identify depression in a child. The Logistic Regression pipeline was fit using Ridge Regression, and the penalty parameter was tuned using Cross-Fold Validation. 

Our Logistic Regression showed rather poor performance with regard to predicting childhood depression based on questionnaire responses, regardless of which target balancing technique was employed. Our models' final predictive performance by balancing technique is summarized in the table below. The most important features in the predictions based on coefficient magnitudes were water insufficiency, lack of household plumbing, missingness of the question related to recent punishment by striking hands, arms, or legs, presence of household flush toilet(s), and "modern" roofing. The former three of these features had positive association with indications of childhood depression, while the latter two had negative association with the target.

| Balancing               | Recall | Specificity | F1 Score | Accuracy |
|-------------------------|--------|-------------|----------|----------|
| Manual Weights          | 0.5640 | 0.6506      | 0.2583   | 0.6410   |
| Built-in Functions      | 0.5606 | 0.6540      | 0.2586   | 0.6437   |

We then considered a neural network, as a sufficiently complex one would, theoretically, perfectly model the data at the expense of computational complexity and lack of interpretability. The neural network approach achieved only slight performance improvements, leading us to believe that the dataset lacked the predictive power necessary to achieve greater performance. Our suggestions therefore mainly involved suggestions related to improving data collection, as well as highlighting the fact that likely indicators of household wealth tended to have the strongest effect on the target. 

## Personal Reflection
In retrospect, there are things here that could have been done better. The most disheartening thing about this project was revising for the course's exam and realizing everything we should have done but failed to do. There was room for improvement in our EDA and feature engineering, notably in the ordering of our steps and the way in which we encoded non-numeric data. With regard to the logisitic regression, which was the part in which I was most involved, there was a lot more tuning and exploration to be done, especially with comparing ridge to lasso and elastic nets and considering nonlinear feature interactions. Ultimately, I'm not sure how much any of this would have changed the final analysis or recommendations, but that uncertainty is precisely why I regret the fact that we did not make these considerations. Also, our work was performed in Jupyter notebooks, with collaboration and version control facilitated through Github. This led to a fair bit of friction related to difficult-to-resolve merge conflicts and pdf generation, which in turn complicated work that was already under significant time pressure. If given the freedom to determine workflow in future projects, I would prefer using individual Python scripts and LaTeX files for development and reporting, respectively, as this would likely represent a much smoother means by which to collaborate.

## Downloads
**Written Report (PDF)**
[Download Report](/images/projects/mlpy/Machine_Learning_Project.pdf)