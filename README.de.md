**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  Django <img src="./assets/django.svg" width="40" height="40" alt="Django logo"/>
</h1>

<h2>Die beliebtesten Django-Interviewfragen und -antworten</h2>

<details>
<summary>1. Was ist Django und was sind seine wichtigsten Fähigkeiten?</summary>

#### Django

Django ist ein High-Level-Python-Framework für die Entwicklung von
Webanwendungen nach dem Prinzip „batteries included“: Die meisten typischen
Aufgaben sind im Framework-Ökosystem bereits gelöst.

#### Wichtige Fähigkeiten von Django:

1. **Schneller Entwicklungsstart:** Projekt- und App-Scaffolding, fertige
   Struktur und klare Konventionen.
2. **Integriertes Admin-Panel:** automatisch generiertes Django Admin zur
   Datenverwaltung im Browser.
3. **Leistungsfähiges ORM:** Arbeit mit der Datenbank über Python-Modelle, in
   den meisten Fällen ohne manuelles SQL.
4. **Migrationssystem:** Kontrolle und Versionierung von Schemaänderungen der
   DB.
5. **URL-Routing und View-Schicht:** klare Trennung von Routing, Geschäftslogik
   und Darstellung.
6. **Template-Engine:** integrierte Templates für HTML-Rendering mit
   Template-Vererbung.
7. **Sicherheit by default:** Schutz vor CSRF, XSS, SQL-Injection, Clickjacking
   sowie sichere Authentifizierungspraktiken.
8. **Integrierte Authentifizierung:** Benutzer, Gruppen, Berechtigungen,
   Sessions.
9. **Formularverarbeitung:** Django Forms/ModelForms mit serverseitiger
   Validierung.
10. **Skalierbarkeit und Ökosystem:** Caching, Middleware, Signals, Integration
    mit Celery, DRF, Redis, PostgreSQL usw.

#### Wann Django besonders geeignet ist:

- CRM/ERP und interne Business-Systeme.
- Content-Plattformen, Marktplätze, Benutzer-Dashboards.
- API + Webteil in einem Projekt.
- Produkte, bei denen Umsetzungsgeschwindigkeit, Sicherheit und Wartbarkeit
  wichtig sind.

#### Kurzes Beispiel: „Was Django out of the box liefert“:

```bash
django-admin startproject config .
python manage.py startapp users
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Danach hast du bereits ein grundlegendes Projektgerüst, eine angebundene
Datenbank, ein Migrationssystem und Zugriff auf das Admin-Panel.

#### Fazit:

Django ist eine praktische Wahl für schnelle und sichere Backend-Entwicklung,
besonders wenn eine reife Architektur, ein stabiler Stack und ein schneller
Produktstart gefragt sind.

</details>

<details>
<summary>2. Welche Vorteile bietet die Nutzung von Django?</summary>

#### Django

Django wird häufig für kommerzielle Entwicklung gewählt, wenn ein schneller
Time-to-Market, eine stabile Architektur und ein sicherer Backend-Stack ohne
unnötiges „Zusammenkleben“ dutzender Drittanbieter-Bibliotheken benötigt werden.

#### Zentrale Vorteile von Django:

1. **Hohe Entwicklungsgeschwindigkeit:** Viele typische Aufgaben sind bereits
   umgesetzt (Auth, Admin, Forms, ORM, Sessions, Cache).
2. **Sicherheit out of the box:** Eingebaute Mechanismen gegen CSRF, XSS,
   SQL-Injection, Clickjacking sowie sichere Passwortverarbeitung.
3. **Klare Projektstruktur:** Verständliche Konventionen erleichtern Team-
   Onboarding und langfristige Wartung des Codes.
4. **Leistungsfähiges ORM und Migrationen:** Schnelle DB-Arbeit, kontrollierte
   Schema-Evolution, gute Unterstützung für PostgreSQL und andere relationale
   Datenbanken.
5. **Admin-Panel für Fachbereiche:** Mit Django Admin erhält
   Content-/Operations- Team schnell ein nutzbares Interface ohne separate
   Frontend-Entwicklung.
6. **Gute architektonische Skalierbarkeit:** Apps, Middleware, Signals, Celery,
   Caches und Queues lassen sich leicht in Production-Szenarien integrieren.
7. **Reifes Ökosystem:** DRF, django-allauth, django-filter, django-celery-beat
   und weitere bewährte Tools.
8. **Eignung für Enterprise-Projekte:** Vorhersagbare Releases, große Community,
   hochwertige Dokumentation und stabile Best Practices.

#### Praktischer Mehrwert für das Team:

- Weniger Infrastruktur-Code am Anfang.
- Weniger Risiko für Sicherheitsfehler in der Basisimplementierung.
- Schnellere MVP-Auslieferung und klarerer Weg zur Skalierung.
- Bessere Wartbarkeit bei wachsendem Team und Codebase.

#### Wann die Vorteile besonders spürbar sind:

- B2B-SaaS, CRM/ERP, Nutzer-Dashboards, Marktplätze.
- Projekte mit viel Geschäftslogik und Rollen-/Rechtekonzepten.
- Teams, denen Stabilität und planbare Produktentwicklung wichtig sind.

#### Fazit:

Der Vorteil von Django liegt darin, dass es schnellen Business-Impact liefert,
ohne Kompromisse bei Sicherheit und Wartbarkeit des Codes.

</details>

<details>
<summary>3. Was ist der Unterschied zwischen MVC- und MVT-Architektur?</summary>

#### Django

In Django spricht man häufiger über **MVT (Model-View-Template)**, während in
vielen anderen Frameworks der Begriff **MVC (Model-View-Controller)** verwendet
wird. Konzeptionell sind diese Ansätze sehr ähnlich; der Unterschied liegt
hauptsächlich in Rollen und Benennung.

#### MVC (klassisch):

1. **Model** - Arbeit mit Daten und Geschäftslogik.
2. **View** - Darstellung der Daten (UI / Presentation Layer).
3. **Controller** - verarbeitet eingehende Requests und steuert den Flow
   zwischen Model und View.

#### MVT in Django:

1. **Model** - Datenmodelle und DB-Zugriff über ORM.
2. **View** - Verarbeitung des HTTP-Requests, Ausführung der Geschäftslogik,
   Vorbereitung der Response.
3. **Template** - Darstellungsschicht (HTML + Template-Syntax).

#### Zuordnung MVC <-> MVT:

- `Model (MVC)` ≈ `Model (Django MVT)`
- `View (MVC)` ≈ `Template (Django MVT)`
- `Controller (MVC)` ≈ `View + URL dispatcher (Django MVT)`

In Django ist die Rolle des „Controllers“ also aufgeteilt zwischen `urls.py`
(Routing) und `views.py` (Request-Verarbeitung).

#### Einfacher Django-Flow (MVT):

1. Ein Request trifft auf eine URL, z. B. `/articles/`.
2. `urls.py` leitet ihn an die passende `view` weiter.
3. Die `view` holt Daten aus dem `Model`.
4. Die `view` übergibt Daten an das `Template`.
5. Das `Template` rendert HTML und es wird als `HttpResponse` zurückgegeben.

#### Fazit:

- Django „bricht“ MVC nicht, sondern setzt es in seiner MVT-Variante um.
- Der praktische Kernunterschied: In Django ist `view` die
  Request-Verarbeitungslogik, während die visuelle Darstellung im `template`
  liegt.

</details>

<details>
<summary>4. Warum wird Django als loosely coupled Framework bezeichnet?</summary>

#### Django

Django gilt als **loosely coupled** (lose gekoppelt), weil seine Komponenten
unabhängig voneinander geändert, erweitert oder ersetzt werden können, ohne die
gesamte Anwendung neu zu schreiben.

#### Was das in der Praxis bedeutet:

1. **Komponenten sind nach Verantwortung getrennt:** URL-Routing, Views,
   Templates, Modelle, Formulare, Middleware arbeiten zusammen, sind aber nicht
   zu einer monolithischen Logikschicht „verschmolzen“.
2. **Plugin-artige App-Architektur:** Das Projekt besteht aus `apps`, die über
   `INSTALLED_APPS` aktiviert/deaktiviert werden können.
3. **Austauschbarkeit einzelner Teile:** z. B. Template-Engine, User-Modell,
   Cache-Backend, Email-Backend, Storage-Backend.
4. **Konfiguration über Settings:** Das Systemverhalten wird über Einstellungen
   gesteuert, nicht über hart codierte Logik.
5. **Erweiterung über Middleware und Signals:** Funktionalität kann ergänzt
   werden, ohne die Kern-Business-Logik zu verändern.

#### Typische Beispiele für den loosely-coupled Ansatz in Django:

- SQLite durch PostgreSQL ersetzen nur über `DATABASES`-Einstellungen.
- Redis-Cache hinzufügen, ohne Views und Modelle umzuschreiben.
- Von lokalem Dateispeicher auf S3-kompatiblen Storage per Backend wechseln.
- Auth auf ein Custom User Model (`AUTH_USER_MODEL`) umstellen, ohne die
  Gesamtarchitektur zu brechen.

#### Warum das für Teams wichtig ist:

- Das Produkt lässt sich modular einfacher skalieren.
- Einzelne Systemteile sind leichter testbar.
- Geringeres Risiko beim Refactoring.
- Bessere Wartbarkeit über den langen Lebenszyklus eines Projekts.

#### Fazit:

Loosely coupled in Django bedeutet technische Flexibilität: Das Projekt kann
schrittweise weiterentwickelt werden, indem einzelne Subsysteme angepasst
werden, statt alles auf einmal umzubauen.

</details>

<details>
<summary>5. Was ist der Unterschied zwischen Django und FastAPI?</summary>

#### Django

Django und FastAPI lösen unterschiedliche Aufgaben. Beide Frameworks sind stark,
werden aber für verschiedene Produkttypen und Teams gewählt.

#### Kernunterschied:

- **Django** - ein vollwertiges Web-Framework out of the box (ORM, Admin, Auth,
  Templates, Forms, Sessions, Middleware).
- **FastAPI** - ein leichtgewichtiges und sehr schnelles ASGI-Framework, primär
  auf API-Entwicklung mit Typisierung und automatischer Dokumentation
  ausgerichtet.

#### Vergleich Django vs FastAPI:

1. **Einsatzzweck**

- Django: vollständige Websysteme und APIs in einem Projekt.
- FastAPI: API-first, Microservices, High-Concurrency-Services.

2. **Projekt-Startgeschwindigkeit**

- Django: sehr schnell für CRUD/Admin-Dashboards/Benutzerbereiche.
- FastAPI: schnell für APIs, aber mehr Bausteine müssen selbst zusammengesetzt
  werden.

3. **Performance**

- Django: ausreichend für die meisten Business-Szenarien; klassisch WSGI,
  unterstützt aber auch ASGI-Modus.
- FastAPI: meist höhere Performance bei I/O-Last dank async-first-Ansatz.

4. **ORM und DB-Arbeit**

- Django: reifes eingebautes ORM + Migrationen.
- FastAPI: kein eingebautes ORM; häufig SQLAlchemy/SQLModel/Tortoise.

5. **Admin und Backoffice**

- Django: leistungsfähiges Django Admin out of the box.
- FastAPI: Admin muss separat gebaut oder integriert werden.

6. **Validierung und Schemas**

- Django: Forms/DRF-Serializer.
- FastAPI: Pydantic-Modelle als De-facto-Standard.

7. **API-Dokumentation**

- Django: üblicherweise über DRF + Swagger/OpenAPI-Pakete.
- FastAPI: OpenAPI/Swagger UI wird automatisch generiert.

8. **Ökosystem**

- Django: sehr breit für Webprodukte (CMS, Auth, Admin-Patterns).
- FastAPI: stark bei APIs/Microservices, moderner Async-Stack.

#### Wann Django wählen:

- Es wird ein All-in-one-Backend mit schnellem Business-Output benötigt.
- Es gibt ein komplexes Rollen-/Rechtemodell, Admin-Bereich und viele
  CRUD-Entitäten.
- Das Team braucht stabile Konventionen und langfristige Wartbarkeit.

#### Wann FastAPI wählen:

- Es wird ein API-first-Service mit hoher Request-Konkurrenz benötigt.
- Priorität: async Integrationen (externe APIs, Queues, Streaming,
  WebSocket-Szenarien).
- Das Team möchte einen möglichst schlanken und kontrollierten Stack.

#### Fazit:

- **Django** ist optimal für schnellen Start von Business-Funktionalität und
  komplexen Websystemen.
- **FastAPI** ist optimal für performante moderne APIs und Microservice-
  Szenarien.
- In großen Produkten existieren beide oft nebeneinander: Django als Core/Admin,
  FastAPI als separate API-Services.

</details>

<details>
<summary>6. Welche Nachteile und Einschränkungen hat Django im Vergleich zu anderen Frameworks?</summary>

#### Django

Django ist ein starkes Framework, aber nicht in jedem Projekttyp die beste Wahl.
Seine Grenzen zeigen sich meist in spezifischen technischen Szenarien.

#### Zentrale Nachteile und Einschränkungen von Django:

1. **Schwergewichtiger Einstieg für sehr einfache Services**

- Für kleine Microservices kann Django durch den Umfang integrierter Komponenten
  überdimensioniert sein.

2. **Weniger „native async-first“-Erlebnis als bei FastAPI**

- Django unterstützt Async, aber historisch ist ein großer Teil des Ökosystems
  sync-orientiert.
- Für stark I/O-lastige APIs bieten FastAPI/Starlette teils den einfacheren Weg.

3. **ORM nicht ideal für sehr komplexes SQL**

- Das Django-ORM ist für die meisten Aufgaben stark, aber bei sehr komplexen
  analytischen Queries oder DB-spezifischer Optimierung ist oft dennoch Raw SQL
  nötig.

4. **Strenge Konventionen**

- Django-Konventionen sind für Teams ein Vorteil, können aber für Entwickler,
  die maximalen Low-Level-Kontrollgrad wollen, einschränkend wirken.

5. **Monolithischer Default-Stil**

- Django führt natürlicherweise zum modularen Monolithen statt zu vielen kleinen
  Microservices.
- Für eine microservice-first-Architektur braucht es klare Abgrenzungsdisziplin.

6. **Zusätzliche Schritte für modernes API-first-DX**

- Für vollständige REST-APIs nutzt man meist DRF, für OpenAPI zusätzliche Tools,
  für Realtime einen separaten Stack (z. B. Channels).

7. **Out-of-the-box-Performance ist nicht immer maximal**

- Ohne Caching, DB-Indizes, ORM-Optimierung und sauberes Profiling können große
  Systeme langsamer laufen.

#### Häufige Fehler, die mit „Django-Nachteilen“ verwechselt werden:

- N+1-Queries durch falsche ORM-Nutzung.
- Fehlende Caching-Strategie.
- Schlechte modulare App-Dekomposition.
- Vermischung von Business-Logik in Views ohne Service-Schicht.

Das sind häufiger Architekturthemen des Teams als Schwächen des Frameworks
selbst.

#### Wann Django nicht die beste Wahl sein kann:

- Sehr schlanke API-Services mit minimaler Geschäftslogik.
- High-Throughput-Async-APIs als Hauptanforderung.
- Systeme mit Bedarf an maximaler low-level Kontrolle ohne „schweren“
  Framework-Kern.

#### Fazit:

Djangos Einschränkungen sind real, aber gut vorhersehbar. Für die meisten
Business-Anwendungen überwiegen seine Vorteile (Entwicklungsgeschwindigkeit,
Sicherheit, Wartbarkeit). Entscheidend ist, das Framework nach Aufgabenkontext
zu wählen, nicht nach Trend.

</details>

<details>
<summary>7. Wie funktioniert Django (Request-Response-Lebenszyklus)?</summary>

#### Django

Der Lebenszyklus in Django ist die Abfolge von Schritten vom Eingang eines
HTTP-Requests auf dem Server bis zur finalen HTTP-Response für den Client.

#### Ablauf der Request-Verarbeitung:

1. **Client sendet einen HTTP-Request**

- Browser oder API-Client ruft die Django-Anwendung auf.

2. **WSGI/ASGI-Server übergibt den Request an Django**

- Zum Beispiel: Gunicorn/Uvicorn + Nginx.

3. **Request durchläuft Middleware (Request-Phase)**

- Middleware kann den Request ändern/anreichern: Authentifizierung, Sessions,
  Locale, Security-Prüfungen usw.

4. **URL-Resolver sucht passende Route**

- Django matched die URL mit Regeln in `urls.py`.
- Falls keine Route gefunden wird -> `404 Not Found`.

5. **View wird aufgerufen**

- Die View erhält `request` und führt Business-Logik aus: Daten lesen/schreiben,
  Zugriffsprüfung, Kontextaufbau.

6. **Arbeit mit Modellen und DB (bei Bedarf)**

- Über ORM (`Model.objects...`) oder Raw SQL für komplexe Fälle.

7. **Response-Erzeugung**

- HTML via `render(...)` + Template,
- oder JSON via `JsonResponse`,
- oder Redirect / File Response.

8. **Response durchläuft Middleware (Response-Phase)**

- Middleware kann Header, Cookies, Cache-Control, Logging ergänzen.

9. **Response wird an den Client zurückgegeben**

- Browser rendert die Seite oder der Client verarbeitet die API-Response.

#### Was bei Fehlern passiert:

- `Http404` oder fehlende Route -> 404-Seite.
- Unbehandelte Exceptions -> 500-Seite.
- Auch Exception-Handling läuft durch die Middleware-Kette.

#### Kurz dargestellt:

`Client -> Server (WSGI/ASGI) -> Middleware (request) -> URLconf -> View -> Model/ORM -> Template/Serializer -> Middleware (response) -> Client`

#### Fazit:

Die Stärke von Django liegt in der vorhersagbaren Request/Response-Pipeline: Sie
ist leicht zu debuggen, zu testen und zu skalieren, weil jeder Schritt eine
klare Verantwortung hat.

</details>

<details>
<summary>8. Wie erstellt man ein neues Django-Projekt?</summary>

#### Django

Ein neues Django-Projekt wird in einigen Standardschritten erstellt: Umgebung
vorbereiten, Django installieren, Projekt generieren, Migrationen anwenden und
Server starten.

#### Schritt für Schritt:

1. **Projektverzeichnis erstellen**

```bash
mkdir my_django_project
cd my_django_project
```

2. **Virtuelle Umgebung erstellen und aktivieren**

```bash
python -m venv .venv
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate         # Windows (PowerShell/CMD)
```

3. **Django installieren**

```bash
pip install django
```

4. **Projekt generieren**

```bash
django-admin startproject config .
```

Danach werden zentrale Dateien erstellt:

- `manage.py`
- `config/settings.py`
- `config/urls.py`
- `config/asgi.py`
- `config/wsgi.py`

5. **Initiale Migrationen anwenden**

```bash
python manage.py migrate
```

6. **Admin-Benutzer erstellen**

```bash
python manage.py createsuperuser
```

7. **Dev-Server starten**

```bash
python manage.py runserver
```

#### Prüfung:

- Öffne `http://127.0.0.1:8000/` - Django-Startseite.
- Öffne `http://127.0.0.1:8000/admin/` - Admin-Panel (nach `createsuperuser`).

#### Empfohlener nächster Schritt:

Erstelle die erste App und füge sie in `INSTALLED_APPS` ein:

```bash
python manage.py startapp core
```

Das ist ein sauberer und praxisnaher Start für die meisten Django-Projekte.

#### Fazit:

Der Standard-Bootstrap-Prozess in Django ist einfach und vorhersehbar: Mit
wenigen Kommandos erhältst du ein lauffähiges Projektgerüst für die weitere
Entwicklung.

</details>

<details>
<summary>9. Warum ist es wichtig, in Django mit virtuellen Umgebungen zu arbeiten?</summary>

#### Django

Eine virtuelle Umgebung (`venv`) isoliert die Abhängigkeiten eines konkreten
Projekts vom globalen Python der Maschine. Für Django ist das kritisch, weil
Projekte oft unterschiedliche Bibliotheksversionen und
Kompatibilitätsanforderungen haben.

#### Warum das wichtig ist:

1. **Isolierung von Abhängigkeiten**

- Jedes Projekt nutzt eigene Versionen von `Django`, `djangorestframework`,
  `psycopg`, `celery` usw., ohne Konflikte mit anderen Projekten.

2. **Reproduzierbare Umgebung**

- Der Abhängigkeitszustand lässt sich in `requirements.txt` fixieren und auf
  anderen Maschinen oder Servern reproduzieren.

3. **Stabilere Deployments**

- Geringere Wahrscheinlichkeit für „works on my machine“, wenn lokal eine
  Paketversion läuft, in CI/Production aber eine andere.

4. **Sichere Updates**

- Upgrades von Django oder Drittanbieter-Paketen können getestet werden, ohne
  andere lokale Projekte zu gefährden.

5. **Sauberer System-Python**

- OS-Systemtools hängen nicht von Paketen ab, die du für Entwicklung
  installierst.

#### Was ohne `venv` passiert:

- Versionskonflikte zwischen Projekten.
- Unvorhersehbare Import-Fehler nach `pip install` neuer Pakete.
- Schweres Debugging in CI/CD wegen unterschiedlicher Umgebungen.
- Kaputte lokale Tools durch globale Updates.

#### Minimale Team-Praxis:

1. Für jedes Repository `.venv` im Projektroot anlegen.
2. Umgebung immer vor `pip install` und `manage.py`-Kommandos aktivieren.
3. Abhängigkeiten in `requirements.txt` festhalten (oder `pyproject.toml` +
   Lockfile).
4. `.venv/` in `.gitignore` aufnehmen.

#### Fazit:

`venv` ist in Django keine Option, sondern ein Basisstandard technischer
Disziplin. Es sorgt für Vorhersagbarkeit, Stabilität und einen gesunden
Team-Workflow.

</details>

<details>
<summary>10. Wie ist ein Django-Projekt aufgebaut und wofür dienen die Hauptdateien: manage.py, settings.py, urls.py?</summary>

#### Django

Ein typisches Django-Projekt hat zwei zentrale Teile: das Repository-Root und
das Konfigurationspaket (oft `config/`), in dem die globalen App-Einstellungen
liegen.

#### Grundstruktur eines Projekts:

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

#### Zweck der Hauptdateien:

1. **manage.py**

- CLI-Einstiegspunkt für lokale Projektarbeit.
- Darüber werden Kommandos ausgeführt: `runserver`, `migrate`, `makemigrations`,
  `createsuperuser`, `test`, `shell`.
- Gibt Django automatisch an, welches Settings-Modul zu nutzen ist.

2. **settings.py**

- Zentrale Projektkonfiguration.
- Hier werden definiert: `INSTALLED_APPS`, `MIDDLEWARE`, `DATABASES`,
  `TEMPLATES`, `CACHES`, `STATIC_URL`, `MEDIA_URL`, `AUTH_PASSWORD_VALIDATORS`,
  `TIME_ZONE` usw.
- Für Production trennt man Settings oft in Module: `settings/base.py`,
  `settings/dev.py`, `settings/prod.py`.

3. **urls.py**

- Globale Routing-Map (URL dispatcher).
- Nimmt den angefragten Pfad entgegen und delegiert ihn per `include()` an die
  jeweilige App.
- Häufig werden hier auch `admin/`, Health-Checks und API-Routing angebunden.

#### Wie das zusammenspielt:

1. `manage.py` startet ein Django-Kommando.
2. Django lädt `settings.py`.
3. Ein HTTP-Request durchläuft Middleware.
4. `urls.py` bestimmt, welche `view` den Request verarbeitet.
5. Die `view` liefert eine Response zurück (HTML/JSON/Redirect/Datei).

#### Praktische Tech-Lead-Empfehlungen:

- Halte `urls.py` schlank: Routing sollte primär auf App-Ebene liegen.
- Mache aus `settings.py` keine „Rumpelkammer“ - nutze modulare Struktur.
- Alle Secrets (Keys, Passwörter, Tokens) in Umgebungsvariablen speichern, nicht
  im Code.
- Business-Logik aus `views.py` in eine Service-Schicht auslagern, um Tests zu
  vereinfachen.

#### Fazit:

`manage.py`, `settings.py` und `urls.py` sind der operative Kern eines
Django-Projekts: Steuerung, Konfiguration und Routing. Eine klare Organisation
dieser Dateien beeinflusst direkt Skalierbarkeit und Wartbarkeit des Systems.

</details>

<details>
<summary>11. Wofür werden Django-Apps verwendet und wie organisiert man ein Projekt mit mehreren Apps?</summary>

#### Django

In Django ist eine `app` ein isoliertes Funktionsmodul mit eigenen Modellen,
Views, URLs, Templates, Tests und (bei Bedarf) API-Schicht. Apps dienen der
Domänentrennung und dem kontrollierten Wachstum der Codebasis.

#### Wofür Django-Apps verwendet werden:

1. **Modularität**

- Jede App ist für einen konkreten Business-Kontext zuständig (z. B. `users`,
  `billing`, `orders`, `notifications`).

2. **Wiederverwendbarkeit**

- Eine App kann in ein anderes Projekt übertragen oder intern wiederverwendet
  werden.

3. **Lokalisierung von Änderungen**

- Änderungen in einer Domäne beeinflussen andere Module weniger.

4. **Bessere Wartbarkeit**

- Das Team orientiert sich leichter im Code, wenn Verantwortlichkeiten klar
  getrennt sind.

5. **Einfacheres Testing**

- Tests werden domänenweise geschrieben und ausgeführt, nicht auf einem
  chaotischen Monolithen.

#### Wie man ein Projekt mit mehreren Apps organisiert:

1. **Nach Domäne aufteilen, nicht nach technischem Typ**

- Gut: `users`, `catalog`, `checkout`, `payments`.
- Schlecht: `models_app`, `views_app`, `utils_app`.

2. **Jede App hat eigene `urls.py`**

- In `config/urls.py` nur Einbindung via `include()`.

3. **Apps autonom halten**

- In jeder App sollten `models.py`, `views.py`, `tests.py`, `admin.py`,
  `apps.py`, `migrations/` vorhanden sein.

4. **Zyklische Abhängigkeiten zwischen Apps vermeiden**

- Für Interaktion zwischen Modulen besser Service-Schicht oder klare Interfaces
  nutzen, statt direkter „alles mit allem“-Imports.

5. **Gemeinsamen Code in separates `common/core`-Modul auslagern**

- Aber nur wirklich gemeinsamen Code; kein „Müllcontainer“-Modul daraus machen.

#### Beispielstruktur eines mehrmoduligen Projekts:

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

#### Einbindung der App-Routen:

```python
# config/urls.py
from django.urls import include, path

urlpatterns = [
    path("users/", include("apps.users.urls")),
    path("orders/", include("apps.orders.urls")),
]
```

#### Typische Anti-Patterns:

- Eine „riesige“ App für das ganze Projekt.
- Trennung nach technischen Schichten statt Business-Domänen.
- Massenhaft Shared-Code ohne Owner und Verträge.
- Unkontrollierte Cross-Imports zwischen Apps.

#### Fazit:

Django-Apps sind ein zentrales Werkzeug zur Code-Skalierung. Wenn man das System
entlang von Domänen mit klaren Grenzen aufteilt, bleibt das Projekt länger
beherrschbar und stabil.

</details>

<details>
<summary>12. Wie funktioniert URL-Routing in Django?</summary>

#### Django

URL-Routing in Django legt fest, welche `view` einen bestimmten HTTP-Request
verarbeiten soll. Dafür ist der URL-Dispatcher zuständig, konfiguriert in
`urls.py`.

#### So funktioniert URL-Routing Schritt für Schritt:

1. **Ein Request kommt bei Django an**

- Zum Beispiel: `GET /articles/42/`.

2. **Django liest die zentrale `urlpatterns`**

- Meist in `config/urls.py`.

3. **Sequenzielles Matching der Routen**

- Django prüft Pattern von oben nach unten.
- Der erste Treffer gewinnt.

4. **Bei Bedarf wird `include()` aufgerufen**

- Ein Teil der Route wird an `urls.py` einer konkreten App delegiert.

5. **URL-Parameter werden an die View übergeben**

- Zum Beispiel übergibt `articles/<int:id>/` den Wert `id` als Argument.

6. **Die View erzeugt eine Response**

- HTML, JSON, Redirect oder Datei.

7. **Wenn kein Match gefunden wird -> 404**

- Django liefert `Not Found` zurück.

#### Basisbeispiel:

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

#### Konverter in `path()`:

- `<int:id>` -> ganze Zahl
- `<str:slug>` -> String ohne `/`
- `<slug:slug>` -> Slug-Format
- `<uuid:id>` -> UUID
- `<path:subpath>` -> beliebiger Pfad inklusive `/`

#### Praktische Regeln für Wartbarkeit:

1. Halte die zentrale `urls.py` kurz, delegiere in Apps.
2. Nutze `name=` für jede Route (wichtig für `reverse()` und Templates).
3. Halte API/Web-URL-Struktur stabil (Versionierung, Präfixe).
4. Reihenfolge der Routen ist wichtig: spezifische Pattern über allgemeinen.

#### Fazit:

URL-Routing in Django ist ein kontrollierter Dispatcher-Mechanismus für
Requests. Gut entworfene Routen machen den Code vorhersehbar, skalierbar und
sicher refaktorierbar.

</details>

<details>
<summary>13. Unterschied zwischen `path()` und `re_path()`.</summary>

#### Django

