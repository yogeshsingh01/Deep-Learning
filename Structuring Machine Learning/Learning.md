#Why ML strategy?
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

#Orthogonalization
Orthogonalization is design property that assure modifying one component of
algorithm will not propagate side effect on other component.

#Chain of assumption in Machine learning
* To fit training set well on cost function - Bigger Network, Change Optimization.
* To fit dev set on cost function - Regularization, Bigger training set.
* Fit test set on cost function - Bigger Dev Test.
* Perform well in real world application - Change either dev set or cost function.

#Single Number Evaluation Metric
This allow us to quicker assessment of our algorithm.

| Classifier | Precision | Recall |
| ---------- | --------- | -------|
|    A       |    95%    |   90%  |
|    B       |    98%    |   85%  |
| ------------------------------- |

By precision we mean what percentage are actually things which are identified.
By recall we mean percentage are true positive among recognized ones.
Precision = True Positive / Actual Result = True Positive / (True Positive + False Positive)
Recall    = True Positive / Predicted Result = True Positive / (True Positive + False Negative)

Having two metric make it difficult for us to choose what to prefer.
For this we have F1 score.
F1 score is Harmonic mean Precision and Recall.
F1 Score = (2/(1/P + 1/R))

#Satisficing and Optimizing Metric
| Classifier | Accuracy  | Time    |
| ---------- | --------- | ------- |
|    A       |    90%    |   80ms  |
|    B       |    92%    |   95ms  |
|    C       |    95%    |   1500ms|
| ---------------------------------|

Overall cost = accuracy - 0.5 * running Time

Let's say customer demand maximum accuracy but running time should be
less than 100ms.

So here, accuracy is Optimizing while running time is satisficing metric.

If there are N metric, then there should be one Optimizing and other  satisficing metric.

#Train/Dev/Test distribution
The training and development (or holdout) sets are used to train a model. The training set is usually used to fit the model to the data, and the development set is used to make predictions and tweak the model.

Then, the test set is an example of real-life data on which you test the algorithm to see how it would perform.

Dev and Test set should come from same distribution.
 ____________________________ _________________
|_____70% Train______________|___30% Test______|
was used when dataset was smaller

_______________________________________________
|_____60% Train_____|___20% Dev_|____20% Test__|
If data is around 1000,10000

_______________________________________________
|_____98% Train_____|___1% Dev_|____1% Test____|
As now a days data is in millions

Test set help us evaluate how good our system performance.

Dev set are meant for better tune-in of system.

#When to change dev/test set and metrics
If doing well on your metric plus dev/test set doesn't correspond to
doing well on application, we have to change metric/dev/test set.

Error: 1/m_dev E(Loss)
Let say our application doing great, but something it show nsfw images.
Then in those cases we should add one more variable in our metric.

Error: 1/m_dev E(Wi)(Loss)
Wi { 1, if x is no porn. 100, if x is porn}  

#Comparing to human level performance
* Bayes Optimal Error - Best possible performance( No way any function can surpass it).
* Avoidable Bias - Difference b/w Human and Training is avoidable bias.

#Surpassing Human Level performance
With structured data most ML surpass Human level performance.
Human are very good natural preceptor.

#Improving your Model Peformance

Human
 |        Avoidable Bias{ Train Bigger model, Train longer/Better       
 |                       Optimization algo - momentum , RMS prop, ADAM
 |                        , NN architecture, Hyperparameter search}
Training
 |        Variance {More Data, Regularization - dropout, data augmentation, NN                     
 |                  architecture,perparameter           search}
Dev
