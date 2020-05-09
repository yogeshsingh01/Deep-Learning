# Why ML strategy?
There are so many thing we can do to  improve accuracy of our ML model.
* Collect more data.
* Collect more diverse training set.
* Train algorithm longer with gradient descent.
* Try Adam instead of gradient descent.
* Try bigger network.
* Try smaller network (over fitting).
* Try dropout, L2 regularization.
* Changing network architecture - Activation Function, Hidden Unit etc.

Some of these take a lot of time and hence we should have strategy, so that
we don't waste much of our time.

# Orthogonalization
Orthogonalization is design property that assure modifying one component of
algorithm will not propagate side effect on other component.

# Chain of assumption in Machine learning
* To fit training set well on cost function - Bigger Network, Change Optimization.
* To fit dev set on cost function - Regularization, Bigger training set.
* Fit test set on cost function - Bigger Dev Test.
* Perform well in real world application - Change either dev set or cost function.

# Single Number Evaluation Metric
This allow us to quicker assessment of our algorithm.

| Classifier | Precision | Recall |
| ---------- | --------- | -------|
|    A       |    95%    |   90%  |
|    B       |    98%    |   85%  |
| -----------|-----------| -------|

By precision we mean what percentage are actually things which are identified.
By recall we mean percentage are true positive among recognized ones.
Precision = True Positive / Actual Result = True Positive / (True Positive + False Positive)
Recall    = True Positive / Predicted Result = True Positive / (True Positive + False Negative)

Having two metric make it difficult for us to choose what to prefer.
For this we have F1 score.
F1 score is Harmonic mean Precision and Recall.
*F1 Score = (2/(1/P + 1/R))*

# Satisficing and Optimizing Metric
| Classifier | Accuracy  | Time    |
| ---------- | --------- | ------- |
|    A       |    90%    |   80ms  |
|    B       |    92%    |   95ms  |
|    C       |    95%    |   1500ms|
| -----------| --------- |---------|

*Overall cost = accuracy - 0.5 * running Time*

Let's say customer demand maximum accuracy but running time should be
less than 100ms.

So here, accuracy is Optimizing while running time is satisficing metric.

If there are N metric, then there should be one Optimizing and other  satisficing metric.

# Train/Dev/Test distribution
The training and development (or holdout) sets are used to train a model. The training set is usually used to fit the model to the data, and the development set is used to make predictions and tweak the model.

Then, the test set is an example of real-life data on which you test the algorithm to see how it would perform.

Dev and Test set should come from same distribution.

| 70% Train  | 30% Test  |
| ---------- | --------- |
was used when dataset was smaller

| 60% Train  | 30% Dev  | 30% Test |
| ---------- | ---------| ---------|
If data is around 1000,10000

| 98% Train  | 1% Dev  | 1% Test |
| ---------- | ---------| ---------|
As now a days data is in millions

Test set help us evaluate how good our system performance.

Dev set are meant for better tune-in of system.

# When to change dev/test set and metrics
If doing well on your metric plus dev/test set doesn't correspond to
doing well on application, we have to change metric/dev/test set.

**Error: 1/m_dev E(Loss)**
Let say our application doing great, but something it show nsfw images.
Then in those cases we should add one more variable in our metric.

**Error: 1/m_dev E(Wi)(Loss)**
Wi { 1, if x is no porn. 100, if x is porn}  

# Comparing to human level performance
* Bayes Optimal Error - Best possible performance( No way any function can surpass it).
* Avoidable Bias - Difference b/w Human and Training is avoidable bias.

# Surpassing Human Level performance
With structured data most ML surpass Human level performance.
Human are very good natural preceptor.

# Improving your Model Peformance

Difference between Human and Training performance -
**Avoidable Bias** can be reduced by **Train Bigger model, Train longer/Better, Optimization algo - momentum ,
 RMS prop, ADAM , NN architecture, Hyperparameter search**

Difference between  Training and Dev performance -
**Variance** can be reduced by **More Data, Regularization - dropout, data augmentation, NN architecture, Hyperparameter  search**.

# Error Analysis
Should we try to make cat classifier do better on dogs
* Get ~ 100 mislabeled dev set example.
* Count how many are dogs
If 5% are dogs then it might not be good use of our time.
If 50% are dogs then it would worth of time, as it will improve performance by 50%

TO carry out error analysis, find a set of mislabeled in dev set and looked for false positive and false negative.

ML are quite robust for random error.
Systematic error are a problem.

**Building our first system quickly and then iterate**
* Set up dev/test set and metric.
* Build initial system quickly.
* Use bias / variance to decide next step.

# Mismatch training and dev sets
Let say we have 10000 cat pics from user. We have 200k from web.
* Option 1 - We use all and shuffle them in dev/train/test.
* Option 2 - We have 200k in train and 5000 from user in training set.
  2500/2500 in dev /test case.

In option 1, we are not targeting on end result, while in option 2 we are focusing on end result by having user data in dev and test.

# Bias and Variance with mismatch data distribution
| Human Level Error         |                         |
|---------------------------|-------------------------|
| Training level Error      | Avoidable Bias          |
| Training Dev Level Error  | Variance                |
| Dev level Error           | Data mismatch           |
| Test Level Error          | Degree of Over fitting  |

* Carry out manual error analysis to try to understand b/w traing and dev/test set.
* Make Training data similar tp dev/test set.

# Artificial Data Synthesis
If we don't have enough data for end product, we can also generate data artificially.
Let say end user environment is full of noise then we can add noise in data to synthesize data for training.
However, we have to be cautious that we don't have enough noise, then we might be overfitting.

# Transfer Learning
If task A and B have same input and low level feature then we can use learning from A for B.
It should be used only if we don't have enough data for B.
Basically all internal layer are same, just outer layer will be changed.

# Multi Task Learning
Let say image have many labels. Making different NN for each label will be waste of resources as all low level features are same.
In this case we can train big Neural Network to do well on all Task
e.g. **Computer Vision**

# End to End Learning

Audio transcript
Audio -- MFCC --> Features -- ML --> Phonemes ---> Words --> transcript

Instead EOE will do Audio ---> transcript in one go.

**Pro** Let data speak, Less hand designing of component.
**Cons** Need vary large data set  required.
