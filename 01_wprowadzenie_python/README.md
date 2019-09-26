# Wprowadzenie do języka Python

## Historia Python

Twórcą Pythona jest holender Guido van Rossum a sama nazwa, co niektórych zapewne nie dziwi, pochodzi od popularnego serialu BBC „Latający Cyrk Monty Pythona”. Prace nad pierwszym interpreterem Pythona rozpoczęły się w 1989 roku jako następca języka ABC. Wszystkie wersje aż do 1.2 powstawały w CWI (Centrum  Matematyki  i  Informatyki)  w  Amsterdamie gdzie Guido wówczas pracował. Od wersji 2.1Python był udostępniany jako projekt Open Source przez niedochodową organizację Python Software Foundation (PSF). Obecnie nad rozwojem Pythona pracuje wiele osób, ale Guido wciąż jest zaangażowany w ten proces.  Sam twórca w 1995 roku wyemigrował do USA gdzie w latach 2005 –2013 pracował dla Google a obecnie pracuje dla firmy Dropbox.

Ważnym momentem w historii Pythona było utworzenie drugiej głównej gałęzi –Pythona  3  w  roku 2008.  Od  tego  momentu  wersja  2oraz 3 były rozwijane oddzielnie, ale czas wersji 2 zaczyna mijać o czym świadczy ogłoszony już termin zakończenia wsparcia na 12 kwietnia 2020 roku. Rozwój języka jest prowadzony przy wykorzystaniu PEP (Python Enhancement Proposal). Dokumenty te to propozycje rozszerzeń lub zmian w języku w postaci artykułu, który jest poddawany pod dyskusję wśród programistów Pythona. Każdy dokument zawiera  opis  proponowanego  rozwiązania, uzasadnienie  oraz  aktualny  status.  Po osiągnięciu  konsensusu propozycje są przyjmowane lub odrzucane.

## Wybrane cechy języka Python

Python jest językiem ogólnego przeznaczenia, którego ideą przewodnią jest czytelność i klarowność kodu źródłowego. Standardowa implementacja języka jest CPython (napisany w C), ale istnieją też inne, np. Jython (napisany w Javie), CLPython napisany w Common Lisp, IronPython (na platformę .NET) i PyPy napisany w Pythonie. Python nie wymusza jednego stylu programowania dając możliwość programowania obiektowego, programowania strukturalnego oraz programowania funkcyjnego.

**Inne cechy języka Python:**

- Typy sprawdzane są dynamicznie (w przeciwieństwie np. do Javy),
- Do zarządzania pamięcią używany jest garbage collector,
- Wszystkie wartości przekazywane są przez referencję,
- Jest czasem kwalifikowany jako język skryptowy,
- Nie ma enkapsulacji, jak to ma miejsce w C++ czy Javie, ale istnieją mechanizmy, które pozwalają na osiągnięcie podobnego efektu,
- Możliwe jest tworzenie funkcji ze zmienną liczbą argumentów,
- Możliwe jest tworzenie funkcji z argumentami o wartościach domyślnych.

## PyCharm Community Edition

W trakcie zajęć prezentacja przykładów kodu oraz ćwiczenia będą wykonywane z wykorzystaniem środowiska  PyCharm Community, którejest darmową wersją tego narzędzia. Wersja Community pozbawiona jest wielu udogodnień, które mogą przydaćsięna dalszym etapie pracy z językiem Python np. w trakcie wytwarzania  aplikacji  webowych  z  wykorzystaniem  m.in.  Django,  Flask,  JavaScript oraz  wielu  innych.  Mamy natomiast do dyspozycji „inteligentny” edytor, graficzny debugger, inspekcję kodu, wsparcie dla systemów kontroli wersji oraz pakiet narzędzi naukowych.

