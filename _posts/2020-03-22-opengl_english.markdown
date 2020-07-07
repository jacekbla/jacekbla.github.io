---
layout: post_english
title:  "Methods for graphics engine performance improvement"
date:   2020-04-19 00:12:50 +0100
featured-img: ogl1
categories: [eng]
---
## Project goal
The purpose of the work is to implement a graphics engine using the **OpenGL** graphic API as well as **GLFW** and **GLEW** support tools. As a part of the work, various methods will be added gradually to improve the performance of the tool. The work will focus on examining the impact of these techniques on the overall performance of the engine. For this benchmarks will be determined on the basis of which it will be possible to evaluate the tool's work. The tests will be carried out on many scenes, using various objects in such a way as to analyze various aspects of engine work.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/ogl.jpg)

## Methods for improving performance
As part of the work, the following techniques were implemented:
- Backface culling
- View frustrum culling
- Level of Detail
- Instanced Rendering
- Mipmapping

For comparative purposes, I also implemented anisotropic filtering - a method working on a similar principle to mipmapping, but focuses on improving image quality, not performance.

## Base version
A basic variant of the graphics engine was built, which does not use any of the studied techniques - it was the basis on which the analysis was carried out.
The engine has mechanisms to display the basic scene:
- Support for models in .obj data format and textures in .bmp and .png format.
- Lighting model - uses diffused and specular light.
- Terrain - terrain generation based on height maps and mixing textures using blend maps.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/multitextures.jpg)

- Water - water implementation using various techniques ([more informations here](https://jacekbla.github.io/eng/2020/01/29/opengl_water_english.html))

- Many light sources support, including spotlights.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/point_light.jpg)

- Skybox - a cube-based skybox has been implemented as the background of the scene.
- Fog - depending on the distance, objects on the stage become less visible. 
- Camera control - supports mouse and keyboard.  

## Application development and tests
Then studied efficiency improvement techniques were added to the engine and tests were carried out. In order to determine and measure the impact of a given method on the overall efficiency of the graphics engine, it was necessary to define indicators representing the level of solution's quality. They included parameters such as: frame time, number of frames per second, number of polygons per second, average number of rendered triangles, average number of rendered objects, CPU and GPU stress load and amount of memory used.
Tests were carried out on stages with different parameters to thoroughly examine the program's capabilities. External tools and internal measuring mechanisms were used to measure engine performance.

## Work results
The aim of the work was accomplished - the impact of methods that, without prejudice to the quality of the generated image, were able to significantly improve the performance of the graphics engine, was thoroughly analyzed and tested. In some cases, the frame time has been reduced by up to 95% compared to the basic version of the engine. During the work, I was also able to get familiarized with theoretical and implementation details of rendering applications.


[BitBucket](https://bitbucket.org/jacekbla/opengl1)

