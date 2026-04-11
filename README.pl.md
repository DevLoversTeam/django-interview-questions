**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  Django <img src="./assets/django.svg" width="40" height="40" alt="Django logo"/>
</h1>

<h2>Najpopularniejsze pytania i odpowiedzi na rozmowie o pracę z Django</h2>

<details>
<summary>1. Czym jest Django i jakie są jego kluczowe możliwości?</summary>

#### Django

Django to wysokopoziomowy framework Pythona do tworzenia aplikacji webowych,
który działa zgodnie z zasadą „batteries included”: większość typowych zadań
jest już gotowa w ekosystemie frameworka.

#### Kluczowe możliwości Django:

1. **Szybki start developmentu:** generowanie projektu i aplikacji,
   gotowa struktura oraz czytelne konwencje.
2. **Wbudowany panel administracyjny:** automatycznie tworzony Django Admin do
   zarządzania danymi przez przeglądarkę.
3. **Mocny ORM:** praca z bazą danych przez modele Pythona bez ręcznego SQL
   w większości przypadków.
4. **System migracji:** kontrola i wersjonowanie zmian schematu bazy danych.
5. **Routing URL i warstwa view:** wyraźny podział routingu, logiki biznesowej
   i prezentacji.
6. **Silnik szablonów:** wbudowane templates do renderowania HTML
   z obsługą dziedziczenia szablonów.
7. **Bezpieczeństwo domyślnie:** ochrona przed CSRF, XSS, SQL injection,
   clickjackingiem oraz bezpieczne praktyki uwierzytelniania.
8. **Wbudowane uwierzytelnianie:** użytkownicy, grupy, uprawnienia, sesje.
9. **Obsługa formularzy:** Django Forms/ModelForms z walidacją po stronie serwera.
10. **Skalowalność i ekosystem:** cache, middleware, sygnały,
    integracja z Celery, DRF, Redis, PostgreSQL itd.

#### Kiedy Django jest szczególnie trafnym wyborem:

- CRM/ERP i wewnętrzne systemy biznesowe.
- Platformy contentowe, marketplace’y, panele użytkownika.
- API + część webowa w jednym projekcie.
- Produkty, gdzie liczą się szybkość wdrożenia, bezpieczeństwo i utrzymywalność kodu.

#### Krótki przykład „co Django daje od razu”:

```bash
django-admin startproject config .
python manage.py startapp users
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Po tym masz już bazowy szkielet projektu, podłączoną bazę danych, system
migracji i dostęp do panelu admina.

#### Wniosek:

Django to praktyczny wybór do szybkiego i bezpiecznego backend developmentu,
zwłaszcza gdy potrzebujesz dojrzałej architektury, stabilnego stacku i szybkiego
startu produktu.

</details>

<details>
<summary>2. Jakie są zalety używania Django?</summary>

#### Django

Django często wybiera się do komercyjnego developmentu, gdy potrzebne są szybki
time-to-market, stabilna architektura i bezpieczny backend bez „sklejania”
dziesiątek bibliotek zewnętrznych.

#### Kluczowe zalety Django:

1. **Wysoka szybkość developmentu:** wiele typowych rzeczy jest już gotowych
   (auth, admin, forms, ORM, sessions, cache).
2. **Bezpieczeństwo „out of the box”:** wbudowane mechanizmy przeciw CSRF, XSS,
   SQL injection, clickjackingowi i bezpieczna obsługa haseł.
3. **Czytelna struktura projektu:** zrozumiałe konwencje upraszczają onboarding
   zespołu i utrzymanie kodu długoterminowo.
4. **Mocny ORM i migracje:** szybka praca z bazą, kontrola ewolucji schematu,
   dobra obsługa PostgreSQL i innych relacyjnych baz danych.
5. **Admin panel dla biznesu:** Django Admin szybko daje zespołom operacyjnym
   działający interfejs bez osobnego frontend developmentu.
6. **Dobra skalowalność architektury:** aplikacje, middleware, signals,
   celery, cache i kolejki łatwo integrować w scenariuszach produkcyjnych.
7. **Dojrzały ekosystem:** DRF, django-allauth, django-filter,
   django-celery-beat i inne sprawdzone narzędzia.
8. **Przydatność w projektach enterprise:** przewidywalne release’y,
   duża społeczność, dobra dokumentacja i stabilne praktyki.

#### Praktyczna wartość dla zespołu:

- Mniej kodu infrastrukturalnego na starcie.
- Mniej ryzyka podstawowych błędów bezpieczeństwa.
- Szybszy start MVP i bardziej przewidywalna ścieżka skalowania.
- Lepsza utrzymywalność wraz ze wzrostem zespołu i kodu.

#### Kiedy zalety Django są najbardziej widoczne:

- B2B SaaS, CRM/ERP, panele użytkownika, marketplace’y.
- Projekty z dużą ilością logiki biznesowej i ról dostępu.
- Zespoły, dla których ważna jest stabilność i przewidywalny rozwój produktu.

#### Wniosek:

Siła Django polega na szybkim dowożeniu wartości biznesowej bez kompromisów
w bezpieczeństwie i utrzymywalności kodu.

</details>

<details>
<summary>3. Jaka jest różnica między architekturą MVC a MVT?</summary>

#### Django

W Django częściej mówi się o **MVT (Model-View-Template)**, podczas gdy
w wielu innych frameworkach używa się terminu **MVC (Model-View-Controller)**.
Koncepcyjnie te podejścia są bardzo podobne, a różnica dotyczy głównie ról i nazw.

#### MVC (klasycznie):

1. **Model** - praca z danymi i logiką biznesową.
2. **View** - prezentacja danych (UI / warstwa prezentacji).
3. **Controller** - obsługa wejściowego requestu, sterowanie przepływem
   między Model i View.

#### MVT w Django:

1. **Model** - modele danych i dostęp do bazy przez ORM.
2. **View** - obsługa HTTP requestu, wykonanie logiki biznesowej,
   przygotowanie odpowiedzi.
3. **Template** - warstwa prezentacji (HTML + template syntax).

#### Jak mapują się MVC i MVT:

- `Model (MVC)` ≈ `Model (Django MVT)`
- `View (MVC)` ≈ `Template (Django MVT)`
- `Controller (MVC)` ≈ `View + URL dispatcher (Django MVT)`

Czyli w Django rola „kontrolera” jest podzielona między `urls.py`
(routing) i `views.py` (obsługa requestu).

#### Prosty przepływ w Django (MVT):

1. Request trafia na URL, np. `/articles/`.
2. `urls.py` kieruje go do odpowiedniego `view`.
3. `view` pobiera dane z `Model`.
4. `view` przekazuje dane do `Template`.
5. `Template` renderuje HTML i zwracany jest `HttpResponse`.

#### Wniosek:

- Django nie „łamie” MVC, tylko realizuje je we własnym wariancie MVT.
- Kluczowa różnica praktyczna: w Django `view` to logika obsługi requestu,
  a prezentacja znajduje się w `template`.

</details>

<details>
<summary>4. Dlaczego Django nazywa się frameworkiem loosely coupled?</summary>

#### Django

Django określa się jako **loosely coupled** (luźno powiązany), ponieważ jego
komponenty można zmieniać, rozszerzać lub podmieniać niezależnie od siebie,
bez przepisywania całej aplikacji.

#### Co to oznacza w praktyce:

1. **Komponenty mają rozdzielone odpowiedzialności:** URL routing, view,
   szablony, modele, formularze, middleware współpracują, ale nie są „zlane”
   w jedną warstwę.
2. **Pluginowa architektura aplikacji:** projekt składa się z `apps`, które
   można włączać/wyłączać przez `INSTALLED_APPS`.
3. **Możliwość podmiany części systemu:** np. silnika szablonów, modelu użytkownika,
   backendu cache, email backendu, storage backendu.
4. **Konfiguracja przez settings:** zachowanie systemu kontrolują ustawienia,
   a nie sztywno zakodowana logika.
5. **Rozszerzanie przez middleware i signals:** można dodawać funkcjonalność
   bez modyfikacji rdzenia logiki biznesowej.

#### Typowe przykłady podejścia loosely coupled w Django:

- Zamiana SQLite na PostgreSQL tylko przez konfigurację `DATABASES`.
- Dodanie Redis cache bez przepisywania view i modeli.
- Przejście z lokalnego storage na S3-compatible storage przez backend.
- Wyniesienie auth do custom modelu użytkownika (`AUTH_USER_MODEL`) bez łamania
  architektury całego projektu.

#### Dlaczego to ważne dla zespołu:

- Łatwiej skalować produkt modułami.
- Łatwiej testować poszczególne części systemu.
- Mniejsze ryzyko przy refaktoryzacji.
- Prostsze utrzymanie kodu w długim cyklu życia projektu.

#### Wniosek:

Loosely coupled w Django oznacza elastyczność inżynierską: możesz rozwijać
projekt stopniowo, zmieniając konkretne podsystemy, a nie przebudowując
wszystkiego naraz.

</details>

<details>
<summary>5. Jaka jest różnica między Django a FastAPI?</summary>

#### Django

Django i FastAPI rozwiązują różne problemy. Oba frameworki są mocne, ale
wybiera się je do różnych typów produktów i zespołów.

#### Kluczowa różnica:

- **Django** - pełnofunkcyjny framework webowy „z pudełka” (ORM, admin, auth,
  templates, forms, sessions, middleware).
- **FastAPI** - lekki i bardzo szybki framework ASGI, nastawiony głównie na
  budowę API z typowaniem i automatyczną dokumentacją.

#### Porównanie Django vs FastAPI:

1. **Przeznaczenie**

- Django: kompletne systemy webowe i API w jednym projekcie.
- FastAPI: API-first, mikroserwisy, usługi high-concurrency.

2. **Szybkość startu projektu**

- Django: bardzo szybko dla CRUD/admin/paneli użytkownika.
- FastAPI: szybko dla API, ale więcej decyzji trzeba złożyć samodzielnie.

3. **Wydajność**

- Django: wystarczająca dla większości scenariuszy biznesowych; klasycznie WSGI,
  ale z obsługą trybu ASGI.
- FastAPI: zwykle wyższa wydajność przy obciążeniu I/O dzięki podejściu async-first.

4. **ORM i praca z bazą danych**

- Django: dojrzały wbudowany ORM + migracje.
- FastAPI: ORM nie jest wbudowany; zwykle SQLAlchemy/SQLModel/Tortoise.

5. **Panel administracyjny i back-office**

- Django: mocny Django Admin „z pudełka”.
- FastAPI: panel admin trzeba zbudować lub zintegrować osobno.

6. **Walidacja i schematy**

- Django: forms/DRF serializers.
- FastAPI: modele Pydantic jako standard de facto.

7. **Dokumentacja API**

- Django: zwykle przez DRF + pakiety Swagger/OpenAPI.
- FastAPI: OpenAPI/Swagger UI generowane automatycznie.

8. **Ekosystem**

- Django: bardzo szeroki dla produktów webowych (CMS, auth, wzorce admin).
- FastAPI: silny w API/mikroserwisach, nowoczesny async stack.

#### Kiedy wybrać Django:

- Potrzebny „all-in-one” backend z szybkim wynikiem biznesowym.
- Jest złożony model ról, panel admina, dużo encji CRUD.
- Zespołowi zależy na stabilnych konwencjach i długofalowej utrzymywalności.

#### Kiedy wybrać FastAPI:

- Potrzebny API-first serwis z wysoką konkurencją requestów.
- Priorytetem są integracje async (zewnętrzne API, kolejki, streaming,
  scenariusze websocket).
- Zespół chce maksymalnie lekki i kontrolowalny stack.

#### Wniosek:

- **Django** - optymalne do szybkiego uruchomienia funkcji biznesowych i
  złożonych systemów webowych.
- **FastAPI** - optymalne do wydajnych nowoczesnych API i scenariuszy
  mikroserwisowych.
- W dużych produktach te frameworki często współistnieją: Django jako core/admin,
  FastAPI jako osobne usługi API.

</details>

<details>
<summary>6. Jakie są wady i ograniczenia Django w porównaniu z innymi frameworkami?</summary>

#### Django

Django to mocny framework, ale nie jest uniwersalnie najlepszy dla każdego typu
projektu. Jego ograniczenia zwykle ujawniają się w specyficznych scenariuszach
technicznych.

#### Główne wady i ograniczenia Django:

1. **„Cięższy” start dla bardzo prostych usług**

- Dla małego mikroserwisu Django może być nadmiarowe ze względu na liczbę
  wbudowanych komponentów.

2. **Mniej „native async-first” UX niż FastAPI**

- Django wspiera async, ale historycznie wiele części ekosystemu jest
  zorientowanych na podejście sync.
- Dla wysokoobciążonych API I/O FastAPI/Starlette czasem daje prostszą ścieżkę.

3. **ORM nie jest idealny do bardzo złożonego SQL**

- Django ORM jest mocny dla większości zadań, ale przy bardzo złożonych
  zapytaniach analitycznych lub optymalizacjach specyficznych dla DB i tak
  często trzeba pisać raw SQL.

4. **Sztywne konwencje**

- Konwencje Django są plusem dla zespołu, ale dla inżynierów chcących
  maksymalnie „cienkiej” kontroli mogą być ograniczeniem.

5. **Monolityczny styl domyślnie**

- Django naturalnie prowadzi do modularnego monolitu, a nie drobnych mikroserwisów.
- Dla architektury microservice-first potrzebna jest wyraźna dyscyplina granic.

6. **Dodatkowe kroki dla nowoczesnego API-first DX**

- Dla pełnego REST API zwykle dodaje się DRF, dla OpenAPI dodatkowe narzędzia,
  a dla realtime osobny stack (np. Channels).

7. **Wydajność „out of the box” nie zawsze jest maksymalna**

- Bez cache, indeksów DB, optymalizacji zapytań ORM i właściwego profilowania
  duże systemy mogą działać wolno.

#### Typowe błędy mylone z „minusami Django”:

- Zapytania N+1 przez niepoprawne użycie ORM.
- Brak strategii cache.
- Słaba dekompozycja modułowa aplikacji.
- Mieszanie logiki biznesowej w view bez warstwy serwisowej.

To częściej problem architektury zespołu, a nie słabość samego frameworka.

#### Kiedy Django może nie być najlepszym wyborem:

- Bardzo lekki serwis API z minimalną logiką biznesową.
- High-throughput async API jako główne wymaganie.
- System, gdzie potrzebna jest maksymalnie custom low-level kontrola bez
  „ciężkiego” framework core.

#### Wniosek:

Ograniczenia Django są realne, ale przewidywalne. Dla większości aplikacji
biznesowych jego zalety (szybkość developmentu, bezpieczeństwo,
utrzymywalność) przeważają. Kluczowe jest dobieranie frameworka do kontekstu,
a nie „pod trend”.

</details>

<details>
<summary>7. Jak działa Django (cykl życia request–response)?</summary>

#### Django

Cykl życia w Django to sekwencja kroków od momentu, gdy HTTP request trafia
na serwer, aż do wygenerowania finalnej HTTP response dla klienta.

#### Sekwencja obsługi requestu:

1. **Klient wysyła HTTP request**

- Przeglądarka lub klient API odwołuje się do aplikacji Django.

2. **Serwer WSGI/ASGI przekazuje request do Django**

- Np. Gunicorn/Uvicorn + Nginx.

3. **Request przechodzi przez middleware (request phase)**

- Middleware może modyfikować/wzbogacać request: auth, sesje, locale,
  kontrole bezpieczeństwa itd.

4. **URL resolver szuka pasującej trasy**

- Django mapuje URL na reguły w `urls.py`.
- Jeśli trasa nie istnieje -> `404 Not Found`.

5. **Wywoływany jest view**

- View otrzymuje `request`, wykonuje logikę biznesową: odczyt/zapis danych,
  kontrola dostępu, przygotowanie kontekstu.

6. **Praca z modelami i DB (w razie potrzeby)**

- Przez ORM (`Model.objects...`) albo raw SQL dla trudniejszych przypadków.

7. **Budowanie odpowiedzi**

- HTML przez `render(...)` + template,
- albo JSON przez `JsonResponse`,
- albo redirect / file response.

8. **Response przechodzi przez middleware (response phase)**

- Middleware może dodać nagłówki, cookies, cache-control, logowanie.

9. **Odpowiedź wraca do klienta**

- Przeglądarka renderuje stronę albo klient przetwarza odpowiedź API.

#### Co dzieje się przy błędach:

- `Http404` lub brak trasy -> strona 404.
- Nieobsłużone wyjątki -> strona 500.
- Obsługa wyjątków również przechodzi przez łańcuch middleware.

#### Skrócony łańcuch:

`Client -> Server (WSGI/ASGI) -> Middleware (request) -> URLconf -> View -> Model/ORM -> Template/Serializer -> Middleware (response) -> Client`

#### Wniosek:

Siła Django leży w przewidywalnym request/response pipeline: łatwo debugować,
testować i skalować, bo każdy etap ma jasną odpowiedzialność.

</details>

<details>
<summary>8. Jak utworzyć nowy projekt Django?</summary>

#### Django

Nowy projekt Django tworzy się w kilku standardowych krokach: przygotowanie
środowiska, instalacja Django, wygenerowanie projektu, migracje i uruchomienie
serwera.

#### Krok po kroku:

1. **Utwórz katalog projektu**

```bash
mkdir my_django_project
cd my_django_project
```

2. **Utwórz i aktywuj środowisko wirtualne**

```bash
python -m venv .venv
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate         # Windows (PowerShell/CMD)
```

3. **Zainstaluj Django**

```bash
pip install django
```

4. **Wygeneruj projekt**

```bash
django-admin startproject config .
```

Po tym pojawią się kluczowe pliki:

- `manage.py`
- `config/settings.py`
- `config/urls.py`
- `config/asgi.py`
- `config/wsgi.py`

5. **Wykonaj początkowe migracje**

```bash
python manage.py migrate
```

6. **Utwórz administratora**

```bash
python manage.py createsuperuser
```

7. **Uruchom dev-serwer**

```bash
python manage.py runserver
```

#### Weryfikacja:

- Otwórz `http://127.0.0.1:8000/` - strona startowa Django.
- Otwórz `http://127.0.0.1:8000/admin/` - panel admina (po `createsuperuser`).

#### Rekomendowany kolejny krok:

Utwórz pierwszą aplikację i dodaj ją do `INSTALLED_APPS`:

```bash
python manage.py startapp core
```

To bazowy i poprawny start dla większości projektów Django.

#### Wniosek:

Standardowy bootstrap Django jest prosty i przewidywalny: kilkoma komendami
otrzymujesz działający szkielet projektu gotowy do dalszego developmentu.

</details>

<details>
<summary>9. Dlaczego ważne jest używanie środowiska wirtualnego przy pracy z Django?</summary>

#### Django

Środowisko wirtualne (`venv`) izoluje zależności konkretnego projektu od
systemowego Pythona. W Django jest to krytyczne, bo projekty często mają różne
wersje bibliotek i różne wymagania kompatybilności.

#### Dlaczego to ważne:

1. **Izolacja zależności**

- Każdy projekt używa własnych wersji `Django`, `djangorestframework`,
  `psycopg`, `celery` itd., bez konfliktów z innymi projektami.

2. **Odtwarzalność środowiska**

- Łatwo utrwalić stan zależności w `requirements.txt` i odtworzyć go
  na innej maszynie lub serwerze.

3. **Stabilność wdrożeń**

- Mniejsze ryzyko „works on my machine”, gdy lokalnie jest inna wersja pakietu,
  a w CI/production inna.

4. **Bezpieczne aktualizacje**

- Można testować upgrade Django lub pakietów zewnętrznych bez ryzyka zepsucia
  innych lokalnych projektów.

5. **Czystość systemowego Pythona**

- Narzędzia systemowe OS nie zależą od pakietów instalowanych pod development.

#### Co się dzieje bez `venv`:

- Konflikty wersji między projektami.
- Nieprzewidywalne błędy importu po `pip install` nowego pakietu.
- Trudniejszy debug problemów w CI/CD przez różne środowiska.
- Popsute lokalne narzędzia przez globalne aktualizacje.

#### Minimalna praktyka dla zespołu:

1. Tworzyć `.venv` w root każdego repozytorium.
2. Zawsze aktywować środowisko przed `pip install` i komendami `manage.py`.
3. Utrwalać zależności w `requirements.txt` (lub `pyproject.toml` + lock file).
4. Dodawać `.venv/` do `.gitignore`.

#### Wniosek:

`venv` w Django to nie opcja, tylko podstawowy standard dyscypliny inżynierskiej.
Zapewnia przewidywalność, stabilność i normalny workflow zespołowy.

</details>

<details>
<summary>10. Jaka jest struktura projektu Django i rola głównych plików: manage.py, settings.py, urls.py?</summary>

#### Django

Typowy projekt Django ma dwie kluczowe części: root repozytorium oraz pakiet
konfiguracyjny (często `config/`), gdzie znajdują się globalne ustawienia aplikacji.

#### Bazowa struktura projektu:

```text
my_project/
├── manage.py
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
├── app1/
├── app2/
└── requirements.txt
```

#### Rola głównych plików:

1. **manage.py**

- CLI entry point do lokalnej pracy z projektem.
- Przez niego uruchamia się komendy: `runserver`, `migrate`, `makemigrations`,
  `createsuperuser`, `test`, `shell`.
- Automatycznie wskazuje Django, którego modułu settings użyć.

2. **settings.py**

- Centralna konfiguracja projektu.
- Tutaj ustawiasz: `INSTALLED_APPS`, `MIDDLEWARE`, `DATABASES`, `TEMPLATES`,
  `CACHES`, `STATIC_URL`, `MEDIA_URL`, `AUTH_PASSWORD_VALIDATORS`, `TIME_ZONE`
  itd.
- W production zwykle rozdziela się ustawienia na moduły: `settings/base.py`,
  `settings/dev.py`, `settings/prod.py`.

3. **urls.py**

- Globalna mapa tras (URL dispatcher).
- Przyjmuje ścieżkę requestu i deleguje ją do odpowiedniej app przez `include()`.
- Często podłącza się tu `admin/`, health-check routes i API routing.

#### Jak to działa razem:

1. `manage.py` uruchamia komendę Django.
2. Django ładuje `settings.py`.
3. HTTP request przechodzi przez middleware.
4. `urls.py` określa, które `view` obsłuży request.
5. `view` zwraca odpowiedź (HTML/JSON/redirect/file).

#### Praktyczne rekomendacje tech leada:

- Trzymaj `urls.py` „cienki”: główny routing powinien żyć na poziomie app.
- Nie zamieniaj `settings.py` w „skład wszystkiego” - używaj modularnej struktury.
- Wszystkie sekrety (klucze, hasła, tokeny) trzymaj w zmiennych środowiskowych,
  nie w kodzie.
- Wynoś logikę biznesową z `views.py` do warstwy serwisowej, by uprościć testy.

#### Wniosek:

`manage.py`, `settings.py` i `urls.py` to operacyjny rdzeń projektu Django:
zarządzanie, konfiguracja i routing. Dobra organizacja tych plików bezpośrednio
wpływa na skalowalność i utrzymywalność systemu.

</details>

<details>
<summary>11. Do czego służą Django apps i jak organizować projekt z wieloma aplikacjami?</summary>

#### Django

W Django `app` to izolowany moduł funkcjonalny z własnymi modelami,
view, URL, szablonami, testami i (w razie potrzeby) warstwą API.
Apps służą do separacji domen i kontrolowanego wzrostu kodu.

#### Do czego używa się Django apps:

1. **Modułowość**

- Każda app odpowiada za konkretny kontekst biznesowy (np. `users`,
  `billing`, `orders`, `notifications`).

2. **Reużywalność**

- App można przenieść do innego projektu lub używać ponownie wewnętrznie.

3. **Lokalizacja zmian**

- Zmiany w jednej domenie mniej wpływają na inne moduły.

4. **Lepsza utrzymywalność**

- Zespołowi łatwiej odnaleźć się w kodzie, gdy odpowiedzialności są jasno podzielone.

5. **Prostsze testowanie**

- Testy pisze się i uruchamia per domena, a nie dla chaotycznego monolitu.

#### Jak organizować projekt z wieloma apps:

1. **Dziel po domenie, nie po typie technicznym**

- Dobrze: `users`, `catalog`, `checkout`, `payments`.
- Źle: `models_app`, `views_app`, `utils_app`.

2. **Każda app ma własny `urls.py`**

- W root `config/urls.py` tylko podłączenia przez `include()`.

3. **Trzymaj app autonomiczną**

- W app powinny być własne `models.py`, `views.py`, `tests.py`, `admin.py`,
  `apps.py`, `migrations/`.

4. **Unikaj cyklicznych zależności między apps**

- Do komunikacji między modułami lepiej używać warstwy serwisowej lub jawnych
  interfejsów, a nie bezpośrednich importów „wszystko do wszystkiego”.

5. **Wspólny kod wynoś do osobnego modułu `common/core`**

- Ale tylko naprawdę wspólny; nie rób z tego „śmietnika”.

#### Przykład struktury wielomodułowego projektu:

```text
project/
├── config/
│   ├── settings/
│   └── urls.py
├── apps/
│   ├── users/
│   ├── products/
│   ├── orders/
│   └── payments/
└── common/
    ├── db/
    ├── exceptions/
    └── utils/
```

#### Podłączanie tras app:

```python
# config/urls.py
from django.urls import include, path

urlpatterns = [
    path("users/", include("apps.users.urls")),
    path("orders/", include("apps.orders.urls")),
]
```

#### Typowe antywzorce:

- Jedna „gigantyczna” app na cały projekt.
- Podział po warstwach technicznych zamiast domeny biznesowej.
- Masowy shared code bez właściciela i kontraktów.
- Cross-importy między apps bez kontroli zależności.

#### Wniosek:

Django apps to podstawowe narzędzie skalowania kodu. Jeśli rozkładasz system
po domenach z czytelnymi granicami, projekt dłużej pozostaje stabilny i zarządzalny.

</details>

<details>
<summary>12. Jak działa routowanie URL w Django?</summary>

#### Django

Routowanie URL w Django określa, które `view` ma obsłużyć konkretny
HTTP request. Odpowiada za to URL dispatcher skonfigurowany w `urls.py`.

#### Jak działa URL routing krok po kroku:

1. **Request trafia do Django**

- Np. `GET /articles/42/`.

2. **Django czyta root `urlpatterns`**

- Zwykle w `config/urls.py`.

3. **Sekwencyjne dopasowanie tras**

- Django sprawdza patterny od góry do dołu.
- Pierwsze dopasowanie wygrywa.

4. **W razie potrzeby wywoływane jest `include()`**

- Część trasy jest delegowana do `urls.py` konkretnej app.

5. **Parametry URL są przekazywane do view**

- Np. `articles/<int:id>/` przekazuje `id` jako argument.

6. **View buduje response**

- HTML, JSON, redirect albo plik.

7. **Jeśli brak dopasowania -> 404**

- Django zwraca `Not Found`.

#### Bazowy przykład:

```python
# config/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("admin/", admin.site.urls),
    path("articles/", include("apps.articles.urls")),
]
```

```python
# apps/articles/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path("", views.article_list, name="article_list"),
    path("<int:article_id>/", views.article_detail, name="article_detail"),
]
```

#### Konwertery w `path()`:

- `<int:id>` -> liczba całkowita
- `<str:slug>` -> string bez `/`
- `<slug:slug>` -> format slug
- `<uuid:id>` -> UUID
- `<path:subpath>` -> dowolna ścieżka, łącznie z `/`

#### Praktyczne reguły utrzymywalności:

1. Root `urls.py` trzymaj krótki, deleguj do apps.
2. Używaj `name=` dla każdej trasy (wygodne dla `reverse()` i template).
3. Trzymaj stabilną strukturę API/web URL (wersjonowanie, prefiksy).
4. Kolejność tras ma znaczenie: specyficzne patterny dawaj wyżej niż ogólne.

#### Wniosek:

URL routing w Django to kontrolowany mechanizm dispatchingu requestów.
Dobrze zaprojektowane trasy czynią kod przewidywalnym, skalowalnym
i bezpiecznym dla refaktoryzacji.

</details>

<details>
<summary>13. Różnica między path() a re_path().</summary>

#### Django

`path()` i `re_path()` to dwa sposoby opisywania tras URL w Django.
Rozwiązują ten sam problem, ale mają inny poziom złożoności i elastyczności.

#### `path()`:

