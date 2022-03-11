# Neural Network Charity Analysis

## Project Overview
In this project I created a binary classifier to predict whether Alphabet Soup's funding to each applicant would be successful or not.  Before creating the model I preprocessed the dataset by removing a couple columns and organizing some of the categorical data into bins.  Then I split the data into training and testing sets and standardized the numerical data.  Finally I compiled and trained the model using a deep neural network, after which I evaluated the model's performance.

## Results

### Data Preprocessing
- The target variable in this case was the values in the IS_SUCCESSFUL column, since we want to predict whether or nor the funding was a success.
- The features were APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS and ASK_AMT.  
- The variables that were not needed in the model were EIN (the identification number) and NAME (the name of the organization).

### Compilation, Training & Evaluation
- For my initial model I used two hidden layers and one output layer. The number of neurons for the first hidden layer was 80, due to the large set of training data, and the number for the second layer was 30, in order for a smaller number of neurons to take in the outputs from the previous layer and try to evaluate interactions between the weighted variables to a higher degree.  I used the relu activation function (better for bigger learning models) for both hidden layers and the sigmoid function for the output layer (since it returns the output as a range between 0 and 1).

![initial model](https://github.com/MaxV6ft4/Neural_Network_Charity_Analysis/blob/main/Screenshots/Initial_model.png)

- The initial model resulted in a accuracy of 72.5%, below the goal of >75%.
- I made three attempts to optimize the model in hopes of better performance.  
  - First I increased the number of neurons in the second hidden layer to 50 and changed the hidden layer activation functions from relu to tanh.
  
  ![extra layers](https://github.com/MaxV6ft4/Neural_Network_Charity_Analysis/blob/main/Screenshots/Extra_layers.png)
  
  - For the second attempt I added a third hidden layer that also featured 50 neurons in an attempt to further evaulate the interactions between the weighted variables.  I also increased the number of epochs from 100 to 150. 
  
  ![modified model](https://github.com/MaxV6ft4/Neural_Network_Charity_Analysis/blob/main/Screenshots/Modified_model.png)
  
  - Both of these attempts resulted in the same accuracy score of 72.5%.  
  - For the third attempt I went back to the original dataset to see if any additional variables could be removed from the features.  In the end, I decided to remove AFFILIATION and ORGANIZATION.  Using the layers, neurons and activation functions from my first attempt (since adding more and changing the functions/epochs proved fruitless), I created a new model with fewer features to compile, train and evaluate but the plan backfired.  The accuracy decreased by 10%. 

## Summary
The model I created resulted in an accuracy a few percentiles below the targeted result when performing at its best.  With a few more attempts I believe I would be able to increase this model's performance, but I also believe that a non-deep learning model could work well with this dataset, specifically a support vector machine.  SVMs can interpret nonlinear data and produce one and only one output vs. neural networks' ability to produce many outputs.  In addition, our problem is a binary classification problem.  SVMs work well with these because they do not converge on a local minimum and are less prone to overfitting than neural networks.
