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
if __name__ == '__main__':
    pass

# możemy też sprawdzić jaką wartość ma zmienna specjalna __name__
print(__name__)

# instrukcja pass nie robi nic, ale jeżeli wymagany jest tutaj kod, żeby
# spełnić wymogi składniowe to możemy jej użyć
```

## Pętle

W Pythonie mamy do dyspozycji dwie pętle: `for` oraz `while` przy  czym  ta  pierwsza  jest  zdecydowanie bardziej „popularna” wśród  programistów  Pythona. Przykład  zastosowania  pętli  `for`  znalazł  się  już  wcześniej gdzie opisywana była funkcja `range`. Dla przypomnienia w poniższych przykładach również pojawi się jej zastosowanie.

```python
# for z funkcją range
for i in range(3):
    print(i)

# for dla listy
lista = [4, 5, 6]
for i in lista:
    print(i)

# a gdybyśmy chcieli zwracać również index elementów listy?
for index, wartosc in enumerate(lista):
    print(str(index) + ' -> ' + str(wartosc))
    
# a mozna jeszcze tak, gdyż funkcja enumerate wypakowuje każdy element listy
# w postaci krotki (index, wartość_z_tablicy)

for krotka in enumerate(lista):
    print(str(krotka[0]) + ' -> '+ str(krotka[1]))
    print(type(krotka[0]))
    print(type(krotka[1]))
    print(type(krotka))
    
# pętla for i słowniki
# jeżeli nie wskażemy pętli for czy chcemy iterować po kluczach 
# czy wartościach to domyślnie zostaną wybrane klucze
slownik = {
    'imie': 'Marek',
    'nazwisko': 'Kowalski',
    'plec': 'mezczyzna'
}

for key in slownik:
    print(key)
    
for val in slownik.values():
    print(val)
    
for key, value in slownik.items():
    print(key + ' -> ' + value)
    
for key in slownik:
    print(key + ' -> ' + slownik[key])
```

Postać Pythonowej pętli while nie różni się od jej sposobu działania w innych językach.

```python
#pętla while
counter = 0
while True:
    counter += 1
    if counter > 10:
        break

counter = 0
while counter < 5:
    print(str(counter) + ' mniejsze od 5')
    counter += 1
    
# pętla while nadaje się dobrze w sytuacji kiedy nie wiemy kiedy (nie
# znamy liczby iteracji) się ona zakończy, np. przy pobieraniu danych
# wejściowych w oczekiwaniu na podanie komendy równej warunkowi stopu pętli

lista = []
print('Podaj liczby całkowite, które chcesz umieścić w pętli.')
print('Wpisz 'stop' aby zakończyć')
while True:
    wejscie = input()
    if wejscie == 'stop':
        break
    lista.append(int(wejscie))
    
print('Twoja lista -> ' + repr(lista))
```

W tym miejscu należy wspomnieć o instrukcji `break` oraz `continue`, które możemy umieszczać wewnątrz pętli. `break` powoduje zakończenie pętli (tylko tej, w bloku której znalazła się instrukcja) natomiast `continue` kończy przebieg aktualnej iteracji pętli (czyli to co jest za `continue` się nie wykona) i rozpoczyna kolejną iterację.

## Python Comprehensions

Tytuł  podrozdziału  postanowiłem  pozostawić  w  języku  angielskim,  gdyż  nie  ma  chyba  dobrego tłumaczenia  tego  terminu  na  język  polski  w  odniesieniu  do  programowania.  Mechanizm  ten  polega  na generowaniu kolekcji (lista, słownik, zbiór) na podstawie jednowierszowego zapisu określającego warunki dla zmiennych, które zostaną w danej kolekcji umieszczone. Najlepiej można to oddać za pomocą odpowiednich przykładów.

```python
# comprehensions dla list
x = [i for i in range(5)]
print(x)

y = [i for i in range(10) if i % 2 == 0]
print(y)

# możemy wykonać funkcję dla każdej wartości
literoliczby = ['1', '2', '3', '4', '5']
liczby = [int(i) for i in literoliczby]
print(liczby)