- Używa czytelnej, deklaratywnej składni z konwerterami.
- Pasuje do większości zwykłych tras.
- Jest bardziej czytelny i łatwiejszy w utrzymaniu zespołowym.

Przykład:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("posts/<int:post_id>/", views.post_detail, name="post_detail"),
    path("users/<slug:username>/", views.user_profile, name="user_profile"),
]
```

#### `re_path()`:

- Używa wyrażeń regularnych (regex).
- Daje maksymalną elastyczność dla niestandardowych URL patternów.
- Trudniej się czyta, większe ryzyko błędów regex.

Przykład:

```python
from django.urls import re_path
from . import views

urlpatterns = [
    re_path(r"^archive/(?P<year>[0-9]{4})/$", views.archive_year),
    re_path(r"^file/(?P<path>.+\.(pdf|docx))/$", views.file_view),
]
```

#### Kiedy czego używać:

1. **Używaj `path()` domyślnie**

- To standardowe i rekomendowane podejście we współczesnym Django.

2. **Używaj `re_path()` tylko gdy `path()` nie wystarcza**

- Np. złożona walidacja formatu URL na poziomie trasy albo legacy URL schemat.

#### Porównanie:

- Prostota: `path()` > `re_path()`
- Elastyczność: `re_path()` > `path()`
- Utrzymywalność zespołowa: zwykle `path()` jest lepszy

#### Praktyczna wskazówka:

Nie komplikuj URL regexami bez potrzeby. Jeśli da się rozwiązać problem przez
konwertery `path()` + walidację w view/serializer/form, to zwykle lepsza droga.

#### Wniosek:

`path()` to główne narzędzie dla 90% tras. `re_path()` to punktowe rozwiązanie
dla szczególnych przypadków wymagających regex-elastyczności.

</details>

<details>
<summary>14. Jak działają URL-konfiguracje i include()?</summary>

#### Django

URL-konfiguracja w Django to zestaw reguł (`urlpatterns`), które mapują
ścieżkę requestu na konkretne `view`. Funkcja `include()` pozwala dzielić duży
routing na moduły na poziomie app.

#### Czym jest URL-konfiguracja:

- To moduł Python (zwykle `urls.py`) z listą tras.
- Każda trasa jest opisana przez `path()` albo `re_path()`.
- Django przechodzi listę od góry do dołu i bierze pierwsze dopasowanie.

#### Do czego służy `include()`:

1. **Dekompozycja routingu**

- Root `urls.py` zostaje krótki.

2. **Modularność po apps**

- Każda aplikacja ma własne trasy w swoim `urls.py`.

3. **Lepsza utrzymywalność**

- Zespół pracuje z lokalnym kontekstem routingu konkretnej domeny.

#### Przykład organizacji:

```python
# config/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("admin/", admin.site.urls),
    path("blog/", include("apps.blog.urls")),
    path("accounts/", include("apps.accounts.urls")),
    path("api/v1/", include("apps.api.urls")),
]
```

```python
# apps/blog/urls.py
from django.urls import path
from . import views

app_name = "blog"

urlpatterns = [
    path("", views.post_list, name="list"),
    path("<slug:slug>/", views.post_detail, name="detail"),
]
```

#### Jak działa łańcuch z `include()`:

1. Request `/blog/django-routing/` trafia do root `config/urls.py`.
2. Prefiks `blog/` pasuje.
3. Django przekazuje resztę ścieżki (`django-routing/`) do `apps.blog.urls`.
4. Tam znajduje się właściwa trasa i wywoływane jest odpowiednie `view`.

#### Namespace i `app_name`:

- `app_name` + `name` trasy daje namespace.
- Pozwala to bez konfliktów używać reverse:
  `reverse("blog:detail", kwargs={"slug": "django-routing"})`.

#### Praktyczne rekomendacje:

1. Zawsze używaj `include()` na poziomie app.
2. Dodawaj `app_name` w każdym app `urls.py`.
3. Trzymaj stabilne prefiksy (`api/v1/`, `admin/`, `auth/`).
4. Nie duplikuj logiki biznesowej w warstwie URL - tylko routing.

#### Wniosek:

URL-konfiguracje + `include()` to podstawa skalowalnego routingu w Django:
jasne granice między app, czysty routing root i przewidywalna nawigacja.

</details>

<details>
<summary>15. Czym jest view w Django?</summary>

#### Django

`View` w Django to handler HTTP requestu. To właśnie view przyjmuje `request`,
wykonuje potrzebną logikę i zwraca `HttpResponse` (HTML, JSON, redirect, plik).

#### Rola view w cyklu request/response:

1. Przyjąć request po URL-matchingu.
2. Zweryfikować parametry wejściowe (path/query/body/files).
3. Wywołać logikę biznesową i/lub ORM.
4. Przygotować dane do odpowiedzi.
5. Zwrócić poprawny HTTP response.

#### Jakie są rodzaje view:

1. **FBV (Function-Based View)**

- Zwykła funkcja Pythona.
- Dobra dla prostej albo mocno custom logiki.

2. **CBV (Class-Based View)**

- Klasa z metodami `get()`, `post()` itd.
- Lepiej skaluje się dla typowych scenariuszy CRUD,
  szczególnie z Generic Views.

#### Przykład FBV:

```python
from django.http import HttpResponse, JsonResponse
from django.shortcuts import render

def healthcheck(request):
    return HttpResponse("OK")

def home(request):
    return render(request, "home.html", {"title": "Strona główna"})

def api_status(request):
    return JsonResponse({"status": "ok"})
```

#### O czym warto pamiętać:

- View nie powinno stawać się „god function”.
- Złożoną logikę biznesową lepiej wynosić do warstwy serwisowej.
- View powinno być „cienkie”: orchestration, walidacja,
  wywołanie serwisów, response.

#### Typowe błędy:

- Pisanie ciężkiej logiki domenowej na setki linii bezpośrednio w view.
- Duplikowanie tej samej logiki w wielu view.
- Ignorowanie kontroli dostępu/autoryzacji na poziomie endpoint.

#### Wniosek:

View to punkt, w którym web-protokół spotyka logikę biznesową.
Dobrze zaprojektowane view daje kod przewidywalny, testowalny i łatwy
w utrzymaniu.

</details>

<details>
<summary>16. Różnica między funkcjonalnymi (FBV) a klasowymi (CBV) widokami.</summary>

#### Django

W Django są dwa główne style widoków: **FBV** (function-based views)
i **CBV** (class-based views). Oba podejścia są poprawne, a różnica dotyczy
sposobu organizacji logiki i skalowania kodu.

#### FBV (Function-Based Views):

- Widok opisany jest jako funkcja.
- Logika request/response czyta się od góry do dołu.
- Proste i przejrzyste podejście dla mniejszych endpointów.

Przykład:

```python
from django.http import JsonResponse

def profile_detail(request, user_id):
    if request.method == "GET":
        return JsonResponse({"user_id": user_id})
    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### CBV (Class-Based Views):

- Widok opisany jest jako klasa (metody `get`, `post`, `put`, `delete` itd.).
- Logikę można reużywać przez dziedziczenie i mixins.
- Dobrze pasuje do CRUD, list, formularzy, scenariuszy detail/create/update/delete.

Przykład:

```python
from django.http import JsonResponse
from django.views import View

class ProfileDetailView(View):
    def get(self, request, user_id):
        return JsonResponse({"user_id": user_id})
```

#### Kluczowe różnice:

1. **Łatwość wejścia**

- FBV: prostsze na start.
- CBV: wymaga zrozumienia hierarchii klas i mechaniki dispatch.

2. **Skalowanie**

- FBV: dobre dla krótkich, mocno custom handlerów.
- CBV: lepsze dla powtarzalnych wzorców i większych projektów.

3. **Reużywalność kodu**

- FBV: przez helper-funkcje/dekoratory.
- CBV: przez dziedziczenie, mixins, generic views.

4. **Czytelność**

- FBV: często bardziej oczywiste lokalnie.
- CBV: bywa trudniejsze przez „ukryte” zachowanie klas bazowych.

5. **Testowanie**

- Oba podejścia testuje się dobrze, jeśli logika nie jest „zaszyta” w view.

#### Kiedy wybierać FBV:

- Endpoint jest prosty i mocno niestandardowy.
- Potrzebujesz maksymalnej przejrzystości kodu do szybkiego debugowania.
- Brak realnego zysku z hierarchii klas.

#### Kiedy wybierać CBV:

- Jest dużo podobnych ekranów/endpointów CRUD.
- Potrzebne są mixins, klasy uprawnień, powtarzalne wzorce.
- Zespół pracuje z Generic CBV i trzyma jednolity styl.

#### Wniosek:

FBV i CBV to nie „dobrze/źle”, tylko kwestia kontekstu. W projektach produkcyjnych
często używa się obu podejść: FBV do punktowych zadań, CBV do
uporządkowanych, powtarzalnych scenariuszy.

</details>

<details>
<summary>17. Kiedy lepiej używać CBV i generic class-based views?</summary>

#### Django

CBV i generic CBV warto stosować wtedy, gdy projekt ma dużo powtarzalnych
wzorców web/API i potrzebna jest standaryzacja zachowania między endpointami.

#### Kiedy CBV realnie wygrywa:

1. **Scenariusze CRUD**

- Listy, strony szczegółów, tworzenie, aktualizacja, usuwanie.
- Typowe klasy: `ListView`, `DetailView`, `CreateView`, `UpdateView`, `DeleteView`.

2. **Dużo podobnych endpointów**

- Gdy różnice między endpointami to głównie model, forma albo reguły uprawnień.

3. **Potrzeba reużywania logiki**

- Przez mixins (`LoginRequiredMixin`, `PermissionRequiredMixin`, własne mixins).

4. **Jednolity styl w większym zespole**

- CBV ułatwia ujednolicenie podejścia i redukuje copy-paste.

5. **Rozszerzanie bazowego zachowania przez override**

- Np. `get_queryset()`, `get_context_data()`, `form_valid()`, `get_success_url()`.

#### Kiedy generic CBV jest szczególnie trafny:

- Interfejsy adminopodobne.
- Strony back-office.
- Standardowe formularze i sekcje contentowe.
- Szybka realizacja MVP bez utraty struktury kodu.

#### Przykład generic CBV:

```python
from django.urls import reverse_lazy
from django.views.generic import ListView, CreateView
from .models import Article
from .forms import ArticleForm

class ArticleListView(ListView):
    model = Article
    template_name = "articles/list.html"
    context_object_name = "articles"
    paginate_by = 20

class ArticleCreateView(CreateView):
    model = Article
    form_class = ArticleForm
    template_name = "articles/form.html"
    success_url = reverse_lazy("articles:list")
```

#### Kiedy lepiej NIE brać generic CBV:

1. Logika jest mocno niestandardowa i nie mieści się w paradygmacie CRUD.
2. Endpoint ma złożony scenariusz orkiestracji (kilka serwisów/integracji).
3. Nadmiar override sprawia, że generic klasa staje się mniej czytelna niż prosty FBV.

#### Praktyczna zasada tech leada:

- Zaczynaj od generic CBV dla standardowych przypadków.
- Jeśli widok „łamie” model generic zachowania, przejdź na zwykły CBV albo FBV.
- Nie trzymaj się generic klasy tylko „bo ładniej” - priorytetem jest
  utrzymywalność i przejrzystość logiki.

#### Wniosek:

CBV/generic CBV to narzędzia przyspieszania i standaryzacji. Najlepiej działają
w powtarzalnych scenariuszach, ale przy nietypowej logice biznesowej
lepiej wybrać prostsze i bardziej jawne podejście.

</details>

<details>
<summary>18. Czym są mixins w CBV i jak ich używać?</summary>

#### Django

`Mixins` w CBV to pomocnicze klasy z reużywalnym zachowaniem, dodawane
przez wielokrotne dziedziczenie. Pozwalają budować elastyczne widoki
bez duplikacji kodu.

#### Po co są mixins:

1. **Reużywanie logiki**

- Auth, permissions, filtrowanie queryset, wspólny kontekst itd.

2. **Kompozycja zachowania**

- Widok składa się z kilku małych „klocków”, a nie jednej dużej klasy.

3. **Mniej copy-paste**

- Jeden mixin można wykorzystać w dziesiątkach widoków.

#### Najczęstsze built-in mixins w Django:

- `LoginRequiredMixin` - dostęp tylko dla zalogowanych.
- `PermissionRequiredMixin` - sprawdzanie konkretnego uprawnienia.
- `UserPassesTestMixin` - custom check dostępu.
- `ContextMixin` - dodawanie danych do kontekstu szablonu.

#### Przykład użycia built-in mixins:

```python
from django.contrib.auth.mixins import LoginRequiredMixin, PermissionRequiredMixin
from django.views.generic import ListView
from .models import Order

class OrderListView(LoginRequiredMixin, PermissionRequiredMixin, ListView):
    model = Order
    permission_required = "orders.view_order"
    template_name = "orders/list.html"
```

#### Przykład custom mixin:

```python
class StaffRequiredMixin:
    def dispatch(self, request, *args, **kwargs):
        if not request.user.is_staff:
            from django.http import HttpResponseForbidden
            return HttpResponseForbidden("Dostęp zabroniony")
        return super().dispatch(request, *args, **kwargs)
```

```python
class DashboardView(StaffRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Kolejność mixins ma znaczenie:

- Django używa MRO (Method Resolution Order).
- Zwykle „ograniczające” mixins (`LoginRequiredMixin`) daje się bardziej na lewo.
- `View`/generic class idą bardziej na prawo.

#### Praktyczne zasady:

1. Jeden mixin - jedna odpowiedzialność.
2. Nie przeciążaj mixinów logiką biznesową.
3. Unikaj głębokiej hierarchii dziedziczenia, która utrudnia debug.
4. Dla złożonego kodu domenowego używaj serwisów, nie mixins.

#### Typowe błędy:

- Zbyt „inteligentne” mixins, które zmieniają zachowanie nieprzewidywalnie.
- Konflikty metod przez złą kolejność dziedziczenia.
- Duplikowanie tych samych kontroli w wielu view zamiast wspólnego mixina.

#### Wniosek:

Mixins to mocne narzędzie w CBV do kompozycji i reużywania kodu.
Dają największą wartość, gdy są małe, jednoznaczne odpowiedzialnościowo
i używane w sposób zdyscyplinowany.

</details>

<details>
<summary>19. Jak obsługiwać metody HTTP (GET, POST)?</summary>

#### Django

W Django metody HTTP obsługuje się w view: `GET` zwykle czyta/pokazuje dane,
`POST` - tworzy lub zmienia stan systemu. Poprawny podział metod to podstawa
bezpiecznego i przewidywalnego API oraz web-flow.

#### Obsługa w FBV:

```python
from django.http import JsonResponse

def contact_view(request):
    if request.method == "GET":
        return JsonResponse({"form": "render contact form"})

    if request.method == "POST":
        # odczyt request.POST, walidacja, zapis
        return JsonResponse({"status": "created"}, status=201)

    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### Obsługa w CBV:

```python
from django.http import JsonResponse
from django.views import View

class ContactView(View):
    def get(self, request):
        return JsonResponse({"form": "render contact form"})

    def post(self, request):
        # walidacja i zapis
        return JsonResponse({"status": "created"}, status=201)
```

#### Ograniczanie dozwolonych metod (dekoratory):

```python
from django.views.decorators.http import require_GET, require_POST, require_http_methods

@require_GET
def list_articles(request):
    ...

@require_POST
def create_article(request):
    ...

@require_http_methods(["GET", "POST"])
def article_endpoint(request):
    ...
```

#### Praktyczne zasady:

1. **GET**

- Nie powinien zmieniać stanu systemu.
- Jest bezpieczny i często cache’owalny.

2. **POST**

- Służy do tworzenia/akcji zmieniającej dane.
- Dla formularzy HTML obowiązkowo CSRF token.

3. **Walidacja**

- Zawsze waliduj dane wejściowe (Forms/Serializer/warstwa serwisowa).

4. **Kody odpowiedzi**

- `200` dla poprawnego odczytu,
- `201` dla utworzenia,
- `400` dla błędów walidacji,
- `405` dla niedozwolonej metody.

#### Typowe błędy:

- Zmienianie danych przez GET (naruszenie semantyki HTTP).
- Mieszanie logiki GET i POST w jeden chaotyczny blok.
- Brak poprawnych status code.

#### Wniosek:

Obsługa GET/POST w Django powinna być jawna: każda metoda to osobna
odpowiedzialność, czytelna walidacja i poprawne kody HTTP.
To poprawia bezpieczeństwo, integracje i utrzymywalność kodu.

</details>

<details>
<summary>20. Jak zaimplementować przekierowanie (redirect)?</summary>

#### Django

Przekierowanie (`redirect`) w Django używa się wtedy, gdy po wykonaniu akcji
trzeba odesłać użytkownika na inną stronę lub endpoint.

#### Główny sposób:

```python
from django.shortcuts import redirect
```

`redirect(...)` zwraca HTTP response z kodem 302 (tymczasowe przekierowanie)
domyślnie.

#### Warianty użycia:

1. **Na absolutny/względny URL**

```python
return redirect("/dashboard/")
```

2. **Na nazwany route (rekomendowane)**

```python
return redirect("orders:list")
```

3. **Na route z parametrami**

```python
return redirect("orders:detail", order_id=order.id)
```

4. **Na model instance (jeśli ma `get_absolute_url`)**

```python
return redirect(order)
```

#### Przykład w FBV (Post/Redirect/Get):

```python
from django.shortcuts import redirect, render

def create_order(request):
    if request.method == "POST":
        # zapis danych
        return redirect("orders:list")
    return render(request, "orders/form.html")
```

#### Przykład w CBV:

```python
from django.urls import reverse_lazy
from django.views.generic import CreateView

class OrderCreateView(CreateView):
    model = Order
    fields = ["title", "amount"]
    success_url = reverse_lazy("orders:list")
```

#### Tymczasowe vs stałe przekierowanie:

- `302 Found` - tymczasowe (domyślne w Django).
- `301 Moved Permanently` - stałe (dla SEO/kanonicznych URL).

Jeśli potrzebujesz stałego redirectu:

```python
from django.http import HttpResponsePermanentRedirect

return HttpResponsePermanentRedirect("/new-url/")
```

#### Praktyczne wskazówki:

1. Używaj nazwanych tras zamiast hardcoded URL.
2. Po udanym POST rób redirect (wzorzec PRG), by uniknąć ponownej wysyłki
   formularza po refresh.
3. Dla redirectu po logowaniu/wylogowaniu używaj `next` i bezpiecznej walidacji
   target URL.

#### Typowe błędy:

- Redirect na URL, który przekierowuje z powrotem (redirect loop).
- Hardcode URL zamiast `name=` route.
- Zwracanie `200` po POST formularza bez PRG tam, gdzie to niepożądane.

#### Wniosek:

`redirect` w Django to podstawowe narzędzie sterowania user flow.
Najlepsza praktyka: nazwane URL + wzorzec PRG + kontrola bezpieczeństwa
celu przekierowania.

</details>

<details>
<summary>21. Czym jest JsonResponse i kiedy się go używa?</summary>

#### Django

`JsonResponse` to HTTP response Django do zwracania danych w formacie JSON.
Najczęściej używa się go w endpointach API, requestach AJAX i integracjach
między serwisami.

#### Co robi `JsonResponse`:

1. Serializuje dane Pythona do JSON.
2. Ustawia poprawny `Content-Type: application/json`.
3. Pozwala jawnie ustawiać HTTP status code.

#### Bazowy przykład:

```python
from django.http import JsonResponse

def health(request):
    return JsonResponse({"status": "ok"})
```

#### Przykład ze status code:

```python
def create_item(request):
    # ... logika tworzenia
    return JsonResponse({"id": 123, "message": "created"}, status=201)
```

#### Ważny niuans `safe`:

- Domyślnie `JsonResponse` oczekuje **dict** (`safe=True`).
- Jeśli chcesz zwrócić listę, ustaw `safe=False`.

```python
def tags(request):
    return JsonResponse(["python", "django", "api"], safe=False)
```

#### Kiedy używać `JsonResponse`:

1. Proste API bez DRF.
2. Wewnętrzne endpointy dla frontendu (fetch/AJAX).
3. Odpowiedzi webhooków i integracji technicznych.
4. Health-check/diagnostic endpoint.

#### Kiedy lepiej DRF, a nie „czysty” `JsonResponse`:

- Potrzebne serializers, walidacja schematu, paginacja, throttling, policy auth.
- Jest dużo endpointów API i potrzebna jedna architektura warstwy API.

#### Praktyczne rekomendacje:

1. Zawsze zwracaj czytelną strukturę JSON (np. `{"data": ...}`,
   `{"error": ...}`).
2. Używaj poprawnych status code (`200`, `201`, `400`, `404`, `500`).
3. Nie zwracaj „surowego” exception trace w production.
4. Ujednolić format błędów dla całego API.

#### Wniosek:

`JsonResponse` to lekki i wygodny mechanizm JSON odpowiedzi w Django.
Do prostych API jest wystarczający, a w większych systemach API zwykle
przechodzi się na DRF.

</details>

<details>
<summary>22. Jak zwracać pliki (CSV, PDF) z view?</summary>

#### Django

W Django pliki z view zwraca się przez `HttpResponse` albo `FileResponse`
z poprawnymi nagłówkami HTTP (`Content-Type`, `Content-Disposition`).

#### Bazowe zasady:

1. **`Content-Type`** musi odpowiadać typowi pliku.
2. **`Content-Disposition`** określa zachowanie przeglądarki:

- `attachment` -> pobierz plik
- `inline` -> pokaż w przeglądarce (jeśli wspierane)

#### Przykład: zwracanie CSV

```python
import csv
from django.http import HttpResponse

def export_users_csv(request):
    response = HttpResponse(content_type="text/csv")
    response["Content-Disposition"] = 'attachment; filename="users.csv"'

    writer = csv.writer(response)
    writer.writerow(["id", "email", "is_active"])
    writer.writerow([1, "user@example.com", True])

    return response
```

#### Przykład: zwracanie PDF z pliku

```python
from django.http import FileResponse

def download_invoice_pdf(request, invoice_id):
    file_path = f"/tmp/invoice-{invoice_id}.pdf"
    return FileResponse(
        open(file_path, "rb"),
        as_attachment=True,
        filename=f"invoice-{invoice_id}.pdf",
        content_type="application/pdf",
    )
```

#### Jeśli PDF generujesz dynamicznie:

- Generuj PDF do pamięci (`io.BytesIO`) albo pliku tymczasowego.
- Potem zwróć przez `HttpResponse`/`FileResponse`.
- Popularne biblioteki: `reportlab`, `weasyprint`, `xhtml2pdf`.

#### Dla dużych plików:

1. Zwracaj przez `FileResponse` (streaming, mniejsze zużycie RAM).
2. Nie czytaj całego pliku do pamięci (`read()` dużych plików jest niewskazane).
3. W razie potrzeby użyj Nginx/X-Accel-Redirect albo CDN/object storage.

#### Praktyczne wskazówki:

1. Ustawiaj czytelne nazwy plików w `filename=`.
2. Kontroluj dostęp do plików (owner/permissions).
3. Dla wrażliwych dokumentów dodaj audyt dostępu.
4. W API zwracaj przewidywalne błędy (`404` gdy brak pliku, `403` gdy brak dostępu).

#### Wniosek:

Zwracanie CSV/PDF w Django to przede wszystkim poprawny typ response i nagłówki.
Dla małych plików wystarczy `HttpResponse`, dla dużych i production obciążenia
lepszy jest `FileResponse` i streaming.

</details>

<details>
<summary>23. Jak zaimplementować paginację?</summary>

#### Django

Paginacja w Django służy do dzielenia dużych list danych na strony, żeby nie
renderować/przesyłać setek lub tysięcy rekordów w jednym request.

#### Bazowe narzędzie:

- `django.core.paginator.Paginator`

#### Przykład w FBV:

```python
from django.core.paginator import Paginator
from django.shortcuts import render
from .models import Article

def article_list(request):
    queryset = Article.objects.order_by("-created_at")
    paginator = Paginator(queryset, 10)  # 10 elementów na stronę
    page_number = request.GET.get("page")
    page_obj = paginator.get_page(page_number)  # bezpieczny wariant

    return render(request, "articles/list.html", {"page_obj": page_obj})
```

#### Render paginacji w template:

```django
{% for article in page_obj %}
  <h3>{{ article.title }}</h3>
{% endfor %}

<div class="pagination">
  {% if page_obj.has_previous %}
    <a href="?page=1">Pierwsza</a>
    <a href="?page={{ page_obj.previous_page_number }}">Wstecz</a>
  {% endif %}

  <span>Strona {{ page_obj.number }} z {{ page_obj.paginator.num_pages }}</span>

  {% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">Dalej</a>
    <a href="?page={{ page_obj.paginator.num_pages }}">Ostatnia</a>
  {% endif %}
</div>
```

#### Wariant CBV (jeszcze prościej):

```python
from django.views.generic import ListView
from .models import Article

class ArticleListView(ListView):
    model = Article
    paginate_by = 10
    ordering = ["-created_at"]
```

#### Praktyczne rekomendacje:

1. Używaj stabilnego sortowania (`order_by`) dla przewidywalnej nawigacji.
2. Dla dużych list optymalizuj queryset:

- `select_related`, `prefetch_related`, indeksy DB.

3. Zachowuj inne query parametry (filtry, wyszukiwanie) przy zmianie strony.
4. Nie ustawiaj zbyt dużego page size bez potrzeby.

#### Typowe błędy:

- Paginacja bez sortowania (dane „skaczą” między stronami).
- Użycie surowego `page()` bez obsługi niepoprawnego numeru strony.
- Brak indeksów na kolumnach używanych do sortowania/filtrowania.

#### Wniosek:

W Django paginację robi się szybko i czysto przez `Paginator` albo `ListView`.
Klucz do wydajności: poprawny queryset, stabilne sortowanie i kontrola
parametrów strony.

</details>

<details>
<summary>24. Jak obsługiwać błędy 404 i 500?</summary>

#### Django

Błędy `404` i `500` w Django obsługiwane są przez standardowy mechanizm
error handling: szablony błędów, funkcje handler i ustawienia globalne.

#### Co oznaczają te błędy:

- **404 Not Found** - trasa albo zasób nie istnieje.
- **500 Internal Server Error** - nieobsłużony błąd po stronie serwera.

#### Bazowa obsługa przez szablony:

W production (`DEBUG = False`) Django automatycznie szuka:

- `templates/404.html`
- `templates/500.html`

Jeśli te pliki istnieją, będą pokazane użytkownikowi.

#### Custom handlers w `urls.py`:

```python
# config/urls.py
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path("admin/", admin.site.urls),
]

handler404 = "config.views.custom_404"
handler500 = "config.views.custom_500"
```

```python
# config/views.py
from django.shortcuts import render

def custom_404(request, exception):
    return render(request, "errors/404.html", status=404)

def custom_500(request):
    return render(request, "errors/500.html", status=500)
```

#### Ważna różnica między dev i production:

1. **DEBUG=True (lokalnie)**

- Django pokazuje szczegółowy debug traceback.

2. **DEBUG=False (production)**

- Użytkownik widzi custom stronę 404/500.
- Szczegóły techniczne błędu nie powinny wyciekać na zewnątrz.

#### Praktyczne rekomendacje:

1. Zawsze miej przyjazne custom strony 404/500.
2. Loguj błędy (Sentry/ELK/OpenTelemetry), zamiast pokazywać stack trace użytkownikowi.
3. Dodaj correlation/request ID do logów dla szybkiej diagnostyki.
4. Zwracaj poprawne status code (nie 200 dla stron błędów).
5. Dla API zwracaj błędy JSON w jednolitym formacie.

#### Testowanie:

- Sprawdzaj 404 dla nieistniejących URL.
- Testuj handlery 500 na staging przy `DEBUG=False`.
- Upewnij się, że szablony błędów są dostępne w zbudowanym środowisku.

#### Wniosek:

Dobra obsługa 404/500 w Django to połączenie UX i dojrzałości operacyjnej:
użytkownik dostaje czytelną stronę, a zespół pełne logi do diagnostyki.

</details>

<details>
<summary>25. Czym są szablony (templates) i jak przekazać dane z view do szablonu?</summary>

#### Django

Szablony (`templates`) w Django to warstwa prezentacji odpowiedzialna za
generowanie HTML na podstawie danych przygotowanych w `view`.

#### Czym jest template:

