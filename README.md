# Airbnb-Berlin Price Prediction
## Context
This project aims to predict the price of a night’s accommodation offered on the short-
term rental website Airbnb in the city of Berlin. The project is derived from a data
challenge proposed by dphi.tech.
We are given 2 datasets:
- **labeled**: ‘train-airbnb-berlin.xls’ (training, testing)
- **unlabeled**: ‘test-airbnb-berlin.xls’ (prediction)
The available labeled dataset contains 15 692 entries and 38 raw explanatory features.
The **Price** variable is the target

## Stratified Train-Test split
To split our dataset into a training and test sets, we decided to take **70%** of the data as training and **30%** as test data.

To ensure an unbiased split, we applied a stratified split using an intermediate variable called **Price Range**.

This variable is representative of the price intervals that we determined by analyzing the distribution of the price.

The distribution of price shows that 75% of the entries have a price less than 100 and a small percentage of the entries are above 200. So we decided to work with the following segmentation: [0,25,50,75,100,125,150,200,1000].

Finally, using the function train_test_split of the module sklearn.model_selection with the argument test_size equal to 0.3 and the argument stratified set to the column **Price Range** we get our training and test sets.

## Model selection
We trained and evaluated several machine learning models using 5-fold cross validation with the root mean square error **RMSE** metric. 

In the initial evaluation round, the best performing models were gradient boosting and random forest, with an RMSE of approximately 39. We then performed hyperparameter tuning on those two models, obtaining an RMSE of approximately 38.5.

This constitutes a small improvement over the previous model and shows that the default hyperparameter values were already reasonable for our training data.