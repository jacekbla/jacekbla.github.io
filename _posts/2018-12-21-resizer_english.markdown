---
layout: post_english
title:  "Resizer"
date:   2018-12-21 23:12:50 +0100
featured-img: suru
categories: [eng]
---
## Project description
The project was aimed at implementing a program using techniques for changing the size of the image, taking into account its content, and analyzing the problem using the created application. At the beginning, a proprietary application design was prepared, containing functional and non-functional requirements, UML diagrams and comparison with applications available on the market. The software will allow you to change the size of the image taking into account its content and present some of the functions available through the use of these techniques. Standard options for scaling and cropping graphics have also been defined so that different techniques can be compared.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/gui.jpg)

Nowadays, people are dealing with a wide variety of devices with different screen diagonals, which display various images using various applications.
It is expected that the photo or website displayed on your desktop computer will transmit the same information on your phone. Often, however, objects that are spotted without problems on a larger screen can be problematic when accurately perceived on another device. With a standard resizing of one dimension, the image may be disturbed, its proportions changed, an important object overlooked, and an invalid element left. Looking at many photos, you can notice a lot of undeveloped space that does not bring much valuable information to the image.
This work deals with such a problem - the use of unnecessary space for important objects without compromising the overall picture.

## Algorithms
The algorithm used to implement the mechanism of changing the size of the image including its content is *Seam-Carving*. It was developed by Shai Avidan from Mitsubishi Electric Research Laboratories and Ariel Shamir from the Interdisciplinary Center at Herzliya and Mitsubishi Electric Research Laboratories.
The method determines the weight of each pixel of the image and based on it finds seams (pixel paths with the lowest energy), which are then removed or inserted, depending on whether the file is to be reduced or enlarged.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/comparasion.jpg)

The algorithm also allows the implementation of several interesting functionalities, such as:

- object amplification
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/amplify.jpg)

- object deletion
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/delete.jpg)

The effect of the *Forward-Energy* technique was also studied, which turned out to be very beneficial for the modified image - it reduced the intensity or completely got rid of artifacts that tend to appear at larger values ​​of image size change.
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/forward_energy.jpg)


## Tools
The Seam-Carving algorithm and most of the program's functionalities have been implemented using the C++ language, its standard libraries and the OpenCV library. Everything was contained in the dynamic DLL library. The graphical interface using these functionalities was written in Java using the JavaFX library. Both components have been combined using JNI - the native Java interface.

## Tests
The entire application has been covered with unit tests. Their task was to check the correctness of actions performed by individual methods or mechanisms that meet the given functionality. The tests verified various possible paths through the program, boundary values ​​and compliance of returned results. For some tests, the program code had to be modified accordingly. The tests were written using the following tools:

- JUnit 4.12
- TestFX 4.0.15
- Google Test

## Analysis
The analysis of the image change mechanism, taking into account its content, aims to examine whether it is worth using it at all, to show the benefits of this approach as well as its problems and limitations. To evaluate the results, so-called key points.
In the work, the Harris-Affine detector was used to detect key points, and the SIFT descriptor was used to describe it. For determining this type of key points using a ready-made tool.

Support software has been implemented that accepts .haraff.sift files and analyzes the similarity of two images. The program has the following functionalities:

- Determination of key point neighborhood - for each key point of one image, the key point of the other image whose characteristics are most similar is searched for. Such a few points are called neighbors.
    
- Determination of key point pairs - a pair of key points are two points whose characteristic feature is mutual proximity, i.e. the nearest neighbor of point A is point B and the nearest neighbor of point B is point A.

- Visualization of key point pairs - the program displays both images with the help of the *OpenCV* library and draws lines connecting pairs of key points.
    
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/key_points.jpg)
    
- Determination of the average difference of image features - for each pair of key points of two images, the absolute value is calculated from the difference in the value of each of the features. All these differences are added together, and then this sum is divided by the number of pairs of key points. The value obtained in this way takes into account the number of pairs of key points and their quality, defined using the feature vector. The indicator value for two identical images is 0.

The software has been implemented in C++ using the *Visual Studio* environment. Uses standard libraries as well as *Boost* and *OpenCV* libraries.  

[BitBucket](https://bitbucket.org/jacekbla/resizer)