- Plik HTML z Django template syntax (`{{ }}` i `{% %}`).
- Pozwala wyświetlać zmienne, pętle, warunki, dołączać części strony.
- Oddziela UI od logiki biznesowej kodu Python.

#### Jak przekazać dane z view do template:

1. W `view` zbudować `context` (słownik).
2. Wywołać `render(request, "template.html", context)`.

#### Przykład:

```python
from django.shortcuts import render
from .models import Article

def article_list(request):
    articles = Article.objects.filter(is_published=True).order_by("-created_at")
    context = {
        "page_title": "Artykuły",
        "articles": articles,
        "total": articles.count(),
    }
    return render(request, "articles/list.html", context)
```

#### Użycie danych w szablonie:

```django
<h1>{{ page_title }}</h1>
<p>Łącznie: {{ total }}</p>

{% if articles %}
  <ul>
    {% for article in articles %}
      <li>{{ article.title }}</li>
    {% endfor %}
  </ul>
{% else %}
  <p>Brak opublikowanych artykułów.</p>
{% endif %}
```

#### Skąd Django bierze szablony:

- Z katalogów wskazanych w `TEMPLATES["DIRS"]`.
- Z folderów `templates/` wewnątrz apps (gdy `APP_DIRS=True`).

#### Praktyczne rekomendacje:

1. Trzymaj logikę biznesową w Pythonie (view/service), nie w szablonie.
2. Przekazuj do context tylko potrzebne dane.
3. Używaj nazwanych URL (`{% url 'app:view' %}`), a nie hardcoded linków.
4. Dla powtarzalnych elementów używaj `include`/partials.

#### Bezpieczeństwo:

- Django domyślnie automatycznie escapuje zmienne w szablonach (ochrona XSS).
- Nie używaj `|safe`, jeśli nie masz pewności co do źródła danych.

#### Wniosek:

Templates w Django to czysty, bezpieczny i kontrolowany sposób renderowania HTML.
View przygotowuje dane, template je wyświetla - to daje utrzymywalność
i jasny podział odpowiedzialności w projekcie.

</details>

<details>
<summary>26. Jak działa dziedziczenie szablonów (extends, block)?</summary>

#### Django

Dziedziczenie szablonów w Django pozwala stworzyć bazowy layout i
reużywać go na stronach potomnych. To usuwa duplikację HTML i
utrzymuje frontendową część projektu w porządku.

#### Kluczowe tagi:

1. **`{% extends "base.html" %}`**

- Szablon potomny dziedziczy bazowy.

2. **`{% block ... %}{% endblock %}`**

- W szablonie bazowym definiuje się „sloty”, które szablon potomny może nadpisać.

#### Szablon bazowy:

```django
{# templates/base.html #}
<!doctype html>
<html lang="pl">
<head>
  <meta charset="utf-8">
  <title>{% block title %}Mój serwis{% endblock %}</title>
</head>
<body>
  <header>Header</header>

  <main>
    {% block content %}{% endblock %}
  </main>

  <footer>Footer</footer>
</body>
</html>
```

#### Szablon potomny:

```django
{# templates/articles/list.html #}
{% extends "base.html" %}

{% block title %}Lista artykułów{% endblock %}

{% block content %}
  <h1>Artykuły</h1>
  <p>Treść strony...</p>
{% endblock %}
```

#### `block.super`:

Jeśli chcesz rozszerzyć blok, a nie nadpisywać go całkowicie:

```django
{% block title %}{{ block.super }} | Artykuły{% endblock %}
```

#### Praktyczne rekomendacje:

1. Trzymaj jeden główny `base.html` (layout: head, header, footer, scripts).
2. Dodawaj osobne bloki dla `title`, `content`, `extra_css`, `extra_js`.
3. Nie duplikuj tych samych części w każdym szablonie - wynoś do base/include.
4. Utrzymuj spójne nazwy bloków w całym projekcie.

#### Typowe błędy:

- Brak jednolitej struktury bloków między stronami.
- Przenoszenie logiki biznesowej do szablonu zamiast do view/service.
- Duplikowanie layoutu bez `extends`.

#### Wniosek:

`extends` i `block` to fundament skalowalnej architektury szablonów w Django:
jedna wspólna otoczka serwisu, minimum duplikacji i szybkie zmiany UI.

</details>

<details>
<summary>27. Do czego służy {% include %}?</summary>

#### Django

`{% include %}` służy do wstawienia jednego szablonu do drugiego.
To wygodne dla powtarzalnych części interfejsu: header, footer, karty,
tabele, paginacja.

#### Po co `include`:

1. **Usuwa duplikację HTML**

- Jeden fragment można reużywać na wielu stronach.

2. **Poprawia utrzymywalność**

- Zmiana w pliku partial automatycznie działa wszędzie, gdzie jest użyty.

3. **Upraszcza czytanie szablonów**

- Duży szablon dzieli się na mniejsze logiczne bloki.

#### Bazowy przykład:

```django
{# templates/base.html #}
<body>
  {% include "partials/header.html" %}
  <main>{% block content %}{% endblock %}</main>
  {% include "partials/footer.html" %}
</body>
```

#### Przekazywanie kontekstu do include:

```django
{% include "partials/user_badge.html" with user=request.user %}
```

Można ograniczyć kontekst wyłącznie do przekazanych zmiennych:

```django
{% include "partials/user_badge.html" with user=request.user only %}
```

#### Praktyczne use-case:

- Komponent paginacji.
- Wiersz tabeli / karta produktu.
- Blok alertów/wiadomości.
- Wspólne elementy layoutu.

#### Różnica między `extends` i `include`:

- `extends` - dziedziczenie struktury szablonu (poziom layoutu).
- `include` - wstawienie lokalnego fragmentu (poziom komponentu).

#### Typowe błędy:

1. Używanie `include` zamiast `extends` dla bazowego layoutu.
2. Przekazywanie zbyt „szerokiego” niejawnego kontekstu.
3. Umieszczanie ciężkiej logiki w partial-szablonie.

#### Wniosek:

`{% include %}` to podstawowe narzędzie modularnego template code w Django.
Używaj go dla małych, reużywalnych fragmentów, a `extends` dla ogólnej
struktury strony.

</details>

<details>
<summary>28. Czym są template partials i jak działają {% partial %} oraz {% partialdef %}?</summary>

#### Django

Template partials to sposób definiowania i reużywania fragmentów szablonu
bezpośrednio wewnątrz pliku template. Do tego służą tagi
`{% partialdef %}` (definicja) oraz `{% partial %}` (wywołanie).

#### Jak to działa:

1. **`{% partialdef name %}...{% endpartialdef %}`**

- Definiuje nazwany fragment partial.

2. **`{% partial name %}`**

- Renderuje partial w wybranym miejscu szablonu.

#### Bazowy przykład:

```django
{% partialdef product_card %}
  <article class="card">
    <h3>{{ product.title }}</h3>
    <p>{{ product.price }} PLN</p>
  </article>
{% endpartialdef %}

<section class="grid">
  {% for product in products %}
    {% partial product_card %}
  {% endfor %}
</section>
```

#### Czym to różni się od `{% include %}`:

- `include` podłącza osobny plik.
- `partial/partialdef` pozwala zdefiniować i wywołać fragment w kontekście
  bieżącego szablonu bez tworzenia osobnego pliku.

#### Kiedy partials są szczególnie przydatne:

1. Gdy trzeba szybko reużyć mały fragment w obrębie jednego szablonu.
2. Gdy chcesz uniknąć „rozdrabniania” na dziesiątki małych include-plików.
3. Dla lokalnych bloków UI, których nie ma sensu wynosić do osobnego template.

#### Praktyczne rekomendacje:

1. Dla globalnie reużywalnych komponentów między stronami zostaw
   `{% include %}` albo osobne partial-pliki.
2. Dla lokalnych, małych fragmentów używaj `partial/partialdef`.
3. Nie przenoś logiki biznesowej do partial - tylko warstwa prezentacji.

#### Kompatybilność:

- W nowszych wersjach Django partial tags są dostępne jako część systemu template.
- Jeśli projekt jest na starszej wersji, podobny efekt zwykle robi się przez
  `{% include %}` i custom template tags.

#### Wniosek:

`{% partialdef %}` i `{% partial %}` to narzędzie lokalnej kompozycji szablonów:
mniej duplikacji, lepsza czytelność i większa kontrola nad strukturą UI.

</details>

<details>
<summary>29. Czym są template tags i filters?</summary>

#### Django

`Template tags` i `filters` to narzędzia Django template engine do
kontrolowanego renderowania danych w szablonach.

#### Template tags:

- Tagi wykonują logikę na poziomie szablonu.
- Używa się ich w formacie `{% ... %}`.

Typowe built-in tagi:

1. `{% if %}` / `{% elif %}` / `{% else %}` - renderowanie warunkowe.
2. `{% for %}` - iteracja kolekcji.
3. `{% url %}` - budowanie linku po nazwie trasy.
4. `{% include %}` - wstawienie części szablonu.
5. `{% csrf_token %}` - ochrona CSRF w formularzach.
6. `{% static %}` - linki do static plików.

Przykład:

```django
{% if user.is_authenticated %}
  <a href="{% url 'profile' %}">Profil</a>
{% else %}
  <a href="{% url 'login' %}">Zaloguj się</a>
{% endif %}
```

#### Filters:

- Filtry transformują wartości zmiennych.
- Używa się ich przez `|` wewnątrz `{{ ... }}`.

Typowe built-in filtry:

1. `|lower`, `|upper`, `|title`
2. `|length`
3. `|date:"d.m.Y"`
4. `|default:"-"`, `|default_if_none:"-"`
5. `|truncatechars:50`
6. `|safe` (ostrożnie!)

Przykład:

```django
<p>{{ article.title|title }}</p>
<p>{{ article.created_at|date:"d.m.Y H:i" }}</p>
<p>{{ article.description|truncatechars:120 }}</p>
```

#### Jak stworzyć własny filter:

```python
# app/templatetags/text_extras.py
from django import template

register = template.Library()

@register.filter
def initials(full_name):
    parts = full_name.split()
    return "".join(p[0].upper() for p in parts if p)
```

```django
{% load text_extras %}
{{ user.full_name|initials }}
```

#### Jak stworzyć własny simple tag:

```python
@register.simple_tag
def app_version():
    return "1.0.0"
```

```django
{% load text_extras %}
<small>v{% app_version %}</small>
```

#### Praktyczne zasady:

1. Trzymaj szablony „cienkie”: minimum logiki, maksimum czytelności.
2. Powtarzalną logikę prezentacji wynoś do custom filters/tags.
3. Nie przenoś logiki biznesowej do template tags.
4. `|safe` stosuj tylko dla zaufanej treści.

#### Wniosek:

Template tags kontrolują strukturę renderowania, a filters formatowanie wartości.
Razem dają elastyczny i bezpieczny sposób budowania UI w szablonach Django.

</details>

<details>
<summary>30. Jak podłączać pliki statyczne (static) i co robi collectstatic?</summary>

#### Django

Pliki statyczne (`static`) to CSS, JS, obrazy, fonty i inne zasoby,
które nie są generowane dynamicznie dla każdego requestu.

#### Bazowe ustawienia w `settings.py`:

```python
STATIC_URL = "/static/"
STATIC_ROOT = BASE_DIR / "staticfiles"   # dla production build
```

Jeśli potrzebujesz dodatkowych katalogów:

```python
STATICFILES_DIRS = [BASE_DIR / "static"]
```

#### Jak podłączać static w szablonie:

```django
{% load static %}
<link rel="stylesheet" href="{% static 'css/main.css' %}">
<script src="{% static 'js/app.js' %}"></script>
<img src="{% static 'img/logo.svg' %}" alt="Logo">
```

#### Gdzie trzymać static:

1. W każdym app:

- `app_name/static/app_name/...`

2. Albo we wspólnym katalogu projektu:

- `project_root/static/...`

#### Co robi `collectstatic`:

Komenda:

```bash
python manage.py collectstatic
```

Wynik:

1. Zbiera wszystkie static pliki z apps i `STATICFILES_DIRS`.
2. Kopiuje je do jednej katalogowej lokalizacji `STATIC_ROOT`.
3. Przygotowuje zestaw plików, który serwuje webserwer/CDN w production.

#### Dev vs Production:

1. **Lokalny development (`DEBUG=True`)**

- Django może samo serwować static.

2. **Production (`DEBUG=False`)**

- Static zwykle serwuje Nginx, CDN albo object storage.
- Proces Django nie powinien serwować static bezpośrednio.

#### Częste production-praktyki:

- `ManifestStaticFilesStorage` dla versioned/hashed plików (cache busting).
- WhiteNoise dla prostego deploy bez osobnego Nginx.
- CDN dla szybkiej dystrybucji zasobów statycznych.

#### Typowe błędy:

1. Brak `collectstatic` przed deployem.
2. Hardcode ścieżek do `/static/...` zamiast `{% static %}`.
3. Mylenie `static` (assets) i `media` (user uploads).
4. Brak konfiguracji `STATIC_ROOT` dla production.

#### Wniosek:

Podłączanie static w Django opiera się na `{% static %}` i poprawnych settings.
`collectstatic` to obowiązkowy krok production build, który unifikuje wszystkie
zasoby statyczne dla szybkiego i stabilnego serwowania.

</details>

<details>
<summary>31. Czym są MEDIA_ROOT i MEDIA_URL?</summary>

#### Django

`MEDIA_ROOT` i `MEDIA_URL` służą do pracy z plikami uploadowanymi przez
użytkowników (uploads): avatary, dokumenty, zdjęcia, wideo itd.

#### Czym jest `MEDIA_ROOT`:

- Absolutna ścieżka w systemie plików serwera, gdzie fizycznie leżą upload pliki.
- To „dysk”, do którego Django zapisuje pliki z `FileField`/`ImageField`.

#### Czym jest `MEDIA_URL`:

- Prefiks URL, przez który te pliki są dostępne z przeglądarki.
- To „publiczna ścieżka” do contentu z `MEDIA_ROOT`.

#### Bazowa konfiguracja:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Przykład modelu:

```python
from django.db import models

class Profile(models.Model):
    avatar = models.ImageField(upload_to="avatars/")
```

Jeśli użytkownik wrzuci plik `photo.jpg`, trafi on do:

- Plik na dysku: `MEDIA_ROOT/avatars/photo.jpg`
- URL w przeglądarce: `MEDIA_URL + "avatars/photo.jpg"` ->
  `/media/avatars/photo.jpg`

#### Konfiguracja URL w development:

