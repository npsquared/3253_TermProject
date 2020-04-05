# 3253_TermProject: Quick-draw dataset

Doodle Prediction using CNN, Tensorflow, Keras.

### Notebooks
preprocess.ipynb

preprocess_analysis.ipynb

data_model.ipynb

### Data
Data used for this project is the crowdsourced Quick-Draw data set which Google amassed using their online game called Quick Draw. The data set contains over 50 million drawings or doodles submitted by users. The drawings are classified into 345 different classes that range from 'aircraft carrier' to 'zig-zag'. 

For data analysis and wrangling, only 20 classes of drawings have been considered, and first 10000 image samples were used for each category. This makes the analysis phase a bit quicker. 

For the actual CNN data modelling, we decided to be ambitious and use all 345 classes to build a Convolutional Neural Network. However, only the first 10000 image samples were used for each category. As we will see later, 10000 images is not enough samples to make a prediction with great accuracy. 

### Downloading the Quick Draw dataset: 
 Entire dataset is available here: 
  https://github.com/googlecreativelab/quickdraw-dataset
  
  https://console.cloud.google.com/storage/browser/quickdraw_dataset/full/numpy_bitmap
  
  For this project, we are working with preprocessed dataset provided by Google Creative Lab.
  
  All the drawings have been rendered into a 28x28 grayscale bitmap in numpy .npy format. 
  

Step1: Install gsutil:  https://cloud.google.com/storage/docs/gsutil_install?hl=fr

Step2: gsutil -m cp gs://quickdraw_dataset/full/simplified/*.npy

### Data wrangling

Since the goal of this project is to build a CNN model using all 345 image classes, the data wrangling steps to achieve this were as follows: 
1) Created a dictionary for url and class labels to dowbload the entiry dataset in .npy files. 
2) Then the dataset was downloaded into a dictionary. 
3) Normalized the image pixels between 0 and 1, and added class labels. 
4) Aggregate the first 10,000 arrays for every doodle into one array of doodles. 
5) Split the data into features and target labels. 
6) Save the train and test data as serialised data using pickle files. 

The steps listed above are described in the jupyter notebook titled preprocess.ipynb

### Challenges

I kept getting a 'Memory Error' trying to create a a dictionary object using the downloaded data. See below: 

![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/MemoryError.PNG)

Running the code in colab crashed the application and produced a RAM error as well. We will have to take another approach to set up data for 345 samples to create our CNN model. 

Following piece of code generates png image files from the .npy files and splits the image files into train and test data:

![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/Code1.PNG)
![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/train_set.PNG)
![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/test_set.PNG)

These images will be used to generate our CNN model to classify 345 images. 

### Analysis

Ammount of test data:
![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/amt_test_data.PNG)

Plotting an intensity histogram for some of the classes:

![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/intensity_histogram.PNG)

### Data modelling

We attempted to build a CNN model with 345 classes. Architecture of our CNN model is below:

![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/cnn_architecture.PNG)

Model summary:
![Image description](https://github.com/npsquared/3253_TermProject/blob/master/images/model_summary.PNG)

