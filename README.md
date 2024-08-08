# Kaggle house prices competition (0.13 score 1075 on leaderboard upon submission

## Table of contents
- importing necessary
- loading data
- descriptive analytics
- cleaning data
- encoding categorical data
- transforming data
- running model
- choosing best model
- submission

### importing necessary libraries and modules
For this project statistical models of scikit learn were mainly used. Even though TensorFlow and PyTorch offer more robust ML algorithms, for their simplisity and explainability Scikit library was chosen. Plots are drawn using matplotlib and seaborn. Finally mean squred error as an indicator of fit is used from scikit learn's metrics library.

### loading data
data is read to pandas using .read_csv() method. train.csv contains data points for training. Test.csv correspondingly contains data for testing. Files are contained within corresponding directory.

### descriptive analytics
```
train_df['SalePrice'].describe().round()
```
produces:

```
count      1460.0
mean     180921.0
std       79443.0
min       34900.0
25%      129975.0
50%      163000.0
75%      214000.0
max      755000.0

```

So we have 1460 data points (some of them will be truncated of course). Mean price is $180K with standard deviation of $79K, which means our data is pretty skewed. This also can be seen in the graph price-dist.png.
Data type distribution is as follows:
```
object: 43
int64: 35
float64: 3
```
We need to transform the dataframe by encoding the categorical aka objec data type columns.

### cleaning data
Data cleaning in our case involved the following:
- doin away with outlier data points
- dropping attributes with too many null values
- dropping attributes with too high correlation with each other (dropped one of them)
We were able to spot the outliers by looking at their graphs individually agains SalePrice. In that manner we found these data points with exceptional values
```
[598, 955, 935, 1299, 250, 314, 336, 707, 379, 1183, 692, 186, 441, 186, 524, 739, 598, 955, 636, 1062, 1191, 496, 198, 1338]
```
and concequently deleted them from our data frame.

Following columns had too many Null values:
```
PoolQC          1435
MiscFeature     1388
Alley           1350
Fence           1162
MasVnrType       861
FireplaceQu      684
LotFrontage      255
```
thus were dropped.

Following attributes had too high correlation thus were eliminated:
```
GarageCars   GarageArea      0.885534
GrLivArea    TotRmsAbvGrd    0.831634

['GarageCars', 'TotRmsAbvGrd'] were gone
```


