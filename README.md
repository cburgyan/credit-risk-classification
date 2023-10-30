# credit-risk-classification

### By Karoly Burgyan<br><br>

---
# Sources
<ol>
<li>Dataset provided by edX Boot Camps LLC</li>
<li>ChatGPT https://chat.openai.com/</li>
</ol>

---

# An Assessment Of Two Predictive Loan Models
In this project, supervised machine learning was used with the aid of a dataset of "historical lending activity" to build two models for predicting 'healthy loan' and 'high-risk loan' borrowers. Both of these models used logistic regressions for their predictions, however, one model used each data point of the original data only ONCE and this model was called the 'single-sampled model' whereas the other model used some of the data points more than once and, so, was called the 'resampled model'.<br><br>

---

# About the Dataset And the Process
The dataset had a total of 77,536 data points with 75,036 'healthy loan' accounts and 2,500 'high-risk loan' accounts. This dataset was split into a training dataset of 58,152 data points and a testing dataset of 19,384 data points.<br>
For both the single-sampled model and the resampled model, the training dataset of 58,152 data points was used to train the models to predict when an account should be labeled as 'healthy loan' or 'high-risk loan' via the supervised machine learning algorithm of logistic regression. And then the testing dataset of 19,384 data points were used to test the accuracy of each model's predicted labels. However, the resampled model (as the name suggests) resampled many of the 'high-risk loans' in an attempt to counter balance the smaller amount of data points that corresponded to 'high-risk loans' (remember, there were only 2,500 'high-risk loans' compared to the 75,036 'healthy loans').
<br>
<br>

---

# The Results<sup style='font-size: 10;'>1</sup>
Let's take a look at the different results between the two models.
## The Single-Sampled Model
The following discusses how well the single-sampled model predicted the 'healthy loan' and the 'high-risk loan':<br>
The single-sampled model predicted the 'healthy loan' ALMOST perfectly with a:<br> 
<ul> 
    <li>precision = 99.64%.<sup>2</sup></li>
    <li>recall = 99.57%.<sup>2</sup></li>
</ul>
Whereas, the single-sampled model predicts the 'high-risk loan' with significant inaccuracy with a:<br>
<ul>
    <li>precision = 87.46%.</li>
    <li>recall = 89.28%.</li>
</ul>
And the single-sampled model predicted, overall:
<ul>
<li>accuracy = 94.427%<sup style='font-size: 10;'>3</sup></li>
</ul>

#### Missed Opportunity Cost
12.54%<sup>4</sup> of the accounts that the single-sampled model predicted/labeled as 'high-risk loan' accounts were actually 'healthy loan' accounts.<br>

#### Unexpected High Credit Risk
0.357%<sup>5</sup> of the accounts that the single-sampled model predicted/labeled as 'healthy loan' accounts were actually 'high-risk loan' accounts.


## The Resampled Model
The following discusses how well the resampled model predict the 'healthy loan' and the 'high-risk loan':<br>
The resampled model predicts the 'healthy loan' ALMOST perfectly with a:<br> 
<ul> 
    <li>precision = 99.99%.<sup>2</sup></li>
    <li>recall = 99.52%.<sup>2</sup></li>
</ul>
Whereas, the resampled model predicts the 'high-risk loan' with some inaccuracy with a:<br>
<ul>
    <li>precision = 87.26%.</li>
    <li>recall = 99.68%.</li>
</ul>
And the resamped model predicted, overall:
<ul>
<li>accuracy = 99.597%<sup style='font-size: 10;'>3</sup></li>
</ul>

#### Missed Opportunity Cost
12.75%<sup>4</sup> of the accounts that the resampled model labeled as 'high-risk loan' accounts were actually 'healthy loan' accounts.

#### Unexpected High Credit Risk
0.001%<sup>5</sup> of the accounts that the single-sampled model labeled as 'healthy loan' accounts were actually 'high-risk loan' accounts.


<sup>1</sup><span style='font-size: 10;'> See the credit_risk_classification.ipynb for the calculation details.</span>

<sup>2</sup><span style='font-size: 10;'> The 'sklearn.metrics.classification_report' function rounded this value to 1.00 corresponding to 100%.</span>

<sup>3</sup><span style='font-size: 10; line-height: .7;'> 'accuracy' here is the accuracy obtained from using the 'sklearn.metrics.balanced_accuracy_score' function and not the 'sklearn.metrics.classification_report' function which also has an 'accuracy'. The 'sklearn.metrics.balanced_accuracy_score' is the same as the 'macro average recall' from within the 'sklearn.metrics.classification_report' rounded to the nearest percent.</span>

<sup>4</sup><span style='font-size: 10;'> This is value is derived from subtracting precision of 'high-risk' loans from 100%.</span>

<sup>5</sup><span style='font-size: 10;'> This is value is derived from subtracting precision of 'healthy' loans from 100%.</span>

---
# Conclusion
The singled-sampled model and the resampled model had nearly identical perfect results in precision and recall for predicting 'healthy loans'. However, when considering the precision and recall of the 'high-risk' loans they diverged significantly.<br>
While the 'precision' of the 'high-risk' loans were nearly identical for the two models (87.46% and 87.26%), the 'recall' saw a dramatic improvement from the single-sampled model with a 89.28% to the resampled model's 99.68%.<br>
Ultimately, the differences in 'high-risk' prediction between these two models could best be captured by comparing the 'Missed Opportunity Cost' and the 'Unexpected High Credit Risk'. 
#### Missed Opportunity Cost
The 'Missed Opportunity' costs were nearly identical with the single-sampled model's 12.57% as compared resampled model 12.75% for mislabelling 'healthy' loans as 'high risk' loans which makes the single-sampled model 1.4% RELATIVELY better than the resampled model at avoiding labelling actual 'healthy' loans as 'high-risk' loans. 
#### Unexpected High Credit Risk
HOWEVER, the 'Unexpected High Credit Risk' results were dramatically different between the two models. The single-sampled model's had an 'Unexpected High Credit Risk' of 0.357%  whereas the resampled model had a 'Unexpected High Credit Risk' of 0.001% which makes the resampled model 35,700% RELATIVELY better than the single-sampled model in avoiding labelling actual 'high-risk' loans as 'healthy' loans.<br>

#### Recommendation
After considering the findings above, the resampled model outperforms the single-sampled model in dramatic fashion and would spare the company from huge unexpected loses.<sup>6</sup>

<sup>6</sup><span style='font-size: 10;'> Here, it's assumed that the interest rates for loans are such that one defaulted loan requires many successfully paid loans to recover from.</span>