`path()` und `re_path()` sind zwei Wege, URL-Routen in Django zu definieren.
Beide lösen dieselbe Aufgabe, unterscheiden sich aber in Komplexität und
Flexibilität.

#### `path()`:

- Nutzt eine klare, deklarative Syntax mit Konvertern.
- Geeignet für die meisten Standardrouten.
- Ist besser lesbar und leichter im Team wartbar.

Beispiel:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("posts/<int:post_id>/", views.post_detail, name="post_detail"),
    path("users/<slug:username>/", views.user_profile, name="user_profile"),
]
```

#### `re_path()`:

- Nutzt reguläre Ausdrücke (Regex).
- Bietet maximale Flexibilität für Sonderfälle bei URL-Pattern.
- Ist schwerer lesbar, höheres Risiko für Regex-Fehler.

Beispiel:

```python
from django.urls import re_path
from . import views

urlpatterns = [
    re_path(r"^archive/(?P<year>[0-9]{4})/$", views.archive_year),
    re_path(r"^file/(?P<path>.+\.(pdf|docx))/$", views.file_view),
]
```

#### Wann was verwenden:

1. **`path()` standardmäßig verwenden**

- Das ist der empfohlene Standardansatz in modernem Django.

2. **`re_path()` nur verwenden, wenn `path()` nicht ausreicht**

- Z. B. komplexe URL-Formatvalidierung auf Routing-Ebene oder
  Legacy-URL-Schemata.

#### Vergleich:

- Einfachheit: `path()` > `re_path()`
- Flexibilität: `re_path()` > `path()`
- Team-Wartbarkeit: meist ist `path()` besser

#### Praktischer Hinweis:

URLs nicht unnötig mit Regex verkomplizieren. Wenn die Aufgabe mit
`path()`-Konvertern + Prüfung in View/Serializer/Form lösbar ist, ist das meist
der bessere Weg.

#### Fazit:

`path()` ist das Hauptwerkzeug für 90% der Routen. `re_path()` ist eine gezielte
Lösung für Sonderfälle, in denen Regex-Flexibilität nötig ist.

</details>

<details>
<summary>14. Wie funktionieren URL-Konfigurationen und `include()`?</summary>

#### Django

URL-Konfiguration in Django ist ein Regelset (`urlpatterns`), das den
Request-Pfad einer konkreten `view` zuordnet. Die Funktion `include()` erlaubt,
großes Routing in app-basierte Module aufzuteilen.

#### Was URL-Konfiguration ist:

- Ein Python-Modul (meist `urls.py`) mit einer Routenliste.
- Jede Route wird über `path()` oder `re_path()` definiert.
- Django geht die Liste von oben nach unten durch und nimmt den ersten Treffer.

#### Wozu `include()` dient:

1. **Dekomposition des Routings**

- Die Root-`urls.py` bleibt kurz und übersichtlich.

2. **Modularität nach Apps**

- Jede App hat eigene Routen in ihrer `urls.py`.

3. **Bessere Wartbarkeit**

- Das Team arbeitet im lokalen Routing-Kontext der jeweiligen Domäne.

#### Beispielorganisation:

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

#### So funktioniert die Kette mit `include()`:

1. Request `/blog/django-routing/` kommt in `config/urls.py` an.
2. Präfix `blog/` matcht.
3. Django übergibt den Restpfad (`django-routing/`) an `apps.blog.urls`.
4. Dort wird die passende Route gefunden und die richtige `view` aufgerufen.

#### Namespace und `app_name`:

- `app_name` + Routen-`name` ergibt einen benannten Namespace.
- Damit funktioniert konfliktfreies Reverse:
  `reverse("blog:detail", kwargs={"slug": "django-routing"})`.

#### Praktische Empfehlungen:

1. Auf App-Ebene immer `include()` verwenden.
2. In jeder App-`urls.py` `app_name` setzen.
3. Präfixe stabil halten (`api/v1/`, `admin/`, `auth/`).
4. Keine Business-Logik in die URL-Schicht legen - nur Routing.

#### Fazit:

URL-Konfigurationen + `include()` sind die Basis für skalierbares Routing in
Django: klare App-Grenzen, sauberes Root-Routing und vorhersehbare Navigation.

</details>

<details>
<summary>15. Was ist eine View in Django?</summary>

#### Django

Eine `view` in Django ist ein HTTP-Request-Handler. Die View nimmt den `request`
entgegen, führt die nötige Logik aus und gibt eine `HttpResponse` zurück (HTML,
JSON, Redirect, Datei).

#### Rolle der View im Request/Response-Zyklus:

1. Request nach URL-Matching entgegennehmen.
2. Eingabeparameter prüfen (path/query/body/files).
3. Business-Logik und/oder ORM aufrufen.
4. Daten für die Response vorbereiten.
5. Gültige HTTP-Response zurückgeben.

#### Welche View-Typen es gibt:

1. **FBV (Function-Based View)**

- Normale Python-Funktion.
- Geeignet für einfache oder stark individuelle Logik.

2. **CBV (Class-Based View)**

- Klasse mit Methoden wie `get()`, `post()` usw.
- Besser skalierbar für typische CRUD-Szenarien, besonders mit Generic Views.

#### FBV-Beispiel:

```python
from django.http import HttpResponse, JsonResponse
from django.shortcuts import render

def healthcheck(request):
    return HttpResponse("OK")

def home(request):
    return render(request, "home.html", {"title": "Startseite"})

def api_status(request):
    return JsonResponse({"status": "ok"})
```

#### Wichtige Punkte:

- Eine View sollte nicht zur „God Function“ werden.
- Komplexe Business-Logik besser in eine Service-Schicht auslagern.
- Die View sollte schlank bleiben: Orchestrierung, Validierung, Service-Aufrufe,
  Response.

#### Typische Fehler:

- Schwere Domänenlogik direkt in der View über hunderte Zeilen schreiben.
- Viele duplizierte Logik in verschiedenen Views.
- Zugriffs-/Autorisierungsprüfungen auf Endpoint-Ebene ignorieren.

#### Fazit:

Die View ist der Punkt, an dem Web-Protokoll und Business-Logik
aufeinandertreffen. Gut gestaltete Views machen den Code vorhersehbar, testbar
und wartbar.

</details>

<details>
<summary>16. Unterschied zwischen funktionalen (FBV) und klassenbasierten (CBV) Views.</summary>

#### Django

In Django gibt es zwei Hauptstile für Views: **FBV** (function-based views) und
**CBV** (class-based views). Beide Ansätze sind valide; der Unterschied liegt in
Logikorganisation und Skalierung der Codebasis.

#### FBV (Function-Based Views):

- Eine View wird als Funktion definiert.
- Request/Response-Logik ist von oben nach unten lesbar.
- Einfacher und transparenter Ansatz für kleine Endpoints.

Beispiel:

```python
from django.http import JsonResponse

def profile_detail(request, user_id):
    if request.method == "GET":
        return JsonResponse({"user_id": user_id})
    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### CBV (Class-Based Views):

- Eine View wird als Klasse definiert (Methoden wie `get`, `post`, `put`,
  `delete` usw.).
- Logik kann über Vererbung und Mixins wiederverwendet werden.
- Gut geeignet für CRUD, Listen, Formulare und detail/create/update/delete-
  Szenarien.

Beispiel:

```python
from django.http import JsonResponse
from django.views import View

class ProfileDetailView(View):
    def get(self, request, user_id):
        return JsonResponse({"user_id": user_id})
```

#### Zentrale Unterschiede:

1. **Einstiegseinfachheit**

- FBV: einfacher zum Start.
- CBV: erfordert Verständnis von Klassenhierarchie und Dispatch-Mechanik.

2. **Skalierung**

- FBV: gut für kurze, stark individuelle Handler.
- CBV: besser für wiederkehrende Patterns und große Projekte.

3. **Code-Wiederverwendung**

- FBV: über Helper-Funktionen/Dekoratoren.
- CBV: über Vererbung, Mixins, Generic Views.

4. **Lesbarkeit**

- FBV: lokal oft direkter verständlich.
- CBV: kann komplexer wirken durch „verstecktes“ Verhalten von Basisklassen.

5. **Testing**

- Beide Ansätze sind gut testbar, wenn Logik nicht hart in Views eingebettet
  ist.

#### Wann FBV wählen:

- Endpoint ist einfach und stark individuell.
- Maximale Code-Transparenz für schnelles Debugging ist wichtig.
- Kein Mehrwert durch Klassenhierarchie.

#### Wann CBV wählen:

- Viele gleichartige CRUD-Screens/Endpoints.
- Mixins, Permission-Klassen, wiederkehrende Patterns werden benötigt.
- Das Team arbeitet mit Generic CBV und pflegt einen einheitlichen Stil.

#### Fazit:

FBV und CBV sind nicht „richtig/falsch“, sondern kontextabhängig. In Production-
Projekten werden oft beide Ansätze kombiniert: FBV für punktuelle Aufgaben, CBV
für strukturierte, wiederkehrende Szenarien.

</details>

<details>
<summary>17. Wann sollte man CBV und generic class-based views verwenden?</summary>

#### Django

CBV und generic CBV sollte man dann einsetzen, wenn ein Projekt viele
wiederkehrende Web/API-Patterns hat und ein standardisiertes Verhalten über
mehrere Endpoints hinweg benötigt.

#### Wann CBV klar im Vorteil sind:

1. **CRUD-Szenarien**

- Listen, Detailseiten, Erstellen, Aktualisieren, Löschen.
- Typische Klassen: `ListView`, `DetailView`, `CreateView`, `UpdateView`,
  `DeleteView`.

2. **Viele ähnliche Endpoints**

- Wenn sich Endpoints nur in Modell, Formular oder Permission-Regeln
  unterscheiden.

3. **Bedarf an Logik-Wiederverwendung**

- Über Mixins (`LoginRequiredMixin`, `PermissionRequiredMixin`, eigene Mixins).

4. **Einheitlicher Stil im großen Team**

- CBV erleichtern die Vereinheitlichung und reduzieren Copy-Paste.

5. **Erweiterung des Basisverhaltens per Override**

- Zum Beispiel `get_queryset()`, `get_context_data()`, `form_valid()`,
  `get_success_url()`.

#### Wann generic CBV besonders passend sind:

- Admin-ähnliche Oberflächen.
- Backoffice-Seiten.
- Standardformulare und Content-Bereiche.
- Schnelle MVP-Umsetzung ohne Verlust von Code-Struktur.

#### Beispiel für generic CBV:

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

#### Wann man besser KEIN generic CBV nimmt:

1. Die Logik ist stark nicht-standardisiert und passt nicht ins CRUD-Modell.
2. Der Endpoint hat ein komplexes Orchestrierungsszenario (mehrere
   Services/Integrationen).
3. Durch zu viele Overrides wird die generic Klasse unlesbarer als ein einfacher
   FBV.

#### Praktische Tech-Lead-Regel:

- Starte bei Standardfällen mit generic CBV.
- Wenn eine View das generic Verhaltensmodell „sprengt“, wechsle zu normalem CBV
  oder FBV.
- Nutze generic Klassen nicht nur „weil es schöner aussieht“ - Priorität sind
  Wartbarkeit und logische Transparenz.

#### Fazit:

CBV/generic CBV sind Werkzeuge für Beschleunigung und Standardisierung. Sie sind
am besten für wiederkehrende Szenarien geeignet; bei atypischer Business-Logik
ist ein einfacherer und expliziterer Ansatz meist besser.

</details>

<details>
<summary>18. Was sind Mixins in CBV und wie verwendet man sie?</summary>

#### Django

`Mixins` in CBV sind Hilfsklassen mit wiederverwendbarem Verhalten, die über
Mehrfachvererbung in Views eingebunden werden. Sie ermöglichen flexible Views
ohne Code-Duplizierung.

#### Wofür Mixins nötig sind:

1. **Wiederverwendung von Logik**

- Authentifizierung, Permissions, Queryset-Filterung, gemeinsamer Kontext usw.

2. **Komposition von Verhalten**

- Eine View wird aus mehreren kleinen „Bausteinen“ zusammengesetzt statt aus
  einer großen Klasse.

3. **Weniger Copy-Paste**

- Ein Mixin kann in dutzenden Views wiederverwendet werden.

#### Häufige Built-in-Mixins in Django:

- `LoginRequiredMixin` - Zugriff nur für authentifizierte Nutzer.
- `PermissionRequiredMixin` - Prüfung konkreter Berechtigungen.
- `UserPassesTestMixin` - benutzerdefinierte Zugriffsprüfung.
- `ContextMixin` - Hinzufügen von Daten zum Template-Kontext.

#### Beispiel mit Built-in-Mixins:

```python
from django.contrib.auth.mixins import LoginRequiredMixin, PermissionRequiredMixin
from django.views.generic import ListView
from .models import Order

class OrderListView(LoginRequiredMixin, PermissionRequiredMixin, ListView):
    model = Order
    permission_required = "orders.view_order"
    template_name = "orders/list.html"
```

#### Beispiel für ein Custom-Mixin:

```python
class StaffRequiredMixin:
    def dispatch(self, request, *args, **kwargs):
        if not request.user.is_staff:
            from django.http import HttpResponseForbidden
            return HttpResponseForbidden("Zugriff verweigert")
        return super().dispatch(request, *args, **kwargs)
```

```python
class DashboardView(StaffRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Reihenfolge der Mixins ist wichtig:

- Django nutzt MRO (Method Resolution Order).
- „Restriktive“ Mixins (`LoginRequiredMixin`) stehen üblicherweise weiter links.
- `View`/Generic Class steht weiter rechts.

#### Praktische Regeln:

1. Ein Mixin - eine Verantwortung.
2. Mixins nicht mit schwerer Business-Logik überladen.
3. Tiefe Vererbungshierarchien vermeiden, die Debugging erschweren.
4. Für komplexe Domänenlogik Services verwenden, nicht Mixins.

#### Typische Fehler:

- Zu „smarte“ Mixins mit unvorhersehbarem Verhalten.
- Methodenkonflikte durch falsche Vererbungsreihenfolge.
- Doppelte Prüfungen in vielen Views statt gemeinsamer Mixins.

#### Fazit:

Mixins sind in CBV ein starkes Werkzeug für Komposition und Wiederverwendung.
Den größten Nutzen bringen sie, wenn sie klein, klar in ihrer Verantwortung und
konsequent eingesetzt sind.

</details>

<details>
<summary>19. Wie verarbeitet man HTTP-Methoden (GET, POST)?</summary>

#### Django

In Django werden HTTP-Methoden in Views verarbeitet: `GET` liest/zeigt in der
Regel Daten, `POST` erstellt oder verändert den Systemzustand. Die saubere
Methodentrennung ist die Grundlage für sichere und vorhersehbare APIs sowie
Web-Flows.

#### Verarbeitung in FBV:

```python
from django.http import JsonResponse

def contact_view(request):
    if request.method == "GET":
        return JsonResponse({"form": "render contact form"})

    if request.method == "POST":
        # request.POST lesen, validieren, speichern
        return JsonResponse({"status": "created"}, status=201)

    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### Verarbeitung in CBV:

```python
from django.http import JsonResponse
from django.views import View

class ContactView(View):
    def get(self, request):
        return JsonResponse({"form": "render contact form"})

    def post(self, request):
        # validieren und speichern
        return JsonResponse({"status": "created"}, status=201)
```

#### Begrenzung erlaubter Methoden (Dekoratoren):

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

#### Praktische Regeln:

1. **GET**

- Sollte den Systemzustand nicht verändern.
- Ist in vielen Szenarien sicher und cachebar.

2. **POST**

- Für Erstellen/Aktionen mit Datenänderung.
- Für HTML-Formulare ist ein CSRF-Token Pflicht.

3. **Validierung**

- Eingabedaten immer validieren (Forms/Serializer/Service-Schicht).

4. **Response-Codes**

- `200` für erfolgreiches Lesen,
- `201` für Erstellen,
- `400` für Validierungsfehler,
- `405` für nicht erlaubte Methode.

#### Typische Fehler:

- Datenänderungen über GET (Verstoß gegen HTTP-Semantik).
- GET- und POST-Logik in einen „chaotischen“ Block mischen.
- Keine korrekten Status-Codes zurückgeben.

#### Fazit:

GET/POST-Verarbeitung in Django sollte explizit sein: jede Methode eine separate
Verantwortung, klare Validierung und korrekte HTTP-Codes. Das verbessert
Sicherheit, Integrationen und Wartbarkeit.

</details>

<details>
<summary>20. Wie implementiert man Weiterleitungen (redirect)?</summary>

#### Django

Weiterleitungen (`redirect`) in Django werden genutzt, wenn ein Benutzer nach
einer Aktion auf eine andere Seite oder einen anderen Endpoint geführt werden
soll.

#### Der Hauptweg:

```python
from django.shortcuts import redirect
```

`redirect(...)` gibt standardmäßig eine HTTP-Response mit Statuscode 302
(temporäre Weiterleitung) zurück.

#### Verwendungsvarianten:

1. **Auf absolute/relative URL**

```python
return redirect("/dashboard/")
```

2. **Auf benannte Route (empfohlen)**

```python
return redirect("orders:list")
```

3. **Auf Route mit Parametern**

```python
return redirect("orders:detail", order_id=order.id)
```

4. **Auf Model-Instanz (wenn `get_absolute_url` vorhanden ist)**

```python
return redirect(order)
```

#### Beispiel in FBV (Post/Redirect/Get):

```python
from django.shortcuts import redirect, render

def create_order(request):
    if request.method == "POST":
        # Daten speichern
        return redirect("orders:list")
    return render(request, "orders/form.html")
```

#### Beispiel in CBV:

```python
from django.urls import reverse_lazy
from django.views.generic import CreateView

class OrderCreateView(CreateView):
    model = Order
    fields = ["title", "amount"]
    success_url = reverse_lazy("orders:list")
```

#### Temporär vs permanent weiterleiten:

- `302 Found` - temporär (Standard in Django).
- `301 Moved Permanently` - permanent (für SEO/kanonische URLs).

Bei Bedarf einer permanenten Weiterleitung:

```python
from django.http import HttpResponsePermanentRedirect

return HttpResponsePermanentRedirect("/new-url/")
```

#### Praktische Hinweise:

1. Benannte Routen statt hart codierter URL-Strings verwenden.
2. Nach erfolgreichem POST redirecten (PRG-Pattern), um Doppel-Submit bei
   Refresh zu vermeiden.
3. Für Redirect nach Login/Logout `next` und sichere Prüfungen des
   Redirect-Ziels nutzen.

#### Typische Fehler:

- Redirect auf URL, die wieder zurückredirectet (Redirect-Loop).
- URL-Hardcoding statt `name=`-Route.
- Rückgabe von 200 nach POST-Form ohne PRG in Flows, wo das unerwünscht ist.

#### Fazit:

`redirect` in Django ist ein Basiswerkzeug zur Steuerung des User-Flows. Best
Practice: benannte URLs + PRG-Pattern + Sicherheitskontrolle des Zielpfads.

</details>

<details>
<summary>21. Was ist `JsonResponse` und wann verwendet man es?</summary>

#### Django

`JsonResponse` ist eine Django-HTTP-Response für die Rückgabe von Daten im
JSON-Format. Sie wird am häufigsten in API-Endpoints, AJAX-Requests und
Service-Integrationen verwendet.

#### Was `JsonResponse` macht:

1. Serialisiert Python-Daten in JSON.
2. Setzt den korrekten `Content-Type: application/json`.
3. Erlaubt das explizite Setzen von HTTP-Statuscodes.

#### Basisbeispiel:

```python
from django.http import JsonResponse

def health(request):
    return JsonResponse({"status": "ok"})
```

#### Beispiel mit Statuscode:

```python
def create_item(request):
    # ... Erstellungslogik
    return JsonResponse({"id": 123, "message": "created"}, status=201)
```

#### Wichtiger `safe`-Hinweis:

- Standardmäßig erwartet `JsonResponse` ein **dict** (`safe=True`).
- Wenn eine Liste zurückgegeben werden soll, setze `safe=False`.

```python
def tags(request):
    return JsonResponse(["python", "django", "api"], safe=False)
```

#### Wann `JsonResponse` genutzt wird:

1. Einfaches API ohne DRF.
2. Interne Endpoints für Frontend (fetch/AJAX).
3. Webhook-Responses und technische Integrationen.
4. Health-Check-/Diagnose-Endpoints.

#### Wann DRF besser ist als „reines“ `JsonResponse`:

- Es werden Serializer, Schema-Validierung, Pagination, Throttling,
  Auth-Policies benötigt.
- Es gibt viele API-Endpoints und eine einheitliche API-Architektur ist nötig.

#### Praktische Empfehlungen:

1. Immer eine klare JSON-Struktur zurückgeben (z. B. `{"data": ...}`,
   `{"error": ...}`).
2. Korrekte Statuscodes verwenden (`200`, `201`, `400`, `404`, `500`).
3. In Production keine „rohen“ Exception-Traces zurückgeben.
4. Einheitliches Fehlerformat für das gesamte API definieren.

#### Fazit:

`JsonResponse` ist ein leichtes und praktisches Werkzeug für JSON-Responses in
Django. Für einfache APIs reicht es aus; bei großen API-Systemen wechselt man in
der Regel zu DRF.

</details>

<details>
<summary>22. Wie liefert man Dateien (CSV, PDF) aus einer View zurück?</summary>

#### Django

In Django werden Dateien aus Views über `HttpResponse` oder `FileResponse` mit
korrekten HTTP-Headern zurückgegeben (`Content-Type`, `Content-Disposition`).

#### Grundprinzipien:

1. **`Content-Type`** muss dem Dateityp entsprechen.
2. **`Content-Disposition`** steuert das Browser-Verhalten:

- `attachment` -> Datei herunterladen
- `inline` -> im Browser anzeigen (falls unterstützt)

#### Beispiel: CSV zurückgeben

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

#### Beispiel: PDF aus Datei zurückgeben

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

#### Wenn PDF dynamisch erzeugt wird:

- PDF im Speicher (`io.BytesIO`) oder als temporäre Datei erzeugen.
- Danach über `HttpResponse`/`FileResponse` zurückgeben.
- Häufige Bibliotheken: `reportlab`, `weasyprint`, `xhtml2pdf`.

#### Für große Dateien:

1. Über `FileResponse` ausliefern (Streaming, weniger RAM).
2. Datei nicht komplett in den Speicher laden (`read()` großer Dateien
   vermeiden).
3. Bei Bedarf Nginx/X-Accel-Redirect oder CDN/Object Storage nutzen.

#### Praktische Hinweise:

1. Verständliche Dateinamen über `filename=` setzen.
2. Dateizugriff kontrollieren (Owner-/Permission-Prüfung).
3. Für sensible Dokumente Zugriff auditieren.
4. In APIs vorhersehbare Fehler zurückgeben (`404` wenn Datei fehlt, `403` bei
   fehlender Berechtigung).

#### Fazit:

Das Zurückgeben von CSV/PDF in Django hängt primär von korrektem Response-Typ
und Headern ab. Für kleine Dateien reicht `HttpResponse`; für große Dateien und
Production-Last ist `FileResponse` mit Streaming die bessere Wahl.

</details>

<details>
<summary>23. Wie implementiert man Paginierung?</summary>

#### Django

Paginierung in Django wird genutzt, um große Datenlisten in Seiten aufzuteilen
und nicht Hunderte oder Tausende Einträge in einem Request zu rendern/zu senden.

#### Basiswerkzeug:

- `django.core.paginator.Paginator`

#### Beispiel in FBV:

```python
from django.core.paginator import Paginator
from django.shortcuts import render
from .models import Article

def article_list(request):
    queryset = Article.objects.order_by("-created_at")
    paginator = Paginator(queryset, 10)  # 10 Einträge pro Seite
    page_number = request.GET.get("page")
    page_obj = paginator.get_page(page_number)  # sichere Variante

    return render(request, "articles/list.html", {"page_obj": page_obj})
```

#### Paginierung im Template rendern:

```django
{% for article in page_obj %}
  <h3>{{ article.title }}</h3>
{% endfor %}

<div class="pagination">
  {% if page_obj.has_previous %}
    <a href="?page=1">Erste</a>
    <a href="?page={{ page_obj.previous_page_number }}">Zurück</a>
  {% endif %}

  <span>Seite {{ page_obj.number }} von {{ page_obj.paginator.num_pages }}</span>

  {% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">Weiter</a>
    <a href="?page={{ page_obj.paginator.num_pages }}">Letzte</a>
  {% endif %}
</div>
```

#### CBV-Variante (noch einfacher):

```python
from django.views.generic import ListView
from .models import Article

class ArticleListView(ListView):
    model = Article
    paginate_by = 10
    ordering = ["-created_at"]
```

#### Praktische Empfehlungen:

1. Stabile Sortierung (`order_by`) verwenden für vorhersehbare Navigation.
2. Bei großen Listen Queryset optimieren:

- `select_related`, `prefetch_related`, DB-Indizes.

3. Weitere Query-Parameter (Filter, Suche) beim Seitenwechsel erhalten.
4. Ohne Bedarf keine zu große Seitengröße wählen.

#### Typische Fehler:

- Paginierung ohne Sortierung (Daten „springen“ zwischen Seiten).
- Rohes `page()` ohne Behandlung ungültiger Seitennummern.
- Fehlende Indizes auf Spalten, nach denen sortiert/gefiltert wird.

#### Fazit:

In Django lässt sich Paginierung schnell und sauber mit `Paginator` oder
`ListView` umsetzen. Für Performance entscheidend sind ein gutes Queryset,
stabile Sortierung und kontrollierte Seitenparameter.

</details>

<details>
<summary>24. Wie behandelt man Fehler 404 und 500?</summary>

#### Django

Fehler `404` und `500` werden in Django über den Standardmechanismus für
Error-Handling verarbeitet: Fehler-Templates, Handler-Funktionen und globale
Einstellungen.

#### Bedeutung dieser Fehler:

- **404 Not Found** - Route oder Ressource wurde nicht gefunden.
- **500 Internal Server Error** - unbehandelter Fehler auf dem Server.

#### Basisverarbeitung über Templates:

In Production (`DEBUG = False`) sucht Django automatisch nach:

- `templates/404.html`
- `templates/500.html`

Wenn diese Dateien existieren, werden sie dem Benutzer angezeigt.

#### Custom-Handler in `urls.py`:

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

#### Wichtiger Unterschied zwischen Dev und Production:

1. **DEBUG=True (lokal)**

- Django zeigt einen detaillierten Debug-Traceback.

2. **DEBUG=False (production)**

- Benutzer sieht die custom 404/500-Seite.
- Technische Fehlerdetails dürfen nicht nach außen gelangen.

#### Praktische Empfehlungen:

1. Immer benutzerfreundliche 404/500-Seiten bereitstellen.
2. Fehler loggen (Sentry/ELK/OpenTelemetry), statt Stacktraces an Nutzer
   auszugeben.
3. Correlation-/Request-ID in Logs aufnehmen für schnellere Analyse.
4. Korrekte Statuscodes zurückgeben (kein 200 für Fehlerseiten).
5. Für APIs JSON-Fehler in einheitlichem Format liefern.

#### Testing:

- 404 für nicht existierende URLs prüfen.
- 500-Handler auf Staging mit `DEBUG=False` testen.
- Sicherstellen, dass Fehler-Templates in der gebauten Umgebung verfügbar sind.

#### Fazit:

Gutes 404/500-Handling in Django verbindet UX mit operativer Reife: Nutzer
erhalten eine verständliche Seite, das Team vollständige Logs zur Diagnose.

</details>

<details>
<summary>25. Was sind Templates und wie übergibt man Daten aus der View an ein Template?</summary>

#### Django

Templates (`templates`) in Django sind die Darstellungsschicht, die HTML auf
Basis der in der `view` vorbereiteten Daten erzeugt.

#### Was ein Template ist:

- Eine HTML-Datei mit Django-Template-Syntax (`{{ }}` und `{% %}`).
- Ermöglicht Variablenausgabe, Schleifen, Bedingungen und das Einbinden von
  Seitenteilen.
- Trennt UI von der Business-Logik im Python-Code.

#### Wie man Daten aus der View ins Template übergibt:

1. In der `view` einen `context` (Dictionary) aufbauen.
2. `render(request, "template.html", context)` aufrufen.

#### Beispiel:

```python
from django.shortcuts import render
from .models import Article

def article_list(request):
    articles = Article.objects.filter(is_published=True).order_by("-created_at")
    context = {
        "page_title": "Artikel",
        "articles": articles,
        "total": articles.count(),
    }
    return render(request, "articles/list.html", context)
```

#### Datennutzung im Template:

```django
<h1>{{ page_title }}</h1>
<p>Gesamt: {{ total }}</p>

{% if articles %}
  <ul>
    {% for article in articles %}
      <li>{{ article.title }}</li>
    {% endfor %}
  </ul>
{% else %}
  <p>Keine veröffentlichten Artikel.</p>
{% endif %}
```

#### Woher Django Templates lädt:

- Aus Verzeichnissen in `TEMPLATES["DIRS"]`.
- Aus `templates/`-Ordnern innerhalb von Apps (wenn `APP_DIRS=True`).

#### Praktische Empfehlungen:

1. Business-Logik in Python (View/Service) halten, nicht im Template.
2. Nur benötigte Daten in den Kontext geben.
3. Benannte URLs verwenden (`{% url 'app:view' %}`), keine hardcodierten Links.
4. Für wiederkehrende Elemente `include`/Partials nutzen.

