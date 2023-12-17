# cities-classifier
An algorithm for accurately predicting the city in which a given image was taken:
https://cities19test.herokuapp.com/

![alt text](https://github.com/dormeir999/cities-classifier/blob/master/example.JPG)

See a youtube demonstration of the tool [in here](https://www.youtube.com/watch?v=5G2upntY03A&ab_channel=ChaySharaby)

## team members 
Arad, Itamar, Dor, Daniel, Sagi

## Project name & one-line description of achievements

Classifying cities by images.
The classifier is doing a good job especially in suburbs and highways of cities, where it is more difficult for a human to distinguish between different cities.

## The final results in detail (include all relevant steps and moving pieces, techniques you tried, metrics that you achieved, etc)

Classifying the right city on the test data of Mapillary with 93% accuracy. For out of our data set image The moving pieces of the model included these steps:
Defining the problem
Getting a dataset
Sampling from dataset - adapting to our needs / problem
Data pipeline to serve the sampled images:
Data generator
Tensor flow Dataset
Pre-processing of images:
Black and white
Data augmentation
Resizing for different image sizes
Data augmentation
De-noising and outlier detection with auto-encoder
Modeling
Tried several networks architecture
Transfer learning, several attempts
LeNet
ResNet
MobileNet
InceptionV3
VGG16
Hyper-Parameter tuning:
Learning rate
Optimizers
Batch sizes
Interpretation:
Lime super-pixels:
Visualizing that for different images when the model is sure about his decision and making a false prediction and also to try to see when the model is sure about the decision and getting positive prediction.
Feature map visualizing to try to understand how the model process images, and what is important
Different Kernels visualizing
Measuring performance metrics:
Val accuracy
Test set
Precision/ Recall/ Accuracy
Trying Images from different datasets (StreetView/ random images..)
Top 1 vs. Top 5 accuracy on different models
Still having generalization issues that 
Serving our model
Deploying our model on Heroku server
https://cities19test.herokuapp.com/
Letting the user upload image
Showing him the first score, and then the 4 most probable cities.
Showing the user the lime explainer next to the original picture 
GAN attempt
	
## Results from both a technical and business strategy perspective.
### Technical:
Great success on the Mapillary - 93% accuracy on 19 classes on pictures that the model has never seen before.
Partial success on out of dataset images - we are estimating around 80% success on unseen images from suburbs and highways, and much lower on city centers and it differs with each city (diverse in pictures of not in the dataset).
We still haven’t established a big enough and solid dataset to test those assumptions regarding out of dataset photos.
### Business:
Identifying the city with features that humans are not able to!
Not identifying well landmarks
https://cities19test.herokuapp.com/

## The 3 largest challenges that the team had to overcome to build this (especially unexpected challenges):
Data preprocessing 
Adapting dataset to our needs
Allow easy access to images
Preprocessing Affecting time performance
Preprocessing Affecting accuracy performance
Outlier detection, convolutioned and rule based
Generalization
Images are not very representative of what we consider to be the city
Research challenges - 
Finding the right platforms - colab - copy of notebooks
Splitting research on same project for 5 ppl
Challenge of documenting research process

## What we would have done differently if you were to start from the beginning

Better definition of the business problem:
We started our research without a specific business problem but with the ambition of finding out how far we can stretch the classification abilities of CNN. The result is pretty impressive. Nevertheless, having a well defined business problem could have served us as a guideline that would have helped us improve our model on specific tasks.

Spend more time on EDA and work on improving the input data: 
The mapillary dataset consists mostly of images taken out of driving cars. It would have been nice to do more EDA on the images and split them into different groups, like highways, parks and trees, suburban or city center. We would analyse how many pictures of each type we have per city and could compare the performance of the prediction per class or try to enrich our data set accordingly.

Agree on benchmarks and metrics to train and evaluate models:
We trained and tested many different models. Retrospectively we would predefine our (hyper-)parameters, such as input size, batch size, loss functions to make our results comparable. Further we should have logged all our results to be able to monitor progress. 

## Next steps:
We discovered that certain cities (like Ottawa, Copenhagen, Helsinki) are working quite well on out of data pictures. For other cities (like Paris, Moscow, Budapest) predictions for screenshots, that were taken from google maps, where often predicted falsely (even though the city usually appears within the top 5 predictions).
 
Therefore we would to improve our project by introducing active learning, a semi-supervised training method. 

A second strategy would focus on introducing more images of iconic places and characteristic architectural features into the training data. 


POC of the project:
https://docs.google.com/presentation/d/1tJi9oaRTegFKCR7S73Av9yoi-Q46SxQXEpb5iYw6dFE/edit?usp=sharing
