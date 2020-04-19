---
layout: post_english
title:  "Methods for graphics engine performance improvement"
date:   2020-04-19 00:12:50 +0100
featured-img: ogl1
categories: [eng]
---
## Project goal
The purpose of the work is to implement a graphic engine using the **OpenGL** graphic API as well as **GLFW** and **GLEW** support tools. As part of the work, various methods will be added gradually to improve the performance of the tool. The work will focus on examining the impact of these techniques on the overall efficiency of the engine. To this end, parameters will be determined on the basis of which it will be possible to evaluate the tool's work. The tests will be carried out on many stages, using various objects in such a way as to analyze various aspects of engine operation.

The project is my master's thesis, it is not finished.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/ogl.jpg)

## Methods for improving performance
The project provides for the implementation of techniques such as:
- Mipmapping
- Occlusion culling
- Backface culling
- View frustrum culling
- Far Clip plane
- Level of Detail manipulation
- Texture atlases

## Work status
The basic version of the graphics engine has now been built. This character uses any of the techniques studied - it will be the basis on which the analysis will be carried out.
The engine has mechanisms to display the basic scene:
- Support for objects in .obj format and textures in .bmp and .png format.
- Terrain - terrain generation based on height maps and mixing terrain textures using blend maps.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/multitextures.jpg)

- Water - water implementation using various techniques ([more informations here](https://jacekbla.github.io/eng/2020/01/29/opengl_water_english.html))

- Many light sources, including spotlights.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/point_light.jpg)

- Skybox - a cube-based skoybox has been implemented as the background of the stage.
- Fog - depending on the distance, objects on the stage are becoming less visible.  

[BitBucket](https://bitbucket.org/jacekbla/opengl1)

