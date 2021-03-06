---
layout: post_english
title:  "Resizer"
date:   2018-12-21 23:12:50 +0100
featured-img: suru
categories: [eng]
---
## Project description
The project was aimed at implementing a program using techniques for changing the size of the image, taking into account its content, and analyzing the problem using the created side application. At the beginning, a design was prepared, containing functional and non-functional requirements, UML diagrams and comparison with applications available on the market. The software allows you to change the size of the image taking into account its content and present some of the functions available through the use of these techniques. Standard options for scaling and cropping graphics have also been defined so that different techniques can be compared.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/gui.jpg)

Nowadays, people are dealing with a wide variety of devices with different screen diagonals, which display various images using all kinds of applications.
It is expected that the photo or website displayed on your desktop computer will transmit the same information on your phone. Often, however, objects that are spotted without problems on a larger screen can be problematic when looked at on another device. With a standard resizing the image may be distorted, its proportions changed, an important object overlooked, and an invalid element left. Looking at many photos, you can notice a lot of useless space that does not bring much valuable information to the image.
This work deals with such a problem - the use of unnecessary space for important objects without compromising the overall picture.

## Algorithms
The algorithm used to implement the mechanism of content-aware image resizing is **Seam-Carving**. It was developed by Shai Avidan from Mitsubishi Electric Research Laboratories and Ariel Shamir from the Interdisciplinary Center at Herzliya and Mitsubishi Electric Research Laboratories.
The method determines the weight of each pixel of the image and based on it finds seams (pixel paths with the lowest energy), which are then removed or inserted, depending on whether the file is to be reduced or enlarged.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/comparasion_eng.jpg)

The algorithm also allows the implementation of several interesting functionalities, such as:

- objects amplification
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/amplify_eng.jpg)

- object deletion
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/delete_eng.jpg)

The effect of the **Forward-Energy** technique was also studied, which turned out to be very beneficial for the modified image - it reduced the intensity or completely got rid of artifacts that tend to appear at larger values ​​of image size change.
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/forward_energy_eng.jpg)


## Tools
The Seam-Carving algorithm and most of the program's functionalities have been implemented using the *C++* language, its standard libraries and the **OpenCV** library. Everything was contained in the dynamic DLL library. The graphical interface that uses these functionalities was written in *Java* using the **JavaFX** library. Both components have been combined using **JNI** - Java Native Interface.

## Tests
The entire application has been covered with unit tests. Their task was to check the correctness of actions performed by individual methods or mechanisms that are supposed to satisfy given functionality. The tests verified various possible paths through the program, boundary values ​​and compliance of returned results. For some tests, the program code had to be modified accordingly. The tests were written using the following tools:

- JUnit 4.12
- TestFX 4.0.15
- Google Test

## Analysis
The analysis of the content-aware image resizing mechanism aims to examine whether it is worth using it at all, to show the benefits of this approach as well as its problems and limitations. To evaluate the results, so-called key points have been used.
In the work, the **Harris-Affine** detector was used to detect key points, and the **SIFT** descriptor was used to describe it. A ready-made tool was used to determine this type of key points.

Support software has been implemented that accepts .haraff.sift files and analyzes the similarity of two images. The program has the following functionalities:

- Determination of key point neighborhood - for each key point of one image, the key point of the other image whose characteristics are most similar is searched for. Such a few points are called neighbors.
    
- Determination of key point pairs - a pair of key points are two points whose characteristic feature is mutual neighborship, i.e. the nearest neighbor of point A is point B and the nearest neighbor of point B is point A.

- Visualization of key point pairs - the program displays both images with the help of the **OpenCV** library and draws lines connecting pairs of key points.
    
![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/resizer/key_points.jpg)
    
- Determination of the average difference of image features - for each pair of key points of two images, a value is calculated taking into account the number of key point pairs and their quality, defined using the feature vector. The indicator value for two identical images is 0.

The software has been implemented in *C++* using the **Visual Studio** environment. Uses standard libraries as well as **Boost** and **OpenCV** libraries.  

[BitBucket](https://bitbucket.org/jacekbla/resizer)

