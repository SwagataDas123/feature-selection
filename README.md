# Feature-selection
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
30% is the test size
