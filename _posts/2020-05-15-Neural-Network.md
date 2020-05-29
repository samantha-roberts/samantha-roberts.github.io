---
title: "Neural Networks"
layout: splash
date: 2020-05-15
tags:
  - Neural Network
  - Convolutional
  - Image Classification
  - CNN
  - Deep Learning
<-- header:
  overlay_image: /images/deep_learning.jpg -->
---
<h2><center><strong>Image Classifiation Through Convolutional Neural Network</strong></center></h2>
<p>
 <center><img src="/images/cnn.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center><br>
  
<h3><center>I. Description of the problem and the data:</center></h3>
<p>
  For the neural network project, I chose a classification problem. The neural network will be classifying if an image is one of a cat or a dog. The data is broken down into training and test images. For the training data, there are a total of 8005 images belonging to two classes, either cat or dog. There is an even balance between the two classes, with approximately half the images being of dogs and the other half being of cats. The test data consists of 2023 images which also belong to either the category of cat or dog. The test data is also approximately equal between the dog and cat classes with about half the images being in one class and half being in the other class. This brings the total number of images being classified to 10,028. The images are pictures of various breeds of cats and dogs, along with them being photographed from different angels and with the animals being positioned differently. Below shows an example of a cat and a dog image from the training data. 
</p>

<h3><center>II. Convolutional Neural Network Framework:</center></h3>
<p>
  In order to classify the images, a convolutional neural network (CNN) was used. A convolutional neural network performs well for computer vision problems, like the classification of whether an image is a cat or a dog. Convolutional neural networks have multiple convolution layers, pooling layers and dense layers. Convolution layers are those that transform the image to make it possible to extract various parts of an image, such as identifying ears, tails or legs of the cats or dogs. An activation function is then applied to the output from the convolutional layers. After the activation function is applied, the pooling layer is implemented. The job of the pooling is to reduce the size of the image being passed through it. By reducing the image size, the important aspects of the image are kept and the unimportant aspects are removed. Unimportant aspects might be something like grass or a leash. Including a pooling layer also reduces the computational cost of the neural network. The size of the pooling matrix in the pooling layer is what determines how much the image is reduced. For example, if the matrix is a 2x2 matrix, the image is reduced in size by 50%. 
</p>
<p>
  The initial convolutional neural network that the images were passed through had three convolutional layers, 3 max-pooling layers, followed by a flatten layer and then two dense layers. The first convolution layer has 16 kernels of size 3x3. The image is then passed through the activation function, which is the ReLu activation function. The images are of size 150x150 pixels with 3 channels for the colors red, green and blue. The max-pooling layer has a 2x2 kernel so the maximum value is taken while the image is reduced in size by 50%. There are three layers of the convolution and max-pooling steps to extract the features in the images to classify whether the image is of a dog or a cat. Next in the neural network is to pass the image through the flatten layer, which takes the output from the max-pooling layer and converts it to a one-dimensional array, in order for it to then be passed through the dense layers. The dense layer is a regular layer or neurons where the learning occurs in the neural network. In the initial convolutional neural network there are two dense layers. The problem of classifying whether an image is a cat or a dog is a binary classification problem, which means that there will be only one neuron in the output layer. In order to obtain better accuracy scores, the neurons in the other layer can be adjusted. 
</p>
<p>
  In order to train the model, the loss needs to be defined. Since the classification problem is binary, the loss will be calculated using the binary cross entropy function. The optimizer parameter adjusts the weights in the neural network so that the loss function is as small as possible. The optimizer used is the RMSprop algorithm, which maintains the moving average of the square of the gradients. To estimate how well the model is performing, the accuracy score will be used. The initial neural network model had a batch size of 64, which means that samples of 64 are processed before the model is updated. In order to cover all the training and testing images with batch sizes of 64, the steps per epoch is 126 for training and 32 for testing images. The initial value of epochs is 64, which means that the entire training data will be cycled through 64 times. After the 64 epochs for the initial convolutional neural network had been calculated, the accuracy for the training set was 49.9% and the accuracy for the testing data was 49.
</p>

<h3><center>III. Algorithm Learning Process</center></h3>
<p>
  To obtain the best model for classifying if an image is a dog or a cat, hyperparameters were adjusted to see which model(s) gave the best accuracy score, while ensuring that the models were not overfitting the data. The initial model’s accuracy score was 0.4990 for training data and 0.4986 with testing data, with 100 steps per epoch in the training data, 50 steps in the testing data and a total of 10 epochs with batch size of 64. The initial model had the ReLu activation function in the convolutional layers, and the first dense layer also has the activation function of ReLu, with the last layer (and second dense layer) has an activation function of sigmoid, which is used for binary output, such as classifying the image as either cat or dog. This means that the initial model was able to accurately classify an image just over 50% of the time. Since this is a low accuracy score, there was a tuning of the hyperparameters.
</p>
<center><img src="/images/table_nn.PNG" style="margin:0 20px 20px 0;" width="800" height="1200" align="middle"></center><br>
<p>
  The model that appears to be the best (based on accuracy score) for classifying whether an image is a cat or a dog was the fifth model. This model had batch size of 64 for the training and test data, with the steps per epoch being 125 and 32 for training and test data, respectively. ReLu was used as the activation function in the layers. The fifth model had 3 convolutional layers, 3 max pooling layers, 1 flatten layer and 2 dense layers. After all 10 epochs with batch sizes of 64 (both train and test data) were run through the model, the accuracy score for the training data is 98.7%, with the testing data having accuracy of 88.6%. Having 10 epochs means that the data was passed forward and backward through the model 10 times, and having a batch size of 64 means that there will be 64 samples that are passed through the model. Having ReLu as the activation function means that if the input is positive then that is directly what the output will be, and if the input is a non-positive value, then 0 will be the output. The optimizer for the final model that was used was Adam, which is a stochastic gradient descent method. 
</p>

<h3><center>IV. Potential Improvement</center></h3>
<p>
  A potential step for improving the image recognition capabilities of the neural network, image augmentation could be implemented. Image augmentation would create more images by resizing and rotating the existing images to create the new ones. Additionally, the hyperparameters could be tuned further. The optimizer could be kept as Adam, and things like the dense layers or number of neurons in each layer could be tuned as well. To test the model capabilities, more images of cats and dogs could be collected and then these images could be passed through the neural network without their labels, to see what the model categorizes them as to test its performance.
</p>
