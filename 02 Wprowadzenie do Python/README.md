# Wprowadzenie do języka Python

## Instrukcje warunkowe

Język Python posiada tylko jedną wbudowaną instrukcję warunkową i jest nią instrukcja `if` - `elif` - `else`. Nie znajdziemy tutaj konstrukcji `case` - `switch` znanej z innych języków programowania. Oto najprostsza postać tej instrukcji:

```python
liczba1 = 1
liczba2 = 2
if liczba1 > liczba2:
    print('Pierwsza liczba jest większa')
```

Zobaczmy jak wygląda bardziej rozbudowana jej wersja wraz z obsługą danych wprowadzanych z klawiatury.

```python
liczba = input('Podaj liczbę całkowitą: ')
liczba = int(liczba)

if liczba < 10:
    print('To dość mała liczba')
elif 9 < liczba < 100:  # to jest wersja skrócona warunku
    print('To już całkiem duża liczba')
else:
    print('To musi być wielka liczba')
```

Aby budować bardziej złożone warunki używamy operatorów boolowskich.

```python
if liczba < 10 or liczba > 15:
    print('Liczba nie jest z odpowiedniego przedziału')
    
# możemy również sprawdzić warunek zawierania się elementu w kolekcji
zbior_dopuszczalny = [1, 3, 5, 7,9]
if liczba not in zbior_dopuszczalny:
    print('Podana liczba nie znajduje się w zbiorze')
```

Jak zostało już wspomniane wcześniej Python posiada typ `None`, który odpowiada Null znanemu z innych języków oraz baz danych.

```python
nic = None
pusty_ciag = ''

if not nic:
    print('None to False')
    
if not pusty_ciag:
    print('Pusty ciąg to False')
    
if nic == pusty_ciag:
    print('None i pusty ciąg to boolowskie False, ale nie są sobie równe')
    
# jeżeli chcemy sprawdzić czy ciąg jest pusty
if pusty_ciag == '':
    print('To jest pusty ciąg')
```

Instrukcję if można również znaleźć w wielu skryptach Pythona sprawdzającą dość tajemniczą własność `if __name__ == '__main__'`. Poniżej wyjaśnienie stosownym przykładem.

```python
# Jest również specjalne zastosowanie instrukcji if
# poniższy zapis powoduje, że kod umieszczony wewnątrz tego bloku
# zostanie uruchomiony tylko w przypadku, gdy plik zostanie
# uruchomiony bezpośrednio, tak jak w tym przypadku.
# Jeżeli plik zostanie zaimportowany, to kod nie zostanie uruchomiony
if __name__ == "__main__":
    pass

# możemy też sprawdzić jaką wartość ma zmienna specjalna __name__
print(__name__)

# instrukcja pass nie robi nic, ale jeżeli wymagany jest tutaj kod, żeby
# spełnić wymogi składniowe to możemy jej użyć
```