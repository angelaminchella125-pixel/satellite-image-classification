Software and Computing for Nuclear and Subnuclear Physics <br>
Satellite Image Classification Project


The project is delivered in a directory consisting of:

* main.py --> python code implemented on Google Colab.
* requirement.txt --> file listing the main libraries used in the project.
* Dockerfile --> containerization as required by the project delivery specifications.
* readme.md.


To run the code follows these steps:
* enter the directory "project" from the command prompt;
* execute the command: docker build -t imagename .
* execute the command: docker run --rm imagename <br>
(imagename --> you can chose a name for the image of your choice)

Note that for the best visualization of plots and results, open the notebook directly on Google Colab or Jupyter Notebook.<br>




-Description-

The aim of this project is to build and train a Convolutional Neural Network (CNN) to classify satellite images into four distinct categories: 'cloudy', 'desert', 'green_area', and 'water'.

The "Satellite Image Classification" dataset from Kaggle (Satellite Remote Sensing Image -RSI-CB256) was used, consisting of 5631 images in JPG format. The dataset was pre-processed, splitting images into training and validation sets (code block 2), and pixel values normalized (https://www.kaggle.com/datasets/mahmoudreda55/satellite-image-classification/data).

The project (code.py), implemented in 9 blocks of code, follows the following squeme: 

* Downloading and setting up the dataset paths. 
* Loading and preprocessing image data. 
* Building and compiling a custom CNN architecture. 
* Training the model and evaluating its performance on validation and test sets.

The CNN model consists of:

* An input layer for 64x64x3 images.
* Two blocks of 'Conv2D' and 'MaxPooling2D' for feature extraction.
* A 'Flatten' layer followed by a 128-unit 'Dense' layer with ReLU activation.
* A 'Dropout' layer to prevent overfitting.
* A final 'Dense' layer with Softmax activation for 4-class classification.

The model was compiled with the 'adam' optimizer and 'categorical_crossentropy' loss function.




-Results-

The model was trained for 10 epochs demonstrating:

* consistent downward trend in both training and validation loss, indicating effective learning.
* progressive increase in both training and validation accuracy, confirming the model's ability to classify both seen and unseen images with high precision.

The confusion matrix (as presented in block 6) highlights strong performance for 'cloudy' and 'desert' classes. However, the model sometimes misclassifies 'green_area' and 'water' images due to visual similarities, providing valuable insight into the model's capability and limitation.

Further analysis of misclassified images (as presented in block 9) confirms that errors are primarily concentrated between 'green_area' and 'water' classes, reinforcing the observations from the confusion matrix. This suggests that future work could involve more sophisticated architectures or additional features to better differentiate these challenging categories.




-Conclusion-

Overall, the CNN model successfully classifies the dataset satellite images into 4 distinct categories.

Future model improvements could explore more complex architectures, different datasets, or incorporate additional features to reduce ambiguity in image classification.