# te instrukcje można również zagnieżdżać, np. dla listy list
# przykład z dokumentacji Pythona
vec_of_vec = [[1,2, 3], [4, 5, 6], [7, 8, 9]]
single = [num for elem in vec_of_vec for num in elem]
print(single)

# comprehensions i słowniki
# odwrócenie kolejności par klucz:wartość w słowniku
slownik = {1: 'Burek', 2: 'Azor', 3: 'Fafik'}
print({value: key for key, value in slownik.items()})

# comprehensions i zbiory
# zwróć uwagę na nawiast klamrowy jak dla słowników
lista = [1, 2, 2, 3, 4, 4, 4, 5]
zbior = {i for i in lista}
print(zbior)
```

Mechanizm przedstawiony w tym podrozdziale jest bardzo przydatny, chociaż skomplikowane polecenia mogą być wyzwaniem do zinterpretowania względem „tradycyjnego” podejścia. Więcej przykładów można znaleźć w dokumentacji Pythona pod adresem https://docs.python.org/3/tutorial/datastructures.html.

## Definiowanie funkcji

Ogólna definicja funkcji mówi, że jest to wydzielony blok kodu, który ma robić możliwie jak najmniej rzeczy na raz, ale ma to robić dobrze. Jest to też niezbędny element metodologii DRY (Don’t Repeat Yourself), czyli  tam  gdzie  jakaś  funkcjonalność  będzie  wykorzystywana  wielokrotnie  możemy  zastosować  funkcję. Przykładowa deklaracja funkcji w języku Python poniżej.

```python
def zainicjalizuj():
    print('inicjalizacja...')
```

Słowo kluczowe def informuje interpreter o tym, że jest to deklaracja funkcji. Funkcja ma swoją nazwę oraz zero lub więcej argumentów. Funkcja może wykonywać jakieś operacje i zmieniać stan obiektów nie zwracając nic na wyjściu (w Javie używamy jako typu zwracanego void) lub może zwracać jakieś wartości. W odróżnieniu od niektórych języków programowania sygnatura funkcji nie mówi nam jakiej wartości możemy się spodziewać.

```python
def powiel(tekst, ile_razy):
    return (tekst + ' ') * ile_razy
    