#### Sicherheit:

- Django escaped Variablen in Templates standardmäßig automatisch (XSS-Schutz by
  default).
- `|safe` nicht verwenden, wenn die Datenquelle nicht vollständig
  vertrauenswürdig ist.

#### Fazit:

Templates in Django sind ein sauberer, sicherer und kontrollierter Weg, HTML zu
rendern. Die View bereitet Daten vor, das Template zeigt sie an - genau so
entstehen Wartbarkeit und klare Verantwortlichkeit im Projekt.

</details>

<details>
<summary>26. Wie funktioniert Template-Vererbung (`extends`, `block`)?</summary>

#### Django

Template-Vererbung in Django ermöglicht es, ein Basis-Layout zu erstellen und in
untergeordneten Seiten wiederzuverwenden. Das reduziert HTML-Duplizierung und
macht den Frontend-Teil des Projekts besser wartbar.

#### Zentrale Tags:

1. **`{% extends "base.html" %}`**

- Das Child-Template erbt vom Basis-Template.

2. **`{% block ... %}{% endblock %}`**

- Im Basis-Template werden „Slots“ definiert, die Child-Templates füllen können.

#### Basis-Template:

```django
{# templates/base.html #}
<!doctype html>
<html lang="de">
<head>
  <meta charset="utf-8">
  <title>{% block title %}Meine Website{% endblock %}</title>
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

#### Child-Template:

```django
{# templates/articles/list.html #}
{% extends "base.html" %}

{% block title %}Artikelliste{% endblock %}

{% block content %}
  <h1>Artikel</h1>
  <p>Seiteninhalt...</p>
{% endblock %}
```

#### `block.super`:

Wenn ein Block ergänzt statt komplett ersetzt werden soll:

```django
{% block title %}{{ block.super }} | Artikel{% endblock %}
```

#### Praktische Empfehlungen:

1. Ein zentrales `base.html` halten (Layout: head, header, footer, scripts).
2. Separate Blöcke für `title`, `content`, `extra_css`, `extra_js` anlegen.
3. Gleichartige Teile nicht in jedem Template duplizieren - in base/include
   auslagern.
4. Bei Blocknamen projektweit konsistent bleiben.

#### Typische Fehler:

- Keine einheitliche Blockstruktur zwischen Seiten.
- Business-Logik ins Template verlagern statt in View/Service.
- Layout-Code duplizieren statt `extends` zu nutzen.

#### Fazit:

`extends` und `block` sind das Fundament einer skalierbaren Template-Architektur
in Django: ein gemeinsames Site-Layout, minimale Duplizierung und schnelle
UI-Änderungen.

</details>

<details>
<summary>27. Wofür wird `{% include %}` verwendet?</summary>

#### Django

`{% include %}` wird verwendet, um ein Template in ein anderes einzubetten. Das
ist praktisch für wiederkehrende UI-Teile: Header, Footer, Karten, Tabellen,
Paginierung.

#### Warum `include` wichtig ist:

1. **Reduziert HTML-Duplizierung**

- Ein Fragment kann auf vielen Seiten wiederverwendet werden.

2. **Verbessert Wartbarkeit**

- Änderungen in einer Partial-Datei gelten automatisch überall, wo sie
  eingebunden ist.

3. **Vereinfacht die Lesbarkeit von Templates**

- Große Templates werden in kleinere logische Blöcke aufgeteilt.

#### Basisbeispiel:

```django
{# templates/base.html #}
<body>
  {% include "partials/header.html" %}
  <main>{% block content %}{% endblock %}</main>
  {% include "partials/footer.html" %}
</body>
```

#### Kontext an `include` übergeben:

```django
{% include "partials/user_badge.html" with user=request.user %}
```

Der Kontext kann auf übergebene Variablen beschränkt werden:

```django
{% include "partials/user_badge.html" with user=request.user only %}
```

#### Praktische Use Cases:

- Paginierungs-Komponente.
- Tabellenzeile/Produktkarte.
- Alert-/Nachrichtenblock.
- Gemeinsame Layout-Elemente.

#### Unterschied zwischen `extends` und `include`:

- `extends` - Vererbung der Template-Struktur (Layout-Ebene).
- `include` - Einbettung eines lokalen Fragments (Komponenten-Ebene).

#### Typische Fehler:

1. `include` statt `extends` für das Basis-Layout verwenden.
2. Zu „breiten“ impliziten Kontext übergeben.
3. Schwere Logik in Partial-Templates unterbringen.

#### Fazit:

`{% include %}` ist ein Basiswerkzeug für modularen Template-Code in Django.
Nutze es für kleine wiederverwendbare Fragmente, und `extends` für die globale
Seitenstruktur.

</details>

<details>
<summary>28. Was sind Template-Partials und wie funktionieren `{% partial %}` und `{% partialdef %}`?</summary>

#### Django

Template-Partials sind ein Weg, Fragmente direkt innerhalb von Template-Dateien
zu definieren und wiederzuverwenden. Dafür nutzt man die Tags `{% partialdef %}`
(Definition) und `{% partial %}` (Aufruf).

#### So funktioniert es:

1. **`{% partialdef name %}...{% endpartialdef %}`**

- Definiert ein benanntes Partial-Fragment.

2. **`{% partial name %}`**

- Rendert das Partial an der gewünschten Stelle im Template.

#### Basisbeispiel:

```django
{% partialdef product_card %}
  <article class="card">
    <h3>{{ product.title }}</h3>
    <p>{{ product.price }} EUR</p>
  </article>
{% endpartialdef %}

<section class="grid">
  {% for product in products %}
    {% partial product_card %}
  {% endfor %}
</section>
```

#### Unterschied zu `{% include %}`:

- `include` bindet eine separate Datei ein.
- `partial/partialdef` erlaubt Definition und Aufruf eines Fragments im Kontext
  des aktuellen Templates ohne separate Datei.

#### Wann Partials besonders nützlich sind:

1. Wenn ein kleines Fragment schnell innerhalb eines Templates wiederverwendet
   werden soll.
2. Wenn man eine Zersplitterung in dutzende kleine Include-Dateien vermeiden
   will.
3. Für lokale UI-Blöcke, die keine eigene Template-Datei brauchen.

#### Praktische Empfehlungen:

1. Für global wiederverwendbare Komponenten zwischen Seiten weiterhin
   `{% include %}` oder separate Partial-Dateien nutzen.
2. Für lokale, kleine Fragmente `partial/partialdef` nutzen.
3. Keine Business-Logik in Partials legen; nur Präsentationsschicht.

#### Kompatibilität:

- In modernen Django-Versionen sind Partial-Tags als Teil des Template-Systems
  verfügbar.
- In älteren Versionen löst man das meist über `{% include %}` und
  benutzerdefinierte Template-Tags.

#### Fazit:

`{% partialdef %}` und `{% partial %}` sind ein Werkzeug für lokale
Template-Komposition: weniger Duplikate, bessere Lesbarkeit und mehr Kontrolle
über die UI-Struktur.

</details>

<details>
<summary>29. Was sind Template-Tags und Filter?</summary>

#### Django

`Template tags` und `filters` sind Werkzeuge der Django-Template-Engine für
kontrolliertes Rendering von Daten in Templates.

#### Template-Tags:

- Tags führen Logik auf Template-Ebene aus.
- Sie werden in der Form `{% ... %}` verwendet.

Typische eingebaute Tags:

1. `{% if %}` / `{% elif %}` / `{% else %}` - bedingtes Rendering.
2. `{% for %}` - Iteration über Kollektionen.
3. `{% url %}` - Link-Aufbau über Routennamen.
4. `{% include %}` - Einfügen eines Template-Teils.
5. `{% csrf_token %}` - CSRF-Schutz in Formularen.
6. `{% static %}` - Verweise auf Static-Dateien.

Beispiel:

```django
{% if user.is_authenticated %}
  <a href="{% url 'profile' %}">Profil</a>
{% else %}
  <a href="{% url 'login' %}">Anmelden</a>
{% endif %}
```

#### Filter:

- Filter transformieren Variablenwerte.
- Sie werden mit `|` in Ausdrücken `{{ ... }}` genutzt.

Typische eingebaute Filter:

1. `|lower`, `|upper`, `|title`
2. `|length`
3. `|date:"d.m.Y"`
4. `|default:"-"`, `|default_if_none:"-"`
5. `|truncatechars:50`
6. `|safe` (mit Vorsicht!)

Beispiel:

```django
<p>{{ article.title|title }}</p>
<p>{{ article.created_at|date:"d.m.Y H:i" }}</p>
<p>{{ article.description|truncatechars:120 }}</p>
```

#### Eigenen Filter erstellen:

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

#### Eigenen `simple_tag` erstellen:

```python
@register.simple_tag
def app_version():
    return "1.0.0"
```

```django
{% load text_extras %}
<small>v{% app_version %}</small>
```

#### Praktische Regeln:

1. Templates „schlank“ halten: minimale Logik, maximale Lesbarkeit.
2. Wiederkehrende Präsentationslogik in eigene Filter/Tags auslagern.
3. Keine Business-Logik in Template-Tags verlagern.
4. `|safe` nur für verifizierten Content einsetzen.

#### Fazit:

Template-Tags steuern die Rendering-Struktur, Filter das Formatieren von Werten.
Zusammen bieten sie einen flexiblen und sicheren Weg, UI in Django-Templates
aufzubauen.

</details>

<details>
<summary>30. Wie bindet man statische Dateien (`static`) ein und was macht `collectstatic`?</summary>

#### Django

Statische Dateien (`static`) sind CSS, JS, Bilder, Fonts und andere Assets, die
nicht pro Request dynamisch erzeugt werden.

#### Grundeinstellungen in `settings.py`:

```python
STATIC_URL = "/static/"
STATIC_ROOT = BASE_DIR / "staticfiles"   # für Production-Build
```

Bei Bedarf zusätzlicher Verzeichnisse:

```python
STATICFILES_DIRS = [BASE_DIR / "static"]
```

#### Static im Template einbinden:

```django
{% load static %}
<link rel="stylesheet" href="{% static 'css/main.css' %}">
<script src="{% static 'js/app.js' %}"></script>
<img src="{% static 'img/logo.svg' %}" alt="Logo">
```

#### Wo man Static speichert:

1. In jeder App:

- `app_name/static/app_name/...`

2. Oder im gemeinsamen Projektordner:

- `project_root/static/...`

#### Was `collectstatic` macht:

Kommando:

```bash
python manage.py collectstatic
```

Ergebnis:

1. Sammelt alle Static-Dateien aus Apps und `STATICFILES_DIRS`.
2. Kopiert sie in ein zentrales Verzeichnis `STATIC_ROOT`.
3. Bereitet ein Datei-Set vor, das in Production vom Webserver/CDN ausgeliefert
   wird.

#### Dev vs Production:

1. **Lokale Entwicklung (`DEBUG=True`)**

- Django kann Static selbst ausliefern.

2. **Production (`DEBUG=False`)**

- Static wird typischerweise von Nginx, CDN oder Object Storage ausgeliefert.
- Der Django-Prozess sollte Static nicht direkt bedienen.

#### Häufige Production-Praktiken:

- `ManifestStaticFilesStorage` für versionierte/gehashte Dateien (Cache
  Busting).
- WhiteNoise für einfaches Deployment ohne separaten Nginx.
- CDN für schnelle Auslieferung statischer Ressourcen.

#### Typische Fehler:

1. `collectstatic` vor dem Deployment nicht ausführen.
2. Pfade zu `/static/...` hart codieren statt `{% static %}`.
3. `static` (Assets) und `media` (User Uploads) verwechseln.
4. `STATIC_ROOT` für Production nicht konfigurieren.

#### Fazit:

Die Einbindung von Static in Django basiert auf `{% static %}` und korrekten
Settings. `collectstatic` ist ein Pflichtschritt im Production-Build, der alle
statischen Ressourcen für schnelle und stabile Auslieferung vereinheitlicht.

</details>

<details>
<summary>31. Was sind `MEDIA_ROOT` und `MEDIA_URL`?</summary>

#### Django

`MEDIA_ROOT` und `MEDIA_URL` werden für Dateien verwendet, die Benutzer
hochladen (Uploads): Avatare, Dokumente, Fotos, Videos usw.

#### Was ist `MEDIA_ROOT`:

- Absoluter Pfad im Dateisystem des Servers, wo Upload-Dateien physisch
  gespeichert werden.
- Das ist die „Festplatte“, auf die Django Dateien aus `FileField`/`ImageField`
  schreibt.

#### Was ist `MEDIA_URL`:

- URL-Präfix, unter dem diese Dateien im Browser erreichbar sind.
- Das ist der „öffentliche Pfad“ zu Inhalten aus `MEDIA_ROOT`.

#### Grundkonfiguration:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Modellbeispiel:

```python
from django.db import models

class Profile(models.Model):
    avatar = models.ImageField(upload_to="avatars/")
```

Wenn der Benutzer die Datei `photo.jpg` hochgeladen hat, landet sie in:

- Datei auf Datenträger: `MEDIA_ROOT/avatars/photo.jpg`
- URL im Browser: `MEDIA_URL + "avatars/photo.jpg"` ->
  `/media/avatars/photo.jpg`

#### URL-Konfiguration in Development:

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

#### Production-Ansatz:

1. Django speichert die Datei (lokal oder in einem Cloud-Storage-Backend).
2. Die Auslieferung der Dateien übernimmt Nginx/CDN/S3, nicht der
   Django-Prozess.
3. Der Zugriff wird über Permissions oder pre-signed URLs gesteuert (für private
   Dateien).

#### Wichtiger Unterschied zwischen `static` und `media`:

- `static` - Entwicklerdateien (CSS/JS/Logo), werden über `collectstatic`
  gesammelt.
- `media` - Benutzerdateien, laufen nicht durch `collectstatic`.

#### Typische Fehler:

1. `STATIC_ROOT` und `MEDIA_ROOT` vermischen.
2. User-Uploads im Git-Repository speichern.
3. Media-Dateien in Production unnötig über Django ausliefern.
4. Typ/Größe hochgeladener Dateien nicht validieren.

#### Fazit:

`MEDIA_ROOT` - wo die Datei physisch liegt, `MEDIA_URL` - wie der Client darauf
zugreift. Eine klare Trennung von media/static ist ein verpflichtender Standard
in Django-Projekten.

</details>

<details>
<summary>32. Welche Ansätze für Template-Caching gibt es?</summary>

#### Django

Template-Caching in Django reduziert die Last auf CPU/DB und beschleunigt die
Seitenantwort, indem bereits erzeugter Content wiederverwendet wird.

#### Grundlegende Ansätze:

1. **Template-Fragment-Caching (empfohlen für Seitenteile)**

- Cacht nur ein Template-Fragment, nicht die ganze Seite.

```django
{% load cache %}
{% cache 300 sidebar user.id %}
  {# schwerer Block: Menü, Empfehlungen, Widgets #}
  ...
{% endcache %}
```

2. **Per-View-Caching**

- Cacht die vollständige Antwort eines bestimmten Views für eine definierte TTL.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)  # 5 Min
def article_list(request):
    ...
```

3. **Site-weites Caching (über Middleware)**

- Cacht fast die gesamte Website nach globalen Regeln.
- Geeignet für Content-Seiten mit geringer Personalisierung.

4. **Low-Level-Cache-API**

- Caching von Query-/Berechnungsergebnissen im Python-Code.

```python
from django.core.cache import cache

data = cache.get("popular_articles")
if data is None:
    data = expensive_query()
    cache.set("popular_articles", data, 300)
```

#### Cache-Backend konfigurieren:

In Production werden meist Redis oder Memcached verwendet:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Wann man was wählt:

- UI-Fragmente mit teurem Rendering -> Template-Fragment-Cache.
- Stabile öffentliche Seite -> Per-View-Cache.
- Überwiegend statische Website -> site-weites Caching.
- Teure Business-Logik/Queries -> Low-Level-Cache-API.

#### Praktische Regeln:

1. Mit dem am wenigsten aggressiven Cache starten (Fragmente), dann skalieren.
2. TTL nach Business-Anforderungen an die „Datenfrische“ wählen.
3. Für personalisierte Blöcke Schlüssel ergänzen (User-ID, Locale, Permissions).
4. Cache-Invalidierung nach Datenänderungen einplanen.

#### Typische Fehler:

1. Personalisierten Content ohne User-Schlüssel cachen.
2. Cache nach Update/Delete nicht invalidieren.
3. Zu lange TTL für dynamische Daten.
4. Cache als „Heilmittel“ für ineffiziente SQL-Queries betrachten.

#### Fazit:

Der sicherste Start in Django ist Fragment-Caching + Redis. Danach ergänzt man
Per-View- oder site-weites Caching, wenn es durch Lastprofil und
UX-Anforderungen begründet ist.

</details>

<details>
<summary>33. Was sind Django Forms und ModelForm?</summary>

#### Django

`Django Forms` ist ein Mechanismus zur Verarbeitung von HTML-Formularen:
Validierung, Datenbereinigung, Rendering von Feldern und Fehlerbehandlung.  
`ModelForm` ist ein spezieller Formulartyp, der automatisch auf Basis eines
Django-Modells aufgebaut wird.

#### Django Form:

- Wird über `forms.Form` definiert.
- Felder werden manuell beschrieben.
- Geeignet für Formulare, die nicht direkt mit einem Modell verknüpft sind.

Beispiel:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.CharField(widget=forms.Textarea)
```

#### ModelForm:

- Wird über `forms.ModelForm` definiert.
- Felder werden aus dem Modell generiert.
- Speichert Daten einfach in der DB über `form.save()`.

Beispiel:

```python
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ["title", "content", "is_published"]
```

#### Hauptunterschied:

1. **Quelle der Felder**

- Form: Du beschreibst Felder manuell.
- ModelForm: Felder kommen aus dem Modell.

2. **Datenspeicherung**

- Form: manuelle Verarbeitung und Speicherung.
- ModelForm: `form.save()` „out of the box“.

3. **Einsatzszenario**

- Form: Kontaktformular, Suche, Filter, Login/Reset, Integrationsformulare.
- ModelForm: CRUD für Modelle, admin-ähnliche Interfaces.

#### Beispiel der Verarbeitung im View:

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

#### Vorteile von Django Forms allgemein:

- Zentralisierte Server-Validierung.
- Schutz vor Eingabefehlern und falschen Datentypen.
- Bequeme Arbeit mit Fehlermeldungen.
- Einfache Integration in Templates.

#### Fazit:

`Form` nutze für Custom-Szenarien ohne direktes Modell.  
`ModelForm` ist der schnellste und sauberste Weg für CRUD-Operationen mit
Django-Modellen.

</details>

<details>
<summary>34. Was ist der Unterschied zwischen einem HTML-Formular und einem Django-Formular?</summary>

#### Django

Ein HTML-Formular und ein Django-Formular lösen dieselbe Aufgabe (Dateneingabe),
aber auf unterschiedlichen Ebenen. Ein HTML-Formular ist nur Markup im Browser,
ein Django-Formular ist ein serverseitiger Mechanismus zur Validierung und
Verarbeitung dieser Daten.

#### HTML-Formular:

- Beschreibt Felder, Buttons, `method`, `action`.
- Läuft auf der Client-Seite (Browser).
- Garantiert keine Sicherheit und Korrektheit der Daten auf dem Server.

Beispiel:

```html
<form method="post" action="/contact/">
  <input type="text" name="name" />
  <input type="email" name="email" />
  <button type="submit">Senden</button>
</form>
```

#### Django-Formular:

- Wird in Python definiert (`forms.Form` oder `forms.ModelForm`).
- Führt Server-Validierung und Datenbereinigung (`cleaned_data`) aus und erzeugt
  Fehler.
- Lässt sich einfach mit Templates und CSRF-Schutz integrieren.

Beispiel:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
```

#### Zentrale Unterschiede:

1. **Ebene**

- HTML-Formular: Presentation Layer.
- Django-Formular: Backend-Validierungsebene.

2. **Validierung**

- HTML: grundlegende Client-Validierung (leicht zu umgehen).
- Django Form: verpflichtende Server-Validierung, zuverlässig.

3. **Sicherheit**

- HTML allein schützt nicht vor gefälschten Requests.
- Das Django-Formular arbeitet mit `{% csrf_token %}` und integrierter
  Fehlerbehandlung.

4. **Wartbarkeit**

- Ein HTML-only-Ansatz führt oft zu doppelter Validierung.
- Django-Formulare zentralisieren Regeln und vereinfachen die Wartung.

5. **Arbeit mit Modellen**

- HTML: manuelles Speichern.
- ModelForm: `form.save()` „out of the box“.

#### Praktische Regel:

In Production darf man sich nicht nur auf HTML-Validierung verlassen.  
Client-Validierung ist für UX, das Django-Formular für Korrektheit und
Sicherheit.

#### Fazit:

Das HTML-Formular ist für das Interface zuständig, das Django-Formular für
Datenqualität und Server-Zuverlässigkeit. In realen Projekten arbeiten beide
Ansätze zusammen, aber die kritische Prüfung muss immer im Backend stattfinden.

</details>

<details>
<summary>35. Wie rendert man Formulare im Template?</summary>

#### Django

Formulare in Django werden im Template über das `form`-Objekt gerendert, das aus
dem View übergeben wird. Es gibt mehrere Ansätze: schnelles automatisches
Rendering oder kontrolliertes manuelles Rendering.

#### 1. Schnelles automatisches Rendering:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Speichern</button>
</form>
```

Verfügbare Varianten:

- `{{ form.as_p }}` - Felder sind in `<p>` eingebettet
- `{{ form.as_ul }}` - Felder als `<li>`-Liste
- `{{ form.as_table }}` - Felder im Tabellenformat

#### 2. Manuelles Rendering (empfohlen für Production-UI):

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

  <button type="submit">Speichern</button>
</form>
```

#### Was unbedingt ergänzt werden muss:

1. `{% csrf_token %}` für POST-Formulare.
2. Anzeige von Feldfehlern (`field.errors`) und allgemeinen Fehlern
   (`non_field_errors`).
3. `enctype="multipart/form-data"` für Formulare mit Dateien.

#### Beispiel für ein Upload-Formular:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Hochladen</button>
</form>
```

#### Praktische Empfehlungen:

1. Für MVP kann man mit `form.as_p` starten.
2. Für ein echtes Produkt ist manuelles Rendering besser, um UX/UI vollständig
   zu kontrollieren.
3. Validierungsfehler nicht verstecken - sie neben den entsprechenden Feldern
   anzeigen.
4. Benannten Aktionsbuttons und klarem Submit-Flow den Vorzug geben.

#### Fazit:

Form-Rendering in Django kann sehr schnell oder sehr kontrolliert sein. Für
Production-Qualität wählt man in der Regel manuelles Rendering mit expliziter
Fehleranzeige, CSRF-Schutz und kontrolliertem Markup.

</details>

<details>
<summary>36. Wie funktioniert die Formularvalidierung und wie erstellt man eine eigene?</summary>

#### Django

Die Formularvalidierung in Django erfolgt serverseitig beim Aufruf von
`form.is_valid()`. Als Ergebnis liefert Django entweder bereinigte Daten
(`cleaned_data`) oder füllt `form.errors`.

#### So funktioniert die Validierung Schritt für Schritt:

1. Django prüft Typen und grundlegende Feldregeln (`required`, `max_length`,
   `EmailField`, `IntegerField` usw.).
2. Ruft benutzerdefinierte Feldvalidatoren auf (falls hinzugefügt).
3. Ruft `clean_<field>()`-Methoden für konkrete Felder auf.
4. Ruft das allgemeine `clean()` für feldübergreifende Logik auf.
5. Bildet `cleaned_data` oder eine Fehlerliste.

#### Validierung eines Feldes (`clean_<field>()`):

```python
from django import forms
from django.core.exceptions import ValidationError

class RegisterForm(forms.Form):
    username = forms.CharField(max_length=50)

    def clean_username(self):
        value = self.cleaned_data["username"].strip()
        if "admin" in value.lower():
            raise ValidationError("Der Benutzername enthält ein verbotenes Wort.")
        return value
```

#### Feldübergreifende Validierung (`clean()`):

```python
class PasswordForm(forms.Form):
    password = forms.CharField(widget=forms.PasswordInput)
    confirm_password = forms.CharField(widget=forms.PasswordInput)

    def clean(self):
        cleaned_data = super().clean()
        p1 = cleaned_data.get("password")
        p2 = cleaned_data.get("confirm_password")

        if p1 and p2 and p1 != p2:
            raise forms.ValidationError("Die Passwörter stimmen nicht überein.")
        return cleaned_data
```

#### Benutzerdefinierte Validatoren:

```python
from django.core.exceptions import ValidationError

def validate_company_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Nur Unternehmens-E-Mails sind erlaubt.")
```

```python
email = forms.EmailField(validators=[validate_company_email])
```

#### Für `ModelForm`:

- Formularvalidierung + Modellvalidierung greifen zusammen.
- Im Modell können zusätzlich verwendet werden: `clean()`, `unique=True`,
  `UniqueConstraint`, `validators`.

#### Verarbeitung im View:

```python
def submit_form(request):
    form = RegisterForm(request.POST or None)
    if request.method == "POST" and form.is_valid():
        # mit form.cleaned_data arbeiten
        ...
    return render(request, "form.html", {"form": form})
```

#### Praktische Regeln:

1. Validierung muss immer serverseitig erfolgen (Client-Validierung nur für UX).
2. Lokale Feldlogik -> `clean_<field>()`.
3. Logik, die von mehreren Feldern abhängt -> `clean()`.
4. Wiederverwendbare Regeln -> separate Validatoren.
5. Domain-Businessregeln auch auf DB-Ebene absichern (Constraints), nicht nur im
   Formular.

#### Fazit:

Die Stärke von Django Forms ist eine strukturierte Validierung auf mehreren
Ebenen. Das bietet Datenqualitätskontrolle, verständliche Fehler für Benutzer
und einen stabilen Backend-Flow bei der Formularverarbeitung in Production.

</details>

<details>
<summary>37. Was sind benutzerdefinierte Validatoren in Django und wie verwendet man sie wieder?</summary>

#### Django

Benutzerdefinierte Validatoren in Django sind Funktionen oder Klassen, die den
Wert eines Feldes nach eigenen Regeln prüfen und `ValidationError` werfen, wenn
die Daten die Prüfung nicht bestehen.

#### Warum man sie braucht:

1. **Wiederverwendung von Regeln**

- Eine Prüfung wird in vielen Formularen/Modellen genutzt.

2. **Single Source of Truth**

- Eine Business-Regel wird nicht im ganzen Code dupliziert.

3. **Sauberere Architektur**

- Die Validierungslogik wird aus Views/Forms in eine eigene Schicht ausgelagert.

#### Beispiel eines funktionalen Validators:

```python
from django.core.exceptions import ValidationError

def validate_corporate_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Nur Unternehmens-E-Mails sind erlaubt.")
```

Verwendung im Modell:

```python
from django.db import models
from .validators import validate_corporate_email

class Employee(models.Model):
    email = models.EmailField(validators=[validate_corporate_email])
```

Verwendung im Formular:

```python
from django import forms
from .validators import validate_corporate_email

class InviteForm(forms.Form):
    email = forms.EmailField(validators=[validate_corporate_email])
```

#### Beispiel eines class-based Validators:

```python
from django.core.exceptions import ValidationError

class MinWordsValidator:
    def __init__(self, min_words=3):
        self.min_words = min_words

    def __call__(self, value):
        if len(value.split()) < self.min_words:
            raise ValidationError(f"Mindestens {self.min_words} Wort/Wörter.")
```

```python
description = models.TextField(validators=[MinWordsValidator(5)])
```

#### Wo man sie am besten platziert:

- `app/validators.py` oder `app/domain/validators.py`
- Für große Projekte: separate Module nach Domänen.

#### Praktische Regeln:

1. Ein Validator sollte genau eine konkrete Prüfung machen.
2. Fehlermeldungen sollten für Benutzer verständlich sein.
3. Für kritische Regeln die Kontrolle auf DB-Ebene absichern
   (`UniqueConstraint`, Check-Constraints).
4. Tests für Validatoren getrennt von Views schreiben.

#### Fazit:

Benutzerdefinierte Validatoren sind der richtige Weg,
Business-Validierungsregeln in Django zu zentralisieren. Sie machen den Code
sauberer, besser wiederverwendbar und reduzieren das Risiko eines Regel-Drifts
in verschiedenen Systemteilen.

</details>

<details>
<summary>38. Wie verarbeitet man Datei-Uploads?</summary>

#### Django

Datei-Uploads in Django werden über `request.FILES`, die Felder
`FileField`/`ImageField` und korrekt konfigurierte `MEDIA_ROOT`/`MEDIA_URL`
verarbeitet.

#### Was man für Uploads braucht:

1. Ein Dateifeld im Formular oder Modell.
2. `enctype="multipart/form-data"` im HTML-Formular.
3. Übergabe von `request.FILES` an das Formular.
4. Konfigurierte Media-Parameter in `settings.py`.

#### Modellbeispiel:

```python
from django.db import models

class Document(models.Model):
    title = models.CharField(max_length=200)
    file = models.FileField(upload_to="documents/%Y/%m/")
```

#### ModelForm-Beispiel:

```python
from django import forms
from .models import Document

class DocumentForm(forms.ModelForm):
    class Meta:
        model = Document
        fields = ["title", "file"]
```

#### View-Beispiel:

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

#### Template:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Hochladen</button>
</form>
```

#### Media-Konfiguration:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Sicherheit und Production-Praxis:

1. Dateityp, Größe und Erweiterung validieren.
2. Dem ursprünglichen Dateinamen vom Client nicht vertrauen.
3. Zugriff auf private Dateien über Permissions begrenzen.
4. Für Production externen Storage (S3-kompatibel) oder einen separaten
   Dateiserver verwenden.
5. Potenziell gefährliche Dateien scannen (wenn der Business-Case risikobehaftet
   ist).

#### Typische Fehler:

1. `enctype="multipart/form-data"` vergessen -> `request.FILES` ist leer.
2. Nur `request.POST` ohne `request.FILES` übergeben.
3. Static und Media vermischen.
4. Größe/Typ nicht prüfen und Sicherheits- oder Überlastungsrisiken erhalten.

#### Fazit:

In Django funktionieren Uploads zuverlässig, wenn die Grundregeln eingehalten
werden: korrektes Formular, `request.FILES`, Validatoren und Zugriffskontrolle
für Dateien in Production.

</details>

<details>
<summary>39. Was ist Django ORM?</summary>

#### Django

Django ORM (Object-Relational Mapping) ist die Datenzugriffsschicht, die es
ermöglicht, mit der Datenbank über Python-Objekte zu arbeiten, statt in den
meisten typischen Szenarien SQL manuell zu schreiben.

#### Grundidee des ORM:

1. **Python-Modell = DB-Tabelle**
2. **Modellinstanz = Tabellenzeile**
3. **Modellfeld = Tabellenspalte**
4. **QuerySet = vom ORM erzeugte SQL-Abfrage(n)**

#### Beispiel:

```python
# models.py
class Article(models.Model):
    title = models.CharField(max_length=200)
    is_published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

```python
# erstellen
Article.objects.create(title="Django ORM", is_published=True)

# lesen
articles = Article.objects.filter(is_published=True).order_by("-created_at")

# aktualisieren
article = Article.objects.get(pk=1)
article.title = "Updated title"
article.save()

# löschen
article.delete()
```

#### Vorteile von Django ORM:

1. **Schnelle Entwicklung** - weniger Boilerplate-SQL.
2. **Lesbarer Code** - Abfragen werden deklarativ beschrieben.
3. **Sicherheit** - Parametrisierung von Abfragen reduziert
   SQL-Injection-Risiken.
4. **Portabilität** - derselbe Code funktioniert (überwiegend) mit verschiedenen
   DBMS.
5. **Integration in Django** - forms, admin, migrations, validators.

#### Wichtige Konzepte:

- `QuerySet` ist lazy: Die Abfrage wird erst ausgeführt, wenn Daten benötigt
  werden.
- `select_related` und `prefetch_related` helfen, N+1-Probleme zu vermeiden.
- `annotate`, `aggregate`, `F`, `Q`, `Subquery` - für komplexere Abfragen.

#### Einschränkungen des ORM:

1. Sehr komplexe SQL-Konstruktionen sind manchmal als Raw SQL einfacher.
2. Ohne Profiling entstehen leicht ineffiziente Abfragen.
3. Falsche Nutzung von Beziehungen kann die Performance stark beeinträchtigen.

#### Wann Raw SQL verwenden:

- Spezifische Optimierungen für ein konkretes DBMS.
- Komplexe Analytics/CTE/Window-Funktionen, bei denen ORM-Code unlesbar wird.
- Migrations-/Betriebsaufgaben, bei denen präzise SQL-Kontrolle nötig ist.

#### Fazit:

Django ORM ist einer der zentralen Vorteile des Frameworks: schnell, sicher und
bequem für die meisten Business-Cases. Für Production-Ergebnisse ist es jedoch
wichtig zu verstehen, was das ORM tatsächlich erzeugt, und Abfragen rechtzeitig
zu optimieren.

</details>

<details>
<summary>40. Was ist ein Modell und wie erstellt man es?</summary>

#### Django

Ein Modell (`Model`) in Django ist eine Python-Klasse, die die Datenstruktur
beschreibt und einer Tabelle in der Datenbank entspricht. Über das Modell
definierst du Felder, Beziehungen und Regeln auf Datenebene.

#### Was ein Modell ist:

1. **Beschreibung des DB-Schemas in Python**

- Modellfelder (`CharField`, `IntegerField`, `DateTimeField`...) entsprechen
  Tabellenspalten.

2. **Schicht der Domänenentitäten**

- Ein Modell repräsentiert ein Business-Objekt: `User`, `Order`, `Invoice`,
  `Product`.

3. **Integration mit ORM**

- Erstellen, Lesen, Aktualisieren und Löschen von Datensätzen über
  `Model.objects`.

#### Modellbeispiel:

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

#### Wie man ein Modell Schritt für Schritt erstellt:

1. Klasse in `app/models.py` hinzufügen.
2. Sicherstellen, dass die App in `INSTALLED_APPS` eingebunden ist.
3. Migration erstellen:

```bash
python manage.py makemigrations
```

4. Migration auf die DB anwenden:

```bash
python manage.py migrate
```

#### Grundlegende Praktiken:

1. Verständliche Feldnamen und Constraints verwenden (`unique`, `db_index`).
2. Technische Felder `created_at`, `updated_at` hinzufügen.
3. `__str__` für Lesbarkeit in Admin und Shell definieren.
4. Domänenkritische Invarianten in der DB absichern (Constraints), nicht nur in
   View/Forms.

#### Typische Fehler:

1. Alles als Text speichern und Datentypen ignorieren.
2. Keine Indizes für Filter-/Suchfelder.
3. Hochlevel-Businesslogik ohne Struktur direkt im Modell mischen.
4. Verspätete Migrationen, die zwischen Umgebungen auseinanderlaufen.

#### Fazit:

Das Modell in Django ist das Fundament für die Arbeit mit Daten. Qualitativ gut
entworfene Modelle bestimmen Performance, Zuverlässigkeit und Skalierbarkeit des
gesamten Projekts.

</details>

<details>
<summary>41. Was sind ForeignKey, OneToOneField, ManyToManyField?</summary>

#### Django

`ForeignKey`, `OneToOneField` und `ManyToManyField` sind Beziehungstypen
zwischen Modellen im Django ORM. Sie bestimmen, wie Entitäten in der DB
miteinander verknüpft sind.

#### 1. ForeignKey (eins-zu-viele, 1:N)

- Ein „Parent“-Objekt kann viele „Child“-Objekte haben.
- Jeder Child-Datensatz verweist nur auf einen Parent.

Beispiel:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Use Case: ein Autor -> viele Bücher.

#### 2. OneToOneField (eins-zu-eins, 1:1)

- Jedem Datensatz von Modell A entspricht maximal ein Datensatz von Modell B.
- Im Kern ist es `ForeignKey(unique=True)` mit klarerer Semantik.

Beispiel:

```python
from django.conf import settings

class Profile(models.Model):
    user = models.OneToOneField(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    bio = models.TextField(blank=True)
```

Use Case: ein Benutzer -> ein Profil.

#### 3. ManyToManyField (viele-zu-viele, M:N)

- Datensätze beider Tabellen können viele Verknüpfungen zueinander haben.
- Django erstellt eine Zwischentabelle automatisch (oder über `through=`).

Beispiel:

```python
class Tag(models.Model):
    name = models.CharField(max_length=50, unique=True)

class Article(models.Model):
    title = models.CharField(max_length=200)
    tags = models.ManyToManyField(Tag, related_name="articles")
```

Use Case: Ein Artikel hat viele Tags, ein Tag gehört zu vielen Artikeln.

#### Wie man den Beziehungstyp wählt:

1. `ForeignKey` - wenn es einen klaren „Owner“ und mehrere Child-Datensätze
   gibt.
2. `OneToOneField` - wenn die Erweiterungsentität nur einmal existieren soll.
3. `ManyToManyField` - wenn beide Seiten viele Gegenstücke haben können.

#### Nuance von `on_delete` bei ForeignKey/OneToOne:

- `CASCADE` - Child-Datensätze zusammen mit dem Parent löschen.
- `PROTECT` - Löschen verbieten, wenn Abhängigkeiten bestehen.
- `SET_NULL` - Referenz auf `NULL` setzen (Feld muss `null=True` haben).

#### Fazit:

Diese drei Felder sind die Basis für die Modellierung relationaler Daten in
Django. Ein korrekt gewählter Beziehungstyp vereinfacht Queries, Migrationen und
die langfristige Wartung des Domänenmodells.

</details>

<details>
<summary>42. Welche Arten der Modellvererbung gibt es?</summary>

#### Django

In Django gibt es drei Hauptarten der Modellvererbung: **Abstract Base
Classes**, **Multi-table Inheritance** und **Proxy Models**. Sie lösen
unterschiedliche Aufgaben und haben unterschiedliche Auswirkungen auf das
DB-Schema.

#### 1. Abstract Base Class (abstrakte Vererbung)

- Das Elternmodell erzeugt keine eigene Tabelle in der DB.
- Seine Felder werden in die Kindmodelle kopiert.

Beispiel:

```python
class TimeStampedModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True

class Article(TimeStampedModel):
    title = models.CharField(max_length=200)
```

Wann verwenden:

- Für gemeinsame Felder/Methoden in vielen Modellen.
- Die häufigste und praktischste Option in Production.

#### 2. Multi-table Inheritance (Vererbung mit separaten Tabellen)

- Jedes Modell in der Vererbungskette hat eine eigene Tabelle.
- Django erstellt eine `OneToOne`-Beziehung zwischen Parent und Child.

Beispiel:

```python
class Person(models.Model):
    name = models.CharField(max_length=120)

class Employee(Person):
    salary = models.DecimalField(max_digits=10, decimal_places=2)
```

Wann verwenden:

- Wenn eine echte Entitätshierarchie in der DB benötigt wird.
- Wenn separate Tabellen für Basis- und Spezialmodell wichtig sind.

Nachteil:

- Zusätzliche JOINs und komplexere Abfragen.

#### 3. Proxy Model (Proxy-Modell)

- Es wird keine neue Tabelle erstellt.
- Arbeitet mit derselben Tabelle wie das Basismodell.
- Ermöglicht, das Python-Verhalten (Methoden, Manager, Ordering) zu ändern, ohne
  das DB-Schema zu ändern.

Beispiel:

```python
class Order(models.Model):
    status = models.CharField(max_length=20)

class OpenOrder(Order):
    class Meta:
        proxy = True
        ordering = ["id"]
```

Wann verwenden:

- Wenn ein anderer Manager/ein anderes Verhalten für dasselbe Modell benötigt
  wird.
- Wenn eine andere Darstellung im Django Admin nötig ist, ohne Tabellenstruktur
  zu ändern.

#### Schnelle Auswahl:

1. Gemeinsame Felder ohne separate Tabelle -> **abstract**.
2. Echte Datenhierarchie mit separaten Tabellen -> **multi-table**.
3. Anderes Python-Verhalten ohne DB-Änderung -> **proxy**.

#### Praktischer Tipp:

Standardmäßig **abstract base class** wählen.  
`multi-table` vorsichtig einsetzen, nur wenn es vom Domänenmodell gefordert ist
und nicht „der Hierarchie wegen“.

#### Fazit:

Den Vererbungstyp in Django wählt man nach Ziel: Wiederverwendung von Feldern,
physische Tabellenhierarchie oder nur Verhaltensänderung des Modells. Die
richtige Wahl vereinfacht DB-Schema und zukünftige Projektwartung.

</details>

<details>
<summary>43. Wofür wird die Klasse Meta verwendet?</summary>

#### Django

Die innere Klasse `Meta` in einem Django-Modell wird verwendet, um das
Modellverhalten auf ORM- und DB-Ebene zu konfigurieren, ohne die Business-Logik
des Modells selbst zu ändern.

#### Was man typischerweise in `Meta` definiert:

1. **`ordering`** - Standard-Sortierung.
2. **`db_table`** - benutzerdefinierter Tabellenname in der DB.
3. **`verbose_name`, `verbose_name_plural`** - lesbare Namen im Admin.
4. **`indexes`** - Indizes für Performance.
5. **`constraints`** - Business-Constraints auf DB-Ebene.
6. **`unique_together` / `UniqueConstraint`** - Eindeutigkeit von
   Feldkombinationen.
7. **`abstract` / `proxy`** - Typ der Modellvererbung.

#### Beispiel:

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
        verbose_name_plural = "Produkte"
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

#### Warum `Meta` wichtig ist:

1. **Performance**

- Indizes und korrekte Constraints reduzieren die Kosten von Abfragen.

2. **Datenintegrität**

- Constraints schützen vor fehlerhaften Datensätzen, auch wenn irgendwo
  Validierung in View/Form fehlt.

3. **Schema-Steuerbarkeit**

- Explizite Kontrolle über Tabellen und Regeln in Migrationen.

4. **Admin-Komfort**

- Menschlich lesbare Modellnamen im Back-Office.

#### Praktische Empfehlungen:

1. `UniqueConstraint` statt des veralteten `unique_together` verwenden.
2. Indizes nur für wirklich „heiße“ Filter-/Sortierfelder hinzufügen.
3. Business-kritische Regeln auf DB-Ebene über `constraints` halten.
4. `db_table` nicht übermäßig nutzen, wenn kein explizites Naming nötig ist.

#### Fazit:

`Meta` ist das Konfigurationszentrum für das ORM-Verhalten eines Modells.
Darüber steuerst du Reihenfolge, Indizes, Constraints und die Qualität des
DB-Schemas, was die Zuverlässigkeit und Performance eines Django-Projekts direkt
beeinflusst.

</details>

<details>
<summary>44. Was ist der Unterschied zwischen `null=True` und `blank=True`?</summary>

#### Django

`null=True` und `blank=True` lösen unterschiedliche Aufgaben und arbeiten auf
verschiedenen Ebenen:

- `null=True` - Ebene der **Datenbank** (ob `NULL` gespeichert werden darf).
- `blank=True` - Ebene der **Form-/Admin-Validierung** (ob ein Feld leer sein
  darf).

#### `null=True`:

1. Erlaubt, `NULL` in die DB-Spalte zu schreiben.
2. Beeinflusst Tabellenschema und Migrationen.
3. Ist kritisch für Felder, bei denen „kein Wert“ als SQL-`NULL` gespeichert
   werden soll.

#### `blank=True`:

1. Erlaubt, das Feld in Formularen, ModelForm und Django Admin leer zu lassen.
2. Ändert den Spaltentyp in der DB nicht direkt.
3. Beeinflusst `form.is_valid()`, nicht die SQL-Ebene.

#### Beispiele:

```python
class Profile(models.Model):
    bio = models.TextField(blank=True)  # im Formular optional
    birth_date = models.DateField(null=True, blank=True)  # NULL in DB und leer im Formular möglich
```

#### Wichtige Nuance für Strings (`CharField`, `TextField`):

- In Django setzt man für String-Felder normalerweise **kein `null=True`**.
- Empfohlene Praxis: leeren String `""` statt `NULL` verwenden.
- Das heißt typischerweise: `CharField(..., blank=True)` ohne `null=True`.

#### Schnelle Matrix:

1. `null=False, blank=False` -> Feld ist in DB und Formular verpflichtend.
2. `null=True, blank=False` -> in DB kann `NULL` stehen, Formular verlangt aber
   einen Wert.
3. `null=False, blank=True` -> Formular erlaubt leer, in DB wird nicht `NULL`
   gespeichert (oft `""`).
4. `null=True, blank=True` -> maximal „optional“ (Formular und DB).

#### Praktische Empfehlungen:

1. Für `DateField`, `DateTimeField`, `ForeignKey` und numerische Felder braucht
   man oft beides: `null=True, blank=True`.
2. Für `CharField/TextField` reicht meist `blank=True`.
3. Eine konsistente Projektpolitik beibehalten, um Chaos zwischen `NULL` und
   `""` zu vermeiden.
4. Beachten: falsche Wahl erschwert Filterung und Analytics.

#### Fazit:

`null` steuert die Speicherung in der DB, `blank` die Validierung auf
Django-Form-Ebene. Das sind zwei verschiedene Verhaltensachsen und sollten
bewusst nach dem Domänenmodell gewählt werden.

</details>

<details>
<summary>45. Was ist der Unterschied zwischen CharField und TextField?</summary>

#### Django

`CharField` und `TextField` speichern beide Text, haben aber unterschiedliche
Einsatzszenarien und Constraints auf Modell-/DB-Ebene.

#### `CharField`:

1. Für kurzen/mittellangen Text gedacht.
2. **Erfordert zwingend** `max_length`.
3. Gut geeignet für Felder mit kontrollierter Länge: Name, Slug, Title, Code,
   E-Mail, Phone.

Beispiel:

```python
title = models.CharField(max_length=200)
sku = models.CharField(max_length=64, unique=True)
```

#### `TextField`:

1. Für langen freien Text gedacht.
2. Erfordert kein `max_length` auf Modellebene (kann per Validierung ergänzt
   werden).
3. Geeignet für Beschreibungen, Artikelinhalte, Notizen, Kommentare.

Beispiel:

```python
description = models.TextField(blank=True)
content = models.TextField()
```

#### Zentrale Unterschiede:

1. **Längenbegrenzung**

- `CharField`: immer `max_length`.
- `TextField`: standardmäßig ohne harte Grenze.

2. **Datensemantik**

- `CharField`: strukturierter kurzer Text.
- `TextField`: großer unstrukturierter Text.

3. **Forms/Admin**

- `CharField` wird meist als `input` gerendert.
- `TextField` meist als `textarea`.

4. **Indizierung und Performance**

- Kurze indexierte Felder liegen meist sinnvoller in `CharField`.
- Für große Texte hängt die Indizierung von der DB ab und braucht oft separate
  Ansätze (Full-Text-Search).

#### Praktische Tech-Lead-Regeln:

1. Wenn der Wert eine natürliche Längenbegrenzung hat -> `CharField`.
2. Wenn der Text potenziell groß/frei ist -> `TextField`.
3. `TextField` nicht „vorsichtshalber“ nutzen, wenn `CharField` ausreicht.
4. Für Suche in großen Texten eine separate Search-Strategie planen (PostgreSQL
   FTS, Elasticsearch/OpenSearch usw.).

#### Fazit:

`CharField` steht für kontrollierten kurzen Text, `TextField` für großen
Content. Die richtige Feldwahl beeinflusst Validierung, Formular-UX, Indizierung
und Abfrage-Performance.

</details>

<details>
<summary>46. Was sind Model Manager und wie erstellt man einen eigenen?</summary>

#### Django

Ein `Model Manager` in Django ist der „Einstiegspunkt“ für Modellabfragen über
ORM. Standardmäßig hat jedes Modell den Manager `objects`, aber man kann eigene
Manager mit domänenspezifischen Methoden erstellen.

#### Warum eigene Manager sinnvoll sind:

1. **Zentralisierung der Query-Logik**

- Damit dieselben `filter(...)` nicht in verschiedenen Views/Services dupliziert
  werden.

2. **Lesbares API für das Modell**

- Zum Beispiel: `Article.objects.published().recent()`.

3. **Kontrolle über den „Default“-Datensatzbereich**

- Zum Beispiel Soft-Deleted-Datensätze ausblenden.

#### Einfaches Manager-Beispiel:

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

Verwendung:

```python
Article.objects.published()
Article.objects.recent()
```

#### Kombination Manager + QuerySet (bessere Skalierbarkeit):

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

#### Praktische Empfehlungen:

1. In Manager/QuerySet nur Datenauswahllogik halten.
2. Business-Orchestrierung in der Service-Schicht lassen.
3. Methoden fachlich benennen (`active`, `paid`, `for_user`).
4. Manager nicht „magisch“ machen - Verhalten muss offensichtlich sein.

#### Typische Fehler:

1. Dieselben Filter im gesamten Code duplizieren.
2. Schwere Business-Logik in den Manager mischen.
3. Default-Manager so überschreiben, dass Admin/Migrationen unerwartet
   reagieren.

#### Fazit:

Model Manager sind der richtige Ort für wiederverwendbare ORM-Abfragen. Ein
Eigener Manager macht den Code sauberer und Abfragen im ganzen Projekt
konsistenter.

</details>

<details>
<summary>47. Was sind Migrationen und wofür braucht man sie?</summary>

#### Django

Migrationen in Django sind eine kontrollierte Historie von Änderungen am
Datenbankschema, die im Projektcode gespeichert und mit den Kommandos
`makemigrations` und `migrate` angewendet wird.

#### Was Migrationen bringen:

1. **DB-Versionierung**

- Änderungen an Tabellen, Feldern, Indizes und Constraints werden als
  Instruktionsdateien festgehalten.

2. **Reproduzierbare Umgebungen**

- Dev, Staging und Production erhalten dasselbe DB-Schema.

3. **Sichere Schema-Evolution**

- Statt manuellem SQL in „Notizen“ hat das Team einen formalisierten
  Änderungsprozess.

4. **Team-Zusammenarbeit**

- Migrationen werden in Git committed und zusammen mit dem Code reviewed.

#### So funktioniert es:

1. Du änderst das Modell in `models.py`.
2. `python manage.py makemigrations` generiert die Migration-Datei.
3. `python manage.py migrate` wendet die Änderungen auf die DB an.
4. Django speichert den Zustand in der Systemtabelle `django_migrations`.

#### Beispiele typischer Änderungen per Migration:

- Feld hinzufügen/entfernen.
- Feldtyp ändern.
- Index erstellen.
- `UniqueConstraint` oder `CheckConstraint` hinzufügen.
- Modell/Feld umbenennen.

#### Data Migrations:

Neben Struktur kann man auch Datenmigrationen (`RunPython`) durchführen, z. B.:

- ein neues Feld mit Werten befüllen,
- Daten zwischen Spalten verschieben,
- bestehende Datensätze normalisieren.

#### Praktische Regeln:

1. Migrationen zusammen mit Modelländerungen committen.
2. Alte Migrationen nicht editieren, wenn sie bereits in gemeinsamen Umgebungen
   angewendet sind.
3. Migrationen vor Production auf Staging testen.
4. Für große Tabellen ein backward-kompatibles Rollout planen (expand/contract).

#### Typische Fehler:

1. Code ohne aktuelle Migrationen starten.
2. Migration-Dateien nicht committen.
3. Gefährliche blockierende Operationen auf großen Tabellen ohne Plan ausführen.
4. Bereits angewendete Migrationen editieren und die Schema-Historie brechen.

#### Fazit:

Migrationen sind das „Versionskontrollsystem“ für die DB in Django. Sie sind
kritisch für zuverlässige Deployments, Teamarbeit und eine vorhersehbare
Datenentwicklung.

</details>

<details>
<summary>48. Was ist der Unterschied zwischen `makemigrations` und `migrate`?</summary>

#### Django

`makemigrations` und `migrate` sind zwei unterschiedliche Phasen bei der Arbeit
mit Migrationen:

- `makemigrations` **erstellt** Migration-Dateien (Änderungsplan).
- `migrate` **wendet** diese Änderungen auf die Datenbank an.

#### `makemigrations`:

1. Analysiert Änderungen in `models.py`.
2. Generiert Python-Migrationen in `app/migrations/`.
3. Ändert die DB nicht direkt.

Kommando:

```bash
python manage.py makemigrations
```

#### `migrate`:

1. Liest Migration-Dateien.
2. Führt SQL-Operationen in der DB aus (CREATE/ALTER/DROP usw.).
3. Markiert angewendete Migrationen in der Tabelle `django_migrations`.

Kommando:

```bash
python manage.py migrate
```

#### Einfacher Workflow:

1. Modelle geändert.
2. `makemigrations` ausgeführt.
3. Generierte Migration geprüft.
4. `migrate` ausgeführt.
5. Code + Migration-Dateien committed.

#### Analogie:

- `makemigrations` = „Anweisung aufschreiben“.
- `migrate` = „Anweisung ausführen“.

#### Nützliche Kommandos:

```bash
python manage.py showmigrations
python manage.py sqlmigrate app_name 0001
```

- `showmigrations` zeigt, welche Migrationen angewendet sind.
- `sqlmigrate` zeigt das SQL, das ausgeführt wird.

#### Typische Fehler:

1. `migrate` ausführen, ohne nach Modelländerungen Migrationen zu erstellen.
2. `makemigrations` ausführen, aber Dateien nicht committen.
3. Lokalen DB-Status mit Staging/Production verwechseln.
4. Migrationskonflikte in Team-Entwicklung ignorieren.

#### Fazit:

`makemigrations` bereitet Änderungen vor, `migrate` wendet sie an. Für einen
stabilen Deployment-Prozess braucht man beide Schritte in der richtigen
Reihenfolge und kontrolliert ausgeführt.

</details>

<details>
<summary>49. Wie verbindet man PostgreSQL oder eine andere DB?</summary>

#### Django

Die DB-Anbindung in Django erfolgt über die Einstellung `DATABASES` in
`settings.py`. Für Production wird am häufigsten PostgreSQL verwendet, seltener
MySQL/MariaDB.

#### 1. DB-Treiber installieren

Für PostgreSQL (empfohlene moderne Variante):

```bash
pip install psycopg[binary]
```

Alternative: `psycopg2-binary`.

#### 2. `DATABASES` in `settings.py` konfigurieren

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

#### 3. Migrationen ausführen

```bash
python manage.py migrate
```

#### Verbindung über Env-Variablen (empfohlen):

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

#### Andere unterstützte Engines:

1. SQLite (Standard für lokal/Prototypen)
2. PostgreSQL (Hauptwahl für Production)
3. MySQL / MariaDB
4. Oracle

#### Production-Empfehlungen:

1. DB-Passwörter nicht im Repository speichern.
2. SSL zur DB aktivieren (wo relevant).
3. Connection-Pooling konfigurieren (PgBouncer oder DB-seitige Parameter).
4. Health-Checks und Monitoring für Latenz/Locks/Slow Queries hinzufügen.
5. Separate Zugriffsrollen verwenden (Least Privilege).

#### Typische Fehler:

1. Falscher `ENGINE` oder fehlender Treiber.
2. Lokal funktioniert es, in CI/Prod nicht wegen Env-Variablen.
3. SQLite in Production unter konkurrierender Last verwenden.
4. Fehlende Timeouts/Pooling unter Last.

#### Fazit:

Um PostgreSQL in Django zu verbinden, braucht man drei Schritte: Treiber,
`DATABASES`, Migrationen. Für Production sind env-basierte Konfiguration,
sichere Credentials, SSL und Kontrolle der Verbindungs-Performance kritisch.

</details>

<details>
<summary>50. Was ist ein QuerySet? Lazy Evaluation?</summary>

#### Django

Ein `QuerySet` im Django ORM ist ein Objekt, das eine Menge von DB-Datensätzen
und eine Kette von Operationen darauf repräsentiert (`filter`, `exclude`,
`order_by`, `annotate` usw.).

#### Was man über QuerySet verstehen muss:

1. Es ist standardmäßig **lazy**.
2. Das Erstellen eines QuerySets führt SQL nicht sofort aus.
3. SQL wird erst ausgeführt, wenn die Daten tatsächlich benötigt werden.

#### Beispiel für Lazy-Verhalten:

```python
qs = Article.objects.filter(is_published=True).order_by("-created_at")
# In diesem Schritt wurde die DB-Abfrage noch NICHT ausgeführt
```

#### Wann ein QuerySet materialisiert wird (SQL-Ausführung):

1. Iteration:

```python
for article in qs:
    ...
```

2. Umwandlung in eine Liste:

```python
items = list(qs)
```

3. Länge/Boolscher Wert abfragen:

```python
len(qs)
bool(qs)
```

4. Aufrufe wie:

- `first()`, `last()`, `exists()`, `count()`, `get()`
- Slicing (oft mit `LIMIT/OFFSET`), z. B. `qs[:10]`

#### Vorteile von Lazy Evaluation:

1. **Query-Optimierung**

- Man kann ein komplexes QuerySet schrittweise vor der Ausführung aufbauen.

2. **Flexibilität**

- Ein Basis-QuerySet kann mit unterschiedlichen Bedingungen wiederverwendet
  werden.

3. **Weniger unnötige DB-Zugriffe**

- Wenn ein QuerySet nicht verwendet wird, wird keine Abfrage ausgeführt.

#### Typische Fehler:

1. QuerySets in Schleifen aufrufen und N+1-Queries erzeugen.
2. Dasselbe QuerySet mehrfach iterieren, ohne Resultat-Caching.
3. `count()` und `len(qs)` verwechseln (Verhalten/Kosten können unterschiedlich
   sein).

#### Praktische Tipps:

1. Für Beziehungen `select_related()` / `prefetch_related()` nutzen.
2. Wenn ein Ergebnis mehrfach im selben Flow gebraucht wird - materialisieren:
   `items = list(qs)`.
3. Für Existenzprüfung `exists()` statt voller Iteration verwenden.
4. SQL profilieren (Django Debug Toolbar, DB-Logs), nicht nur auf Intuition
   vertrauen.

#### Fazit:

`QuerySet` ist die zentrale Abstraktion im Django ORM, und Lazy Evaluation ist
seine Schlüsseloptimierung. Das Verständnis, wann SQL ausgeführt wird, ist
kritisch für die Performance realer Django-Projekte.

</details>

<details>
<summary>51. Wie funktionieren filter(), exclude(), get()?</summary>

#### Django

`filter()`, `exclude()` und `get()` sind grundlegende Methoden des Django ORM
für Datenabfragen. Sie haben eine ähnliche Syntax, aber unterschiedliches
Verhalten und unterschiedliche Garantien.

#### `filter()`:

- Gibt ein `QuerySet` mit allen Datensätzen zurück, die der Bedingung
  entsprechen.
- Wenn es keine Treffer gibt, wird ein leeres `QuerySet` zurückgegeben (ohne
  Exception).

```python
active_users = User.objects.filter(is_active=True)
cheap_products = Product.objects.filter(price__lt=1000)
```

#### `exclude()`:

- Gibt ein `QuerySet` mit Datensätzen zurück, die der Bedingung **nicht**
  entsprechen.

```python
non_archived = Article.objects.exclude(status="archived")
```

#### `get()`:

- Gibt **ein** Modellobjekt zurück.
- Erwartet genau einen Treffer.
- Bei 0 oder >1 Treffern -> wird eine Exception geworfen.

```python
user = User.objects.get(pk=1)
```

#### Exceptions bei `get()`:

1. `Model.DoesNotExist` - nichts gefunden.
2. `Model.MultipleObjectsReturned` - mehr als ein Datensatz gefunden.

Beispiel für sichere Behandlung:

```python
from django.http import Http404

def profile_view(request, user_id):
    try:
        user = User.objects.get(pk=user_id)
    except User.DoesNotExist:
        raise Http404("Benutzer nicht gefunden")
```

Oder kurz:

```python
from django.shortcuts import get_object_or_404
user = get_object_or_404(User, pk=user_id)
```

#### Wann man was verwendet:

1. **`filter()`** - wenn es viele oder null Ergebnisse geben kann.
2. **`exclude()`** - wenn ein Teil der Daten ausgeschlossen werden soll.
3. **`get()`** - wenn ein eindeutiges Ergebnis garantiert ist (PK, unique Feld).

#### Praktische Tipps:

1. `get()` nicht verwenden, wenn Eindeutigkeit nicht garantiert ist.
2. Für Existenzprüfung `exists()` statt `get()+try/except` verwenden.
3. Bedingungen über `Q` für komplexe Logik kombinieren.

#### Fazit:

`filter()` und `exclude()` arbeiten mit Mengen von Datensätzen via QuerySet,
`get()` mit einem einzelnen Objekt und strengen Eindeutigkeitsanforderungen. Die
richtige Methodenwahl reduziert Fehler und vereinfacht den Umgang mit Edge
Cases.

</details>

<details>
<summary>52. Unterschied zwischen get() und filter()?</summary>

#### Django

`get()` und `filter()` suchen beide Daten im ORM, haben aber grundlegend
unterschiedliche Semantik: Das eine gibt **ein Objekt** zurück, das andere
**eine Objektmenge (QuerySet)**.

#### `get()`:

1. Gibt eine Modellinstanz zurück.
2. Erwartet genau einen Treffer.
3. Wirft Exceptions, wenn es 0 oder mehr als 1 Datensatz gibt.

```python
user = User.objects.get(pk=10)
```

Mögliche Exceptions:

- `User.DoesNotExist`
- `User.MultipleObjectsReturned`

#### `filter()`:

1. Gibt ein `QuerySet` zurück.
2. Kann 0, 1 oder viele Datensätze zurückgeben.
3. Wirft keine Exception, wenn nichts gefunden wird.

```python
users = User.objects.filter(is_active=True)
```

#### Zentrale Unterschiede:

1. **Ergebnistyp**

- `get()` -> ein Objekt.
- `filter()` -> QuerySet.

2. **Verhalten bei fehlenden Daten**

- `get()` -> Exception.
- `filter()` -> leeres QuerySet.

3. **Einsatzszenario**

- `get()` -> eindeutige Felder (`id`, `uuid`, `email` mit `unique=True`).
- `filter()` -> Suche nach Bedingungen, bei denen viele Treffer möglich sind.

#### Praktisches Beispiel:

```python
# korrekt: eindeutige Suche
order = Order.objects.get(id=order_id)

# korrekt: Liste der Benutzerbestellungen
orders = Order.objects.filter(user=request.user).order_by("-created_at")
```

#### Typische Fehler:

1. `get()` für nicht-eindeutige Felder verwenden (Risiko
   `MultipleObjectsReturned`).
2. Von `filter()` ein Einzelobjekt erwarten und `.first()` oder `get()`
   vergessen.
3. `get()`-Exceptions in API/View nicht behandeln.

#### Fazit:

`get()` ist für einen punktuellen eindeutigen Datensatz, `filter()` für
Kollektionen und flexible Suche. Wenn die Kardinalität unklar ist, ist der
sicherere Start meistens `filter()`.

</details>

<details>
<summary>53. Wie bekommt man alle Datensätze oder einen einzelnen Datensatz?</summary>

#### Django

Im Django ORM gibt es verschiedene Methoden, um alle Datensätze oder einen
konkreten Datensatz zu holen. Die Wahl hängt davon ab, ob eine Collection oder
ein einzelnes Ergebnis erwartet wird.

#### Alle Datensätze holen:

1. **Alle Datensätze eines Modells**

```python
articles = Article.objects.all()
```

2. **Alle Datensätze nach Bedingung**

```python
articles = Article.objects.filter(is_published=True)
```

3. **Optimierte Auswahl bestimmter Felder**

```python
articles = Article.objects.values("id", "title")
```

#### Einen Datensatz holen:

1. **Genau ein Datensatz mit `get()`**

```python
article = Article.objects.get(pk=article_id)
```

Geeignet, wenn Eindeutigkeit garantiert ist.

2. **Sichere Variante im Web-View**

```python
from django.shortcuts import get_object_or_404

article = get_object_or_404(Article, pk=article_id)
```

3. **Erster Datensatz aus einem QuerySet**

```python
article = Article.objects.filter(is_published=True).first()
```

Gibt ein Objekt oder `None` zurück, ohne Exceptions.

#### Wann man was verwendet:

1. Collection für Listen/Tabellen -> `all()` / `filter()`.
2. Ein eindeutiger Datensatz -> `get()`.
3. Ein Datensatz im Web-Flow mit 404 -> `get_object_or_404()`.
4. Optionales Einzelergebnis -> `first()`.

#### Typische Fehler:

1. `get()` für ein nicht eindeutiges Feld verwenden.
2. `all()` ohne Filter/Paginierung bei großen Tabellen ziehen.
3. `DoesNotExist` in API/View nicht behandeln.

#### Fazit:

Für „alle Datensätze“ verwende `QuerySet` (`all/filter`), für „einen Datensatz“
verwende `get()` oder sichere Wrapper (`get_object_or_404`, `first()`), je nach
Fehleranforderungen und UX.

</details>

<details>
<summary>54. Unterschied zwischen select_related() und prefetch_related()?</summary>

#### Django

`select_related()` und `prefetch_related()` werden zur ORM-Optimierung genutzt,
um das N+1-Problem bei verknüpften Modellen zu vermeiden.

#### `select_related()`:

1. Funktioniert für Beziehungen **ForeignKey** und **OneToOne** (also die
   „eine“-Seite).
2. Macht einen **SQL JOIN** und lädt verknüpfte Daten in einer Abfrage.
3. Effizient für „single-valued“-Beziehungen.

Beispiel:

```python
orders = Order.objects.select_related("customer").all()
for order in orders:
    print(order.customer.email)  # ohne zusätzliche Abfragen
```

#### `prefetch_related()`:

1. Funktioniert für **ManyToMany**, reverse ForeignKey und kann auch für FK/O2O
   genutzt werden.
2. Macht mehrere Abfragen (Hauptabfrage + zusätzliche) und „klebt“ Ergebnisse in
   Python zusammen.
3. Effizient für „multi-valued“-Beziehungen.

Beispiel:

```python
articles = Article.objects.prefetch_related("tags").all()
for article in articles:
    print([tag.name for tag in article.tags.all()])  # ohne N+1
```

#### Zentraler Unterschied:

1. **Mechanismus**

- `select_related()` -> JOIN in einer SQL-Abfrage.
- `prefetch_related()` -> mehrere SQL-Abfragen + Zusammenführung in Python.

2. **Beziehungstypen**

- `select_related()` -> FK/O2O.
- `prefetch_related()` -> M2M, reverse FK (und bei Bedarf andere).

3. **Datenmenge**

- `select_related()` kann Zeilen durch JOINs „aufblähen“.
- `prefetch_related()` ist besser für Collections von Child-Objekten.

#### Kombinierte Verwendung:

```python
orders = (
    Order.objects
    .select_related("customer")
    .prefetch_related("items", "items__product")
)
```

#### Praktische Auswahlregel:

1. Feld aus FK/O2O benötigt -> mit `select_related` starten.
2. Liste verknüpfter Objekte (M2M/reverse) benötigt -> `prefetch_related`.
3. Queries profilieren (Debug Toolbar/Logs), nicht „nach Gefühl“ raten.

#### Typische Fehler:

1. Keinen der beiden Methoden verwenden und N+1 erhalten.
2. `select_related()` auf M2M anwenden (löst das Problem nicht).
3. `.all()` auf Related Manager in Schleifen ohne prefetch aufrufen.

#### Fazit:

`select_related()` optimiert „einzelne“ Beziehungen via JOIN,
`prefetch_related()` „kollektive“ Beziehungen via zusätzliche Abfragen. Die
richtige Kombination beider Methoden liefert den größten Performance-Gewinn für
ORM-Code.

</details>

<details>
<summary>55. Wie optimiert man ORM-Abfragen (annotate, aggregate, F(), Q())?</summary>

#### Django

Die Optimierung von ORM-Abfragen in Django basiert auf der Idee: aufwendige
Berechnungen in die DB zu verlagern und Anzahl der Abfragen sowie das abgerufene
Datenvolumen zu reduzieren.

#### 1. `annotate()` - Berechnungen pro Zeile

- Fügt jedem QuerySet-Objekt ein „virtuelles“ Feld hinzu.
- Nützlich für Zähler, Summen, Zeitpunkte letzter Aktivität usw.

```python
from django.db.models import Count

authors = Author.objects.annotate(books_count=Count("books"))
```

#### 2. `aggregate()` - Zusammenfassung über das gesamte QuerySet

- Gibt ein Dictionary mit aggregierten Werten zurück.

```python
from django.db.models import Avg, Sum

stats = Order.objects.aggregate(
    total_revenue=Sum("amount"),
    avg_revenue=Avg("amount"),
)
```

#### 3. `F()` - Feldoperationen auf DB-Ebene

- Erlaubt Updates ohne Objekt erst in Python zu laden.
- Reduziert Race Conditions bei konkurrierenden Updates.

```python
from django.db.models import F

Product.objects.filter(pk=product_id).update(stock=F("stock") - 1)
```

#### 4. `Q()` - komplexe Bedingungslogik (`AND/OR/NOT`)

- Wenn `filter(a=..., b=...)` allein nicht ausreicht.

```python
from django.db.models import Q

users = User.objects.filter(
    Q(is_active=True) & (Q(role="admin") | Q(role="manager"))
).exclude(Q(email__isnull=True) | Q(email=""))
```

#### Kombiniertes Beispiel:

```python
from django.db.models import Count, Q

articles = (
    Article.objects
    .filter(is_published=True)
    .annotate(comments_count=Count("comments", filter=Q(comments__is_approved=True)))
    .order_by("-comments_count")
)
```

#### Praktische Optimierungsregeln:

1. In der DB berechnen (`annotate/aggregate`), nicht in Python-Schleifen.
2. Für Massenupdates `update(..., F(...))` verwenden.
3. Für komplexe Bedingungen `Q` nutzen statt mehrfacher Abfragen.
4. Mit `select_related/prefetch_related` kombinieren, um N+1 zu vermeiden.
5. Nur benötigte Felder laden (`only`, `values`, `values_list`).

#### Effektprüfung:

1. SQL über `queryset.query` oder `django-debug-toolbar` prüfen.
2. Anzahl der Abfragen vor/nach vergleichen.
3. Execution Plan auf Production-DB prüfen (`EXPLAIN ANALYZE`).

#### Typische Fehler:

1. Aggregationen in Python nach `list(qs)` statt in SQL berechnen.
2. `save()` in Schleifen statt eines einzelnen `update()`.
3. Zu komplexe Annotationen ohne DB-Indizes bauen.

#### Fazit:

`annotate`, `aggregate`, `F`, `Q` sind Kernwerkzeuge für performanten ORM-Code.
Sie helfen, Abfrageanzahl zu reduzieren, überflüssige Python-Berechnungen zu
vermeiden und die DB-Arbeit unter Last stabil zu halten.

</details>

<details>
<summary>56. Wie überschreibt man die Methoden save() und delete()?</summary>

#### Django

In Django kann man `save()` und `delete()` im Modell überschreiben, um
zusätzliche Logik vor/nach dem Speichern oder Löschen eines Datensatzes
hinzuzufügen.

#### So überschreibt man `save()`:

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

Wichtige Regel: immer `super().save(*args, **kwargs)` aufrufen.

#### So überschreibt man `delete()`:

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

#### Was man beachten muss:

1. `QuerySet.update()` ruft `save()` nicht auf.
2. `QuerySet.delete()` ruft das individuelle `delete()` jedes Objekts nicht im
   selben Sinn wie der direkte Instanzaufruf auf.
3. Deshalb sollte für datenintegritätskritische Logik zusätzlich auf
   DB-/Service-Ebene abgesichert werden.

#### Wann Überschreiben sinnvoll ist:

1. Generierung abgeleiteter Felder (Slug, normalisierter Wert).
2. Lokale Modellinvarianten, die nicht von externen Services abhängen.
3. Sauberes Aufräumen verknüpfter lokaler Ressourcen.

#### Wann ein anderer Ansatz besser ist:

1. Komplexe Business-Logik oder Orchestrierung mehrerer Modelle ->
   Service-Schicht.
2. Modulübergreifende Side Effects -> Signals (vorsichtig) oder Domain Events.
3. Massenoperationen -> separate Bulk-Kommandos statt Instanzmethoden.

#### Praktische Regeln:

1. `save()/delete()` kurz und vorhersehbar halten.
2. Keine langsamen externen HTTP-Calls darin ausführen.
3. Side Effects dokumentieren, damit das Team keine „Magie“ bekommt.
4. Solche Stellen mit Tests abdecken (Create/Update/Delete-Szenarien).

#### Fazit:

Das Überschreiben von `save()` und `delete()` ist ein starkes, aber sensibles
Werkzeug. Für lokale Modelllogik ist es sinnvoll; komplexes Domänenverhalten
sollte aus Transparenz- und Kontrollgründen in der Service-Schicht bleiben.

</details>

<details>
<summary>57. Wie funktioniert das kaskadierende Löschen (CASCADE)?</summary>

#### Django

Kaskadierendes Löschen (`models.CASCADE`) bedeutet: Wenn ein „Parent“-Objekt
gelöscht wird, löscht Django automatisch alle verknüpften „Child“-Datensätze.

#### Wo es verwendet wird:

- In `ForeignKey` und `OneToOneField` über den Parameter `on_delete`.

#### Beispiel:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Was passiert:

- `author.delete()` -> Django löscht den Autor und alle seine Bücher.

#### Wann CASCADE sinnvoll ist:

1. Child-Daten haben ohne Parent keinen Sinn.
2. Man will sicherstellen, dass keine „verwaisten“ Datensätze bleiben.
3. Einfacher Domänen-Lifecycle abhängiger Entitäten.

#### Potenzielle Risiken:

1. Unbeabsichtigtes Massenlöschen großer Datenmengen.
2. Schwieriges Audit/Recovery nach Fehlern.
3. Unerwartete Side Effects in verbundenen Domänen.

#### Alternativen zu `on_delete`:

1. `PROTECT` - verbietet das Löschen des Parent, wenn Abhängigkeiten bestehen.
2. `SET_NULL` - setzt `NULL` im Child-Feld (`null=True` ist Pflicht).
3. `SET_DEFAULT` - setzt den Standardwert ein.
4. `RESTRICT` - beschränkt Löschung bei vorhandenen Referenzen (ähnlich strengem
   protect).
5. `DO_NOTHING` - Verantwortung liegt bei DB/Entwickler.

#### Praktische Empfehlungen:

1. Für kritische Business-Daten eher `PROTECT/RESTRICT` verwenden.
2. Für klar abhängige technische Entitäten (z. B. temporäre Datensätze) passt
   oft `CASCADE`.
3. Vor Massenlöschungen prüfen, was genau gelöscht wird.
4. Soft Delete erwägen, wenn historisches Audit nötig ist.

#### Fazit:

`CASCADE` ist ein bequemes Integritätswerkzeug, aber im Verhalten aggressiv. Es
sollte dort eingesetzt werden, wo der Lifecycle der Child-Daten vollständig vom
Parent-Objekt abhängt.

</details>

<details>
<summary>58. Wie funktionieren Transaktionen in Django?</summary>

#### Django

Transaktionen in Django garantieren, dass eine Gruppe von DB-Änderungen als
Einheit ausgeführt wird: Entweder werden alle Änderungen angewendet (`commit`),
oder bei Fehlern keine (`rollback`).

#### Hauptwerkzeug:

- `transaction.atomic()`

#### Grundbeispiel:

```python
from django.db import transaction

@transaction.atomic
def create_order(user, items):
    order = Order.objects.create(user=user)
    for item in items:
        OrderItem.objects.create(order=order, product=item["product"], qty=item["qty"])
    return order
```

Wenn innerhalb ein Exception auftritt, werden alle Änderungen im Block
zurückgerollt.

#### Context Manager:

```python
from django.db import transaction

def transfer(from_acc, to_acc, amount):
    with transaction.atomic():
        from_acc.balance -= amount
        to_acc.balance += amount
        from_acc.save()
        to_acc.save()
```

#### Verschachtelte Transaktionen und Savepoints:

- Verschachtelte `atomic()` erzeugen Savepoints.
- Ein Fehler im inneren Block kann nur den Teil bis zum Savepoint zurückrollen.

#### Modus `ATOMIC_REQUESTS`:

In `settings.py` kann eine Transaktion „pro HTTP-Request“ aktiviert werden:

```python
DATABASES["default"]["ATOMIC_REQUESTS"] = True
```

Das ist bequem, aber bei komplexen Endpoints nicht immer optimal für
Performance.

#### Praktische Empfehlungen:

1. Nur wirklich zusammenhängende Operationen mit `atomic()` kapseln.
2. Transaktionen kurz halten (minimale externe Aufrufe innerhalb).
3. Keine HTTP/API-Calls innerhalb einer Transaktion ausführen.
4. Für konkurrierende Szenarien `select_for_update()` verwenden.

#### Beispiel für Row-Locking:

```python
with transaction.atomic():
    account = Account.objects.select_for_update().get(pk=account_id)
    account.balance = F("balance") - amount
    account.save(update_fields=["balance"])
```

#### Typische Fehler:

1. Einen Teil der Operation vor `atomic()`, den Rest danach ausführen.
2. Lange Transaktionen, die Locks halten und andere Requests blockieren.
3. Erwarten, dass die Transaktion externe Systeme (Queues, Drittanbieter-APIs)
   abdeckt.
4. DB-Isolationslevel in High-Concurrency-Szenarien ignorieren.

#### Fazit:

Transaktionen in Django sind ein grundlegender Mechanismus für Datenkonsistenz.
`transaction.atomic()` sollte Standard bei kritischen mehrstufigen Operationen
sein, besonders in Finanz-, Lager- und Workflow-Domänen.

</details>

<details>
<summary>59. Unterstützt Django NoSQL?</summary>

#### Django

Kurz: Django ist **nativ auf relationale DBs ausgerichtet** (PostgreSQL, MySQL,
SQLite, Oracle) über sein ORM. NoSQL wird nicht „out of the box“ auf demselben
Niveau unterstützt, aber Integration ist möglich.

#### Was das praktisch bedeutet:

1. **Djangos Kern-ORM = SQL-first**

- Die meisten Features (Migrationen, Beziehungen, Admin, Constraints) sind auf
  SQL ausgelegt.

2. **NoSQL lässt sich über Drittanbieter-Bibliotheken anbinden**

- Für MongoDB und andere Lösungen gibt es Adapter/ODMs von Drittanbietern, aber
  die Kompatibilität mit dem Django-Ökosystem ist oft nicht vollständig.

3. **Häufigster Production-Ansatz ist hybrid**

- Das Haupt-Transaktionsmodell läuft auf PostgreSQL.
- NoSQL-Storage für spezialisierte Aufgaben (Cache, Dokumente, Suche, Events).

#### Typische NoSQL-Rollen in Django-Projekten:

1. Redis - Cache, Rate Limit, Queue-Broker, Sessions.
2. Elasticsearch/OpenSearch - Volltextsuche und analytische Abfragen.
3. Dokumenten-DBs - separate Domänen mit flexiblem Schema (wenn nötig).

#### Wann SQL in Django meist besser ist:

- Komplexe Beziehungen zwischen Entitäten.
- Transaktionalität und strenge Konsistenzgarantien.
- Viel Standard-CRUD + Admin + klares Domänenmodell.

#### Wann NoSQL sinnvoll sein kann:

- Sehr flexibles/wechselndes Datenschema.
- Hochperformanter Key-Value-Zugriff.
- Such-/Log-Analytics-Szenarien, in denen SQL ineffizient ist.

#### Praktische Tech-Lead-Empfehlungen:

1. Relationale DB nicht „wegen Trend“ durch NoSQL ersetzen.
2. Mit PostgreSQL als verlässlichem Default für Django starten.
3. NoSQL gezielt für konkrete nichtfunktionale Anforderungen ergänzen (Latenz,
   Suche, Scale).
4. Konsistenz zwischen SQL und NoSQL separat entwerfen (Outbox/Events/Retry).

#### Fazit:

Django ist kein NoSQL-first-Framework, funktioniert aber sehr gut in einer
hybriden Architektur. Für die meisten Produkte ist die optimale Strategie: SQL
als Basis der Domänendaten + NoSQL als spezialisierte Ergänzung für bestimmte
Lastprofile.

</details>

<details>
<summary>60. Welche typischen Django-Exceptions sollte man kennen?</summary>

#### Django

In Django gibt es eine Reihe typischer Exceptions, die in realen Projekten
regelmäßig auftreten. Das Wissen darüber beschleunigt das Debugging und hilft,
Fehlerbehandlung in Views/APIs korrekt aufzubauen.

#### Wichtigste Exceptions:

1. **`Model.DoesNotExist`**

- Tritt bei `Model.objects.get(...)` auf, wenn kein Datensatz gefunden wird.

2. **`Model.MultipleObjectsReturned`**

- `get()` hat mehr als einen Datensatz zurückgegeben.

3. **`ValidationError`**

- Validierungsfehler bei Formularen, Modellen, benutzerdefinierten Validatoren.

4. **`IntegrityError`**

- Verletzung von DB-Constraints (`UNIQUE`, `FK`, `NOT NULL`, `CHECK`).

5. **`ObjectDoesNotExist`**

- Basis-Exception für alle `*.DoesNotExist`.

6. **`PermissionDenied`**

- Kein Zugriff auf die Ressource (liefert 403).

7. **`SuspiciousOperation`**

- Verdächtige/gefährliche Aktivität (z. B. ungültiger Host/Header).

8. **`Http404`**

- Wird genutzt, um explizit 404 zurückzugeben.

9. **`ImproperlyConfigured`**

- Konfigurationsfehler in Settings, URL, Middleware, Apps.

10. **`OperationalError` (DB-Backend)**

- Probleme mit DB-Verbindung/Verfügbarkeit, Timeouts, Netzstörungen.

#### Beispiele für Behandlung:

```python
from django.core.exceptions import ValidationError
from django.db import IntegrityError
from django.http import Http404

try:
    user = User.objects.get(pk=user_id)
except User.DoesNotExist:
    raise Http404("Benutzer nicht gefunden")

try:
    create_order(...)
except ValidationError as exc:
    return JsonResponse({"errors": exc.message_dict}, status=400)
except IntegrityError:
    return JsonResponse({"error": "Datenintegrität verletzt"}, status=409)
```

#### Praktische Regeln:

1. Für 404 in Views `get_object_or_404` verwenden.
2. Exceptions nicht ohne Logging „verschlucken“.
3. User-Fehler (4xx) und Systemfehler (5xx) trennen.
4. In Production keine Stacktraces an Clients zurückgeben.
5. Für APIs Fehlerformat standardisieren (Code, Message, Details).

#### Typische Anti-Patterns:

1. `except Exception:` ohne Spezifizierung.
2. `IntegrityError` ignorieren und inkonsistente Folgeoperationen ausführen.
3. Fachliche und technische Fehler in ein einziges „400 unknown“ mischen.

#### Fazit:

Gute Exception-Behandlung in Django bedeutet API-Qualität, Service-Stabilität
und schnelle Problemaufklärung in Production. Die Basis-Exceptions sollte man
systematisch kennen und behandeln, nicht nur punktuell.

</details>

<details>
<summary>61. Was ist Django Admin? Wie registriert man ein Modell?</summary>

#### Django

`Django Admin` ist ein eingebautes Administrationspanel zur Verwaltung von
Modelldaten über ein Web-Interface, ohne ein eigenes Back-Office von Grund auf
zu bauen.

#### Was Django Admin bietet:

1. CRUD für Modelle „out of the box“.
2. Suche, Filter, Sortierung, Paginierung.
3. Arbeit mit verknüpften Objekten (Inlines).
4. Schnelles Back-Office für Business-Teams.

#### Modell registrieren (Minimum):

```python
# app/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

Danach erscheint das Modell unter `/admin/`.

#### Empfohlene Variante über `ModelAdmin`:

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

#### Voraussetzungen für Admin-Login:

1. Migrationen angewendet:

```bash
python manage.py migrate
```

2. Superuser erstellt:

```bash
python manage.py createsuperuser
```

3. Server gestartet und `/admin/` geöffnet.

#### Praktische Empfehlungen:

1. `list_display`, `search_fields`, `list_filter` für Kernmodelle konfigurieren.
2. Admin-Zugriff über Rollen/Permissions begrenzen.
3. Bei großen Tabellen QuerySet im `ModelAdmin` optimieren
   (select_related/prefetch).
4. Admin nicht als öffentliches Interface für Endnutzer verwenden.

#### Fazit:

Django Admin ist ein starkes Werkzeug für interne Datenverwaltung. Die
Modellregistrierung dauert Minuten, und mit einem Basis-`ModelAdmin` wird die
Admin-Oberfläche schnell zu einem produktiven Back-Office für das Team.

</details>

<details>
<summary>62. Was ist ein Superuser?</summary>

#### Django

Ein `Superuser` in Django ist ein Benutzer mit maximalen administrativen Rechten
im System, typischerweise für Zugriff auf Django Admin und die volle Verwaltung
von Daten.

#### Zentrale Eigenschaften eines Superusers:

1. `is_superuser = True`
2. `is_staff = True`
3. Hat alle Permissions, ohne jede einzelne Berechtigung separat zuzuweisen.
4. Kann Benutzer, Gruppen, Modelle und Inhalte über `/admin/` verwalten.

#### So erstellt man einen Superuser:

```bash
python manage.py createsuperuser
```

Danach fragt Django nach:

- username
- email (abhängig vom Modell)
- password

#### Wo er verwendet wird:

1. Initiale Projektadministration.
2. Konfiguration von Rollen/Gruppen und Zugriffsrechten.
3. Operativer Support über Django Admin.

#### Wichtige Sicherheits-Hinweise:

1. Superuser-Account nicht für tägliche operative Arbeit verwenden.
2. Anzahl der Superuser in Production minimal halten.
3. Starke Passwörter + 2FA nutzen (wenn über SSO/Admin-Lösung verfügbar).
4. Admin-Aktionen loggen und Zugriff über IP/VPN kontrollieren.
5. Keine „temporären“ Superuser ohne klaren Entfernungsprozess anlegen.

#### Praktische Rolle im Team:

- Superuser ist für die Bootstrap-Phase nötig.
- In stabilen Prozessen sollten die meisten Aufgaben über `staff` + Gruppen +
  granulare Permissions laufen, nicht über Vollzugriff.

#### Fazit:

Ein Superuser ist der „Root-Benutzer“ in Django. Das Werkzeug ist kritisch
wichtig für Administration, aber der Zugriff muss maximal begrenzt und
kontrolliert sein.

</details>

<details>
<summary>63. Wie passt man Django Admin an?</summary>

#### Django

Die Anpassung von Django Admin erfolgt über die Klasse `ModelAdmin` und
verwandte Mechanismen (Inlines, Actions, Permissions, Form-Overrides). Damit
kann man die Basis-Adminoberfläche in ein effektives Back-Office-Tool
verwandeln.

#### Basis-Anpassung von `ModelAdmin`:

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

#### Häufigste Werkzeuge:

1. `list_display` - welche Spalten in der Liste sichtbar sind.
2. `list_filter` - Filter rechts.
3. `search_fields` - Suche über Felder/Beziehungen.
4. `readonly_fields` - nur-lesbare Felder.
5. `fieldsets` - Gruppierung von Feldern im Bearbeitungsformular.
6. `actions` - Massenaktionen für ausgewählte Datensätze.

#### Inline-Bearbeitung verknüpfter Modelle:

```python
class OrderItemInline(admin.TabularInline):
    model = OrderItem
    extra = 0

@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    inlines = [OrderItemInline]
```

#### Eigene Actions:

```python
@admin.action(description="Als veröffentlicht markieren")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)
```

#### Zugriffsbeschränkung:

- `has_view_permission`, `has_change_permission`, `has_delete_permission`
- `get_queryset()` für Data-Scoping (z. B. Manager sieht nur eigene Objekte).

#### Performance-Optimierung im Admin:

1. `list_select_related` für FK in `list_display` nutzen.
2. Vorsicht mit `search_fields` auf großen Tabellen (Indizes sind Pflicht).
3. „Schwere“ Berechnungen in List Views reduzieren.
4. Für sehr große Referenzlisten `autocomplete_fields` einsetzen.

#### Zusätzliche Anpassungen:

- Überschreiben von `form`/`get_form`.
- Überschreiben von `save_model`/`delete_model`.
- Eigene Admin-Templates für spezifisches UI.

#### Fazit:

Django Admin skaliert gut über `ModelAdmin`: von einfacher Registrierung bis zu
einem vollwertigen internen Panel mit Rollen, Filtern, Massenaktionen und
kontrollierter Performance.

</details>

<details>
<summary>64. Welche Komponenten hat Django Admin und welche individuellen Einstellungen gibt es?</summary>

#### Django

Django Admin besteht aus mehreren zentralen Komponenten, die sich flexibel an
Team-Business-Prozesse anpassen lassen: Objektliste, Bearbeitungsformular,
Filter, Suche, Actions, Zugriffsrechte, Inlines und globale Admin-Site-
Konfiguration.

#### Hauptkomponenten von Django Admin:

1. **Admin Site (`admin.site`)**

- Globales Admin-Panel; Header/Title/Index können angepasst werden.

2. **`ModelAdmin`**

- Konfiguration der Darstellung eines konkreten Modells im Admin.

3. **Change List**

- Objektlisten-Seite (`list_display`, `list_filter`, `search_fields`).

4. **Change Form**

- Erstell-/Bearbeitungsformular (`fields`, `fieldsets`, `readonly_fields`).

5. **Inlines**

- Bearbeitung verknüpfter Modelle auf derselben Seite.

6. **Actions**

- Massenoperationen auf ausgewählten Datensätzen.

7. **Permissions**

- Zugriff auf Anzeigen/Bearbeiten/Löschen nach Rollen.

#### Beispiel individueller Einstellungen:

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
        ("Grunddaten", {"fields": ("email", "first_name", "last_name")}),
        ("Status", {"fields": ("is_active",)}),
        ("System", {"fields": ("created_at", "updated_at")}),
    )
```

#### Globale Admin-Site-Einstellungen:

```python
from django.contrib import admin

admin.site.site_header = "Admin Panel"
admin.site.site_title = "Backoffice"
admin.site.index_title = "Systemverwaltung"
```

#### Individuelles Verhalten nach Rollen:

- `get_queryset()` - einschränken, was ein bestimmter Staff-Benutzer sieht.
- `get_readonly_fields()` - einen Teil der Felder rollenabhängig read-only
  machen.
- `has_change_permission()` / `has_delete_permission()` - granularer
  Rechtekontrolle.

#### Komponenten, die oft in Production ergänzt werden:

1. `autocomplete_fields` für schwere FK-Felder.
2. `list_select_related` für List-View-Optimierung.
3. Eigene `form` und `formfield_overrides` für bessere UX.
4. Eigene Templates für spezifische Back-Office-Szenarien.

#### Fazit:

Die Stärke von Django Admin liegt darin, dass man aus Basis-Komponenten ein
steuerbares internes Interface für konkrete Team-Prozesse bauen kann: schnell,
sicher und operativ komfortabel.

</details>

<details>
<summary>65. Was sind Django Admin Actions und ihre Anpassung?</summary>

#### Django

`Admin Actions` in Django sind Massenoperationen auf ausgewählten Objekten in
der Admin-Liste. Sie ermöglichen, typische Aufgaben schnell auszuführen, ohne
jeden Datensatz manuell zu bearbeiten.

#### Was eine Action ist:

- Eine Funktion oder Methode, die Folgendes annimmt: `modeladmin`, `request`,
  `queryset`.
- Wird für die Objektmenge aufgerufen, die der Admin-Benutzer in der Liste
  markiert hat.

#### Basisbeispiel einer Action:

```python
from django.contrib import admin
from .models import Article

@admin.action(description="Ausgewählte Artikel veröffentlichen")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)

@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    list_display = ("id", "title", "is_published")
    actions = [make_published]
```

#### Beispiel einer Action als `ModelAdmin`-Methode:

```python
@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    actions = ["mark_as_paid"]

    @admin.action(description="Als bezahlt markieren")
    def mark_as_paid(self, request, queryset):
        updated = queryset.update(status="paid")
        self.message_user(request, f"Bestellungen aktualisiert: {updated}")
```

#### Anpassung von Actions:

1. Eigene `description` für UI.
2. Verfügbarkeitsbedingungen nach Rolle/Status.
3. Rückgabe einer Zwischenseite zur Bestätigung (custom admin view).
4. Logging ausgeführter Massenaktionen.

#### Praktische Empfehlungen:

1. Für Massenänderungen `queryset.update()` bevorzugen (schneller, weniger SQL).
2. Wenn Business-Logik pro Objekt nötig ist, vorsichtig in Transaktion
   iterieren.
3. Zusammenfassung über `message_user` anzeigen.
4. Gefährliche Actions für nicht-administrative Rollen einschränken.

#### Wichtige Nuancen:

1. `queryset.update()` ruft `save()` und `post_save`-Signale nicht auf.
2. Massenlöschung über Standard-Action kann ohne Zusatzkontrolle riskant sein.
3. Für kritische Operationen besser einen Bestätigungsschritt ergänzen.

#### Typische Action-Use-Cases:

- Publish/Unpublish von Content.
- Batch-Statuszuweisung.
- Export ausgewählter Datensätze als CSV.
- Start von Background-Verarbeitung für ausgewählte IDs.

#### Fazit:

Admin Actions sind ein schnelles Werkzeug für operative Automatisierung im
Django Admin. Bei richtiger Anpassung beschleunigen sie die Teamarbeit deutlich
und reduzieren manuelle Routineaufgaben.

</details>

<details>
<summary>66. Was ist Middleware und wie funktioniert sie?</summary>

#### Django

`Middleware` in Django ist eine Verarbeitungsschicht zwischen
HTTP-Request/-Response und View. Sie erlaubt, Code **vor** dem Eintritt des
Requests in die View und **nach** der Erstellung der Response auszuführen.

#### So funktioniert die Middleware-Pipeline:

1. Request kommt in Django an.
2. Läuft der Reihe nach durch Middleware (Request-Phase).
3. Geht in URL-Resolver und View.
4. Response läuft in umgekehrter Reihenfolge zurück durch Middleware
   (Response-Phase).
5. Wird an den Client gesendet.

#### Wichtiges Detail:

- Die Reihenfolge in `settings.py` (`MIDDLEWARE = [...]`) ist kritisch wichtig.
- Obere Middleware sieht den Request zuerst, die Response aber zuletzt.

#### Typische Aufgaben von Middleware:

1. Sicherheit (Security-Header, Host-Checks).
2. Sessions und Authentifizierung.
3. CSRF-Schutz.
4. Lokalisierung (Locale/Sprache).
5. Logging, Request-ID, Metriken.
6. Caching auf Request-/Response-Ebene.

#### Middleware-Skelett:

```python
class SimpleMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # vor der View
        response = self.get_response(request)
        # nach der View
        return response
```

#### Wo sie eingebunden wird:

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    # ...
]
```

#### Praktische Regeln:

1. Middleware leicht und schnell halten.
2. Keine schwere Domänen-Business-Logik dort platzieren.
3. Langsame externe Aufrufe in Middleware vermeiden.
4. Reihenfolge in der Middleware-Liste sorgfältig kontrollieren.

#### Typische Fehler:

1. Zu „intelligente“ Middleware mit Side Effects.
2. Falsche Reihenfolge, die Auth/CSRF/Session-Flow bricht.
3. Logikduplikate zwischen Middleware und View.

#### Fazit:

Middleware ist ein globaler Interceptor für Requests/Responses in Django. Ihre
Stärke sind zentralisierte cross-cutting Aufgaben (Sicherheit, Sessions,
Logging), nicht die Business-Logik einzelner Endpoints.

</details>

<details>
<summary>67. Welche eingebauten Middleware gibt es?</summary>

#### Django

Django hat ein Set eingebauter Middleware, die die Basisanforderungen einer
Webanwendung abdecken: Sicherheit, Sessions, Authentifizierung, CSRF, Caching,
Lokalisierung.

#### Häufigste Built-in-Middleware:

1. **`django.middleware.security.SecurityMiddleware`**

- Security-Header, HTTPS-bezogene Einstellungen, grundlegende Schutzmechanismen.

2. **`django.contrib.sessions.middleware.SessionMiddleware`**

- Unterstützung serverseitiger Benutzersessions.

3. **`django.middleware.common.CommonMiddleware`**

- Allgemeines HTTP-Verhalten (z. B. `APPEND_SLASH`, `PREPEND_WWW`).

4. **`django.middleware.csrf.CsrfViewMiddleware`**

- Schutz vor CSRF-Angriffen für state-changing Requests.

5. **`django.contrib.auth.middleware.AuthenticationMiddleware`**

- Fügt `request.user` hinzu und integriert das Auth-System in den Request-Flow.

6. **`django.contrib.messages.middleware.MessageMiddleware`**

- Unterstützung für Flash-Messages (`messages.success`, `messages.error`).

7. **`django.middleware.clickjacking.XFrameOptionsMiddleware`**

- Schutz vor Clickjacking über den Header `X-Frame-Options`.

8. **`django.middleware.locale.LocaleMiddleware`**

- Erkennung von Sprache/Locale für i18n.

9. **`django.middleware.gzip.GZipMiddleware`**

- Komprimierung von Responses (vorsichtig bei bereits komprimiertem Content).

10. **`django.middleware.cache.UpdateCacheMiddleware` /
    `FetchFromCacheMiddleware`**

- Site-weites Caching auf Middleware-Ebene.

#### Typische Reihenfolge in `MIDDLEWARE` (gekürzt):

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

#### Praktische Hinweise:

1. Die Middleware-Reihenfolge ist wichtig und beeinflusst das Verhalten der
   gesamten Anwendung.
2. `SecurityMiddleware`, `CsrfViewMiddleware`, `AuthenticationMiddleware` nicht
   ohne Verständnis der Folgen entfernen.
3. In Production Security-Header und Cache-Policy nach Middleware-Änderungen
   prüfen.

#### Fazit:

Djangos eingebaute Middleware deckt die meisten infrastrukturellen Anforderungen
„out of the box“ ab. Die richtige Auswahl und Reihenfolge wirkt sich direkt auf
Sicherheit, Stabilität und Verhalten der Anwendung in Production aus.

</details>

<details>
<summary>68. Wie erstellt man eigene Middleware?</summary>

#### Django

Eigene Middleware in Django erstellt man als Klasse, die `get_response` annimmt
und `request/response` im globalen Request-Processing-Pipeline abfängt.

#### Minimales Middleware-Template:

```python
# app/middleware.py
class RequestIdMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # Logik vor der View
        response = self.get_response(request)
        # Logik nach der View
        return response
```

#### Beispiel mit Request-ID:

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

#### Einbindung in `settings.py`:

```python
MIDDLEWARE = [
    # ...
    "app.middleware.RequestIdMiddleware",
]
```

#### Wo sie in die Liste gehört:

1. Security-/Session-Middleware - in der Regel weiter oben.
2. Custom Logging/Request-ID - oft nach den grundlegenden
   Security-/Session-Middleware.
3. Reihenfolge ist wichtig: Sie beeinflusst, was Middleware im `request` sieht.

#### Was Middleware tun kann:

- Header hinzufügen.
- Request/Response loggen.
- Tracing-Kontext hinzufügen.
- Request nach globalen Regeln ablehnen.

#### Was man vermeiden sollte:

1. Komplexe Business-Logik eines konkreten Endpoints.
2. Langsame externe HTTP-Calls.
3. Schwere Operationen, die jeden Request blockieren.

#### Fazit:

Custom Middleware ist ein Werkzeug für cross-cutting Aufgaben auf Ebene der
gesamten Anwendung. Sie sollte leicht und vorhersehbar sein und korrekt in
`MIDDLEWARE` platziert werden, um Side Effects zu vermeiden.

</details>

<details>
<summary>69. Was sind Signals und wann sollte man sie verwenden?</summary>

#### Django

`Signals` in Django sind ein Event-Mechanismus, der erlaubt, Code als Reaktion
auf bestimmte Aktionen auszuführen (z. B. Speichern oder Löschen eines Modells),
ohne diese Logik direkt in View oder Service aufzurufen.

#### So funktioniert es:

1. Ein Event (Signal) tritt auf, z. B. `post_save`.
2. Eine Receiver-Funktion, die auf dieses Event subscribed ist, läuft
   automatisch.

#### Häufig verwendete Signale:

1. `pre_save`, `post_save`
2. `pre_delete`, `post_delete`
3. `m2m_changed`
4. `request_started`, `request_finished` (seltener für App-Logik)

#### Beispiel `post_save`:

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

Import/Registrierung in `apps.py`:

```python
from django.apps import AppConfig

class UsersConfig(AppConfig):
    name = "users"

    def ready(self):
        import users.signals  # noqa
```

#### Wann Signals sinnvoll sind:

1. Locker gekoppelte Side Effects (z. B. Profil nach Benutzererstellung
   erzeugen).
2. Technische Hooks, die Views nicht verkomplizieren sollen.
3. Events, bei denen Entkopplung zwischen Modulen wichtig ist.

#### Wann man sie besser nicht nutzt:

1. Kritische Business-Logik mit klar erforderlicher Schrittfolge.
2. Komplexe Orchestrierungen zwischen mehreren Services.
3. Logik, die in einem expliziten Use Case transparent sein muss.

#### Typische Signal-Probleme:

1. „Magie“ und unerwartete Side Effects.
2. Schwieriges Debugging in großen Projekten.
3. Doppelte Aufrufe bei ungenauer Registrierung.
4. Schwer kontrollierbare Reihenfolge bei vielen Receivern.

#### Praktische Regeln:

1. Signale kurz und schnell halten.
2. Lange/schwere Aufgaben in Queue auslagern (Celery/RQ).
3. Dokumentieren, auf welche Events ein Modul subscribed ist.
4. Zentrale transaktionale Business-Logik nicht im Signal verstecken.

#### Fazit:

Signals sind in Django nützlich für moderate Side-Event-Logik und lose
Modulkopplung. Für Core-Business-Prozesse ist eine explizite Service-Schicht
meist zuverlässiger, weil der Flow direkt im Code sichtbar bleibt.

</details>

<details>
<summary>70. Unterschied zwischen Signals und Middleware.</summary>

#### Django

`Middleware` und `Signals` lösen unterschiedliche Aufgaben, obwohl beide wie ein
„Ort für zusätzliche Logik“ wirken. Der Schlüsselunterschied ist die
**Event-Ebene**, auf der sie arbeiten.

#### Middleware:

1. Arbeitet auf der Ebene von **HTTP-Request/Response**.
2. Läuft für jeden Request in der globalen Pipeline.
3. Wird für cross-cutting Web-Aufgaben genutzt.

Typische Cases:

- Security-Header
- Auth/Session-Flow
- Logging/Tracing/Request-ID
- Locale/Caching/Compression

#### Signals:

1. Arbeiten auf der Ebene von **Modell-/Framework-Events**.
2. Feuern bei Aktionen wie `post_save`, `post_delete`, `m2m_changed`.
3. Werden genutzt, um auf Events der Domänenmodelle zu reagieren.

Typische Cases:

- Profil nach Benutzererstellung anlegen
- Synchronisierung von Hilfsentitäten
- Lightweight Hooks nach Datenänderungen

#### Hauptunterschied:

- Middleware reagiert auf Request/Response.
- Signals reagieren auf Daten-/Modell-Events.

#### Wann man was wählt:

1. Globale HTTP-Verhaltenslogik nötig -> **Middleware**.
2. Reaktion auf Modelländerung nötig -> **Signals**.
3. Explizite Kontrolle über Business-Flow nötig -> **Service-Schicht**, nicht
   Signals/Middleware.

#### Vergleichstabelle:

| Kriterium        | Middleware                | Signals                       |
| ---------------- | ------------------------- | ----------------------------- |
| Ebene            | HTTP-Pipeline             | Modell-/Framework-Events      |
| Startpunkt       | Vor/nach View             | Vor/nach save/delete usw.     |
| Flow-Transparenz | Höher (über `MIDDLEWARE`) | Niedriger (kann „Magie“ sein) |
| Aufgabentyp      | Infrastrukturell          | Ereignisbasierte Side Effects |

#### Typische Fehler:

1. Modell-Business-Logik in Middleware legen.
2. Kritischen Business-Flow ohne explizite Orchestrierung in Signals verstecken.
3. Dieselbe Logik in beiden Schichten duplizieren.

#### Fazit:

Middleware ist für HTTP-Infrastruktur, Signals für Reaktionen auf Modell-Events.
Für wichtige Business-Logik sind explizite Services besser: transparenter,
besser testbar und weniger anfällig für versteckte Side Effects.

</details>

<details>
<summary>71. Wie funktioniert das Authentifizierungs- und Autorisierungssystem?</summary>

#### Django

In Django besteht das Zugriffssystem aus zwei Teilen:

1. **Authentifizierung (authentication)** - wer bist du?
2. **Autorisierung (authorization)** - was darfst du?

#### So funktioniert Authentifizierung:

1. Benutzer sendet Login/Passwort.
2. Django prüft Credentials über `authenticate()`.
3. Bei Erfolg wird `login()` aufgerufen und eine Session erstellt.
4. In folgenden Requests fügt `AuthenticationMiddleware` `request.user` hinzu.

Basisbeispiel:

```python
from django.contrib.auth import authenticate, login

user = authenticate(request, username=username, password=password)
if user is not None:
    login(request, user)
```

#### So funktioniert Autorisierung:

- Django prüft Benutzerrechte über Permissions, Gruppen und rollenbasierte
  Regeln.
- Basis-Permissions für Modelle: `add`, `change`, `delete`, `view`.

Rechteprüfung:

```python
if request.user.has_perm("orders.change_order"):
    ...
```

#### Werkzeuge für Zugriffskontrolle:

1. `@login_required` - Zugriff nur für authentifizierte Nutzer.
2. `@permission_required("app.perm_codename")`
3. `LoginRequiredMixin`, `PermissionRequiredMixin` für CBV.
4. Gruppen (`Group`) für rollenbasierte Permission-Sets.

#### Session-Modell (Standard):

- Nach `login()` erstellt Django eine Session in DB/Cache.
- Session-ID wird im Cookie gespeichert.
- Bei jedem Request wird der Benutzer über diese Session identifiziert.

#### Wo es konfiguriert wird:

- `AUTHENTICATION_BACKENDS`
- `LOGIN_URL`, `LOGIN_REDIRECT_URL`, `LOGOUT_REDIRECT_URL`
- `AUTH_USER_MODEL` (falls benutzerdefiniertes User-Modell)

#### Praktische Empfehlungen:

1. Zugriff nicht nur im Frontend prüfen - Backend muss Source of Truth sein.
2. Rechte über Rollen gruppieren, nicht einzeln pro User vergeben.
3. Für APIs Token-/Session-Auth und Zugriffspolicy separat designen.
4. Sensible Admin-Aktionen für Audit loggen.

#### Fazit:

In Django ist Authentifizierung für die Benutzeridentifikation zuständig,
Autorisierung für Berechtigungen. Zusammen bilden sie ein sicheres und
skalierbares Zugriffsmodell für Web- und API-Anwendungen.

</details>

<details>
<summary>72. Wie implementiert man die Benutzerregistrierung?</summary>

#### Django

Die Benutzerregistrierung in Django besteht meist aus einem Formular,
View-Logik, Benutzererstellung mit gehashtem Passwort und (optional)
automatischem Login.

#### Basisansatz:

1. Registrierungsformular erstellen (`UserCreationForm` oder custom).
2. Formular im View verarbeiten (`GET`/`POST`).
3. Benutzer speichern.
4. Auf Login umleiten oder Auto-Login ausführen.

#### Formularbeispiel:

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

#### View-Beispiel:

```python
# users/views.py
from django.contrib.auth import login
from django.shortcuts import redirect, render
from .forms import SignUpForm

def signup_view(request):
    if request.method == "POST":
        form = SignUpForm(request.POST)
        if form.is_valid():
            user = form.save()  # Passwort wird automatisch gehasht
            login(request, user)  # optional: sofort einloggen
            return redirect("home")
    else:
        form = SignUpForm()
    return render(request, "users/signup.html", {"form": form})
```

#### Template:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Registrieren</button>
</form>
```

#### URL:

```python
path("signup/", signup_view, name="signup")
```

#### Wichtige Sicherheitsregeln:

1. Passwort niemals manuell als Plain Text speichern.
2. `UserCreationForm` oder `set_password()` verwenden.
3. Schutz vor Brute Force hinzufügen (Rate Limiting / Captcha, wo nötig).
4. Für Production idealerweise E-Mail-Bestätigung vor Account-Aktivierung.

#### Erweiterung der Registrierung:

1. Benutzerprofil (über `OneToOne`).
2. E-Mail-Bestätigung per Token.
3. Social Login (Google/GitHub) über allauth.
4. Audit-Log für Registrierungsereignisse.

#### Fazit:

In Django lässt sich Registrierung schnell über eingebaute Auth-Formulare und
View-Flow umsetzen. Entscheidend sind korrekte Passwortverarbeitung, CSRF-Schutz
und ein durchdachter Aktivierungsprozess für Accounts in Production.

</details>

<details>
<summary>73. Wie erstellt man ein eigenes Benutzermodell?</summary>

#### Django

Ein eigenes Benutzermodell in Django erstellt man, wenn der Standard-`User`
nicht ausreicht (z. B. E-Mail als Login, zusätzliche Pflichtfelder,
benutzerdefinierte Identifikationslogik).

#### Schlüsselregel:

`AUTH_USER_MODEL` muss **zu Projektbeginn**, vor den ersten Migrationen,
definiert werden. Ein späterer Wechsel ist teuer und riskant.

#### Variante 1 (in 90% der Fälle empfohlen): `AbstractUser`

- Man erbt den eingebauten Benutzer und ergänzt eigene Felder.
- Der einfachste und stabilste Weg.

```python
# users/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    phone = models.CharField(max_length=30, blank=True)
    timezone = models.CharField(max_length=64, blank=True, default="UTC")
```

In `settings.py`:

```python
AUTH_USER_MODEL = "users.User"
```

#### Variante 2: `AbstractBaseUser` + `PermissionsMixin`

- Volle Kontrolle über Modell und Login-Feld.
- Deutlich komplexer: eigener `UserManager`, `USERNAME_FIELD`,
  `REQUIRED_FIELDS`, Kompatibilität mit Admin/Forms/Auth-Flow.

Nur verwenden, wenn wirklich ein nichtstandardmäßiges Auth-Modell nötig ist.

#### Beispiel für Referenz auf den benutzerdefinierten User in Modellen:

```python
from django.conf import settings

class Order(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
```

#### Im Code statt direktem `User`-Import:

```python
from django.contrib.auth import get_user_model
User = get_user_model()
```

#### Praktische Empfehlungen:

1. Wenn unsicher - direkt ein Custom-Modell via `AbstractUser` anlegen.
2. `from django.contrib.auth.models import User` im Domänencode vermeiden.
3. Sicherstellen, dass Forms/Admin/Auth-Backend mit deinem Modell funktionieren.
4. Registrierung, Login, Reset Password, Permissions per Tests abdecken.

#### Typische Fehler:

1. Versuch, das Benutzermodell nach Production-Start zu wechseln.
2. Harter Import des Standard-`User` in Modellen und Migrationen.
3. `AbstractBaseUser` ohne echte Notwendigkeit und ohne vollständige
   Konfiguration.

#### Fazit:

Ein korrektes Custom-User-Modell in Django ist eine strategische Entscheidung
zum Projektstart. Der sicherste Weg: `AbstractUser` + `AUTH_USER_MODEL` +
konsequente Nutzung von `get_user_model()` und `settings.AUTH_USER_MODEL` im
gesamten Projekt.

</details>

<details>
<summary>74. Wofür verwendet man `login_required`?</summary>

#### Django

`login_required` ist ein Decorator, der den Zugriff auf eine View nur für
angemeldete Benutzer erlaubt.

#### So funktioniert es:

1. Wenn der Benutzer authentifiziert ist -> wird die View ausgeführt.
2. Wenn nicht -> Redirect auf die Login-Seite (`LOGIN_URL`) mit dem Parameter
   `next`.

#### Beispiel für FBV:

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, "dashboard.html")
```

#### Eigenes Login-URL:

```python
@login_required(login_url="/auth/login/")
def billing_page(request):
    ...
```

#### Pendant für CBV:

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import TemplateView

class DashboardView(LoginRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Einstellungen in `settings.py`:

```python
LOGIN_URL = "login"
LOGIN_REDIRECT_URL = "home"
```

#### Wofür man es nutzt:

1. Schutz privater Seiten (Dashboard, Bestellungen, Profileinstellungen).
2. Basiskontrolle in admin-ähnlichen Bereichen.
3. Verhinderung nicht autorisierter POST-Aktionen.

#### Was `login_required` NICHT macht:

1. Prüft keine Rollen/Permissions (nur Login-Status).
2. Ersetzt keine detaillierte Autorisierungskontrolle.

Für Berechtigungen verwenden:

- `permission_required`
- `user_passes_test`
- `PermissionRequiredMixin`

#### Praktische Tipps:

1. `login_required` standardmäßig auf alle privaten Endpoints setzen.
2. Nicht nur auf versteckte Buttons im Frontend verlassen.
3. Prüfen, dass `next`-Redirect sicher ist (Django behandelt das standardmäßig).

#### Fazit:

`login_required` ist ein grundlegender und notwendiger Schutz für private Views
in Django. Es beantwortet „ist der Benutzer eingeloggt?“, während detaillierte
Zugriffsrechte über zusätzliche Autorisierungsmechanismen aufgebaut werden
müssen.

</details>

<details>
<summary>75. Wie funktionieren Sessions und Cookies?</summary>

#### Django

In Django werden Sessions und Cookies verwendet, um Zustand zwischen Requests zu
speichern, da HTTP selbst stateless ist.

#### Was Cookies sind:

- Kleine Daten, die der Browser clientseitig speichert.
- Werden bei jedem weiteren Request an dieselbe Domain zurückgesendet.
- Enthalten oft nur eine Session-ID, nicht die sensiblen Daten selbst.

#### Was eine Session ist:

- Serverseitiger Speicher für Benutzerdaten (in DB/Cache/Dateien).
- Der Browser hält nur den Session-Key im Cookie.
- Über `request.session` liest/aktualisiert Django Session-Daten.

#### So arbeiten sie zusammen:

1. Nach dem Login erstellt Django eine Session auf dem Server.
2. Der Session-Key wird im Cookie gespeichert (`sessionid`).
3. Bei jedem Request liest Django das Cookie und stellt die Session wieder her.

#### Beispiel mit Session:

```python
def set_theme(request):
    request.session["theme"] = "dark"
    return HttpResponse("ok")

def get_theme(request):
    theme = request.session.get("theme", "light")
    return HttpResponse(theme)
```

#### Beispiel für explizites Cookie:

```python
response = HttpResponse("ok")
response.set_cookie("promo_seen", "1", max_age=3600)
```

#### Wo Sessions in Django gespeichert werden:

- Standard: in der DB (`django.contrib.sessions`).
- Backend kann auf Cache, Datei oder signed cookies umgestellt werden.

#### Wichtige Security-Einstellungen:

1. `SESSION_COOKIE_HTTPONLY = True` (Schutz vor JS-Zugriff auf Cookie).
2. `SESSION_COOKIE_SECURE = True` (nur über HTTPS).
3. `SESSION_COOKIE_SAMESITE = "Lax"` oder `"Strict"` je nach Bedarf.
4. Analog für CSRF-Cookie (`CSRF_COOKIE_SECURE`, `CSRF_COOKIE_HTTPONLY`).

#### Praktische Empfehlungen:

1. Keine sensiblen Daten direkt im Cookie speichern.
2. Umfang der Session-Daten klein halten.
3. Für Skalierung Redis-backed Sessions nutzen.
4. Session bei Logout und kritischen Account-Änderungen bereinigen/invalideren.

#### Fazit:

Cookies sind ein clientseitiger Mechanismus zur Übergabe kleiner Daten, Sessions
sind serverseitige Zustandsspeicherung. In Django arbeiten beide zusammen und
bilden die Basis des klassischen Auth-Flows und personalisierter UX.

</details>

<details>
<summary>76. Was sind Gruppen und Berechtigungen und wie implementiert man ein rollenbasiertes Zugriffsmodell?</summary>

#### Django

In Django sind **Permissions** (Berechtigungen) und **Groups** (Gruppen)
Grundmechanismen der Autorisierung zur Umsetzung von RBAC (Role-Based Access
Control).

#### Was Berechtigungen (permissions) sind:

- Rechte im Format `app_label.codename`, zum Beispiel: `orders.view_order`,
  `orders.change_order`.
- Django erstellt automatisch Basisrechte für Modelle: `add`, `change`,
  `delete`, `view`.
- Eigene Rechte (custom permissions) können in `Meta` ergänzt werden.

#### Was Gruppen (groups) sind:

- Gruppe = Rolle, der ein Set von Permissions zugewiesen ist.
- Ein Benutzer wird der Gruppe hinzugefügt und erhält die Rechte dieser Rolle.

#### Beispiel für custom permission im Modell:

```python
class Order(models.Model):
    ...
    class Meta:
        permissions = [
            ("approve_order", "Can approve order"),
        ]
```

#### Zugriffsprüfung im Code:

```python
if request.user.has_perm("orders.approve_order"):
    ...
```

Decorator:

```python
from django.contrib.auth.decorators import permission_required

@permission_required("orders.approve_order", raise_exception=True)
def approve_view(request, order_id):
    ...
```

#### Beispielrollen (RBAC):

1. **viewer** -> nur `view_*`
2. **manager** -> `view_*`, `change_*`, `approve_order`
3. **admin** -> voller Zugriffsumfang der Domäne

#### Typischer Prozess zur RBAC-Umsetzung:

1. Rollen und Verantwortlichkeiten beschreiben.
2. Mapping „Rolle -> Permissions“ definieren.
3. Gruppen erstellen und Permissions zuweisen.
4. Benutzer zu Gruppen hinzufügen (über Admin oder Seed-Skripte).
5. Permissions in View/CBV/API prüfen.

#### Praktische Empfehlungen:

1. Rechte über Rollen (groups) vergeben, nicht manuell pro Benutzer.
2. Zugriffspolicy zentralisiert und dokumentiert halten.
3. Zugriff im Backend prüfen, auch wenn UI Buttons ausblendet.
4. Für komplexe Fälle object-level permissions ergänzen (falls nötig).

#### Typische Fehler:

1. `is_superuser` vergeben, wo role-based permissions ausreichen.
2. Rollen und Business-Zustände ohne klare Regeln vermischen.
3. „Temporäre“ Rechte ohne Audit und Ablaufdatum vergeben.

#### Fazit:

Gruppen und Berechtigungen in Django sind eine solide Basis für ein
rollenbasiertes Zugriffsmodell. RBAC über Groups macht das System sicherer,
transparenter und leichter wartbar, wenn Team und Produkt skalieren.

</details>

<details>
<summary>77. Wie implementiert man Passwort-Reset?</summary>

#### Django

Passwort-Reset in Django lässt sich am einfachsten über eingebaute Auth-Views
umsetzen: Sie enthalten bereits einen sicheren Flow mit Einmal-Token und
Ablaufprüfung.

#### Standard-Flow:

1. Benutzer gibt E-Mail auf der „Passwort vergessen“-Seite ein.
2. Django sendet eine E-Mail mit Link (uid + token).
3. Benutzer folgt dem Link und setzt ein neues Passwort.
4. Django bestätigt die erfolgreiche Änderung.

#### URL-Einbindung:

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

#### Benötigte Templates:

- `registration/password_reset_form.html`
- `registration/password_reset_done.html`
- `registration/password_reset_confirm.html`
- `registration/password_reset_complete.html`
- E-Mail-Template, z. B. `registration/password_reset_email.html`

#### Grundlegende E-Mail-Einstellungen:

```python
EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "smtp.example.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "..."
EMAIL_HOST_PASSWORD = "..."
DEFAULT_FROM_EMAIL = "noreply@example.com"
```

#### Wichtige Sicherheitsprinzipien:

1. Nicht offenlegen, ob E-Mail im System existiert (Schutz vor User
   Enumeration).
2. HTTPS für Reset-Links verwenden.
3. Reset-Anfragen rate-limiten.
4. Nach Passwortänderung aktive Sessions gemäß Security-Policy invalidieren.
5. Passwort-Reset-Events für Audit loggen.

#### Wann Customizing nötig ist:

- Eigenes Design für E-Mail/Seiten.
- Eigenes User-Modell mit Login via E-Mail.
- Integration mit externem Auth/SSO.

#### Fazit:

Django liefert einen fertigen sicheren Passwort-Reset-Mechanismus über
Standard-Auth-Views. In Production reicht es, E-Mail, Templates, HTTPS und
Anti-Abuse-Schutz korrekt zu konfigurieren.

</details>

<details>
<summary>78. Was ist CSRF und wie funktioniert `{% csrf_token %}`?</summary>

#### Django

**CSRF (Cross-Site Request Forgery)** ist ein Angriff, bei dem eine bösartige
Seite einen authentifizierten Benutzer dazu bringt, in deiner Anwendung eine
unerwünschte Aktion auszuführen (z. B. Passwort ändern oder Zahlung auslösen).

#### Wie Django vor CSRF schützt:

1. Serverseitig wird ein CSRF-Token erzeugt.
2. Das Token wird in das Formular eingebettet (über `{% csrf_token %}`).
3. Bei state-changing Requests (`POST`, `PUT`, `PATCH`, `DELETE`) vergleicht
   Django den Token aus dem Request mit dem erwarteten Token.
4. Wenn Token fehlt/ungültig ist -> `403 Forbidden`.

#### `{% csrf_token %}` im Formular:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Speichern</button>
</form>
```

#### Was dafür nötig ist:

1. `django.middleware.csrf.CsrfViewMiddleware` in `MIDDLEWARE`.
2. `{% csrf_token %}` in allen POST-Formularen.
3. Korrekte Cookie-Policy (besonders in Production mit HTTPS).

#### Für AJAX/fetch-Requests:

- CSRF-Token wird im Header `X-CSRFToken` gesendet.
- Token wird aus Cookie (`csrftoken`) oder HTML gelesen (je nach Ansatz).

#### Typische Fehler:

1. `{% csrf_token %}` im Formular-Template vergessen.
2. `CsrfViewMiddleware` ohne begründeten Grund deaktivieren.
3. Domain-/Secure-Cookie-Parameter falsch konfigurieren.
4. `@csrf_exempt` „für schnell“ einsetzen und Schutz nicht wieder aktivieren.

#### Wann `csrf_exempt` vertretbar ist:

- Nur für spezielle Endpoints (z. B. externe Webhooks), und nur wenn ein anderer
  verlässlicher Request-Validierungsmechanismus existiert (HMAC-Signatur, Token,
  Allowlist).

#### Praktische Empfehlungen:

1. Alle browserbasierten state-changing Formulare müssen `{% csrf_token %}`
   enthalten.
2. Für APIs ohne Cookie-Sessions (Bearer/JWT) ein separates Auth-Modell nutzen.
3. In Production HTTPS + `CSRF_COOKIE_SECURE = True` einsetzen.

#### Fazit:

`{% csrf_token %}` ist ein Schlüsselelement des Django-Schutzes gegen
CSRF-Angriffe in Formularen. Es ist keine Option, sondern ein grundlegender
Sicherheitsstandard für jede Aktion, die den Systemzustand verändert.

</details>

<details>
<summary>79. Wie schützt Django vor XSS, CSRF und SQL Injection?</summary>

#### Django

Django verfolgt einen „secure by default“-Ansatz und hat eingebaute Schutz-
mechanismen gegen die häufigsten Web-Schwachstellen: XSS, CSRF und SQL
Injection.

#### 1. Schutz vor XSS (Cross-Site Scripting)

So funktioniert es:

1. Django-Templates escapen Variablen in `{{ ... }}` automatisch.
2. HTML-Sonderzeichen werden in sichere Darstellung umgewandelt.
3. Potenziell gefährlicher Content wird nicht als Script ausgeführt.

Wichtig:

- `|safe` deaktiviert Escaping, nur für vollständig vertrauenswürdiges HTML
  nutzen.
- Rohes User-Input nicht ohne Sanitizing rendern.

#### 2. Schutz vor CSRF

So funktioniert es:

1. `CsrfViewMiddleware` prüft Token bei state-changing Requests.
2. `{% csrf_token %}` fügt den Token in HTML-Formulare ein.
3. Ohne gültigen Token gibt Django `403` zurück.

#### 3. Schutz vor SQL Injection

So funktioniert es:

1. ORM verwendet parametrisierte Queries.
2. Daten werden getrennt von der SQL-Struktur übergeben.
3. Das blockiert klassische Injection-Angriffe in den meisten Standardfällen.

Risiko entsteht, wenn:

- Raw SQL mit manueller String-Konkatenation geschrieben wird.

#### Zusätzliche eingebaute Django-Schutzmechanismen:

1. `SecurityMiddleware` (Header, SSL-bezogene Policies).
2. `XFrameOptionsMiddleware` (Schutz vor Clickjacking).
3. Sichere Passwort-Hashing-Standards (`PBKDF2` standardmäßig).
4. Host-Header-Prüfung (`ALLOWED_HOSTS`).

#### Praktische Production-Empfehlungen:

1. `DEBUG=False` in Production.
2. HTTPS überall (`SECURE_SSL_REDIRECT`, sichere Cookies).
3. `SESSION_COOKIE_SECURE`, `CSRF_COOKIE_SECURE`, `HTTPONLY` setzen.
4. CSP verwenden (über Header/Pakete).
5. Django und Abhängigkeiten regelmäßig aktualisieren.

#### Typische Entwicklerfehler:

1. Unkontrollierte Nutzung von `|safe`.
2. `@csrf_exempt` ohne alternative Validierung.
3. Raw SQL mit f-string/format.
4. `DEBUG=True` in Production gelassen.

#### Fazit:

Django bietet einen starken Basisschutz gegen XSS, CSRF und SQL Injection.
Sicherheit hängt aber auch von Code-Disziplin ab: korrektes Template-Handling,
ORM-Ansatz, Production-Settings und kontinuierliches Security-Review.

</details>

<details>
<summary>80. Wie schützt Django vor SQL-Injections?</summary>

#### Django

Django schützt vor SQL-Injections vor allem durch ORM und parametrisierte
Abfragen: Benutzerdaten werden als Parameter übergeben, nicht in SQL-Strings
eingebaut.

#### Hauptmechanismus des Schutzes:

1. Du schreibst eine ORM-Abfrage:

```python
User.objects.filter(email=user_input)
```

2. Django generiert SQL mit Placeholder-Parametern.
3. Der Wert `user_input` „bricht“ die SQL-Struktur nicht.

#### Warum das sicher ist:

- ORM trennt SQL-Logik von Daten.
- Das DBMS verarbeitet Parameter als Werte, nicht als Teil des SQL-Befehls.

#### Wo SQL-Injection-Risiko trotzdem möglich bleibt:

1. **Raw SQL mit String-Konkatenation**

```python
# Unsicher
sql = f"SELECT * FROM users WHERE email = '{user_input}'"
```

2. Falsche Nutzung von `.extra()` (Legacy-Ansatz).
3. Dynamisches ORDER BY/Feldnamen ohne Allowlist-Prüfung.

#### Sicheres Raw SQL (wenn wirklich nötig):

```python
from django.db import connection

with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM users WHERE email = %s", [user_input])
    rows = cursor.fetchall()
```

#### Praktische Regeln:

1. Standardmäßig ORM verwenden (`filter/get/exclude/annotate`).
2. Wenn Raw SQL unvermeidbar ist - nur parametrisierte Queries.
3. User-Input niemals via f-string oder `format` in SQL einsetzen.
4. Für dynamische Felder/Sortierung Allowlist nutzen:

- nur vordefinierte Spaltennamen erlauben.

#### Zusätzliche Hardening-Schritte:

1. Minimale Rechte für DB-Benutzer (Least Privilege).
2. Logging verdächtiger Abfragen und Monitoring von Anomalien.
3. Regelmäßige Updates von Django/DB-Treibern.

#### Fazit:

Django ORM schützt „out of the box“ gut vor SQL-Injections. Reale Risiken
beginnen dort, wo Entwickler ORM umgehen und SQL manuell ohne Parametrisierung
und Validierung bauen.

</details>

<details>
<summary>81. Was ist Content Security Policy (CSP) in Django?</summary>

#### Django

**Content Security Policy (CSP)** ist eine HTTP-Sicherheitsrichtlinie, die
festlegt, aus welchen Quellen der Browser Skripte, Styles, Bilder, Fonts usw.
laden darf. Das Hauptziel ist, das Risiko von XSS und Ausführung gefährlicher
Inhalte zu reduzieren.

#### Was CSP macht:

1. Definiert eine Allowlist von Quellen (`self`, CDN, API-Domains).
2. Blockiert unbekannte oder injizierte Ressourcen.
3. Ermöglicht schrittweise Einführung über `Report-Only`.

#### Beispiel für CSP-Header:

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

#### So fügt man CSP in Django hinzu:

Am einfachsten über das Paket `django-csp`:

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

#### Wichtige Praktiken:

1. Mit `Content-Security-Policy-Report-Only` starten, um Verstöße zu sammeln.
2. Nutzung von `'unsafe-inline'` und `'unsafe-eval'` minimieren.
3. Für Inline-Skripte Nonce-/Hash-Ansatz nutzen.
4. Policy schrittweise auf die minimal nötigen Quellen verengen.

#### Typische Probleme bei Einführung:

1. Drittanbieter-Widgets/Analytics brechen bei zu strikten Regeln.
2. Unüberlegte Wildcard-Quellen (`*`) entwerten CSP.
3. Fehlendes Monitoring von CSP-Verstößen nach Release.

#### Fazit:

CSP in Django ist eine wichtige zusätzliche Schutzschicht gegen XSS und
Supply-Chain-Risiken. Bester Ansatz: zuerst `Report-Only`, dann schrittweise
Verschärfung zur strikten Allowlist-Policy.

</details>

<details>
<summary>82. Was sind Custom Management Commands und wann sollte man sie verwenden?</summary>

#### Django

`Custom management commands` sind eigene Django-CLI-Kommandos, die über
`python manage.py <command_name>` gestartet werden. Damit lassen sich operative
und technische Aufgaben als wartbarer Projektcode abbilden.

#### Wofür das nötig ist:

1. Automatisierung von Routineaufgaben (Import/Export, Bereinigung,
   Synchronisierung).
2. Operative Kommandos für DevOps/Support.
3. Skripte für Datenmigrationen/Backfills.
4. Kommandos für CI/CD, Staging und Maintenance-Fenster.

#### Dateistruktur:

```text
my_app/
  management/
    __init__.py
    commands/
      __init__.py
      recalc_stats.py
```

#### Beispielkommando:

```python
from django.core.management.base import BaseCommand
from orders.models import Order

class Command(BaseCommand):
    help = "Berechnet aggregierte Bestellstatistiken neu"

    def add_arguments(self, parser):
        parser.add_argument("--dry-run", action="store_true")

    def handle(self, *args, **options):
        total = Order.objects.count()
        if options["dry_run"]:
            self.stdout.write(self.style.WARNING(f"DRY RUN: orders={total}"))
            return
        # reale Logik
        self.stdout.write(self.style.SUCCESS(f"Done. orders={total}"))
```

Ausführung:

```bash
python manage.py recalc_stats --dry-run
```

#### Wann ein Custom Command die richtige Wahl ist:

1. Aufgabe wiederholt sich und soll reproduzierbar sein.
2. Zugriff auf vollen Django-Kontext wird benötigt (ORM, settings, services).
3. Kontrolliertes Kommando für Team/CI ist erforderlich.

#### Praktische Empfehlungen:

1. `--dry-run` für sichere Vorprüfung anbieten.
2. Operationen nach Möglichkeit idempotent gestalten.
3. Für kritische Batch-Änderungen Transaktionen nutzen.
4. Fortschritt und Ergebnis loggen (`self.stdout`, strukturierte Logs).
5. Für lange Tasks Ausführung über Queue/Worker erwägen.

#### Typische Fehler:

1. Wichtige „one-off“-Skripte außerhalb des Repos halten.
2. Riskante Update/Delete ohne Dry-Run und Backup-Plan starten.
3. Kommando als unlesbaren Monolith ohne Tests schreiben.

#### Fazit:

Custom Management Commands sind ein Standardwerkzeug operativer Reife in Django.
Sie machen technische Prozeduren transparent, kontrollierbar und wiederholbar im
Team-Umfeld.

</details>

<details>
<summary>83. Was sind Context Processors und wie werden sie verwendet?</summary>

#### Django

`Context processors` sind Funktionen, die automatisch Daten in den Kontext jedes
Templates (oder bestimmter Templates) hinzufügen, sodass diese Variablen nicht
in jedem View manuell übergeben werden müssen.

#### So funktioniert ein Context Processor:

1. Django ruft die Funktion beim Template-Rendering auf.
2. Die Funktion gibt ein Dictionary zurück.
3. Dieses Dictionary wird dem Template-Kontext hinzugefügt.

#### Beispiel:

```python
# core/context_processors.py
def app_meta(request):
    return {
        "APP_NAME": "My Django App",
        "SUPPORT_EMAIL": "support@example.com",
    }
```

Einbindung in `settings.py`:

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

Danach in jedem Template:

```django
<footer>{{ APP_NAME }} · {{ SUPPORT_EMAIL }}</footer>
```

#### Wann man sie verwenden sollte:

1. Globale Daten fürs Layout (App-Name, Kontakte, Feature Flags).
2. Daten, die in vielen Templates benötigt werden.
3. Leichte und schnelle Werte ohne teure Berechnungen.

#### Wann eher nicht:

1. Für schwere SQL-Abfragen bei jedem Render.
2. Für sehr spezifische Daten nur eines oder zweier Views.
3. Für komplexe Business-Logik.

#### Nützliche eingebaute Context Processors:

1. `django.template.context_processors.request` (`request` im Template)
2. `django.contrib.auth.context_processors.auth` (`user`, `perms`)
3. `django.contrib.messages.context_processors.messages`
4. `django.template.context_processors.static`
5. `django.template.context_processors.media`

#### Praktische Empfehlungen:

1. Context Processors so leicht wie möglich halten.
2. Schlüsselduplikate vermeiden, die mit lokalem Kontext kollidieren können.
3. Wenn Daten teuer sind - cachen oder gezielt aus dem View übergeben.
4. Globale Kontextschlüssel für das Team dokumentieren.

#### Fazit:

Context Processors sind ein praktischer Mechanismus für allgemeine
Template-Daten. Sie funktionieren gut für leichte globale Werte, sollten aber
kein Ort für schwere Domänenlogik werden.

</details>

<details>
<summary>84. Wie funktioniert Caching in Django? Die wichtigsten Caching-Ansätze.</summary>

#### Django

Caching in Django reduziert teure Operationen (SQL, Template-Rendering,
Berechnungen) und beschleunigt Antworten für Benutzer.

#### So funktioniert es:

1. Daten/Response werden in einem schnellen Storage (Redis/Memcached)
   gespeichert.
2. Ein Folge-Request bekommt das Ergebnis aus dem Cache, ohne vollständige
   Neuberechnung.
3. Nach TTL oder Invalidation wird der Wert neu berechnet.

#### Die wichtigsten Caching-Ansätze in Django:

1. **Site-wide Cache (Middleware)**

- Cached fast die gesamte HTTP-Response von Seiten.
- Gut für öffentlichen Content mit geringer Personalisierung.

2. **Per-view Cache (`cache_page`)**

- Cached einen konkreten View für eine definierte Zeit.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)
def article_list(request):
    ...
```

3. **Template Fragment Cache**

- Cached nur einen Teil des Templates, nicht die ganze Seite.

```django
{% load cache %}
{% cache 300 homepage_sidebar user.id %}
  ...
{% endcache %}
```

4. **Low-level Cache API**

- Manuelles Caching von Ergebnissen im Code.

```python
from django.core.cache import cache

data = cache.get("popular_products")
if data is None:
    data = expensive_query()
    cache.set("popular_products", data, 300)
```

#### Backend-Konfiguration:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Wann welchen Ansatz wählen:

1. Öffentliche Seiten ohne Personalisierung -> per-view/site-wide.
2. Teilweise dynamische Seiten -> Fragment Cache.
3. Teure fachliche Berechnungen/Aggregationen -> Low-level Cache API.

#### Praktische Regeln:

1. Mit gezieltem Cache starten (Fragment/per-view), nicht sofort site-wide.
2. TTL anhand der Anforderungen an Datenaktualität festlegen.
3. Für personalisierte Daten Schlüssel ergänzen (user id, locale, role).
4. Cache-Invalidation nach Datenänderungen einplanen.

#### Typische Fehler:

1. Personalisierten Content ohne User-Key cachen.
2. Cache nach update/delete nicht invalidieren.
3. Zu lange TTL für „lebende“ Daten.
4. Sich auf Cache verlassen statt schlechte SQL-Queries zu optimieren.

#### Fazit:

Caching in Django ist eine mehrstufige Strategie: von Template-Fragmenten bis zu
vollständigen Responses. Das beste Ergebnis liefert die Kombination aus
passendem Backend (meist Redis), moderater TTL und kontrollierter Invalidation.

</details>

<details>
<summary>85. Wie optimiert man Queries, Caching und DB-Indizierung?</summary>

#### Django

Optimierung in Django ist immer ganzheitlich:  
`ORM-Queries` + `Caching` + `korrekte DB-Indizes` + `Profiling`. Ein einzelner
Trick liefert selten ein stabiles Ergebnis.

#### 1. ORM-Query-Optimierung

1. N+1 vermeiden durch:

- `select_related()` für FK/O2O
- `prefetch_related()` für M2M/reverse FK

2. Nur benötigte Felder laden:

- `values()`, `values_list()`, `only()`, `defer()`

3. Für Massenupdates verwenden:

- `update()` + `F()` statt `save()` in Schleifen

4. Für Existenzprüfung:

- `exists()` statt gesamten QuerySet zu laden

#### 2. Caching

1. Mit Fragment-/Per-View-Cache starten.
2. Für „heiße“ Berechnungen die Low-level Cache API nutzen.
3. Für Production meist Redis als Backend.
4. Cache-Keys (user/locale/role) und Invalidation nach Datenänderungen planen.

#### 3. DB-Indizierung

1. Indizes für Felder hinzufügen, die oft in

- `WHERE`
- `ORDER BY`
- `JOIN` verwendet werden.

2. `models.Index` und `UniqueConstraint` in `Meta` nutzen.
3. Nicht „alles“ indizieren: jeder Index kostet bei `INSERT/UPDATE`.

Beispiel:

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

#### 4. Profiling und Messen

1. Django Debug Toolbar auf Dev/Staging nutzen.
2. Langsame SQL-Queries auf DB-Ebene loggen.
3. `EXPLAIN ANALYZE` für kritische Abfragen prüfen.
4. p95/p99-Latenz vor/nach Änderungen messen.

#### Typische Optimierungsreihenfolge:

1. Langsame Stelle finden (nicht „blind“ optimieren).
2. ORM korrigieren (N+1, unnötige Felder, doppelte Queries).
3. Indizes ergänzen/prüfen.
4. Cache für stabil heiße Szenarien ergänzen.
5. Ergebnis erneut messen.

#### Typische Fehler:

1. Alles ohne Invalidation-Strategie cachen.
2. Indizes ohne Analyse realer Queries hinzufügen.
3. Python-Code optimieren und SQL-Engpass ignorieren.
4. Große Schema-Änderungen in Production ohne gestaffeltes Rollout durchführen.

#### Fazit:

Stabile Django-Performance erreicht man nicht mit „einem Knopf“, sondern mit
systematischem Vorgehen: messen, ORM optimieren, DB sauber indizieren und nur
das cachen, was unter Last wirklich messbaren Nutzen bringt.

</details>

<details>
<summary>86. Was ist das Django Testing Framework?</summary>

#### Django

Das `Django testing framework` ist ein eingebautes Toolset zum Testen von
Modellen, Views, Formularen, APIs und Integrationen innerhalb eines
Django-Projekts.

#### Was zum Framework gehört:

1. `django.test.TestCase` - Basisklasse für die meisten Tests.
2. `Client` - HTTP-Testclient für Requests an Views/URLs.
3. Testdatenbank (wird vor dem Lauf automatisch erstellt).
4. Assertions für Response, Kontext, Redirects, Templates.
5. Werkzeuge für Settings-Overrides und Umgebungsisolation.

#### Wie Tests gestartet werden:

```bash
python manage.py test
```

#### Wie die Test-DB funktioniert:

1. Django erstellt eine separate Test-DB.
2. Spielt Migrationen/Schema ein.
3. Jeder Test wird transaktional isoliert (`TestCase`).
4. Nach Abschluss wird die Test-DB entfernt.

#### Haupt-Testklassen:

1. **`TestCase`**

- Häufigste Wahl; schnell und isoliert für ORM/View-Tests.

2. **`TransactionTestCase`**

- Wenn Kontrolle über Transaktionen/Commit-Verhalten benötigt wird.

3. **`SimpleTestCase`**

- Tests ohne DB-Zugriff.

4. **`LiveServerTestCase`**

- Integrations-/Browser-Tests mit laufendem Testserver.

#### Beispiel für einen einfachen Test:

```python
from django.test import TestCase
from django.urls import reverse

class HealthViewTests(TestCase):
    def test_health_endpoint_returns_200(self):
        response = self.client.get(reverse("health"))
        self.assertEqual(response.status_code, 200)
```

#### Praktische Empfehlungen:

1. Tests für kritische Business-Szenarien schreiben, nicht nur „für Coverage“.
2. Tests deterministisch halten (keine Zeit-/Netz-Abhängigkeit ohne Mock).
3. Fabriken/Fixtures für lesbare Datenvorbereitung nutzen.
4. Tests in CI bei jedem PR ausführen.

#### Typische Fehler:

1. Tests mit Abhängigkeit von Ausführungsreihenfolge.
2. Zu viele Integrations-Tests, wo Unit-Level ausreicht.
3. Edge Cases und Negativszenarien ignorieren.

#### Fazit:

Das Django Testing Framework liefert „out of the box“ eine fertige Infrastruktur
für zuverlässige Backend-Tests. Es ist die Basis für sicheres Refactoring und
einen stabilen Release-Prozess in Team-Entwicklung.

</details>

<details>
<summary>87. Worin unterscheiden sich Unit- und Integrationstests?</summary>

#### Django

`Unit`- und `Integration`-Tests unterscheiden sich im Prüfungsniveau:

- **Unit-Test** prüft isolierte Logik.
- **Integrationstest** prüft das Zusammenspiel mehrerer Komponenten.

#### Unit-Tests:

1. Testen eine Funktion/Methode/Klasse isoliert vom Rest des Systems.
2. Verwenden oft Mock/Stub für Abhängigkeiten.
3. Sehr schnell, Fehlerursache lässt sich präzise lokalisieren.

Beispiel in Django:

- Test eines Validators,
- Test einer Helper-Funktion,
- Test einer Service-Methode ohne echtes HTTP/DB (oder mit minimaler Isolation).

#### Integrationstests:

1. Prüfen mehrere Schichten gemeinsam (View + ORM + Middleware + Templates).
2. Verwenden häufig Test Client und Testdatenbank.
3. Langsamer, aber näher am realen Verhalten.

Beispiel in Django:

- `client.post(...)` -> view -> model save -> redirect -> DB-Checks.

#### Zentrale Unterschiede:

1. **Geschwindigkeit**

- Unit: schnell.
- Integration: langsamer.

2. **Abdeckungsumfang**

- Unit: enger Fokus.
- Integration: breiter Systemszenario-Fokus.

3. **Diagnose**

- Unit: konkrete Ursache leichter zu finden.
- Integration: erkennt besser Probleme im Zusammenspiel von Komponenten.

#### Beispiel für Test-Pyramide in Django:

1. Viele Unit-Tests (Validatoren, Services, Utilities).
2. Weniger Integrationstests (Schlüssel-Endpoints, kritische Business-Flows).
3. Noch weniger End-to-End-/Browser-Tests.

#### Praktische Empfehlungen:

1. Kritische Domänenlogik gut mit Unit-Tests abdecken.
2. Für Core User Journeys verpflichtend Integrationstests ergänzen.
3. Nicht alles nur mit Integrationstests abdecken - das ist langsam und fragil.
4. Jeder Production-Bug sollte mit einem neuen Test passender Ebene enden.

#### Fazit:

Unit- und Integrationstests ersetzen sich nicht. Ein stabiles Django-Projekt
braucht beides: Unit-Tests für schnelles Feedback und Integrationstests zur
Prüfung des realen Zusammenspiels der Komponenten.

</details>

<details>
<summary>88. Was ist der Django Test Client?</summary>

#### Django

Der `Django test client` ist ein eingebautes Werkzeug zur Simulation von
HTTP-Requests an deine Anwendung, ohne echten Browser oder externen HTTP-Server
zu starten.

#### Was der Test Client kann:

1. `GET`, `POST`, `PUT`, `PATCH`, `DELETE` Requests ausführen.
2. Status-Code, Redirects, Templates und Kontext prüfen.
3. Mit Session, Cookies und User-Authentifizierung arbeiten.
4. Die Kette URL -> View -> Response testen.

#### Basisbeispiel:

```python
from django.test import TestCase
from django.urls import reverse

class HomeTests(TestCase):
    def test_home_returns_200(self):
        response = self.client.get(reverse("home"))
        self.assertEqual(response.status_code, 200)
```

#### Beispiel für POST-Request:

```python
response = self.client.post(reverse("signup"), {
    "username": "testuser",
    "password1": "StrongPass123!",
    "password2": "StrongPass123!",
})
self.assertEqual(response.status_code, 302)
```

#### Login in Tests:

1. Schneller technischer Login:

```python
self.client.force_login(user)
```

2. Realistischer Login über Credentials:

```python
logged_in = self.client.login(username="testuser", password="secret")
self.assertTrue(logged_in)
```

#### Was man prüfen kann:

1. `response.status_code`
2. `response.context`
3. `response.templates`
4. `assertRedirects(...)`
5. Response-Inhalt (`assertContains(...)`)

#### Grenzen des Test Clients:

1. Führt kein JavaScript aus (keine Browser-Automation).
2. Prüft kein echtes Frontend-Runtime wie Playwright/Selenium.
3. Modelliert nicht alle Netzwerkdetails einer Production-Umgebung.

#### Praktische Empfehlungen:

1. Test Client für die meisten Django-Web/API-Integrationstests verwenden.
2. Für JS-Flows separate E2E-/Browser-Tests ergänzen.
3. Mit Fabriken/Fixtures kombinieren für lesbare Testdatenvorbereitung.

#### Fazit:

Der Django Test Client ist ein schnelles und starkes Werkzeug für Prüfung des
HTTP-Verhaltens auf Backend-Ebene. Er ist die Standardwahl für Tests von Views,
URLs, Authentifizierung und grundlegender Komponentenintegration.

</details>

<details>
<summary>89. Wie testet man Formulare, Views und ORM?</summary>

#### Django

In Django testet man Formulare, Views und ORM auf unterschiedlichen Ebenen, aber
im selben Muster: klare Preconditions -> Aktion -> Ergebnisprüfung.

#### 1. Formulartests

Was prüfen:

1. valide/ungültige Daten
2. Fehler auf konkreten Feldern
3. benutzerdefinierte Validierung (`clean_<field>`, `clean()`)

Beispiel:

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

#### 2. View-Tests

Was prüfen:

1. Status-Code
2. Template/Kontext
3. Redirects
4. Auth-/Permission-Verhalten

Beispiel:

```python
from django.test import TestCase
from django.urls import reverse

class DashboardViewTests(TestCase):
    def test_anonymous_redirected_to_login(self):
        response = self.client.get(reverse("dashboard"))
        self.assertEqual(response.status_code, 302)
```

#### 3. ORM-Tests

Was prüfen:

1. Erstellen/Aktualisieren/Löschen von Modellen
2. Custom Manager/QuerySet-Methoden
3. Beziehungen und Constraints (`unique`, `constraints`)

Beispiel:

```python
from django.test import TestCase
from blog.models import Article

class ArticleORMTests(TestCase):
    def test_create_article(self):
        article = Article.objects.create(title="Test", is_published=True)
        self.assertEqual(Article.objects.count(), 1)
        self.assertTrue(article.is_published)
```

#### Praktische Empfehlungen:

1. Tests voneinander unabhängig halten.
2. Tests beschreibend benennen, z. B. nach Muster `should_<behavior>`.
3. Für Testdaten factories/fixtures nutzen statt Setup-Duplikate.
4. Negativszenarien genauso sorgfältig testen wie Positivszenarien.

#### Was oft vergessen wird:

1. Permission-Prüfungen auf View-Ebene.
2. Formularvalidierung mit unerwarteten Eingabedaten.
3. Verhalten von Manager/QuerySet-Methoden bei leeren Ergebnissen.

#### Fazit:

Formulare testen Validierung, Views das HTTP-Verhalten, ORM Daten und
Beziehungen. Zusammen ergibt das ein robustes Testfundament, das sicheres
Refactoring und stabile Releases in Django ermöglicht.

</details>

<details>
<summary>90. Wie verwendet man Fixtures?</summary>

#### Django

`Fixtures` in Django sind vorab vorbereitete Daten (JSON/YAML/XML), die in die
DB geladen werden können - für Tests, Demos oder initiales Seeding.

#### Wofür Fixtures verwendet werden:

1. Standarddatenset schnell bereitstellen.
2. Reproduzierbaren Testzustand in verschiedenen Umgebungen erzeugen.
3. Szenarien mit „realistischen“ verknüpften Datensätzen testen.

#### Beispiel einer Fixture-Datei:

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

Ablage:

- `app/fixtures/articles.json` (typische Variante)

#### Fixture laden:

```bash
python manage.py loaddata articles.json
```

#### Verwendung in Tests:

```python
from django.test import TestCase
from blog.models import Article

class ArticleTests(TestCase):
    fixtures = ["articles.json"]

    def test_fixture_loaded(self):
        self.assertEqual(Article.objects.count(), 1)
```

#### Wann Fixtures sinnvoll sind:

1. Kleine stabile Referenzdatensets.
2. Integrationstests mit komplexen Beziehungen.
3. Demo/lokale Befüllung für Review-Umgebungen.

#### Einschränkungen von Fixtures:

1. Fragil bei Änderungen des Modellschemas.
2. Große JSON-Dateien sind schwerer lesbar und wartbar.
3. Weniger flexibel kombinierbar für unterschiedliche Tests.

#### Praktische Alternative:

- Für die meisten Tests sind Factories besser (factory_boy, model_bakery), weil:

1. Daten programmatisch erstellt werden.
2. Anpassung an Modelländerungen leichter ist.
3. Es weniger „magische“ statische Dateien gibt.

#### Empfohlener Tech-Lead-Ansatz:

1. Kleine gemeinsame Datensätze -> Fixtures.
2. Mehrheit der Unit-/Integrationstests -> Factories.
3. Beide Ansätze nicht chaotisch ohne klare Teamregeln mischen.

#### Fazit:

Fixtures in Django sind nützlich für stabile Startdatensätze, aber für flexible
und langfristige Testdatensets sind Factory-Ansätze meist effizienter.

</details>

<details>
<summary>91. Wie funktionieren Async Views und Async ORM in Django?</summary>

#### Django

Django unterstützt asynchrone Views (`async def`) und entwickelt den Async-Stack
schrittweise für I/O-lastige Szenarien weiter. Der Hauptwert von Async ist
bessere Skalierbarkeit bei vielen gleichzeitigen Warteoperationen (externe APIs,
Netzwerk-I/O).

#### Async View in Django:

```python
from django.http import JsonResponse

async def async_health(request):
    return JsonResponse({"status": "ok"})
```

#### Wann Async wirklich nützlich ist:

1. Viele I/O-Wartezeiten (HTTP-Requests an Fremdservices).
2. Long-Polling/WebSocket-Patterns (mit passendem Stack).
3. Hohe Request-Konkurrenz bei relativ leichter CPU-Logik.

#### Sync vs Async in Django:

1. `def view(...)` -> synchroner View.
2. `async def view(...)` -> asynchroner View.
3. Django kann Sync/Async-Grenzen adaptieren, aber unnötige Übergänge haben
   Overhead.

#### Arbeit mit DB (ORM):

- Historisch war ORM sync-first.
- In modernen Django-Versionen gibt es Async-Varianten für einen Teil der
  Operationen (`aget`, `acreate`, `aupdate_or_create`, Async-Iteration usw.),
  aber man muss Version- und DB-Treiber-Kompatibilität beachten.

Beispiel:

```python
user = await User.objects.aget(pk=user_id)
```

#### Wichtige Einschränkungen:

1. Nicht alle Drittanbieter-Bibliotheken sind async-safe.
2. CPU-bound Aufgaben werden durch Async nicht schneller (dafür
   Worker/Queues/Prozesse).
3. Sync-ORM in Async-Code kann die Event-Loop blockieren.

#### Praktische Empfehlungen:

1. Async dort einsetzen, wo ein echter I/O-Bottleneck besteht.
2. Wenn der Stack überwiegend sync ist - Async nicht „der Mode wegen“ erzwingen.
3. Sync<->Async-Übergänge minimieren.
4. Für Hintergrund-CPU-/Long-Processing Celery/RQ nutzen, nicht `await` im View.

#### Typische Fehler:

1. Performance-Gewinn erwarten ohne Änderung des I/O-Profils.
2. Blockierende Sync-Calls innerhalb eines Async-Views ausführen.
3. Verhalten unter konkurrierender Last nicht testen.

#### Fazit:

Async in Django ist ein starkes Werkzeug für I/O-heavy Szenarien, aber keine
universelle Lösung. Die Wirksamkeit hängt von der Konsistenz des gesamten Stacks
ab: View, ORM, externe Clients und reales Lastprofil.

</details>

<details>
<summary>92. Wie erstellt man Backend-Tasks (@task, Celery)?</summary>

#### Django

Backend-Tasks (Background Jobs) in Django nutzt man für schwere oder verzögerte
Operationen, die nicht direkt im HTTP-Request laufen sollten: E-Mail-Versand,
Importe, Dateigenerierung, Integrationen, Retries.

#### Häufigster Stack:

- **Celery** + Broker (meist Redis oder RabbitMQ) + Worker

#### Basisarchitektur:

1. Django-Code stellt eine Aufgabe in die Queue.
2. Der Broker speichert die Nachricht.
3. Ein Celery-Worker holt die Aufgabe und führt sie asynchron aus.
4. (Optional) das Ergebnis wird im Result-Backend gespeichert.

#### Beispiel einer Task:

```python
# app/tasks.py
from celery import shared_task

@shared_task
def send_welcome_email(user_id):
    # E-Mail-Logik
    return {"user_id": user_id, "status": "sent"}
```

Aufruf aus View/Service:

```python
send_welcome_email.delay(user.id)
```

#### Minimale Celery-Integration in Django:

1. Installieren:

```bash
pip install celery redis
```

2. `celery.py` in die Projektkonfiguration hinzufügen.
3. Broker-URL in settings/env setzen.
4. Worker starten:

```bash
celery -A config worker -l info
```

#### Periodische Tasks:

- Über `celery beat` oder `django-celery-beat` (cron-ähnlicher Scheduler).

#### Praktische Empfehlungen:

1. Tasks sollten **idempotent** sein (erneuter Lauf darf Daten nicht zerstören).
2. `retry` für temporäre Fehler ergänzen (Netzwerk, externe APIs).
3. Keine „schweren“ Objekte in Tasks übergeben - IDs übergeben, Daten im Worker
   laden.
4. Ausführungsstatus und Fehler loggen.
5. Timeouts und Worker-Concurrency-Limits definieren.

#### Typische Fehler:

1. Lange Operationen direkt im View statt in der Queue ausführen.
2. Fehlende Retry-Policy bei Integrationen mit externen Services.
3. Unerwartete Task-Duplikate durch nicht-idempotente Logik.
4. Kein Monitoring für Queues und „hängende“ Tasks.

#### Fazit:

Celery in Django ist der Standard für asynchrone Backend-Verarbeitung. Schlüssel
zur Zuverlässigkeit: Idempotenz, Retries, Monitoring und klare Trennung von
HTTP-Flow und Hintergrundverarbeitung.

</details>

<details>
<summary>93. Was ist Django REST Framework?</summary>

#### Django

**Django REST Framework (DRF)** ist ein verbreitetes Framework auf Django-Basis
für den Bau von REST-APIs: Datenserialisierung, Validierung, Autorisierung,
Routing, Pagination und eine praktische browsable API-Oberfläche.

#### Warum DRF verwendet wird:

1. Schneller Aufbau stabiler APIs für Web-/Mobile-Clients.
2. Standardisierte Validierung und Response-Format.
3. Flexible Steuerung von Auth/Permissions/Throttling.
4. Weniger Boilerplate als bei „reinen“ JsonResponse-Views.

#### Schlüsselkomponenten von DRF:

1. **Serializer**

- Wandelt Modell/Objekt <-> JSON.
- Führt Validierung eingehender Daten aus.

2. **APIView / GenericAPIView / ViewSet**

- Schichten zum Aufbau von Endpoint-Logik.

3. **Routers**

- Automatische URL-Generierung für ViewSets.

4. **Authentication / Permissions**

- Kontrolle, wer du bist und was du darfst.

5. **Pagination / Filtering / Ordering**

- Fertige Mechanismen für Listen und Suche.

#### Beispiel Serializer:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Beispiel ViewSet:

```python
from rest_framework.viewsets import ModelViewSet
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
```

#### Beispiel Router:

```python
from rest_framework.routers import DefaultRouter
from .views import ArticleViewSet

router = DefaultRouter()
router.register("articles", ArticleViewSet, basename="article")
urlpatterns = router.urls
```

#### Wann DRF besonders sinnvoll ist:

1. API-first oder Multi-Client-Produkt wird benötigt.
2. Es gibt komplexe Anforderungen an Permissions/Pagination/Filtering.
3. Skalierbare API-Architektur und standardisiertes Error-Format sind nötig.

#### Fazit:

DRF ist der De-facto-Standard für APIs im Django-Ökosystem. Es liefert eine
strukturierte API-Architektur, beschleunigt Entwicklung und vereinfacht die
Wartung von Production-Endpoints.

</details>

<details>
<summary>94. Was ist Serialisierung und wofür wird sie gebraucht?</summary>

#### Django

Serialisierung ist die Umwandlung von Python-Objekten/Modellen in ein
Datenübertragungsformat (meist JSON), und Deserialisierung ist die
Rückumwandlung in Objekte mit Validierung.

#### Warum Serialisierung nötig ist:

1. Daten zwischen Backend und Frontend/Mobile-Clients übertragen.
2. API-Response-Format standardisieren.
3. Eingabedaten vor dem Schreiben in die DB validieren.
4. DB-Modell vom externen API-Vertrag entkoppeln.

#### Serialisierung in DRF:

- Erfolgt über `Serializer` oder `ModelSerializer`.

Beispiel:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Umwandlung model -> JSON:

```python
article = Article.objects.first()
data = ArticleSerializer(article).data
```

#### Umwandlung JSON -> validierte Daten/Modell:

```python
payload = {"title": "New", "is_published": True}
serializer = ArticleSerializer(data=payload)
serializer.is_valid(raise_exception=True)
obj = serializer.save()
```

#### Was der Serializer zusätzlich liefert:

1. Prüfung von Typen und Pflichtfeldern.
2. Custom Validierung (`validate_<field>`, `validate`).
3. Kontrolle über read-only/write-only Felder.
4. Verschachtelte Serializer für verknüpfte Entitäten.

#### Praktische Empfehlungen:

1. Modell nicht „as is“ ohne expliziten Serializer-Vertrag ausliefern.
2. API-Schema stabil und backward-kompatibel halten.
3. Custom-Businessregeln im Serializer oder in der Service-Schicht validieren.
4. Für verschiedene Use-Cases getrennte Serializer nutzen
   (list/detail/create/update).

#### Fazit:

Serialisierung ist der Kern der API-Schicht in Django/DRF: Sie ist zuständig für
Datenformat, Validierung und Vertragsstabilität zwischen Server und Clients.

</details>

<details>
<summary>95. Welche Besonderheiten hat Django mit dem REST-Framework (DRF)?</summary>

#### Django

Django + DRF ist die Kombination aus einem reifen Web-Framework und einer
starken API-Schicht. Sie eignet sich sehr gut für produktive REST-Services mit
klarer Domänenmodellierung.

#### Zentrale Besonderheiten von DRF im Django-Ökosystem:

1. **Serializer-first-Ansatz**

- Klarer API-Vertrag, Validierung eingehender Daten, Feldkontrolle.

2. **Flexible Endpoint-Erstellung**

- `APIView`, `GenericAPIView`, `ViewSet`, `ModelViewSet`.

3. **Automatisches Routing**

- Router reduzieren Boilerplate bei CRUD-APIs deutlich.

4. **Auth + Permissions**

- Session, Token, JWT (über Pakete), benutzerdefinierte Permission-Klassen.

5. **Pagination, Filtering, Ordering**

- Fertige Mechanismen für Listen in großen Systemen.

6. **Throttling**

- Begrenzung der Request-Frequenz (Anti-Abuse / API-Hygiene).

7. **Content Negotiation**

- Unterstützung verschiedener Renderer/Parser (standardmäßig JSON).

8. **Browsable API**

- Praktisches Dev-Interface für manuelle Endpoint-Prüfung.

#### Typischer Production-Stack mit DRF:

1. Versionierte API (`/api/v1/...`).
2. Serializer je nach Use Case (`list/detail/create/update`).
3. Permission-Policy pro Endpoint.
4. Standardisiertes Error-Format.
5. Pagination + Filtering + DB-Indizierung.

#### Stärken des Ansatzes:

1. Hohe Entwicklungsgeschwindigkeit ohne Strukturverlust.
2. Kompatibel mit Django auth/admin/ORM/migrations.
3. Leicht per Custom-Klassen an Business-Anforderungen erweiterbar.

#### Worauf man achten sollte:

1. `ModelViewSet` nicht mit komplexer Domänenlogik überladen.
2. N+1-Queries in Serializer/ViewSet kontrollieren.
3. API-Vertrag klar von internem Datenmodell trennen.

#### Fazit:

DRF macht Django zu einem starken API-Framework auf Enterprise-Niveau: schneller
Start, strukturierte Architektur, reife Sicherheit und Skalierbarkeit für echte
Multi-Client-Produkte.

</details>

<details>
<summary>96. Welche Rolle spielt Django in der Architektur von Services und REST APIs?</summary>

#### Django

Django nimmt in moderner Architektur meist die Rolle des **zentralen
Business-Backends** ein: Es steuert Domänenlogik, transaktionale Daten,
Admin-Prozesse und REST APIs für Web-/Mobile-Clients.

#### Typische Django-Rollen in der Architektur:

1. **Modularer Monolith (am häufigsten)**

- Ein Service mit klarer Dekomposition in Apps/Domänen.
- Schnelle Produktentwicklung und einfacherer operativer Betrieb.

2. **API-Service (DRF)**

- Reines Backend für SPA/Mobile/Partner-Integrationen.

3. **Core-Service in einer Microservice-Landschaft**

- Django als „Source of Truth“ für kritische Domänen (User, Billing, Orders).

4. **Backoffice/Admin-Service**

- Interner Betriebsbereich über Django Admin + Custom UI.

#### Warum Django dafür gut geeignet ist:

1. Schnelle Entwicklung des kompletten Backend-Zyklus.
2. Starker ORM + transaktionales Modell.
3. Reifes Auth-/Permissions-System.
4. DRF für standardisierte APIs.
5. Zuverlässiger Admin für operative Teams.

#### Wo Django nicht immer die erste Wahl ist:

1. Ultra-leichte High-Concurrency API-only Services (teils ist FastAPI
   passender).
2. Spezifische Low-Latency-Szenarien mit minimalem Framework-Overhead.

#### Praktischer Architekturansatz:

1. Mit Django-Monolith starten, aber mit klaren Domänengrenzen.
2. Separate Services nur bei realem Skalierungsbedarf ausgliedern.
3. Django als Core Domain/API/Admin-Knoten beibehalten.

#### Integration mit anderen Services:

- Celery/Queues für Async Processing
- Redis für Caching
- Search Engine für Full-Text
- Object Storage/CDN für Media
- Observability Stack (Logs, Metrics, Tracing)

#### Fazit:

Django hat eine starke Position als Backbone für Business-Services und REST
APIs. In den meisten Produkten ist es ein praktikabler Kompromiss zwischen
Entwicklungsgeschwindigkeit, Architekturdisziplin und langfristiger Wartbarkeit.

</details>

<details>
<summary>97. Wie deployt man ein Django-Projekt (WSGI, ASGI, Nginx)?</summary>

#### Django

Ein Django-Deployment in Production wird typischerweise so aufgebaut:

1. **Nginx** - Reverse Proxy, Static/Media, TLS.
2. **App-Server** - Gunicorn (WSGI) oder Uvicorn/Daphne (ASGI).
3. **Django App** - Business-Logik.
4. **PostgreSQL/Redis** - Daten und Cache/Queues.

#### WSGI vs ASGI:

1. **WSGI (Gunicorn)**

- Klassische stabile Variante für synchrone Django-Anwendungen.

2. **ASGI (Uvicorn/Daphne)**

- Nötig für Async Views, WebSockets und moderne Async-Szenarien.

#### Minimaler Production-Flow:

1. Umgebung vorbereiten:

- `DEBUG=False`
- `ALLOWED_HOSTS`
- Secrets über Env

2. Abhängigkeiten installieren:

```bash
pip install gunicorn
```

3. Static sammeln:

```bash
python manage.py collectstatic --noinput
```

4. Migrationen anwenden:

```bash
python manage.py migrate
```

5. App-Server starten:

```bash
gunicorn config.wsgi:application --bind 127.0.0.1:8000 --workers 4
```

#### Beispiel Nginx (vereinfacht):

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

#### Für ASGI-Deployment:

```bash
uvicorn config.asgi:application --host 127.0.0.1 --port 8000 --workers 4
```

#### Obligatorische Security/Ops-Checkliste:

1. HTTPS (Let’s Encrypt), sichere Cookies.
2. `CSRF_TRUSTED_ORIGINS` und korrekte Proxy-Header.
3. `SECURE_HSTS_SECONDS`, `SECURE_SSL_REDIRECT`, `X_FRAME_OPTIONS`.
4. Logs, Monitoring, Alerts (Error Rate, Latenz, DB Health).
5. Backup und getesteter Rollback-Plan.

#### Typische Fehler:

1. `DEBUG=True` in Production.
2. Fehlendes `collectstatic` vor Release.
3. Falsche `ALLOWED_HOSTS` / Proxy-Header -> CSRF/Redirect-Probleme.
4. Django Development Server (`runserver`) in Production verwenden.

#### Fazit:

Ein stabiles Django-Deployment ist die Kombination aus Nginx + WSGI/ASGI
App-Server + korrekten Production-Security- und Observability-Einstellungen.
Technisch nicht schwer, wenn der Release-Prozess diszipliniert ist.

</details>

<details>
<summary>98. Wie skaliert man eine Django-Anwendung?</summary>

#### Django

Django-Skalierung ist kein Einzelschritt, sondern eine Folge von Entscheidungen
auf Code-, DB-, Cache-, Queue- und Infrastruktur-Ebene. Die beste Strategie:
nach Metriken skalieren, nicht „auf Vorrat“.

#### 1. App-Optimierung (erste Phase)

1. N+1-Queries entfernen (`select_related`, `prefetch_related`).
2. Schwere Endpoints optimieren (Pagination, Limits, Indizes).
3. API/HTML-Payload minimieren.
4. Caching ergänzen, wo wiederkehrende „heiße“ Requests auftreten.

#### 2. Caching und Read-Beschleunigung

1. Redis für low-level/per-view/fragment cache.
2. CDN für static/media.
3. HTTP-Cache-Header für öffentliche Ressourcen.

#### 3. Horizontale Skalierung auf App-Ebene

1. Mehrere Django-Instanzen hinter einem Load Balancer.
2. Stateless App-Prozesse (Sessions in Redis/DB, kein lokaler Zustand).
3. Autoscaling nach CPU/RPS/Latenz.

#### 4. Schwere Aufgaben in den Hintergrund verlagern

1. Celery/RQ für asynchrone Jobs.
2. Queues für E-Mails, Reports, Integrationen, Importe.
3. Retry/Backoff und Idempotenz für Zuverlässigkeit.

#### 5. DB-Skalierung

1. Indizes und Query-Tuning.
2. Connection Pooling (PgBouncer).
3. Read Replicas für read-heavy Szenarien.
4. Partitioning/Sharding nur bei realem Bedarf und klarer Architektur.

#### 6. Architektur-Evolution

1. Von „Monolith ohne Grenzen“ -> modularer Monolith.
2. Bei Bedarf enge Domänen in eigene Services auslagern.
3. Microservices nicht zu früh einführen.

#### 7. Observability als Skalierungsvoraussetzung

1. Metriken: p95/p99-Latenz, Error Rate, Queue Lag, DB Locks.
2. Logs mit Request-ID.
3. Tracing über Services/Queues hinweg.
4. Alerts bei SLA/SLO-Verletzungen.

#### Typische Fehler:

1. Infrastruktur skalieren, ohne Queries zu optimieren.
2. Cachen ohne Invalidation-Strategie.
3. DB-Engpässe ignorieren.
4. Vorzeitige Microservice-Komplexität.

#### Fazit:

Django-Skalierung ist ein kontrollierter Prozess: zuerst Code und DB optimieren,
dann Cache und Queues ergänzen, danach App-Instanzen horizontal skalieren und
erst anschließend Architektur komplexer machen. Metriken sollten alle
Entscheidungen steuern.

</details>

<details>
<summary>99. Welche Ansätze gibt es für Deployment und Monitoring einer Django-Anwendung?</summary>

#### Django

Zuverlässige Django-Production steht auf zwei Säulen:

1. **kontrolliertes Deployment**
2. **vollständiges Monitoring (Observability)**

#### Deployment-Ansätze:

1. **Klassisches VM/VPS-Deployment**

- Nginx + Gunicorn/Uvicorn + systemd + PostgreSQL/Redis.
- Geeignet für kontrollierte self-hosted Umgebungen.

2. **Container-basiert (Docker/Kubernetes)**

- Vorhersehbare Umgebung, Skalierung über Replikate.
- Praktisch für Teams mit DevOps-Prozessen.

3. **PaaS/Managed-Plattformen**

- Schnellere Inbetriebnahme, weniger operativer Aufwand.
- Kompromiss bei Infrastruktur-Flexibilität.

#### Empfohlene Release-Pipeline:

1. CI: Tests + Linter + Security-Checks.
2. Immutable Artifact (Image) bauen.
3. Deployment auf Staging.
4. Smoke-/Health-Checks.
5. Production-Rollout (blue/green, rolling oder canary).
6. Automatischer Rollback bei Degradation.

#### Was zwingend zu monitoren ist:

1. **Application Metrics**

- RPS, p95/p99-Latenz, 4xx/5xx-Error-Rate.

2. **Infrastructure Metrics**

- CPU, RAM, Disk, Netzwerk, Pod-/Container-Restart-Rate.

3. **Database Metrics**

- Slow Queries, Locks, Connections, Replication Lag.

4. **Queue/Worker Metrics**

- Queue Depth, Task-Latenz, Retry-/Failure-Rate.

5. **Logs + Tracing**

- Strukturierte Logs, Request-ID, Distributed Tracing.

#### Minimales Production-Set:

1. Health Endpoints (`/health/live`, `/health/ready`).
2. Zentrale Logs (ELK/Loki/Cloud Logs).
3. APM/Metrics (Prometheus + Grafana, Datadog, New Relic, Sentry).
4. Alerts auf SLO-Verletzungen, nicht nur auf „Server down“.

#### Praktische Empfehlungen:

1. Runbook für Incidents einführen (wer, was, wie wiederherstellt).
2. Migrationen backward-kompatibel halten für zero/min-downtime Releases.
3. Secrets und Konfiguration über env/secret manager automatisieren.
4. Rollback und Disaster Recovery regelmäßig üben.

#### Typische Fehler:

1. Deployment ohne Health Checks und Rollback-Strategie.
2. Monitoring nur von CPU ohne Business-Metriken und Latenz.
3. Kein Zusammenhang zwischen Logs und konkreter Request-/Trace-ID.
4. Manuelle „Hotfixes“ auf Servern ohne Reproduktion im Code.

#### Fazit:

Erfolgreiches Django-Deployment ist ein vorhersehbarer CI/CD-Prozess, stabiler
Betrieb bedeutet Monitoring mit frühem Degradationssignal. Ohne Observability
verliert selbst guter Code in Production schnell an Steuerbarkeit.

</details>

<details>
<summary>100. Welche Änderungen enthalten Patch-Releases typischerweise und warum ist es wichtig, zu aktualisieren?</summary>

#### Django

Patch-Releases (z. B. `5.1.2 -> 5.1.3`) enthalten typischerweise **rückwärts-
kompatible** Fixes ohne API-Änderungen, die Anwendungen auf Major/Minor-Ebene
brechen.

#### Was ein Patch-Release typischerweise enthält:

1. **Security Fixes**

- Schließt Sicherheitslücken (oft kritisch für Production).

2. **Bug Fixes**

- Fehlerbehebungen in ORM, Forms, Middleware, Admin, Migrationen usw.

3. **Stability Improvements**

- Bessere Kompatibilität mit Abhängigkeiten, Edge-Case-Fixes.

4. **Kleinere Docs-/Test-Verbesserungen**

- Ohne Änderungen am architektonischen Vertragsverhalten der Anwendung.

#### Warum Updates wichtig sind:

1. **Sicherheit**

- Ein verpasster Security-Patch kann bekannte Schwachstellen in Production
  offenlassen.

2. **Zuverlässigkeit**

- Patch-Releases beheben Bugs, die unter Last sichtbar werden können.

3. **Kompatibilität**

- Aktuelle Bibliotheken erwarten oft aktuelle Patch-Versionen des Frameworks.

4. **Einfacherer Upgrade-Pfad**

- Regelmäßige kleine Updates sind leichter als seltene „große Sprünge“.

#### Praktischer Update-Prozess:

1. Abhängigkeit aktualisieren (`pip`/`poetry`/`uv`).
2. Tests und Linter ausführen.
3. Changelog/Release Notes prüfen.
4. Auf Staging ausrollen.
5. Kontrollierter Rollout in Production.

#### Frequenz:

- Patch-Updates regelmäßig prüfen (mindestens monatlich oder nach Security
  Advisory).
- Bei LTS-Versionen Security-Patches möglichst schnell einspielen.

#### Typische Fehler:

1. Patch-Updates aufschieben.
2. In Production ohne Staging-/CI-Prüfung aktualisieren.
3. Release Notes und mögliche Side Effects ignorieren.

#### Fazit:

Patch-Releases sind keine „Kosmetik“, sondern operative Hygiene im Projekt.
Regelmäßige Django-Updates senken Security-Risiken, erhöhen Stabilität und
machen zukünftige Upgrades planbarer.

</details>
