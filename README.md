## 🔗 Google Colab Notebook

You can view and run the full implementation of this project using Google Colab:

[Open in Google Colab](https://colab.research.google.com/drive/1pT2CmhQJrVSiwf7p8RYL26XDkpVf5-OP?usp=sharing)

---

# 📘 Custom Image Classification Activity 3 - Reflection

# Activity 3: Custom Image Classification Using CNN

---

## 1. Dataset Preparation

### How did you organize your dataset in Google Drive?

I organized my dataset in Google Drive by creating one main dataset folder. Inside that folder, I created separate folders for each class. Each class folder contains the images that belong to that specific category.

The dataset was organized like this:

```text
image_classification/
│
├── Abronia maritima/
├── Batis maritima/
├── Cakile maritima/
├── Canavalia rosea/
├── Crinum asiaticum/
├── Crotalaria pumila/
├── Euphorbia mesembryanthemifolia/
├── Helianthus debilis/
├── Heliotropium curassavicum/
├── Ipomoea pes-caprae/
├── Limonium longifolium/
├── Sesuvium portulacastrum/
├── Solidago sempervirens/
├── Sophora tomentosa/
├── Spinifex littoreus/
├── Suriana maritima/
├── Vigna marina/
├── Wedelia trilobata/
├── Pandanus tectorius/
└── Scaevola taccada/
```

This structure helped TensorFlow automatically detect the class names based on the folder names.

---

### Why is folder structure important for TensorFlow image loading?

Folder structure is important because TensorFlow uses the folder names as class labels when loading images using `image_dataset_from_directory()`.

If the dataset is properly organized, TensorFlow can automatically understand which image belongs to each class. This makes the loading process easier because there is no need to manually label every image.

A correct folder structure also helps avoid mistakes during training. If an image is placed in the wrong folder, the model may learn the wrong label, which can affect the accuracy of the model.

---

## 2. Model Training

### What is the role of convolutional layers in image classification?

Convolutional layers are responsible for extracting important features from images. These features include edges, shapes, colors, textures, and patterns.

In image classification, convolutional layers help the model understand the visual differences between classes. In this activity, the CNN model used convolutional layers to learn the features of the 20 plant classes.

After the convolutional layers extract the features, the model uses the dense layers to classify the image into the correct category.

---

### Why do we split data into training and validation sets?

We split the data into training and validation sets to check if the model can perform well on images it has not seen before.

The training set is used to teach the model and allow it to learn image patterns. The validation set is used to evaluate the model’s performance during training.

In this activity, the dataset was divided into training and validation sets. This helped determine whether the model was only memorizing the training images or actually learning useful patterns that can work on new images.

---

## 3. Performance Analysis

### What accuracy did your model achieve?

The model achieved around **50.92% validation accuracy**.

This means that the model was able to correctly classify about half of the validation images. Since the dataset contains **20 classes**, the result shows that the model was able to learn some useful image features, but it still needs improvement to achieve better performance.

The result is acceptable for a basic CNN model, but the accuracy can still be improved by using techniques such as data augmentation, dropout, and more training adjustments.

---

### How did the number of images affect the model’s performance?

The number of images affected the model’s performance because CNN models need enough image examples to learn the patterns of each class.

In this activity, the dataset contained **5,175 images** across **20 classes**. This helped the model learn basic features from each class. However, since there are many classes, the model needs enough images for every class to classify them correctly.

If some classes have fewer images, the model may have difficulty learning those classes. More balanced and larger datasets can help improve the model’s accuracy and make the predictions more reliable.

---

## 4. Critical Thinking

### What challenges did you encounter while using your own dataset?

One challenge I encountered was organizing the dataset properly. Each image had to be placed in the correct class folder because TensorFlow uses the folder names as labels.

Another challenge was handling a dataset with many classes. Since the dataset has **20 plant classes**, some plants may have similar visual features, which makes classification more difficult for the model.

I also needed to make sure that the dataset had enough images per class. If some classes have fewer images than others, the model may learn some classes better and may perform poorly on the classes with fewer samples.

---

### How can data augmentation improve your model?

Data augmentation can improve the model by creating different versions of the training images. It can apply changes such as flipping, rotating, zooming, and shifting the images.

This helps the model learn more general features instead of memorizing the exact training images. Because of this, the model can perform better when it sees new or unseen images.

Data augmentation is useful because it increases the variety of the dataset without needing to collect more images manually. It can also help reduce overfitting and improve validation accuracy.

---

## 5. Application

### Suggest a real-world application for your trained model.

A real-world application for this trained model is a plant image classification system.

Users can upload or capture an image of a plant, and the system will predict which plant class it belongs to. This can be useful for students, researchers, teachers, and people who want to identify plant species using images.

This kind of system can also be used as an educational tool for learning about different plant species.

---

### How can this system be integrated into a mobile or web application?

This system can be integrated into a mobile or web application by saving the trained model and connecting it to an application interface.

For a web application, the user can upload an image through a webpage. The backend system will process the image, resize it to the required image size, load the trained model, and return the predicted class.

For a mobile application, the user can take a photo using the phone camera or upload an image from the gallery. The image will then be sent to the model for prediction, and the app will display the predicted plant name.

A possible system flow is:

```text
User uploads or captures an image
        ↓
System preprocesses the image
        ↓
Image is resized to 180x180
        ↓
Trained CNN model predicts the class
        ↓
Application displays the predicted plant name
```

---

## Final Reflection

In this activity, I learned how to prepare a custom image dataset, organize it properly in Google Drive, and load it in Google Colab using TensorFlow. I also learned how a CNN model works in image classification by using convolutional layers to extract important features from images.

The model achieved around **50.92% validation accuracy**, which shows that it was able to learn from the dataset. However, the result also shows that the model still needs improvement because the dataset has many classes and some classes may have similar visual features.

Overall, this activity helped me understand the importance of proper dataset preparation, correct folder structure, training and validation splitting, CNN model training, and how an image classification model can be applied in a real-world mobile or web application.

---

# 📘 Custom Image Classification Activity 3A - Reflection

# Laboratory Work 3: CNN Model Improvement and Reflection

## Overview

This laboratory activity focused on building and improving a Convolutional Neural Network (CNN) model for image classification. The main goal was to identify signs of overfitting in the first model and apply improvement techniques such as data augmentation and dropout to improve the model's validation performance.

The dataset used in this activity contains **5,175 images** divided into **20 classes**. The training set contains **4,140 images**, while the validation set contains **1,035 images**.

---

## Dataset Summary

| Dataset Split | Number of Images | Number of Batches |
|---|---:|---:|
| Training Set | 4,140 | 130 |
| Validation Set | 1,035 | 33 |
| Total Dataset | 5,175 | - |

---

## Model Performance Summary

| Model | Techniques Used | Best Validation Accuracy | Validation Loss |
|---|---|---:|---:|
| Baseline Model | Basic CNN | 50.92% | 3.3548 |
| Improved Model | Data Augmentation + Dropout | 59.13% | 1.5122 |

The improved model increased the validation accuracy by approximately **8.21 percentage points** compared to the baseline model.

---

## Baseline Model Analysis

The first model used a basic CNN architecture with convolutional layers, pooling layers, and dense layers. Based on the training results, the baseline model showed signs of overfitting.

The training accuracy reached almost **99%**, but the validation accuracy only stayed around **50% to 51%**. This means that the model performed very well on the training data but struggled when tested on unseen validation images.

Another sign of overfitting was the high validation loss. Even though the training loss became very low, the validation loss increased. This indicates that the model memorized the training images instead of learning general features that could help classify new images correctly.

---

## Improved Model Analysis

To improve the model, data augmentation and dropout were added. Data augmentation helped create more variety in the training images by applying random transformations such as flipping, rotation, and zooming. Dropout was also added to reduce overfitting by randomly disabling some neurons during training.

After applying these improvements, the validation accuracy improved from **50.92%** to **59.13%**. The validation loss also decreased, which means the improved model generalized better than the baseline model.

Although the improved model had lower training accuracy compared to the baseline model, this is actually a better result because the gap between training accuracy and validation accuracy became smaller.

---

# Guide Questions and Answers

## Visualization and Overfitting

### 1. What signs indicated overfitting in your first model?

In my first model, the signs of overfitting were seen in the large gap between training accuracy and validation accuracy. The training accuracy increased very high, reaching around **99%**, while the validation accuracy only stayed around **50% to 51%**.

This means that the model learned the training images too well but did not perform well on unseen validation images. Another sign of overfitting was the validation loss. Even though the training loss became very low, the validation loss increased up to around **3.41**, which shows that the model made many confident but incorrect predictions on the validation data.

---

### 2. How did data augmentation affect validation accuracy?

Data augmentation helped improve the validation accuracy. In the baseline model, the best validation accuracy was around **50.92%**. After applying data augmentation together with dropout, the improved model reached around **59.13%** validation accuracy.

This improvement happened because data augmentation created slightly different versions of the training images using random flip, rotation, and zoom. Because of this, the model learned more general features instead of memorizing the exact training images.

---

## Model Improvement

### 3. What is the purpose of dropout layers?

The purpose of dropout layers is to reduce overfitting. During training, dropout randomly turns off some neurons so that the model does not depend too much on specific features or patterns.

In my improved model, I used **Dropout 0.3**, which helped control the training accuracy and reduced the gap between training and validation performance. This made the model less dependent on memorizing the training data.

---

### 4. Why does data augmentation improve generalization?

Data augmentation improves generalization because it increases the variety of training images without adding new image files. By applying random transformations such as flipping, rotation, and zooming, the model sees different versions of the same image.

This helps the model become less sensitive to small changes in image position, angle, or size. As a result, it can perform better on new or unseen images, not only on the exact images used during training.

---

## Performance Comparison

### 5. Compare accuracy before and after improvements.

Before the improvement, the baseline model achieved a best validation accuracy of **50.92%**. After adding data augmentation and dropout, the improved model achieved a best validation accuracy of **59.13%**.

This means that the improved model increased validation accuracy by about **8.21 percentage points**. The baseline model had very high training accuracy but poor validation performance, while the improved model had a more balanced training and validation performance.

---

### 6. Which technique contributed most to improvement?

Based on the notebook, the improvement came from the combination of **data augmentation and dropout**. However, since both techniques were added in the improved model at the same time, it is not possible to prove exactly which one contributed more without doing a separate experiment.

In my observation, data augmentation likely contributed the most because it directly increased the variety of training images. Dropout also helped by reducing memorization and controlling overfitting. Together, both techniques helped the model generalize better.

---

## Deployment and Application

### 7. Why is saving the model important?

Saving the model is important because it allows the trained model to be reused without training it again from the beginning. Training a CNN model takes time, so saving the best model helps preserve the best validation performance.

In my notebook, the improved model was saved as:

```text
/content/drive/MyDrive/LW3_improved_best.keras
