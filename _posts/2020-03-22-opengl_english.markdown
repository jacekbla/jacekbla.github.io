---
layout: post_english
title:  "e Metody poprawy wydajności silnika graficznego"
date:   2020-03-22 23:12:50 +0100
featured-img: ogl1
categories: [eng]
---
Celem pracy jest implementacja silnika graficznego wykorzystującego API graficzne OpenGL oraz narzędzia pomocnicze GLFW i GLEW. W ramach pracy stopniowo dodawane będą różne metody poprawiające wydajność narzędzia. Praca będzie skupiać się na badaniu wpływu tych technik na ogólną sprawność silnika. W tym celu zostaną wyznaczone parametry, na podstawie których możliwa będzie ocena pracy narzędzia. Testy zostaną przeprowadzone na wielu scenach, z wykorzystaniem rozmaitych obiektów w taki sposób, aby przeanalizować różne aspekty pracy silnika.

Projekt stanowi moją pracę magisterską, nie jest skończony.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/ogl.jpg)

## Metody poprawy wydajności
Projekt przewiduje implementację takich technik jak:
- Mipmapping
- Occlusion culling
- Backface culling
- View frustrum culling
- Far Clip plane
- Manipulacja poziomem detali (Level of Detail)
- Atlasy tekstur

## Stan pracy
Aktualnie zbudowana została podstawowa wersja silnika graficznego. Ta postać wykorzystuje żadnej z badanych technik - będzie stanowiła bazę, na podstawie której przeprowadzona zostanie analiza.
Silnik posiada mechanizmy umożliwiające wyświetlenie podstawowej sceny:
- Obsługa obiektów w formacie .obj i tekstur w formacie .bmp i .png.
- Teren - generacja terenu na podstawie map wysokości oraz mieszanie tekstur terenu z użyciem map mieszających (blend map).

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/multitextures.jpg)

- Woda - implementacja wody z użyciem rozmaitych technik ([więcej informacji tutaj](https://jacekbla.github.io/2020/01/29/opengl_water.html))
- Wiele źródeł światła, w tym światła punktowe.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl/point_light.jpg)

- Skybox - jako tło sceny zaimplementowano skoybox oparty na sześcianie.
- Mgła - w zależności od odległości obiekty na scenie są coraz mniej widoczne.
