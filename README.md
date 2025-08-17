<img src="src\img\title.jpg" width="800" height="250">

<a id="readme-top"></a>

<!-- TITLE -->
#  **Data Analytics**

This project is educational. It presents solutions to the most pressing problems encountered in the practical work of a data analyst.

<!-- TABLE OF CONTENTS -->
<details>
  <summary> Table of Contents </summary>
  <ol>
    <li>
          <a href="#getting-started">Getting Started</a>
          <ul>
            <li><a href="#file-assignment">File assignment</a></li>
            <li><a href="#installation">Installation</a></li>
          </ul>
    <li><a href="#task-1-time-series-analysis-and-forecasting">TASK 1. Time series analysis and forecasting</a></li>
    <li><a href="#task-2-binary-classification">TASK 2. Binary classification</a></li>
    <li><a href="#task-3-analysis-of-subscriber-tariff-plans">TASK 3. Analysis of subscriber tariff plans</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#Source-of-information">Source of information</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>


<!-- GETTING STARTED -->
## Getting Started

The information about file assignment of the project and how that used.

### File assignment

This is an example of how to list things you need to use the software and how to install them.
* requirements.txt (for installing the main packages)
* task1.ipybn (for solution TASK 1. Time series analysis and forecasting)
* task2.ipybn (for solution TASK 2. Binary classification)
* task3.ipybn (for solution TASK 3. Analysis of subscriber tariff plans)
* 'data' (csv-files for analytic)
* 'presentation' (presentations with task results are located here)
* 'result' (vectors of forecasting and saved Xgbmodel are located here)


### Installation

_Below is an example of how you can  installing and setting up model._

1. Clone the repo
   ```sh
   git clone https://github.com/kek7777/Data_Analytics.git
   ```
2. Install packages if necessary
   ```
   pip install -r requirements.txt
   ```
   
 <p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- TASK 1 -->

<details>
  <summary><strong><h2 id="task-1-time-series-analysis-and-forecasting">TASK 1. Time series analysis and forecasting</h2></strong></summary>
  <div>
    <p><strong>DESCRIPTION OF TASK</strong><br>
    Using historical data on the "Timeseries" sheet (see tasks_1_2.xlsx), build a time series model. Predict the daily behavior of the series over the next 3 months. Explain the choice of forecasting method. Provide estimates of the forecast quality.</p>
    <p style="line-height: 1.2; margin: 0;">
    <strong>TASK PROGRESS</strong><br>
        <strong>Step 1. Time series analysis.</strong><br>  The objective of the time series analysis was to examine its structure and key characteristics: trend, seasonality, and stationarity. For this purpose, the capabilities of the Pandas and Statsmodels libraries were utilized. The analysis revealed that the time series is  <strong>well-structured</strong>  and contains no missing (null) values. It also exhibits  <strong>weak stationarity, annual seasonality, and a positive upward trend.</strong>  Based on a review of scientific and technical literature, and considering the characteristics of the time series under study, the  <strong>PROPHET model</strong>  was selected for further investigation.</p>
        <strong>Step 2. Model training.</strong> <br> Three Prophet models with different parameter configurations were evaluated:<br>
        Model 1 - default parameters.<br>
        Model 2 - parameters optimized using Prophet's built-in <strong>cross-validation</strong> function.<br>
        Model 3 - custom parameters based on Model2's configuration.<br>
        All models were trained and tested on datasets containing 1552 training samples and 90 test samples.<br>
        The most accurate model was selected based on the minimum MAPE (Mean Absolute Percentage Error) value.<br>
        Research results showed that Model 3 achieved the lowest <strong>MAPE (0.13)</strong>, demonstrating the most accurate predictions for the time series.</p>
        <strong>Step 3. Forecasting.</strong><br> Using Model 3, 3-month forecast (July 1 - September 28, 2019) were  generated.<br> <strong>The forecast results:</strong><br> An overall positive trend with a minor downturn at the end of the forecast period.<br>
        Forecast vector is presented in the file <strong>'forecast_1.csv'</strong>.<br>
        Visualized results of the TASK 1 are presented in the file <strong>'task_1.pdf'</strong>.</p><br>
        <table style="border-collapse: collapse; width: 200px; font-family: Arial, sans-serif;">
      <tr>
      <th colspan="2" style="border-bottom: 1px solid #ddd; padding: 8px; text-align: left;">Predicted values</th>
      </tr>
      <tr>
      <td style="padding: 8px; border-bottom: 1px solid #ddd;">max:</td>
      <td style="padding: 8px; border-bottom: 1px solid #ddd; text-align: right;">6564</td>
      </tr>
      <tr>
      <td style="padding: 8px; border-bottom: 1px solid #ddd;">min:</td>
      <td style="padding: 8px; border-bottom: 1px solid #ddd; text-align: right;">3400</td>
      </tr>
      <tr>
      <td style="padding: 8px;">mean:</td>
      <td style="padding: 8px; text-align: right;">4877</td>
      </tr>
      </table>
  </div>
