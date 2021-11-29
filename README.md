# Binary Classification

<p align="center">
  <img width="460" height="300" src="https://media-exp1.licdn.com/dms/image/C510BAQEEBs9SDDcsqg/company-logo_200_200/0/1555057697060?e=1646265600&v=beta&t=GfH5y89gRColK9Lq4JySLTNHU4qTo5XYX1-d8w5SGfM">
</p>

INTRODUCTION-

The task of this assignment is to perform binary classification on the dataset provided.

DATASET-
Following are the 2 datasets were provided for this task-

Training_set.csv = 3910 rows and 59 columns. 57 features are independent and 1 feature is dependent as output class label 0/1 (Y/N). (1 feature is redundant as index/unnamed)

Test_set.csv = 691 observations and 57 columns. For this dataset predictions are to be made.

APPROACH-

Started with statistical description of dataset and also checked null values presence. There were no null values in the dataset.
Since we have 57 features/columns in the dataset for any real world problem of classification task, considering these many features would be incomprehensible to anyone. Complexity constraint is the key because assume that this dataset is for credit card default prediction. Focusing on too many factors will be a cumbersome task. Therefore practically it’s better to reduce these features and consider only those that are important in predicting the final output.

For selecting features, the importance of ExtraTreesclassifier was used. Those top 10 features that were contributing the most in the prediction were selected for further analysis and training purposes. Output of feature importance showed that X21 is the most important feature and the second we have X7.

NOTE- INSTEAD OF TOP 10 TOP 'k' FEATURES CAN BE SELECTED. THIS SELECTION IS SUBJECT TO DOMAIN EXPERT/PROBLEM STATEMENT. 

Created new dataframe only of those top 10 features that were shown by ExtraTreesclassifier. After creating dataframe performed some analysis and removed outliers as another part of data preprocessing. Outlier treatment resulted in 525 fewer observations than the original dataset.

In the dataset class distribution was 35% as 1/y and 65% as 0/n.
Created heatmap to check correlation between features and X25 showed negative correlation with respect to output and other features as well.

After performing EDA, I moved on to the machine learning model implementation part. 
Separated X and y in 80% / 20% (4:1) train and validation. Defined hyperparameters for random forest classifier tuning to achieve optimal performance on the dataset. 
Trained the model on dataset and achieved accuracy of 93% with good (90+) precision, recall and F1 score.  
After implementing RFclassifier feature importance was used to identify how much each feature is contributing in the predictions made by the model so far. As a result X52 turns out to be the most important feature. 
Used Shap to get a more clear idea about the magnitude and direction of each feature in predicting outcome and observed that the higher the value of feature X25 it’ll impact negatively on the output variable we have and vice-versa.   

After completing training on tuned classifier model, I saved the trained model on google drive.
For making predictions loaded the test_set.csv file and imported the trained model.  
Since the dataset again contained 57 features to use in my model I reduced the dimension of data by selecting only those important features on which my model was trained.
Created a dataframe for those columns and fed them into random forest and predictions were made by the model. 
After making predictions, I added a new column in test_set.csv as Y by assigning output class to each observation in the test set. 


CHALLENGES-

Since independent features were anonymously named/labelled, it’s difficult to get the context of the dataset. Had they been assigned by proper naming or some sort of context was provided exploratory data analysis could be improved. Selecting top 10 features by using feature importance are again subject to domain expert/ context of dataset and problem statement.


WHY RANDOM FOREST CLASSIFIER AND ACCURACY?

Since random forest is a non-parametric approach (no assumptions) it's better to use RF here.
Also scaling is not required in random forest so we can use our training and test dataset without further modifications.
Since we don’t have an imbalance dataset in this problem statement we can go with accuracy as our evaluation metric. If there was a scenario of an imbalanced dataset then techniques like over/under sampling , SMOTE etc. could be used and instead of accuracy other evaluation metrics such as precision, recall, f1 score can be selected in order to evaluate the performance of the model.    
    


 
          


          


