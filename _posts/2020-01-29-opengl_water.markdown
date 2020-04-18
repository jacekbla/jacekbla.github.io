---
layout: post
title:  "Realistyczna symulacja wody"
date:   2020-01-29 23:12:50 +0100
featured-img: elefun
---
## Cel projektu

Celem pracy było utworzenie sceny 3D, wykorzystującej API graficzne OpenGL do realistycznego odwzorowania wody z użyciem zaawansowanych efektów graficznych. Aby prawidłowo zrealizować zadanie konieczna była implementacja technik imitujących zjawiska fizycznye, które opisują zachowanie się wody - między innymi efekt Fresnela, odbicie oraz załamanie wody.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl_water/dudv.gif)


## Wynik prac

Zrealizowana scena przedstawia jezioro otoczone przez powierzchnię utworzoną z użyciem oprogramowania open-source Blender. Sama tafla wody generowana jest w kodzie programu. Sterowanie z użyciem klawiatury i myszki umożliwia swobodne przemieszczanie i obracanie kamery w obrębie sceny.

Większość efektów osiągnięta poprzez jednostki cieniujące, wśród nich można wymienić:
- Refrakcja i odbicie - ustalana jest płaszczyzna przycinająca (clip plane), która dzieli całą scenę na obszar znajdujący się powyżej tafli waody oraz poniżej. Następnie utworzone zostają dwa fbo (frame buffer object). Na pierwszy z nich renderowany jest widok z kamery o niezmienionej pozycji, ale obcięty o wszystko ponad płaszczyzną przycinającą. Drugi fbo przechowuje widok z kamery analogicznie spoglądającej w stronę tafli wody, jednak przesuniętej w dół o wartość odpowiadającą dwukrotnej wysokości pierwotnej kamery. W tym przypadku kamera nie wdzi obszaru położonego poniżej płaszczyzny przycinającej. Na koniec obrazy z obu fbo nakładane są na taflę wody, dodany zostaje delikatny kolor niebieski oraz inne efekty.
- Efekt Fresnela - decyduje o stosunku odbicia do refrakcji. Patrząc na wodę z góry użytkownik powienien bez przeszkód zobaczyć dno zbiornika, podczas gdy patrząc pod niewielkim kątem należy spodziewać się, że odbicie będzie bardzo wyraźne.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl_water/fresnel.jpg)

- Efekt mętnej wody - utworzona została mapa głębokości zbiornika wody. Na jej podstawie dodany kolor niebieski jest coraz bardziej intensywny w niżej położonych obszarach. Nadaje to efekt mętności, w głębinach nie jesteśmy w stanie dostrzec odbicia i refrakcji.
- Zanikające krawędzi - za pomocą manipulacji składowej alfa koloru wody, staje się ona coraz mnie widoczna przy brzegach zbiornika.
- Mapy dudv - w celu wprawienia wody w ruch zastosowane zostały dwie metody. Jedna z nich to mapy dudv. Z wczytanych tekstur pobierane są wartości nasycenia kolorów zielonego i czerwonego, na podstawie których nakładane na wodę zostają zniekształcenia. Tekstura przesuwana jest po tafli wody w czasie, dzięki czemu woda zdaje się być w ruchu.
- Poruszanie wierzchołków - drugą metodą wprawienia tafli wody w ruch jest manipulacja jej siatką wierzchołków.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/ogl_water/moving_vert.gif)

GitHub:
[Ruchomy mesh](https://github.com/jacekbla/opengl_water_moving_mesh)

[Mapy dudv](https://github.com/jacekbla/opengl_water_dudv)