```python
# config/urls.py
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    # ...
]

if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

#### Podejście production:

1. Django zapisuje plik (lokalnie albo w cloud storage backend).
2. Serwowanie plików robi Nginx/CDN/S3, a nie proces Django.
3. Dostęp kontroluje się przez permissions albo pre-signed URL (dla prywatnych plików).

#### Ważna różnica między `static` i `media`:

- `static` - pliki dewelopera (CSS/JS/logo), zbierane przez `collectstatic`.
- `media` - pliki użytkowników, nie przechodzą przez `collectstatic`.

#### Typowe błędy:

1. Mieszanie `STATIC_ROOT` i `MEDIA_ROOT`.
2. Trzymanie user uploads w git repo.
3. Serwowanie media przez Django w production bez potrzeby.
4. Brak walidacji typu/rozmiaru uploadowanych plików.

#### Wniosek:

`MEDIA_ROOT` - gdzie plik leży fizycznie, `MEDIA_URL` - jak klient się do niego
odwołuje. Jasne rozdzielenie media/static to obowiązkowy standard w projektach Django.

</details>

<details>
<summary>32. Jakie są podejścia do cache’owania szablonów?</summary>

#### Django

Cache’owanie szablonów w Django zmniejsza obciążenie CPU/DB i przyspiesza
odpowiedź stron dzięki ponownemu użyciu już wygenerowanego contentu.

#### Główne podejścia:

1. **Template fragment caching (rekomendowane dla części strony)**

- Cache’uje tylko fragment szablonu, a nie całą stronę.

```django
{% load cache %}
{% cache 300 sidebar user.id %}
  {# ciężki blok: menu, rekomendacje, widżety #}
  ...
{% endcache %}
```

2. **Per-view caching**

- Cache’uje pełną odpowiedź konkretnego view na określony TTL.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)  # 5 min

def article_list(request):
    ...
```

3. **Site-wide caching (przez middleware)**

- Cache’uje prawie cały serwis według globalnych reguł.
- Dobre dla serwisów contentowych z niską personalizacją.

4. **Low-level cache API**

- Cache’owanie wyników zapytań/obliczeń w kodzie Python.

```python
from django.core.cache import cache

data = cache.get("popular_articles")
if data is None:
    data = expensive_query()
    cache.set("popular_articles", data, 300)
```

#### Konfiguracja cache backendu:

W production zwykle stosuje się Redis albo Memcached:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Co wybierać w jakim przypadku:

- Fragmenty UI z ciężkim renderem -> template fragment cache.
- Stabilna publiczna strona -> per-view cache.
- Głównie statyczny serwis -> site-wide cache.
- Ciężka logika biznesowa/zapytania -> low-level cache API.

#### Praktyczne zasady:

1. Zaczynaj od najmniej agresywnego cache (fragmenty), potem skaluj.
2. Dobieraj TTL do wymagań biznesowych świeżości danych.
3. Dla personalizowanych bloków dodawaj klucze (user id, locale, permissions).
4. Przewiduj invalidację cache po zmianach danych.

#### Typowe błędy:

1. Cache’owanie personalizowanego contentu bez klucza użytkownika.
2. Brak invalidacji cache po update/delete.
3. Zbyt długi TTL dla dynamicznych danych.
4. Traktowanie cache jako „lekarstwa” na nieefektywne zapytania SQL.

#### Wniosek:

Najbezpieczniejszy start w Django to fragment caching + Redis.
Potem dodaje się per-view albo site-wide cache, gdy uzasadnia to profil obciążenia i UX.

</details>

<details>
<summary>33. Czym są Django Forms i ModelForm?</summary>

#### Django

`Django Forms` to mechanizm obsługi HTML formularzy: walidacja, czyszczenie danych,
renderowanie pól i obsługa błędów.
`ModelForm` to specjalny typ formularza automatycznie budowany na podstawie
modelu Django.

#### Django Form:

- Definiowany przez `forms.Form`.
- Pola definiujesz ręcznie.
- Dobry dla formularzy niezwiązanych bezpośrednio z modelem.

Przykład:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.CharField(widget=forms.Textarea)
```

#### ModelForm:

- Definiowany przez `forms.ModelForm`.
- Pola są generowane z modelu.
- Łatwy zapis do DB przez `form.save()`.

Przykład:

```python
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ["title", "content", "is_published"]
```

#### Główna różnica:

1. **Źródło pól**

- Form: pola definiujesz ręcznie.
- ModelForm: pola pochodzą z modelu.

2. **Zapis danych**

- Form: ręczna obróbka i zapis.
- ModelForm: `form.save()` out of the box.

3. **Scenariusz użycia**

- Form: contact form, wyszukiwanie, filtry, login/reset, formularze integracyjne.
- ModelForm: CRUD dla modeli, interfejsy adminopodobne.

#### Przykład obsługi w view:

```python
def create_article(request):
    if request.method == "POST":
        form = ArticleForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect("articles:list")
    else:
        form = ArticleForm()

    return render(request, "articles/form.html", {"form": form})
```

#### Zalety Django Forms ogólnie:

- Scentralizowana walidacja po stronie serwera.
- Ochrona przed błędami wejścia i niepoprawnymi typami.
- Wygodna praca z komunikatami błędów.
- Łatwa integracja z template.

#### Wniosek:

`Form` wybieraj dla custom scenariuszy bez bezpośredniego modelu.
`ModelForm` to najszybsza i najczystsza droga dla CRUD na modelach Django.

</details>

<details>
<summary>34. Jaka jest różnica między formularzem HTML a formularzem Django?</summary>

#### Django

HTML formularz i Django formularz rozwiązują ten sam problem (wprowadzanie danych),
ale na różnych poziomach. HTML formularz to tylko markup w przeglądarce,
a Django formularz to serwerowy mechanizm walidacji i obróbki danych.

#### HTML formularz:

- Opisuje pola, przyciski, `method`, `action`.
- Działa po stronie klienta (przeglądarka).
- Nie gwarantuje bezpieczeństwa i poprawności danych po stronie serwera.

Przykład:

```html
<form method="post" action="/contact/">
  <input type="text" name="name" />
  <input type="email" name="email" />
  <button type="submit">Wyślij</button>
</form>
```

#### Django formularz:

- Definiowany w Pythonie (`forms.Form` albo `forms.ModelForm`).
- Wykonuje serwerową walidację, czyszczenie danych (`cleaned_data`), buduje błędy.
- Łatwo integruje się z template i ochroną CSRF.

Przykład:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
```

#### Kluczowe różnice:

1. **Poziom**

- HTML formularz: presentation layer.
- Django formularz: backend validation layer.

2. **Walidacja**

- HTML: podstawowa klientowska (łatwa do obejścia).
- Django Form: obowiązkowa serwerowa, wiarygodna.

3. **Bezpieczeństwo**

- HTML sam nie chroni przed forged requestami.
- Django form współpracuje z `{% csrf_token %}` i wbudowaną obsługą błędów.

4. **Utrzymywalność**

- HTML-only często prowadzi do duplikacji walidacji.
- Django form centralizuje reguły i upraszcza utrzymanie.

5. **Praca z modelami**

- HTML: ręczny zapis.
- ModelForm: `form.save()` out of the box.

#### Praktyczna zasada:

W production nie można polegać wyłącznie na walidacji HTML.
Walidacja kliencka jest dla UX, Django form dla correctness i bezpieczeństwa.

#### Wniosek:

HTML formularz odpowiada za interfejs, Django formularz za jakość danych
i serwerową niezawodność. W realnych projektach działają razem, ale
krytyczna walidacja zawsze musi być na backendzie.

</details>

<details>
<summary>35. Jak renderować formularze w szablonie?</summary>

#### Django

Formularze w Django renderuje się w szablonie przez obiekt `form`,
przekazany z view. Są dwa podejścia: szybki render automatyczny
lub kontrolowany render ręczny.

#### 1. Szybki render automatyczny:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Zapisz</button>
</form>
```

Dostępne warianty:

- `{{ form.as_p }}` - pola owinięte w `<p>`
- `{{ form.as_ul }}` - pola jako lista `<li>`
- `{{ form.as_table }}` - pola w układzie tabeli

#### 2. Render ręczny (rekomendowany dla production UI):

```django
<form method="post" novalidate>
  {% csrf_token %}

  <div>
    {{ form.title.label_tag }}
    {{ form.title }}
    {% for error in form.title.errors %}
      <p class="error">{{ error }}</p>
    {% endfor %}
  </div>

  <div>
    {{ form.content.label_tag }}
    {{ form.content }}
    {% for error in form.content.errors %}
      <p class="error">{{ error }}</p>
    {% endfor %}
  </div>

  {% if form.non_field_errors %}
    <div class="error">
      {% for error in form.non_field_errors %}
        <p>{{ error }}</p>
      {% endfor %}
    </div>
  {% endif %}

  <button type="submit">Zapisz</button>
</form>
```

#### Co trzeba dodać obowiązkowo:

1. `{% csrf_token %}` dla formularzy POST.
2. Wyświetlanie błędów pól (`field.errors`) i błędów ogólnych (`non_field_errors`).
3. `enctype="multipart/form-data"` dla formularzy z plikami.

#### Przykład dla upload formularza:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Wgraj</button>
</form>
```

#### Praktyczne rekomendacje:

1. Dla MVP można zacząć od `form.as_p`.
2. Dla realnego produktu lepszy jest render ręczny dla pełnej kontroli UX/UI.
3. Nie ukrywaj błędów walidacji - pokazuj je przy odpowiednich polach.
4. Preferuj nazwane akcje przycisków i czytelny submit-flow.

#### Wniosek:

Render formularzy w Django może być bardzo szybki albo bardzo kontrolowany.
Dla jakości production zwykle wybiera się render ręczny z jawnym pokazywaniem
błędów, ochroną CSRF i kontrolowaną strukturą HTML.

</details>

<details>
<summary>36. Jak działa walidacja formularzy i jak stworzyć własną?</summary>

#### Django

Walidacja formularzy w Django odbywa się po stronie serwera przy wywołaniu
`form.is_valid()`. W rezultacie Django albo zwraca oczyszczone dane
(`cleaned_data`), albo wypełnia `form.errors`.

#### Jak działa walidacja krok po kroku:

1. Django sprawdza typy i podstawowe reguły pól (`required`, `max_length`,
   `EmailField`, `IntegerField` itd.).
2. Wywołuje custom walidatory pola (jeśli dodane).
3. Wywołuje metody `clean_<field>()` dla konkretnych pól.
4. Wywołuje ogólną metodę `clean()` dla logiki między polami.
5. Buduje `cleaned_data` albo listę błędów.

#### Walidacja jednego pola (`clean_<field>()`):

```python
from django import forms
from django.core.exceptions import ValidationError

class RegisterForm(forms.Form):
    username = forms.CharField(max_length=50)

    def clean_username(self):
        value = self.cleaned_data["username"].strip()
        if "admin" in value.lower():
            raise ValidationError("Nazwa użytkownika zawiera niedozwolone słowo.")
        return value
```

#### Walidacja między polami (`clean()`):

```python
class PasswordForm(forms.Form):
    password = forms.CharField(widget=forms.PasswordInput)
    confirm_password = forms.CharField(widget=forms.PasswordInput)

    def clean(self):
        cleaned_data = super().clean()
        p1 = cleaned_data.get("password")
        p2 = cleaned_data.get("confirm_password")

        if p1 and p2 and p1 != p2:
            raise forms.ValidationError("Hasła nie są takie same.")
        return cleaned_data
```

#### Custom walidatory:

```python
from django.core.exceptions import ValidationError

def validate_company_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Dozwolony jest tylko firmowy e-mail.")
```

```python
email = forms.EmailField(validators=[validate_company_email])
```

#### Dla `ModelForm`:

- Działa walidacja formularza + walidacja modelu.
- W modelu można dodatkowo używać: `clean()`, `unique=True`,
  `UniqueConstraint`, `validators`.

#### Jak obsługiwać w view:

```python
def submit_form(request):
    form = RegisterForm(request.POST or None)
    if request.method == "POST" and form.is_valid():
        # pracujemy z form.cleaned_data
        ...
    return render(request, "form.html", {"form": form})
```

#### Praktyczne zasady:

1. Walidacja zawsze musi być po stronie serwera (kliencka tylko dla UX).
2. Lokalna logika pola -> `clean_<field>()`.
3. Logika zależna od wielu pól -> `clean()`.
4. Reguły wielokrotnego użytku -> osobne walidatory.
5. Reguły domenowe krytyczne duplikuj na poziomie DB (constraints), nie tylko w form.

#### Wniosek:

Mocna strona Django Forms to wielopoziomowa, uporządkowana walidacja.
Daje to kontrolę jakości danych, czytelne błędy dla użytkownika i stabilny
backend flow obsługi formularzy w production.

</details>

<details>
<summary>37. Czym są custom walidatory w Django i jak stosować je wielokrotnie?</summary>

#### Django

Custom walidatory w Django to funkcje albo klasy sprawdzające wartość pola
według twoich reguł i rzucające `ValidationError`, gdy dane nie przechodzą
walidacji.

#### Po co są potrzebne:

1. **Reużywanie reguł**

- Jedna reguła może działać w wielu formularzach/modelach.

2. **Jedno źródło prawdy**

- Reguła biznesowa nie jest duplikowana po całym kodzie.

3. **Czystsza architektura**

- Logika walidacji jest wyniesiona z view/forms do osobnej warstwy.

#### Przykład funkcjonalnego walidatora:

```python
from django.core.exceptions import ValidationError

def validate_corporate_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Dozwolony jest tylko firmowy e-mail.")
```

Użycie w modelu:

```python
from django.db import models
from .validators import validate_corporate_email

class Employee(models.Model):
    email = models.EmailField(validators=[validate_corporate_email])
```

Użycie w formularzu:

```python
from django import forms
from .validators import validate_corporate_email

class InviteForm(forms.Form):
    email = forms.EmailField(validators=[validate_corporate_email])
```

#### Przykład class-based walidatora:

```python
from django.core.exceptions import ValidationError

class MinWordsValidator:
    def __init__(self, min_words=3):
        self.min_words = min_words

    def __call__(self, value):
        if len(value.split()) < self.min_words:
            raise ValidationError(f"Minimum {self.min_words} słowa/słów.")
```

```python
description = models.TextField(validators=[MinWordsValidator(5)])
```

#### Gdzie najlepiej trzymać:

- `app/validators.py` albo `app/domain/validators.py`
- W dużych projektach - osobne moduły per domena.

#### Praktyczne zasady:

1. Walidator powinien robić jedną konkretną kontrolę.
2. Komunikaty błędów muszą być zrozumiałe dla użytkownika.
3. Dla krytycznych reguł duplikuj kontrolę na poziomie DB (`UniqueConstraint`, check constraints).
4. Pisz testy walidatorów osobno od view.

#### Wniosek:

Custom walidatory to poprawny sposób centralizacji reguł walidacji w Django.
Kod jest czystszy, bardziej reużywalny i mniej podatny na rozjazd reguł
w różnych częściach systemu.

</details>

<details>
<summary>38. Jak obsługiwać upload plików?</summary>

#### Django

Upload plików w Django obsługuje się przez `request.FILES`, pola
`FileField`/`ImageField` i poprawnie ustawione `MEDIA_ROOT`/`MEDIA_URL`.

#### Co jest potrzebne do uploadu:

1. Pole pliku w formularzu albo modelu.
2. `enctype="multipart/form-data"` w formularzu HTML.
3. Przekazanie `request.FILES` do formularza.
4. Skonfigurowane media parametry w `settings.py`.

#### Przykład modelu:

```python
from django.db import models

class Document(models.Model):
    title = models.CharField(max_length=200)
    file = models.FileField(upload_to="documents/%Y/%m/")
```

#### Przykład ModelForm:

```python
from django import forms
from .models import Document

class DocumentForm(forms.ModelForm):
    class Meta:
        model = Document
        fields = ["title", "file"]
```

#### Przykład view:

```python
from django.shortcuts import redirect, render
from .forms import DocumentForm

def upload_document(request):
    if request.method == "POST":
        form = DocumentForm(request.POST, request.FILES)
        if form.is_valid():
            form.save()
            return redirect("documents:list")
    else:
        form = DocumentForm()

    return render(request, "documents/upload.html", {"form": form})
```

#### Szablon:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Wgraj</button>
</form>
```

#### Konfiguracja media:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Bezpieczeństwo i praktyka production:

1. Waliduj typ, rozmiar i rozszerzenie pliku.
2. Nie ufaj oryginalnej nazwie pliku od klienta.
3. Ograniczaj dostęp do prywatnych plików przez permissions.
4. W production używaj zewnętrznego storage (S3-compatible) albo osobnego file servera.
5. Skanuj potencjalnie niebezpieczne pliki (jeśli use-case jest ryzykowny).

#### Typowe błędy:

1. Brak `enctype="multipart/form-data"` -> `request.FILES` jest puste.
2. Przekazanie tylko `request.POST` bez `request.FILES`.
3. Mieszanie static i media.
4. Brak walidacji rozmiaru/typu i ryzyka bezpieczeństwa lub przeciążenia.

#### Wniosek:

W Django upload działa stabilnie, jeśli trzymasz się bazowych reguł:
poprawny formularz, `request.FILES`, walidatory i kontrola dostępu
do plików w production.

</details>

<details>
<summary>39. Czym jest Django ORM?</summary>

#### Django

Django ORM (Object-Relational Mapping) to warstwa dostępu do danych,
która pozwala pracować z bazą przez obiekty Pythona zamiast ręcznego
pisania SQL w większości typowych scenariuszy.

#### Główna idea ORM:

1. **Model Python = tabela DB**
2. **Instancja modelu = wiersz tabeli**
3. **Pole modelu = kolumna tabeli**
4. **QuerySet = SQL zapytanie(a) generowane przez ORM**

#### Przykład:

```python
# models.py
class Article(models.Model):
    title = models.CharField(max_length=200)
    is_published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

```python
# tworzenie
Article.objects.create(title="Django ORM", is_published=True)

# odczyt
articles = Article.objects.filter(is_published=True).order_by("-created_at")

# aktualizacja
article = Article.objects.get(pk=1)
article.title = "Updated title"
article.save()

# usunięcie
article.delete()
```

#### Zalety Django ORM:

1. **Szybszy development** - mniej SQL boilerplate.
2. **Czytelny kod** - zapytania opisujesz deklaratywnie.
3. **Bezpieczeństwo** - parametryzacja zapytań ogranicza ryzyko SQL injection.
4. **Przenośność** - ten sam kod działa z różnymi DB (w większości przypadków).
5. **Integracja z Django** - forms, admin, migrations, validators.

#### Ważne koncepty:

- `QuerySet` jest lazy: zapytanie wykonuje się dopiero gdy dane są potrzebne.
- `select_related` i `prefetch_related` pomagają unikać problemu N+1.
- `annotate`, `aggregate`, `F`, `Q`, `Subquery` - do bardziej złożonych zapytań.

#### Ograniczenia ORM:

1. Bardzo złożone konstrukcje SQL czasem prościej pisać jako raw SQL.
2. Bez profilowania łatwo wygenerować nieefektywne zapytania.
3. Niewłaściwe użycie relacji może mocno uderzyć w wydajność.

#### Kiedy używać raw SQL:

- Optymalizacje specyficzne dla konkretnej bazy.
- Złożona analityka/CTE/window functions, gdzie ORM traci czytelność.
- Zadania migracyjne/operacyjne wymagające pełnej kontroli SQL.

#### Wniosek:

Django ORM to jeden z największych plusów frameworka: szybki, bezpieczny i
wygodny dla większości use-case’ów biznesowych. Dla dobrych wyników production
trzeba jednak rozumieć, jaki SQL ORM generuje, i optymalizować zapytania.

</details>

<details>
<summary>40. Czym jest model i jak go stworzyć?</summary>

#### Django

Model (`Model`) w Django to klasa Pythona opisująca strukturę danych i
odpowiadająca tabeli w bazie danych. Przez model definiujesz pola, relacje
i reguły na poziomie danych.

#### Czym jest model:

1. **Opis schematu DB w Pythonie**

- Pola modelu (`CharField`, `IntegerField`, `DateTimeField`...) odpowiadają
  kolumnom tabeli.

2. **Warstwa encji domenowych**

- Model reprezentuje obiekt biznesowy: `User`, `Order`, `Invoice`, `Product`.

3. **Integracja z ORM**

- Tworzenie, odczyt, aktualizacja, usuwanie rekordów przez `Model.objects`.

#### Przykład modelu:

```python
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=150)
    sku = models.CharField(max_length=64, unique=True)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    is_active = models.BooleanField(default=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def __str__(self):
        return f"{self.name} ({self.sku})"
```

#### Jak stworzyć model krok po kroku:

1. Dodaj klasę do `app/models.py`.
2. Upewnij się, że app jest dodana do `INSTALLED_APPS`.
3. Utwórz migrację:

```bash
python manage.py makemigrations
```

4. Zastosuj migrację do DB:

```bash
python manage.py migrate
```

#### Bazowe praktyki:

1. Używaj czytelnych nazw pól i ograniczeń (`unique`, `db_index`).
2. Dodawaj pola techniczne `created_at`, `updated_at`.
3. Definiuj `__str__` dla czytelności w admin i shell.
4. Krytyczne inwarianty domenowe utrwalaj w DB (constraints), nie tylko w view/forms.

#### Typowe błędy:

1. Trzymanie „wszystkiego jako text” i ignorowanie typów danych.
2. Brak indeksów dla pól filtrowania/wyszukiwania.
3. Mieszanie wysokopoziomowej logiki biznesowej bezpośrednio w modelu bez struktury.
4. Opóźnione migracje powodujące rozjazd między środowiskami.

#### Wniosek:

Model w Django to fundament pracy z danymi. Dobrze zaprojektowane modele
bezpośrednio wpływają na wydajność, niezawodność i skalowalność całego projektu.

</details>

<details>
<summary>41. Czym są ForeignKey, OneToOneField, ManyToManyField?</summary>

#### Django

`ForeignKey`, `OneToOneField` i `ManyToManyField` to typy relacji między
modelami w Django ORM. Określają, jak encje są powiązane ze sobą w DB.

#### 1. ForeignKey (jeden-do-wielu, 1:N)

- Jeden obiekt „rodzica” może mieć wiele „dzieci”.
- Każdy rekord dziecka wskazuje tylko jednego rodzica.

Przykład:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Use-case: jeden autor -> wiele książek.

#### 2. OneToOneField (jeden-do-jednego, 1:1)

- Każdemu rekordowi modelu A odpowiada maksymalnie jeden rekord modelu B.
- W praktyce to `ForeignKey(unique=True)` z czytelniejszą semantyką.

Przykład:

```python
from django.conf import settings

class Profile(models.Model):
    user = models.OneToOneField(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    bio = models.TextField(blank=True)
```

Use-case: jeden użytkownik -> jeden profil.

#### 3. ManyToManyField (wiele-do-wielu, M:N)

- Rekordy z obu tabel mogą mieć wiele powiązań między sobą.
- Django tworzy tabelę pośrednią automatycznie (albo przez `through=`).

Przykład:

```python
class Tag(models.Model):
    name = models.CharField(max_length=50, unique=True)

class Article(models.Model):
    title = models.CharField(max_length=200)
    tags = models.ManyToManyField(Tag, related_name="articles")
```

Use-case: artykuł ma wiele tagów, tag należy do wielu artykułów.

#### Jak wybierać typ relacji:

1. `ForeignKey` - gdy jest wyraźny „właściciel” i wiele rekordów podrzędnych.
2. `OneToOneField` - gdy encja rozszerzająca ma istnieć w jednej instancji.
3. `ManyToManyField` - gdy obie strony mogą mieć wiele odpowiedników.

#### Niuans `on_delete` dla ForeignKey/OneToOne:

- `CASCADE` - usuń rekordy podrzędne razem z rodzicem.
- `PROTECT` - zablokuj usunięcie, jeśli istnieją zależności.
- `SET_NULL` - wyzeruj referencję (pole musi mieć `null=True`).

#### Wniosek:

Te trzy pola to podstawa modelowania relacyjnych danych w Django.
Dobrze dobrany typ relacji upraszcza zapytania, migracje i długoterminowe
utrzymanie modelu domenowego.

</details>

<details>
<summary>42. Jakie istnieją typy dziedziczenia modeli?</summary>

#### Django

W Django są trzy główne typy dziedziczenia modeli: **Abstract Base Classes**,
**Multi-table inheritance** i **Proxy models**. Rozwiązują różne problemy
i mają różny wpływ na schemat DB.

#### 1. Abstract Base Class (dziedziczenie abstrakcyjne)

- Model bazowy nie tworzy własnej tabeli w DB.
- Jego pola są kopiowane do modeli potomnych.

Przykład:

```python
class TimeStampedModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True

class Article(TimeStampedModel):
    title = models.CharField(max_length=200)
```

Kiedy używać:

- Dla wspólnych pól/metod między wieloma modelami.
- Najczęstszy i najbardziej praktyczny wariant w production.

#### 2. Multi-table inheritance (dziedziczenie z osobnymi tabelami)

- Każdy model w łańcuchu dziedziczenia ma osobną tabelę.
- Django tworzy relację `OneToOne` między rodzicem i potomkiem.

Przykład:

```python
class Person(models.Model):
    name = models.CharField(max_length=120)

class Employee(Person):
    salary = models.DecimalField(max_digits=10, decimal_places=2)
```

Kiedy używać:

- Gdy potrzebna jest realna hierarchia encji w DB.
- Gdy ważne są osobne tabele dla modelu bazowego i specjalizacji.

Minus:

- Dodatkowe JOIN-y i bardziej złożone zapytania.

#### 3. Proxy model (model proxy)

- Nie tworzy nowej tabeli.
- Pracuje na tej samej tabeli co model bazowy.
- Pozwala zmienić zachowanie Pythona (metody, manager, ordering)
  bez zmiany schematu DB.

Przykład:

```python
class Order(models.Model):
    status = models.CharField(max_length=20)

class OpenOrder(Order):
    class Meta:
        proxy = True
        ordering = ["id"]
```

Kiedy używać:

- Potrzebny inny manager/zachowanie dla tego samego modelu.
- Potrzebna inna prezentacja w Django Admin bez zmiany tabel.

#### Szybki wybór:

1. Wspólne pola bez osobnej tabeli -> **abstract**.
2. Realna hierarchia danych z osobnymi tabelami -> **multi-table**.
3. Inne zachowanie Pythona bez zmiany DB -> **proxy**.

#### Praktyczna rada:

Domyślnie wybieraj **abstract base class**.
`multi-table` stosuj ostrożnie, tylko gdy wynika to z modelu domenowego,
a nie „dla ładnej hierarchii”.

#### Wniosek:

Typ dziedziczenia w Django dobiera się do celu: reużywanie pól,
fizyczna hierarchia tabel albo sama zmiana zachowania modelu.
Dobry wybór upraszcza schemat DB i późniejsze utrzymanie projektu.

</details>

<details>
<summary>43. Do czego służy klasa Meta?</summary>

#### Django

Wewnętrzna klasa `Meta` w modelu Django służy do konfiguracji
zachowania modelu na poziomie ORM i DB bez zmiany logiki biznesowej modelu.

#### Co zwykle ustawia się w `Meta`:

1. **`ordering`** - domyślne sortowanie.
2. **`db_table`** - custom nazwa tabeli w DB.
3. **`verbose_name`, `verbose_name_plural`** - czytelne nazwy w admin.
4. **`indexes`** - indeksy wydajnościowe.
5. **`constraints`** - ograniczenia biznesowe na poziomie DB.
6. **`unique_together` / `UniqueConstraint`** - unikalność kombinacji pól.
7. **`abstract` / `proxy`** - typ dziedziczenia modelu.

#### Przykład:

```python
from django.db import models
from django.db.models import Q

class Product(models.Model):
    sku = models.CharField(max_length=64)
    name = models.CharField(max_length=200)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    is_active = models.BooleanField(default=True)

    class Meta:
        db_table = "catalog_product"
        ordering = ["name"]
        verbose_name = "Produkt"
        verbose_name_plural = "Produkty"
        indexes = [
            models.Index(fields=["sku"]),
            models.Index(fields=["is_active", "name"]),
        ]
        constraints = [
            models.UniqueConstraint(fields=["sku"], name="uq_product_sku"),
            models.CheckConstraint(
                check=Q(price__gte=0), name="chk_product_price_non_negative"
            ),
        ]
```

#### Dlaczego `Meta` jest ważna:

1. **Wydajność**

- Indeksy i poprawne ograniczenia obniżają koszt zapytań.

2. **Integralność danych**

- Constraints chronią przed błędnymi zapisami, nawet gdy walidacja
  została gdzieś pominięta.

3. **Kontrola schematu**

- Jawna kontrola tabel i reguł w migracjach.

4. **Wygoda admina**

- Czytelne nazwy modeli w back-office.

#### Praktyczne rekomendacje:

1. Używaj `UniqueConstraint` zamiast przestarzałego `unique_together`.
2. Dodawaj indeksy tylko na realnie „gorące” pola filtrowania/sortowania.
3. Trzymaj krytyczne reguły biznesowe na poziomie DB przez `constraints`.
4. Nie nadużywaj `db_table`, jeśli nie ma potrzeby jawnego nazewnictwa.

#### Wniosek:

`Meta` to centrum konfiguracji ORM-zachowania modelu.
Przez nią sterujesz sortowaniem, indeksami, ograniczeniami i jakością schematu DB,
co bezpośrednio wpływa na niezawodność i wydajność projektu Django.

</details>

<details>
<summary>44. Jaka jest różnica między null=True a blank=True?</summary>

#### Django

`null=True` i `blank=True` rozwiązują różne problemy i działają na różnych poziomach:

- `null=True` - poziom **bazy danych** (czy można przechowywać `NULL`).
- `blank=True` - poziom **walidacji formularzy/admina** (czy pole może być puste).

#### `null=True`:

1. Pozwala zapisać `NULL` w kolumnie DB.
2. Wpływa na schemat tabeli i migracje.
3. Jest krytyczne dla pól, gdzie brak wartości powinien być SQL `NULL`.

#### `blank=True`:

1. Pozwala nie wypełniać pola w formularzach, ModelForm, Django Admin.
2. Nie zmienia bezpośrednio typu kolumny w DB.
3. Wpływa na `form.is_valid()`, a nie na poziom SQL.

#### Przykłady:

```python
class Profile(models.Model):
    bio = models.TextField(blank=True)  # w formie opcjonalne
    birth_date = models.DateField(null=True, blank=True)  # DB NULL i puste w formie
```

#### Ważny niuans dla stringów (`CharField`, `TextField`):

- W Django zwykle **nie ustawia się `null=True`** dla pól tekstowych.
- Rekomendowana praktyka: używać pustego stringa `""`, a nie `NULL`.
- Czyli zwykle: `CharField(..., blank=True)` bez `null=True`.

#### Szybka matryca:

1. `null=False, blank=False` -> pole obowiązkowe i w DB, i w formularzach.
2. `null=True, blank=False` -> w DB może być `NULL`, ale formularz wymaga wartości.
3. `null=False, blank=True` -> formularz dopuszcza puste, ale DB przechowuje nie `NULL`
   (często `""`).
4. `null=True, blank=True` -> najbardziej „opcjonalne” pole (i formularz, i DB).

#### Praktyczne rekomendacje:

1. Dla `DateField`, `DateTimeField`, `ForeignKey`, pól liczbowych często potrzebne
   są oba: `null=True, blank=True`.
2. Dla `CharField/TextField` zwykle wystarczy `blank=True`.
3. Trzymaj spójną politykę w projekcie, żeby uniknąć chaosu między `NULL` i `""`.
4. Pamiętaj: zły wybór utrudnia filtrowanie i analitykę.

#### Wniosek:

`null` steruje przechowywaniem w DB, `blank` - walidacją na poziomie Django forms.
To dwie różne osie zachowania i trzeba je ustawiać świadomie pod model domenowy.

</details>

<details>
<summary>45. Jaka jest różnica między CharField a TextField?</summary>

#### Django

`CharField` i `TextField` przechowują tekst, ale mają różne scenariusze użycia
oraz ograniczenia na poziomie modelu/DB.

#### `CharField`:

1. Przeznaczony do krótkiego/średniego tekstu.
2. **Obowiązkowo** wymaga `max_length`.
3. Dobrze pasuje do pól, gdzie długość ma być kontrolowana: name, slug,
   title, code, email, phone.

Przykład:

```python
title = models.CharField(max_length=200)
sku = models.CharField(max_length=64, unique=True)
```

#### `TextField`:

1. Przeznaczony do długiego, swobodnego tekstu.
2. Nie wymaga `max_length` na poziomie modelu (można dodać walidacją).
3. Dobry dla opisów, treści artykułów, notatek, komentarzy.

Przykład:

```python
description = models.TextField(blank=True)
content = models.TextField()
```

#### Kluczowe różnice:

1. **Ograniczenie długości**

- `CharField`: zawsze `max_length`.
- `TextField`: bez twardego limitu domyślnie.

2. **Semantyka danych**

- `CharField`: ustrukturyzowany krótki tekst.
- `TextField`: duży nieustrukturyzowany tekst.

3. **Formularze/admin**

- `CharField` zwykle renderuje się jako `input`.
- `TextField` zwykle jako `textarea`.

4. **Indeksowanie i wydajność**

- Krótkie indeksowane pola zwykle sensowniej trzymać w `CharField`.
- Dla dużych tekstów indeksowanie zależy od DB i często wymaga osobnej
  strategii (full-text search).

#### Praktyczne zasady tech leada:

1. Jeśli wartość ma naturalny limit długości -> wybieraj `CharField`.
2. Jeśli tekst potencjalnie jest duży/dowolny -> `TextField`.
3. Nie używaj `TextField` „na zapas”, gdy wystarczy `CharField`.
4. Dla wyszukiwania po dużych tekstach planuj osobną strategię search
   (PostgreSQL FTS, Elasticsearch/OpenSearch itd.).

#### Wniosek:

`CharField` - kontrolowany krótki tekst, `TextField` - duża treść.
Poprawny wybór pola wpływa na walidację, UX formularzy, indeksowanie
i wydajność zapytań.

</details>

<details>
<summary>46. Czym są model managers i jak stworzyć własny?</summary>

#### Django

`Model Manager` w Django to „entry point” do zapytań modelu przez ORM.
Domyślnie każdy model ma manager `objects`, ale możesz tworzyć własne
managery z metodami domenowymi.

#### Po co własne managery:

1. **Centralizacja logiki zapytań**

- Żeby nie duplikować tych samych `filter(...)` w wielu view/serwisach.

2. **Czytelny API modelu**

- Np. `Article.objects.published().recent()`.

3. **Kontrola „domyślnego” zestawu danych**

- Np. ukrycie soft-deleted rekordów.

#### Bazowy przykład managera:

```python
from django.db import models
from django.utils import timezone

class ArticleManager(models.Manager):
    def published(self):
        return self.get_queryset().filter(is_published=True)

    def recent(self):
        return self.get_queryset().filter(
            created_at__gte=timezone.now() - timezone.timedelta(days=7)
        )

class Article(models.Model):
    title = models.CharField(max_length=200)
    is_published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)

    objects = ArticleManager()
```

Użycie:

```python
Article.objects.published()
Article.objects.recent()
```

#### Kombinacja Manager + QuerySet (lepsza skalowalność):

```python
class ArticleQuerySet(models.QuerySet):
    def published(self):
        return self.filter(is_published=True)

    def recent(self):
        return self.order_by("-created_at")

class Article(models.Model):
    ...
    objects = ArticleQuerySet.as_manager()
```

#### Praktyczne rekomendacje:

1. Do manager/queryset wynoś tylko logikę selekcji danych.
2. Orkiestrację biznesową zostawiaj w warstwie serwisowej.
3. Nazwy metod rób domenowe (`active`, `paid`, `for_user`).
4. Nie rób managera „magicznego” - zachowanie ma być czytelne.

#### Typowe błędy:

1. Duplikowanie tych samych filtrów po całym kodzie.
2. Mieszanie ciężkiej logiki biznesowej w managerze.
3. Nadpisanie default managera tak, że admin/migracje zachowują się nieoczekiwanie.

#### Wniosek:

Model managers to właściwe miejsce na wielokrotnie używane zapytania ORM.
Własny manager porządkuje kod i zapewnia spójność zapytań w całym projekcie.

</details>

<details>
<summary>47. Czym są migracje i po co są potrzebne?</summary>

#### Django

Migracje w Django to kontrolowana historia zmian schematu bazy danych,
przechowywana w kodzie projektu i wykonywana przez `makemigrations` oraz
`migrate`.

#### Co dają migracje:

1. **Wersjonowanie DB**

- Zmiany tabel, pól, indeksów, constraints są utrwalone jako pliki-instrukcje.

2. **Odtwarzalność środowisk**

- Dev, staging i production dostają ten sam schemat DB.

3. **Bezpieczna ewolucja schematu**

- Zamiast ręcznego SQL w notatkach zespół ma formalny proces zmian.

4. **Współpraca zespołowa**

- Migracje są commitowane do gita i przechodzą code review razem z kodem.

#### Jak to działa:

1. Zmieniasz model w `models.py`.
2. `python manage.py makemigrations` generuje plik migracji.
3. `python manage.py migrate` aplikuje zmiany do DB.
4. Django zapisuje stan w tabeli `django_migrations`.

#### Przykłady zmian przez migracje:

- Dodanie/usunięcie pola.
- Zmiana typu pola.
- Utworzenie indeksu.
- Dodanie `UniqueConstraint` albo `CheckConstraint`.
- Zmiana nazwy modelu/pola.

#### Data migrations:

Poza strukturą można wykonywać migracje danych (`RunPython`), np.:

- wypełnić nowe pole wartościami,
- przenieść dane między kolumnami,
- znormalizować istniejące rekordy.

#### Praktyczne zasady:

1. Commituj migracje razem ze zmianami modeli.
2. Nie edytuj starych migracji, jeśli są już użyte we wspólnych środowiskach.
3. Testuj migracje na staging przed production.
4. Dla dużych tabel planuj backward-compatible rollout (expand/contract).

#### Typowe błędy:

1. Uruchamianie kodu bez aktualnych migracji.
2. Zapomnienie commitowania plików migracji.
3. Wykonywanie ryzykownych blocking operacji na dużych tabelach bez planu.
4. Edycja zastosowanych migracji i psucie historii schematu.

#### Wniosek:

Migracje to „system kontroli wersji” dla DB w Django.
Są krytyczne dla bezpiecznego deployu, pracy zespołowej i przewidywalnej
ewolucji danych.

</details>

<details>
<summary>48. Jaka jest różnica między makemigrations a migrate?</summary>

#### Django

`makemigrations` i `migrate` to dwie różne fazy pracy z migracjami:

- `makemigrations` **tworzy** pliki migracji (plan zmian).
- `migrate` **aplikuje** te zmiany do bazy danych.

#### `makemigrations`:

1. Analizuje zmiany w `models.py`.
2. Generuje pliki migracji Python w `app/migrations/`.
3. Nie zmienia DB bezpośrednio.

Komenda:

```bash
python manage.py makemigrations
```

#### `migrate`:

1. Czyta pliki migracji.
2. Wykonuje operacje SQL w DB (CREATE/ALTER/DROP itd.).
3. Oznacza zastosowane migracje w tabeli `django_migrations`.

Komenda:

```bash
python manage.py migrate
```

#### Prosty workflow:

1. Zmieniłeś modele.
2. Uruchomiłeś `makemigrations`.
3. Sprawdziłeś wygenerowaną migrację.
4. Uruchomiłeś `migrate`.
5. Commitnąłeś kod + pliki migracji.

#### Analogia:

- `makemigrations` = „zapisać instrukcję”.
- `migrate` = „wykonać instrukcję”.

#### Przydatne komendy:

```bash
python manage.py showmigrations
python manage.py sqlmigrate app_name 0001
```

- `showmigrations` pokazuje, które migracje są zastosowane.
- `sqlmigrate` pokazuje SQL, który zostanie wykonany.

#### Typowe błędy:

1. Uruchomienie `migrate` bez wygenerowania migracji po zmianie modeli.
2. Wykonanie `makemigrations`, ale bez commitowania plików.
3. Mylenie lokalnego stanu DB ze stanem na staging/production.
4. Ignorowanie konfliktów migracji w pracy zespołowej.

#### Wniosek:

`makemigrations` przygotowuje zmiany, `migrate` je stosuje.
Dla stabilnego procesu deployu potrzebne są oba kroki,
wykonywane sekwencyjnie i świadomie.

</details>

<details>
<summary>49. Jak podłączyć PostgreSQL albo inną bazę danych?</summary>

#### Django

Podłączenie DB w Django robi się przez konfigurację `DATABASES` w `settings.py`.
W production najczęściej używa się PostgreSQL, rzadziej MySQL/MariaDB.

#### 1. Zainstaluj driver DB

Dla PostgreSQL (rekomendowany nowoczesny wariant):

```bash
pip install psycopg[binary]
```

Alternatywa: `psycopg2-binary`.

#### 2. Skonfiguruj `DATABASES` w `settings.py`

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "mydb",
        "USER": "myuser",
        "PASSWORD": "mypassword",
        "HOST": "127.0.0.1",
        "PORT": "5432",
    }
}
```

#### 3. Uruchom migracje

```bash
python manage.py migrate
```

#### Podłączenie przez env zmienne (rekomendowane):

```python
import os

DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": os.getenv("DB_NAME", "mydb"),
        "USER": os.getenv("DB_USER", "myuser"),
        "PASSWORD": os.getenv("DB_PASSWORD", ""),
        "HOST": os.getenv("DB_HOST", "127.0.0.1"),
        "PORT": os.getenv("DB_PORT", "5432"),
    }
}
```

#### Inne wspierane silniki:

1. SQLite (domyślnie dla lokalnego dev/prototypów)
2. PostgreSQL (główny wybór production)
3. MySQL / MariaDB
4. Oracle

#### Rekomendacje production:

1. Nie trzymaj haseł DB w repozytorium.
2. Włącz SSL do DB (tam, gdzie potrzebne).
3. Skonfiguruj connection pooling (PgBouncer albo parametry po stronie DB).
4. Dodaj health-check i monitoring latency/locks/slow queries.
5. Używaj osobnych ról dostępu (least privilege).

#### Typowe błędy:

1. Zły `ENGINE` albo brak drivera.
2. Lokalnie działa, a w CI/prod nie - przez env zmienne.
3. Używanie SQLite w production pod współbieżnym obciążeniem.
4. Brak timeoutów/poolingu pod loadem.

#### Wniosek:

Aby podłączyć PostgreSQL w Django, potrzebujesz trzech kroków: driver,
`DATABASES`, migracje. W production krytyczne są: env konfiguracja,
bezpieczne dane dostępowe, SSL i kontrola wydajności połączeń.

</details>

<details>
<summary>50. Czym jest QuerySet? Czym jest lazy evaluation?</summary>

#### Django

`QuerySet` w Django ORM to obiekt reprezentujący zestaw rekordów z DB i
łańcuch operacji na nich (`filter`, `exclude`, `order_by`, `annotate` itd.).

#### Co ważne o QuerySet:

1. Domyślnie jest **leniwy** (`lazy`).
2. Zbudowanie QuerySet nie wykonuje SQL od razu.
3. SQL wykonuje się dopiero wtedy, gdy dane są realnie potrzebne.

#### Przykład leniwości:

```python
qs = Article.objects.filter(is_published=True).order_by("-created_at")
# Na tym etapie zapytanie do DB jeszcze NIE zostało wykonane
```

#### Kiedy QuerySet się materializuje (wykonuje SQL):

1. Iteracja:

```python
for article in qs:
    ...
```

2. Konwersja do listy:

```python
items = list(qs)
```

3. Pobranie długości/wartości bool:

```python
len(qs)
bool(qs)
```

4. Wywołania typu:

- `first()`, `last()`, `exists()`, `count()`, `get()`
- slicing (często z `LIMIT/OFFSET`), np. `qs[:10]`

#### Zalety lazy evaluation:

1. **Optymalizacja zapytań**

- Możesz budować złożony queryset etapami przed wykonaniem.

2. **Elastyczność**

- Jeden bazowy queryset możesz reużywać z różnymi warunkami.

3. **Mniej zbędnych odwołań do DB**

- Jeśli queryset nie został użyty, zapytanie się nie wykona.

#### Typowe błędy:

1. Wywoływanie querysetów w pętlach i generowanie N+1 zapytań.
2. Wielokrotna iteracja po tym samym queryset bez cache wyniku.
3. Mylenie `count()` i `len(qs)` (zachowanie/koszt mogą się różnić).

#### Praktyczne wskazówki:

1. Dla relacji używaj `select_related()` / `prefetch_related()`.
2. Jeśli wynik potrzebny wiele razy w tym samym flow - materializuj:
   `items = list(qs)`.
3. Do sprawdzania istnienia używaj `exists()`, a nie pełnej iteracji.
4. Profiluj SQL (Django Debug Toolbar, logi DB), zamiast ufać intuicji.

#### Wniosek:

`QuerySet` to centralna abstrakcja Django ORM, a lazy evaluation to jej kluczowa
optymalizacja. Zrozumienie momentu wykonania SQL jest krytyczne dla wydajności
realnych projektów Django.

</details>

<details>
<summary>51. Jak działają filter(), exclude(), get()?</summary>

#### Django

`filter()`, `exclude()` i `get()` to bazowe metody Django ORM do pobierania danych.
Mają podobną składnię, ale różnią się zachowaniem i gwarancjami.

#### `filter()`:

- Zwraca `QuerySet` ze wszystkimi rekordami spełniającymi warunek.
- Jeśli nie ma dopasowań, zwraca pusty `QuerySet` (bez wyjątku).

```python
active_users = User.objects.filter(is_active=True)
cheap_products = Product.objects.filter(price__lt=1000)
```

#### `exclude()`:

- Zwraca `QuerySet` z rekordami, które **nie** spełniają warunku.

```python
non_archived = Article.objects.exclude(status="archived")
```

#### `get()`:

- Zwraca **jeden** obiekt modelu.
- Oczekuje dokładnie jednego dopasowania.
- Jeśli wyników jest 0 albo >1 -> rzuca wyjątek.

```python
user = User.objects.get(pk=1)
```

#### Wyjątki dla `get()`:

1. `Model.DoesNotExist` - nic nie znaleziono.
2. `Model.MultipleObjectsReturned` - znaleziono więcej niż jeden rekord.

Przykład bezpiecznej obsługi:

```python
from django.http import Http404

def profile_view(request, user_id):
    try:
        user = User.objects.get(pk=user_id)
    except User.DoesNotExist:
        raise Http404("Nie znaleziono użytkownika")
```

Albo krócej:

```python
from django.shortcuts import get_object_or_404
user = get_object_or_404(User, pk=user_id)
```

#### Kiedy czego używać:

1. **`filter()`** - gdy wyników może być wiele albo zero.
2. **`exclude()`** - gdy trzeba odsiać część danych.
3. **`get()`** - gdy gwarantujesz unikalny wynik (PK, pole unique).

#### Praktyczne wskazówki:

1. Nie używaj `get()`, gdy unikalność nie jest gwarantowana.
2. Do sprawdzania istnienia używaj `exists()`, a nie `get()+try/except`.
3. Dla złożonej logiki warunków łącz `Q`.

#### Wniosek:

`filter()` i `exclude()` pracują na zbiorze rekordów przez QuerySet,
a `get()` na pojedynczym obiekcie z ostrym wymaganiem unikalności.
Poprawny wybór metody zmniejsza liczbę błędów i upraszcza edge case’y.

</details>

<details>
<summary>52. Jaka jest różnica między get() a filter()?</summary>

#### Django

`get()` i `filter()` oba wyszukują dane w ORM, ale mają inną semantykę:
jeden zwraca **jeden obiekt**, drugi **zbiór obiektów (QuerySet)**.

#### `get()`:

1. Zwraca pojedynczą instancję modelu.
2. Oczekuje dokładnie jednego dopasowania.
3. Rzuca wyjątki, jeśli rekordów jest 0 albo więcej niż 1.

```python
user = User.objects.get(pk=10)
```

Możliwe wyjątki:

- `User.DoesNotExist`
- `User.MultipleObjectsReturned`

#### `filter()`:

1. Zwraca `QuerySet`.
2. Może zwrócić 0, 1 lub wiele rekordów.
3. Nie rzuca wyjątku, jeśli nic nie znaleziono.

```python
users = User.objects.filter(is_active=True)
```

#### Kluczowe różnice:

1. **Typ wyniku**

- `get()` -> jeden obiekt.
- `filter()` -> QuerySet.

2. **Zachowanie przy braku danych**

- `get()` -> wyjątek.
- `filter()` -> pusty QuerySet.

3. **Scenariusz użycia**

- `get()` -> pola unikalne (`id`, `uuid`, `email` z `unique=True`).
- `filter()` -> wyszukiwanie po warunkach, gdzie wyników może być wiele.

#### Praktyczny przykład:

```python
# poprawnie: unikalne wyszukiwanie
order = Order.objects.get(id=order_id)

# poprawnie: lista zamówień użytkownika
orders = Order.objects.filter(user=request.user).order_by("-created_at")
```

#### Typowe błędy:

1. Używanie `get()` dla pola nieunikalnego (ryzyko `MultipleObjectsReturned`).
2. Oczekiwanie pojedynczego obiektu z `filter()` bez `.first()` albo `get()`.
3. Brak obsługi wyjątków `get()` w API/view.

#### Wniosek:

`get()` jest do pojedynczego unikalnego rekordu, `filter()` do kolekcji i
elastycznego wyszukiwania. Jeśli masz wątpliwość co do krotności wyniku,
bezpieczniej zacząć od `filter()`.

</details>

<details>
<summary>53. Jak pobrać wszystkie rekordy albo jeden rekord?</summary>

#### Django

W Django ORM są różne metody pobierania wszystkich rekordów lub jednego
konkretnego rekordu. Wybór zależy od tego, czy oczekujesz kolekcji,
czy pojedynczego wyniku.

#### Pobranie wszystkich rekordów:

1. **Wszystkie rekordy modelu**

```python
articles = Article.objects.all()
```

2. **Wszystkie rekordy spełniające warunek**

```python
articles = Article.objects.filter(is_published=True)
```

3. **Zoptymalizowane pobranie konkretnych pól**

```python
articles = Article.objects.values("id", "title")
```

#### Pobranie jednego rekordu:

1. **Dokładnie jeden rekord przez `get()`**

```python
article = Article.objects.get(pk=article_id)
```

Dobre, gdy unikalność jest gwarantowana.

2. **Bezpieczny wariant w web-view**

```python
from django.shortcuts import get_object_or_404

article = get_object_or_404(Article, pk=article_id)
```

3. **Pierwszy rekord z queryset**

```python
article = Article.objects.filter(is_published=True).first()
```

Zwraca obiekt albo `None`, bez wyjątków.

#### Kiedy czego używać:

1. Kolekcja do list/tabel -> `all()` / `filter()`.
2. Jeden unikalny rekord -> `get()`.
3. Jeden rekord w web-flow z 404 -> `get_object_or_404()`.
4. Opcjonalny pojedynczy wynik -> `first()`.

#### Typowe błędy:

1. Używanie `get()` dla pola nieunikalnego.
2. Pobieranie `all()` bez filtrów/paginacji na dużych tabelach.
3. Brak obsługi `DoesNotExist` w API/view.

#### Wniosek:

Dla „wszystkich rekordów” używaj QuerySet (`all/filter`), dla „jednego rekordu”
wybieraj `get()` albo bezpieczne warianty (`get_object_or_404`, `first()`)
w zależności od wymagań błędów i UX.

</details>

<details>
<summary>54. Różnica między select_related() i prefetch_related()?</summary>

#### Django

`select_related()` i `prefetch_related()` służą do optymalizacji ORM,
aby uniknąć problemu N+1 zapytań przy pracy z powiązanymi modelami.

#### `select_related()`:

1. Działa dla relacji **ForeignKey** i **OneToOne** (strona „jeden”).
2. Wykonuje **SQL JOIN** i pobiera dane powiązane jednym zapytaniem.
3. Jest efektywny dla relacji „single-valued”.

Przykład:

```python
orders = Order.objects.select_related("customer").all()
for order in orders:
    print(order.customer.email)  # bez dodatkowych zapytań
```

#### `prefetch_related()`:

1. Działa dla **ManyToMany**, reverse ForeignKey i także może dla FK/O2O.
2. Wykonuje kilka zapytań (główne + dodatkowe), a potem „skleja” wyniki w Pythonie.
3. Jest efektywny dla relacji „multi-valued”.

Przykład:

```python
articles = Article.objects.prefetch_related("tags").all()
for article in articles:
    print([tag.name for tag in article.tags.all()])  # bez N+1
```

#### Kluczowa różnica:

1. **Mechanizm**

- `select_related()` -> JOIN w jednym SQL.
- `prefetch_related()` -> kilka SQL + łączenie w Python.

2. **Typ relacji**

- `select_related()` -> FK/O2O.
- `prefetch_related()` -> M2M, reverse FK (i w razie potrzeby inne).

3. **Wolumen danych**

- `select_related()` może „rozdmuchać” wiersz przez JOIN-y.
- `prefetch_related()` lepszy dla kolekcji obiektów podrzędnych.

#### Użycie łączone:

```python
orders = (
    Order.objects
    .select_related("customer")
    .prefetch_related("items", "items__product")
)
```

#### Praktyczna reguła wyboru:

1. Potrzebujesz pola z FK/O2O -> zaczynaj od `select_related`.
2. Potrzebujesz listy obiektów powiązanych (M2M/reverse) -> `prefetch_related`.
3. Profiluj zapytania (debug toolbar/logi), nie zgaduj „na oko”.

#### Typowe błędy:

1. Brak obu metod i problem N+1.
2. Używanie `select_related()` dla M2M (nie rozwiązuje problemu).
3. Wywoływanie `.all()` na related manager w pętli bez prefetch.

#### Wniosek:

`select_related()` optymalizuje relacje „pojedyncze” przez JOIN,
a `prefetch_related()` relacje „kolekcyjne” przez dodatkowe zapytania.
Poprawna kombinacja tych metod daje duży wzrost wydajności ORM.

</details>

<details>
<summary>55. Jak optymalizować zapytania ORM (annotate, aggregate, F(), Q())?</summary>

#### Django

Optymalizacja zapytań ORM w Django opiera się na zasadzie: przenosić ciężkie
obliczenia do DB i zmniejszać liczbę zapytań oraz ilość pobieranych danych.

#### 1. `annotate()` - obliczenia dla każdego wiersza

- Dodaje „wirtualne” pole do każdego obiektu queryset.
- Przydatne dla liczników, sum, dat ostatniej aktywności itd.

```python
from django.db.models import Count

authors = Author.objects.annotate(books_count=Count("books"))
```

#### 2. `aggregate()` - podsumowanie dla całego queryset

- Zwraca słownik z zagregowanymi wartościami.

```python
from django.db.models import Avg, Sum

stats = Order.objects.aggregate(
    total_revenue=Sum("amount"),
    avg_revenue=Avg("amount"),
)
```

#### 3. `F()` - operacje na polach na poziomie DB

- Pozwala aktualizować wartości bez odczytu obiektu do Pythona.
- Ogranicza race conditions przy współbieżnych aktualizacjach.

```python
from django.db.models import F

Product.objects.filter(pk=product_id).update(stock=F("stock") - 1)
```

#### 4. `Q()` - złożona logika warunków (`AND/OR/NOT`)

- Gdy pojedynczy `filter(a=..., b=...)` nie wystarcza.

```python
from django.db.models import Q

users = User.objects.filter(
    Q(is_active=True) & (Q(role="admin") | Q(role="manager"))
).exclude(Q(email__isnull=True) | Q(email=""))
```

#### Przykład łączony:

```python
from django.db.models import Count, Q

articles = (
    Article.objects
    .filter(is_published=True)
    .annotate(comments_count=Count("comments", filter=Q(comments__is_approved=True)))
    .order_by("-comments_count")
)
```

#### Praktyczne zasady optymalizacji:

1. Licz w DB (`annotate/aggregate`), a nie pętlą w Pythonie.
2. Do masowych aktualizacji używaj `update(..., F(...))`.
3. Dla złożonych warunków używaj `Q`, zamiast wielu osobnych zapytań.
4. Łącz z `select_related/prefetch_related`, aby uniknąć N+1.
5. Pobieraj tylko potrzebne pola (`only`, `values`, `values_list`).

#### Jak sprawdzać efekt:

1. Oglądaj SQL przez `queryset.query` lub `django-debug-toolbar`.
2. Porównuj liczbę zapytań przed/po zmianach.
3. Sprawdzaj execution plan na production DB (`EXPLAIN ANALYZE`).

#### Typowe błędy:

1. Robienie agregacji w Pythonie po `list(qs)` zamiast w SQL.
2. Wywoływanie `save()` w pętli zamiast jednego `update()`.
3. Budowanie zbyt złożonych adnotacji bez indeksów w DB.

#### Wniosek:

`annotate`, `aggregate`, `F`, `Q` to kluczowe narzędzia wydajnego ORM.
Pozwalają zmniejszyć liczbę zapytań, usunąć zbędne obliczenia po stronie
Pythona i utrzymać stabilną pracę DB pod obciążeniem.

</details>

<details>
<summary>56. Jak nadpisać metody save() i delete()?</summary>

#### Django

W Django możesz nadpisywać `save()` i `delete()` w modelu, żeby dodać
logikę przed/po zapisie albo usunięciu rekordu.

#### Jak nadpisać `save()`:

```python
from django.db import models
from django.utils.text import slugify

class Article(models.Model):
    title = models.CharField(max_length=200)
    slug = models.SlugField(unique=True, blank=True)

    def save(self, *args, **kwargs):
        if not self.slug:
            self.slug = slugify(self.title)
        super().save(*args, **kwargs)
```

Kluczowa zasada: zawsze wywołuj `super().save(*args, **kwargs)`.

#### Jak nadpisać `delete()`:

```python
class Document(models.Model):
    file = models.FileField(upload_to="docs/")

    def delete(self, *args, **kwargs):
        storage = self.file.storage
        file_path = self.file.name
        super().delete(*args, **kwargs)
        if file_path:
            storage.delete(file_path)
```

#### Co ważne:

1. `QuerySet.update()` nie wywołuje `save()`.
2. `QuerySet.delete()` nie działa jak ręczne `instance.delete()` dla każdego rekordu.
3. Krytyczne reguły integralności warto wzmacniać też na poziomie DB/serwisów.

#### Wniosek:

Nadpisanie `save()`/`delete()` jest przydatne dla lokalnej logiki modelu,
ale złożoną orkiestrację lepiej trzymać w warstwie serwisowej.

</details>

<details>
<summary>57. Jak działa kaskadowe usuwanie (CASCADE)?</summary>

#### Django

Kaskadowe usuwanie (`models.CASCADE`) oznacza: gdy usuwasz obiekt „rodzica”,
Django automatycznie usuwa powiązane rekordy „dzieci”.

#### Przykład:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

`author.delete()` usunie autora i jego książki.

#### Alternatywy `on_delete`:

1. `PROTECT`
2. `SET_NULL`
3. `SET_DEFAULT`
4. `RESTRICT`
5. `DO_NOTHING`

#### Wniosek:

`CASCADE` jest wygodny, ale „agresywny” — stosuj go tam,
gdzie dane podrzędne nie mają sensu bez nadrzędnych.

</details>

<details>
<summary>58. Jak działają transakcje w Django?</summary>

#### Django

Transakcje gwarantują, że grupa zmian w DB wykona się w całości (`commit`)
albo wcale (`rollback`) przy błędzie.

#### Główne narzędzie:

- `transaction.atomic()`

```python
from django.db import transaction

@transaction.atomic
def create_order(user, items):
    order = Order.objects.create(user=user)
    for item in items:
        OrderItem.objects.create(order=order, product=item["product"], qty=item["qty"])
    return order
```

#### Praktyka:

1. Trzymaj transakcje krótkie.
2. Nie rób zewnętrznych HTTP wywołań wewnątrz transakcji.
3. W konkurencyjnych przypadkach rozważ `select_for_update()`.

#### Wniosek:

`transaction.atomic()` to standard dla krytycznych wielokrokowych operacji.

</details>

<details>
<summary>59. Czy Django wspiera NoSQL?</summary>

#### Django

Krótko: Django jest **SQL-first** (PostgreSQL, MySQL, SQLite, Oracle).
NoSQL da się integrować, ale nie jest to natywny „pierwszy wybór” ORM Django.

#### Praktycznie:

1. Rdzeń domeny zwykle w PostgreSQL.
2. NoSQL dodawany punktowo do specjalnych zadań.
3. Częsty model hybrydowy: SQL + Redis/Elasticsearch.

#### Wniosek:

Django dobrze działa w architekturze hybrydowej,
ale bazowo jest frameworkiem relacyjnym.

</details>

<details>
<summary>60. Jakie typowe wyjątki Django warto znać?</summary>

#### Django

Najczęściej spotykane wyjątki:

1. `Model.DoesNotExist`
2. `Model.MultipleObjectsReturned`
3. `ValidationError`
4. `IntegrityError`
5. `PermissionDenied`
6. `Http404`
7. `ImproperlyConfigured`
8. `OperationalError`

#### Praktyka:

1. Dla web-view używaj `get_object_or_404`.
2. Rozdzielaj błędy użytkownika (4xx) i systemowe (5xx).
3. Nie zwracaj stack trace klientowi w production.

#### Wniosek:

Systematyczna obsługa wyjątków zwiększa stabilność API i przyspiesza diagnostykę.

</details>

<details>
<summary>61. Czym jest Django Admin? Jak zarejestrować model?</summary>

#### Django

`Django Admin` to wbudowany panel administracyjny do zarządzania danymi modeli
przez interfejs webowy bez tworzenia osobnego back-office od zera.

#### Co daje Django Admin:

1. CRUD dla modeli "out of the box".
2. Wyszukiwanie, filtry, sortowanie, paginacja.
3. Praca z powiązanymi obiektami (inlines).
4. Szybki back-office dla zespołu biznesowego.

#### Jak zarejestrować model (minimum):

```python
# app/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

Po tym model pojawi się w `/admin/`.

#### Zalecany wariant przez `ModelAdmin`:

```python
from django.contrib import admin
from .models import Article

@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    list_display = ("id", "title", "is_published", "created_at")
    list_filter = ("is_published", "created_at")
    search_fields = ("title",)
    ordering = ("-created_at",)
```

#### Wymagania wstępne do logowania do panelu admina:

1. Zastosowane migracje:

```bash
python manage.py migrate
```

2. Utworzony superuser:

```bash
python manage.py createsuperuser
```

3. Uruchomiony serwer i otwarte `/admin/`.

#### Praktyczne rekomendacje:

1. Konfiguruj `list_display`, `search_fields`, `list_filter` dla kluczowych
   modeli.
2. Ograniczaj dostęp do admina przez role/uprawnienia.
3. Dla dużych tabel optymalizuj queryset w `ModelAdmin`
   (`select_related`/`prefetch_related`).
4. Nie używaj admina jako publicznego interfejsu dla użytkowników końcowych.

#### Wniosek:

Django Admin to potężne narzędzie do wewnętrznego zarządzania danymi.
Rejestracja modelu zajmuje minuty, a z podstawowym `ModelAdmin` panel szybko
staje się produktywnym back-office dla zespołu.

</details>

<details>
<summary>62. Czym jest superuser?</summary>

#### Django

`Superuser` w Django to użytkownik z maksymalnymi uprawnieniami
administracyjnymi w systemie, zwykle do dostępu do Django Admin i pełnego
zarządzania danymi.

#### Kluczowe cechy superusera:

1. `is_superuser = True`
2. `is_staff = True`
3. Ma wszystkie uprawnienia bez potrzeby osobnego przypisywania każdego
   pozwolenia.
4. Może zarządzać użytkownikami, grupami, modelami i treścią przez `/admin/`.

#### Jak utworzyć superusera:

```bash
python manage.py createsuperuser
```

Dalej Django poprosi o:

- username
- email (zależnie od modelu)
- password

#### Gdzie jest używany:

1. Początkowa administracja projektem.
2. Konfiguracja ról/grup i dostępów.
3. Wsparcie operacyjne przez Django Admin.

#### Ważne uwagi bezpieczeństwa:

1. Nie używaj konta superusera do codziennej pracy operacyjnej.
2. Liczba superuserów na produkcji powinna być minimalna.
3. Używaj silnych haseł + 2FA (jeśli dostępne przez SSO/rozwiązania admin).
4. Loguj działania administratora i kontroluj dostęp przez IP/VPN.
5. Nie twórz "tymczasowych" superuserów bez procesu ich usuwania.

#### Praktyczna rola w zespole:

- Superuser jest potrzebny na etapie bootstrapu.
- W stabilnym procesie większość zadań lepiej wykonywać przez `staff` + grupy +
  granularne uprawnienia, a nie przez pełny dostęp.

#### Wniosek:

Superuser to "root-user" w Django. To narzędzie krytycznie ważne dla
administracji, ale dostęp do niego powinien być maksymalnie ograniczony i
kontrolowany.

</details>

<details>
<summary>63. Jak dostosować Django Admin?</summary>

#### Django

Dostosowanie Django Admin wykonuje się przez klasę `ModelAdmin` i powiązane
mechanizmy (inlines, actions, permissions, form overrides). Pozwala to
zamienić podstawowy panel admina w efektywne narzędzie back-office.

#### Podstawowa personalizacja `ModelAdmin`:

```python
from django.contrib import admin
from .models import Order

@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    list_display = ("id", "user", "status", "total", "created_at")
    list_filter = ("status", "created_at")
    search_fields = ("id", "user__email")
    ordering = ("-created_at",)
    list_per_page = 50
```

#### Najczęściej używane narzędzia:

1. `list_display` - które kolumny są widoczne na liście.
2. `list_filter` - filtry po prawej stronie.
3. `search_fields` - wyszukiwanie po polach/relacjach.
4. `readonly_fields` - pola tylko do odczytu.
5. `fieldsets` - grupowanie pól w formularzu edycji.
6. `actions` - działania masowe na wybranych rekordach.

#### Edycja inline powiązanych modeli:

```python
class OrderItemInline(admin.TabularInline):
    model = OrderItem
    extra = 0

@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    inlines = [OrderItemInline]
```

#### Własne actions:

```python
@admin.action(description="Oznaczyć jako opublikowane")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)
```

#### Ograniczenia dostępu:

- `has_view_permission`, `has_change_permission`, `has_delete_permission`
- `get_queryset()` do data-scopingu (np. menedżer widzi tylko swoje obiekty).

#### Optymalizacja wydajności panelu admina:

1. Używaj `list_select_related` dla FK w `list_display`.
2. Uważaj z `search_fields` na dużych tabelach (indeksy są obowiązkowe).
3. Ograniczaj "ciężkie" obliczenia w widoku listy.
4. Dla bardzo dużych słowników używaj `autocomplete_fields`.

#### Dodatkowa personalizacja:

- Nadpisanie `form`/`get_form`.
- Nadpisanie `save_model`/`delete_model`.
- Własne szablony admina dla specyficznego UI.

#### Wniosek:

Django Admin dobrze skaluje się przez `ModelAdmin`: od prostej rejestracji po
pełnowartościowy panel wewnętrzny z rolami, filtrami, akcjami masowymi i
kontrolowaną wydajnością.

</details>

<details>
<summary>64. Jakie są komponenty Django Admin i ustawienia indywidualne?</summary>

#### Django

Django Admin składa się z kilku kluczowych komponentów, które można elastycznie
dostosować pod procesy biznesowe zespołu: lista obiektów, formularz edycji,
filtry, wyszukiwanie, działania, prawa dostępu, inlines i globalna konfiguracja
admin site.

#### Główne komponenty Django Admin:

1. **Admin Site (`admin.site`)**

- Globalny panel administracyjny, można dostosować jego header/title/index.

2. **`ModelAdmin`**

- Konfiguracja prezentacji konkretnego modelu w adminie.

3. **Change List**

- Strona listy obiektów (`list_display`, `list_filter`, `search_fields`).

4. **Change Form**

- Formularz tworzenia/edycji (`fields`, `fieldsets`, `readonly_fields`).

5. **Inlines**

- Edycja powiązanych modeli na jednej stronie.

6. **Actions**

- Operacje masowe na wybranych rekordach.

7. **Permissions**

- Dostęp do podglądu/edycji/usuwania według ról.

#### Przykład ustawień indywidualnych:

```python
from django.contrib import admin
from .models import Customer

@admin.register(Customer)
class CustomerAdmin(admin.ModelAdmin):
    list_display = ("id", "email", "is_active", "created_at")
    list_filter = ("is_active", "created_at")
    search_fields = ("email", "first_name", "last_name")
    readonly_fields = ("created_at", "updated_at")
    fieldsets = (
        ("Podstawowe", {"fields": ("email", "first_name", "last_name")}),
        ("Status", {"fields": ("is_active",)}),
        ("Serwisowe", {"fields": ("created_at", "updated_at")}),
    )
```

#### Globalne ustawienia admin site:

```python
from django.contrib import admin

admin.site.site_header = "Admin Panel"
admin.site.site_title = "Backoffice"
admin.site.index_title = "Zarządzanie systemem"
```

#### Indywidualne zachowanie zależnie od ról:

- `get_queryset()` - ogranicza, co widzi dany użytkownik `staff`.
- `get_readonly_fields()` - ustawia część pól jako read-only zależnie od roli.
- `has_change_permission()` / `has_delete_permission()` - granularna kontrola
  uprawnień.

#### Komponenty często dodawane na produkcji:

1. `autocomplete_fields` dla ciężkich pól FK.
2. `list_select_related` do optymalizacji list-view.
3. Własne `form` i `formfield_overrides` dla lepszego UX.
4. Własne templates dla specyficznych scenariuszy back-office.

#### Wniosek:

Siła Django Admin polega na tym, że z bazowych komponentów można zbudować
zarządzalny wewnętrzny interfejs pod konkretne procesy zespołu: szybki,
bezpieczny i operacyjnie wygodny.

</details>

<details>
<summary>65. Czym są Django Admin actions i ich personalizacja?</summary>

#### Django

`Admin actions` w Django to operacje masowe na wybranych obiektach na liście
admina. Pozwalają szybko wykonywać typowe działania bez ręcznej edycji każdego
rekordu.

#### Czym jest action:

