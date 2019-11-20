# Widoki API

# Ćwiczenia

Celem ćwiczeń będzie stworzenie widoków (endpointów), dzięki którym użytkownik będzie mógł łączyć się z naszym API by pobierac, edytować czy usuwać dane. W tym celu zostanie użyte `djangorestframework`.

1. Odpal swoje środowisko `virtualenv`, w którym już masz zainstalowane `django`.
2. Za pomocą `pip` doinstaluj `djangorestframework`, jeżeli jeszcze tego nie zrobiłeś,
3. Dodaj `'rest_framework'` do zainstalowanych aplikacji w swoim projekcie Django,
4. Dodaj widoki drf do `urlpatterns` swojego projektu:
   ```
   url(r'^api-auth/', include('rest_framework.urls'))
   ```
5. Stwórz widoki dla swoich modeli na podstawie [dokumentacji](https://www.django-rest-framework.org/tutorial/3-class-based-views/). A następnie dodaj je do `urlpatterns` by wyświetliły się w liście dostępnych endpointów API.
   - Zwróć uwagę, które modele powinny mieć możliwość dodawania, usuwania czy edytowania informacji. Może niektóre powinny tylko wyświetlać dane?
   - Pamiętaj by zastosować serializery z poprzednich zajęć.