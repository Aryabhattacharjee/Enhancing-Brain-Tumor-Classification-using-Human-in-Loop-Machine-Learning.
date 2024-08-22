# HIML-In-Action
## Motivation
• There are many domains where machine learning has not achieved human level performance.  
• In many of these domains even small errors may result in catastrophe.  
• However the number of human experts capable of doing the tasks is limited.  
• So we propose a method that brings machine power and human expertise together.  
• In our proposed method we predict the majority samples with machine.  
• We reserve the machine uncertain samples for human experts.  
• By using machine for predicting samples that the machine is more confident in, we are reducing error.  
• By giving limited number of samples we are also reducing the load on human experts.  
• Here we have chosen the medical domain of predicting tumor categories as our domain of interest.  
  
  
## Dataset
• We have collected our dataset from kaggle. Link:- https://www.kaggle.com/datasets/prathamgrover/brain-tumor-classification  
• Our Data consists of 3027 human brain mri scan images.  
• There are four classes of images in the dataset.  
![image](https://github.com/user-attachments/assets/b41da66a-18f8-422a-b16c-25fa1bf5f72e)  

## Model Roadmap
• First we have trained a tumor classification model on our dataset and made it as refined as we could and made sure it doesn’t overfit the data.  
• Then we iteratively removed the samples which caused the most training loss.  
• We train our model on the reduced dataset.  
• Now when the training accuracy is equal or near to 100%. We stop the process.  
• We now have two type of data. The reduced data is labeled as machine and the collection of removed image is labeled as human.  
• We trained another model to classify if a new image should go to machine or human.  
• Then a collection of new image is sent to the second model and see the outcome.  
• If its outcome is machine, we sent that image to be predicted by ml model.  
• Otherwise it is sent to human experts to predict.  

![image](https://github.com/user-attachments/assets/6b6f167d-fc32-44c8-8342-be01c870a86e)  
## Result
• Best hyperparameter tuned independent model we got lasso SoftMax regression which gives these accuracy  
train 90%  
validation 85%  
test 86%  
• Performance of Human-Machine assignment classifier when we are satisfied with train accuracy  
train 100%  
validation 86%  
• Human Assisted brain tumor classifier intelligently chooses 24 % test images to human experts and rest to machine. When machine predicts on images send to machine test accuracy goes to 97%.  
• To find if the Human Machine classifier is working good enough or not we ran our tumor classifier model on the images sent to human and it gives 36% accuracy (low is better).
