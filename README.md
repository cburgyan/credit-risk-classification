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
In this project, supervised machine learning was used with the aid of a dataset of "historical lending activity" to build two models for predicting 'healthy loan'* and 'high-risk loan' borrowers. Both of these models used logistic regressions for their predictions, however, one model used each data point of the original data only ONCE and this model was called the 'single-sampled model' whereas the other model used some of the data points more than once and, so, was called the 'resampled model'.<br><br>

*<sub style='font-size: 10;'> From here going forward, '<strong>healthy</strong>' loans will be referred to as '<strong>low-risk</strong>' loans for contrast to 'high-risk' loans.</sub>
<br><br>

---

# About the Dataset And the Process
The dataset had a total of 77,536 data points with 75,036 'low-risk loan' accounts and 2,500 'high-risk loan' accounts. This dataset was split into a training dataset of 58,152 data points and a testing dataset of 19,384 data points.<br>
For both the single-sampled model and the resampled model, the training dataset of 58,152 data points was used to train the models to predict when an account should be labeled as 'low-risk loan' or 'high-risk loan' via the supervised machine learning algorithm of logistic regression. And then the testing dataset of 19,384 data points were used to test the accuracy of each model's predicted labels. However, the resampled model (as the name suggests) resampled many of the 'high-risk loans' in an attempt to counterbalance the smaller amount of data points that corresponded to 'high-risk loans' (remember, there were only 2,500 'high-risk loans' compared to the 75,036 'low-risk loans').
<br>
<br>

---

# The Results<sup style='font-size: 10;'>1</sup>
Let's take a look at the different results between the two models.
## The Single-Sampled Model
The following discusses how well the single-sampled model predicted the 'low-risk loan' and the 'high-risk loan':<br>
The single-sampled model predicted the 'low-risk loan' ALMOST perfectly with a:<br> 
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
12.54%<sup>4</sup> of the accounts that the single-sampled model predicted/labeled as 'high-risk loan' accounts were actually 'low-risk loan' accounts.<br>

#### Unexpected High Credit Risk
0.357%<sup>5</sup> of the accounts that the single-sampled model predicted/labeled as 'low-risk loan' accounts were actually 'high-risk loan' accounts.


## The Resampled Model
The following discusses how well the resampled model predict the 'low-risk loan' and the 'high-risk loan':<br>
The resampled model predicts the 'low-risk loan' ALMOST perfectly with a:<br> 
<ul> 
    <li>precision = 99.99%.<sup>2</sup></li>
    <li>recall = 99.52%.<sup>2</sup></li>
</ul>
Whereas, the resampled model predicts the 'high-risk loan' with some inaccuracy with a:<br>
<ul>
    <li>precision = 87.26%.</li>
    <li>recall = 99.68%.</li>
</ul>
And the resampled model predicted, overall:
<ul>
<li>accuracy = 99.597%<sup style='font-size: 10;'>3</sup></li>
</ul>

#### Missed Opportunity Cost
12.75%<sup>4</sup> of the accounts that the resampled model labeled as 'high-risk loan' accounts were actually 'low-risk loan' accounts.

#### Unexpected High Credit Risk
0.001%<sup>5</sup> of the accounts that the single-sampled model labeled as 'low-risk loan' accounts were actually 'high-risk loan' accounts.


<sup>1</sup><sub style='font-size: 10;'> See the credit_risk_classification.ipynb for the calculation details.</sub>

<sup>2</sup><sub style='font-size: 10;'> The 'sklearn.metrics.classification_report' function rounds this value to 1.00 corresponding to 100% if no explicit statement is given to display more digits after the decimal.</sub>

<sup>3</sup><sub style='font-size: 10; line-height: .7;'> 'accuracy' here is the accuracy obtained from using the 'sklearn.metrics.balanced_accuracy_score' function and not the 'sklearn.metrics.classification_report' function which also has an 'accuracy'. The 'sklearn.metrics.balanced_accuracy_score' is the same as the 'macro average recall' from within the 'sklearn.metrics.classification_report'.</sub>

<sup>4</sup><sub style='font-size: 10;'> This is value is derived from subtracting precision of 'high-risk' loans from 100%. See credit_risk_classification.ipynb file for any further clarity.</sub>

<sup>5</sup><sub style='font-size: 10;'> This is value is derived from subtracting precision of 'low-risk' loans from 100%. See credit_risk_classification.ipynb file for any further clarity.</sub>

---
# Conclusion
The singled-sampled model and the resampled model had nearly identical, perfect results in precision and recall for predicting 'low-risk loans'. However, when considering the precision and recall of the 'high-risk' loans they diverged significantly.<br>
While the 'precision' of the 'high-risk' loans were fairly close for the two models (87.46% and 87.26%), the 'recall' saw a dramatic improvement from the single-sampled model's 89.28% to the resampled model's 99.68%.<br>
Ultimately, the differences in 'high-risk' prediction between these two models could best be captured by comparing the 'Missed Opportunity Cost' and the 'Unexpected High Credit Risk'. 
#### Missed Opportunity Cost
The 'Missed Opportunity' costs were fairly similar with the single-sampled model's 12.57% as compared resampled model's 12.75% for mislabeling 'low-risk' loans as 'high-risk' loans which makes the single-sampled model 1.4% RELATIVELY better than the resampled model at avoiding labelling actual 'low-risk' loans as 'high-risk' loans. 
#### Unexpected High Credit Risk
HOWEVER, the 'Unexpected High Credit Risk' results were dramatically different between the two models. The single-sampled model had an 'Unexpected High Credit Risk' of 0.357%  whereas the resampled model had an 'Unexpected High Credit Risk' of 0.001% which makes the resampled model 35,700% RELATIVELY better than the single-sampled model in avoiding labelling actual 'high-risk' loans as 'low-risk' loans.<br>

#### Recommendation
After considering the findings above, the resampled model outperforms the single-sampled model in dramatic fashion and would spare the company from huge unexpected losses. Trading in a 1.4% improved avoidance of 'missed opportunity cost' for a 35,700% improvement in 'unexpected high credit risk' avoidance is a phenomenal bargain especially considering that it usually takes many successful loans to counterbalance a single unsuccessful loan.<sup>6</sup>

<sup>6</sup><sub style='font-size: 10;'> Here, it's assumed that the interest rates for loans are such that one defaulted loan requires many successfully paid loans to recover from.</sub>