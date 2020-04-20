---
layout: post_english
title:  "Classification of trajectories of means of transport"
date:   2019-09-10 23:12:50 +0100
featured-img: tpdia
categories: [eng]
---
## Project goal
The project focuses on the study of user movement, it presents a solution to the problem of feature extraction and trajectory classification of various means of transport. Research focuses on the analysis and proper preparation of raw trajectories downloaded from the GeoLife database and their classification into a given means of transport using deep neural networks. The aim of the work was to review, implement and analyze the solution proposed in the article. The task was carried out in a team of two. I was responsible for the first part of the work - data preparation.

## Review of publication
The publication on the basis of which the study was conducted is **"Classifying spatial trajectories using representational learning"**, written by Yuki Endo, Hiroyuki Toda, Kyosuke Nishida and Jotaro Ikedo.
Research shows that deep neural networks are good at analyzing images, which is why the authors decided to transform trajectories and represent them in graphic form. The image uses grayscale, non-black pixels show the route. This format allows time information to be saved - the brighter the pixel, the more time the user spent in a given place. The images prepared this way are transmitted to a deep neural network, where the automatic extraction of features takes place. The neural network learns to recognize the features that distinguish given modes of transport, and classifies images into separate classes according to automatically learned rules.

## Solution
We decided to divide the project into two programs. The first of these deals with the transformation of raw trajectories into images ready for transmission of a neural network. This program was written in **Java**. The second program written in **Python** deals with neural network training and model validation. We decided on this environment mainly due to the support of external libraries that implement an interface that allows working with deep neural networks.

### Segmentation and preparation of data
Data preparation boils down to converting .plt files into images in .png format.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/tpdia/img_gen_eng.jpg)


This process can be divided into several stages:
- Segmentation - all points in a given time period are saved as one segment.
- Sampling - then in order to set equal periods of time between the route points, it should be sampled.
- Cropping - then in order to standardize data given area is cropped in such a way that all fragments of the route contain data from areas of the same size.
- Assigning points to pixels - now assign individual trajectory points to the pixels of the output image. A table with dimensions corresponding to the image resolution is created, to which points located in a given section of the route are counted. After this stage, the table containing the number of points present in the sections is ready to be converted into a graphic image.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/tpdia/img_gen2.jpg)

- Assigning values ​​to pixels - the values ​​in the table created in the previous step are normalized. Then, based on the table, the color values ​​of each pixel are derived.

Sample output images:
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/tpdia/example_imgs.jpg)


### External libraries used
As already mentioned, we decided to work with the **Python** language due to the powerful libraries in the field of machine learning and neural networks. In particular, we wanted to use the following libraries:
- Tensorflow
- Keras
- NumPy

### Learning and classification
Prepared data, that is labeled, is saved to folders described by the name of the means of transport. Then the learning program loads data from folders and, using Data Augumentation techniques, enlarges the training data set.

The tests performed checked the effects obtained by performing rotation, mirroring, cropping and zooming of data on the images. Performed tests showed a positive effect of generating additional data by rotation and reflection, but the positive effect of cropping and zooming was not noticed. The neural network used in the final solution consisted of three convolution layers and four fully connected. All layers except the last one use the ReLU activation function.

The last layer uses the softmax function. Tests were carried out to determine the correct size of each layer. The error function we used was the cross-entropy function. The learning process uses the adam optimizer and dropout value of 0.5 on the penultimate layer of the neural network.

### Verification
Before generating the images, we divided users into five groups in order to perform a fully reliable method of cross-validation. In this way, we received data groups from various, fully independent sources. Using this method, we performed training of five models, each time testing the model on a different part and using the remaining four for training. Division by user has a disadvantage in the form of uneven presence of training data of different classes in the group, e.g. in group No. 4 we received overrepresentation of data regarding the representation of car trajectories, which caused difficulties in the testing phase.