# ENHANCING-PLANT-DISEASE-DETECTION-WITH-DEEP-LEARNING-MODELS
## PROJECT TOPIC
ENHANCING PLANT DISEASE DETECTION WITH DEEP LEARNING MODELS: A CASE STUDY ON MAIZE AND CASSAVA SPECIES. 

## PROJECT DESCRIPTION
This project aims to develop a high-performance deep learning model for detecting diseases in maize and cassava crops. Leveraging an extensive image dataset and state-of-the-art architectures, the study seeks to improve the accuracy and efficiency of plant disease detection, ultimately benefiting agricultural productivity and sustainability.

### Dataset

Source: Mendeley Data (https://data.mendeley.com/datasets/bwh3zbpkpv/1)

Total Images:

Raw: 24,881

Crops Included: Cashew, Cassava, Maize, Tomato (CCMT)

Focus Crops: Cassava (7508) and Maize  (5389)

### Cassava - 5 Classes:

- Bacterial Blight
- ![image](https://github.com/user-attachments/assets/5ef3b97d-236f-4a98-a28a-4812c4925bb6)


- Mosaic
- ![image](https://github.com/user-attachments/assets/74501546-a9ec-45e6-a788-4ac42ce8642f)


- Brown Spot
- ![image](https://github.com/user-attachments/assets/2761ae0a-6d3f-402f-8154-d592b1d0cebd)


- Green Mite
- ![image](https://github.com/user-attachments/assets/3f38c0ee-a076-4826-baca-e37964c31100)


- Healthy (renamed with a capital 'H' to distinguish from maize)
- ![image](https://github.com/user-attachments/assets/d12776af-ccda-4464-9562-87ba8ff7cdf9)


### Maize - 7 Classes:

- Fall Armyworm
- ![image](https://github.com/user-attachments/assets/e0e7d260-73f0-44fe-918b-10e3f509d019)


- Grasshopper
- ![image](https://github.com/user-attachments/assets/1d5a8d80-db2e-427b-bd33-cba7505c0764)


- Healthy
- ![image](https://github.com/user-attachments/assets/c3ba76ba-3265-45c2-8ea9-f1bdd69a330c)


- Leaf Beetle
- ![image](https://github.com/user-attachments/assets/2dce8960-ddd0-4e44-bbad-cbd67ec873c7)

  

- Leaf Blight
- ![image](https://github.com/user-attachments/assets/96ed7cde-0d37-486a-9e76-e15e9cadbb3e)


- Leaf Spot
- ![image](https://github.com/user-attachments/assets/f9e12942-80f8-4567-b8a3-ecebbbc326a0)


- Streak Virus
![image](https://github.com/user-attachments/assets/54aacf74-ff52-4750-8d46-db99cc3bf16c)

##   Cleaning Technique

- class weighing: ability of the system to recognize the particular class of images 

- Data augmentation: making sure all images are in same sizes before applying any model

### Models Used

 ## CNN (Custom)
 
3-layer CNN trained from scratch

Evaluated over 10, 20, and 30 epochs

## Compilation:

Optimizer: Adam

Loss Function: Categorical Crossentropy

Metrics: Accuracy, classification report and confusion matrix

## Training Setup:

Epochs Tested: 10, 20, 30

Callback: ModelCheckpoint to save the best model based on validation loss

Batch Size: 32

Input Image Size: 150x150 pixels

Data Augmentation: Included (rescale, rotation, zoom, shift, flip)

## VGG16 (Transfer Learning)

Pretrained on ImageNet

Custom classifier added

Fine-tuned using early stopping

## Architecture Overview:

Base Model: VGG16 (without top layers, include_top=False)

Input Shape: (150, 150, 3)

Freezing: All VGG16 layers frozen during training

## Custom Top Layers:

GlobalAveragePooling2D

Dense(512, ReLU)

Dropout(0.5)

Dense(final classification layer with softmax)

## Compilation:

Optimizer: Adam

Loss Function: Categorical Crossentropy

Metrics: Accuracy, classification report, confusion matrix

## Training Strategy:

Epochs Tested: 10, 20, 30

Callbacks:

ModelCheckpoint: Saves best model (based on validation loss)

EarlyStopping: Stops training early to prevent overfitting

Patience: 5 epochs for early stopping

## MobileNetV2 (Transfer Learning)

Lightweight model for fast inference

Transfer learning with added dense layers

## Architecture Overview:

Base Model: MobileNetV2 (pretrained on ImageNet)

Input Shape: (150, 150, 3)

Frozen Layers: All base layers are frozen to preserve pretrained features

## Custom Top Layers:

GlobalAveragePooling2D

Dense(128, ReLU)

Dropout(0.5)

Dense(output, softmax)

## Compilation:

Optimizer: Adam

Loss Function: Categorical Crossentropy

Metrics: Accuracy, classification report and confusion matrix

## Training Strategy:

Epochs Evaluated: 10, 20, 30

Callback: ModelCheckpoint to retain the best model based on validation loss

## Hybrid Model

Custom ensemble combining:

ResNet50

EfficientNetB3

MobileNetV2

Outputs merged via feature concatenation and processed through dense layers

## Components Combined:

ResNet50 – Deep residual network known for handling vanishing gradients

EfficientNetB3 – Scalable model that balances performance and efficiency

MobileNetV2 – Lightweight architecture optimized for speed and mobility

## Architecture Overview:

hared input tensor: (150, 150, 3)

Each backbone extracts deep features via GlobalAveragePooling2D

Outputs are concatenated and passed through:

BatchNormalization (stabilizes learning)

Dense(512, ReLU) → Dropout(0.5)

Dense(256, ReLU) → Dropout(0.3)

Final Dense(num_classes, softmax) for classification

## Compilation:

Optimizer: AdamW (adaptive decay)

Loss Function: Categorical Crossentropy

Metrics: Accuracy

 Training Setup:
 
Epochs Evaluated: 10, 20, 30

## Callbacks:

EarlyStopping: Monitors validation loss with patience of 7

ReduceLROnPlateau: Dynamically reduces learning rate if plateauing

### Final Model Performance (30 Epochs)

Model | Test Accuracy

CNN | 81%

VGG16 | 75%

MobileNetV2 | 80%

Hybrid | 88% ✅ Best

## Highlights:

Outperformed individual CNNs and pretrained models

Achieved a well-balanced tradeoff between depth, speed, and precision

Excellent generalization due to diverse backbone features

### Features

- Data Preprocessing: Cleaned corrupted images, normalized input

- Augmentation: Random flips, rotations, zoom, and shifts

- Visualization: Confusion matrices, performance curves, class distributions

- Evaluation: Accuracy, Precision, Recall, F1-score across models & epochs

### How to Use

- Clone this repository

- Upload dataset to Google Drive (path: /MyDrive/Raw Data/CCMT Dataset)

- Run the notebook in Google Colab

- View model performance and modify architecture or hyperparameters as needed

### Notes

“Healthy” class for cassava renamed to "Healthy" to avoid overlap with maize's "healthy"

Dataset split: 80% training, 10% validation, 10% testing

Early stopping and checkpoint callbacks implemented for optimal model selection

## Testing & User Interaction

This project goes beyond training and evaluation by allowing users to interact directly with the model and test predictions in two ways:

1.  Interactive Console Prediction
   
Users can test the model by entering a label name (e.g., mosaic, healthy, fall armyworm), and the system randomly selects an image from the dataset under that label. The model predicts the class, displays the image, and calculates accuracy in real time.

## Features:

- Random sample-based testing

- Immediate feedback with prediction confidence

- Tracks accuracy across user inputs

- Stops automatically if accuracy falls below 80%

2.  Image Prediction from URL
   
- Users can paste an image URL (e.g., from Google Images), and the model will:

- Download the image

- Resize and preprocess it

- Predict the plant disease class

- Display the image with prediction and confidence score

## Inputs:

- URL to an image

- Optional: actual label (for manual comparison)

## Outputs:

- Predicted class

- Confidence score (%)

- Image display with annotation

These tools make the model hands-on, making it easier for farmers, researchers, or students to test the classifier directly on their own inputs.

