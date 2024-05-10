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
 
+ Model Training
  + Data Preparation and Augmentation : Load and preprocess image data using ImageDataGenerator.
  + Construct training and validation datasets : By using flow_from_directory method
  + Take advantage of pre-trained models : Load InceptionV3 model with pretrained weights (imagenet)
  + Add custom top layer : Add a custom top layer to the last output layer of the pretrained model for transfer learning.
  + Compilation and callback settings : val_accuracy, val_loss, ReduceLROnPlateau, EarlyStopping

+ Performance Evaluation : Accuracy of the model is 94.3396%

![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/e4e3a6e7-ee84-4cd6-9ae7-f6d024064606)




![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/a3689437-8096-452b-afc1-0cc023a616f0)


+ Dataset : <https://www.kaggle.com/datasets/devzohaib/dog-emotions-prediction>
  + 15900 images with 4 categories of emotion


+ Base Model : VGG16
  + Using 3x3 filter

+ Model Training
  + Data Loading : Load image data from dataset_path
  + Pretrained Model Loading(VGG16) : By using tf.keras.applications.vgg16 function
  + Model Composition : Define VGG16 as Sequential model, Add Flatten() layer and Dense() layer
  + Model Training : The model is compiled with a 'sparse_categorical_crossentropy' loss function and the 'adam' optimizer.
  + Save results : training history of the model is stored in the ‘hist’ variable

+ Performance Evaluation
  + Training accuracy steadily increases, reaching approximately 75%.
  + Verification accuracy is not improving significantly at around 50%.
    
![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/bd361410-d0d6-4436-b863-afd9bfac1d22)










## 예제코드 
