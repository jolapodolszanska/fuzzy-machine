# Implementacja sterownika rozmytego do kontroli procesów

Projekt sterownika do kontroli procesu prania pojawił się na moich zajęciach laboratoryjnych na przedmiocie Podstawy Sztucznej Inteligencji na UJD.

## Wprowadzenie do logiki rozmytej

Logika rozmyta zawiera wiele wartości logicznych i wartości te są wartościami prawdy zmiennej lub problemu pomiędzy 0 a 1. Koncepcja ta została wprowadzona przez Lofti Zadeh w 1965 roku w oparciu o Fuzzy Set Theory. Koncepcja ta zapewnia możliwości, które nie są podawane przez komputery, ale podobne do zakresu możliwości generowanych przez ludzi. Logika rozmyta może być zaimplementowana w systemach takich jak mikrokontrolery, systemy oparte na stacjach roboczych lub duże systemy oparte
na sieciach w celu osiągnięcia określonego wyjścia. Może być również zaimplementowana zarówno w spręcie jak i oprogramowaniu.

## Potrzebne biblioteki

Do zrealizowania tego zadania potrzebne będzie zainstalowanie pakietu scikit-fuzzy

```conda
  conda install -c conda-forge scikit-fuzzy
```

## Zasada działania

Program zawiera dwie zmienne wejściowe, które będą reprezentować typ brudu oraz stopień zabrudzenia za pomocą wartości liczbowych (1-100). Czas prania będzie generowany w zależności od stopnia i rodzaju zabrudzenia. Za pomocą pakietu scikit-fuzzy wygenerujemy układ sterujący, który oszacuje ile czasu zajmie wypranie jednej partii ubrań. 

## Reguły

```python
    rule1 = ctrl.Rule(degree_dirt['High'] | type_dirt['Fat'], wash_time['VeryLong'])
    rule2 = ctrl.Rule(degree_dirt['Medium'] | type_dirt['Fat'], wash_time['long'])
    rule3 = ctrl.Rule(degree_dirt['Low'] | type_dirt['Fat'], wash_time['long'])
    rule4 = ctrl.Rule(degree_dirt['High'] | type_dirt['Medium'], wash_time['long'])
    rule5 = ctrl.Rule(degree_dirt['Medium'] | type_dirt['Medium'], wash_time['medium'])
    rule6 = ctrl.Rule(degree_dirt['Low'] | type_dirt['Medium'], wash_time['medium'])
    rule7 = ctrl.Rule(degree_dirt['High'] | type_dirt['NonFat'], wash_time['medium'])
    rule8 = ctrl.Rule(degree_dirt['Medium'] | type_dirt['NonFat'], wash_time['short'])
    rule9 = ctrl.Rule(degree_dirt['Low'] | type_dirt['NonFat'], wash_time['very_short'])
```

## Wynik 
Gdy dane wyjściowe obliczone zostaną obliczone, możemy je zwizualizować na wykresie proces prania, szacując ile potrzebujemy czasu na pranie w zależności od typu zabrudzenia na ubraniach i skali zabrudzenia. 
