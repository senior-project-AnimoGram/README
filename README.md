# Animogram
가천대학교 소프트웨어학과 졸업작품

지도 교수 : 이주형 교수님

## 프로젝트 개요
**Animogram** : A compound word of animal, emotion, and instagram; a SNS that shares photos that recognize the emotions of your pets.

![animogram_function](https://github.com/senior-project-AnimoGram/README/blob/main/animogram_1.jpg)
+ Recognition of a pet's facial expression and breed

![animogram_function2](https://github.com/senior-project-AnimoGram/README/blob/main/animogram_2.jpg)
+ Provide filters that fit the emotions

+ Provide statistics on emotional changes according to location
## Installation 환경

## Library

## AI Model
![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/fae28300-3662-4d87-86f2-354d8afc1e3d)

+ Dataset : <https://www.kaggle.com/datasets/mohamedchahed/dog-breeds>
  + 541 images with 8 categories of breeds
 
  
+ Base Model : Inception V3 Model
  + Pre-trained weights up to mixed10 layers were used.
  + For transfer learning, a custom top layer was added to the last output layer of the pretrained model.
  + In the custom top layer,
    + First, we use a Flatten layer to flatten the features into one dimension.
    + Second, we apply the ReLU activation function to the dense layer with 512 neurons.
    + Third, to prevent overfitting, we use a dropout layer and apply a dropout rate of 20%.
  + The final output layer has neurons corresponding to the number of dog breeds and performs multiple classification using a Softmax activation function.
 
+ Model training
  + Data Preparation and Augmentation : Load and preprocess image data using ImageDataGenerator.
  + Construct training and validation datasets : By using flow_from_directory method
  + Take advantage of pre-trained models : Load InceptionV3 model with pretrained weights (imagenet)
  + Add custom top layer : Add a custom top layer to the last output layer of the pretrained model for transfer learning.
  + Compilation and callback settings : val_accuracy, val_loss, ReduceLROnPlateau, EarlyStopping

+ Performance Evaluation : Accuracy of the model is 94.3396%
![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/773a4516-7541-4b2b-914b-32a8ed372df8)
![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/48eb1f70-e104-4fc8-b0ca-9d0fc8d36e09)





![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/b2fef6c8-9796-4b61-a3c8-3e9f46e58af3)




## 예제코드 
