# 📌 Project Background  
Driver drowsiness detection is a type of technology used in vehicles that helps detect driver drowsiness. These systems help prevent fatigue-related accidents. Various technologies, such as steering pattern monitoring, vehicle position in lane monitoring, and driver face monitoring, are being used. This project aims to find the best deep learning model to detect drowsiness given an image [dataset](https://www.kaggle.com/datasets/serenaraju/yawn-eye-dataset-new).

<i>In collaboration with Anurag Ramesh Patil, Bijay Gautam, Justin Gamoras, Shri Hari Sekar, and Suyog Sanklapur.</i>

# 🧐 Data Overview  
This dataset contains 2900 images, each in one of the following categories:  
- eye opened
- eye closed
- person yawning
- person not yawning  

The outcome variable is binary (1 for drowsy and 0 for non-drowsy). Images in the "eye opened" or "person not yawning" groups are considered non-drowsy, whereas images in the "eye closed" or "person yawning" groups are considered drowsy. 75% of the images in this dataset have an outcome of 1, or drowsy.  

# 🖥️ Data Processing  
To pre-process the data, we did data partitioning, image processing, and normalization. 
- Data partitioning to split the images into three datasets, 60% in training, 20% in cross-validation, and the remaining 20% in testing. This resulted in 1740 images in the training set and 580 images in each of the cross-validation and testing sets.  
  <br>
    <img src="Images/img-02.png" width="800">
  <br>   
- Image processing to resize each of the images to 64 pixels x 64 pixels and to add the 0 and 1 labels to the images.  
  <br>
    <img src="Images/img-01.png" width="800">
  <br>  
- Normalizing the images by scaling the features to be between 0 and 1, making the data more interpretable.  
  <br>
    <img src="Images/img-03.png" width="800">
  <br>  

# 📈 Evaluation of Models  
The evaluation metric that we used was accuracy. Not only is accuracy easy to explain, but overall model correctness is important. Misclassifying a drowsy driver as non-drowsy can be dangerous, and misclassifying alert drivers as drowsy could lead to unnecessary alerts or make the system less robust. In general, humans can identify whether someone is yawning or an image of an eye is open or closed, so the human error is close to 0% meaning that our goal should be to try to aim for high accuracy. Our benchmark model, logistic regression, returned a training accuracy of 90.7%.  

We then tried building two simple neural networks, one with 1 hidden layer (4 nodes) and another one with 2 hidden layers (7 nodes in hidden layer 1 and 4 nodes in hidden layer 2). The neural network with 1 hidden layer returned the best results with a training accuracy of 99%, a cross-validation accuracy of 98.5%, and a testing accuracy of 97%.  

Though the performance of the neural network with 1 hidden layer was extremely positive, we used the Tensorflow package to try to run the dataset through different models to see if they would provide better results. Some algorithms we tried included:  
- Adam (Adaptive Moment Estimation)
- Mini-Batch Gradient Descent
- Mini-Bath Gradient Descent with Momentum
- RMSprop (Root Mean Squared Prop)
- L2 Regularization
- Dropout
- Batch Normalization
- Early Stopping  