- [Bardziej szczegółowe porównanie Community vs Professional](https://www.jetbrains.com/pycharm/features/editions_comparison_matrix.html)

Firma  JetBrains,  która  jest  autorem  m.in.  oprogramowania  PyCharm  oferuje  pełen  pakiet oprogramowania w wersji Professional za darmo dla studentów oraz nauczycieli. Aby taką licencję uzyskać należy się zarejestrować i aplikować o przyznanie takiej licencji. Jedyne ograniczenie to wykorzystywanie tego oprogramowania do celów komercyjnych. 

- [Informacje o Professional dla studentów](https://www.jetbrains.com/student/)

## Organizacja kodu według PEP8

Jak zostało już wspomniane, w specyfikacji języka odbywają się poprzez system PEP. Dokument  o  numerze  PEP8  jest  jedną (ale nie jedyną) propozycją organizacji kodu języka Python. 

- [Oryginalna treść dokumentu PEP8](https://www.python.org/dev/peps/pep-0008/)

W dalszej części zajęć będziemy korzystać z `flake8`, aby dbać o jakość naszego kodu.

- [Więcej informacji o `flake8`](https://gitlab.com/pycqa/flake8)

### Wcięcia

 W kodzie języka Python nie znajdziemy znanych z PHP, Javy czy C# klamerek do separacji bloków kodu, określania ram ciała metody czy klasy lub zakresu operacji w pętli. Tutaj do tego celu służą odpowiednio ustawione wcięcia i puste linie między w/w elementami. Dla osób, które nigdy wcześniej nie miały do czynienia z taką organizacją kodu może to być zaskakujące, ale dość szybko staje się zrozumiałe i intuicyjne.

 ```python
 if score >= 100:
    print('Zwycięstwo !')
 ```

 Każdy  kolejny  poziom  zagnieżdżenia  w  bloku  kodu  poprzedza  odstęp  w  postaci wielokrotności  4  spacji (pojedyncza wartość wcięcia). Dopuszczalne jest również stosowanie tabulatorów jako wcięć, ale zalecane są spacje a dodatkowo w wersji Python 3 użycie jednocześnie spacji i tabulatorów jako wcięć nie jest dozwolone.

 Wcięcia używamy również w sytuacjach, w których linia kodu jest zbyt długa i musi być złamana na większą ilość wierszy. Zalecana długość linii według PEP8 to 79 znaków

 ```python
 wyslane = wyslij_wiadomosc(
     e_mail_odbiorcy, temat, wiadomosc,
)
 ```

 Deklaracja zmiennych takich jak lista, tablica, krotka czy słownik dzięki wcięciom często poprawia ich czytelność co jest główną zasadą, która kierowano się określając reguły formatowania kodu w Pythonie.

 ```python
 lista = [
     1, 2, 3,
     4, 5, 6,
 ]
 ```

 W przypadku łamania linii i operatorów np.. arytmetycznych obowiązuje zasada przenoszenia operatora do nowej linii.

```python
 zysk = (
     przychod
     - koszty
     - podatki
 )
 ```

 ### Puste linie

 Funkcje najwyższego rzędu oraz definicje klas oddzielamy od pozostałych bloków kodu dwiema pustymi liniami.

 ```python
 def zrob_cos():
    return 'zrobione'


def tez_cos_zrob():
    return 'też zrobione'
 ```

 Metody klas oraz funkcje lokalne oddzielone są natomiast pojedynczą pustą linią.

 ```python
 class Osoba:
    def __init__(self, imie, nazwisko, plec):
        self.imie = imie
        self.nazwisko = nazwisko
        self.plec = plec
        
    def przedstaw_sie(self):
        print(f'Nazywam się {self.imie} {self.nazwisko}')

    def moja_plec(self):
        print(f'Moja płeć to {self.plec}')
        

os = Osoba('Krzysztof', 'Ropiak', 'mężczyzna')
os.przedstaw_sie()
os.moja_plec()
 ```

Pojedyncze puste linie mogą być również stosowane wewnątrz funkcji aby odseparować od siebie logiczne sekcje funkcji.

 ```python
 def funkcja_top_level():
    
    def funkcja_lokalna():
        pass
    
    def kolejna_funkcja_lokalna():
        pass
 ```

 ### Import modułów

 Poszczególne instrukcje importu powinny być rozdzielone na oddzielne linie.

 ```python
 # Tak poprawnie importujemy moduły:
 import os
 import sys

 # Tak nie robimy:
 import os, sys
 ```

 Poprawny jest natomiast taki sposób definiowania importu:

 ```python
 from subprocess import Popen, PIPE
 ```

W momencie gdy importów z jednego modułu jest dużo warto zastąpić to w ten sposób:

```python
from rest_framework.mixins import (
    ListModelMixin,
    CreateModelMixin,
    RetrieveModelMixin,
)
```

Importy  powinny  być  umieszczane  na  początku  pliku  tuż  za  ewentualnymi  komentarzami  dla  modułu  i elementami docstring. Kolejnośc importów ma również znaczenie. Oto zalecany porządek:

- import bibliotek standardowych
- import powiązanych bibliotek zewnętrznych (ang. third party imports)
- import lokalnych aplikacji/bibliotek

Zalecane jest również dodawanie pustej linii po każdej z w/w grup importów. Jako, że Python umożliwia zarówno import całej biblioteki lub tylko wybranych jej modułów często trzeba dobrać odpowiedni sposób do sytuacji,  ale  z  reguły  zaleca  się  wykonywanie  importu  i  dodanie  aliasu  lub  import  modułu  zamiast  np. konkretnej klasy z tego modułu co zmniejsza ryzyko wystąpienia konfliktów w przestrzeninazw. Więcej informacji oraz przykłady znajdują się w rozdziale poświęconym zarządzaniu i importowi pakietów.

### Inne zalecenia

Zmienne typu string można umieszczać zarówno w cudzysłowie lub w apostrofach, gdyż w przypadku Pythona nie ma to znaczenia. Natomiast PEP8 nie zaleca żonglowania tym zapisem i trzymania się jednej z opcji. Sytuacją, w której dozwolone jest użycie obu jednocześnie jest ciąg tekstowy, który sam już zawiera cudzysłów lub apostrof – tedy należy użyć drugiego z nich. Każdy z następujących wpisów jest poprawny:

```python
artykul = 'Recenzja "Władcy Pierścieni".'
artykul = "Recenzja \"Władcy Pierścieni\"."
artykul = """Recenzja "Władcy Pierścieni"."""
```

Spacje w wyrażeniach i definicjach są pożądane, ale nie należy ich nadużywać.

```python
# Dobry zapis:
zakupy(szynka[1], {jajka: 2})
x = 1
lista[index]
lista[1:4]

# Tak nie robimy:
zakupy( szynka[ 1 ], { jajka: 2 } )
x=1
lista [index]
lista[1: 4]
```

Wszystkie operatory binarne powinny być otoczone pojedynczą spacją.

# Ćwiczenia

Zasad, które opisane są w dokumencie PEP8 jest więcej, ale nie wszystkie będą tutaj przytoczone. Poświęć ok. 15 minut na zapoznanie się z dokumentem PEP8 (link na początku rozdziału) i przejrzyj pokazane tam  przykładowe  fragmenty  kodu.  Zwróć  uwagę  na  informacje  w  sekcji  „Comments”  oraz  „Naming Conventions”.

Na sam koniec warto dodać, że edytor środowiska PyCharm posiada zaimplementowany mechanizm formatowania kodu wg. PEP8 więc nawet jak złamiemy zasadę wcięć, odstępów lub inną, zostaniemy o tym fakcie  poinformowanico umożliwi dokonanie poprawek  lub  skorzystanie  z  automatycznego  formatowania. Czasem jednak automatyczne formatowanie potrafi się pogubić...