---
layout: post
title:  "openGL water"
date:   2020-01-29 23:12:50 +0100
featured-img: elefun
---
Cel projektu

Celem zajęć projektowych z przedmiotu Programowanie w API Graficznych, było utworzenie sceny 3D w OpenGL, z uwzględnieniem zaawansowanych efektów graficznych. Do implementacji wybrano algorytmy pozwalające na realistyczne odwzorowanie wody oraz symulację cyklu dnia i nocy.
Do prawidłowego zrealizowania zadania konieczne było zapoznanie się z rzeczywistymi zjawiskami fizycznymi opisującymi zachowanie się wody - między innymi efekt Fresnela, refrakcja oraz refleksja. Dodatkowo zdecydowano się na próbę użycia teselacji w celu poprawy jakości otrzymywanych rezultatów.

Wynik prac

Zrealizowana scena przedstawia jezioro otoczone przez powierzchnię utworzoną z użyciem wolno źródłowego oprogramowania Blender. Do sceny zostały dodatkowo zaimportowane obiekty słonia i latarni stanowiącej dodatkowe źródło światła po zajściu słońca. Sterowanie z użyciem klawiatury i myszki umożliwia na swobodne przemieszczanie i obracanie kamery w obrębie sceny. Dodatkowe możliwe jest włączanie i wyłączanie poszczególnych efektów graficznych takich jak teselacja.

Jednym z najważniejszych zjawisk dotyczących wody było odbijanie obiektów nad jej powierzchnią i zniekształcanie odbicia wynikające z falowania. Renderując obraz widoczny z innego kąta niż kamera i odcinając odpowiednią część modelu udało się wyświetlić odbicie w odpowiednim miejscu. Całość była odpowiednio połączona z widokiem dna w proporcji zależnej od kąta pomiędzy normalną płaszczyzny i obserwatorem - zgodnie z efektem Fresnela.
Samo falowanie i wynikające z niego zniekształcenie obrazu zostało zrealizowane zarówno na płaskiej tafli jeziora w jednostce cieniującej, jak i poprzez poruszanie wierzchołkami wygenerowanej siatki wody oraz tymi uzyskanymi dzięki teselacji.
Warto również wspomnieć o wpływie głębokości wody w danym punkcie na wynikową przezroczystość w danym punkcie i rozmyciu obrazu przy lądzie.

Istotnym elementem całego projektu było również zaprogramowanie cyklu dnia i nocy. Główne źródło światła na scenie porusza się dookoła sceny. Oprócz oczywistych zmian w oświetleniu samych płaszczyzn modelu, w płynny zmienia się kolor nieba - niebieski dla słońca znajdującego się wysoko nad sceną, przez pomarańcz przy wschodzie i zachodzie, oraz niemal czarny w czasie nocy.

Podsumowanie

W czasie trwania projektu udało się zapoznać ze zjawiskami fizycznymi opisującymi zachowanie się wody i zaimplementować najważniejsze z nich. Uzyskana wiedza może zostać użyta przy realizacji innych projektów związanych z komputerowym generowaniem grafiki.
Całość projektu została przedstawiona prowadzącemu i oceniona pozytywnie.