</details>
 <p align="right">(<a href="#readme-top">back to top</a>)</p>




<!-- TASK 2 -->

<details>
  <summary><strong><h2 id="task-2-binary-classification">TASK 2. Binary classification</h2></strong></summary>
  <div>
    <p><strong>DESCRIPTION OF TASK</strong><br>
    Using the dataset on the "Training" sheet (see tasks_1_2.xlsx) as a training sample, predict the values of the target variable 'Target' for the dataset on the "Validate" sheet. Justify the choice of the method. Provide accuracy and predictive model quality metrics. Plot the ROC curve. Name the three most important predictors.</p>
    <p style="line-height: 1.2; margin: 0;">
    <strong>TASK PROGRESS</strong><br>
        <strong>Step 1. Exploratory data analysis.</strong><br>  The data analysis showed that the data is structured and contains about <strong>3% missing values (null)</strong>. Additionally, there are outliers in the data. The target features are balanced.<br>
        Two approaches were considered for handling missing values: <strong>median</strong> replacement and <strong>KNNImputer</strong> (Scikit-learn). The best model performance was obtained when using the second imputation method.</p>
        <strong>Step 2. Model training.</strong><br> For a classification problem, three models were considered: <strong>DecisionTreeClassifier, XGBClassifier, and ExtraTreeClassifier</strong>.<br> The models' parameters were tuned using <strong>GridSearchCV</strong>.<br>
        All models were trained and tested on data split into 80% train and 20% test sets.<br>
      The selection of the most accurate model was based on the analysis of the following metrics: <strong>ROC, Recall, Accuracy, Precision, F1, and Confusion Matrix</strong>.<br>
      The training found that the <strong>XGBClassifier model</strong> provides the most accurate classification of the classes.<br></p>
      <table style="border-collapse: collapse; width: 200px; font-family: Arial, sans-serif;">
      <tr>
      <th colspan="2" style="border-bottom: 1px solid #ddd; padding: 8px; text-align: left;">Metrics</th>
      </tr>
      <tr>
      <td style="padding: 8px; border-bottom: 1px solid #ddd;">ROC:</td>
      <td style="padding: 8px; border-bottom: 1px solid #ddd; text-align: right;">0.78</td>
      </tr>
      <tr>
      <td style="padding: 8px; border-bottom: 1px solid #ddd;">Precision:</td>
      <td style="padding: 8px; border-bottom: 1px solid #ddd; text-align: right;">0.71</td>
      </tr>
      <tr>
      <td style="padding: 8px;">F1:</td>
      <td style="padding: 8px; text-align: right;">0.69</td>
      </tr>
      </table>
      </p>
      The features were also assessed according to their degree of influence on the MSE. Of the 31 features, three have the greatest influence on prediction: <strong>P22, P1, P9</strong>.</p>
        <strong>Step 3. Forecasting.</strong><br> Using XGBClassifier model, the target variable 'Target' was  generated. Distribution of predicted classes: <strong>Class 0 (15508), Class 1 (4492)</strong>.</p>
  </div>
</details>
 <p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- TASK 3 -->

