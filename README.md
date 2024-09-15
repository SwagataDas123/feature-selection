# Feature-selection(7th sem)
The filename starting with original word is the 7 th sem work and the one starting with the name new word is the 8 th sem work.
This repository contains a project on feature selection. This project investigates the stability and consistency of filter-based feature selection methods using 21 datasets and  three different methods. The project aims to find mainly similarity and also standard deviation between two different filter based  feature selection concepts or methods(between Mutual Information and Correlation as well as between Mutual Information and Chi2  Test) across those 21 datasets for two different test sizes(20% and 30%).

Proposed Methodology

We are importing all the different libraries needed in our system such as numpy (for working with arrays), pandas (for working with 
datasets), train_test_split (for splitting our data for training and testing), SelectKBest (selecting the best features to match our criteria), 
preprocessing (to make the data ready for our project), mutual_info_classif (for the algorithm of mutual info) and chi2 (for the 
algorithm of chi square test) from sklearn, statistics (for measuring the probabilities, SD and mean from the required features), sns 
from seaborn (for plotting graphs) and math (for all the mathematical calculations).
We import a dataset from the drive and and send this data to func() for further calculations.
In func(), we use LabelEncoder for fitting and transforming the target variable ‘class’. We remove any rows with any sort of null 
values or negative values present in the dataset. 
We need to find out top 20% required columns from the dataset.
We start with training the dataset with a test size of 20% and 30%.By using the correlation function, we find out the columns which 
have a correlation value of 80% between themselves and remove them.
Now, we again form a correlation matrix with the target variable and then extract the top 20% correlated features. Finally, we store it 
in the cfd list.In case of Mutual Information, we fit the model using mutual_info_classif and then sort it into descending order so that 
we get the best 20% among them. We store that in mifd.Now we find the similar features between cfd and mifd which we will use
later to calculate the percentage of similarity and it’s standard deviation.We will be performing the same for Mutual Information and 
Chi Square Test.The entire test will be performed 20 times to find a more accurate result.
All the functions and components have been fully implemented as of now.

