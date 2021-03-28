# Cars-detection-and-evaluation-using-TensorFlow

## Technologies
Project is created with:
* numpy
* pandas
* tensorflow
* sklearn
* matplotlib
* seaborn

## General info
This project has the aim to recognize cars inside images and draw the relative bounding-box, we will also deploy an evaluation system based on the Intersection of the bounding boxes.
We will use the TensorFlow Object Detection API, to correctly install the API follow this [link](https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html#tensorflow-object-detection-api-installation).
We will use a pre-trained model to recognize cars inside our images, the dataset is extracted from [COCO](https://cocodataset.org/#download), we have also a .JSON file containing info about the pics, we will use the manually-crafted bounding boxes inside this file as test data to evaluate our model.
Once the pre-trained TensorFlow Object Detection has made his prediction and produced a bounding box, we will use the concept of [Intersection over Union](https://www.pyimagesearch.com/2016/11/07/intersection-over-union-iou-for-object-detection/) to perform matching between the predicted Bounding Boxes and the real ones.
Based on this matching and the confidence score of the model we will scikit-learn to calculate the Average Precision, this metric use the confidence score to obtain a better insight of the model performance:
in case of a non-matching prediction, the result will be weighted concerning the confidence score so that
a bad prediction with high confidence will be considered worse than a bad prediction with low confidence, for more info about this metric you can read the sklearn documentation at this [link](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html).
Using this information we can finally make a decision about a threshold of confidence to use when we have to produce new predictions.
