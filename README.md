# Credit Risk Prediction Project

A project where I built a full pipeline, from raw data to a working dashboard, to predict which borrowers are likely to default on a loan. I used SQL, Python, and Power BI together, and I wanted to go beyond just training a model, so I also added a part that shows how a bank could actually use the results to make decisions.

## Overview

The goal is to predict whether a borrower is likely to be seriously late on payments (90 days or more) within two years, using a public dataset of 150,000 borrowers. Instead of stopping at "here is my model's accuracy," I focused on showing what the model actually means for a real business decision.

## What I did

**Data cleaning (SQL):** I loaded the raw data into a SQL database first. Then I used SQL queries to find problems in the data, like missing income values, and a few strange entries, for example one row with age listed as 0, and some columns using 96 or 98 as a placeholder instead of a real number. I cleaned all of this before doing anything else.

**Building the model (Python, scikit learn):** I filled in the missing values, added three new features (total number of times someone was late, whether they had ever been seriously late, and income per person they support), then trained two models to compare. A simple Logistic Regression model reached an AUC of about 0.82, and a Random Forest model did better, reaching about 0.86.

**Turning it into a business decision:** Most projects like this stop at the model. I wanted to take it one step further, so I built an analysis that tests different decision cutoffs, showing the trade off, a stricter cutoff catches more risky borrowers but also rejects more good ones, along with what that would cost in missed defaults.

**Dashboard (Power BI, DAX):** Finally, I built a two page interactive dashboard to bring all of this together visually.

## Dashboard

### Model Overview
This page shows the basics: total borrowers, actual versus predicted default rate, default rate by age group, and a breakdown by risk level. It also confirms the model makes sense, borrowers the model marks as "High risk" really do default more often in the real data.

![Model Overview Dashboard](model_overview.png)

### Threshold Decision Analysis
This page lets you pick a single decision cutoff and instantly see the estimated cost of missed defaults at that cutoff, along with a chart showing the full trade off across all possible cutoffs.

![Threshold Decision Analysis Dashboard](threshold_decision_analysis.png)

## Tools and Skills

SQL, Python (pandas, scikit learn), Power BI, DAX, predictive modeling, feature engineering, data cleaning, dashboard design.

## Dataset

The dataset used is the public "Give Me Some Credit" dataset, originally released as part of a 2011 Kaggle competition.

## Notebook

The full analysis, from data loading through model training and export, is available in `credit_risk_project.ipynb`.
