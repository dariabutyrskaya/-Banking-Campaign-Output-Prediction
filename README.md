# -Banking-Campaign-Output-Prediction

<b>Introduction</b>

The data given is related with direct marketing campaigns of a banking institution. The goal of this mini project is to train a Neural Network Model in order to predict whether a client would respond positive or negative to the campaign and subscribe to a term bank deposit.
Note: the project was done in Google Colab, therefore before running the code you need to put .csv file into Google Colab explorer. 

<b>Data processing</b>
  
The data was checked on/got rid off:
  
1.	Duplicates
  
2.	“unknown” values
  
3.	Null values
  
Deposit data was found to be unbalance, much more people do not subscribe to deposit. 
  
![image](https://user-images.githubusercontent.com/90958123/156230218-e644b630-3a93-4630-ba47-ed668253630e.png)

 
Fig. 1. Deposit distribution overall. 

Furthermore, the features were correlated with deposit information (fig. 2,3,4, 5). For full analysis of categories please look into the google colab notebook. 

 
  ![image](https://user-images.githubusercontent.com/90958123/156230260-7131e10e-136d-4361-9dd4-568bd96c64b2.png)

  
Fig. 2. Deposit distribution in every feature. 

 ![image](https://user-images.githubusercontent.com/90958123/156230288-df69fadb-f457-4059-b5bf-570c283a8c5f.png)
![image](https://user-images.githubusercontent.com/90958123/156230305-cd4334b2-3748-4b86-9096-4bc9e8dab9fb.png)

 
Fig. 3. Deposit distribution in every feature. 

  ![image](https://user-images.githubusercontent.com/90958123/156230325-ee90ec4b-169c-4352-b4ce-84ffa45e8d2b.png)

 
Fig. 4. Heat map
 
  ![image](https://user-images.githubusercontent.com/90958123/156230394-b0018d0e-a45e-4f3b-add8-d639ef23dcff.png)

  
Fig. 5. Box plot visualization for age. 
  
Conclusion: overall, we can see that from all clients old people are more responsive to a deposit marketing. Also we note that emp.var.rate, cons.price.idx, euribor3m and nr.employed are features with very high correlation to deposit status!
  
Now we need to process the data before using it to train model. The categories duration, campaign, month, day_of_week, contact were dropped because they were no relevant to prediction deposit status of a client. 
  
Because we have categorical data it was decided to use One Hot Encoding to make the data more useful and expressive, and it can be rescaled easily. By using numeric values, we more easily determine a probability for the values. Example of One Hot Encoded data we can see in fig. 6.

 
  ![image](https://user-images.githubusercontent.com/90958123/156230438-27dc84ea-0be4-4f20-944a-ed27f835829e.png)

  
Fig. 6. One Hot Encoded data. 
The data is ready for creating the model.


  <b>Modelling</b>
  
For network modelling I used Keras, an open-source software library that provides a Python interface for artificial neural networks. Performance of the model was improved by changing selecting features and deleting irrelevant ones (for examples, ‘contact’).
The performance of model was evaluated. The accuracy for test set reached 0.8569, and the difference between train set accuracy and test set accuracy was not big, meaning the model wasn’t overfitted.
 
  ![image](https://user-images.githubusercontent.com/90958123/156230477-87312f27-325b-4194-a6e4-e3ce0e043ce0.png)

  
Fig. 7. Accuracy scores of the model. 

Model also was checked for AUC and ROC curve. Higher the AUC value, higher the performance of the model. AUC for the train set is 0.7219. Note, that it is not the accuracy of the model. 

  ![image](https://user-images.githubusercontent.com/90958123/156230497-af6d56e3-8b5b-4f86-a44f-b66dca4a2e0d.png)

 
Fig. 7. AUC scores of the model. 

As for the ROC curve, it was visualized:
 
  
  ![image](https://user-images.githubusercontent.com/90958123/156230512-f8be93b5-89d4-4080-a1de-45e3c28339f7.png)

  
Fig. 8. ROC plot.
  
  
Furthermore, the network architecture was also visualized with the help of keras.utils:
 
  
  ![image](https://user-images.githubusercontent.com/90958123/156230617-4d02a8f9-4679-4193-affb-cc6230f9226a.png)

  
  
Fig. 9. Network architecture.

  
  <b>Conclusion</b>
  
During the work on project, there were several bottlenecks. 
  
•	The data type
  
Most variable of dataset were categorical, but machine learning and deep learning models, like those in Keras, require all input and output variables to be numeric. For that reason, I used One Hot Encoding to encode data into numeric variables. Another approach is to use other methods of encoding, such as Embedding Categorical Data and others.
  
•	Network visualization
  
Unfortunately, beautiful visualizer ANN_viz is not supported by Keras anymore, therefore I have to find another way to visualize the network. So I used keras.utils embedded visualization. 
  
In the conclusion, a Neural Network Model was built and used to predict deposit status for clients. 


