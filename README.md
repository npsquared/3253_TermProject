# 3253_TermProject

Drawing Prediction using CNN, Tensorflow, Keras. 

Model will be run using a Flask + html application. 

# Downloading the Quick Draw dataset: 
 Entire dataset is available here: 
  https://github.com/googlecreativelab/quickdraw-dataset
  
  For this project, we are working with preprocessed dataset provided by Google Creative Lab.
  
  All the drawings have been rendered into a 28x28 grayscale bitmap in numpy .npy format. 
  

Step1: Install gsutil:  https://cloud.google.com/storage/docs/gsutil_install?hl=fr

Step2: gsutil -m cp gs://quickdraw_dataset/full/simplified/*.npy

