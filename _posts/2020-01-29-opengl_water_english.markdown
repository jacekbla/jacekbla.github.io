---
layout: post_english
title:  "Realistic water simulation"
date:   2020-01-29 23:12:50 +0100
featured-img: elefun
categories: [eng]
---
## Project goal
The aim of the work was to create a 3D scene, using the OpenGL graphics API to realistically reproduce water using advanced graphic effects. To properly accomplish the task, it was necessary to implement techniques imitating physical phenomena that describe the behavior of water - including the Fresnel effect, reflection and refraction of water.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl_water/dudv.gif)


## Result of work
The completed scene shows a lake surrounded by a surface created using the open-source Blender software. The water surface itself is generated in the program code. Keyboard and mouse control allows free movement and rotation of the camera within the scene.

Most of the effects achieved through the shading units, among them can be mentioned:
- Refraction and reflection - a clip plane is established that divides the entire stage into an area above the waoda surface and below. Then two fbo (frame buffer object) are created. On the first of them, the camera view is rendered unchanged, but cut off by everything above the clipping plane. The second fbo stores the view from the camera looking in the same direction towards the water surface, but shifted down by the value corresponding to twice the height of the original camera. In this case, the camera does not see the area below the clipping plane. Finally, images from both fbo are applied to the water surface, a delicate blue color and other effects are added.
- Fresnel effect - determines the ratio of reflection to refraction. Looking at the water from above, the user should see the bottom of the tank without hindrance, while looking at a small angle, the reflection should be expected to be very clear.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl_water/fresnel.jpg)

- Murky water effect - a depth map of the water tank has been created. On its basis, the added blue color is more and more intense in the lower areas. This gives the effect of murkiness, in the depths we are not able to see the reflection and refraction.
- Blending edges - by manipulating the alpha component of the water color, it becomes increasingly visible at the edges of the tank.
- dudv maps - two methods were used to set the water in motion. One of them is dudv maps. From the loaded textures, saturation values ​​of green and red colors are taken, based on which distortions are applied to the water. The texture is moved over the water surface in time, thanks to which the water seems to be moving.
- Moving mesh - the second method to set the water surface in motion is to manipulate its tops grid.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl_water/moving_vert.gif)

GitHub:  
[Moving mesh](https://github.com/jacekbla/opengl_water_moving_mesh)

[dudv maps](https://github.com/jacekbla/opengl_water_dudv)

