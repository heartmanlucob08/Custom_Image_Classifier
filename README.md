## 🔗 Google Colab Notebook

You can view and run the full implementation of this project using Google Colab:

👉 [Open in Google Colab]((https://colab.research.google.com/drive/1pT2CmhQJrVSiwf7p8RYL26XDkpVf5-OP?usp=sharing))

---

# 📘 Image Classification Activity 3 - Reflection

## 1. Dataset Preparation

**How did you organize your dataset in Google Drive?**  
I organized my dataset by creating one main folder, then inside it I made separate folders for each class. Since I have 20 classes, each class has its own folder, and I placed the images inside their correct folders. This made it easier for TensorFlow to read the dataset.

**Why is folder structure important for TensorFlow image loading?**  
Folder structure is important because TensorFlow uses the folder names as labels. If the folders are not organized properly, the model will not be able to identify the classes correctly or may cause errors.

---

## 2. Model Training

**What is the role of convolutional layers in image classification?**  
Convolutional layers help the model detect features in an image like edges, shapes, and patterns. These features help the model understand what the image contains.

**Why do we split data into training and validation sets?**  
We split the data so the model can learn using the training set and then be tested using the validation set. In my case, I used 4140 images for training and 1035 images for validation. This helps check if the model is learning correctly.

---

## 3. Performance Analysis

**What accuracy did your model achieve?**  
The dataset was loaded successfully with 5175 images and 20 classes, and it was properly split into training and validation. After training the model, it achieved a validation accuracy of 0.5401 (54.01%), which shows that the model is still in the early stage of learning and has room for improvement in terms of generalization and performance.

**How did the number of images affect the model’s performance?**  
Having 5175 images helped the model learn better because it has more data to study. More images give better results compared to having a small dataset.

---

## 4. Critical Thinking

**What challenges did you encounter while using your own dataset?**  
It was a bit challenging to gather enough images for each class. Some categories had fewer images compared to others, which made the dataset slightly unbalanced. I also had to make sure the images were relevant to each class so the model could learn properly. I encountered issues like duplicate images and some low-quality or unclear images. These duplicates can affect the model because it may memorize the same images instead of learning patterns. I also had to check if all images were placed in the correct folders. Labeling was done through folder names, so it was important to place images in the correct class. The challenge here was making sure there were no misclassified images, since even one wrong placement could affect the model’s learning. I experienced slower processing during training because of the large number of images (5175 total). It required more time and computing resources, especially when running in Google Colab. These challenges affected the model by increasing training time and possibly reducing accuracy if duplicates or incorrect labels were present. An unbalanced dataset could also cause the model to favor certain classes over others.

**How can data augmentation improve your model?**  
Data augmentation helps by creating more variations of images like flipping or rotating them. This makes the model more accurate and prevents overfitting.

---

## 5. Application

**Suggest a real-world application for your trained model.**  
A real-world application of this model is in environmental monitoring and coastal management. It can be used to automatically identify beach plant species, which helps in tracking biodiversity, detecting invasive species, and supporting conservation efforts in coastal areas.

**How can this system be integrated into a mobile or web application?**  
The system can be integrated by converting the trained model into a deployable format such as TensorFlow Lite or TensorFlow.js. In a mobile app, users can use the camera to capture plant images and get real-time predictions. In a web application, users can upload images, and the model processes them on the backend or directly in the browser to classify the plant species.

---

# 📘 Image Classification Activity 3A - Reflection

**Visualization & Overfitting**

**1. What signs indicated overfitting in your first model?**
In my first model (without data augmentation), there were clear signs of overfitting. The training accuracy increased very high, reaching about 99%, while the validation accuracy stayed much lower at around 54%. This large gap shows that the model was learning the training data too well but could not perform well on new data. Also, the training loss kept decreasing until it was almost 0, but the validation loss started to increase after a few epochs. This means the model was getting better on training data but worse on validation data. These patterns clearly show that the model was memorizing the training images instead of learning general features of the coastal beach plants.

**2. How did data augmentation affect validation accuracy?**
After applying data augmentation, the validation accuracy improved from around 54% to about 60–61%. It also became more stable instead of dropping or fluctuating a lot. At the same time, the training accuracy was lower (around 64%), but the gap between training and validation accuracy became much smaller. This indicates that the model is no longer overfitting as much and is learning features that can be applied to new images. Overall, data augmentation helped improve the model’s ability to generalize.

---

**Model Improvement**

**3. What is the purpose of dropout layers?**
The purpose of dropout layers is to reduce overfitting. During training, dropout randomly turns off some neurons in the network. This prevents the model from depending too much on specific features or patterns in the training data. Because of this, the model is forced to learn more general and useful features, which improves its performance on unseen data.

**4. Why does data augmentation improve generalization?**
Data augmentation improves generalization by increasing the diversity of the dataset. It creates modified versions of the original images, such as flipping, rotating, zooming, or changing brightness. For my coastal beach plant dataset, this means the model can see plants in different positions, angles, and lighting conditions. As a result, the model learns more general patterns instead of memorizing exact images, which helps it perform better on new data.

---

**Performance Comparison**

**5. Compare accuracy before and after improvements.**
Before using data augmentation, the model had very high training accuracy (~99%) but low validation accuracy (~54%), which shows overfitting. After applying data augmentation, the training accuracy decreased to about ~64%, but the validation accuracy improved to around 60–61%. Even though the training accuracy became lower, the validation accuracy increased, which is more important because it shows better performance on unseen data. This comparison shows that the improved model is more balanced and generalizes better.

**6. Which technique contributed most to improvement?**
The technique that contributed the most to improvement was data augmentation. It significantly reduced overfitting by lowering the gap between training and validation accuracy. It also increased validation accuracy and made the model more stable during training. Compared to the first model, data augmentation had the biggest impact in helping the model learn general features of coastal beach plants instead of memorizing the training data.

---

**Deployment & Application**

**7. Why is saving the model important?**
Saving the model is important because it allows us to reuse the trained model without training it again. Training a model takes a lot of time and computing power, so saving it helps us avoid repeating that process. It also allows the model to be used later for prediction, shared with others, or deployed into real-world applications. For example, once the model for coastal beach plants is saved, it can be loaded anytime to classify new plant images without retraining.

**8. How can this model be deployed in a real-world system?**
This model can be deployed in a real-world system by integrating it into an application that allows users to upload images and receive predictions. For example, it can be used in a mobile or web app where a user takes a photo of a coastal beach plant and the model automatically identifies the plant type. It can also be used in research or environmental monitoring systems to help classify and track coastal vegetation. To deploy the model, it is first saved (such as in a .h5 or .keras file), then loaded into a program using TensorFlow or Keras. After that, it is connected to a user interface or an API so that users can input images and get predictions easily.
