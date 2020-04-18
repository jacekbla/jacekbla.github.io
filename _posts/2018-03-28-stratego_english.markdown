---
layout: post_english
title:  "Stratego e"
date:   2018-03-28 23:12:50 +0100
featured-img: minmax
categories: [eng]
---
## Stratego
Głównym celem projektu była implementacja silnika gry „Stratego” oraz zapoznanie się i przenalizowanie algorytmów rozwiązywania gier logicznych. 
Gra polega na zajmowaniu kolejnych pól na planszy. W czasie swojego ruchu gracz wybiera wolne pole które chce zająć, jeżeli wybrane pole tworzy z innymi zajętymi polami co najmniej jedną linię (od krawędzi planszy do krawędzi), składającą się z przynajmniej 3 pól, otrzymuje wówczas liczbę punktów równą liczbie pól, z których składają się wszystkie linie przechodzące przez zajęte pole. Gracze wykonują ruchy na przemian. Niektóre warianty gry przewidują punkty tylko za pola wcześniej przez jednego z graczy oraz po jednym punkcie za każdą linię, niezależnie od długości. Rozmiary planszy nie są z góry ustalone, mogą się zmieniać.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/stratego/stratego.jpg)

## Podstawowe algorytmy rozwiązywania gier

### min-max
Min-max jest algorytmem stosowanym dla minimalizacji możliwej straty w scenariuszu najgorszego przypadku (maksymalna strata) i maksymalizacji minimalnego zysku. Pierwotnie sformułowany dla teorii gier o sumie zerowej dwóch graczy, obejmujący zarówno przypadki, w których gracze wykonują ruchy alternatywne, jak i te, w których wykonują ruchy jednocześnie, został również rozszerzony na bardziej złożone gry i do ogólnego podejmowania decyzji w obecności niepewności.

### alfa-beta
Przycinanie alfa-beta to algorytm wyszukiwania, który ma na celu zmniejszenie liczby węzłów, które są oceniane przez algorytm min-max w drzewie wyszukiwania. Jest to algorytm wyszukiwania przeciwnika, powszechnie stosowany w grach komputerowych w grach dwuosobowych.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/stratego/menu.jpg)

## Heurystyki 

#### Heurystyki oceny stanu gry
Zastosowane zostały 3 heurystyki do oceny stanu gry:
- standardowa – kolory nie mają znaczenia, punkty przyznawane za pełną linię od krawędzi do krawędzi. Liczba punktów wynosi tyle co długość linii.
- kolorowa – kolory mają znaczenie, punkty przyznawane za pełną linię od krawędzi do krawędzi. Liczba punktów wynosi tyle co liczba pól o kolorze gracza w linii.
- jeden za linie – niezależnie od kolory gracze dostają po 1 punkcie po domknięciu linii.

#### Heurystyki wyboru kolejności węzłów
Zaimplementowane zostały 2 heurystyki wyboru kolejności węzłów:
- standardowa – węzły wybierane są po kolei
- losowa – węzły wybierane są w kolejności losowej