![arch drawio (1)](https://github.com/SwagataDas123/feature-selection/assets/84619023/2374afbe-a322-4f59-a5d3-89901a3761c0)

Experimental Setup

The system requirements for the intended setup entail a robust CPU, specifically an AMD Ryzen 7 4800H or an Intel Core i5, or
equivalent, alongside a minimum of 8.00 GB of RAM. Software prerequisites include the utilization of Python 3.7 or later as the 
primary programming language, and the choice between Windows 10 or Ubuntu 18.04 (or newer) as the operating system. Moreover, 
the project necessitates several external libraries/modules to be integrated seamlessly, including NumPy, Pandas, Matplotlib, Scikitlearn, Seaborn, as well as the standard Python modules math and statistics. To ensure smooth execution, users can leverage pip, the 
default Python package manager, for installing and managing these libraries efficiently.
The project is implemented using Python.We have 21 different datasets with various rows and columns.We read one 
dataset at a time and apply the function func to get our desired results. Here we run the code for 20 times and eventually 
calls the functions for 20 times to get our desired results from the work conducted as described above in full details.
We split our 21 datasets for training and testing once in the ratio of 80:20 and then in the ratio of 70:30 percent as 
required. At this point, we come to the end of data preprocessing.Each time the function returns the similarities of 
Correlation-Mutual Information ,Chi Square-Mutual Information and Chi Square-Correlation for 20 times.
Here after we take the data set and we proceed to find the average similarity percentage that is mean and standard 
deviation by using various mathematical metrics in order to get the desired results.
We have analysed the datasets and performed three filter based feature selection: Correlation,Mutual Information and Chi 
Square .We have performed feature selection in two phases: config 1 where 20% is the test size and in config 2 where 
30% is the test size.               


# Feature-selection(8th sem)
This project examines the stability and 
consistency of filter-based feature selection techniques across 21 datasets and three distinct filter 
based feature selection methods. The goal of the project is to determine the average similarity, 
precision, and recall for three pairs of filter-based feature selection methods (Mutual Information 
vs Correlation, Mutual Information vs Chi Square, and Correlation vs Chi Square) across 21 
datasets and five test sizes(10%,20%,30%,40% and 50%). Specifically, we aim to assess how 
consistently these methods identify relevant features across 21 diverse datasets and across 
different test set sizes.


Proposed Methodology

Architecture /Flow Diagram:
The model developed for this project is designed to systematically evaluate the similarity, 
precision and recall of outcomes between three pairs of filter-based feature selection methods, 
Mutual Information and Correlation, Mutual Information and Chi Square as well as Correlation 
and Chi Square on multiple datasets. The architecture of the model can be outlined as follows:

1.Data Loading and Cleaning:
For this project,21 datasets with varying characteristics have been used. All those 21 datasets are 
loaded one at a time and then sent to the function as a parameter where the main work is being 
done. At first Label Encoding is applied for categorical values using the preprocessing library. 
After that some processing is done on the data like checking for null values, negative values, 
missing values and so on and data cleaning is done to handle those issues. Then normalization is 
done on datasets.

2.Feature Selection Function:
Inside the function, all the three feature selection methods are implemented on the training 
dataset after the data has been splitted into training dataset and test dataset using the 
train_test_split function in model selectionlibrary. Here five test sizes have been considered 
which are 10%,20% ,30%,40% and 50%.In this components there are four sub components:

2.1.Correlation:
A sub function is created under which we find out the correlation matrix between the 
columns using correlation function in Pandas library and select only those columns 
whose correlation value is lower than the threshold. This function is called and set the 
threshold value and training dataset as parameters. Columns whose correlation value is 
greater than the threshold are dropped but not in the original dataset. Finally the 
correlation list is sorted in descending order thus showing the most informative features 
at the top and we extract the keys of the columns that is the column numbers and then we 
pick up only 20% of the total columns out of that which are appended in a list named cr.

2.2.Mutual Information:
Mutual information between each feature and the target variable is calculated using the 
mutual_info_classif function in feature_selection library and stored in a Pandas Series 
with feature names as indices. Then the series is sorted in descending order based on 
mutual information values, showing the most informative features at the top. We are 
extracting the keys of the columns that is the column number .Then we are selecting top k 
columns from the series where k in our case is 20% of the total columns which are 
appended in a list named mi.

2.3.Chi Square:
The f-values and p-values are calculated for each feature in the absolute values of the 
training set with respect to the target variable using the chi2 function in feature_selection 
library. f values and p values are converted and stored in different Pandas Series indexed 
by the column names. Then based on f values ,columns are sorted in descending order 
and we extracted the keys of the columns that is the column number . Then we are 
selecting top k columns from the series where k in our case is 20% of the total columns 
which are appended in a list named ch.

2.4 Similarity Calculation:
The list of features selected by correlation and mutual information are copied to another 
list and the same has been done for Mutual Information and Chi Square as well as 
Correlation and Chi Square. Then two dictionaries are created for each case to keep the 
count of occurrences of items of both lists in separate dictionaries. Then the no of 
common items and the no of unique items are counted. The identified similarities are 
returned from the function and function is exited.
 Similarity formula: Similarity = common count/unique count if unique count ≠ 0
Similarity = 0 if unique count =0

3.Iterative Feature Selection:
The function is called 20 times on different datasets using a for loop. The similarities(sub1) 
obtained from mutual information and chi2 square are appended in one list named sl1,the 
similarities(sub2) obtained from mutual information and correlation in another list sl2 and 
similarities(sub3) obtained from chi2 square and correlation in another list sl3 .Thus 20 
similarities are obtained at the end in each of the three cases.

4.Top Most Feature Items Selection:
The provided code consists of two functions: count_item_frequencies and 
extract_top_most_frequent_items. The count_item_frequencies function takes a list of lists 
(list_of_lists) and calculates the frequency of each item across all sublists, storing these 
frequencies in a dictionary. The extract_top_most_frequent_items function then takes this 
frequency dictionary and a number k , sorts the items by their frequencies in descending order, 
and extracts the top k most frequent items. The main script calls the count_item_frequencies 
function with a list of lists and extract_top_most_frequent_items with the frequency dictionary 
outputted by the first function and limit (the number k) which in our case is 20% of the total 
columns in the dataset, and prints the top k most frequent items between the pair of methods. 
This is done for all the three pair of methods. The list of lists in the three different cases are 
represented by arr (containing the features selected by mutual information and chi square),arr1 
(containing the features selected by mutual information and correlation) and arr2(containing the 
features selected by correlation and chi square) and these are globally declared.

5.Precision and Recall:
In this code, the column names of X_train and X_test are reset to a range of integers 
corresponding to their respective number of columns. A GradientBoostingClassifier is then 
instantiated and trained on the training data (X_train) using only the features identified as the top 
most frequent items between the two methods, and the corresponding target labels (y_train). The 
trained model is used to predict labels (y_nu) for the test data (X_test) using the same subset of 
features. The accuracy, precision, and recall of the predictions are calculated and printed. 
Precision and recall are specifically computed using the weighted average to account for class 
imbalances. This is done for all the three pair of methods.

6. Statistical Analysis:
In this component there are two sub components:

6.1. Average Similarity Calculation:
The average of the list representing similarities between mutual information and 
correlation, mutual information and chi square as well as correlation and chi square is 
calculated .

6.2. Average Similarity, Average Precision and Average Recall and Plotting of 
Graphs:
The average similarity , precision and recall of 21 datasets is recorded in all the three 
cases .Then an average value of these three measures are calculated separately which 
leads to average similarity, average precision and average recall for all the three cases. So 
nine such values are inserted into nine different lists and plotted against percent of 
features selected(10%,20% ,30%,40% and 50%) which leads to nine different graphs 
showing the different trends in average similarity ,average precision and average recall in 
accordance with no of features selected.
All the functions and components have been fully implemented as of now.

![image](https://github.com/SwagataDas123/feature-selection/assets/84619023/a330f4fa-a3ae-4a8e-8151-8a34677e5110) 

Algorithm

The project is implemented using Python .We are importing all the different libraries needed in 
our system such as numpy (for working with arrays), pandas (for working with datasets), 
train_test_split (for splitting our data for training and testing), SelectKBest , preprocessing (to 
make the data ready for our project), mutual_info_classif (for the algorithm of mutual info) and 
chi2 (for the algorithm of chi square test) from sklearn, statistics, sns from seaborn (for plotting 
graphs) and math (for all the mathematical calculations), GradientBoostingClassifier, 
accuracy_score, f1_score,classification_report, confusion_matrix.
12
We read one dataset at a time and apply the function func to get our desired results. 
The three cases considered here are Mutual Information and Correlation, Mutual Information and 
Chi2 Square as well as Correlation and Chi2 Square.
Using label encoder, we transform the non-numerical features to numerical ones. After that some 
processing is done on the data like checking for null values, negative values, missing values and 
so on and data cleaning is done to handle those issues. Then normalization is done on datasets. 
We create the train and test variables by dropping the result feature. We split our data for train 
and test in the ratio of 90-10,80-20,70-30,60-40,50-50 percent as required. At this point, we 
come to the end of data preprocessing.
By using the correlation function, we identify all the similar types of features that is highly 
correlated features and drop only those. These features are filtered out by means of a threshold 
value that is if columns have correlation value higher than the threshold then only they are 
dropped. Now we bring the most important features from the top by sorting and and we extract 
the keys of the columns that is the column numbers and then we pick 20% of our dataset from 
those and append into a list named as cr. 
Now comes the mutual information part .We apply this algorithm to our dataset and then we sort 
columns based on f values in decreasing order .We are extracting the keys of the columns that is 
the column number .Then we are selecting top 20% of the total columns from those which are 
appended in a list named mi.
Later, we will use this to calculate the similarity between correlation and mutual information.
Now comes the Chi Square part .The f-values and p-values are calculated for each feature in the 
absolute values of the training set with respect to the target variable using the chi2 function in 
feature_selection library. f values and p values are converted and stored in different Pandas 
Series indexed by the column names. Then based on f values ,columns are sorted in descending 
order and we extracted the keys of the columns that is the column number . Then we are 
selecting top 20% of the total columns from those which are appended in a list named ch.
At last, we calculate the similarity between Chi Square and Mutual Information and between 
correlation and Chi Square.
The function is called 20 times on various datasets using a for loop, appending 
similarities(sub1,sub2,sub3) in lists sl1,sl2,sl3 resulting in 20 similarities for all the three cases. 
Then we find the top most frequent items in the three cases. Then once again data is 
preprocessed and splitted. The precision and recall is calculated in the three cases. The average 
similarity is calculated by taking mean of the similarity lists separately in three cases.
The average similarity , precision and recall of 21 datasets is recorded in all the three cases .Then 
an average value of these three measures are calculated separately which leads to average 
similarity, average precision and average recall for all the three cases, then inserts these values 
into nine lists and plots against per cent of selected features(10%,20% ,30%,40% and 50%), 
resulting in nine different graphs showing trends.
