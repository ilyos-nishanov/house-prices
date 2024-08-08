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
train_df['SalePrice'].describe()
```

