**Software and Computing for Nuclear and Subnuclear Physics** - **Satellite Image Classification Project** 
<br><br>

The project is delivered in a directory consisting of:
* main.py --> python code implemented on Google Colab.
* requirements.txt --> file listing the main libraries used in the python project.
* Dockerfile --> containerization as required by the project delivery specifications.
* readme.md.
* images --> a subdirectory containing an example of the confusion matrix, the model accuracy (training vs validation) and model loss (training vs validation) generated in a code execution.

<br><br>

To run the code, follow these steps:
* Open Docker.
* Open the command prompt and run the command: git clone https://github.com/angelaminchella125-pixel/satellite-image-classification
* Enter the directory "satellite-image-reconstruction"
* Run the command: docker build -t imagename .
* Run the command: docker run --rm imagename <br>
(Note: imagename --> a placeholder for a custom name you choose for the Docker image, any name can be chosen)

Note that the code was originally written on Google Colab. When running the code inside the Docker container, plots and some results will not pop up visually, so for the best visualization, open the code directly on Google Colab or Jupyter Notebook. Nevertheless, in the subdirectory "images" some of the plots are shown.
<br><br>

-Motivation and physical relevance-

Remote sensing data provides massive, continuous Earth observation information that is critical for environmental monitoring and geophysical analysis. 

In the context of NSN physics, analyzing satellite imagery shares some ideological computational methodologies with detector data analysis, where pattern recognition and spatial reconstruction are essential. Furthermore, because traditional algorithms struggle with the complexity and volume of spatial imaging, Machine Learning and, more in particular Convolutional Neural Networks, offer the scalability and precision required to automatically extract meaningful physical insights.
<br><br>


-Description-

The aim of this project is to build and train a Convolutional Neural Network (CNN) to classify satellite images into four distinct categories: "cloudy", "desert", "green_area", and "water".

The "Satellite Image Classification" dataset from Kaggle (Satellite Remote Sensing Image -RSI-CB256) was used, consisting of 5631 images in JPG format. The dataset was pre-processed, splitting images into training and validation sets ( as shown in code block 2), and pixel values normalized (https://www.kaggle.com/datasets/mahmoudreda55/satellite-image-classification/data).

The project (main.py), implemented in 9 blocks of code, follows the following scheme: 

* Downloading and setting up the dataset paths. 
* Loading and preprocessing image data. 
* Building and compiling a custom CNN architecture. 
* Training the model and evaluating its performance on validation and test sets.

The CNN model characteristics are:

* An input layer for 64x64x3 images.
* Two blocks of "Conv2D" and "MaxPooling2D" for feature extraction.
* A "Flatten" layer followed by a 128-unit "Dense" layer with ReLU activation.
* A "Dropout" layer to prevent overfitting.
* A final "Dense" layer with Softmax activation for 4-class classification.

The model was compiled with the "adam" optimizer and "categorical_crossentropy" loss function.
<br><br>


-Results-

The model was trained for 10 epochs demonstrating:

* consistent downward trend in both training and validation loss, indicating effective learning.
* progressive increase in both training and validation accuracy, confirming the model's ability to classify both seen and unseen images with high precision.

The confusion matrix (as presented in block 6) highlights strong performance for "cloudy" and "desert" classes. However, the model sometimes misclassifies "green_area" and "water" images due to visual similarities, providing valuable insight into the model's capability and limitation.

Further analysis of misclassified images (as presented in block 9) confirms that errors are primarily concentrated between 
"green_area" and "water" classes, reinforcing the observations from the confusion matrix. This suggests that future work could involve more sophisticated architectures or additional features to better differentiate these challenging categories.
<br><br>


-Conclusion-

Overall, the CNN model successfully classifies the dataset satellite images into 4 distinct categories.

Future model improvements could explore more complex architectures, different datasets, or incorporate additional features to reduce ambiguity in image classification.

