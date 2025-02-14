# Project goal
- This porject explores three different learning algorithms under various train-test splits, hyperparameters, and datasets. 

# Datasets:
- Data was sourced from the UCI Machine Learning Repository


❖ Iris:
➢ The Iris dataset was choses as a baseline for very basic data and to compare the
classification performance on smaller datasets.
➢ There were 150 instances with 4 numerical features. These features included sepal length,
sepal width, petal length, petal width. The two-class classification was based on whether
the plant iris was setose or versicolor/virginica; 1 if setose, -1 else.


❖ Abalone:
➢ The abalone dataset was chosen due to its diverse choices on how one could predict the
age of the abalone based on many physical attributes.
➢ There were 4,177 instances with 8 features and 1 classifier column. The features were
Sex, (categorical: Male, Female, Infant), Length, Diameter, Height, Whole weight,
Shucked weight, Viscera weight, Shell weight, and Rings (the output and the indicator of
age). All features were continuous data types (excluding sex which was categorical).
➢ The two-class classification was based on the median age (Rings) of the dataset; 1 if >=
threshold, -1 else.


❖ MPG (miles per gallon):
➢ This dataset was chosen as a middle ground between the two datasets as it is much
smaller compared to Abalone, but more complex compared to Iris.
➢ There were 398 instances with 7 features and 1 output column. The features were
Cylinders, Displacement, Horsepower, Weight, Acceleration, Model Y ear, Origin, and
mpg (output). All features were numeric (excluding origin which was categorical).
➢ The two-class classification was based on the median mpg of the dataset; 1 if >=
threshold, -1 else

# Preprocessing:
➢ After loading in the datasets and selecting/defining the columns, missing values were
removed or replaced
➢ The classification threshold was then applied to the entire set
➢ StandardScaler() was then applied to the data in order to standardize all features in order
to avoid disproportionate influence of some features over others.

# Models: 
The parameters were chosen to optimize were the most influential on test/train
accuracy and impacted the classification of the data the most

➢ Svm - a powerful algorithm for classification and regression that finds the optimal
boundary that maximizes the margin between classes.

➢ Random Forest- an ensemble of multiple Decision Trees where each tree is trained on a
random subset of data and features. Predictions are made by aggregating the outputs (e.g.,
majority vote for classification)

➢ Decision Tree - a tree-like structure where internal nodes represent conditions on
features, branches represent outcomes, and leaf nodes represent predictions.


# Algorithm Development:
➢ In order to introduce some novelty into my classifier implementation, I made
functions in order to automate the implementation and optimal parameter
extraction. This vastly streamlined the process of fitting each dataset to the
classifier and easily extracting objects needed for accuracy scoring.
➢ I was finding it tedious to iteratively implement the grid_search function for each
dataset and each partition so I wrote a simple code that defined the classifier
type and ran a grid search to find the optimal parameters all in one.


# Data Partitioning:
➢ Each dataset was split into 3 main partitions in order to compare performance based on
quantity of training and testing data
■ (80/20) 80% of the data was training data and 20% testing
■ (20/80) 20% of the data was training data and 80% testing
■ (50/50) 50% of the data was training data and 50% testing
# Evaluation parameters:
➢ The classification accuracy was the main result I was looking for across all classifiers,
data, and partitions
➢ Testing, Training, and Validation accuracies are reported for all data-classifier
configurations


# Results
❖ SVM:
➢ performed well for all data and partitions, especially for the Iris data due to its smaller
size.
➢ The highest training accuracy was 97% on the Iris dataset with data partitioning (80/20).
➢ Cross validation scores remained high for all partitions.
➢ The average highest C - values was 10 for all datasets but varied from 1 to 100.

❖ Random Forest:
➢ Performed very well on datasets of all sizes with a highest test accuracy score of 95%
percent on the iris dataset at (20/80) partitioning
➢ V alidation accuracy was good across all partitions and datasets
➢ Optimal hyperparameters stayed near a C - values of 3 but did go higher at times, the
n_estimators varied a lot depending on the data size and partition.

❖ Decision Tree:
➢ Performed well on datasets but favored the smaller and simpler iris dataset.
➢ V alidation accuracy was lower on average compared to the other classifiers and had some
bottle-necks when optimizing the parameters but over very good performance.
➢ Optimal hyperparameters stayed similar with max_depth staying below 10.


# Comparison
➢ Key Insights - The disparities between the generated hyper parameters
gathered by .best_params_ and the mean test accuracies reflected in the
classifiers heat maps. The heat maps can show the exact parameter
combination that would result in the highest mean accuracy but that
doesn't necessarily mean that the hyperparameter combination is optimal
for the model as a whole. Oftentimes an intelligent learning algorithm will
choose parameters that maximize the generalizability of their performance
rather than pure maximization of train, test, validation accuracy.
➢ Performance - Each classifier performed very well on each dataset but
some favored datasets with specific characteristics such as size,
complexity, and data type. For example SVM performed best on the iris
dataset as that is the optimal dataset for SVM’s architecture. Conversely
Random forest performed best on the MPG data set, boasting an average
of 92% test accuracy between all partitions. Decision tree performed best
on the Iris dataset as well as its better on smaller datasets and is flexible
due to its branching decision making architecture. Decision tree struggled
with overfitting on the Iris dataset but only with the validation scores
which is to be expected.
➢ Partitions - this aspect provided an interesting insight into how these
models perform based on that learning. The (20/80) typically displayed
lower average test accuracies which was to be expected and allowed me to
study the requirements these models need in order to perform to the best
of their ability
