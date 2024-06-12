# us-delinquency-forecast

<h1>Forecasting U.S. Delinquency Rates ft. Economic Data (Py)</h1>


<h2>Problem Statement</h2>
Developing a Credit default model that provides broader view on potentially default value to financial
institutions as their risk models evolved over the time to reduce their Credit Risk.

Objective:
Prediction (using ML Algorithms) delinquency or default rates considering the economic outlook
which aids in estimating the likelihood of a prospective default by small or large corporations.


<h2>Language Used</h2>

- <b>Python</b>

<h2> Target variables </h2>

- Single Family Mortgage Loan
- Commercial Real Estate Loan
- Business Loans
- Consumer Loans
- Credit Cards Loans

<h2> Predictors </h2>
<b>Aspects on selecting the data series:</b>
<br>
  <br/>

1. US Bureau of Labor Statistics:
- US Unemployment rate, monthly.

2. University of Michigan Surveys of Consumers:
- Index of Consumer Sentiment, quarterly (Table 1)
- Expected Change in Financial Situation in a Year, quarterly (Table 8)
- Expected Change in Unemployment During the Next Year, quarterly (Table 30)

3. US Census Bureau:
- US Housing Starts, single unit and multi-unit, quarterly.
- US Housing Completions, single unit, and multi-unit, quarterly.

4. Bureau of Economic Analysis, US Department of Commerce:
- Household personal savings, quarterly.
- Undistributed Corporate profits, quarterly.

5. Economic Indicators

- GDP growth rates
- GDP per capita
- GNI growth rates
- GNI per capita
- Inflation rate
- Interest rate
- Gov. debt to GDP
- Current account to GDP, Fiscal
- Expenditure, CPI
- Food Inflation
- Business confidence
- Consumer confidence
- Consumer credit

<h2> Data & Sources </h2>
<b>Focused on 4 delinquency rates, available from the Federal Reserve Economic Database (FRED):
</b>
<br>
  <br/>

- Delinquency Rate on Consumer Loans (Q1 1987 to Q2 2023)
- Delinquency Rate on Credit Card Loans (Q1 1991 to Q2 2023)
- Delinquency Rate on Commercial Real Estate Loans excluding Farmland (Q1 1991 to Q2 2023)
- Delinquency Rate on Business Loans (Q1 1987 to Q2 2023)

Together, these series encompass the percentage of defaulted loans within consumer and business lending, activities which are typically larger sources of credit risk for banks.
<br>
  <br/>
<b>Several macro economic indicators should have an impact on delinquency rates:</b>

- Refiniv Eikon (available in WRDS database):
GDP growth, unemployment rate, consumer confidence levels
- Federal Reserve bank reports (available in WRDS database):
Interest rates on commercial paper, short term business lending, prime lending rates, swap rates, yields on state and local bonds.
- Consumption, Aggregate Wealth, and Expected Stock returns (CAY data as computed by Martin Lettau and Sydney Ludvigson, available in WRDS database)

<h2> Limitations </h2>

- Each target series has only ~140 data points.

- Feature set has more data points than the target variables. They needed to be transformed to fit with the target variables.

<h2>Data Processing and Model Fitting</h2>

<p align="center">
  Identifying the correlation between the target variable
  <br>
  <br/>
  <img src="https://i.imgur.com/rlRvFek.png" height="80%" width="80%" alt="TimeSeriesDeinquencies"/>
</p>

<p align="center">
  <em>(Time series of various delinquency rates)</em>
</p>

<p align="center">
  <img src="https://i.imgur.com/axXCXUj.png" height="80%" width="80%" alt="CorrMtxx"/>
</p>

From the above correlation matrix, we can infer that:
- Single Family Mortgages are uncorrelated with other categories.
- CRE Loans and Business Loans are highly correlated, both of which are moderately correlated with Consumer Loans and Credit Card Loans.
- Consumer Loans and Credit Card Loans are highly correlated, both of which are moderately correlated with CRE Loans and Business Loans.

<h3>Further processing of data variables and model fitting to derive the relationship</h3>

Models Fitted:
- Linear Regression
- Lasso Regression 
- Ridge Regression

<h3>Results</h3>

<p align="center">
  <img src="https://i.imgur.com/35HEl3U.png" height="400px" width="400px" alt="Model Fit: 1"/>
  <img src="https://i.imgur.com/yld4weD.png" height="400px" width="400px" alt="Model Fit: 2"/>
  <img src="https://i.imgur.com/n9UsJsJ.png" height="400px" width="400px" alt="Model Fit: 3"/>
</p>

<p align="center">
  <em>(Time Series of Model Fit)</em>
</p>

<h3>Inference</h3>

- The result implies the poor fitting of the model. This may be due to less number of data points (quarterly datapoints, from 1987 to 2023) considered to fit the model. <em>(See limitations)</em>

- Overall, Lasso Regression appears to provide a relatively better fit for predicting consumer loan delinquencies compared to other estimation methods.
<br>
  <br/>
<p align="center">
  <img src="https://i.imgur.com/7ldKQBL.png" height="500px" width="700px" alt="Coeff Model Plot"/>
</p>

<p align="center">
  <em>(Coefficient model plot of all the variables)</em>
</p>

<h2 align="center">Performance Metrics of Regression Models Across Loan Categories</h2>

<p align="center">
  <img src="https://i.imgur.com/H2e8QbB.png" alt="Performance Metrics of Regression Models Across Loan Categories"/>
</p>

<h2>Conclusion and Further Exploration</h2>

- The current models exhibit poor fit due to the limited dataset available. Efforts to locate additional data prior to 1987 were unsuccessful. Despite this, the results indicate that predicting delinquency rates based on economic outlook is feasible and meaningful with a more comprehensive selection of target variables and improved optimization techniques.

- Further exploration could involve retraining the models using a broader range of economic datasets in combination with the current ones. Additional improvements can be achieved by fine-tuning model hyperparameters and employing ensemble methods such as boosting, which combines several weak learners for better performance. These steps could significantly enhance the model's predictive capabilities with additional time and resources.

<h3>Literature Reference</h3>

- [Machine Learning in Banking Risk Management: A Literature Review (2019)](https://www.mdpi.com/2227-9091/7/1/29)
- [Consumer Credit-Risk Models via Machine-Learning Algorithms (2010)](https://www.sciencedirect.com/science/article/abs/pii/S0378426610002372)
- [Machine Learning for Corporate Default Risk: Multi-Period Prediction, Frailty Correlation, Loan Portfolios, and Tail Probabilities (2023)](https://www.sciencedirect.com/science/article/pii/S0377221722005100)
- [A Comparison of Prediction Methods for Credit Default on Peer to Peer Lending using Machine Learning (2019)](https://www.sciencedirect.com/science/article/pii/S1877050919310579)
- [Explainable Prediction of Loan Default Based on Machine Learning Models (2023)](https://www.sciencedirect.com/science/article/pii/S2666764923000218)
- [National Student Loans Default Risk Prediction: A Heterogeneous Ensemble Learning Approach and the SHAP Method (2023)](https://www.sciencedirect.com/science/article/pii/S2666920X23000450)
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
