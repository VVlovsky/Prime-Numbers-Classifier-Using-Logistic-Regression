# Prime-Numbers-Classifier-Using-Logistic-Regression

### Wprowadzenie
W doświadczeniu wykorzystałem model regresji logistycznej trenowanego algorytmem SGD z momentum.
W rezultacie przeprowadzonych badań najlepszy wynik, który udało się uzyskać na zbiorze walidacyjnym to accuracy = 97% (precision = 97% i recall = 97%). To znaczy że uzyskany model poprawnie klasyfikuje podaną na wejście cyfrę w 97% przypadkach.


### Feature Vector

Oczywiście bezpośrednio podając normalizowane znaczenia każdego z pikseli jako feature vector nie otrzymamy potrzebnej informacji dla poprawnej klasyfikacji. Dodatkowo wektor o rozmiarze 28^2 elementów będzie miał duży wpływ na wydajność modelu. Więc dla mnie najcięższą częścią zadania okazało się tworzenie feature vector takiego, który dawałby dobre wyniki precision i recall i miałby nie więcej niż kilkadziesiąt elementów.

Okazało się, że standardowe metody tworzenia feature vector dla klasyfikacji każdej pojedynczej cyfry są słabo efektywne dla binarnej klasyfikacji na cyfry proste / złożone.

Na potrzeby zadania został wymyślony algorytm Blind Area Seach specyficzny dla podanego zagadnienia. Polega on na "farbowaniu" obrazu pod różnymi kątami różnymi kolorami. I później ilość pofarbowanych pikseli wystąpia osobnym znaczeniem dla każdego koloru w feature vector. (bardziej szczegółowo niżej)

Chociaż ten algorytm jest podstawą działania generacji wektoru dając najwięcej informacji o klasie cyfry, jednak go samego nie wystarcza dla wysokiej dokładności. Więc trzeba było dodać dodatkowe charakterystyki dla zwiększenia dokładności, co jednak miało wpływ na wydajność modelu. Finalnie dla każdej cyfry jest tworzony wektor o rozmiarze 70 elementów.


### Model

Prosty model regresji logistycznej trenowanego algorytmem SGD z momentum, dodatkowo posiadający regularyzacje L2.