print(powiel('jesień', 5)
```

Należy również pamiętać o tym, że w przypadku gdy deklaracja i wywołanie funkcji odbywają się w tym samym pliku to wywołanie funkcji musi znaleźć się po jej deklaracji. Podobnie jak np. w języku PHP argumenty funkcji mogą mieć swoje wartości domyślne i zostaną użyte w przypadku gdy programista nie przekażeich wartości.

```python
def powiel(tekst='Hello ', ile_razy=3):
    return (tekst + ' ') * ile_razy
    
print(powiel())
```

W przypadku, gdy funkcja zawiera argumenty opcjonalne w celu uniknięcia konieczności pilnowania kolejności przekazywanych argumentów możemy przekazać wartości argumentów wraz z ich nazwami.

```python
print(powiel(ile_razy=5, tekst='Jingle bells'))
```

Funkcje w Pythonie mogą przyjmować właściwie nieograniczoną liczbę argumentów lub argumentów z kluczem (te, których nazwę określamy). Zgodnie z przyjętą konwencją zmienna przechowująca te pierwsze to `*args`, a zmienna dla argumentów z kluczem to `**kwargs`, ale ich nazwy w naszych funkcjach mogą być dowolne.

```python
def robie_duzo_rzeczy(*args, **kwargs):
    print(args)
    print(kwargs)
    
robie_duzo_rzeczy(
    3, 4, 5.6,
    imie='Krzysztof',
    hobby=['sport', 'fantasy']
)
```

Zasięg zmiennych oraz zmienne globalne. Zmienne zadeklarowane wewnątrz funkcji mają zasięg tylko wewnątrz tej funkcji, co oznacza, że próba odwołania się do nich poza funkcją nie powiedzie się. Istnieje jednak możliwość  zdefiniowania  takiej  zmiennej jako  zmienna  globalna.  Mimo,  że  jest  to  częścią  języka  to wykorzystywanie tego mechanizmu nie jest zalecane, a często wręcz piętnowane przez innych programistów.

```python
def mam_globala():
    global a
    a = 1
    b = 2
    return a + b
    
def nie_mam_globala():
    c = 3
    return a + c
    
print(mam_globala())
print(nie_mam_globala())
```

## Pakiety i moduły

W środowisku Python moduł to po prostu pojedynczy plik z kodem Pythona, który możemy stworzyć i zapisać. Pakiet to zbiór takich modułówa najczęściej oznacza folder, w którym znajdują się pliki (moduły). Oba te elementy można importować na różne sposoby, kilka przykładów znalazło się w rozdziale poświęconym formatowaniu kodu wg. PEP8.

Zawartość modułu może być zbiorem funkcji lub klas i metod. Taki moduł możemy następnie po zaimportowaniu  wykorzystywać  w  innych  naszych  programach,  modułach  lub  pakietach. Poniżej  prosty przykład modułu i jego wykorzystania w innym skrypcie.

```python
# plik matma.py
'''deklaracja funkcji w prostym module'''


def dodaj(a, b):
    return a + b
    
    
def odejmij(a, b):
    return a - b


def podziel(a, b):
    return a / b


def pomnoz(a, b):
    return a * b
```

Teraz możemy z poziomu innego pliku w tym samym folderze zaimportować ten moduł.

```python
import matma

print(matma.dodaj(1, 2))
print(dir(mojpakiet))
print(dir(mojpakiet.matma))
```

Moduły najczęściej importują inne moduły a te importują kolejne. Jeżeli w trakcie tego procesu zostanie napotkany zduplikowany import to zostanie on zignorowany. Polecenie `dir(modul|pakiet)` wyświetla wszystkie zmienne oraz nazwy modułów, które się w nich znajdują.

Aby stworzyć pakiet trzeba jeszcze dodać specjalny plik do folderu (pakietu) o nazwie `__init__.py`. Jeżeli korzystamy z zalecanego sposobu importu modułów czyli `import pakiet.moduł` to możemy jego zawartość pozostawić pustą chociaż może się tam również znajdować kod inicjalizujący dla pakietu. Natomiast jeżeli chcemy umożliwić import z tego pakietu za pomocą `from pakiet import *` to  plik  `__init__.py` powinien zawierać zmienną `__all__` zawierającą listę modułów, które będą zaimportowane:

```python
__all__ = ['matma', 'jingle']
```

Reasumując, został utworzony folder `mojpakiet` a w nim znajduje się plik `matma.py` przedstawiony na listingu w tym rozdziale. Zawartość pliku `__init__.py` przedstawiłem na poprzednim listingu. Została tylko zawartość pliku `jingle.py`:

```python
__all__ = ['sing']


def sing():
    return 'Jingle bells, jingle bells...'

def snow():
    return 'It's snowing...'
```

Plik, który wykonuje same importyna tym pakiecie znajduje się w tym samym folderze co pakiet. A jego zawartość to:

```python
from mojpakiet import *

print(matma.dodaj(1, 2))
print(jingle.sing())
```

Zmienna `__all__` służy również do określanialisty funkcji w module. Zmienna jest wtedy umieszczana w pliku z definicją klas/funkcji a jej postać jest taka sama jak w przypadku pakietu z taką różnicą, że po zaimportowaniu takiego modułu (pliku) wszystkie jego funkcje i tak będą widoczne bez względu na to czy znalazły się w zmiennej `__all__` czy też nie.

Określanie `__all__` w module najczęściej wykorzystywanejest po to, aby mieć dostęp do listy klas, metod danego modułu np. po to, aby sprawdzić jakie funkcje możemy wywołać. Bardzo  dobrze  wytłumaczone  jest  to  w  artykule  pod  adresem http://xion.io/post/code/python-all-wild-imports.html.

Struktura pakietów i modułów może być bardziej rozbudowana i rozmieszczona na kolejnych poziomach zagnieżdżenia. Więcej informacji można znaleźć pod adresem https://docs.python.org/3/tutorial/modules.htmlPodsumowując. Zalecanym sposobem wykonywania importów jest `from pakiet import moduł` lub `import moduł`. Jako ciekawostkę polecam umieszczenie polecenia `import this` w swoim pliku lub wykonanie w konsoli.

## Zarządzanie pakietami oraz `virtualenv`