<details>
  <summary><strong><h2 id="task-3-analysis-of-subscriber-tariff-plans">TASK 3. Analysis of subscriber tariff plans</h2></strong></summary>
  <div>
    <p><strong>DESCRIPTION OF TASK</strong><br>
    The file "Tariff_plans_change.csv" contains sample data on transactions related to the activation and deactivation of tariff plans by subscribers who switched tariff plans in the first half of 2017. The file "Charges.csv" contains monthly historical data on subscribers' total mobile service expenses. The file "Suspended.csv" contains historical data on subscriber suspensions in transactional form.<br>
    The following questions need to be investigated:<br>
    <strong>Directions of tariff plan changes</strong>:<br> From which tariff plans and to which ones were the largest migrations? Visualize the migration flows in a diagram.<br> <strong>Change in the average monthly bill</strong>: How did the average monthly bill of subscribers change over the 3-month period after the month of switching compared to the 3-month period before the switch? Which tariff plan change directions were associated with an increase in the average bill, and which with a decrease? <br> <strong>Change in suspension rates</strong>: Similarly to point 2, but regarding changes in suspension frequency—how much less or more often subscribers were suspended after migration, both overall and for each migration direction separately. Use the same comparison periods: 3 months before the switch month and 3 months after.</p>
    <p style="line-height: 1.2; margin: 0;">
    <strong>TASK PROGRESS</strong><br>
        <strong>Step 1. Exploratory data analysis.</strong><br>  The data analysis showed that the data is structured and contains about <strong>3% missing values (null)</strong>. Additionally, there are outliers in the data. The target features are balanced.<br>
        Two approaches were considered for handling missing values: <strong>median</strong> replacement and <strong>KNNImputer</strong> (Scikit-learn). The best model performance was obtained when using the second imputation method.</p>
        <strong>Step 2. Model training.</strong><br> For a classification problem, three models were considered: <strong>DecisionTreeClassifier, XGBClassifier, and ExtraTreeClassifier</strong>.<br> The models' parameters were tuned using <strong>GridSearchCV</strong>.<br>
        All models were trained and tested on data split into 80% train and 20% test sets.<br>
      The selection of the most accurate model was based on the analysis of the following metrics: <strong>ROC, Recall, Accuracy, Precision, F1, and Confusion Matrix</strong>.<br>
      The training found that the <strong>XGBClassifier model</strong> provides the most accurate classification of the classes.<br></p>
      <table style="border-collapse: collapse; width: 200px; font-family: Arial, sans-serif;">
      <tr>
      <th colspan="2" style="border-bottom: 1px solid #ddd; padding: 8px; text-align: left;">Metrics</th>
      </tr>
      <tr>
      <td style="padding: 8px; border-bottom: 1px solid #ddd;">ROC:</td>
      <td style="padding: 8px; border-bottom: 1px solid #ddd; text-align: right;">0.78</td>
      </tr>
      <tr>
      <td style="padding: 8px; border-bottom: 1px solid #ddd;">Precision:</td>
      <td style="padding: 8px; border-bottom: 1px solid #ddd; text-align: right;">0.71</td>
      </tr>
      <tr>
      <td style="padding: 8px;">F1:</td>
      <td style="padding: 8px; text-align: right;">0.69</td>
      </tr>
      </table>
      </p>
      The features were also assessed according to their degree of influence on the MSE. Of the 31 features, three have the greatest influence on prediction: <strong>P22, P1, P9</strong>.</p>
        <strong>Step 3. Forecasting.</strong><br> Using XGBClassifier model, the target variable 'Target' was  generated. Distribution of predicted classes: <strong>Class 0 (15508), Class 1 (4492)</strong>.</p>
  </div>
</details>
 <p align="right">(<a href="#readme-top">back to top</a>)</p>



 <!-- LICENSE -->
 ## License
 
 Distributed under the Unlicense License. See `LICENSE.txt` for more information.
 
 <p align="right">(<a href="#readme-top">back to top</a>)</p>
 
 <!-- Source of information -->
 
 ## Source of information
 
 Information that was used in the development of the project.
 
 * [Origin article of Prophet](https://facebook.github.io/prophet/static/prophet_paper_20170113.pdf)
 * [XGBoost Documentation](https://xgboost.readthedocs.io/en/stable/)

 
 <p align="right">(<a href="#readme-top">back to top</a>)</p>

  <!-- CONTACT -->
 ## Contact
 
 Author of the project - [Email](https://kek777.mail.ru)
 
 Project Link: [https://github.com](https://github.com/kek7777/Data_Analytics.git)
 
 <p align="right">(<a href="#readme-top">back to top</a>)</p>



 <!-- TASK 2 -->
 ## TASK 2. Binary classification
 
 Author of the project - [Email](https://kek777.mail.ru)
 
 Project Link: [https://github.com](https://github.com/kek7777/Data_Analytics.git)
 
 <p align="right">(<a href="#readme-top">back to top</a>)</p>
 
 