- Funkcja lub metoda, która przyjmuje: `modeladmin`, `request`, `queryset`.
- Wywoływana dla zestawu obiektów zaznaczonych przez użytkownika admina.

#### Podstawowy przykład action:

```python
from django.contrib import admin
from .models import Article

@admin.action(description="Opublikować wybrane artykuły")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)

@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    list_display = ("id", "title", "is_published")
    actions = [make_published]
```

#### Przykład action jako metody `ModelAdmin`:

```python
@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    actions = ["mark_as_paid"]

    @admin.action(description="Oznaczyć jako opłacone")
    def mark_as_paid(self, request, queryset):
        updated = queryset.update(status="paid")
        self.message_user(request, f"Zaktualizowano zamówień: {updated}")
```

#### Personalizacja actions:

1. Własny `description` dla UI.
2. Warunki dostępności akcji zależnie od roli/stanu.
3. Zwrot strony pośredniej potwierdzenia (custom admin view).
4. Logowanie wykonanych działań masowych.

#### Praktyczne rekomendacje:

1. Dla zmian masowych preferuj `queryset.update()` (szybciej, mniej SQL).
2. Jeśli potrzebna jest logika biznesowa per obiekt, iteruj ostrożnie w
   transakcji.
3. Pokazuj podsumowanie przez `message_user`.
4. Ograniczaj niebezpieczne actions dla ról nieadministracyjnych.

#### Ważne niuanse:

1. `queryset.update()` nie wywołuje `save()` i sygnałów `post_save`.
2. Masowe usuwanie przez standardową akcję może być ryzykowne bez dodatkowej
   kontroli.
3. Dla krytycznych operacji warto dodawać krok potwierdzenia.

#### Typowe przypadki użycia actions:

- Publish/Unpublish treści.
- Batchowe nadawanie statusu.
- Eksport wybranych rekordów do CSV.
- Uruchamianie przetwarzania w tle dla selected IDs.

#### Wniosek:

Admin actions to szybkie narzędzie automatyzacji operacyjnej w Django Admin.
Przy poprawnej personalizacji istotnie przyspieszają pracę zespołu i zmniejszają
liczbę ręcznych, rutynowych działań.

</details>

<details>
<summary>66. Czym jest middleware i jak działa?</summary>

#### Django

`Middleware` w Django to warstwa przetwarzania między żądaniem/odpowiedzią HTTP
a view. Pozwala wykonać kod **przed** trafieniem żądania do view oraz **po**
utworzeniu odpowiedzi.

#### Jak działa pipeline middleware:

1. Żądanie trafia do Django.
2. Przechodzi kolejno przez middleware (request phase).
3. Trafia do URL resolvera i view.
4. Odpowiedź wraca przez middleware w odwrotnej kolejności (response phase).
5. Odpowiedź jest wysyłana do klienta.

#### Ważny detal:

- Kolejność middleware w `settings.py` (`MIDDLEWARE = [...]`) jest krytyczna.
- Middleware z góry listy widzą żądanie jako pierwsze, a odpowiedź jako ostatnie.

#### Typowe zadania middleware:

1. Bezpieczeństwo (security headers, host checks).
2. Sesje i uwierzytelnianie.
3. Ochrona CSRF.
4. Lokalizacja (locale/language).
5. Logowanie, request-id, metryki.
6. Cache na poziomie request/response.

#### Szkielet middleware:

```python
class SimpleMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # przed view
        response = self.get_response(request)
        # po view
        return response
```

#### Gdzie jest podłączane:

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    # ...
]
```

#### Praktyczne zasady:

1. Utrzymuj middleware lekkie i szybkie.
2. Nie umieszczaj tam ciężkiej logiki biznesowej domeny.
3. Unikaj wolnych zewnętrznych wywołań w middleware.
4. Uważnie kontroluj kolejność middleware na liście.

#### Typowe błędy:

1. Zbyt "sprytne" middleware ze skutkami ubocznymi.
2. Nieprawidłowa kolejność, która psuje flow auth/csrf/session.
3. Duplikacja logiki między middleware i view.

#### Wniosek:

Middleware to globalny interceptor żądań/odpowiedzi w Django. Jego siłą są
scentralizowane zadania cross-cutting (bezpieczeństwo, sesje, logowanie), a nie
logika biznesowa konkretnych endpointów.

</details>

<details>
<summary>67. Jakie są wbudowane middleware?</summary>

#### Django

Django ma zestaw wbudowanych middleware, które pokrywają podstawowe potrzeby
aplikacji webowej: bezpieczeństwo, sesje, uwierzytelnianie, CSRF, cache,
lokalizację.

#### Najczęściej używane built-in middleware:

1. **`django.middleware.security.SecurityMiddleware`**

- Security headers, ustawienia HTTPS i bazowe mechanizmy ochrony.

2. **`django.contrib.sessions.middleware.SessionMiddleware`**

- Obsługa serwerowych sesji użytkownika.

3. **`django.middleware.common.CommonMiddleware`**

- Ogólne zachowania HTTP (np. `APPEND_SLASH`, `PREPEND_WWW`).

4. **`django.middleware.csrf.CsrfViewMiddleware`**

- Ochrona przed atakami CSRF dla żądań zmieniających stan.

5. **`django.contrib.auth.middleware.AuthenticationMiddleware`**

- Dodaje `request.user` i integruje system auth z flow żądania.

6. **`django.contrib.messages.middleware.MessageMiddleware`**

- Obsługa flash messages (`messages.success`, `messages.error`).

7. **`django.middleware.clickjacking.XFrameOptionsMiddleware`**

- Ochrona przed clickjacking przez nagłówek `X-Frame-Options`.

8. **`django.middleware.locale.LocaleMiddleware`**

- Ustalanie języka/lokali dla i18n.

9. **`django.middleware.gzip.GZipMiddleware`**

- Kompresja odpowiedzi (ostrożnie z już skompresowaną treścią).

10. **`django.middleware.cache.UpdateCacheMiddleware` /
    `FetchFromCacheMiddleware`**

- Site-wide cache na poziomie middleware.

#### Typowa kolejność w `MIDDLEWARE` (skrót):

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    "django.middleware.csrf.CsrfViewMiddleware",
    "django.contrib.auth.middleware.AuthenticationMiddleware",
    "django.contrib.messages.middleware.MessageMiddleware",
    "django.middleware.clickjacking.XFrameOptionsMiddleware",
]
```

#### Praktyczne uwagi:

1. Kolejność middleware ma znaczenie i wpływa na działanie całej aplikacji.
2. Nie usuwaj bez zrozumienia skutków `SecurityMiddleware`,
   `CsrfViewMiddleware`, `AuthenticationMiddleware`.
3. Dla production sprawdzaj nagłówki bezpieczeństwa i cache-policy po zmianach
   middleware.

#### Wniosek:

Wbudowane middleware Django pokrywają większość potrzeb infrastrukturalnych "out
of the box". Poprawny zestaw i kolejność middleware bezpośrednio wpływają na
bezpieczeństwo, stabilność i zachowanie aplikacji na produkcji.

</details>

<details>
<summary>68. Jak utworzyć własne middleware?</summary>

#### Django

Własne middleware w Django tworzy się jako klasę, która przyjmuje
`get_response` i przechwytuje `request/response` w globalnym pipeline
przetwarzania.

#### Minimalny szablon middleware:

```python
# app/middleware.py
class RequestIdMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # logika przed view
        response = self.get_response(request)
        # logika po view
        return response
```

#### Przykład z request-id:

```python
import uuid

class RequestIdMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        request.request_id = str(uuid.uuid4())
        response = self.get_response(request)
        response["X-Request-ID"] = request.request_id
        return response
```

#### Podłączenie w `settings.py`:

```python
MIDDLEWARE = [
    # ...
    "app.middleware.RequestIdMiddleware",
]
```

#### Gdzie umieszczać na liście:

1. Middleware bezpieczeństwa/sesji zwykle wyżej.
2. Custom logging/request-id często po bazowych middleware security/session.
3. Kolejność jest ważna: wpływa na to, co middleware widzi w `request`.

#### Co można robić w middleware:

- Dodawać nagłówki.
- Logować żądanie/odpowiedź.
- Dodawać kontekst tracingu.
- Odrzucać żądanie według globalnych reguł.

#### Czego nie robić:

1. Złożona logika biznesowa konkretnego endpointu.
2. Wolne zewnętrzne wywołania HTTP.
3. Ciężkie operacje blokujące każde żądanie.

#### Wniosek:

Custom middleware to narzędzie do zadań cross-cutting na poziomie całej
aplikacji. Powinno być lekkie, przewidywalne i poprawnie ustawione w
`MIDDLEWARE`, aby uniknąć efektów ubocznych.

</details>

<details>
<summary>69. Czym są signals i kiedy ich używać?</summary>

#### Django

`Signals` w Django to mechanizm zdarzeń, który pozwala uruchamiać kod w
odpowiedzi na określone akcje (np. zapis lub usunięcie modelu) bez bezpośredniego
wywołania tej logiki w view lub serwisie.

#### Jak to działa:

1. Występuje zdarzenie (signal), np. `post_save`.
2. Funkcja receiver, subskrybująca zdarzenie, wykonuje się automatycznie.

#### Najczęściej używane sygnały:

1. `pre_save`, `post_save`
2. `pre_delete`, `post_delete`
3. `m2m_changed`
4. `request_started`, `request_finished` (rzadziej dla logiki aplikacji)

#### Przykład `post_save`:

```python
# app/signals.py
from django.db.models.signals import post_save
from django.dispatch import receiver
from django.contrib.auth import get_user_model
from .models import Profile

User = get_user_model()

@receiver(post_save, sender=User)
def create_profile(sender, instance, created, **kwargs):
    if created:
        Profile.objects.create(user=instance)
```

Import/rejestracja w `apps.py`:

```python
from django.apps import AppConfig

class UsersConfig(AppConfig):
    name = "users"

    def ready(self):
        import users.signals  # noqa
```

#### Kiedy signals są zasadne:

1. Słabo sprzężone skutki uboczne (np. utworzenie profilu po utworzeniu
   użytkownika).
2. Techniczne hooki, które nie powinny komplikować view.
3. Zdarzenia, gdzie ważne jest rozdzielenie modułów.

#### Kiedy lepiej nie używać:

1. Krytyczna logika biznesowa wymagająca jawnej sekwencji kroków.
2. Złożona orkiestracja między kilkoma serwisami.
3. Logika, która powinna być przejrzysta w jednym jawnym use-case.

#### Typowe problemy signals:

1. "Magia" i nieoczekiwane skutki uboczne.
2. Trudny debugging w dużych projektach.
3. Podwójne wywołania przy nieuważnej rejestracji.
4. Trudno kontrolować kolejność wielu receiverów.

#### Praktyczne zasady:

1. Signals powinny być krótkie i szybkie.
2. Długie/ciężkie zadania wysyłaj do kolejki (Celery/RQ).
3. Dokumentuj, na jakie zdarzenia subskrybuje moduł.
4. Nie ukrywaj głównej logiki biznesowej transakcji w signal.

#### Wniosek:

Signals w Django są przydatne dla umiarkowanych zdarzeń ubocznych i luźnego
sprzęgania modułów. Dla core-procesów biznesowych zwykle pewniejsza jest jawna
warstwa serwisowa, gdzie flow jest widoczny wprost w kodzie.

</details>

<details>
<summary>70. Różnica między signals a middleware.</summary>

#### Django

`Middleware` i `signals` rozwiązują różne problemy, mimo że oba wyglądają jak
"miejsce na dodatkową logikę". Kluczowa różnica to **poziom zdarzeń**, na
którym działają.

#### Middleware:

1. Działa na poziomie **HTTP request/response**.
2. Wykonuje się dla każdego żądania w globalnym pipeline.
3. Służy do cross-cutting zadań webowych.

Typowe przypadki:

- security headers
- auth/session flow
- logging/tracing/request-id
- locale/caching/compression

#### Signals:

1. Działają na poziomie **zdarzeń modeli/frameworka**.
2. Wywołują się przy akcjach typu `post_save`, `post_delete`, `m2m_changed`.
3. Służą do reakcji na zdarzenia modelu domenowego.

Typowe przypadki:

- utworzenie profilu po utworzeniu użytkownika
- synchronizacja encji pomocniczych
- lightweight hooks po zmianach danych

#### Główna różnica:

- Middleware odpowiadają na request/response.
- Signals odpowiadają na zdarzenia danych/modeli.

#### Kiedy co wybrać:

1. Potrzebne globalne zachowanie HTTP -> **middleware**.
2. Potrzebna reakcja na zmianę modelu -> **signals**.
3. Potrzebna jawna kontrola business-flow -> **warstwa serwisowa**, nie
   signals/middleware.

#### Tabela porównawcza:

| Kryterium       | Middleware                 | Signals                  |
| --------------- | -------------------------- | ------------------------ |
| Poziom          | HTTP pipeline              | Model/framework events   |
| Punkt uruchomień| Przed/po view              | Przed/po save/delete itp.|
| Przejrzystość   | Wyższa (przez `MIDDLEWARE`)| Niższa (możliwa "magia")|
| Typ zadań       | Infrastrukturalne          | Zdarzeniowe skutki uboczne |

#### Typowe błędy:

1. Umieszczanie logiki biznesowej modelu w middleware.
2. Ukrywanie krytycznego business-flow w signals bez jawnej orkiestracji.
3. Duplikowanie tej samej logiki w obu warstwach.

#### Wniosek:

Middleware służy do infrastruktury HTTP, a signals do reakcji na zdarzenia
modeli. Dla ważnej logiki biznesowej lepsze są jawne serwisy: są
najbardziej przejrzyste, najlepiej testowalne i najmniej podatne na ukryte
skutki uboczne.

</details>

<details>
<summary>71. Jak działa system uwierzytelniania i autoryzacji?</summary>

#### Django

W Django system dostępu składa się z dwóch części:

1. **Uwierzytelnianie (authentication)** - kim jesteś?
2. **Autoryzacja (authorization)** - co wolno Ci zrobić?

#### Jak działa uwierzytelnianie:

1. Użytkownik wysyła login i hasło.
2. Django sprawdza dane przez `authenticate()`.
3. Jeśli sukces - wywoływane jest `login()`, tworzona jest sesja.
4. W kolejnych żądaniach `AuthenticationMiddleware` dodaje `request.user`.

Podstawowy przykład:

```python
from django.contrib.auth import authenticate, login

user = authenticate(request, username=username, password=password)
if user is not None:
    login(request, user)
```

#### Jak działa autoryzacja:

- Django sprawdza uprawnienia użytkownika przez permissions, grupy i reguły
  role-based.
- Bazowe permissions dla modeli: `add`, `change`, `delete`, `view`.

Sprawdzenie uprawnienia:

```python
if request.user.has_perm("orders.change_order"):
    ...
```

#### Narzędzia kontroli dostępu:

1. `@login_required` - dostęp tylko dla zalogowanych.
2. `@permission_required("app.perm_codename")`
3. `LoginRequiredMixin`, `PermissionRequiredMixin` dla CBV.
4. Grupy (`Group`) do role-based zarządzania zestawami permissions.

#### Model sesyjny (domyślnie):

- Po `login()` Django tworzy sesję w DB/cache.
- Identyfikator sesji jest zapisywany w cookie.
- Przy każdym żądaniu użytkownik jest identyfikowany przez tę sesję.

#### Gdzie to się konfiguruje:

- `AUTHENTICATION_BACKENDS`
- `LOGIN_URL`, `LOGIN_REDIRECT_URL`, `LOGOUT_REDIRECT_URL`
- `AUTH_USER_MODEL` (jeśli model użytkownika jest custom)

#### Praktyczne rekomendacje:

1. Nie sprawdzaj dostępu tylko na froncie - backend musi być źródłem prawdy.
2. Grupuj uprawnienia wg ról, zamiast nadawać je indywidualnie każdemu.
3. Dla API osobno zaplanuj token/session auth i policy dostępu.
4. Loguj wrażliwe akcje administracyjne do audytu.

#### Wniosek:

W Django uwierzytelnianie odpowiada za identyfikację użytkownika, a autoryzacja
za jego uprawnienia. Razem tworzą bezpieczny i skalowalny model dostępu dla
aplikacji web i API.

</details>

<details>
<summary>72. Jak zaimplementować rejestrację użytkowników?</summary>

#### Django

Rejestracja użytkowników w Django zwykle składa się z formularza, logiki view,
utworzenia użytkownika z hashowanym hasłem i (opcjonalnie) automatycznego
logowania.

#### Podejście bazowe:

1. Utworzyć formularz rejestracji (`UserCreationForm` lub custom).
2. Obsłużyć formularz w view (`GET`/`POST`).
3. Zapisać użytkownika.
4. Przekierować na login albo wykonać autologowanie.

#### Przykład formularza:

```python
# users/forms.py
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth import get_user_model

User = get_user_model()

class SignUpForm(UserCreationForm):
    class Meta(UserCreationForm.Meta):
        model = User
        fields = ("username", "email")
```

#### Przykład view:

```python
# users/views.py
from django.contrib.auth import login
from django.shortcuts import redirect, render
from .forms import SignUpForm

def signup_view(request):
    if request.method == "POST":
        form = SignUpForm(request.POST)
        if form.is_valid():
            user = form.save()  # hasło hashuje się automatycznie
            login(request, user)  # opcjonalnie: logowanie od razu
            return redirect("home")
    else:
        form = SignUpForm()
    return render(request, "users/signup.html", {"form": form})
```

#### Szablon:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Zarejestruj się</button>
</form>
```

#### URL:

```python
path("signup/", signup_view, name="signup")
```

#### Ważne zasady bezpieczeństwa:

1. Nigdy nie zapisuj hasła ręcznie jako plain text.
2. Używaj `UserCreationForm` albo `set_password()`.
3. Dodaj ochronę przed brute force (rate limiting / captcha, gdzie potrzeba).
4. Dla production warto mieć potwierdzenie email przed aktywacją konta.

#### Rozszerzenia rejestracji:

1. Profil użytkownika (przez `OneToOne`).
2. Potwierdzenie email tokenem.
3. Social login (Google/GitHub) przez allauth.
4. Audit log zdarzeń rejestracji.

#### Wniosek:

W Django rejestrację wdraża się szybko przez wbudowane formularze auth i flow
view. Kluczowe są: poprawna obsługa haseł, ochrona CSRF i przemyślany proces
aktywacji kont w production.

</details>

<details>
<summary>73. Jak utworzyć własny model użytkownika?</summary>

#### Django

Własny model użytkownika w Django tworzy się, gdy standardowy `User` nie
wystarcza (np. potrzebny email jako login, dodatkowe obowiązkowe pola,
niestandardowa logika identyfikacji).

#### Kluczowa zasada:

`AUTH_USER_MODEL` trzeba zdefiniować **na początku projektu**, przed pierwszymi
migracjami. Późniejsza zmiana jest kosztowna i ryzykowna.

#### Wariant 1 (zalecany w 90% przypadków): `AbstractUser`

- Dziedziczysz wbudowanego użytkownika i dodajesz własne pola.
- Najprostsza i najstabilniejsza ścieżka.

```python
# users/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    phone = models.CharField(max_length=30, blank=True)
    timezone = models.CharField(max_length=64, blank=True, default="UTC")
```

W `settings.py`:

```python
AUTH_USER_MODEL = "users.User"
```

#### Wariant 2: `AbstractBaseUser` + `PermissionsMixin`

- Pełna kontrola nad modelem i polem logowania.
- Znacznie trudniejszy: potrzebny custom `UserManager`, `USERNAME_FIELD`,
  `REQUIRED_FIELDS`, zgodność z admin/forms/auth flow.

Używaj tylko wtedy, gdy faktycznie potrzebujesz niestandardowego modelu auth.

#### Przykład odwołania do custom użytkownika w modelach:

```python
from django.conf import settings

