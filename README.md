<div align="center">🐕</div>
<h1 align="center"> Animogram </h1>

<h4 align="center">A SNS that shares photos that recognize the emotions of your pets.</h4>
<p align="center">가천대학교 소프트웨어학과 졸업작품</p>
<p align="center">지도 교수 : 오영민 교수님, 이주형 교수님</p>
<div align="center"><img src="https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white"><img src="https://img.shields.io/badge/dart-%230175C2.svg?style=for-the-badge&logo=dart&logoColor=white"><img src="https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white"><img src = "https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white"><img src="https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white"><img src="https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white"></div>


## About The Project

If you live with a lovely dog, what you want to know the most is the dog's feelings and thoughts. Simply because dogs cannot speak!


So we thought:
+ Predict breeds & emotions by analyzing your dog's face.
+ Improve dog culture by sharing your dog's emotions.
+ Record your dog's emotions that change depending on the location and understand your dog through statistics.


Animogram, a compound word of animal, emotion, and Instagram, is the perfect project that satisfies all the needs above.


## Features

![animogram_function](https://github.com/senior-project-AnimoGram/README/blob/main/animogram_1.jpg)
+ Provide the breed of your dogs.

![animogram_function2](https://github.com/senior-project-AnimoGram/README/blob/main/animogram_2.jpg)
+ Provide filters that fit the emotions

+ Provide statistics on emotional changes according to location

## Getting Started

### Prerequisites
Before you begin, ensure you have met the following requirements:

+ **Flutter SDK**:

  Ensure you have Flutter installed on your machine. You can download it from the Flutter official website.
+ **Dart SDK**:

  Dart SDK is included with Flutter. Ensure you are using a version compatible with the Flutter SDK specified in this project (>=2.19.2 <3.0.0).
+ **Android Studio / Xcode**:

  To build and run the app on an emulator or a physical device, you will need Android Studio for Android development and Xcode for iOS development.
+ **Git**:

  Ensure Git is installed on your machine to clone the repository.
+ **Environment Setup**:

  Follow the official Flutter setup guide to ensure your environment is correctly set up for Flutter development.

### Installation
To get the project up and running locally, follow these steps:

1. **Clone the Repository**:


    Open your terminal and run the following command to clone the repository:
    ```
   git clone https://github.com/senior-project-AnimoGram/Frontend.git
   cd Frontend
2. **Install Dependencies:**

   
   Navigate to the project directory and run the following command to install the necessary dependencies:
   ```
   flutter pub get
3. **Run the App:**

   You can now run the app on an emulator or a physical device. Ensure you have an emulator running or a physical device connected, then execute:
   ```
   flutter run
### Additional Setup
1. **Configure Assets:**


    Ensure the following asset directories exist in your project structure:

    + **'asset/img/'**
    + **'asset/mypost/'**
    + **'asset/model/'**
    + **'asset/filter/'**
      
    These directories should contain the relevant assets required by the app.

2. **TFLite Model:**

   Place your TensorFlow Lite model in the **'asset/model/'** directory. Ensure the model file name matches the one specified in your code (**'emotion_model.tflite'**).

3. **Permissions:**

   Make sure to configure the necessary permissions in your Android and iOS configuration files for accessing the camera, gallery, and location services.

### Troubleshooting
If you encounter any issues during the setup or run process, consider the following steps:

+ Ensure all prerequisites are installed and configured correctly.
+ Verify that all dependencies are correctly installed by running **'flutter pub get'**.
+ Ensure your Flutter environment is correctly set up by running **'flutter doctor'** and resolving any issues reported.
  
For additional help and support, refer to the official Flutter documentation or raise an issue in the repository.
## Library
+ Dog face recognition : <https://github.com/tureckova/Doggie-smile>
+ *dlib* for loading dog face recognition model
+ *cv2* for image processing

## AI Model
![image](https://github.com/senior-project-AnimoGram/README/assets/98259281/fae28300-3662-4d87-86f2-354d8afc1e3d)

+ Dataset : <https://www.kaggle.com/datasets/mohamedchahed/dog-breeds>
  + 541 images with 8 categories of breeds
 
  
+ Base Model : InceptionV3
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


## Contributors
👨‍💻조윤상 

🙋‍♂️구건호
  qwer159874@gachon.ac.kr

💁‍♀️이라연 
  layeon0218@gmail.com

💁김재희
