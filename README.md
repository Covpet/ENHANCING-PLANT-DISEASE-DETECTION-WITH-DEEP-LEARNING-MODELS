# ENHANCING-PLANT-DISEASE-DETECTION-WITH-DEEP-LEARNING-MODELS
## PROJECT TOPIC
ENHANCING PLANT DISEASE DETECTION WITH DEEP LEARNING MODELS: A CASE STUDY ON MAIZE AND CASSAVA SPECIES. 

## PROJECT DESCRIPTION
This project aims to develop a high-performance deep learning model for detecting diseases in maize and cassava crops. Leveraging an extensive image dataset and state-of-the-art architectures, the study seeks to improve the accuracy and efficiency of plant disease detection, ultimately benefiting agricultural productivity and sustainability.

### Dataset

Source: Mendeley Data (https://data.mendeley.com/datasets/bwh3zbpkpv/1)

Total Images:

Raw: 24,881

Augmented: 102,976

Crops Included: Cashew, Cassava, Maize, Tomato (CCMT)

Focus Crops: Cassava and Maize

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

### Models Used

 ## CNN (Custom)
 
3-layer CNN trained from scratch

Evaluated over 10, 20, and 30 epochs

## VGG16 (Transfer Learning)

Pretrained on ImageNet

Custom classifier added

Fine-tuned using early stopping

## MobileNetV2 (Transfer Learning)

Lightweight model for fast inference

Transfer learning with added dense layers

## Hybrid Model

Custom ensemble combining:

ResNet50

EfficientNetB3

MobileNetV2

Outputs merged via feature concatenation and processed through dense layers

### Final Model Performance (30 Epochs)

Model | Test Accuracy

CNN | 81%

VGG16 | 75%

MobileNetV2 | 80%

Hybrid | 88% ✅ Best

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