class Order(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
```

#### W kodzie zamiast bezpośredniego importu `User`:

```python
from django.contrib.auth import get_user_model
User = get_user_model()
```

#### Praktyczne rekomendacje:

1. Jeśli nie jesteś pewien - od razu twórz custom model przez `AbstractUser`.
2. Nie używaj `from django.contrib.auth.models import User` w kodzie domenowym.
3. Upewnij się, że forms/admin/auth backend działają z Twoim modelem.
4. Pokryj testami rejestrację, login, reset hasła i permissions.

#### Typowe błędy:

1. Próba zmiany modelu użytkownika po starcie projektu na production.
2. Twardy import standardowego `User` w modelach i migracjach.
3. Użycie `AbstractBaseUser` bez realnej potrzeby i pełnej konfiguracji.

#### Wniosek:

Poprawny custom model użytkownika w Django to decyzja strategiczna na starcie.
Najbezpieczniejsza droga: `AbstractUser` + `AUTH_USER_MODEL` + dyscyplina użycia
`get_user_model()` i `settings.AUTH_USER_MODEL` w całym projekcie.

</details>

<details>
<summary>74. Do czego służy login_required?</summary>

#### Django

`login_required` to dekorator, który ogranicza dostęp do view wyłącznie dla
zalogowanych użytkowników.

#### Jak działa:

1. Jeśli użytkownik jest zalogowany -> view jest wykonywany.
2. Jeśli nie -> przekierowanie na stronę logowania (`LOGIN_URL`) z parametrem
   `next`.

#### Przykład dla FBV:

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, "dashboard.html")
```

#### Niestandardowy login URL:

```python
@login_required(login_url="/auth/login/")
def billing_page(request):
    ...
```

#### Odpowiednik dla CBV:

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import TemplateView

class DashboardView(LoginRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Konfiguracja w `settings.py`:

```python
LOGIN_URL = "login"
LOGIN_REDIRECT_URL = "home"
```

#### Do czego się go używa:

1. Ochrona prywatnych stron (konto, zamówienia, ustawienia profilu).
2. Bazowa kontrola dostępu w sekcjach typu admin-like.
3. Zapobieganie nieautoryzowanym akcjom POST.

#### Czego `login_required` NIE robi:

1. Nie sprawdza ról/permissions (tylko fakt zalogowania).
2. Nie zastępuje szczegółowej kontroli autoryzacji.

Do uprawnień używaj:

- `permission_required`
- `user_passes_test`
- `PermissionRequiredMixin`

#### Praktyczne wskazówki:

1. Ustawiaj `login_required` na wszystkich prywatnych endpointach domyślnie.
2. Nie polegaj wyłącznie na ukrywaniu przycisków na froncie.
3. Sprawdzaj, że redirect `next` jest bezpieczny (Django obsługuje to
   standardowo).

#### Wniosek:

`login_required` to bazowa i obowiązkowa ochrona prywatnych view w Django.
Rozwiązuje pytanie "czy użytkownik jest zalogowany", a szczegółowe prawa dostępu
trzeba budować dodatkowymi mechanizmami autoryzacji.

</details>

<details>
<summary>75. Jak działają sesje i cookies?</summary>

#### Django

W Django sesje i cookies służą do przechowywania stanu między żądaniami, bo HTTP
samo w sobie jest stateless.

#### Czym są cookies:

- Małe dane, które przeglądarka przechowuje po stronie klienta.
- Są odsyłane do serwera w każdym kolejnym żądaniu do tej samej domeny.
- Często zawierają session ID, a nie same dane wrażliwe.

#### Czym jest sesja:

- Serwerowe przechowywanie danych użytkownika (w DB/cache/plikach).
- Przeglądarka trzyma tylko klucz sesji w cookie.
- Przez `request.session` Django odczytuje/aktualizuje dane sesji.

#### Jak działają razem:

1. Po logowaniu Django tworzy sesję na serwerze.
2. Session key zapisywany jest w cookie (`sessionid`).
3. Przy każdym żądaniu Django czyta cookie i odtwarza sesję.

#### Przykład pracy z sesją:

```python
def set_theme(request):
    request.session["theme"] = "dark"
    return HttpResponse("ok")

def get_theme(request):
    theme = request.session.get("theme", "light")
    return HttpResponse(theme)
```

#### Przykład jawnego cookie:

```python
response = HttpResponse("ok")
response.set_cookie("promo_seen", "1", max_age=3600)
```

#### Gdzie są przechowywane sesje w Django:

- Domyślnie: w DB (`django.contrib.sessions`).
- Można zmienić backend na cache, file, signed cookies.

#### Ważne ustawienia bezpieczeństwa:

1. `SESSION_COOKIE_HTTPONLY = True` (ochrona przed dostępem JS do cookie).
2. `SESSION_COOKIE_SECURE = True` (tylko przez HTTPS).
3. `SESSION_COOKIE_SAMESITE = "Lax"` albo `"Strict"` zależnie od potrzeb.
4. Analogicznie dla cookie CSRF (`CSRF_COOKIE_SECURE`, `CSRF_COOKIE_HTTPONLY`).

#### Praktyczne rekomendacje:

1. Nie przechowuj danych wrażliwych bezpośrednio w cookie.
2. Minimalizuj ilość danych w sesji.
3. Do skalowania używaj sesji opartych o Redis.
4. Czyść/unieważniaj sesję przy logout i krytycznych zmianach konta.

#### Wniosek:

Cookies to mechanizm kliencki do przekazywania małych danych, a sesje to
serwerowe przechowywanie stanu użytkownika. W Django działają razem i stanowią
podstawę klasycznego auth-flow oraz spersonalizowanego UX.

</details>

<details>
<summary>76. Czym są grupy i uprawnienia oraz jak wdrożyć model dostępu oparty na rolach?</summary>

#### Django

W Django **permissions** (uprawnienia) i **groups** (grupy) to bazowe mechanizmy
autoryzacji do realizacji RBAC (Role-Based Access Control).

#### Czym są uprawnienia (permissions):

- To prawa typu `app_label.codename`, np. `orders.view_order`,
  `orders.change_order`.
- Django automatycznie tworzy bazowe uprawnienia modeli: `add`, `change`,
  `delete`, `view`.
- Można dodawać własne (custom permissions) w `Meta`.

#### Czym są grupy (groups):

- Grupa = rola, której przypisuje się zestaw permissions.
- Użytkownika dodaje się do grupy i dziedziczy on prawa tej roli.

#### Przykład custom permission w modelu:

```python
class Order(models.Model):
    ...
    class Meta:
        permissions = [
            ("approve_order", "Can approve order"),
        ]
```

#### Sprawdzenie dostępu w kodzie:

```python
if request.user.has_perm("orders.approve_order"):
    ...
```

Dekorator:

```python
from django.contrib.auth.decorators import permission_required

@permission_required("orders.approve_order", raise_exception=True)
def approve_view(request, order_id):
    ...
```

#### Przykład ról (RBAC):

1. **viewer** -> tylko `view_*`
2. **manager** -> `view_*`, `change_*`, `approve_order`
3. **admin** -> pełny zestaw dostępów domeny

#### Typowy proces wdrożenia RBAC:

1. Opisać role i ich odpowiedzialności.
2. Zdefiniować mapowanie "rola -> permissions".
3. Utworzyć grupy i przypisać permissions.
4. Dodawać użytkowników do grup (przez admin lub skrypty seed).
5. Sprawdzać permissions w view/CBV/API.

#### Praktyczne rekomendacje:

1. Nadawaj prawa przez role (groups), nie ręcznie per użytkownik.
2. Utrzymuj policy dostępu centralnie i w dokumentacji.
3. Sprawdzaj dostęp na backendzie, nawet jeśli UI ukrywa przyciski.
4. Dla złożonych przypadków dodawaj object-level permissions (gdy trzeba).

#### Typowe błędy:

1. Nadawanie `is_superuser`, gdy wystarczą role-permissions.
2. Mieszanie ról i stanów biznesowych bez jasnych reguł.
3. Rozdawanie "tymczasowych" praw bez audytu i terminu wygaśnięcia.

#### Wniosek:

Grupy i uprawnienia w Django to solidna podstawa modelu dostępu opartego na
rolach. RBAC przez groups czyni system bezpieczniejszym, bardziej przejrzystym i
łatwiejszym w utrzymaniu przy skalowaniu zespołu oraz produktu.

</details>

<details>
<summary>77. Jak zaimplementować odzyskiwanie hasła?</summary>

#### Django

Odzyskiwanie hasła w Django najłatwiej wdrożyć przez wbudowane auth-views: mają
już bezpieczny flow z jednorazowym tokenem i kontrolą czasu ważności.

#### Standardowy flow:

1. Użytkownik wpisuje email na stronie "Nie pamiętasz hasła".
2. Django wysyła email z linkiem (uid + token).
3. Użytkownik przechodzi pod link i ustawia nowe hasło.
4. Django potwierdza udaną zmianę.

#### Konfiguracja URL:

```python
from django.urls import path
from django.contrib.auth import views as auth_views

urlpatterns = [
    path("password-reset/", auth_views.PasswordResetView.as_view(), name="password_reset"),
    path("password-reset/done/", auth_views.PasswordResetDoneView.as_view(), name="password_reset_done"),
    path(
        "reset/<uidb64>/<token>/",
        auth_views.PasswordResetConfirmView.as_view(),
        name="password_reset_confirm",
    ),
    path("reset/done/", auth_views.PasswordResetCompleteView.as_view(), name="password_reset_complete"),
]
```

#### Wymagane szablony:

- `registration/password_reset_form.html`
- `registration/password_reset_done.html`
- `registration/password_reset_confirm.html`
- `registration/password_reset_complete.html`
- szablon email, np. `registration/password_reset_email.html`

#### Bazowe ustawienia email:

```python
EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "smtp.example.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "..."
EMAIL_HOST_PASSWORD = "..."
DEFAULT_FROM_EMAIL = "noreply@example.com"
```

#### Ważne zasady bezpieczeństwa:

1. Nie ujawniaj, czy email istnieje w systemie (ochrona przed user enumeration).
2. Używaj HTTPS dla linków resetu.
3. Ograniczaj częstotliwość żądań resetu (rate limiting).
4. Po zmianie hasła unieważniaj aktywne sesje zgodnie z polityką.
5. Loguj zdarzenia odzyskiwania hasła do audytu.

#### Kiedy potrzebna jest customizacja:

- Własny design emaili/stron.
- Custom model użytkownika z loginem po email.
- Integracja z zewnętrznym auth/SSO.

#### Wniosek:

Django daje gotowy, bezpieczny mechanizm odzyskiwania hasła przez standardowe
auth-views. W production wystarczy poprawnie skonfigurować email, szablony,
HTTPS i ochronę anti-abuse.

</details>

<details>
<summary>78. Czym jest CSRF i jak działa {% csrf_token %}?</summary>

#### Django

**CSRF (Cross-Site Request Forgery)** to atak, w którym złośliwa strona wymusza
na zalogowanym użytkowniku wykonanie niechcianej akcji w Twojej aplikacji (np.
zmiana hasła lub wykonanie płatności).

#### Jak Django chroni przed CSRF:

1. Po stronie serwera generowany jest token CSRF.
2. Token trafia do formularza (przez `{% csrf_token %}`).
3. Dla żądań zmieniających stan (`POST`, `PUT`, `PATCH`, `DELETE`) Django
   porównuje token z żądania z oczekiwanym tokenem.
4. Jeśli tokenu brakuje lub jest niepoprawny -> `403 Forbidden`.

#### `{% csrf_token %}` w formularzu:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Zapisz</button>
</form>
```

#### Co jest potrzebne do działania:

1. `django.middleware.csrf.CsrfViewMiddleware` w `MIDDLEWARE`.
2. Użycie `{% csrf_token %}` we wszystkich formularzach POST.
3. Poprawna polityka cookie (szczególnie w production z HTTPS).

#### Dla zapytań AJAX/fetch:

- Token CSRF przekazuje się w nagłówku `X-CSRFToken`.
- Token pobiera się z cookie (`csrftoken`) albo z HTML (zależnie od podejścia).

#### Typowe błędy:

1. Brak `{% csrf_token %}` w szablonie formularza.
2. Wyłączenie `CsrfViewMiddleware` bez uzasadnionej przyczyny.
3. Błędna konfiguracja domeny/secure-parametrów cookie.
4. Użycie `@csrf_exempt` "na szybko", a potem brak przywrócenia ochrony.

#### Kiedy `csrf_exempt` bywa dopuszczalne:

- Tylko dla specjalnych endpointów (np. zewnętrzne webhooks) i tylko jeśli jest
  inny wiarygodny mechanizm walidacji (HMAC signature, token, allowlist).

#### Praktyczne rekomendacje:

1. Wszystkie browser-based formularze zmieniające stan muszą zawierać
   `{% csrf_token %}`.
2. Dla API bez cookie-sesji (Bearer/JWT) buduj osobny model auth.
3. W production używaj HTTPS + `CSRF_COOKIE_SECURE = True`.

#### Wniosek:

`{% csrf_token %}` to kluczowy element ochrony Django przed atakami CSRF w
formularzach. To nie opcja, tylko bazowy standard bezpieczeństwa dla działań
zmieniających stan systemu.

</details>

<details>
<summary>79. Jak Django chroni przed XSS, CSRF i SQL injection?</summary>

#### Django

Django ma podejście "secure by default" i wbudowane mechanizmy ochrony przed
najczęstszymi podatnościami webowymi: XSS, CSRF i SQL injection.

#### 1. Ochrona przed XSS (Cross-Site Scripting)

Jak działa:

1. Szablony Django automatycznie escapują zmienne w `{{ ... }}`.
2. Specjalne znaki HTML są zamieniane na bezpieczną postać.
3. Potencjalnie niebezpieczna treść nie wykonuje się jako skrypt.

Ważne:

- `|safe` wyłącza escaping, używaj tylko dla w pełni zaufanego HTML.
- Nie renderuj surowego user input bez sanitizacji.

#### 2. Ochrona przed CSRF

Jak działa:

1. `CsrfViewMiddleware` sprawdza token w żądaniach zmieniających stan.
2. `{% csrf_token %}` dodaje token do formularzy HTML.
3. Bez poprawnego tokenu Django zwraca `403`.

#### 3. Ochrona przed SQL injection

Jak działa:

1. ORM używa zapytań parametryzowanych.
2. Dane są przekazywane oddzielnie od struktury SQL.
3. To blokuje klasyczne iniekcje w większości standardowych scenariuszy.

Ryzyko pojawia się, gdy:

- piszesz raw SQL z ręcznym konkatenowaniem stringów.

#### Dodatkowe wbudowane zabezpieczenia Django:

1. `SecurityMiddleware` (headers, polityki SSL-related).
2. `XFrameOptionsMiddleware` (ochrona przed clickjacking).
3. Bezpieczne hashowanie haseł (`PBKDF2` domyślnie).
4. Kontrola host header (`ALLOWED_HOSTS`).

#### Praktyczne rekomendacje produkcyjne:

1. `DEBUG=False` w production.
2. HTTPS wszędzie (`SECURE_SSL_REDIRECT`, secure cookies).
3. Ustaw `SESSION_COOKIE_SECURE`, `CSRF_COOKIE_SECURE`, `HTTPONLY`.
4. Używaj CSP (przez nagłówki/pakiety).
5. Regularnie aktualizuj Django i zależności.

#### Typowe błędy deweloperów:

1. Niekontrolowane używanie `|safe`.
2. `@csrf_exempt` bez alternatywnej walidacji.
3. Raw SQL przez f-string/format.
4. Pozostawienie `DEBUG=True` na production.

#### Wniosek:

Django zapewnia silną bazową ochronę przed XSS, CSRF i SQL injection. Jednak
bezpieczeństwo zależy też od dyscypliny kodu: poprawnego użycia templates,
ORM, konfiguracji produkcyjnej i regularnego security review.

</details>

<details>
<summary>80. Jak Django chroni przed SQL injection?</summary>

#### Django

Django chroni przed SQL injection przede wszystkim przez ORM i zapytania
parametryzowane: dane użytkownika są przekazywane jako parametry, a nie
wstrzykiwane bezpośrednio do SQL.

#### Główny mechanizm ochrony:

1. Piszesz zapytanie ORM:

```python
User.objects.filter(email=user_input)
```

2. Django generuje SQL z placeholderami.
3. Wartość `user_input` nie "psuje" struktury SQL.

#### Dlaczego to jest bezpieczne:

- ORM oddziela logikę SQL od danych.
- Baza traktuje parametry jako wartości, nie jako część komendy SQL.

#### Gdzie ryzyko nadal jest możliwe:

1. **Raw SQL z konkatenacją stringów**

```python
# Niebezpieczne
sql = f"SELECT * FROM users WHERE email = '{user_input}'"
```

2. Nieprawidłowe użycie `.extra()` (legacy).
3. Dynamiczne ORDER BY/nazwy pól bez sprawdzenia allowlist.

#### Bezpieczny raw SQL (jeśli naprawdę potrzebny):

```python
from django.db import connection

with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM users WHERE email = %s", [user_input])
    rows = cursor.fetchall()
```

#### Praktyczne zasady:

1. Domyślnie używaj ORM (`filter/get/exclude/annotate`).
2. Jeśli raw SQL jest nieunikniony - tylko zapytania parametryzowane.
3. Nigdy nie wstawiaj user input do SQL przez f-string lub `format`.
4. Dla dynamicznych pól/sortowania stosuj allowlist:

- dozwolone są tylko wcześniej zdefiniowane nazwy kolumn.

#### Dodatkowe kroki hardening:

1. Minimalne uprawnienia użytkownika DB (least privilege).
2. Logi podejrzanych zapytań i monitoring anomalii.
3. Regularne aktualizacje Django i sterowników DB.

#### Wniosek:

Django ORM dobrze chroni przed SQL injection "out of the box". Realne ryzyko
pojawia się tam, gdzie deweloper omija ORM i buduje SQL ręcznie bez
parametryzacji i walidacji.

</details>

<details>
<summary>81. Czym jest Content Security Policy (CSP) w Django?</summary>

#### Django

**Content Security Policy (CSP)** to polityka bezpieczeństwa HTTP, która
ogranicza źródła, z których przeglądarka może ładować skrypty, style, obrazy,
fonty itd. Główny cel to zmniejszenie ryzyka XSS i wykonania niebezpiecznego
kontentu.

#### Co robi CSP:

1. Definiuje allowlist źródeł (`self`, CDN, domeny API).
2. Blokuje nieznane lub iniekcyjne zasoby.
3. Pozwala wdrażać politykę stopniowo przez tryb `Report-Only`.

#### Przykład nagłówka CSP:

```http
Content-Security-Policy:
default-src 'self';
script-src 'self';
style-src 'self' https://fonts.googleapis.com;
font-src 'self' https://fonts.gstatic.com;
img-src 'self' data:;
connect-src 'self';
frame-ancestors 'none';
base-uri 'self';
```

#### Jak dodać CSP w Django:

Najwygodniej przez pakiet `django-csp`:

```bash
pip install django-csp
```

```python
# settings.py
INSTALLED_APPS += ["csp"]
MIDDLEWARE += ["csp.middleware.CSPMiddleware"]

CSP_DEFAULT_SRC = ("'self'",)
CSP_SCRIPT_SRC = ("'self'",)
CSP_STYLE_SRC = ("'self'", "https://fonts.googleapis.com")
CSP_FONT_SRC = ("'self'", "https://fonts.gstatic.com")
CSP_IMG_SRC = ("'self'", "data:")
CSP_CONNECT_SRC = ("'self'",)
CSP_FRAME_ANCESTORS = ("'none'",)
```

#### Ważne praktyki:

1. Zacznij od `Content-Security-Policy-Report-Only`, żeby zebrać naruszenia.
2. Minimalizuj użycie `'unsafe-inline'` i `'unsafe-eval'`.
3. Dla inline skryptów stosuj podejście nonce/hash.
4. Stopniowo zawężaj politykę do niezbędnych źródeł.

#### Typowe problemy przy wdrożeniu:

1. Zbyt restrykcyjne reguły psują widgety/analitykę stron trzecich.
2. Nieprzemyślane wildcardy (`*`) osłabiają wartość CSP.
3. Brak monitorowania naruszeń CSP po wdrożeniu.

#### Wniosek:

CSP w Django to ważna dodatkowa warstwa ochrony przed XSS i ryzykiem
supply-chain. Najlepsze podejście: najpierw `Report-Only`, potem stopniowe
zaostrzenie polityki do modelu ścisłej allowlisty.

</details>

<details>
<summary>82. Czym są custom management commands i kiedy warto ich używać?</summary>

#### Django

`Custom management commands` to własne komendy CLI Django uruchamiane przez
`python manage.py <command_name>`. Pozwalają zapisać operacyjne i techniczne
zadania jako utrzymywalny kod projektu.

#### Po co to stosować:

1. Automatyzacja rutynowych zadań (import/eksport, czyszczenie, synchronizacja).
2. Komendy operacyjne dla DevOps/Support.
3. Skrypty do migracji/backfillu danych.
4. Komendy dla CI/CD, stagingu i okien maintenance.

#### Struktura plików:

```text
my_app/
  management/
    __init__.py
    commands/
      __init__.py
      recalc_stats.py
```

#### Przykład komendy:

```python
from django.core.management.base import BaseCommand
from orders.models import Order

class Command(BaseCommand):
    help = "Przelicza zagregowane statystyki zamówień"

    def add_arguments(self, parser):
        parser.add_argument("--dry-run", action="store_true")

    def handle(self, *args, **options):
        total = Order.objects.count()
        if options["dry_run"]:
            self.stdout.write(self.style.WARNING(f"DRY RUN: orders={total}"))
            return
        # właściwa logika
        self.stdout.write(self.style.SUCCESS(f"Done. orders={total}"))
```

Uruchomienie:

```bash
python manage.py recalc_stats --dry-run
```

#### Kiedy custom command to dobry wybór:

1. Zadanie jest powtarzalne i powinno być odtwarzalne.
2. Potrzebny jest pełny kontekst Django (ORM, settings, services).
3. Potrzebna jest kontrolowana komenda dla zespołu/CI.

#### Praktyczne rekomendacje:

1. Dodawaj `--dry-run` do bezpiecznej weryfikacji.
2. Rób operacje idempotentne, jeśli to możliwe.
3. Używaj transakcji dla krytycznych zmian wsadowych.
4. Loguj postęp i wynik (`self.stdout`, structured logs).
5. Dla długich zadań rozważ kolejki/workery.

#### Typowe błędy:

1. Trzymanie ważnych "one-off" skryptów poza repozytorium.
2. Uruchamianie ryzykownych update/delete bez dry-run i planu backupu.
3. Pisanie komendy jako nieczytelnego monolitu bez testów.

#### Wniosek:

Custom management commands to standardowe narzędzie dojrzałości operacyjnej
Django. Ułatwiają transparentne, kontrolowane i powtarzalne wykonywanie
procedur technicznych.

</details>

<details>
<summary>83. Czym są context processors i jak się ich używa?</summary>

#### Django

`Context processors` to funkcje, które automatycznie dodają dane do kontekstu
każdego szablonu (lub wybranych szablonów), aby nie przekazywać tych zmiennych
ręcznie w każdym view.

#### Jak działa context processor:

1. Django wywołuje funkcję podczas renderowania szablonu.
2. Funkcja zwraca słownik.
3. Ten słownik jest dodawany do template context.

#### Przykład:

```python
# core/context_processors.py
def app_meta(request):
    return {
        "APP_NAME": "My Django App",
        "SUPPORT_EMAIL": "support@example.com",
    }
```

Podłączenie w `settings.py`:

```python
TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [],
        "APP_DIRS": True,
        "OPTIONS": {
            "context_processors": [
                "django.template.context_processors.request",
                "django.contrib.auth.context_processors.auth",
                "django.contrib.messages.context_processors.messages",
                "core.context_processors.app_meta",
            ],
        },
    },
]
```

Po tym w dowolnym szablonie:

```django
<footer>{{ APP_NAME }} · {{ SUPPORT_EMAIL }}</footer>
```

#### Kiedy używać:

1. Globalne dane dla layoutu (nazwa aplikacji, kontakty, feature flags).
2. Dane potrzebne w wielu szablonach.
3. Lekkie i szybkie wartości bez kosztownych obliczeń.

#### Kiedy nie warto:

1. Dla ciężkich zapytań SQL przy każdym renderze.
2. Dla wąsko specyficznych danych jednego-dwóch view.
3. Dla złożonej logiki biznesowej.

#### Wbudowane przydatne context processors:

1. `django.template.context_processors.request` (`request` w szablonie)
2. `django.contrib.auth.context_processors.auth` (`user`, `perms`)
3. `django.contrib.messages.context_processors.messages`
4. `django.template.context_processors.static`
5. `django.template.context_processors.media`

#### Praktyczne rekomendacje:

1. Utrzymuj context processors maksymalnie lekkie.
2. Unikaj duplikowania kluczy, które mogą kolidować z lokalnym context.
3. Jeśli dane są kosztowne - cache'uj je albo przekazuj punktowo z view.
4. Dokumentuj globalne klucze kontekstu dla zespołu.

#### Wniosek:

Context processors to wygodny mechanizm dla wspólnych danych szablonów. Dobrze
sprawdzają się dla lekkich wartości globalnych, ale nie powinny stawać się
miejscem dla ciężkiej logiki domenowej.

</details>

<details>
<summary>84. Jak działa cache w Django? Główne podejścia do cache'owania.</summary>

#### Django

Cache w Django zmniejsza liczbę kosztownych operacji (SQL, renderowanie
szablonów, obliczenia) i przyspiesza odpowiedzi dla użytkownika.

#### Jak to działa:

1. Dane/odpowiedź są zapisywane w szybkim magazynie (Redis/Memcached).
2. Kolejne żądanie pobiera wynik z cache, bez pełnego przeliczenia.
3. Po TTL lub inwalidacji wartość jest obliczana ponownie.

#### Główne podejścia do cache'owania w Django:

1. **Site-wide cache (middleware)**

- Cache'uje prawie całą odpowiedź HTTP dla stron.
- Dobre dla publicznego kontentu z niewielką personalizacją.

2. **Per-view cache (`cache_page`)**

- Cache'uje konkretny view na określony czas.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)
def article_list(request):
    ...
```

3. **Template fragment cache**

- Cache'uje fragment szablonu, a nie całą stronę.

```django
{% load cache %}
{% cache 300 homepage_sidebar user.id %}
  ...
{% endcache %}
```

4. **Low-level cache API**

- Ręczne cache'owanie wyników w kodzie.

```python
from django.core.cache import cache

data = cache.get("popular_products")
if data is None:
    data = expensive_query()
    cache.set("popular_products", data, 300)
```

#### Konfiguracja backendu:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Kiedy wybierać które podejście:

1. Publiczne strony bez personalizacji -> per-view/site-wide.
2. Częściowo dynamiczne strony -> fragment cache.
3. Kosztowne obliczenia domenowe/agregacje -> low-level cache API.

#### Praktyczne zasady:

1. Zaczynaj od cache punktowego (fragment/per-view), nie od razu site-wide.
2. Ustalaj TTL z uwzględnieniem wymagań aktualności danych.
3. Dla danych personalizowanych dodawaj klucze (user id, locale, role).
4. Planowo inwaliduj cache po zmianach danych.

#### Typowe błędy:

1. Cache'owanie personalizowanego kontentu bez klucza użytkownika.
2. Brak inwalidacji cache po update/delete.
3. Zbyt długi TTL dla "żywych" danych.
4. Poleganie na cache zamiast optymalizacji słabych zapytań SQL.

#### Wniosek:

Cache w Django to strategia wielopoziomowa: od fragmentów szablonu po pełne
odpowiedzi. Najlepszy efekt daje połączenie właściwego backendu (zwykle Redis),
rozsądnego TTL i kontrolowanej inwalidacji.

</details>

<details>
<summary>85. Jak optymalizować zapytania, cache'owanie i indeksację bazy danych?</summary>

#### Django

Optymalizacja w Django zawsze jest kompleksowa:
`zapytania ORM` + `cache` + `właściwe indeksy DB` + `profilowanie`. Pojedyncza
technika rzadko daje stabilny efekt.

#### 1. Optymalizacja zapytań ORM

1. Unikaj N+1 przez:

- `select_related()` dla FK/O2O
- `prefetch_related()` dla M2M/reverse FK

2. Pobieraj tylko potrzebne pola:

- `values()`, `values_list()`, `only()`, `defer()`

3. Dla update'ów masowych używaj:

- `update()` + `F()` zamiast `save()` w pętli

4. Do sprawdzania istnienia używaj:

- `exists()` zamiast ładowania całego queryset

#### 2. Cache'owanie

1. Zaczynaj od fragment/per-view cache.
2. Dla "gorących" obliczeń - low-level cache API.
3. Dla production najczęściej backend Redis.
4. Projektuj klucze cache (user/locale/role) i inwalidację po zmianie danych.

#### 3. Indeksacja bazy danych

1. Dodawaj indeksy na pola często używane w:

- `WHERE`
- `ORDER BY`
- `JOIN`

2. Używaj `models.Index` i `UniqueConstraint` w `Meta`.
3. Nie indeksuj "wszystkiego": każdy indeks kosztuje przy `INSERT/UPDATE`.

Przykład:

```python
class Order(models.Model):
    user = models.ForeignKey("auth.User", on_delete=models.CASCADE)
    status = models.CharField(max_length=20)
    created_at = models.DateTimeField(auto_now_add=True)

    class Meta:
        indexes = [
            models.Index(fields=["status", "-created_at"]),
            models.Index(fields=["user", "-created_at"]),
        ]
```

#### 4. Profilowanie i pomiar

1. Używaj Django Debug Toolbar na dev/staging.
2. Loguj wolne zapytania SQL na poziomie bazy.
3. Sprawdzaj `EXPLAIN ANALYZE` dla krytycznych zapytań.
4. Mierz p95/p99 latency przed i po zmianach.

#### Typowa kolejność optymalizacji:

1. Znajdź wąskie gardło (nie optymalizuj "w ciemno").
2. Popraw ORM (N+1, zbędne pola, zduplikowane zapytania).
3. Dodaj/sprawdź indeksy.
4. Dodaj cache dla stale gorących scenariuszy.
5. Ponownie zmierz rezultat.

#### Typowe błędy:

1. Cache'owanie wszystkiego bez strategii inwalidacji.
2. Dodawanie indeksów bez analizy realnych zapytań.
3. Optymalizacja kodu Python z pominięciem wąskiego gardła SQL.
4. Duże zmiany schematu w production bez etapowego rolloutu.

#### Wniosek:

Stabilna wydajność Django nie wynika z "jednego przycisku", tylko z
systemowego podejścia: mierzyć, optymalizować ORM, poprawnie indeksować DB i
cache'ować tylko to, co daje realny zysk pod obciążeniem.

</details>

<details>
<summary>86. Czym jest Django testing framework?</summary>

#### Django

`Django testing framework` to wbudowany zestaw narzędzi do testowania modeli,
view, formularzy, API i integracji w projekcie Django.

#### Co zawiera framework:

1. `django.test.TestCase` - bazowa klasa dla większości testów.
2. `Client` - testowy klient HTTP do zapytań do view/URL.
3. Testową bazę danych (tworzoną automatycznie przed uruchomieniem).
4. Assertions dla response, contextu, redirectów i szablonów.
5. Narzędzia do override settings i izolacji środowiska.

#### Jak uruchamia się testy:

```bash
python manage.py test
```

#### Jak działa testowa DB:

1. Django tworzy osobną test-DB.
2. Nakłada migracje/schemat.
3. Każdy test jest izolowany transakcyjnie (`TestCase`).
4. Po zakończeniu test-DB jest usuwana.

#### Główne klasy testów:

1. **`TestCase`**

- Najczęstszy wybór; szybkie i izolowane testy ORM/view.

2. **`TransactionTestCase`**

- Gdy potrzebna jest kontrola transakcji/commit behavior.

3. **`SimpleTestCase`**

- Testy bez dostępu do bazy danych.

4. **`LiveServerTestCase`**

- Testy integracyjne/browserowe z uruchomionym testowym serwerem.

#### Przykład prostego testu:

```python
from django.test import TestCase
from django.urls import reverse

class HealthViewTests(TestCase):
    def test_health_endpoint_returns_200(self):
        response = self.client.get(reverse("health"))
        self.assertEqual(response.status_code, 200)
```

#### Praktyczne rekomendacje:

1. Pisz testy dla krytycznych scenariuszy biznesowych, nie tylko dla coverage.
2. Twórz testy deterministyczne (bez zależności od czasu/sieci bez mock).
3. Wynoś factories/fixtures dla czytelnego przygotowania danych.
4. Uruchamiaj testy w CI na każdym PR.

#### Typowe błędy:

1. Testy zależne od kolejności wykonania.
2. Nadmiernie integracyjne testy tam, gdzie wystarczy poziom unit.
3. Ignorowanie edge case'ów i scenariuszy negatywnych.

#### Wniosek:

Django testing framework daje gotową infrastrukturę do niezawodnego testowania
backendu "out of the box". To podstawa bezpiecznego refaktoringu i stabilnego
procesu wydawniczego w pracy zespołowej.

</details>

<details>
<summary>87. Czym różnią się testy unit i integration?</summary>

#### Django

Testy `unit` i `integration` różnią się poziomem weryfikacji:

- **Unit test** sprawdza izolowany fragment logiki.
- **Integration test** sprawdza współpracę kilku komponentów razem.

#### Testy unit:

1. Testują jedną funkcję/metodę/klasę w oderwaniu od reszty systemu.
2. Często używają mock/stub dla zależności.
3. Są bardzo szybkie i precyzyjnie lokalizują błąd.

Przykład w Django:

- test walidatora,
- test helper-funkcji,
- test metody serwisowej bez realnego HTTP/DB (lub z minimalną izolacją).

#### Testy integration:

1. Sprawdzają działanie kilku warstw razem (view + ORM + middleware + templates).
2. Często używają test clienta i testowej bazy.
3. Są wolniejsze, ale bliższe realnemu scenariuszowi zachowania.

Przykład w Django:

- `client.post(...)` -> view -> zapis modelu -> redirect -> weryfikacja DB.

#### Kluczowe różnice:

1. **Szybkość**

- Unit: szybkie.
- Integration: wolniejsze.

2. **Zakres pokrycia**

- Unit: wąski fokus.
- Integration: szerszy scenariusz systemowy.

3. **Diagnostyka**

- Unit: łatwiej znaleźć konkretną przyczynę.
- Integration: lepiej łapią problemy integracji komponentów.

#### Przykład piramidy testów dla Django:

1. Wiele testów unit (walidatory, serwisy, utility).
2. Mniej testów integration (kluczowe endpointy, krytyczne flow biznesowe).
3. Jeszcze mniej testów end-to-end/browserowych.

#### Praktyczne rekomendacje:

1. Krytyczną logikę domenową pokrywaj dobrze testami unit.
2. Dla core user journeys obowiązkowo dodawaj testy integration.
3. Nie próbuj pokryć wszystkiego tylko testami integracyjnymi - to wolne i kruche.
4. Każdy bug na production powinien kończyć się nowym testem odpowiedniego poziomu.

#### Wniosek:

Testy unit i integration nie zastępują się nawzajem. Stabilny projekt Django
potrzebuje kombinacji: unit dla szybkiego feedbacku i integration dla weryfikacji
realnej współpracy komponentów.

</details>

<details>
<summary>88. Czym jest Django test client?</summary>

#### Django

`Django test client` to wbudowane narzędzie do symulacji żądań HTTP do aplikacji
bez uruchamiania realnej przeglądarki ani zewnętrznego serwera HTTP.

#### Co potrafi test client:

1. Wysyłać żądania `GET`, `POST`, `PUT`, `PATCH`, `DELETE`.
2. Sprawdzać status code, redirecty, templates i context.
3. Pracować z sesją, cookies i autoryzacją użytkownika.
4. Testować łańcuch URL -> view -> response.

#### Bazowy przykład:

```python
from django.test import TestCase
from django.urls import reverse

class HomeTests(TestCase):
    def test_home_returns_200(self):
        response = self.client.get(reverse("home"))
        self.assertEqual(response.status_code, 200)
```

#### Przykład zapytania POST:

```python
response = self.client.post(reverse("signup"), {
    "username": "testuser",
    "password1": "StrongPass123!",
    "password2": "StrongPass123!",
})
self.assertEqual(response.status_code, 302)
```

#### Logowanie w testach:

1. Szybkie techniczne logowanie:

```python
self.client.force_login(user)
```

2. Bardziej realistyczne logowanie przez credentials:

```python
logged_in = self.client.login(username="testuser", password="secret")
self.assertTrue(logged_in)
```

#### Co można weryfikować:

1. `response.status_code`
2. `response.context`
3. `response.templates`
4. `assertRedirects(...)`
5. zawartość odpowiedzi (`assertContains(...)`)

#### Ograniczenia test clienta:

1. Nie wykonuje JavaScript (to nie browser automation).
2. Nie sprawdza realnego runtime frontendu jak Playwright/Selenium.
3. Nie modeluje wszystkich niuansów środowiska sieciowego production.

#### Praktyczne rekomendacje:

1. Używaj test clienta dla większości web/API testów integracyjnych Django.
2. Dla JS-flow dodawaj osobne testy e2e/browserowe.
3. Łącz go z factories/fixtures dla czytelnego przygotowania danych.

#### Wniosek:

Django test client to szybkie i mocne narzędzie do testowania zachowania HTTP na
poziomie backendu. To standardowy wybór do testów view, URL, autoryzacji i
bazowej integracji komponentów.

</details>

<details>
<summary>89. Jak testować formularze, views i ORM?</summary>

#### Django

W Django formularze, views i ORM testuje się na różnych poziomach, ale w jednym
stylu: jasne preconditions -> akcja -> weryfikacja wyniku.

#### 1. Testowanie formularzy

Co sprawdzać:

1. poprawne/niepoprawne dane,
2. błędy dla konkretnych pól,
3. custom walidację (`clean_<field>`, `clean()`).

Przykład:

```python
from django.test import TestCase
from users.forms import SignUpForm

class SignUpFormTests(TestCase):
    def test_form_valid(self):
        form = SignUpForm(data={
            "username": "newuser",
            "email": "user@example.com",
            "password1": "StrongPass123!",
            "password2": "StrongPass123!",
        })
        self.assertTrue(form.is_valid())

    def test_form_invalid_password_mismatch(self):
        form = SignUpForm(data={
            "username": "newuser",
            "email": "user@example.com",
            "password1": "StrongPass123!",
            "password2": "WrongPass123!",
        })
        self.assertFalse(form.is_valid())
```

#### 2. Testowanie views

Co sprawdzać:

1. status code,
2. szablon/context,
3. redirecty,
4. zachowanie auth/permissions.

Przykład:

```python
from django.test import TestCase
from django.urls import reverse

class DashboardViewTests(TestCase):
    def test_anonymous_redirected_to_login(self):
        response = self.client.get(reverse("dashboard"))
        self.assertEqual(response.status_code, 302)
```

#### 3. Testowanie ORM

Co sprawdzać:

1. tworzenie/aktualizację/usuwanie modeli,
2. custom metody manager/queryset,
3. relacje i ograniczenia (`unique`, `constraints`).

Przykład:

```python
from django.test import TestCase
from blog.models import Article

class ArticleORMTests(TestCase):
    def test_create_article(self):
        article = Article.objects.create(title="Test", is_published=True)
        self.assertEqual(Article.objects.count(), 1)
        self.assertTrue(article.is_published)
```

#### Praktyczne rekomendacje:

1. Utrzymuj testy niezależne od siebie.
2. Nadawaj opisowe nazwy testom wg reguły `should_<behavior>`.
3. Do danych testowych używaj factories/fixtures, a nie duplikacji setup.
4. Testuj scenariusze negatywne tak samo starannie jak pozytywne.

#### O czym często się zapomina:

1. Sprawdzenie permissions na poziomie view.
2. Walidacja formularzy z nieoczywistymi danymi wejściowymi.
3. Zachowanie metod manager/queryset na pustych zbiorach.

#### Wniosek:

Formularze testują walidację, views - zachowanie HTTP, ORM - dane i relacje.
Razem daje to solidny fundament testowy, który pozwala bezpiecznie refaktoryzować
kod Django i stabilnie wydawać zmiany.

</details>

<details>
<summary>90. Jak używać fixtures?</summary>

#### Django

`Fixtures` w Django to wcześniej przygotowane dane (JSON/YAML/XML), które można
załadować do bazy dla testów, demo lub początkowego seedowania.

#### Po co używa się fixtures:

1. Szybkie podniesienie standardowego zestawu danych.
2. Odtworzenie identycznego stanu testowego w różnych środowiskach.
3. Testowanie scenariuszy z "realistycznie" powiązanymi rekordami.

#### Przykład pliku fixture:

```json
[
  {
    "model": "blog.article",
    "pk": 1,
    "fields": {
      "title": "Hello Django",
      "is_published": true
    }
  }
]
```

Umieszczenie:

- `app/fixtures/articles.json` (typowy wariant)

#### Załadowanie fixture:

```bash
python manage.py loaddata articles.json
```

#### Użycie w testach:

```python
from django.test import TestCase
from blog.models import Article

class ArticleTests(TestCase):
    fixtures = ["articles.json"]

    def test_fixture_loaded(self):
        self.assertEqual(Article.objects.count(), 1)
```

#### Kiedy fixtures są zasadne:

1. Mały, stabilny zestaw danych referencyjnych.
2. Testy integracyjne ze złożonymi relacjami.
3. Demo/lokalne dane dla środowisk review.

#### Ograniczenia fixtures:

1. Kruche przy zmianach schematu modeli.
2. Trudniejsze do czytania i utrzymania przy dużych plikach JSON.
3. Trudniej elastycznie komponować dane pod różne testy.

#### Praktyczna alternatywa:

- Dla większości testów lepsze są factories (`factory_boy`, `model_bakery`), bo:

1. Dane tworzą się programowo.
2. Łatwiej je dostosować do zmian modelu.
3. Mniej "magicznych" statycznych plików.

#### Rekomendowane podejście tech leada:

1. Małe współdzielone dane -> fixtures.
2. Większość testów unit/integration -> factories.
3. Nie mieszaj chaotycznie obu podejść bez jasnych zasad zespołowych.

#### Wniosek:

Fixtures w Django są przydatne dla stabilnego zestawu startowego danych, ale dla
elastycznych i długoterminowych zestawów testowych zwykle skuteczniejsze są
podejścia oparte na factory.

</details>

<details>
<summary>91. Jak działają async views i async ORM w Django?</summary>

#### Django

Django wspiera asynchroniczne view (`async def`) i stopniowo rozwija async
stack dla scenariuszy I/O-heavy. Główna wartość async to lepsza skalowalność
przy dużej liczbie jednoczesnych oczekiwań (zewnętrzne API, operacje sieciowe).

#### Async view w Django:

```python
from django.http import JsonResponse

async def async_health(request):
    return JsonResponse({"status": "ok"})
```

#### Kiedy async jest naprawdę przydatny:

1. Dużo oczekiwania na I/O (HTTP do usług zewnętrznych).
2. Long-polling/websocket (z odpowiednim stackiem).
3. Wysoka współbieżność żądań przy relatywnie lekkiej logice CPU.

#### Sync vs Async w Django:

1. `def view(...)` -> synchroniczny view.
2. `async def view(...)` -> asynchroniczny view.
3. Django może adaptować granice sync/async, ale nadmiar przejść ma overhead.

#### Praca z DB (ORM):

- Historycznie ORM był sync-first.
- W nowszych wersjach Django są async-odpowiedniki części operacji (`aget`,
  `acreate`, `aupdate_or_create`, async iteration itd.), ale trzeba uwzględnić
  kompatybilność wersji i drivera DB.

Przykład:

```python
user = await User.objects.aget(pk=user_id)
```

#### Ważne ograniczenia:

1. Nie wszystkie biblioteki zewnętrzne mają async-safe API.
2. Zadań CPU-bound async nie przyspiesza (tu lepsze są workery/kolejki/procesy).
3. Mieszanie sync ORM w async kodzie może blokować event loop.

#### Praktyczne rekomendacje:

1. Używaj async tam, gdzie jest realny I/O bottleneck.
2. Jeśli stack jest głównie sync - nie forsuj async "dla mody".
3. Minimalizuj przejścia sync<->async.
4. Dla długich zadań CPU/background używaj Celery/RQ, nie `await` w view.

#### Typowe błędy:

1. Oczekiwanie wzrostu wydajności bez zmiany profilu I/O aplikacji.
2. Blokujące wywołania sync wewnątrz async view.
3. Brak testów pod obciążeniem współbieżnym.

#### Wniosek:

Async w Django to mocne narzędzie dla scenariuszy I/O-heavy, ale nie uniwersalne
lekarstwo. Efektywność zależy od spójności całego stacku: view, ORM, klientów
zewnętrznych i realnego profilu obciążenia.

</details>

<details>
<summary>92. Jak tworzyć backendowe zadania (@task, Celery)?</summary>

#### Django

Backendowe zadania (background jobs) w Django stosuje się dla ciężkich lub
odroczonych operacji, których nie warto wykonywać bezpośrednio w żądaniu HTTP:
wysyłka emaili, import, generowanie plików, integracje, retry.

#### Najpopularniejszy stack:

- **Celery** + broker (zwykle Redis lub RabbitMQ) + workers

#### Bazowa architektura:

1. Kod Django odkłada zadanie do kolejki.
2. Broker przechowuje komunikat.
3. Worker Celery pobiera zadanie i wykonuje je asynchronicznie.
4. (Opcjonalnie) wynik trafia do result backend.

#### Przykład zadania:

```python
# app/tasks.py
from celery import shared_task

@shared_task
def send_welcome_email(user_id):
    # logika wysyłki email
    return {"user_id": user_id, "status": "sent"}
```

Wywołanie z view/serwisu:

```python
send_welcome_email.delay(user.id)
```

#### Minimalna integracja Celery z Django:

1. Zainstalować:

```bash
pip install celery redis
```

2. Dodać `celery.py` do konfiguracji projektu.
3. Ustawić broker URL w settings/env.
4. Uruchomić workera:

```bash
celery -A config worker -l info
```

#### Zadania okresowe:

- Przez `celery beat` albo `django-celery-beat` (scheduler typu cron).

#### Praktyczne rekomendacje:

1. Zadania powinny być **idempotentne** (ponowne uruchomienie nie psuje danych).
2. Dodawaj `retry` dla tymczasowych błędów (sieć, zewnętrzne API).
3. Nie przekazuj ciężkich obiektów - przekazuj `id`, dane pobieraj w workerze.
4. Loguj status wykonania i błędy.
5. Ustalaj timeouty i limity współbieżności workerów.

#### Typowe błędy:

1. Wykonywanie długich operacji w view zamiast przez kolejkę.
2. Brak retry/policy przy integracjach z usługami zewnętrznymi.
3. Nieoczekiwane duplikaty zadań przez brak idempotentności.
4. Brak monitoringu kolejek i "zawieszonych" zadań.

#### Wniosek:

Celery w Django to standard dla asynchronicznego przetwarzania zadań backendowych.
Klucz do niezawodności: idempotentność, retry, monitoring i jasny podział
między HTTP-flow i przetwarzaniem w tle.

</details>

<details>
<summary>93. Czym jest Django REST Framework?</summary>

#### Django

**Django REST Framework (DRF)** to popularny framework nad Django do budowy REST
API: serializacja danych, walidacja, autoryzacja, routing, paginacja oraz
wygodny interfejs API-browsable.

#### Po co używa się DRF:

1. Szybkie budowanie stabilnych API dla klientów web/mobile.
2. Standaryzacja walidacji i formatu odpowiedzi.
3. Elastyczne zarządzanie auth/permissions/throttling.
4. Mniej boilerplate niż w "czystych" view z JsonResponse.

#### Kluczowe komponenty DRF:

1. **Serializer**

- Konwersja model/obiekt <-> JSON.
- Walidacja danych wejściowych.

2. **APIView / GenericAPIView / ViewSet**

- Warstwy do budowy logiki endpointów.

3. **Routers**

- Automatyczne generowanie URL dla ViewSet.

4. **Authentication / Permissions**

- Kontrola kto jesteś i co możesz zrobić.

5. **Pagination / Filtering / Ordering**

- Gotowe mechanizmy listowania i wyszukiwania.

#### Przykład serializera:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Przykład ViewSet:

```python
from rest_framework.viewsets import ModelViewSet
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
```

#### Przykład routera:

```python
from rest_framework.routers import DefaultRouter
from .views import ArticleViewSet

router = DefaultRouter()
router.register("articles", ArticleViewSet, basename="article")
urlpatterns = router.urls
```

#### Kiedy DRF jest szczególnie trafny:

1. Gdy produkt jest API-first lub multi-client.
2. Gdy są złożone wymagania permission/pagination/filtering.
3. Gdy potrzebna jest skalowalna architektura API i standaryzacja błędów.

#### Wniosek:

DRF to de facto standard API w ekosystemie Django. Daje uporządkowaną
architekturę API, przyspiesza development i upraszcza utrzymanie endpointów
produkcyjnych.

</details>

<details>
<summary>94. Czym jest serializacja i po co jest potrzebna?</summary>

#### Django

Serializacja to przekształcanie obiektów Python/modeli do formatu wymiany danych
(zwykle JSON), a deserializacja to odwrotny proces do obiektów z walidacją.

#### Po co potrzebna jest serializacja:

1. Przekazywanie danych między backendem a klientami frontend/mobile.
2. Standaryzacja formatu odpowiedzi API.
3. Walidacja danych wejściowych przed zapisem do DB.
4. Oddzielenie modelu DB od zewnętrznego kontraktu API.

#### Serializacja w DRF:

- Realizowana przez `Serializer` lub `ModelSerializer`.

Przykład:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Konwersja model -> JSON:

```python
article = Article.objects.first()
data = ArticleSerializer(article).data
```

#### Konwersja JSON -> validated data/model:

```python
payload = {"title": "New", "is_published": True}
serializer = ArticleSerializer(data=payload)
serializer.is_valid(raise_exception=True)
obj = serializer.save()
```

#### Co jeszcze daje serializer:

1. Walidację typów i pól wymaganych.
2. Custom walidację (`validate_<field>`, `validate`).
3. Kontrolę pól read-only/write-only.
4. Zagnieżdżone serializery dla powiązanych encji.

#### Praktyczne rekomendacje:

1. Nie wystawiaj modelu "as is" bez jawnego kontraktu serializera.
2. Utrzymuj schemat API stabilny i backward-compatible.
3. Custom reguły biznesowe waliduj w serializerze albo w warstwie serwisowej.
4. Dla różnych use-case twórz osobne serializery (list/detail/create/update).

#### Wniosek:

Serializacja to rdzeń warstwy API w Django/DRF: odpowiada za format danych,
walidację i stabilność kontraktu między serwerem a klientami.

</details>

<details>
<summary>95. Jakie są cechy Django z REST frameworkiem (DRF)?</summary>

#### Django

Django + DRF to połączenie dojrzałego web frameworka i mocnej warstwy API.
Dobrze sprawdza się dla produkcyjnych usług REST z klarownym modelem domenowym.

#### Kluczowe cechy DRF w ekosystemie Django:

1. **Serializer-first podejście**

- Jasny kontrakt API, walidacja danych wejściowych, kontrola pól.

2. **Elastyczna budowa endpointów**

- `APIView`, `GenericAPIView`, `ViewSet`, `ModelViewSet`.

3. **Automatyczny routing**

- Routery znacząco redukują boilerplate dla CRUD API.

4. **Auth + permissions**

- Session, Token, JWT (przez pakiety), custom klasy uprawnień.

5. **Pagination, filtering, ordering**

- Gotowe mechanizmy dla list i wyszukiwania.

6. **Throttling**

- Ograniczanie częstotliwości zapytań (anti-abuse / API hygiene).

7. **Content negotiation**

- Wsparcie dla różnych renderer/parser (domyślnie JSON).

8. **Browsable API**

- Wygodny interfejs deweloperski do ręcznej weryfikacji endpointów.

#### Typowy production stack z DRF:

1. Versioned API (`/api/v1/...`).
2. Serializery pod różne scenariusze (`list/detail/create/update`).
3. Permission policy per endpoint.
4. Standaryzowany format błędów.
5. Paginacja + filtrowanie + indeksacja DB.

#### Mocne strony podejścia:

1. Wysoka szybkość developmentu bez utraty struktury.
2. Kompatybilność z Django auth/admin/ORM/migrations.
3. Łatwe rozszerzanie custom klasami pod wymagania biznesowe.

#### Na co uważać:

1. Nie przeciążać `ModelViewSet` złożoną logiką domenową.
2. Kontrolować zapytania N+1 w serializerach/viewsetach.
3. Wyraźnie oddzielać kontrakt API od wewnętrznego modelu danych.

#### Wniosek:

DRF czyni Django silnym API frameworkiem klasy enterprise: szybki start,
uporządkowana architektura, dojrzałe bezpieczeństwo i skalowalność dla realnych
produktów multi-client.

</details>

<details>
<summary>96. Jaką rolę zajmuje Django w architekturze serwisów i REST API?</summary>

#### Django

W nowoczesnej architekturze Django najczęściej pełni rolę **głównego backendu
biznesowego**: zarządza logiką domenową, danymi transakcyjnymi, procesami
administracyjnymi i REST API dla klientów web/mobile.

#### Typowe role Django w architekturze:

1. **Modularny monolit (najczęściej)**

- Jeden serwis z czytelną dekompozycją na aplikacje/domeny.
- Szybki rozwój produktu i prostszy model operacyjny.

2. **Serwis API (DRF)**

- Czysty backend dla SPA/mobile/integracji partnerskich.

3. **Core service w ekosystemie mikroserwisowym**

- Django jako "source of truth" dla krytycznych domen (użytkownicy, billing,
  zamówienia).

4. **Backoffice/Admin service**

- Wewnętrzna obsługa operacyjna przez Django Admin + custom UI.

#### Dlaczego Django dobrze pasuje do tej roli:

1. Szybki development pełnego cyklu backendowego.
2. Mocny ORM + model transakcyjny.
3. Dojrzały system auth/permissions.
4. DRF dla standaryzowanego API.
5. Niezawodny panel admina dla zespołów operacyjnych.

#### Gdzie Django może nie być idealnym "first choice":

1. Ultra lekkie high-concurrency API-only serwisy (czasem lepszy FastAPI).
2. Specyficzne scenariusze low-latency z minimalnym framework overhead.

#### Praktyczne podejście architektoniczne:

1. Start od monolitu Django z jasnymi granicami domen.
2. Wydzielanie osobnych serwisów tylko przy realnej potrzebie skalowania.
3. Zostawienie Django jako core node dla domain/API/admin.

#### Integracja z innymi serwisami:

- Celery/kolejki dla async processing
- Redis dla cache
- Search engine dla full-text
- Object storage/CDN dla mediów
- Observability stack (logi, metryki, tracing)

#### Wniosek:

Django zajmuje mocną pozycję jako backbone dla serwisów biznesowych i REST API.
W większości produktów to praktyczny kompromis między szybkością developmentu,
dyscypliną architektoniczną i długoterminową utrzymywalnością.

</details>

<details>
<summary>97. Jak wdrożyć projekt Django (WSGI, ASGI, Nginx)?</summary>

#### Django

Deploy Django na production zwykle wygląda tak:

1. **Nginx** - reverse proxy, static/media, TLS.
2. **App server** - Gunicorn (WSGI) albo Uvicorn/Daphne (ASGI).
3. **Django app** - logika biznesowa.
4. **PostgreSQL/Redis** - dane i cache/kolejki.

#### WSGI vs ASGI:

1. **WSGI (Gunicorn)**

- Klasyczny, stabilny wariant dla synchronicznych aplikacji Django.

2. **ASGI (Uvicorn/Daphne)**

- Potrzebny dla async views, websocketów i nowoczesnych scenariuszy async.

#### Minimalny production flow:

1. Przygotować środowisko:

- `DEBUG=False`
- `ALLOWED_HOSTS`
- sekrety przez env

2. Zainstalować zależności:

```bash
pip install gunicorn
```

3. Zebrać statyczne pliki:

```bash
python manage.py collectstatic --noinput
```

4. Wykonać migracje:

```bash
python manage.py migrate
```

5. Uruchomić app server:

```bash
gunicorn config.wsgi:application --bind 127.0.0.1:8000 --workers 4
```

#### Przykład Nginx (uproszczony):

```nginx
server {
    listen 80;
    server_name example.com;

    location /static/ {
        alias /srv/app/staticfiles/;
    }

    location /media/ {
        alias /srv/app/media/;
    }

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

#### Dla ASGI deployu:

```bash
uvicorn config.asgi:application --host 127.0.0.1 --port 8000 --workers 4
```

#### Obowiązkowy security/ops checklist:

1. HTTPS (Let’s Encrypt), secure cookies.
2. `CSRF_TRUSTED_ORIGINS` i poprawne proxy headers.
3. `SECURE_HSTS_SECONDS`, `SECURE_SSL_REDIRECT`, `X_FRAME_OPTIONS`.
4. Logi, monitoring, alerty (error rate, latency, DB health).
5. Backup i sprawdzony plan rollbacku.

#### Typowe błędy:

1. `DEBUG=True` na production.
2. Brak `collectstatic` przed releasem.
3. Błędne `ALLOWED_HOSTS` / proxy headers -> problemy CSRF/redirect.
4. Uruchamianie Django development server (`runserver`) na production.

#### Wniosek:

Stabilny deploy Django to połączenie Nginx + WSGI/ASGI app server + poprawna
konfiguracja bezpieczeństwa i observability. Technicznie to proste, jeśli jest
dyscyplina procesu release.

</details>

<details>
<summary>98. Jak skalować aplikację Django?</summary>

#### Django

Skalowanie Django to nie jeden krok, tylko sekwencja decyzji na poziomie kodu,
DB, cache, kolejek i infrastruktury. Najlepsza strategia: skalować na podstawie
metryk, a nie "na zapas".

#### 1. Optymalizacja aplikacji (pierwszy etap)

1. Usunięcie zapytań N+1 (`select_related`, `prefetch_related`).
2. Optymalizacja ciężkich endpointów (pagination, limity, indeksy).
3. Minimalizacja payload API/HTML.
4. Dodanie cache tam, gdzie są powtarzalne "gorące" zapytania.

#### 2. Cache i przyspieszenie odczytu

1. Redis dla low-level/per-view/fragment cache.
2. CDN dla static/media.
3. Nagłówki HTTP cache dla zasobów publicznych.

#### 3. Skalowanie horyzontalne warstwy app

1. Uruchamianie wielu instancji Django za load balancerem.
2. Stateless procesy app (sesje w Redis/DB, bez lokalnego stanu).
3. Autoscaling wg CPU/RPS/latency.

#### 4. Wyniesienie ciężkich zadań do tła

1. Celery/RQ dla asynchronicznych jobów.
2. Kolejki dla emaili, raportów, integracji, importów.
3. Retry/backoff i idempotency dla niezawodności.

#### 5. Skalowanie bazy danych

1. Indeksy i query tuning.
2. Connection pooling (PgBouncer).
3. Read replicas dla scenariuszy read-heavy.
4. Partitioning/sharding - tylko przy realnej potrzebie i jasnej architekturze.

#### 6. Ewolucja architektury

1. Od "monolitu bez granic" -> do modularnego monolitu.
2. Wydzielanie usług tylko dla rzeczywiście wąskich domen.
3. Bez przedwczesnego przechodzenia na mikroserwisy.

#### 7. Observability jako warunek skalowania

1. Metryki: p95/p99 latency, error rate, queue lag, DB locks.
2. Logi z request-id.
3. Tracing między serwisami/kolejkami.
4. Alerty na naruszenia SLA/SLO.

#### Typowe błędy:

1. Skalowanie infrastruktury bez optymalizacji zapytań.
2. Cache bez strategii inwalidacji.
3. Ignorowanie wąskiego gardła po stronie DB.
4. Przedwczesna złożoność mikroserwisowa.

#### Wniosek:

Skalowanie Django to kontrolowany proces: najpierw optymalizacja kodu i DB,
potem cache i kolejki, dalej skalowanie horyzontalne instancji app i dopiero
później komplikowanie architektury. Decyzje powinny wynikać z metryk.

</details>

<details>
<summary>99. Jakie są podejścia do deployu i monitoringu aplikacji Django?</summary>

#### Django

Niezawodne production dla Django opiera się na dwóch filarach:

1. **kontrolowany deploy**
2. **pełny monitoring (observability)**

#### Podejścia do deployu:

1. **Klasyczny deploy VM/VPS**

- Nginx + Gunicorn/Uvicorn + systemd + PostgreSQL/Redis.
- Dobre dla kontrolowanego środowiska self-hosted.

2. **Container-based (Docker/Kubernetes)**

- Przewidywalne środowisko, skalowanie przez repliki.
- Wygodne dla zespołów z procesami DevOps.

3. **PaaS/Managed platformy**

- Szybszy start, mniej kosztów operacyjnych.
- Kompromis w elastyczności infrastruktury.

#### Rekomendowany pipeline release:

1. CI: testy + lint + security checks.
2. Build immutable artifact (image).
3. Deploy na staging.
4. Smoke/health checks.
5. Production rollout (blue/green, rolling albo canary).
6. Automatyczny rollback przy degradacji.

#### Co monitorować obowiązkowo:

1. **Application metrics**

- RPS, p95/p99 latency, 4xx/5xx error rate.

2. **Infrastructure metrics**

- CPU, RAM, disk, network, restart rate kontenerów/podów.

3. **Database metrics**

- slow queries, locks, connections, replication lag.

4. **Queue/worker metrics**

- queue depth, task latency, retry/failure rate.

5. **Logs + tracing**

- structured logs, request-id, distributed tracing.

#### Minimalny zestaw production:

1. Health endpointy (`/health/live`, `/health/ready`).
2. Centralizacja logów (ELK/Loki/Cloud logs).
3. APM/metrics (Prometheus + Grafana, Datadog, New Relic, Sentry).
4. Alerty na naruszenia SLO, nie tylko "serwer padł".

#### Praktyczne rekomendacje:

1. Przygotuj runbook incydentowy (kto/co/jak odtwarza usługę).
2. Utrzymuj migracje backward-compatible dla zero/min-downtime release.
3. Automatyzuj sekrety i config przez env/secret manager.
4. Regularnie ćwicz rollback i disaster recovery.

#### Typowe błędy:

1. Deploy bez health checks i strategii rollback.
2. Monitoring tylko CPU bez metryk biznesowych i latency.
3. Brak powiązania logów z konkretnym request/trace id.
4. Ręczne "hot fixy" na serwerze bez odtworzenia ich w kodzie.

#### Wniosek:

Skuteczny deploy Django to przewidywalny proces CI/CD, a stabilna praca to
monitoring dający wczesny sygnał degradacji. Bez observability nawet dobry kod
szybko traci sterowalność na production.

</details>

<details>
<summary>100. Jakie zmiany zwykle zawierają patch releasy i dlaczego warto się aktualizować?</summary>

#### Django

Patch releasy (np. `5.1.2 -> 5.1.3`) zwykle zawierają **wstecznie kompatybilne**
poprawki bez zmian publicznego API, które łamią aplikację na poziomie
major/minor.

#### Co zwykle wchodzi do patch release:

1. **Security fixes**

- Zamknięcie podatności (często krytyczne dla production).

2. **Bug fixes**

- Poprawki błędów w ORM, forms, middleware, admin, migrations itd.

3. **Stability improvements**

- Lepsza kompatybilność z zależnościami, poprawki edge case.

4. **Drobne ulepszenia docs/test**

- Bez zmian kontraktu architektonicznego aplikacji.

#### Dlaczego ważne jest aktualizowanie:

1. **Bezpieczeństwo**

- Pominięty security patch może zostawić znaną podatność na produkcji.

2. **Niezawodność**

- Patch releasy usuwają błędy, które potrafią ujawniać się pod obciążeniem.

3. **Kompatybilność**

- Nowsze biblioteki oczekują aktualnych patch wersji frameworka.

4. **Prostsza ścieżka upgrade**

- Regularne małe aktualizacje są łatwiejsze niż rzadkie duże skoki.

#### Praktyczny proces aktualizacji:

1. Zaktualizować zależność (`pip`/`poetry`/`uv`).
2. Uruchomić testy i lintery.
3. Sprawdzić changelog/release notes.
4. Wdrożyć na staging.
5. Wypuścić na production przez kontrolowany rollout.

#### Częstotliwość:

- Sprawdzać patch aktualizacje regularnie (minimum raz w miesiącu albo po
  security advisory).
- Dla wersji LTS instalować security patche możliwie szybko.

#### Typowe błędy:

1. Odkładanie patch aktualizacji "na później".
2. Aktualizacja na production bez weryfikacji na staging/CI.
3. Ignorowanie release notes i potencjalnych efektów ubocznych.

#### Wniosek:

Patch releasy to nie "kosmetyka", tylko higiena operacyjna projektu. Regularne
aktualizacje Django redukują ryzyko bezpieczeństwa, podnoszą stabilność i
ułatwiają przyszłe upgrade'y.

</details>
