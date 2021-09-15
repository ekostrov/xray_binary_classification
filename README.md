```
├── README.md                           <- The top-level README for reviewers of this project
├── JupyterNotebooks/submission.ipynb      <- Narrative documentation of analysis in Jupyter notebook
├── non_technical.pdf                    <- PDF version of project presentation
└── images                              <- Both sourced externally and generated from code
```
![xray](../images/first.png)
***
# Classify Chest X-ray Images
** by Yevgeniy Kostrov
***

***
# Overview
## In this project, I create a model that will classify x-ray image of a chest as the one that has pneumonia or the one that doesn't have pneumonia.

## During the analysis:
## 1.  I will perform the necessary data wrangling first.
## 2. I will build a Baseline Model from scratch.
> * ##   I will check the performance of the baseline model.
## 3.  I will build a Transfer Learning Model based on the VGG19 architecture.
>  *   ## I will check the performance of the transfer learning model.
## 4. I will compare the results of the beforementioned models to choose the better of the two.

***
# Business Problem
## Pneumonia is a very dangerous diseases that is caused by a bacterial or viral infection of the lungs. The consequences of pneumonia could be catastrophic within a short period of time if not diagnosed quickly. Two years ago my father was admitted into an emergency room with pneumonia, but doctors in the emergency facilities could not find pneumonia in the x-ray images, eventually they needed help of the expert and it took them about 8 hours to figure the cause of the disease. It would be great to design a system of automatic diagnosis, capable of analyzing X-rays and help the pneumonia detection on early stages. In this project I will develop two models for the classification of chest X-ray images into NORMAL (no pneumonia) vs. PNEUMONIA(there is pneumonia in the lungs). I will recommend the model that has a better performance.

***
# Metrics for Assessement of Models:
## 1. The primary metric for my analysis will be recall.
> * ##   Recall is defined as: a number of True Positives divided by the number of Total Actual Positives.
> * ##   Thus Recall is a better model metric when there is a high cost associated with False Negative.
> * ##   In our case False Negative is predicting images as ”NORMAL” when in reality the image has the label ”PNEUMONIA”. 
> * ##   In this case pneumonia will not be diagnosed in the patient and consequnces might be drastic.

## 2. The secondary metric will be accuracy.
> * ## deepai.org defines accuracy as follows:"The accuracy of a machine learning classification algorithm is one way to measure how often the algorithm classifies a data point correctly. Accuracy is the number of correctly predicted data points out of all the data points. More formally, it is defined as the number of true positives and true negatives divided by the number of true positives, true negatives, false positives, and false negatives. A true positive or true negative is a data point that the algorithm correctly classified as true or false, respectively. A false positive or false negative, on the other hand, is a data point that the algorithm incorrectly classified. For example, if the algorithm classified a false data point as true, it would be a false positive. Often, accuracy is used along with precision and recall, which are other metrics that use various ratios of true/false positives/negatives. Together, these metrics provide a detailed look at how the algorithm is classifying data points." 


# Data Description
* ## Data for this project was downloaded from [Mendeley Data: Large Dataset of Labeled Optical Coherence Tomography (OCT) and Chest X-Ray Images](https://data.mendeley.com/datasets/rscbjbr9sj/3).

* ## Data consists of chest x-ray images located in two directories: train with images for training a model  and test with images for testing a model at the end.

* ## Images in the directory are of different size so the have to be regularized before training and testing.

# Cleaning/Modifying Data:
* ## I deleted one file in the training set that had incompatible label.
* ## I put the paths to the files and labels into dataframe so it would be easier to create Data Generators and, also, would beeasier to test my models.
* ## I used preprocessing function from Keras/VGG19 model to bring pictures to the same shape and form for training and testing.

# Modeling 

* ## I built two models for comparison
* ## First, I built a baseline model from scratch and trained it for 30 epochs.
* ## Second, I built a transfer learning model for which I used VGG19 model provided by Keras/Tensorflow and initila weights came from 'imagenet' pre-trainded weights, then I added few dense layers of my own.
* ## I warmed up the model by freezing the VGG19 layers and just updating the top layers while training for 10 epochs.
* ## I unfreeze all layers and trained the whole model for 20 epochs.

***
# Conclusion
***

# Modeling
* ## Transfer Learning model based on VGG19 performed better getting better recall and accuracy scores compared to the baseline model that achieved recall scores

# Business decision:
## **Based on my analysis, I suggest to use transfer learning model for detection of pneumonia in the x-ray images. It can help doctors to detect pneumonia faster with high accuracy according to the scores we have from testing set of images. I have to add, that more testing is required to be sure that the model preforms well.**

# Ways to improve the project:
* ## One way would be to build custom model taylored towards our particular set of images.
* ## Another way, would be to use another model for transfer learning.
* ## Find more extensive data set  with chest x-ray images.

# Please review my full work in [Jupyter Notebook](https://github.com/ekostrov/xray_binary_classification/blob/main/JupyterScripts/submission.ipynb) or in the [non technical presentation](non_technical.pdf)

For any additional questions, please contact Yevgeniy (Gene) Kostrov at ekostrov@yahoo.com
