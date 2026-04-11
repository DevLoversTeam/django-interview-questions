**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  Django <img src="./assets/django.svg" width="40" height="40" alt="Django logo"/>
</h1>

<h2>Les questions et réponses les plus populaires pour un entretien Django</h2>

<details>
<summary>1. Qu'est-ce que Django et quelles sont ses fonctionnalités clés ?</summary>

#### Django

Django est un framework Python de haut niveau pour le développement web, qui
suit le principe « batteries included » : la plupart des tâches typiques sont
déjà implémentées dans l’écosystème du framework.

#### Fonctionnalités clés de Django :

1. **Démarrage rapide du développement :** génération du projet et des apps,
   structure prête à l’emploi et conventions claires.
2. **Panneau d’administration intégré :** Django Admin généré automatiquement
   pour gérer les données via le navigateur.
3. **ORM puissant :** travail avec la base de données via des modèles Python,
   sans SQL manuel dans la plupart des cas.
4. **Système de migrations :** contrôle et versionnement des changements de
   schéma de la base de données.
5. **Routage URL et couche view :** séparation claire du routage, de la logique
   métier et de la présentation.
6. **Moteur de templates :** templates intégrés pour le rendu HTML avec prise
   en charge de l’héritage de templates.
7. **Sécurité par défaut :** protection contre CSRF, XSS, injection SQL,
   clickjacking, et bonnes pratiques d’authentification.
8. **Authentification intégrée :** utilisateurs, groupes, permissions, sessions.
9. **Gestion des formulaires :** Django Forms/ModelForms avec validation côté
   serveur.
10. **Scalabilité et écosystème :** cache, middleware, signaux,
    intégration avec Celery, DRF, Redis, PostgreSQL, etc.

#### Quand Django est particulièrement pertinent :

- CRM/ERP et systèmes métiers internes.
- Plateformes de contenu, marketplaces, espaces utilisateurs.
- API + partie web dans un même projet.
- Produits où la rapidité de livraison, la sécurité et la maintenabilité du
  code sont essentielles.

#### Exemple court de ce que Django offre « out of the box » :

```bash
django-admin startproject config .
python manage.py startapp users
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Après cela, tu as déjà un squelette de projet de base, une base de données
connectée, un système de migrations et l’accès à l’admin.

#### Conclusion :

Django est un choix pragmatique pour un développement backend rapide et sécurisé,
surtout quand il faut une architecture mature, une stack stable et un lancement
rapide du produit.

</details>

<details>
<summary>2. Quels sont les avantages d’utiliser Django ?</summary>

#### Django

Django est souvent choisi pour le développement commercial lorsqu’on a besoin
d’un time-to-market rapide, d’une architecture stable et d’un backend sécurisé,
sans devoir « assembler » des dizaines de bibliothèques tierces.

#### Avantages clés de Django :

1. **Grande vitesse de développement :** de nombreuses tâches typiques sont déjà
   implémentées (auth, admin, forms, ORM, sessions, cache).
2. **Sécurité « out of the box » :** mécanismes intégrés contre CSRF, XSS,
   injection SQL, clickjacking, et gestion sûre des mots de passe.
3. **Structure de projet claire :** conventions compréhensibles qui simplifient
   l’onboarding de l’équipe et la maintenance du code à long terme.
4. **ORM puissant et migrations :** travail rapide avec la BD, contrôle de
   l’évolution du schéma, bonne prise en charge de PostgreSQL et d’autres SGBD relationnels.
5. **Admin panel utile pour le business :** Django Admin permet de fournir
   rapidement à l’équipe contenu/opérations une interface de travail sans
   développement frontend séparé.
6. **Bonne scalabilité de l’architecture :** apps, middleware, signals, celery,
   cache et files de tâches s’intègrent facilement en production.
7. **Écosystème mature :** DRF, django-allauth, django-filter,
   django-celery-beat et d’autres outils éprouvés.
8. **Adapté aux projets enterprise :** releases prévisibles, grande communauté,
   documentation de qualité et pratiques stables.

#### Valeur pratique pour l’équipe :

- Moins de code d’infrastructure au démarrage.
- Moins de risques d’erreurs de sécurité dans l’implémentation de base.
- Lancement MVP plus rapide et trajectoire de montée en charge plus claire.
- Meilleure maintenabilité à mesure que l’équipe et le code grandissent.

#### Quand les avantages de Django se ressentent le plus :

- B2B SaaS, CRM/ERP, espaces utilisateurs, marketplaces.
- Projets avec beaucoup de logique métier et de rôles d’accès.
- Équipes pour lesquelles la stabilité et l’évolution prévisible du produit
  sont prioritaires.

#### Conclusion :

La force de Django est d’apporter un résultat business rapide sans compromis
sur la sécurité ni sur la maintenabilité du code.

</details>

<details>
<summary>3. Quelle est la différence entre les architectures MVC et MVT ?</summary>

#### Django

Dans Django, on parle plus souvent de **MVT (Model-View-Template)**, alors que
dans beaucoup d’autres frameworks on utilise le terme **MVC (Model-View-Controller)**.
Conceptuellement, ces approches sont très proches ; la différence est surtout
liée aux rôles et à la terminologie.

#### MVC (classique) :

1. **Model** - gestion des données et de la logique métier.
2. **View** - affichage des données (UI / couche de présentation).
3. **Controller** - traite la requête entrante et orchestre le flux entre
   Model et View.

#### MVT dans Django :

1. **Model** - modèles de données et accès à la BD via l’ORM.
2. **View** - traitement de la requête HTTP, exécution de la logique métier,
   préparation de la réponse.
3. **Template** - couche de présentation (HTML + syntaxe template).

#### Correspondance MVC et MVT :

- `Model (MVC)` ≈ `Model (Django MVT)`
- `View (MVC)` ≈ `Template (Django MVT)`
- `Controller (MVC)` ≈ `View + URL dispatcher (Django MVT)`

Autrement dit, dans Django, le rôle du « contrôleur » est réparti entre
`urls.py` (routage) et `views.py` (traitement de la requête).

#### Exemple simple de flux Django (MVT) :

1. La requête arrive sur une URL, par exemple `/articles/`.
2. `urls.py` la dirige vers la `view` correspondante.
3. La `view` récupère les données depuis le `Model`.
4. La `view` transmet les données au `Template`.
5. Le `Template` rend le HTML et renvoie une `HttpResponse`.

#### Conclusion :

- Django ne « casse » pas MVC ; il l’implémente dans sa variante MVT.
- Différence pratique clé : dans Django, la `view` porte la logique de requête,
  et la représentation visuelle est dans le `template`.

</details>

<details>
<summary>4. Pourquoi Django est-il considéré comme un framework loosely coupled ?</summary>

#### Django

Django est qualifié de **loosely coupled** (faiblement couplé), car ses
composants peuvent être modifiés, étendus ou remplacés de manière indépendante,
sans réécrire toute l’application.

#### Ce que cela signifie en pratique :

1. **Composants séparés par responsabilité :** routage URL, view, templates,
   modèles, formulaires, middleware fonctionnent ensemble, mais ne sont pas
   « fusionnés » dans une seule couche monolithique.
2. **Architecture modulaire d’apps :** le projet est composé d’`apps`, qu’on
   peut activer/désactiver via `INSTALLED_APPS`.
3. **Remplacement possible de parties spécifiques :** par exemple moteur de
   templates, user model, backend de cache, email backend, storage backend.
4. **Configuration via settings :** le comportement du système se règle via des
   paramètres, et non via une logique rigidement codée.
5. **Extension via middleware et signals :** on peut ajouter des fonctionnalités
   sans modifier le cœur de la logique métier.

#### Exemples typiques d’approche loosely coupled dans Django :

- Remplacer SQLite par PostgreSQL uniquement via `DATABASES`.
- Ajouter un cache Redis sans réécrire les views ni les modèles.
- Passer du stockage local à un stockage S3-compatible via un backend.
- Basculer l’auth vers un modèle utilisateur custom (`AUTH_USER_MODEL`) sans
  casser l’architecture globale du projet.

#### Pourquoi c’est important pour l’équipe :

- Plus simple de faire évoluer le produit par modules.
- Plus facile de tester les parties séparément.
- Moins de risques lors du refactoring.
- Maintenance facilitée sur un cycle de vie long.

#### Conclusion :

Le loosely coupled dans Django, c’est de la flexibilité d’ingénierie : tu peux
faire évoluer le projet progressivement, en changeant des sous-systèmes ciblés,
au lieu de tout reconstruire d’un coup.

</details>

<details>
<summary>5. Quelle est la différence entre Django et FastAPI ?</summary>

#### Django

Django et FastAPI adressent des besoins différents. Les deux frameworks sont
solides, mais on les choisit pour des types de produits et d’équipes différents.

#### Différence clé :

- **Django** - framework web full-featured « out of the box » (ORM, admin,
  auth, templates, forms, sessions, middleware).
- **FastAPI** - framework ASGI léger et très rapide, orienté avant tout vers la
  construction d’API avec typage et documentation automatique.

#### Comparaison Django vs FastAPI :

1. **Objectif**
- Django : systèmes web complets et API dans un même projet.
- FastAPI : API-first, microservices, services à haute concurrence.

2. **Vitesse de démarrage du projet**
- Django : très rapide pour CRUD/admin/espace utilisateur.
- FastAPI : rapide pour API, mais plus de décisions à assembler soi-même.

3. **Performance**
- Django : suffisante pour la plupart des scénarios business ; historiquement
  WSGI, mais supporte aussi ASGI.
- FastAPI : généralement plus performant sur charge I/O grâce à une approche
  async-first.

4. **ORM et travail avec la base de données**
- Django : ORM intégré mature + migrations.
- FastAPI : ORM non intégré ; SQLAlchemy/SQLModel/Tortoise le plus souvent.

5. **Admin et back-office**
- Django : Django Admin puissant « out of the box ».
- FastAPI : l’admin doit être développé ou intégré séparément.

6. **Validation et schémas**
- Django : forms/serializers DRF.
- FastAPI : modèles Pydantic comme standard de facto.

7. **Documentation API**
- Django : généralement via DRF + paquets Swagger/OpenAPI.
- FastAPI : OpenAPI/Swagger UI généré automatiquement.

8. **Écosystème**
- Django : très riche pour les produits web (CMS, auth, patterns admin).
- FastAPI : fort en API/microservices avec une stack async moderne.

#### Quand choisir Django :

- Besoin d’un backend « all-in-one » avec résultat business rapide.
- Modèle de rôles complexe, admin, nombreuses entités CRUD.
- Priorité à des conventions stables et à la maintenabilité long terme.

#### Quand choisir FastAPI :

- Besoin d’un service API-first avec forte concurrence de requêtes.
- Priorité aux intégrations async (API externes, files, streaming, websocket).
- L’équipe veut une stack minimaliste et très contrôlable.

#### Conclusion :

- **Django** - optimal pour lancer rapidement des fonctionnalités métier et des
  systèmes web complexes.
- **FastAPI** - optimal pour des API modernes performantes et des scénarios
  microservices.
- Dans les grands produits, ces frameworks coexistent souvent : Django pour le
  core/admin, FastAPI pour des services API séparés.

</details>

<details>
<summary>6. Quels sont les inconvénients et les limites de Django par rapport à d’autres frameworks ?</summary>

#### Django

Django est un framework solide, mais pas universellement le meilleur pour tous
les types de projets. Ses limites apparaissent surtout dans des scénarios
techniques spécifiques.

#### Principaux inconvénients et limites de Django :

1. **Entrée plus « lourde » pour des services très simples**
- Pour un petit microservice, Django peut être excessif à cause du volume de
  composants intégrés.

2. **UX moins « native async-first » que FastAPI**
- Django supporte l’async, mais historiquement une grande partie de
  l’écosystème est orientée sync.
- Pour des API I/O très chargées, FastAPI/Starlette offrent parfois un chemin
  plus simple.

3. **ORM pas idéal pour du SQL très complexe**
- L’ORM Django est puissant pour la majorité des cas, mais pour des requêtes
  analytiques très complexes ou des optimisations DB spécifiques, il faut
  souvent écrire du SQL brut.

4. **Conventions assez strictes**
- Les conventions Django sont un avantage pour l’équipe, mais pour des
  ingénieurs qui veulent un contrôle très fin, elles peuvent sembler limitantes.

5. **Style monolithique par défaut**
- Django pousse naturellement vers un monolithe modulaire plutôt que vers des
  microservices très granulaires.
- Pour une architecture microservice-first, il faut une discipline claire de
  séparation.

6. **Étapes supplémentaires pour un DX API-first moderne**
- Pour une API REST complète, on ajoute généralement DRF ; pour OpenAPI,
  des outils supplémentaires ; pour le temps réel, une stack séparée
  (par ex. Channels).

7. **Performance « out of the box » pas toujours maximale**
- Sans cache, index BD, optimisation des requêtes ORM et profiling correct,
  les grands systèmes peuvent devenir lents.

#### Erreurs typiques confondues avec des « défauts de Django » :

- Requêtes N+1 à cause d’une mauvaise utilisation de l’ORM.
- Absence de stratégie de cache.
- Mauvaise décomposition modulaire des apps.
- Mélange de logique métier dans les views sans couche de services.

Ce sont plus souvent des problèmes d’architecture d’équipe que des faiblesses
intrinsèques du framework.

#### Quand Django peut ne pas être le meilleur choix :

- Service API très léger avec logique métier minimale.
- API async à très haut débit comme exigence principale.
- Système nécessitant un contrôle low-level maximal sans core framework « lourd ».

#### Conclusion :

Les limites de Django sont réelles, mais prévisibles. Pour la majorité des
applications métier, ses avantages (vitesse de développement, sécurité,
maintenabilité) dominent. L’essentiel est de choisir le framework selon le
contexte, pas selon la mode.

</details>

<details>
<summary>7. Comment fonctionne Django (cycle de vie requête–réponse) ?</summary>

#### Django

Le cycle de vie dans Django est une séquence d’étapes entre l’arrivée de la
requête HTTP sur le serveur et la génération de la réponse HTTP finale pour le
client.

#### Séquence de traitement d’une requête :

1. **Le client envoie une requête HTTP**
- Le navigateur ou un client API appelle l’application Django.

2. **Le serveur WSGI/ASGI transmet la requête à Django**
- Par exemple : Gunicorn/Uvicorn + Nginx.

3. **La requête traverse les middleware (phase request)**
- Les middleware peuvent modifier/enrichir la requête :
  authentification, sessions, locale, contrôles de sécurité, etc.

4. **Le resolveur d’URL cherche la route correspondante**
- Django associe l’URL aux règles dans `urls.py`.
- Si aucune route n’est trouvée -> `404 Not Found`.

5. **La view est appelée**
- La view reçoit `request`, exécute la logique métier :
  lit/écrit des données, vérifie les accès, prépare le contexte.

6. **Travail avec les modèles et la BD (si nécessaire)**
- Via l’ORM (`Model.objects...`) ou SQL brut pour les cas complexes.

7. **Construction de la réponse**
- HTML via `render(...)` + template,
- ou JSON via `JsonResponse`,
- ou redirect / file response.

8. **La réponse traverse les middleware (phase response)**
- Les middleware peuvent ajouter headers, cookies, cache-control, logging.

9. **La réponse est renvoyée au client**
- Le navigateur rend la page ou le client traite la réponse API.

#### Ce qui se passe en cas d’erreurs :

- `Http404` ou route absente -> page 404.
- Exceptions non interceptées -> page 500.
- Le traitement des exceptions passe aussi par la chaîne middleware.

#### Chaîne résumée :

`Client -> Serveur (WSGI/ASGI) -> Middleware (request) -> URLconf -> View -> Model/ORM -> Template/Serializer -> Middleware (response) -> Client`

#### Conclusion :

La force de Django est un pipeline requête/réponse prévisible : facile à déboguer,
à tester et à faire évoluer, car chaque étape a une responsabilité claire.

</details>

<details>
<summary>8. Comment créer un nouveau projet Django ?</summary>

#### Django

Un nouveau projet Django se crée en quelques étapes standard : préparation de
l’environnement, installation de Django, génération du projet, migrations et
lancement du serveur.

#### Étapes :

1. **Créer le répertoire du projet**

```bash
mkdir my_django_project
cd my_django_project
```

2. **Créer et activer l’environnement virtuel**

```bash
python -m venv .venv
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate         # Windows (PowerShell/CMD)
```

3. **Installer Django**

```bash
pip install django
```

4. **Générer le projet**

```bash
django-admin startproject config .
```

Après cela, les fichiers clés apparaissent :
- `manage.py`
- `config/settings.py`
- `config/urls.py`
- `config/asgi.py`
- `config/wsgi.py`

5. **Appliquer les migrations initiales**

```bash
python manage.py migrate
```

6. **Créer un administrateur**

```bash
python manage.py createsuperuser
```

7. **Lancer le serveur de dev**

```bash
python manage.py runserver
```

#### Vérification :

- Ouvre `http://127.0.0.1:8000/` - page de démarrage Django.
- Ouvre `http://127.0.0.1:8000/admin/` - admin (après `createsuperuser`).

#### Étape suivante recommandée :

Créer la première app et l’ajouter à `INSTALLED_APPS` :

```bash
python manage.py startapp core
```

C’est un démarrage de base, correct, pour la majorité des projets Django.

#### Conclusion :

Le bootstrap standard de Django est simple et prévisible : en quelques commandes,
tu obtiens un squelette fonctionnel prêt pour le développement.

</details>

<details>
<summary>9. Pourquoi est-il important d’utiliser un environnement virtuel avec Django ?</summary>

#### Django

L’environnement virtuel (`venv`) isole les dépendances d’un projet des paquets
Python globaux du système. Pour Django, c’est critique, car les projets ont
souvent des versions de bibliothèques et des exigences de compatibilité différentes.

#### Pourquoi c’est important :

1. **Isolation des dépendances**
- Chaque projet utilise ses propres versions de `Django`, `djangorestframework`,
  `psycopg`, `celery`, etc., sans conflits avec d’autres projets.

2. **Reproductibilité de l’environnement**
- Il est facile de figer l’état des dépendances dans `requirements.txt` et de le
  reproduire sur une autre machine ou un serveur.

3. **Stabilité du déploiement**
- Moins de risques de « works on my machine » quand local et CI/production
  utilisent des versions différentes.

4. **Mises à jour sûres**
- On peut tester les upgrades de Django ou d’autres paquets sans casser les
  autres projets locaux.

5. **Propreté du Python système**
- Les outils système de l’OS ne dépendent pas des paquets installés pour le dev.

#### Ce qui arrive sans `venv` :

- Conflits de versions entre projets.
- Erreurs d’import imprévisibles après `pip install` d’un nouveau paquet.
- Débogage CI/CD plus difficile à cause d’environnements divergents.
- Outils locaux cassés après des mises à jour globales.

#### Pratique minimale pour l’équipe :

1. Créer `.venv` à la racine de chaque repo.
2. Activer l’environnement avant `pip install` et commandes `manage.py`.
3. Figer les dépendances dans `requirements.txt` (ou `pyproject.toml` + lock file).
4. Ajouter `.venv/` dans `.gitignore`.

#### Conclusion :

`venv` dans Django n’est pas une option, mais un standard d’ingénierie de base.
Il garantit prévisibilité, stabilité et workflow d’équipe correct.

</details>

<details>
<summary>10. Quelle est la structure d’un projet Django et le rôle des fichiers principaux : manage.py, settings.py, urls.py ?</summary>

#### Django

Un projet Django typique a deux parties clés : la racine du repo et le package
de configuration (souvent `config/`) contenant les réglages globaux de l’application.

#### Structure de base d’un projet :

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

#### Rôle des fichiers principaux :

1. **manage.py**
- Point d’entrée CLI pour le travail local avec le projet.
- Sert à lancer les commandes :
  `runserver`, `migrate`, `makemigrations`, `createsuperuser`, `test`, `shell`.
- Indique automatiquement à Django quel module settings utiliser.

2. **settings.py**
- Configuration centrale du projet.
- Définit notamment :
  `INSTALLED_APPS`, `MIDDLEWARE`, `DATABASES`, `TEMPLATES`, `CACHES`,
  `STATIC_URL`, `MEDIA_URL`, `AUTH_PASSWORD_VALIDATORS`, `TIME_ZONE`, etc.
- En production, on sépare souvent en modules :
  `settings/base.py`, `settings/dev.py`, `settings/prod.py`.

3. **urls.py**
- Carte globale des routes (URL dispatcher).
- Reçoit le chemin demandé et délègue à l’app correspondante via `include()`.
- On y connecte aussi souvent `admin/`, routes health-check et routing API.

#### Comment tout fonctionne ensemble :

1. `manage.py` lance une commande Django.
2. Django charge `settings.py`.
3. La requête HTTP passe par les middleware.
4. `urls.py` décide quelle `view` traitera la requête.
5. La `view` renvoie une réponse (HTML/JSON/redirect/file).

#### Recommandations pratiques de tech lead :

- Garder `urls.py` « fin » : le routage principal doit vivre au niveau des apps.
- Ne pas transformer `settings.py` en « fourre-tout » : utiliser une structure modulaire.
- Stocker tous les secrets (clés, mots de passe, tokens) dans les variables d’environnement, pas dans le code.
- Sortir la logique métier de `views.py` vers une couche de services pour simplifier les tests.

#### Conclusion :

`manage.py`, `settings.py` et `urls.py` sont le noyau opérationnel du projet Django :
pilotage, configuration et routage. Une bonne organisation de ces fichiers impacte
 directement la scalabilité et la maintenabilité du système.

</details>

<details>
<summary>11. À quoi servent les applications Django (apps) et comment organiser un projet avec plusieurs apps ?</summary>

#### Django

Dans Django, une `app` est un module fonctionnel isolé avec ses propres modèles,
views, URL, templates, tests et (si nécessaire) couche API. Les apps servent à
séparer les domaines et à faire évoluer le code de manière contrôlée.

#### À quoi servent les apps Django :

1. **Modularité**
- Chaque app couvre un contexte métier précis (par exemple : `users`,
  `billing`, `orders`, `notifications`).

2. **Réutilisation**
- Une app peut être déplacée vers un autre projet ou réutilisée en interne.

3. **Localisation des changements**
- Les changements dans un domaine impactent moins les autres modules.

4. **Meilleure maintenabilité**
- L’équipe s’oriente plus facilement dans le code quand les responsabilités
  sont bien séparées.

5. **Tests plus simples**
- Les tests se structurent par domaines, pas sur un monolithe chaotique.

#### Comment organiser un projet avec plusieurs apps :

1. **Découper par domaine, pas par type technique**
- Bien : `users`, `catalog`, `checkout`, `payments`.
- Mal : `models_app`, `views_app`, `utils_app`.

2. **Chaque app a son propre `urls.py`**
- Dans `config/urls.py`, seulement des connexions via `include()`.

3. **Garder chaque app autonome**
- L’app doit avoir ses `models.py`, `views.py`, `tests.py`, `admin.py`,
  `apps.py`, `migrations/`.

4. **Éviter les dépendances cycliques entre apps**
- Pour la communication inter-modules, utiliser une couche de services ou des
  interfaces claires, plutôt que des imports croisés « partout ».

5. **Extraire le code partagé dans un module `common/core`**
- Mais uniquement le vrai code partagé ; ne pas en faire une « poubelle ».

#### Exemple de structure multi-modules :

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

#### Connexion des routes d’app :

```python
# config/urls.py
from django.urls import include, path

urlpatterns = [
    path("users/", include("apps.users.urls")),
    path("orders/", include("apps.orders.urls")),
]
```

#### Anti-patterns typiques :

- Une seule app « gigantesque » pour tout le projet.
- Découpage par couches techniques au lieu du domaine métier.
- Code partagé massif sans propriétaire ni contrat.
- Imports croisés entre apps sans contrôle des dépendances.

#### Conclusion :

Les apps Django sont l’outil de base pour faire évoluer le code. Si le système
est découpé par domaines avec des frontières claires, le projet reste plus
longtemps maîtrisable et stable.

</details>

<details>
<summary>12. Comment fonctionne le routage URL dans Django ?</summary>

#### Django

Le routage URL dans Django détermine quelle `view` doit traiter une requête HTTP.
Le URL dispatcher configuré dans `urls.py` s’en charge.

#### Comment fonctionne le routing URL, étape par étape :

1. **La requête arrive dans Django**
- Par exemple : `GET /articles/42/`.

2. **Django lit le `urlpatterns` racine**
- Généralement dans `config/urls.py`.

3. **Matching séquentiel des routes**
- Django vérifie les patterns de haut en bas.
- Le premier match gagne.

4. **`include()` est appelé si nécessaire**
- Une partie de la route est déléguée au `urls.py` d’une app.

5. **Les paramètres URL sont passés à la view**
- Par exemple `articles/<int:id>/` passe `id` en argument.

6. **La view construit la response**
- HTML, JSON, redirect ou fichier.

7. **S’il n’y a pas de match -> 404**
- Django renvoie `Not Found`.

#### Exemple de base :

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

#### Convertisseurs dans `path()` :

- `<int:id>` -> entier
- `<str:slug>` -> chaîne sans `/`
- `<slug:slug>` -> format slug
- `<uuid:id>` -> UUID
- `<path:subpath>` -> chemin arbitraire, y compris `/`

#### Règles pratiques de maintenabilité :

1. Garder `urls.py` racine court, déléguer aux apps.
2. Utiliser `name=` pour chaque route (utile pour `reverse()` et templates).
3. Garder une structure URL API/web stable (versionnement, préfixes).
4. L’ordre des routes compte : les patterns spécifiques avant les généraux.

#### Conclusion :

Le routing URL dans Django est un mécanisme de dispatch contrôlé. Des routes bien
conçues rendent le code prévisible, scalable et sûr pour le refactoring.

</details>

<details>
<summary>13. Différence entre path() et re_path().</summary>

#### Django

`path()` et `re_path()` sont deux manières de décrire des routes URL dans Django.
Elles résolvent le même problème, mais avec des niveaux différents de simplicité
et de flexibilité.

#### `path()` :

- Utilise une syntaxe déclarative lisible avec convertisseurs.
- Convient à la majorité des routes classiques.
- Plus lisible et plus facile à maintenir en équipe.

Exemple :

```python
from django.urls import path
from . import views

urlpatterns = [
    path("posts/<int:post_id>/", views.post_detail, name="post_detail"),
    path("users/<slug:username>/", views.user_profile, name="user_profile"),
]
```

#### `re_path()` :

- Utilise des expressions régulières (regex).
- Offre une flexibilité maximale pour des patterns URL non standards.
- Plus difficile à lire, risque d’erreurs regex plus élevé.

Exemple :

```python
from django.urls import re_path
from . import views

urlpatterns = [
    re_path(r"^archive/(?P<year>[0-9]{4})/$", views.archive_year),
    re_path(r"^file/(?P<path>.+\.(pdf|docx))/$", views.file_view),
]
```

#### Quand utiliser quoi :

1. **Utiliser `path()` par défaut**
- C’est l’approche standard et recommandée dans Django moderne.

2. **Utiliser `re_path()` seulement si `path()` ne suffit pas**
- Par exemple validation complexe du format URL au niveau route ou schémas URL legacy.

#### Comparaison :

- Simplicité : `path()` > `re_path()`
- Flexibilité : `re_path()` > `path()`
- Maintenabilité d’équipe : en général `path()` est meilleur

#### Conseil pratique :

Ne complexifie pas les URL avec des regex sans nécessité. Si le besoin peut être
couvert par des convertisseurs `path()` + validation dans view/serializer/form,
c’est souvent la meilleure solution.

#### Conclusion :

`path()` est l’outil principal pour 90% des routes. `re_path()` est une solution
ciblée pour les cas particuliers qui exigent la flexibilité regex.

</details>

<details>
<summary>14. Comment fonctionnent les URL configurations et include() ?</summary>

#### Django

La configuration URL dans Django est un ensemble de règles (`urlpatterns`) qui
associent un chemin de requête à une `view` précise. La fonction `include()`
permet de découper un gros routing en modules au niveau app.

#### Qu’est-ce qu’une URL configuration :

- C’est un module Python (généralement `urls.py`) avec une liste de routes.
- Chaque route est décrite avec `path()` ou `re_path()`.
- Django parcourt la liste de haut en bas et prend le premier match.

#### À quoi sert `include()` :

1. **Décomposition du routing**
- Le `urls.py` racine reste court.

2. **Modularité par apps**
- Chaque app a ses propres routes dans son `urls.py`.

3. **Meilleure maintenabilité**
- L’équipe travaille dans le contexte routing local du domaine concerné.

#### Exemple d’organisation :

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

#### Comment fonctionne la chaîne avec `include()` :

1. La requête `/blog/django-routing/` arrive dans `config/urls.py`.
2. Le préfixe `blog/` correspond.
3. Django transmet le reste du chemin (`django-routing/`) à `apps.blog.urls`.
4. La route correspondante est trouvée et la `view` adéquate est appelée.

#### Namespace et `app_name` :

- `app_name` + `name` de route donne un namespace nommé.
- Cela permet de faire un reverse sans conflit :
  `reverse("blog:detail", kwargs={"slug": "django-routing"})`.

#### Recommandations pratiques :

1. Utiliser `include()` systématiquement au niveau app.
2. Ajouter `app_name` dans chaque `urls.py` d’app.
3. Garder des préfixes stables (`api/v1/`, `admin/`, `auth/`).
4. Ne pas mettre de logique métier dans la couche URL - uniquement routing.

#### Conclusion :

Les URL configurations + `include()` sont la base d’un routing scalable dans Django :
frontières claires entre apps, routing racine propre et navigation prévisible.

</details>

<details>
<summary>15. Qu’est-ce qu’une view dans Django ?</summary>

#### Django

Une `view` dans Django est un gestionnaire de requête HTTP. C’est la view qui
reçoit `request`, exécute la logique nécessaire et renvoie une `HttpResponse`
(HTML, JSON, redirect, fichier).

#### Rôle de la view dans le cycle requête/réponse :

1. Recevoir la requête après le matching URL.
2. Vérifier les paramètres d’entrée (path/query/body/files).
3. Appeler la logique métier et/ou l’ORM.
4. Préparer les données de la réponse.
5. Renvoyer une réponse HTTP valide.

#### Types de views :

1. **FBV (Function-Based View)**
- Fonction Python classique.
- Adaptée à une logique simple ou très custom.

2. **CBV (Class-Based View)**
- Classe avec méthodes `get()`, `post()`, etc.
- Mieux scalable pour les scénarios CRUD typiques, surtout avec Generic Views.

#### Exemple FBV :

```python
from django.http import HttpResponse, JsonResponse
from django.shortcuts import render

def healthcheck(request):
    return HttpResponse("OK")

def home(request):
    return render(request, "home.html", {"title": "Accueil"})

def api_status(request):
    return JsonResponse({"status": "ok"})
```

#### Points importants :

- Une view ne doit pas devenir une « god function ».
- La logique métier complexe doit aller dans une couche de services.
- La view doit rester fine : orchestration, validation, appel de services, response.

#### Erreurs typiques :

- Écrire une logique métier lourde de centaines de lignes directement en view.
- Dupliquer la même logique dans plusieurs views.
- Ignorer les contrôles d’accès/autorisation au niveau endpoint.

#### Conclusion :

La view est le point où le protocole web rencontre la logique métier. Des views
bien conçues rendent le code prévisible, testable et facile à maintenir.

</details>

<details>
<summary>16. Différence entre les vues fonctionnelles (FBV) et les vues basées sur des classes (CBV).</summary>

#### Django

Dans Django, il existe deux styles principaux de vues : **FBV** (function-based
views) et **CBV** (class-based views). Les deux approches sont valides ; la
différence se situe dans l’organisation de la logique et la scalabilité du code.

#### FBV (Function-Based Views) :

- La vue est définie comme une fonction.
- La logique requête/réponse se lit de haut en bas.
- Approche simple et transparente pour de petits endpoints.

Exemple :

```python
from django.http import JsonResponse

def profile_detail(request, user_id):
    if request.method == "GET":
        return JsonResponse({"user_id": user_id})
    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### CBV (Class-Based Views) :

- La vue est définie comme une classe (méthodes `get`, `post`, `put`, `delete`, etc.).
- La logique peut être réutilisée via héritage et mixins.
- Très adaptée aux scénarios CRUD, listes, formulaires, detail/create/update/delete.

Exemple :

```python
from django.http import JsonResponse
from django.views import View

class ProfileDetailView(View):
    def get(self, request, user_id):
        return JsonResponse({"user_id": user_id})
```

#### Différences clés :

1. **Simplicité d’entrée**
- FBV : plus simple au démarrage.
- CBV : demande de comprendre la hiérarchie des classes et le mécanisme de dispatch.

2. **Scalabilité**
- FBV : bien pour des handlers courts et très custom.
- CBV : mieux pour des patterns répétitifs et des gros projets.

3. **Réutilisation du code**
- FBV : via fonctions helper/décorateurs.
- CBV : via héritage, mixins, generic views.

4. **Lisibilité**
- FBV : souvent plus évidente localement.
- CBV : peut être plus complexe à cause du comportement « caché » des classes de base.

5. **Tests**
- Les deux approches se testent bien si la logique n’est pas « enfouie » dans la vue.

#### Quand choisir FBV :

- Endpoint simple et fortement custom.
- Besoin d’une transparence maximale pour un debug rapide.
- Pas d’intérêt à utiliser une hiérarchie de classes.

#### Quand choisir CBV :

- Beaucoup d’écrans/endpoints CRUD similaires.
- Besoin de mixins, classes de permissions, patterns réutilisables.
- Équipe alignée sur Generic CBV et style unifié.

#### Conclusion :

FBV et CBV ne sont pas « bien/mal », mais un choix de contexte. En production,
on utilise souvent les deux : FBV pour les besoins ciblés, CBV pour les scénarios
structurés et répétitifs.

</details>

<details>
<summary>17. Quand vaut-il mieux utiliser CBV et generic class-based views ?</summary>

#### Django

CBV et generic CBV sont particulièrement utiles quand le projet contient beaucoup
de patterns web/API répétitifs et qu’il faut standardiser le comportement entre endpoints.

#### Quand les CBV apportent un vrai gain :

1. **Scénarios CRUD**
- Listes, pages détail, création, mise à jour, suppression.
- Classes typiques : `ListView`, `DetailView`, `CreateView`, `UpdateView`, `DeleteView`.

2. **Beaucoup d’endpoints similaires**
- Quand les différences portent surtout sur le modèle, le formulaire ou les permissions.

3. **Besoin de réutiliser la logique**
- Via des mixins (`LoginRequiredMixin`, `PermissionRequiredMixin`, mixins custom).

4. **Style unifié dans une grande équipe**
- Les CBV facilitent l’unification et réduisent le copy-paste.

5. **Extension du comportement de base par override**
- Par exemple `get_queryset()`, `get_context_data()`, `form_valid()`,
  `get_success_url()`.

#### Quand les generic CBV sont particulièrement adaptées :

- Interfaces de type admin.
- Pages back-office.
- Formulaires standards et sections de contenu.
- Implémentation rapide d’un MVP sans perdre la structure du code.

#### Exemple generic CBV :

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

#### Quand il vaut mieux NE PAS utiliser generic CBV :

1. Logique très non standard qui ne rentre pas dans le paradigme CRUD.
2. Endpoint avec orchestration complexe (plusieurs services/intégrations).
3. Trop d’overrides, rendant la generic class moins lisible qu’une FBV simple.

#### Règle pratique de tech lead :

- Commencer par generic CBV pour les cas standards.
- Si la vue casse le modèle generic, passer à CBV classique ou FBV.
- Ne pas s’accrocher au generic « parce que c’est plus élégant » : la priorité
  est la maintenabilité et la clarté.

#### Conclusion :

CBV/generic CBV sont des outils d’accélération et de standardisation. Ils sont
excellents pour les scénarios répétitifs, mais pour une logique métier atypique,
une approche plus simple et explicite est préférable.

</details>

<details>
<summary>18. Que sont les mixins en CBV et comment les utiliser ?</summary>

#### Django

Les `mixins` en CBV sont des classes auxiliaires avec un comportement
réutilisable, ajoutées à une vue via l’héritage multiple. Ils permettent de
construire des vues flexibles sans duplication de code.

#### Pourquoi utiliser des mixins :

1. **Réutilisation de logique**
- Authentification, permissions, filtrage de queryset, contexte commun, etc.

2. **Composition de comportement**
- Une vue est construite à partir de petites briques, pas d’une seule grosse classe.

3. **Réduction du copy-paste**
- Un mixin peut être utilisé dans des dizaines de vues.

#### Mixins built-in les plus courants dans Django :

- `LoginRequiredMixin` - accès réservé aux utilisateurs authentifiés.
- `PermissionRequiredMixin` - vérification d’une permission précise.
- `UserPassesTestMixin` - contrôle d’accès custom.
- `ContextMixin` - ajout de données au contexte template.

#### Exemple avec built-in mixins :

```python
from django.contrib.auth.mixins import LoginRequiredMixin, PermissionRequiredMixin
from django.views.generic import ListView
from .models import Order

class OrderListView(LoginRequiredMixin, PermissionRequiredMixin, ListView):
    model = Order
    permission_required = "orders.view_order"
    template_name = "orders/list.html"
```

#### Exemple de mixin custom :

```python
class StaffRequiredMixin:
    def dispatch(self, request, *args, **kwargs):
        if not request.user.is_staff:
            from django.http import HttpResponseForbidden
            return HttpResponseForbidden("Accès refusé")
        return super().dispatch(request, *args, **kwargs)
```

```python
class DashboardView(StaffRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### L’ordre des mixins est important :

- Django utilise la MRO (Method Resolution Order).
- En général, les mixins « restrictifs » (`LoginRequiredMixin`) se mettent à gauche.
- `View`/generic class se place plus à droite.

#### Règles pratiques :

1. Un mixin = une responsabilité.
2. Ne pas surcharger les mixins avec la logique métier.
3. Éviter des hiérarchies trop profondes qui compliquent le debug.
4. Pour du code métier complexe, utiliser des services plutôt que des mixins.

#### Erreurs typiques :

- Mixins trop « intelligents » qui modifient le comportement de façon imprévisible.
- Conflits de méthodes à cause d’un mauvais ordre d’héritage.
- Duplication des mêmes contrôles dans plusieurs vues au lieu d’un mixin commun.

#### Conclusion :

Les mixins sont un outil puissant en CBV pour la composition et la réutilisation.
Ils apportent le plus de valeur quand ils restent petits, à responsabilité claire,
et utilisés avec discipline.

</details>

<details>
<summary>19. Comment gérer les méthodes HTTP (GET, POST) ?</summary>

#### Django

Dans Django, les méthodes HTTP se gèrent dans les vues : `GET` sert généralement
à lire/afficher des données, `POST` à créer ou modifier l’état du système. Une
séparation correcte des méthodes est la base d’un API et d’un web-flow sûrs et prévisibles.

#### Gestion en FBV :

```python
from django.http import JsonResponse

def contact_view(request):
    if request.method == "GET":
        return JsonResponse({"form": "render contact form"})

    if request.method == "POST":
        # lecture request.POST, validation, sauvegarde
        return JsonResponse({"status": "created"}, status=201)

    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### Gestion en CBV :

```python
from django.http import JsonResponse
from django.views import View

class ContactView(View):
    def get(self, request):
        return JsonResponse({"form": "render contact form"})

    def post(self, request):
        # validation et sauvegarde
        return JsonResponse({"status": "created"}, status=201)
```

#### Limiter les méthodes autorisées (décorateurs) :

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

#### Règles pratiques :

1. **GET**
- Ne doit pas modifier l’état du système.
- Méthode sûre et souvent cacheable.

2. **POST**
- Utilisé pour créer/exécuter une action qui modifie les données.
- Pour les formulaires HTML : CSRF token obligatoire.

3. **Validation**
- Toujours valider les données entrantes (Forms/Serializer/couche service).

4. **Codes de réponse**
- `200` pour lecture réussie,
- `201` pour création,
- `400` pour erreurs de validation,
- `405` pour méthode non autorisée.

#### Erreurs typiques :

- Modifier des données via GET (violation de la sémantique HTTP).
- Mélanger logique GET et POST dans un bloc chaotique.
- Ne pas renvoyer les bons status codes.

#### Conclusion :

Le traitement GET/POST dans Django doit être explicite : une responsabilité par
méthode, validation claire et codes HTTP corrects. Cela améliore la sécurité,
les intégrations et la maintenabilité.

</details>

<details>
<summary>20. Comment implémenter une redirection (redirect) ?</summary>

#### Django

La redirection (`redirect`) dans Django s’utilise lorsqu’après une action il faut
envoyer l’utilisateur vers une autre page ou un autre endpoint.

#### Méthode principale :

```python
from django.shortcuts import redirect
```

`redirect(...)` renvoie une réponse HTTP avec code 302 (redirection temporaire)
par défaut.

#### Variantes d’utilisation :

1. **Vers une URL absolue/relative**

```python
return redirect("/dashboard/")
```

2. **Vers une route nommée (recommandé)**

```python
return redirect("orders:list")
```

3. **Vers une route avec paramètres**

```python
return redirect("orders:detail", order_id=order.id)
```

4. **Vers une instance de modèle (si `get_absolute_url` existe)**

```python
return redirect(order)
```

#### Exemple en FBV (Post/Redirect/Get) :

```python
from django.shortcuts import redirect, render

def create_order(request):
    if request.method == "POST":
        # sauvegarde des données
        return redirect("orders:list")
    return render(request, "orders/form.html")
```

#### Exemple en CBV :

```python
from django.urls import reverse_lazy
from django.views.generic import CreateView

class OrderCreateView(CreateView):
    model = Order
    fields = ["title", "amount"]
    success_url = reverse_lazy("orders:list")
```

#### Redirection temporaire vs permanente :

- `302 Found` - temporaire (par défaut dans Django).
- `301 Moved Permanently` - permanente (SEO/URL canoniques).

Pour une redirection permanente :

```python
from django.http import HttpResponsePermanentRedirect

return HttpResponsePermanentRedirect("/new-url/")
```

#### Conseils pratiques :

1. Utiliser des routes nommées plutôt que des URL codées en dur.
2. Après un POST réussi, faire un redirect (pattern PRG) pour éviter la
   double soumission au refresh.
3. Pour redirect après login/logout, utiliser `next` et des vérifications
   sûres de la cible.

#### Erreurs typiques :

- Redirection vers une URL qui redirige en boucle (redirect loop).
- URL hardcodée au lieu d’une route `name=`.
- Retourner `200` après un POST dans un flow où PRG est préférable.

#### Conclusion :

`redirect` dans Django est un outil de base pour piloter le user flow. Meilleure
pratique : URL nommées + pattern PRG + contrôle de sécurité de la cible.

</details>

<details>
<summary>21. Qu’est-ce que JsonResponse et quand l’utiliser ?</summary>

#### Django

`JsonResponse` est une réponse HTTP Django pour retourner des données au format JSON.
Il est surtout utilisé dans les endpoints API, les requêtes AJAX et les intégrations
inter-services.

#### Ce que fait `JsonResponse` :

1. Sérialise les données Python en JSON.
2. Définit le bon `Content-Type: application/json`.
3. Permet de définir explicitement le code de statut HTTP.

#### Exemple de base :

```python
from django.http import JsonResponse

def health(request):
    return JsonResponse({"status": "ok"})
```

#### Exemple avec code de statut :

```python
def create_item(request):
    # ... logique de création
    return JsonResponse({"id": 123, "message": "created"}, status=201)
```

#### Point important sur `safe` :

- Par défaut, `JsonResponse` attend un **dict** (`safe=True`).
- Pour retourner une liste, il faut mettre `safe=False`.

```python
def tags(request):
    return JsonResponse(["python", "django", "api"], safe=False)
```

#### Quand utiliser `JsonResponse` :

1. API simple sans DRF.
2. Endpoints internes pour frontend (fetch/AJAX).
3. Réponses webhook et intégrations techniques.
4. Endpoints health-check/diagnostic.

#### Quand préférer DRF à `JsonResponse` « pur » :

- Besoin de serializers, validation de schémas, pagination, throttling, politiques auth.
- Beaucoup d’endpoints API avec besoin d’une architecture API unifiée.

#### Recommandations pratiques :

1. Retourner une structure JSON claire (par ex. `{"data": ...}`, `{"error": ...}`).
2. Utiliser les bons statuts (`200`, `201`, `400`, `404`, `500`).
3. Ne pas exposer les traces d’exception en production.
4. Uniformiser le format d’erreur pour tout l’API.

#### Conclusion :

`JsonResponse` est un outil léger et pratique pour les réponses JSON dans Django.
Pour des API simples, il suffit ; pour des API larges, DRF est généralement préférable.

</details>

<details>
<summary>22. Comment retourner des fichiers (CSV, PDF) depuis une view ?</summary>

#### Django

Dans Django, on renvoie des fichiers depuis une view via `HttpResponse` ou
`FileResponse` avec les bons headers HTTP (`Content-Type`, `Content-Disposition`).

#### Principes de base :

1. **`Content-Type`** doit correspondre au type de fichier.
2. **`Content-Disposition`** détermine le comportement navigateur :
- `attachment` -> téléchargement
- `inline` -> affichage dans le navigateur (si supporté)

#### Exemple : retour CSV

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

#### Exemple : retour PDF depuis fichier

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

#### Si le PDF est généré dynamiquement :

- Générer en mémoire (`io.BytesIO`) ou dans un fichier temporaire.
- Puis renvoyer via `HttpResponse`/`FileResponse`.
- Bibliothèques fréquentes : `reportlab`, `weasyprint`, `xhtml2pdf`.

#### Pour les gros fichiers :

1. Utiliser `FileResponse` (streaming, moins de RAM).
2. Éviter de lire tout le fichier en mémoire (`read()` de gros fichiers).
3. Si nécessaire, utiliser Nginx/X-Accel-Redirect ou CDN/object storage.

#### Conseils pratiques :

1. Donner des noms de fichiers explicites dans `filename=`.
2. Contrôler l’accès aux fichiers (owner/permissions).
3. Ajouter un audit d’accès pour les documents sensibles.
4. En API, renvoyer des erreurs prévisibles (`404` si absent, `403` si interdit).

#### Conclusion :

Retourner du CSV/PDF dans Django repose surtout sur le bon type de réponse et les
headers. Pour petits fichiers, `HttpResponse` suffit ; pour production et gros
volumes, préférer `FileResponse` et le streaming.

</details>

<details>
<summary>23. Comment implémenter la pagination ?</summary>

#### Django

La pagination dans Django sert à découper de grandes listes en pages et à éviter
de rendre/transférer des centaines ou milliers d’éléments en une requête.

#### Outil de base :

- `django.core.paginator.Paginator`

#### Exemple en FBV :

```python
from django.core.paginator import Paginator
from django.shortcuts import render
from .models import Article

def article_list(request):
    queryset = Article.objects.order_by("-created_at")
    paginator = Paginator(queryset, 10)  # 10 éléments par page
    page_number = request.GET.get("page")
    page_obj = paginator.get_page(page_number)  # variante sûre

    return render(request, "articles/list.html", {"page_obj": page_obj})
```

#### Rendu pagination en template :

```django
{% for article in page_obj %}
  <h3>{{ article.title }}</h3>
{% endfor %}

<div class="pagination">
  {% if page_obj.has_previous %}
    <a href="?page=1">Première</a>
    <a href="?page={{ page_obj.previous_page_number }}">Précédente</a>
  {% endif %}

  <span>Page {{ page_obj.number }} sur {{ page_obj.paginator.num_pages }}</span>

  {% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">Suivante</a>
    <a href="?page={{ page_obj.paginator.num_pages }}">Dernière</a>
  {% endif %}
</div>
```

#### Variante CBV (encore plus simple) :

```python
from django.views.generic import ListView
from .models import Article

class ArticleListView(ListView):
    model = Article
    paginate_by = 10
    ordering = ["-created_at"]
```

#### Recommandations pratiques :

1. Utiliser un tri stable (`order_by`) pour une navigation prévisible.
2. Pour grosses listes, optimiser le queryset :
- `select_related`, `prefetch_related`, index BD.
3. Conserver les autres query params (filtres, recherche) entre pages.
4. Éviter un page size trop grand sans besoin.

#### Erreurs typiques :

- Pagination sans tri (données qui « sautent » entre pages).
- Usage de `page()` brut sans gérer les numéros invalides.
- Absence d’index sur colonnes de tri/filtre.

#### Conclusion :

Dans Django, la pagination est rapide et propre via `Paginator` ou `ListView`.
La performance dépend d’un bon queryset, d’un tri stable et d’un contrôle correct
des paramètres de page.

</details>

<details>
<summary>24. Comment gérer les erreurs 404 et 500 ?</summary>

#### Django

Les erreurs `404` et `500` dans Django sont gérées via le mécanisme standard
error-handling : templates d’erreur, handlers et réglages globaux.

#### Signification :

- **404 Not Found** - route ou ressource introuvable.
- **500 Internal Server Error** - erreur non interceptée côté serveur.

#### Gestion de base via templates :

En production (`DEBUG = False`), Django cherche automatiquement :

- `templates/404.html`
- `templates/500.html`

Si ces fichiers existent, ils sont affichés à l’utilisateur.

#### Handlers custom dans `urls.py` :

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

#### Différence clé entre dev et production :

1. **DEBUG=True (local)**
- Django affiche un traceback détaillé.

2. **DEBUG=False (production)**
- L’utilisateur voit une page 404/500 custom.
- Les détails techniques ne doivent pas fuiter.

#### Recommandations pratiques :

1. Toujours avoir des pages 404/500 conviviales.
2. Logger les erreurs (Sentry/ELK/OpenTelemetry), pas de stack trace côté user.
3. Ajouter un correlation/request ID dans les logs.
4. Renvoyer les bons statuts (pas de 200 sur pages d’erreur).
5. Pour API, renvoyer des erreurs JSON avec format unique.

#### Tests :

- Vérifier les 404 sur URL inexistantes.
- Tester les handlers 500 en staging avec `DEBUG=False`.
- Vérifier que les templates d’erreur sont disponibles en environnement buildé.

#### Conclusion :

Une bonne gestion 404/500 dans Django combine UX et maturité opérationnelle :
utilisateur avec message clair, équipe avec logs complets pour diagnostic.

</details>

<details>
<summary>25. Que sont les templates et comment passer des données d’une view vers un template ?</summary>

#### Django

Les templates dans Django sont la couche de présentation responsable de la
génération HTML à partir des données préparées dans la `view`.

#### Qu’est-ce qu’un template :

- Fichier HTML avec syntaxe template Django (`{{ }}` et `{% %}`).
- Permet d’afficher variables, boucles, conditions, inclusions de fragments.
- Sépare l’UI de la logique métier Python.

#### Passer des données de la view au template :

1. Construire un `context` (dict) dans la `view`.
2. Appeler `render(request, "template.html", context)`.

#### Exemple :

```python
from django.shortcuts import render
from .models import Article

def article_list(request):
    articles = Article.objects.filter(is_published=True).order_by("-created_at")
    context = {
        "page_title": "Articles",
        "articles": articles,
        "total": articles.count(),
    }
    return render(request, "articles/list.html", context)
```

#### Utilisation des données dans le template :

```django
<h1>{{ page_title }}</h1>
<p>Total : {{ total }}</p>

{% if articles %}
  <ul>
    {% for article in articles %}
      <li>{{ article.title }}</li>
    {% endfor %}
  </ul>
{% else %}
  <p>Aucun article publié.</p>
{% endif %}
```

#### Où Django cherche les templates :

- Dans les dossiers indiqués dans `TEMPLATES["DIRS"]`.
- Dans `templates/` à l’intérieur des apps (quand `APP_DIRS=True`).

#### Recommandations pratiques :

1. Garder la logique métier en Python (view/service), pas dans le template.
2. Passer seulement les données nécessaires dans le contexte.
3. Utiliser des URL nommées (`{% url 'app:view' %}`), pas de liens hardcodés.
4. Utiliser `include`/partials pour les éléments répétitifs.

#### Sécurité :

- Django échappe automatiquement les variables (protection XSS par défaut).
- Ne pas utiliser `|safe` sans certitude sur la source des données.

#### Conclusion :

Les templates Django offrent une manière propre, sûre et contrôlée de rendre du HTML.
La view prépare les données, le template les affiche : c’est la base de la
maintenabilité et de la séparation des responsabilités.

</details>

<details>
<summary>26. Comment fonctionne l’héritage de templates (extends, block) ?</summary>

#### Django

L’héritage de templates dans Django permet de créer un layout de base et de le
réutiliser dans les pages filles. Cela évite la duplication HTML et rend la
partie frontend plus maintenable.

#### Balises clés :

1. **`{% extends "base.html" %}`**
- Le template enfant hérite du template de base.

2. **`{% block ... %}{% endblock %}`**
- Dans le template de base, on définit des « slots » que les enfants peuvent remplir.

#### Template de base :

```django
{# templates/base.html #}
<!doctype html>
<html lang="uk">
<head>
  <meta charset="utf-8">
  <title>{% block title %}Mon site{% endblock %}</title>
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

#### Template enfant :

```django
{# templates/articles/list.html #}
{% extends "base.html" %}

{% block title %}Liste des articles{% endblock %}

{% block content %}
  <h1>Articles</h1>
  <p>Contenu de la page...</p>
{% endblock %}
```

#### `block.super` :

Si tu veux compléter un bloc au lieu de le remplacer entièrement :

```django
{% block title %}{{ block.super }} | Articles{% endblock %}
```

#### Recommandations pratiques :

1. Garder un `base.html` principal (head, header, footer, scripts).
2. Prévoir des blocs séparés pour `title`, `content`, `extra_css`, `extra_js`.
3. Éviter de dupliquer les mêmes sections dans chaque template.
4. Rester cohérent sur les noms de blocs dans tout le projet.

#### Erreurs typiques :

- Pas de structure de blocs unifiée entre pages.
- Logique métier dans le template au lieu de view/service.
- Duplication de layout sans `extends`.

#### Conclusion :

`extends` et `block` sont la base d’une architecture templates scalable dans Django :
layout unique, minimum de duplication, évolution UI plus rapide.

</details>

<details>
<summary>27. À quoi sert `{% include %}` ?</summary>

#### Django

`{% include %}` sert à insérer un template dans un autre. C’est pratique pour
les parties d’interface réutilisables : header, footer, cartes, tableaux, pagination.

#### Pourquoi utiliser `include` :

1. **Réduit la duplication HTML**
- Un fragment est réutilisable sur plusieurs pages.

2. **Améliore la maintenabilité**
- Modifier un partial met à jour tous les endroits où il est inclus.

3. **Simplifie la lecture des templates**
- Un gros template est découpé en blocs logiques plus petits.

#### Exemple de base :

```django
{# templates/base.html #}
<body>
  {% include "partials/header.html" %}
  <main>{% block content %}{% endblock %}</main>
  {% include "partials/footer.html" %}
</body>
```

#### Passage de contexte à `include` :

```django
{% include "partials/user_badge.html" with user=request.user %}
```

Limiter le contexte aux seules variables transmises :

```django
{% include "partials/user_badge.html" with user=request.user only %}
```

#### Cas d’usage :

- Composant de pagination.
- Ligne de tableau / carte produit.
- Bloc d’alertes/messages.
- Éléments communs de layout.

#### Différence entre `extends` et `include` :

- `extends` : héritage de structure globale (niveau layout).
- `include` : insertion d’un fragment local (niveau composant).

#### Erreurs typiques :

1. Utiliser `include` à la place de `extends` pour le layout global.
2. Passer un contexte implicite trop large.
3. Mettre de la logique lourde dans un partial.

#### Conclusion :

`{% include %}` est un outil fondamental de modularité des templates Django.
Utilise-le pour de petits fragments réutilisables, et `extends` pour la structure globale.

</details>

<details>
<summary>28. Que sont les template partials et comment fonctionnent `{% partial %}` et `{% partialdef %}` ?</summary>

#### Django

Les template partials permettent de définir et réutiliser des fragments
à l’intérieur d’un template. On utilise `{% partialdef %}` (définition)
et `{% partial %}` (appel).

#### Fonctionnement :

1. **`{% partialdef name %}...{% endpartialdef %}`**
- Définit un fragment partial nommé.

2. **`{% partial name %}`**
- Rend ce partial à l’endroit voulu.

#### Exemple de base :

```django
{% partialdef product_card %}
  <article class="card">
    <h3>{{ product.title }}</h3>
    <p>{{ product.price }} грн</p>
  </article>
{% endpartialdef %}

<section class="grid">
  {% for product in products %}
    {% partial product_card %}
  {% endfor %}
</section>
```

#### Différence avec `{% include %}` :

- `include` charge un fichier séparé.
- `partial/partialdef` permet de définir/appeler un fragment dans le template courant,
  sans créer de fichier distinct.

#### Quand c’est utile :

1. Réutiliser rapidement un petit fragment dans un même template.
2. Éviter de découper en trop de micro-fichiers include.
3. Gérer des blocs UI locaux sans intérêt à externaliser.

#### Recommandations pratiques :

1. Pour composants réutilisés globalement : préférer `{% include %}`.
2. Pour petits fragments locaux : `partial/partialdef`.
3. Éviter d’y mettre de la logique métier ; rester au niveau présentation.

#### Compatibilité :

- Dans les versions récentes de Django, ces tags peuvent être disponibles via le système de templates.
- Sur versions plus anciennes, on couvre souvent le besoin via `{% include %}`
  et des template tags custom.

#### Conclusion :

`{% partialdef %}` et `{% partial %}` sont des outils de composition locale :
moins de duplication, meilleure lisibilité et structure UI plus maîtrisée.

</details>

<details>
<summary>29. Que sont les template tags et les filters ?</summary>

#### Django

Les `template tags` et `filters` sont des outils du moteur de templates Django
pour contrôler le rendu des données.

#### Template tags :

- Les tags exécutent de la logique au niveau template.
- Syntaxe : `{% ... %}`.

Tags intégrés fréquents :

1. `{% if %}` / `{% elif %}` / `{% else %}`
2. `{% for %}`
3. `{% url %}`
4. `{% include %}`
5. `{% csrf_token %}`
6. `{% static %}`

Exemple :

```django
{% if user.is_authenticated %}
  <a href="{% url 'profile' %}">Profil</a>
{% else %}
  <a href="{% url 'login' %}">Se connecter</a>
{% endif %}
```

#### Filters :

- Les filters transforment la valeur des variables.
- Syntaxe : `|` dans `{{ ... }}`.

Filters intégrés fréquents :

1. `|lower`, `|upper`, `|title`
2. `|length`
3. `|date:"d.m.Y"`
4. `|default:"-"`, `|default_if_none:"-"`
5. `|truncatechars:50`
6. `|safe` (avec prudence)

Exemple :

```django
<p>{{ article.title|title }}</p>
<p>{{ article.created_at|date:"d.m.Y H:i" }}</p>
<p>{{ article.description|truncatechars:120 }}</p>
```

#### Créer un filter custom :

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

#### Créer un simple tag custom :

```python
@register.simple_tag
def app_version():
    return "1.0.0"
```

```django
{% load text_extras %}
<small>v{% app_version %}</small>
```

#### Règles pratiques :

1. Garder les templates « fins » : peu de logique, lisibilité élevée.
2. Extraire la logique de présentation répétitive en filters/tags custom.
3. Ne pas déplacer la logique métier dans les template tags.
4. Utiliser `|safe` uniquement pour du contenu fiable.

#### Conclusion :

Les template tags pilotent la structure du rendu, les filters formatent les valeurs.
Ensemble, ils permettent de construire une UI Django flexible et sûre.

</details>

<details>
<summary>30. Comment connecter les fichiers statiques (static) et que fait collectstatic ?</summary>

#### Django

Les fichiers statiques (`static`) sont les CSS, JS, images, polices et autres
ressources non générées dynamiquement à chaque requête.

#### Réglages de base dans `settings.py` :

```python
STATIC_URL = "/static/"
STATIC_ROOT = BASE_DIR / "staticfiles"   # build production
```

Si besoin de dossiers supplémentaires :

```python
STATICFILES_DIRS = [BASE_DIR / "static"]
```

#### Connecter static dans un template :

```django
{% load static %}
<link rel="stylesheet" href="{% static 'css/main.css' %}">
<script src="{% static 'js/app.js' %}"></script>
<img src="{% static 'img/logo.svg' %}" alt="Logo">
```

#### Où stocker les static :

1. Dans chaque app :
- `app_name/static/app_name/...`

2. Ou dans un dossier partagé du projet :
- `project_root/static/...`

#### Que fait `collectstatic` :

Commande :

```bash
python manage.py collectstatic
```

Résultat :

1. Récupère tous les fichiers static des apps et de `STATICFILES_DIRS`.
2. Les copie dans un répertoire unique `STATIC_ROOT`.
3. Prépare l’ensemble que le serveur web/CDN sert en production.

#### Dev vs Production :

1. **Développement (`DEBUG=True`)**
- Django peut servir les static lui-même.

2. **Production (`DEBUG=False`)**
- Les static sont en général servis par Nginx, CDN ou object storage.
- Le process Django ne doit pas les servir directement.

#### Pratiques production courantes :

- `ManifestStaticFilesStorage` pour fichiers versionnés/hashés (cache busting).
- WhiteNoise pour déploiement simple sans Nginx séparé.
- CDN pour distribution rapide des assets statiques.

#### Erreurs typiques :

1. Ne pas lancer `collectstatic` avant déploiement.
2. Hardcoder des chemins `/static/...` sans `{% static %}`.
3. Confondre `static` (assets) et `media` (uploads utilisateurs).
4. Oublier `STATIC_ROOT` en production.

#### Conclusion :

L’usage des static dans Django repose sur `{% static %}` et des settings corrects.
`collectstatic` est une étape obligatoire du build production pour unifier les
ressources statiques et les servir de façon stable et rapide.

</details>

<details>
<summary>31. Que sont MEDIA_ROOT et MEDIA_URL ?</summary>

#### Django

`MEDIA_ROOT` et `MEDIA_URL` sont utilisés pour gérer les fichiers téléversés
par les utilisateurs (uploads) : avatars, documents, photos, vidéos, etc.

#### Qu’est-ce que `MEDIA_ROOT` :

- Chemin absolu sur le système de fichiers du serveur où les uploads sont stockés.
- C’est le « disque » où Django écrit les fichiers de `FileField`/`ImageField`.

#### Qu’est-ce que `MEDIA_URL` :

- Préfixe URL par lequel ces fichiers sont accessibles depuis le navigateur.
- C’est le « chemin public » vers le contenu de `MEDIA_ROOT`.

#### Configuration de base :

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Exemple de modèle :

```python
from django.db import models

class Profile(models.Model):
    avatar = models.ImageField(upload_to="avatars/")
```

Si l’utilisateur charge `photo.jpg`, le fichier sera :

- Sur disque : `MEDIA_ROOT/avatars/photo.jpg`
- En URL : `MEDIA_URL + "avatars/photo.jpg"` -> `/media/avatars/photo.jpg`

#### Configuration URL en développement :

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

#### Approche production :

1. Django stocke le fichier (localement ou via backend cloud storage).
2. Le service des fichiers est assuré par Nginx/CDN/S3, pas par le process Django.
3. L’accès se contrôle via permissions ou pre-signed URL (fichiers privés).

#### Différence importante entre `static` et `media` :

- `static` : fichiers du développeur (CSS/JS/logo), collectés via `collectstatic`.
- `media` : fichiers utilisateurs, non traités par `collectstatic`.

#### Erreurs typiques :

1. Mélanger `STATIC_ROOT` et `MEDIA_ROOT`.
2. Stocker les uploads utilisateurs dans le dépôt git.
3. Servir media via Django en production sans besoin.
4. Ne pas valider type/taille des fichiers uploadés.

#### Conclusion :

`MEDIA_ROOT` = où le fichier est stocké physiquement, `MEDIA_URL` = comment le
client y accède. La séparation claire media/static est un standard obligatoire
pour les projets Django.

</details>

<details>
<summary>32. Quelles sont les approches de cache pour les templates ?</summary>

#### Django

Le cache de templates dans Django réduit la charge CPU/BD et accélère les pages
en réutilisant du contenu déjà rendu.

#### Approches principales :

1. **Template fragment caching (recommandé pour parties de page)**
- Met en cache uniquement un fragment, pas toute la page.

```django
{% load cache %}
{% cache 300 sidebar user.id %}
  {# bloc lourd : menu, recommandations, widgets #}
  ...
{% endcache %}
```

2. **Per-view caching**
- Met en cache la réponse complète d’une view pendant un TTL donné.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)  # 5 min
def article_list(request):
    ...
```

3. **Site-wide caching (middleware)**
- Met en cache presque tout le site selon des règles globales.
- Adapté aux sites de contenu peu personnalisés.

4. **Low-level cache API**
- Mise en cache de résultats de requêtes/calculs dans le code Python.

```python
from django.core.cache import cache

data = cache.get("popular_articles")
if data is None:
    data = expensive_query()
    cache.set("popular_articles", data, 300)
```

#### Configuration backend cache :

En production on utilise généralement Redis ou Memcached :

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Que choisir selon le besoin :

- Fragments UI coûteux -> template fragment cache.
- Page publique stable -> per-view cache.
- Site principalement statique -> site-wide cache.
- Logique métier/requêtes coûteuses -> low-level cache API.

#### Règles pratiques :

1. Commencer par un cache peu agressif (fragments), puis étendre.
2. Choisir TTL selon les exigences de fraîcheur métier.
3. Pour contenu personnalisé, ajouter des clés (user id, locale, permissions).
4. Prévoir l’invalidation après modifications de données.

#### Erreurs typiques :

1. Cacher du contenu personnalisé sans clé utilisateur.
2. Oublier l’invalidation après update/delete.
3. TTL trop long pour données dynamiques.
4. Considérer le cache comme « solution » à des requêtes SQL inefficaces.

#### Conclusion :

Le point de départ le plus sûr dans Django : fragment caching + Redis. Ensuite,
ajouter per-view ou site-wide cache selon le profil de charge et les exigences UX.

</details>

<details>
<summary>33. Que sont Django Forms et ModelForm ?</summary>

#### Django

`Django Forms` est le mécanisme de traitement des formulaires HTML : validation,
nettoyage des données, rendu des champs et gestion des erreurs.
`ModelForm` est un type spécial de formulaire construit automatiquement à partir
d’un modèle Django.

#### Django Form :

- Défini via `forms.Form`.
- Champs décrits manuellement.
- Adapté aux formulaires non liés directement à un modèle.

Exemple :

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.CharField(widget=forms.Textarea)
```

#### ModelForm :

- Défini via `forms.ModelForm`.
- Champs générés depuis le modèle.
- Sauvegarde en BD simple via `form.save()`.

Exemple :

```python
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ["title", "content", "is_published"]
```

#### Différences principales :

1. **Source des champs**
- Form : champs définis manuellement.
- ModelForm : champs issus du modèle.

2. **Sauvegarde des données**
- Form : traitement et sauvegarde manuels.
- ModelForm : `form.save()` prêt à l’emploi.

3. **Cas d’usage**
- Form : contact, recherche, filtres, login/reset, formulaires d’intégration.
- ModelForm : CRUD de modèles, interfaces type admin.

#### Exemple de traitement dans une view :

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

#### Avantages généraux de Django Forms :

- Validation serveur centralisée.
- Protection contre erreurs de saisie et types invalides.
- Gestion pratique des messages d’erreur.
- Intégration simple avec templates.

#### Conclusion :

Utiliser `Form` pour scénarios custom sans modèle direct.
`ModelForm` est la voie la plus rapide et la plus propre pour du CRUD sur des
modèles Django.

</details>

<details>
<summary>34. Quelle est la différence entre un formulaire HTML et un formulaire Django ?</summary>

#### Django

Un formulaire HTML et un formulaire Django répondent au même besoin (saisie de
données), mais à des niveaux différents. Le formulaire HTML n’est que du markup
côté navigateur, alors que le formulaire Django est un mécanisme serveur de
validation et de traitement.

#### Formulaire HTML :

- Décrit les champs, boutons, `method`, `action`.
- Fonctionne côté client (navigateur).
- Ne garantit ni sécurité ni validité serveur.

Exemple :

```html
<form method="post" action="/contact/">
  <input type="text" name="name" />
  <input type="email" name="email" />
  <button type="submit">Envoyer</button>
</form>
```

#### Formulaire Django :

- Défini en Python (`forms.Form` ou `forms.ModelForm`).
- Réalise validation serveur, nettoyage (`cleaned_data`), gestion d’erreurs.
- S’intègre facilement aux templates et à la protection CSRF.

Exemple :

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
```

#### Différences clés :

1. **Niveau**
- HTML form : couche présentation.
- Django form : couche validation backend.

2. **Validation**
- HTML : validation client basique (contournable).
- Django Form : validation serveur obligatoire et fiable.

3. **Sécurité**
- HTML seul ne protège pas contre requêtes forgées.
- Django form fonctionne avec `{% csrf_token %}` et gestion d’erreurs intégrée.

4. **Maintenabilité**
- Approche HTML-only = duplication fréquente des règles.
- Django form centralise les règles et simplifie la maintenance.

5. **Travail avec modèles**
- HTML : sauvegarde manuelle.
- ModelForm : `form.save()` prêt à l’emploi.

#### Règle pratique :

En production, ne jamais se reposer uniquement sur la validation HTML.
Validation client = UX, validation Django = sûreté et correction.

#### Conclusion :

Le formulaire HTML gère l’interface, le formulaire Django garantit la qualité
des données côté serveur. En pratique, les deux sont complémentaires, mais la
validation critique doit toujours être côté backend.

</details>

<details>
<summary>35. Comment rendre des formulaires dans un template ?</summary>

#### Django

Dans Django, les formulaires se rendent dans les templates via l’objet `form`
passé depuis la view. On peut utiliser un rendu automatique rapide ou un rendu
manuel plus contrôlé.

#### 1. Rendu automatique rapide :

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Enregistrer</button>
</form>
```

Variantes disponibles :

- `{{ form.as_p }}` - champs dans des balises `<p>`
- `{{ form.as_ul }}` - champs en liste `<li>`
- `{{ form.as_table }}` - champs en tableau

#### 2. Rendu manuel (recommandé pour UI production) :

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

  <button type="submit">Enregistrer</button>
</form>
```

#### Éléments obligatoires :

1. `{% csrf_token %}` pour formulaires POST.
2. Affichage des erreurs de champs (`field.errors`) et globales (`non_field_errors`).
3. `enctype="multipart/form-data"` pour formulaires avec fichiers.

#### Exemple upload :

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Téléverser</button>
</form>
```

#### Recommandations pratiques :

1. Pour MVP, commencer avec `form.as_p`.
2. Pour produit réel, préférer rendu manuel pour un contrôle UX/UI complet.
3. Ne pas cacher les erreurs ; les afficher près des champs concernés.
4. Utiliser des actions de bouton explicites et un submit-flow clair.

#### Conclusion :

Le rendu des formulaires Django peut être très rapide ou très contrôlé. Pour une
qualité production, on choisit généralement le rendu manuel avec erreurs visibles,
protection CSRF et mise en page maîtrisée.

</details>

<details>
<summary>36. Comment fonctionne la validation des formulaires et comment créer la vôtre ?</summary>

#### Django

La validation des formulaires Django se fait côté serveur lors de `form.is_valid()`.
Ensuite, Django renvoie soit les données nettoyées (`cleaned_data`), soit remplit
`form.errors`.

#### Validation étape par étape :

1. Django valide types et règles de base (`required`, `max_length`, `EmailField`, etc.).
2. Exécute les validateurs custom de champ (si définis).
3. Appelle `clean_<field>()` pour chaque champ concerné.
4. Appelle `clean()` pour la logique inter-champs.
5. Produit `cleaned_data` ou la liste d’erreurs.

#### Validation d’un champ (`clean_<field>()`) :

```python
from django import forms
from django.core.exceptions import ValidationError

class RegisterForm(forms.Form):
    username = forms.CharField(max_length=50)

    def clean_username(self):
        value = self.cleaned_data["username"].strip()
        if "admin" in value.lower():
            raise ValidationError("Le nom contient un mot interdit.")
        return value
```

#### Validation inter-champs (`clean()`) :

```python
class PasswordForm(forms.Form):
    password = forms.CharField(widget=forms.PasswordInput)
    confirm_password = forms.CharField(widget=forms.PasswordInput)

    def clean(self):
        cleaned_data = super().clean()
        p1 = cleaned_data.get("password")
        p2 = cleaned_data.get("confirm_password")

        if p1 and p2 and p1 != p2:
            raise forms.ValidationError("Les mots de passe ne correspondent pas.")
        return cleaned_data
```

#### Validateurs custom :

```python
from django.core.exceptions import ValidationError

def validate_company_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Seul l’email d’entreprise est autorisé.")
```

```python
email = forms.EmailField(validators=[validate_company_email])
```

#### Pour `ModelForm` :

- Validation du formulaire + validation du modèle.
- Dans le modèle, on peut aussi utiliser `clean()`, `unique=True`,
  `UniqueConstraint`, `validators`.

#### Traitement dans une view :

```python
def submit_form(request):
    form = RegisterForm(request.POST or None)
    if request.method == "POST" and form.is_valid():
        # utiliser form.cleaned_data
        ...
    return render(request, "form.html", {"form": form})
```

#### Règles pratiques :

1. Validation serveur obligatoire (client = UX seulement).
2. Logique locale de champ -> `clean_<field>()`.
3. Logique multi-champs -> `clean()`.
4. Règles réutilisables -> validateurs dédiés.
5. Règles métier critiques à doubler au niveau BD (constraints).

#### Conclusion :

La force de Django Forms est la validation structurée à plusieurs niveaux.
Résultat : qualité des données, erreurs claires, flux backend stable en production.

</details>

<details>
<summary>37. Que sont les validateurs custom dans Django et comment les réutiliser ?</summary>

#### Django

Les validateurs custom Django sont des fonctions ou classes qui vérifient une
valeur et lèvent `ValidationError` si la règle n’est pas respectée.

#### Pourquoi les utiliser :

1. **Réutilisation des règles**
- Une même validation dans plusieurs forms/models.

2. **Source unique de vérité**
- La règle métier n’est pas dupliquée partout.

3. **Architecture plus propre**
- La logique de validation sort de view/forms vers une couche dédiée.

#### Exemple de validateur fonctionnel :

```python
from django.core.exceptions import ValidationError

def validate_corporate_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Seul l’email d’entreprise est autorisé.")
```

Usage dans un modèle :

```python
from django.db import models
from .validators import validate_corporate_email

class Employee(models.Model):
    email = models.EmailField(validators=[validate_corporate_email])
```

Usage dans un formulaire :

```python
from django import forms
from .validators import validate_corporate_email

class InviteForm(forms.Form):
    email = forms.EmailField(validators=[validate_corporate_email])
```

#### Exemple de validateur class-based :

```python
from django.core.exceptions import ValidationError

class MinWordsValidator:
    def __init__(self, min_words=3):
        self.min_words = min_words

    def __call__(self, value):
        if len(value.split()) < self.min_words:
            raise ValidationError(f"Minimum {self.min_words} mot(s).")
```

```python
description = models.TextField(validators=[MinWordsValidator(5)])
```

#### Où les placer :

- `app/validators.py` ou `app/domain/validators.py`
- En grand projet : modules séparés par domaine.

#### Règles pratiques :

1. Un validateur = une vérification claire.
2. Messages d’erreur compréhensibles côté utilisateur.
3. Règles critiques doublées au niveau BD (`UniqueConstraint`, check constraints).
4. Tests unitaires dédiés aux validateurs.

#### Conclusion :

Les validateurs custom centralisent correctement les règles métier de validation.
Le code devient plus propre, réutilisable et cohérent.

</details>

<details>
<summary>38. Comment gérer l’upload de fichiers ?</summary>

#### Django

L’upload de fichiers dans Django passe par `request.FILES`, les champs
`FileField`/`ImageField`, et la config correcte de `MEDIA_ROOT`/`MEDIA_URL`.

#### Pré-requis upload :

1. Un champ fichier dans form ou modèle.
2. `enctype="multipart/form-data"` dans le formulaire HTML.
3. Passage de `request.FILES` au formulaire.
4. Paramètres media configurés dans `settings.py`.

#### Exemple de modèle :

```python
from django.db import models

class Document(models.Model):
    title = models.CharField(max_length=200)
    file = models.FileField(upload_to="documents/%Y/%m/")
```

#### Exemple ModelForm :

```python
from django import forms
from .models import Document

class DocumentForm(forms.ModelForm):
    class Meta:
        model = Document
        fields = ["title", "file"]
```

#### Exemple de view :

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

#### Template :

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Téléverser</button>
</form>
```

#### Configuration media :

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Sécurité et bonnes pratiques production :

1. Valider type, taille, extension du fichier.
2. Ne pas faire confiance au nom de fichier client.
3. Restreindre l’accès aux fichiers privés via permissions.
4. En production, préférer stockage externe (S3-compatible) ou serveur fichiers dédié.
5. Scanner les fichiers potentiellement risqués si nécessaire.

#### Erreurs typiques :

1. Oublier `enctype="multipart/form-data"` -> `request.FILES` vide.
2. Passer uniquement `request.POST` sans `request.FILES`.
3. Confondre static et media.
4. Ne pas valider type/taille -> risque sécurité/perf.

#### Conclusion :

L’upload Django est fiable si on respecte les bases : bon formulaire,
`request.FILES`, validateurs et contrôle d’accès en production.

</details>

<details>
<summary>39. Qu’est-ce que Django ORM ?</summary>

#### Django

Django ORM (Object-Relational Mapping) est la couche d’accès aux données qui
permet de manipuler la base via des objets Python plutôt qu’écrire du SQL à la main
dans la majorité des cas.

#### Idée de base :

1. **Modèle Python = table BD**
2. **Instance modèle = ligne**
3. **Champ modèle = colonne**
4. **QuerySet = requête(s) SQL générées par l’ORM**

#### Exemple :

```python
# models.py
class Article(models.Model):
    title = models.CharField(max_length=200)
    is_published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

```python
# création
Article.objects.create(title="Django ORM", is_published=True)

# lecture
articles = Article.objects.filter(is_published=True).order_by("-created_at")

# mise à jour
article = Article.objects.get(pk=1)
article.title = "Updated title"
article.save()

# suppression
article.delete()
```

#### Avantages ORM Django :

1. **Développement rapide** - moins de SQL boilerplate.
2. **Code lisible** - requêtes déclaratives.
3. **Sécurité** - requêtes paramétrées, risque SQL injection réduit.
4. **Portabilité** - même code pour plusieurs SGBD (dans la plupart des cas).
5. **Intégration Django** - forms, admin, migrations, validateurs.

#### Concepts importants :

- `QuerySet` est lazy : la requête part seulement quand les données sont nécessaires.
- `select_related` et `prefetch_related` aident à éviter le N+1.
- `annotate`, `aggregate`, `F`, `Q`, `Subquery` pour requêtes plus avancées.

#### Limites ORM :

1. SQL très complexe parfois plus clair en raw SQL.
2. Sans profiling, on peut créer des requêtes inefficaces.
3. Mauvaise gestion des relations -> gros impact perf.

#### Quand utiliser raw SQL :

- Optimisations spécifiques à un SGBD.
- Analytique complexe/CTE/window functions si ORM devient illisible.
- Tâches migration/opérations nécessitant contrôle SQL précis.

#### Conclusion :

Django ORM est un des grands atouts du framework : rapide, sûr et pratique pour
la plupart des besoins métier. En production, il faut comprendre ce qu’il génère
et optimiser à temps.

</details>

<details>
<summary>40. Qu’est-ce qu’un modèle et comment le créer ?</summary>

#### Django

Un modèle (`Model`) dans Django est une classe Python qui décrit la structure des données et correspond à une table en base. C’est via le modèle qu’on définit
champs, relations et règles de données.

#### Qu’est-ce qu’un modèle :

1. **Description du schéma BD en Python**
- Les champs (`CharField`, `IntegerField`, `DateTimeField`...) correspondent
  aux colonnes.

2. **Couche d’entités métier**
- Le modèle représente un objet métier : `User`, `Order`, `Invoice`, `Product`.

3. **Intégration ORM**
- Création, lecture, mise à jour, suppression via `Model.objects`.

#### Exemple de modèle :

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

#### Création d’un modèle étape par étape :

1. Ajouter la classe dans `app/models.py`.
2. Vérifier que l’app est dans `INSTALLED_APPS`.
3. Créer la migration :

```bash
python manage.py makemigrations
```

4. Appliquer la migration :

```bash
python manage.py migrate
```

#### Bonnes pratiques :

1. Noms de champs clairs et contraintes utiles (`unique`, `db_index`).
2. Ajouter `created_at`, `updated_at`.
3. Définir `__str__` pour lisibilité admin/shell.
4. Fixer invariants métier au niveau BD (constraints), pas seulement dans view/forms.

#### Erreurs typiques :

1. Tout stocker en texte en ignorant les types.
2. Oublier les index sur champs de filtre/recherche.
3. Mettre de la logique métier haut niveau dans le modèle sans structure.
4. Migrations non synchronisées entre environnements.

#### Conclusion :

Le modèle Django est la base du système de données. Des modèles bien conçus
conditionnent performance, fiabilité et scalabilité du projet.

</details>

<details>
<summary>41. Que sont ForeignKey, OneToOneField et ManyToManyField ?</summary>

#### Django

`ForeignKey`, `OneToOneField` et `ManyToManyField` sont les types de relations
entre modèles dans Django ORM. Ils définissent comment les entités sont liées
en base de données.

#### 1. ForeignKey (un-à-plusieurs, 1:N)

- Un objet « parent » peut avoir plusieurs objets « enfants ».
- Chaque enregistrement enfant pointe vers un seul parent.

Exemple :

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Cas : un auteur -> plusieurs livres.

#### 2. OneToOneField (un-à-un, 1:1)

- À chaque enregistrement de A correspond au plus un enregistrement de B.
- C’est essentiellement un `ForeignKey(unique=True)` avec une sémantique claire.

Exemple :

```python
from django.conf import settings

class Profile(models.Model):
    user = models.OneToOneField(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    bio = models.TextField(blank=True)
```

Cas : un utilisateur -> un profil.

#### 3. ManyToManyField (plusieurs-à-plusieurs, M:N)

- Les enregistrements des deux tables peuvent être liés à plusieurs éléments.
- Django crée automatiquement une table intermédiaire (ou via `through=`).

Exemple :

```python
class Tag(models.Model):
    name = models.CharField(max_length=50, unique=True)

class Article(models.Model):
    title = models.CharField(max_length=200)
    tags = models.ManyToManyField(Tag, related_name="articles")
```

Cas : un article a plusieurs tags, un tag appartient à plusieurs articles.

#### Comment choisir :

1. `ForeignKey` - quand il y a un propriétaire clair et plusieurs enfants.
2. `OneToOneField` - quand l’entité d’extension doit exister en un seul exemplaire.
3. `ManyToManyField` - quand les deux côtés ont plusieurs correspondances.

#### Nuance `on_delete` pour ForeignKey/OneToOne :

- `CASCADE` - supprime les enfants avec le parent.
- `PROTECT` - bloque la suppression si dépendances.
- `SET_NULL` - met la référence à NULL (`null=True` requis).

#### Conclusion :

Ces trois champs sont la base de la modélisation relationnelle dans Django.
Un bon choix de relation simplifie requêtes, migrations et maintenance long terme.

</details>

<details>
<summary>42. Quels types d’héritage de modèles existent ?</summary>

#### Django

Dans Django, il existe trois types principaux d’héritage de modèles :
**Abstract Base Classes**, **Multi-table inheritance** et **Proxy models**.
Ils répondent à des besoins différents et ont un impact différent sur le schéma BD.

#### 1. Abstract Base Class (héritage abstrait)

- Le modèle parent ne crée pas sa propre table en BD.
- Ses champs sont copiés dans les modèles enfants.

Exemple :

```python
class TimeStampedModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True

class Article(TimeStampedModel):
    title = models.CharField(max_length=200)
```

Quand l’utiliser :

- Pour des champs/méthodes communs à plusieurs modèles.
- Variante la plus fréquente et pratique en production.

#### 2. Multi-table inheritance (table séparée par niveau)

- Chaque modèle de la hiérarchie a sa propre table.
- Django crée un lien `OneToOne` entre parent et enfant.

Exemple :

```python
class Person(models.Model):
    name = models.CharField(max_length=120)

class Employee(Person):
    salary = models.DecimalField(max_digits=10, decimal_places=2)
```

Quand l’utiliser :

- Quand une vraie hiérarchie d’entités est nécessaire en BD.
- Quand il faut des tables distinctes pour base et spécialisation.

Inconvénient :

- JOIN supplémentaires et requêtes plus complexes.

#### 3. Proxy model

- Ne crée pas de nouvelle table.
- Utilise la même table que le modèle de base.
- Permet de changer le comportement Python (méthodes, manager, ordering)
  sans changer le schéma BD.

Exemple :

```python
class Order(models.Model):
    status = models.CharField(max_length=20)

class OpenOrder(Order):
    class Meta:
        proxy = True
        ordering = ["id"]
```

Quand l’utiliser :

- Besoin d’un manager/comportement différent pour la même table.
- Besoin d’un affichage admin différent sans changer la structure.

#### Choix rapide :

1. Champs communs sans table dédiée -> **abstract**.
2. Hiérarchie physique avec tables séparées -> **multi-table**.
3. Comportement Python différent sans changer BD -> **proxy**.

#### Conseil pratique :

Par défaut, privilégier **abstract base class**.
`multi-table` doit être utilisé avec prudence, uniquement si le domaine l’exige.

#### Conclusion :

On choisit le type d’héritage selon l’objectif : réutiliser des champs,
modéliser une hiérarchie physique, ou changer seulement le comportement.
Le bon choix simplifie la BD et la maintenance future.

</details>

<details>
<summary>43. À quoi sert la classe Meta ?</summary>

#### Django

La classe interne `Meta` d’un modèle Django sert à configurer le comportement
ORM et BD du modèle, sans toucher à la logique métier du modèle lui-même.

#### Ce qu’on définit souvent dans `Meta` :

1. `ordering` - tri par défaut.
2. `db_table` - nom de table custom en BD.
3. `verbose_name`, `verbose_name_plural` - noms lisibles en admin.
4. `indexes` - index pour performance.
5. `constraints` - règles métier au niveau BD.
6. `unique_together` / `UniqueConstraint` - unicité de combinaisons de champs.
7. `abstract` / `proxy` - type d’héritage du modèle.

#### Exemple :

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
        verbose_name = "Produit"
        verbose_name_plural = "Produits"
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

#### Pourquoi `Meta` est important :

1. **Performance**
- Index et contraintes adaptés réduisent le coût des requêtes.

2. **Intégrité des données**
- Les constraints évitent les données invalides même si une validation est manquée.

3. **Schéma maîtrisé**
- Contrôle explicite des tables et règles dans les migrations.

4. **Admin plus ergonomique**
- Noms lisibles pour le back-office.

#### Recommandations pratiques :

1. Utiliser `UniqueConstraint` plutôt que `unique_together` (ancien style).
2. Ajouter des index seulement sur champs réellement « chauds ».
3. Mettre les règles critiques au niveau BD via `constraints`.
4. Éviter l’abus de `db_table` sans besoin réel.

#### Conclusion :

`Meta` est le centre de configuration ORM du modèle. C’est là qu’on pilote tri,
index, contraintes et qualité du schéma BD, avec impact direct sur fiabilité
et performance du projet Django.

</details>

<details>
<summary>44. Quelle est la différence entre null=True et blank=True ?</summary>

#### Django

`null=True` et `blank=True` répondent à des besoins différents et opèrent à
des niveaux différents :

- `null=True` - niveau **base de données** (NULL autorisé en colonne).
- `blank=True` - niveau **validation formulaires/admin** (champ autorisé vide).

#### `null=True` :

1. Autorise la valeur `NULL` en BD.
2. Impacte le schéma de table et les migrations.
3. Important quand l’absence de valeur doit être un SQL `NULL` réel.

#### `blank=True` :

1. Autorise un champ vide dans forms, ModelForm, Django Admin.
2. Ne modifie pas directement le type de colonne BD.
3. Impacte `form.is_valid()`, pas le stockage SQL.

#### Exemples :

```python
class Profile(models.Model):
    bio = models.TextField(blank=True)  # optionnel en formulaire
    birth_date = models.DateField(null=True, blank=True)  # NULL en BD + vide en form
```

#### Nuance importante pour les champs texte (`CharField`, `TextField`) :

- En Django, on évite généralement `null=True` pour les champs texte.
- Bonne pratique : utiliser chaîne vide `""` plutôt que `NULL`.
- Donc souvent : `CharField(..., blank=True)` sans `null=True`.

#### Matrice rapide :

1. `null=False, blank=False` -> obligatoire en BD et en formulaire.
2. `null=True, blank=False` -> NULL possible en BD, mais formulaire exige valeur.
3. `null=False, blank=True` -> formulaire accepte vide, BD stocke non-NULL (souvent `""`).
4. `null=True, blank=True` -> champ optionnel au maximum.

#### Recommandations pratiques :

1. Pour `DateField`, `DateTimeField`, `ForeignKey`, numériques : souvent
   `null=True, blank=True`.
2. Pour `CharField/TextField` : généralement `blank=True` suffit.
3. Garder une politique cohérente pour éviter chaos `NULL` vs `""`.
4. Un mauvais choix complique filtres et analytique.

#### Conclusion :

`null` contrôle le stockage BD, `blank` la validation côté Django.
Ce sont deux axes distincts à configurer consciemment selon le domaine.

</details>

<details>
<summary>45. Quelle est la différence entre CharField et TextField ?</summary>

#### Django

`CharField` et `TextField` stockent tous deux du texte, mais pour des usages
et contraintes différents au niveau modèle/BD.

#### `CharField` :

1. Conçu pour texte court/moyen.
2. `max_length` est **obligatoire**.
3. Adapté aux champs à longueur contrôlée :
   nom, slug, titre, code, email, téléphone.

Exemple :

```python
title = models.CharField(max_length=200)
sku = models.CharField(max_length=64, unique=True)
```

#### `TextField` :

1. Conçu pour texte long libre.
2. Pas de `max_length` requis au niveau modèle.
3. Adapté aux descriptions, contenu d’articles, notes, commentaires.

Exemple :

```python
description = models.TextField(blank=True)
content = models.TextField()
```

#### Différences clés :

1. **Limite de longueur**
- `CharField` : toujours `max_length`.
- `TextField` : pas de limite stricte par défaut.

2. **Sémantique**
- `CharField` : texte court structuré.
- `TextField` : texte volumineux non structuré.

3. **Forms/admin**
- `CharField` est souvent rendu en `input`.
- `TextField` est souvent rendu en `textarea`.

4. **Indexation/performance**
- Les champs courts indexés sont plus logiques en `CharField`.
- Pour gros textes, indexation dépend SGBD et demande souvent
  une stratégie dédiée (full-text search).

#### Règles pratiques tech lead :

1. Si la valeur a une limite naturelle -> `CharField`.
2. Si le texte peut devenir long/libre -> `TextField`.
3. Éviter `TextField` « au cas où » quand `CharField` suffit.
4. Pour recherche sur gros textes, prévoir stratégie dédiée (PostgreSQL FTS,
   Elasticsearch/OpenSearch, etc.).

#### Conclusion :

`CharField` = texte court contrôlé, `TextField` = contenu long.
Le bon choix impacte validation, UX formulaires, indexation et performance.

</details>

<details>
<summary>46. Que sont les model managers et comment créer le vôtre ?</summary>

#### Django

Un `Model Manager` dans Django est le point d’entrée des requêtes ORM d’un modèle.
Par défaut, chaque modèle a `objects`, mais tu peux créer des managers custom
avec des méthodes orientées domaine.

#### Pourquoi créer des managers custom :

1. **Centraliser la logique de requêtes**
- Éviter de dupliquer les mêmes `filter(...)` dans plusieurs views/services.

2. **API plus lisible pour le modèle**
- Exemple : `Article.objects.published().recent()`.

3. **Contrôler l’ensemble de données par défaut**
- Exemple : masquer les enregistrements soft-deleted.

#### Exemple de manager :

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

Usage :

```python
Article.objects.published()
Article.objects.recent()
```

#### Combo Manager + QuerySet (plus scalable) :

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

#### Recommandations pratiques :

1. Mettre en manager/queryset uniquement la logique de sélection de données.
2. Garder l’orchestration métier dans une couche service.
3. Donner des noms métiers clairs (`active`, `paid`, `for_user`).
4. Éviter les managers « magiques » au comportement implicite.

#### Erreurs typiques :

1. Dupliquer les mêmes filtres partout.
2. Mettre trop de logique métier lourde dans le manager.
3. Redéfinir le manager par défaut au point de casser admin/comportements attendus.

#### Conclusion :

Les model managers sont le bon endroit pour les requêtes ORM réutilisables.
Un manager custom rend le code plus propre et les requêtes plus cohérentes.

</details>

<details>
<summary>47. Que sont les migrations et pourquoi sont-elles nécessaires ?</summary>

#### Django

Les migrations Django sont l’historique versionné des changements de schéma BD,
stocké dans le code du projet et appliqué via `makemigrations` et `migrate`.

#### Ce qu’elles apportent :

1. **Versioning de la BD**
- Changements de tables, champs, index, contraintes enregistrés en fichiers.

2. **Reproductibilité des environnements**
- Dev, staging, prod partagent le même schéma.

3. **Évolution sûre du schéma**
- Process formalisé au lieu de SQL manuel non traçable.

4. **Travail d’équipe**
- Les migrations sont commitées et relues en code review.

#### Fonctionnement :

1. Tu modifies `models.py`.
2. `python manage.py makemigrations` génère un fichier migration.
3. `python manage.py migrate` applique les changements BD.
4. Django enregistre l’état dans `django_migrations`.

#### Exemples de changements via migrations :

- Ajouter/supprimer un champ.
- Changer type de champ.
- Créer un index.
- Ajouter `UniqueConstraint` / `CheckConstraint`.
- Renommer modèle/champ.

#### Data migrations :

Au-delà du schéma, migrations de données (`RunPython`) pour :
- remplir un nouveau champ,
- déplacer des données entre colonnes,
- normaliser les enregistrements existants.

#### Règles pratiques :

1. Committer migrations avec les changements de modèles.
2. Ne pas modifier d’anciennes migrations déjà appliquées en environnements partagés.
3. Tester migrations en staging avant production.
4. Pour grosses tables : rollout backward-compatible (expand/contract).

#### Erreurs typiques :

1. Lancer le code sans migrations à jour.
2. Oublier de commit les fichiers migration.
3. Faire des opérations bloquantes sans plan sur grosses tables.
4. Réécrire migrations appliquées et casser l’historique.

#### Conclusion :

Les migrations sont le système de contrôle de version de la BD dans Django.
Elles sont critiques pour des déploiements fiables et une évolution maîtrisée.

</details>

<details>
<summary>48. Quelle différence entre makemigrations et migrate ?</summary>

#### Django

`makemigrations` et `migrate` représentent deux phases différentes :

- `makemigrations` **crée** les fichiers migration (plan de changement).
- `migrate` **applique** ces changements à la base de données.

#### `makemigrations` :

1. Analyse les changements de `models.py`.
2. Génère des fichiers Python dans `app/migrations/`.
3. Ne modifie pas la BD directement.

Commande :

```bash
python manage.py makemigrations
```

#### `migrate` :

1. Lit les fichiers migration.
2. Exécute les opérations SQL en BD (CREATE/ALTER/DROP, etc.).
3. Marque les migrations appliquées dans `django_migrations`.

Commande :

```bash
python manage.py migrate
```

#### Workflow simple :

1. Modifier les modèles.
2. Lancer `makemigrations`.
3. Vérifier la migration générée.
4. Lancer `migrate`.
5. Committer code + migrations.

#### Analogie :

- `makemigrations` = écrire l’instruction.
- `migrate` = exécuter l’instruction.

#### Commandes utiles :

```bash
python manage.py showmigrations
python manage.py sqlmigrate app_name 0001
```

- `showmigrations` : migrations appliquées ou non.
- `sqlmigrate` : SQL qui sera exécuté.

#### Erreurs typiques :

1. Lancer `migrate` sans créer migrations après changement de modèles.
2. Faire `makemigrations` puis oublier de commit.
3. Confondre état local BD et état staging/prod.
4. Ignorer les conflits de migrations en équipe.

#### Conclusion :

`makemigrations` prépare, `migrate` applique. Les deux étapes sont indispensables
pour un processus de déploiement stable.

</details>

<details>
<summary>49. Comment connecter PostgreSQL ou une autre BD ?</summary>

#### Django

La connexion BD dans Django se configure via `DATABASES` dans `settings.py`.
En production, PostgreSQL est le choix principal dans la plupart des cas.

#### 1. Installer le driver BD

Pour PostgreSQL (option moderne recommandée) :

```bash
pip install psycopg[binary]
```

Alternative : `psycopg2-binary`.

#### 2. Configurer `DATABASES` dans `settings.py`

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

#### 3. Lancer les migrations

```bash
python manage.py migrate
```

#### Configuration via variables d’environnement (recommandé) :

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

#### Autres moteurs supportés :

1. SQLite (par défaut local/prototype)
2. PostgreSQL (choix production principal)
3. MySQL / MariaDB
4. Oracle

#### Recommandations production :

1. Ne pas stocker les mots de passe BD dans le repo.
2. Activer SSL vers la BD si applicable.
3. Configurer pooling de connexions (PgBouncer ou côté BD).
4. Ajouter health-check et monitoring (latency/locks/slow queries).
5. Utiliser des rôles d’accès à privilèges minimaux.

#### Erreurs typiques :

1. Mauvais `ENGINE` ou driver absent.
2. Config OK en local mais KO en CI/prod à cause des env vars.
3. SQLite en production sous charge concurrente.
4. Pas de timeout/pooling sous charge.

#### Conclusion :

Pour connecter PostgreSQL dans Django : driver, `DATABASES`, migrations.
En production : env config, credentials sûrs, SSL et monitoring sont essentiels.

</details>

<details>
<summary>50. Qu’est-ce qu’un QuerySet ? L’évaluation lazy ?</summary>

#### Django

Un `QuerySet` dans Django ORM est un objet qui représente un ensemble d’enregistrements
et une chaîne d’opérations (`filter`, `exclude`, `order_by`, `annotate`, etc.).

#### Points clés :

1. Il est **lazy** par défaut.
2. Construire un QuerySet n’exécute pas SQL immédiatement.
3. SQL s’exécute seulement quand les données sont réellement demandées.

#### Exemple de lazy :

```python
qs = Article.objects.filter(is_published=True).order_by("-created_at")
# À ce stade, la requête BD n’a PAS encore été exécutée
```

#### Quand SQL est exécuté (materialization) :

1. Itération :

```python
for article in qs:
    ...
```

2. Conversion en liste :

```python
items = list(qs)
```

3. Longueur / booléen :

```python
len(qs)
bool(qs)
```

4. Appels comme :
- `first()`, `last()`, `exists()`, `count()`, `get()`
- slicing (`qs[:10]`, souvent avec `LIMIT/OFFSET`)

#### Avantages du lazy evaluation :

1. **Optimisation des requêtes**
- Composer une requête complexe avant exécution.

2. **Flexibilité**
- Réutiliser un queryset de base avec différentes conditions.

3. **Moins d’accès BD inutiles**
- Si le queryset n’est jamais consommé, aucune requête n’est lancée.

#### Erreurs typiques :

1. Utiliser des querysets en boucle et créer du N+1.
2. Itérer plusieurs fois le même queryset sans matérialiser en liste.
3. Confondre `count()` et `len(qs)` (coût/comportement différents).

#### Conseils pratiques :

1. Utiliser `select_related()` / `prefetch_related()` pour les relations.
2. Si résultat utilisé plusieurs fois dans un flux : `items = list(qs)`.
3. Pour simple existence : `exists()` plutôt qu’itération complète.
4. Profiler le SQL (Debug Toolbar, logs BD) au lieu d’intuition.

#### Conclusion :

`QuerySet` est l’abstraction centrale de Django ORM, et le lazy evaluation est
une optimisation clé. Comprendre quand SQL s’exécute est crucial pour la perf réelle.

</details>

<details>
<summary>51. Comment fonctionnent filter(), exclude(), get() ?</summary>

#### Django

`filter()`, `exclude()` et `get()` sont des méthodes de base de Django ORM pour
récupérer des données. La syntaxe est proche, mais le comportement diffère.

#### `filter()` :

- Retourne un `QuerySet` avec tous les enregistrements qui correspondent.
- S’il n’y a aucun résultat, retourne un `QuerySet` vide (sans exception).

```python
active_users = User.objects.filter(is_active=True)
cheap_products = Product.objects.filter(price__lt=1000)
```

#### `exclude()` :

- Retourne un `QuerySet` avec les enregistrements qui **ne** correspondent pas.

```python
non_archived = Article.objects.exclude(status="archived")
```

#### `get()` :

- Retourne **un seul** objet.
- Exige exactement un résultat.
- Si 0 ou >1 résultat -> exception.

```python
user = User.objects.get(pk=1)
```

#### Exceptions de `get()` :

1. `Model.DoesNotExist` - rien trouvé.
2. `Model.MultipleObjectsReturned` - plus d’un trouvé.

Exemple sécurisé :

```python
from django.http import Http404

def profile_view(request, user_id):
    try:
        user = User.objects.get(pk=user_id)
    except User.DoesNotExist:
        raise Http404("Utilisateur introuvable")
```

Ou plus court :

```python
from django.shortcuts import get_object_or_404
user = get_object_or_404(User, pk=user_id)
```

#### Quand utiliser quoi :

1. `filter()` - quand il peut y avoir plusieurs ou zéro résultat.
2. `exclude()` - pour retirer une partie des données.
3. `get()` - quand l’unicité est garantie (PK, champ unique).

#### Conseils pratiques :

1. Ne pas utiliser `get()` si l’unicité n’est pas garantie.
2. Pour tester l’existence, préférer `exists()` à `get()+try/except`.
3. Pour logique complexe, combiner avec `Q`.

#### Conclusion :

`filter()` et `exclude()` manipulent des ensembles (`QuerySet`), `get()` vise un
objet unique. Le bon choix évite erreurs et simplifie les cas limites.

</details>

<details>
<summary>52. Quelle différence entre get() et filter() ?</summary>

#### Django

`get()` et `filter()` recherchent tous deux des données ORM, mais avec une
sémantique différente : l’un retourne **un objet**, l’autre **un QuerySet**.

#### `get()` :

1. Retourne une instance unique.
2. Exige exactement un match.
3. Lève une exception si 0 ou >1 résultat.

```python
user = User.objects.get(pk=10)
```

Exceptions possibles :

- `User.DoesNotExist`
- `User.MultipleObjectsReturned`

#### `filter()` :

1. Retourne un `QuerySet`.
2. Peut renvoyer 0, 1 ou plusieurs enregistrements.
3. Ne lève pas d’exception si vide.

```python
users = User.objects.filter(is_active=True)
```

#### Différences clés :

1. **Type de résultat**
- `get()` -> objet unique.
- `filter()` -> QuerySet.

2. **Comportement si absence de données**
- `get()` -> exception.
- `filter()` -> QuerySet vide.

3. **Cas d’usage**
- `get()` -> champs uniques (`id`, `uuid`, `email` unique).
- `filter()` -> recherche multi-résultats.

#### Exemple pratique :

```python
# correct : recherche unique
order = Order.objects.get(id=order_id)

# correct : liste des commandes d’un utilisateur
orders = Order.objects.filter(user=request.user).order_by("-created_at")
```

#### Erreurs typiques :

1. `get()` sur champ non unique (risque `MultipleObjectsReturned`).
2. Attendre un objet de `filter()` sans `.first()` / `.get()`.
3. Oublier de gérer les exceptions de `get()` en API/view.

#### Conclusion :

`get()` pour un enregistrement unique, `filter()` pour collections et recherche flexible.
En cas de doute sur la cardinalité, commencer avec `filter()`.

</details>

<details>
<summary>53. Comment récupérer tous les enregistrements ou un seul ?</summary>

#### Django

Dans Django ORM, plusieurs méthodes existent pour récupérer tous les enregistrements
ou un seul, selon le besoin de collection ou de résultat unique.

#### Récupérer tous les enregistrements :

1. **Tous les enregistrements du modèle**

```python
articles = Article.objects.all()
```

2. **Tous les enregistrements selon condition**

```python
articles = Article.objects.filter(is_published=True)
```

3. **Version optimisée avec champs ciblés**

```python
articles = Article.objects.values("id", "title")
```

#### Récupérer un seul enregistrement :

1. **Strictement un avec `get()`**

```python
article = Article.objects.get(pk=article_id)
```

2. **Version web sûre**

```python
from django.shortcuts import get_object_or_404

article = get_object_or_404(Article, pk=article_id)
```

3. **Premier objet d’un queryset**

```python
article = Article.objects.filter(is_published=True).first()
```

Retourne un objet ou `None`, sans exception.

#### Quand utiliser quoi :

1. Collection pour listes/tableaux -> `all()` / `filter()`.
2. Un enregistrement unique -> `get()`.
3. Un enregistrement avec 404 en web flow -> `get_object_or_404()`.
4. Résultat optionnel unique -> `first()`.

#### Erreurs typiques :

1. Utiliser `get()` sur un champ non unique.
2. Utiliser `all()` sans pagination sur grosses tables.
3. Ne pas gérer `DoesNotExist` en API/view.

#### Conclusion :

Pour « tous les enregistrements », utiliser `QuerySet` (`all/filter`), pour « un seul »,
utiliser `get()` ou variantes sûres (`get_object_or_404`, `first()`).

</details>

<details>
<summary>54. Différence entre select_related() et prefetch_related() ?</summary>

#### Django

`select_related()` et `prefetch_related()` servent à optimiser l’ORM pour éviter
le problème N+1 avec des modèles liés.

#### `select_related()` :

1. Pour relations **ForeignKey** et **OneToOne**.
2. Fait un **JOIN SQL** et récupère en une requête.
3. Efficace pour relations « single-valued ».

Exemple :

```python
orders = Order.objects.select_related("customer").all()
for order in orders:
    print(order.customer.email)
```

#### `prefetch_related()` :

1. Pour **ManyToMany**, reverse ForeignKey (et aussi FK/O2O si utile).
2. Fait plusieurs requêtes puis assemble en Python.
3. Efficace pour relations « multi-valued ».

Exemple :

```python
articles = Article.objects.prefetch_related("tags").all()
for article in articles:
    print([tag.name for tag in article.tags.all()])
```

#### Différence clé :

1. **Mécanisme**
- `select_related()` -> JOIN unique.
- `prefetch_related()` -> requêtes multiples + merge Python.

2. **Type de relation**
- `select_related()` -> FK/O2O.
- `prefetch_related()` -> M2M, reverse FK.

3. **Volume de données**
- `select_related()` peut gonfler les lignes via JOIN.
- `prefetch_related()` est meilleur pour collections liées.

#### Utilisation combinée :

```python
orders = (
    Order.objects
    .select_related("customer")
    .prefetch_related("items", "items__product")
)
```

#### Règle pratique :

1. Besoin de FK/O2O -> commencer par `select_related`.
2. Besoin de listes liées (M2M/reverse) -> `prefetch_related`.
3. Profiler les requêtes (debug toolbar/logs), pas à l’intuition.

#### Erreurs typiques :

1. N’utiliser aucun des deux et subir N+1.
2. Tenter `select_related()` sur M2M.
3. Appeler `.all()` dans boucle sans prefetch.

#### Conclusion :

`select_related()` optimise les relations unitaires via JOIN,
`prefetch_related()` optimise les relations multiples via requêtes dédiées.
Leur bonne combinaison apporte un gros gain de performance ORM.

</details>

<details>
<summary>55. Comment optimiser les requêtes ORM (annotate, aggregate, F(), Q()) ?</summary>

#### Django

L’optimisation ORM dans Django repose sur un principe : déplacer les calculs
coûteux vers la BD et réduire le nombre de requêtes et le volume de données.

#### 1. `annotate()` - calcul par ligne

- Ajoute un champ calculé à chaque objet du queryset.

```python
from django.db.models import Count

authors = Author.objects.annotate(books_count=Count("books"))
```

#### 2. `aggregate()` - calcul global queryset

- Retourne un dictionnaire de valeurs agrégées.

```python
from django.db.models import Avg, Sum

stats = Order.objects.aggregate(
    total_revenue=Sum("amount"),
    avg_revenue=Avg("amount"),
)
```

#### 3. `F()` - opérations au niveau BD

- Met à jour sans charger l’objet en Python.
- Réduit les race conditions en concurrence.

```python
from django.db.models import F

Product.objects.filter(pk=product_id).update(stock=F("stock") - 1)
```

#### 4. `Q()` - logique complexe (`AND/OR/NOT`)

```python
from django.db.models import Q

users = User.objects.filter(
    Q(is_active=True) & (Q(role="admin") | Q(role="manager"))
).exclude(Q(email__isnull=True) | Q(email=""))
```

#### Exemple combiné :

```python
from django.db.models import Count, Q

articles = (
    Article.objects
    .filter(is_published=True)
    .annotate(comments_count=Count("comments", filter=Q(comments__is_approved=True)))
    .order_by("-comments_count")
)
```

#### Règles pratiques :

1. Calculer en BD (`annotate/aggregate`), pas en boucle Python.
2. Pour updates massifs, utiliser `update(..., F(...))`.
3. Pour conditions complexes, utiliser `Q` plutôt que plusieurs requêtes.
4. Combiner avec `select_related/prefetch_related` contre N+1.
5. Extraire seulement champs nécessaires (`only`, `values`, `values_list`).

#### Vérifier l’effet :

1. Inspecter SQL via `queryset.query` ou debug toolbar.
2. Comparer nombre de requêtes avant/après.
3. Vérifier le plan d’exécution (`EXPLAIN ANALYZE`) en BD réelle.

#### Erreurs typiques :

1. Agrégations en Python après `list(qs)` au lieu du SQL.
2. `save()` en boucle au lieu d’un `update()`.
3. Annotations complexes sans index BD adaptés.

#### Conclusion :

`annotate`, `aggregate`, `F`, `Q` sont essentiels pour un ORM performant.
Ils réduisent requêtes, calculs Python inutiles et améliorent la stabilité sous charge.

</details>

<details>
<summary>56. Comment surcharger les méthodes save() et delete() ?</summary>

#### Django

Dans Django, on peut surcharger `save()` et `delete()` d’un modèle pour ajouter
une logique avant/après sauvegarde ou suppression.

#### Surcharger `save()` :

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

Règle clé : toujours appeler `super().save(*args, **kwargs)`.

#### Surcharger `delete()` :

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

#### Points importants :

1. `QuerySet.update()` n’appelle pas `save()`.
2. `QuerySet.delete()` ne se comporte pas comme un appel `instance.delete()` unitaire.
3. Les règles critiques doivent aussi être garanties au niveau BD/services.

#### Quand c’est pertinent :

1. Génération de champs dérivés (slug, normalisation).
2. Invariants locaux du modèle.
3. Nettoyage de ressources locales liées.

#### Quand préférer autre chose :

1. Logique métier complexe multi-modèles -> couche service.
2. Effets transverses -> signals (avec prudence) ou événements de domaine.
3. Opérations massives -> commandes bulk dédiées.

#### Bonnes pratiques :

1. Garder `save()/delete()` courts et prévisibles.
2. Éviter les appels HTTP externes dedans.
3. Documenter les effets de bord.
4. Couvrir par tests create/update/delete.

#### Conclusion :

Surcharger `save()`/`delete()` est puissant mais sensible. À réserver à la logique
locale du modèle ; la logique métier complexe doit rester en couche service.

</details>

<details>
<summary>57. Comment fonctionne la suppression en cascade (CASCADE) ?</summary>

#### Django

La suppression en cascade (`models.CASCADE`) signifie : si l’objet parent est
supprimé, Django supprime automatiquement les enregistrements enfants liés.

#### Où c’est utilisé :

- Dans `ForeignKey` et `OneToOneField` via `on_delete`.

#### Exemple :

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Conséquence :

- `author.delete()` supprime l’auteur et tous ses livres.

#### Quand CASCADE est pertinent :

1. Les données enfants n’ont pas de sens sans parent.
2. On veut éviter les enregistrements orphelins.
3. Le cycle de vie enfant dépend entièrement du parent.

#### Risques potentiels :

1. Suppression massive accidentelle.
2. Audit/recovery plus complexes.
3. Effets de bord inattendus dans des domaines liés.

#### Alternatives `on_delete` :

1. `PROTECT` - bloque la suppression du parent si dépendances.
2. `SET_NULL` - met NULL côté enfant (`null=True` requis).
3. `SET_DEFAULT` - applique valeur par défaut.
4. `RESTRICT` - restriction stricte si référence existante.
5. `DO_NOTHING` - responsabilité laissée à la BD/au développeur.

#### Recommandations :

1. Pour données métier critiques, préférer souvent `PROTECT/RESTRICT`.
2. Pour entités techniques dépendantes, `CASCADE` peut convenir.
3. Avant suppression massive, vérifier ce qui sera réellement supprimé.
4. Envisager soft delete si audit historique requis.

#### Conclusion :

`CASCADE` maintient l’intégrité, mais reste agressif. À utiliser quand les
enfants dépendent totalement du parent.

</details>

<details>
<summary>58. Comment fonctionnent les transactions dans Django ?</summary>

#### Django

Les transactions Django garantissent qu’un groupe de changements BD est atomique :
soit tout est validé (`commit`), soit tout est annulé (`rollback`) en cas d’erreur.

#### Outil principal :

- `transaction.atomic()`

#### Exemple :

```python
from django.db import transaction

@transaction.atomic
def create_order(user, items):
    order = Order.objects.create(user=user)
    for item in items:
        OrderItem.objects.create(order=order, product=item["product"], qty=item["qty"])
    return order
```

Si une exception se produit, tout le bloc est rollback.

#### Version context manager :

```python
from django.db import transaction

def transfer(from_acc, to_acc, amount):
    with transaction.atomic():
        from_acc.balance -= amount
        to_acc.balance += amount
        from_acc.save()
        to_acc.save()
```

#### Transactions imbriquées et savepoints :

- Les `atomic()` imbriqués créent des savepoints.
- Une erreur interne peut rollback partiellement jusqu’au savepoint.

#### Mode `ATOMIC_REQUESTS` :

```python
DATABASES["default"]["ATOMIC_REQUESTS"] = True
```

Pratique mais pas toujours optimal en performance.

#### Recommandations :

1. Mettre en `atomic()` seulement les opérations réellement liées.
2. Garder les transactions courtes.
3. Éviter appels HTTP/API externes à l’intérieur.
4. Pour concurrence, utiliser `select_for_update()`.

#### Exemple verrouillage de ligne :

```python
with transaction.atomic():
    account = Account.objects.select_for_update().get(pk=account_id)
    account.balance = F("balance") - amount
    account.save(update_fields=["balance"])
```

#### Erreurs typiques :

1. Fractionner une opération critique hors `atomic()`.
2. Transactions longues qui gardent des locks.
3. Croire que la transaction couvre systèmes externes.
4. Ignorer niveaux d’isolation en contexte concurrent.

#### Conclusion :

Les transactions Django sont la base de la cohérence des données. `atomic()`
doit être standard pour les opérations critiques multi-étapes.

</details>

<details>
<summary>59. Django supporte-t-il NoSQL ?</summary>

#### Django

Réponse courte : Django est **nativement orienté SQL** (PostgreSQL, MySQL,
SQLite, Oracle) via son ORM. Le NoSQL n’est pas supporté au même niveau natif,
mais l’intégration reste possible.

#### En pratique :

1. **ORM Django = SQL-first**
- Migrations, relations, admin, contraintes sont pensés pour SQL.

2. **NoSQL via bibliothèques tierces**
- Adaptateurs/ODM existent, mais compatibilité partielle avec l’écosystème Django.

3. **Approche production la plus fréquente : hybride**
- Données transactionnelles principales en PostgreSQL.
- NoSQL pour besoins spécialisés (cache, documents, recherche, événements).

#### Rôles typiques du NoSQL avec Django :

1. Redis - cache, rate limit, broker de file, sessions.
2. Elasticsearch/OpenSearch - recherche full-text, analytique.
3. Document stores - domaines à schéma très flexible.

#### Quand SQL est généralement meilleur :

- Relations complexes entre entités.
- Transactions et cohérence stricte.
- CRUD standard + admin + modèle métier clair.

#### Quand NoSQL est pertinent :

- Schéma très flexible/évolutif.
- Accès clé-valeur à très faible latence.
- Recherche/log analytics où SQL est moins adapté.

#### Recommandations tech lead :

1. Ne pas remplacer SQL par NoSQL « par mode ».
2. Démarrer avec PostgreSQL comme default Django.
3. Ajouter NoSQL de façon ciblée selon besoin non-fonctionnel.
4. Concevoir la cohérence SQL/NoSQL explicitement (outbox/events/retry).

#### Conclusion :

Django n’est pas NoSQL-first, mais fonctionne très bien en architecture hybride :
SQL pour le cœur métier, NoSQL comme complément spécialisé.

</details>

<details>
<summary>60. Quelles exceptions Django faut-il connaître ?</summary>

#### Django

Django propose un ensemble d’exceptions fréquentes en production. Les connaître
accélère le debug et améliore la gestion d’erreurs en view/API.

#### Exceptions importantes :

1. `Model.DoesNotExist` - `get(...)` sans résultat.
2. `Model.MultipleObjectsReturned` - `get(...)` avec >1 résultat.
3. `ValidationError` - erreurs de validation forms/models/validators.
4. `IntegrityError` - violation contraintes BD (`UNIQUE`, `FK`, `NOT NULL`, `CHECK`).
5. `ObjectDoesNotExist` - exception mère des `*.DoesNotExist`.
6. `PermissionDenied` - accès interdit (403).
7. `SuspiciousOperation` - activité suspecte/invalide.
8. `Http404` - retour explicite de 404.
9. `ImproperlyConfigured` - erreur de configuration.
10. `OperationalError` - erreurs de connexion/disponibilité BD, timeouts.

#### Exemples :

```python
from django.core.exceptions import ValidationError
from django.db import IntegrityError
from django.http import Http404

try:
    user = User.objects.get(pk=user_id)
except User.DoesNotExist:
    raise Http404("Utilisateur introuvable")

try:
    create_order(...)
except ValidationError as exc:
    return JsonResponse({"errors": exc.message_dict}, status=400)
except IntegrityError:
    return JsonResponse({"error": "Intégrité des données violée"}, status=409)
```

#### Règles pratiques :

1. En view, utiliser `get_object_or_404` pour 404.
2. Ne pas avaler les exceptions sans logs.
3. Séparer erreurs utilisateur (4xx) et système (5xx).
4. Ne jamais exposer stack trace en production.
5. Standardiser format d’erreur API (code, message, details).

#### Anti-patterns :

1. `except Exception:` sans précision.
2. Ignorer `IntegrityError` et continuer un flux incohérent.
3. Mélanger erreurs métier et techniques dans un « 400 unknown ».

#### Conclusion :

Une gestion d’exceptions robuste en Django améliore qualité API, stabilité
service et vitesse d’investigation en production.

</details>

<details>
<summary>61. Qu’est-ce que Django Admin ? Comment enregistrer un modèle ?</summary>

#### Django

`Django Admin` est le panneau d’administration intégré pour gérer les données
via interface web, sans développer un back-office séparé depuis zéro.

#### Ce que Django Admin offre :

1. CRUD des modèles prêt à l’emploi.
2. Recherche, filtres, tri, pagination.
3. Gestion d’objets liés (inlines).
4. Back-office rapide pour l’équipe métier.

#### Enregistrer un modèle (minimum) :

```python
# app/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

Le modèle apparaît ensuite dans `/admin/`.

#### Variante recommandée via `ModelAdmin` :

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

#### Prérequis d’accès admin :

1. Migrations appliquées :
```bash
python manage.py migrate
```
2. Superuser créé :
```bash
python manage.py createsuperuser
```
3. Serveur lancé + ouverture de `/admin/`.

#### Recommandations pratiques :

1. Configurer `list_display`, `search_fields`, `list_filter` sur modèles clés.
2. Limiter l’accès admin par rôles/permissions.
3. Optimiser queryset admin sur grosses tables (`select_related/prefetch`).
4. Ne pas utiliser admin comme interface publique utilisateur final.

#### Conclusion :

Django Admin est un outil puissant pour la gestion interne des données.
L’enregistrement d’un modèle prend quelques minutes, et `ModelAdmin` permet vite
un back-office réellement productif.

</details>

<details>
<summary>62. Qu’est-ce qu’un superuser ?</summary>

#### Django

Un `superuser` Django est un compte avec droits administratifs maximum,
généralement utilisé pour accéder à Django Admin et gérer intégralement le système.

#### Caractéristiques clés :

1. `is_superuser = True`
2. `is_staff = True`
3. Dispose de toutes les permissions sans assignation manuelle.
4. Peut gérer users, groupes, modèles et contenu via `/admin/`.

#### Créer un superuser :

```bash
python manage.py createsuperuser
```

Django demandera :
- username
- email (selon modèle)
- password

#### Usages :

1. Administration initiale du projet.
2. Configuration des rôles/groupes/permissions.
3. Support opérationnel via Django Admin.

#### Points sécurité importants :

1. Ne pas utiliser le superuser pour les tâches quotidiennes.
2. Limiter au minimum le nombre de superusers en production.
3. Utiliser mots de passe forts + 2FA si possible.
4. Logger les actions admin et restreindre accès (IP/VPN).
5. Éviter les superusers « temporaires » sans process de suppression.

#### Rôle pratique en équipe :

- Superuser est indispensable au bootstrap.
- En régime stable, préférer `staff` + groupes + permissions fines.

#### Conclusion :

Le superuser est l’équivalent d’un compte root dans Django : indispensable,
mais accès à limiter strictement et à tracer.

</details>

<details>
<summary>63. Comment personnaliser Django Admin ?</summary>

#### Django

La personnalisation de Django Admin se fait via `ModelAdmin` et mécanismes liés
(inlines, actions, permissions, form overrides), pour transformer l’admin de base
en vrai back-office.

#### Personnalisation de base `ModelAdmin` :

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

#### Outils les plus utilisés :

1. `list_display` - colonnes visibles.
2. `list_filter` - filtres latéraux.
3. `search_fields` - recherche champs/relations.
4. `readonly_fields` - champs lecture seule.
5. `fieldsets` - regroupement de champs en formulaire.
6. `actions` - actions de masse.

#### Inline de modèles liés :

```python
class OrderItemInline(admin.TabularInline):
    model = OrderItem
    extra = 0

@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    inlines = [OrderItemInline]
```

#### Action custom :

```python
@admin.action(description="Marquer comme publiés")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)
```

#### Contrôle d’accès :

- `has_view_permission`, `has_change_permission`, `has_delete_permission`
- `get_queryset()` pour scoper les données par rôle.

#### Optimisation performance admin :

1. Utiliser `list_select_related` pour FK en list_display.
2. Prudence avec `search_fields` sur grosses tables (index requis).
3. Réduire calculs lourds dans list view.
4. Utiliser `autocomplete_fields` pour grosses FK.

#### Personnalisation avancée :

- Override `form` / `get_form`.
- Override `save_model` / `delete_model`.
- Templates admin custom pour cas spécifiques.

#### Conclusion :

Django Admin scale bien via `ModelAdmin` : de la simple inscription de modèle
à un cockpit interne complet, avec rôles, filtres, actions et perf maîtrisée.

</details>

<details>
<summary>64. Quels composants compose Django Admin et quels réglages personnalisés ?</summary>

#### Django

Django Admin se compose de plusieurs éléments clés ajustables selon les processus
métier : listes d’objets, formulaires, filtres, recherche, actions, permissions,
inlines et configuration globale du site admin.

#### Composants principaux :

1. **Admin Site (`admin.site`)**
- Panneau global, header/title/index personnalisables.

2. **`ModelAdmin`**
- Configuration de l’affichage d’un modèle donné.

3. **Change List**
- Liste d’objets (`list_display`, `list_filter`, `search_fields`).

4. **Change Form**
- Formulaire create/edit (`fields`, `fieldsets`, `readonly_fields`).

5. **Inlines**
- Édition des modèles liés sur une même page.

6. **Actions**
- Opérations de masse sur sélection.

7. **Permissions**
- Contrôle view/change/delete par rôle.

#### Exemple de réglages personnalisés :

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
        ("Principal", {"fields": ("email", "first_name", "last_name")}),
        ("Statut", {"fields": ("is_active",)}),
        ("Technique", {"fields": ("created_at", "updated_at")}),
    )
```

#### Réglages globaux du site admin :

```python
from django.contrib import admin

admin.site.site_header = "Admin Panel"
admin.site.site_title = "Backoffice"
admin.site.index_title = "Gestion du système"
```

#### Comportement par rôle :

- `get_queryset()` - limiter ce qu’un staff peut voir.
- `get_readonly_fields()` - champs en lecture seule selon rôle.
- `has_change_permission()` / `has_delete_permission()` - contrôle fin.

#### Composants souvent ajoutés en production :

1. `autocomplete_fields` pour FK volumineuses.
2. `list_select_related` pour optimiser list-view.
3. `form` custom / `formfield_overrides` pour meilleur UX.
4. Templates admin custom pour workflows spécifiques.

#### Conclusion :

La force de Django Admin est de permettre un back-office interne rapide,
sécurisé et ergonomique, entièrement configurable selon l’organisation.

</details>

<details>
<summary>65. Que sont les Django Admin actions et leur personnalisation ?</summary>

#### Django

Les `Admin actions` Django sont des opérations de masse exécutées sur des objets
sélectionnés dans la liste admin. Elles évitent l’édition manuelle en série.

#### Qu’est-ce qu’une action :

- Fonction ou méthode qui reçoit : `modeladmin`, `request`, `queryset`.
- Exécutée sur l’ensemble sélectionné par l’administrateur.

#### Exemple de base :

```python
from django.contrib import admin
from .models import Article

@admin.action(description="Publier les articles sélectionnés")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)

@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    list_display = ("id", "title", "is_published")
    actions = [make_published]
```

#### Exemple action en méthode `ModelAdmin` :

```python
@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    actions = ["mark_as_paid"]

    @admin.action(description="Marquer comme payées")
    def mark_as_paid(self, request, queryset):
        updated = queryset.update(status="paid")
        self.message_user(request, f"Commandes mises à jour : {updated}")
```

#### Personnalisation des actions :

1. `description` explicite pour l’UI.
2. Disponibilité conditionnelle selon rôle/état.
3. Écran intermédiaire de confirmation (admin view custom).
4. Journalisation des actions de masse.

#### Recommandations pratiques :

1. Pour changements massifs, privilégier `queryset.update()`.
2. Si logique objet par objet nécessaire, itérer prudemment en transaction.
3. Afficher un résumé via `message_user`.
4. Restreindre actions sensibles aux rôles adéquats.

#### Nuances importantes :

1. `queryset.update()` n’appelle pas `save()` ni `post_save`.
2. La suppression de masse standard peut être risquée sans garde-fous.
3. Pour opérations critiques, ajouter une étape de confirmation.

#### Cas d’usage fréquents :

- Publish/Unpublish de contenu.
- Changement de statut en lot.
- Export CSV d’une sélection.
- Déclenchement d’un traitement asynchrone sur IDs sélectionnés.

#### Conclusion :

Les Admin actions sont un levier fort d’automatisation opérationnelle dans Django Admin.
Bien personnalisées, elles accélèrent nettement le travail et réduisent la routine manuelle.

</details>

<details>
<summary>66. Qu’est-ce que le middleware et comment fonctionne-t-il ?</summary>

#### Django

Le `middleware` dans Django est une couche entre requête/réponse HTTP et la view.
Il permet d’exécuter du code **avant** l’entrée en view et **après** la création
 de la réponse.

#### Pipeline middleware :

1. La requête arrive dans Django.
2. Elle traverse les middleware dans l’ordre (request phase).
3. Elle passe par URL resolver et view.
4. La réponse repasse via middleware en ordre inverse (response phase).
5. Elle est envoyée au client.

#### Détail important :

- L’ordre dans `MIDDLEWARE` (`settings.py`) est critique.
- Les middleware du haut voient la requête en premier et la réponse en dernier.

#### Cas d’usage typiques :

1. Sécurité (headers, host checks).
2. Sessions et authentification.
3. Protection CSRF.
4. Locale/langue.
5. Logging, request-id, métriques.
6. Caching au niveau requête/réponse.

#### Squelette middleware :

```python
class SimpleMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # avant view
        response = self.get_response(request)
        # après view
        return response
```

#### Branchements :

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    # ...
]
```

#### Bonnes pratiques :

1. Garder le middleware léger et rapide.
2. Ne pas y mettre la logique métier de domaine.
3. Éviter les appels externes lents dedans.
4. Contrôler soigneusement l’ordre des middleware.

#### Erreurs typiques :

1. Middleware trop « intelligent » avec effets de bord.
2. Mauvais ordre cassant auth/csrf/session flow.
3. Duplication de logique middleware/view.

#### Conclusion :

Le middleware est un intercepteur global requête/réponse. Il est idéal pour les
aspects transverses (sécurité, sessions, logs), pas pour la logique métier endpoint.

</details>

<details>
<summary>67. Quels middleware intégrés existent ?</summary>

#### Django

Django fournit des middleware intégrés couvrant les besoins de base : sécurité,
sessions, auth, CSRF, cache, localisation.

#### Built-in middleware les plus courants :

1. `django.middleware.security.SecurityMiddleware`
2. `django.contrib.sessions.middleware.SessionMiddleware`
3. `django.middleware.common.CommonMiddleware`
4. `django.middleware.csrf.CsrfViewMiddleware`
5. `django.contrib.auth.middleware.AuthenticationMiddleware`
6. `django.contrib.messages.middleware.MessageMiddleware`
7. `django.middleware.clickjacking.XFrameOptionsMiddleware`
8. `django.middleware.locale.LocaleMiddleware`
9. `django.middleware.gzip.GZipMiddleware`
10. `django.middleware.cache.UpdateCacheMiddleware` / `FetchFromCacheMiddleware`

#### Ordre typique (raccourci) :

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

#### Notes pratiques :

1. L’ordre impacte le comportement global.
2. Ne retire pas `SecurityMiddleware`, `CsrfViewMiddleware`,
   `AuthenticationMiddleware` sans comprendre l’impact.
3. En production, valider headers de sécurité et cache-policy après changements.

#### Conclusion :

Les middleware intégrés couvrent la majorité des besoins infra « out of the box ».
Le bon ensemble et le bon ordre influencent directement sécurité et stabilité.

</details>

<details>
<summary>68. Comment créer un middleware personnalisé ?</summary>

#### Django

Un middleware custom Django est une classe recevant `get_response` et interceptant
`request/response` dans le pipeline global.

#### Template minimal :

```python
# app/middleware.py
class RequestIdMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # logique avant view
        response = self.get_response(request)
        # logique après view
        return response
```

#### Exemple avec request-id :

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

#### Activation dans `settings.py` :

```python
MIDDLEWARE = [
    # ...
    "app.middleware.RequestIdMiddleware",
]
```

#### Où le placer :

1. Middleware sécurité/sessions plutôt en haut.
2. Logging/request-id souvent après sécurité/session.
3. L’ordre détermine ce que le middleware voit dans `request`.

#### Ce qu’on peut faire :

- Ajouter des headers.
- Logger requête/réponse.
- Ajouter contexte de tracing.
- Refuser requêtes selon règles globales.

#### À éviter :

1. Logique métier endpoint spécifique.
2. Appels HTTP externes lents.
3. Traitements lourds bloquant chaque requête.

#### Conclusion :

Le middleware custom sert les besoins transverses globaux. Il doit rester léger,
prévisible, et correctement positionné dans `MIDDLEWARE`.

</details>

<details>
<summary>69. Que sont les signals et quand les utiliser ?</summary>

#### Django

Les `signals` Django sont un mécanisme événementiel permettant d’exécuter du code
lors d’actions spécifiques (ex. sauvegarde/suppression), sans appel direct dans
view/service.

#### Fonctionnement :

1. Un événement survient (`post_save` par exemple).
2. Une fonction receiver abonnée est exécutée automatiquement.

#### Signals fréquents :

1. `pre_save`, `post_save`
2. `pre_delete`, `post_delete`
3. `m2m_changed`
4. `request_started`, `request_finished` (moins fréquent côté domaine)

#### Exemple `post_save` :

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

Enregistrement dans `apps.py` :

```python
from django.apps import AppConfig

class UsersConfig(AppConfig):
    name = "users"

    def ready(self):
        import users.signals  # noqa
```

#### Quand c’est pertinent :

1. Effets secondaires faiblement couplés.
2. Hooks techniques qui ne doivent pas surcharger la view.
3. Réactions d’événements où le découplage est utile.

#### Quand éviter :

1. Logique métier critique avec ordre explicite requis.
2. Orchestration complexe multi-services.
3. Flows qui doivent rester 100% explicites dans un use-case unique.

#### Problèmes typiques :

1. Effets de bord « magiques ».
2. Debug plus difficile en gros projets.
3. Doubles exécutions si enregistrement imprécis.
4. Ordre d’exécution de multiples receivers difficile à maîtriser.

#### Règles pratiques :

1. Signals courts et rapides.
2. Tâches longues -> file (Celery/RQ).
3. Documenter les abonnements de chaque module.
4. Ne pas cacher la logique métier principale dans les signals.

#### Conclusion :

Les signals conviennent aux effets secondaires modérés et au découplage.
Pour la logique cœur métier, la couche service explicite reste généralement meilleure.

</details>

<details>
<summary>70. Différence entre signals et middleware.</summary>

#### Django

`Middleware` et `signals` servent des objectifs différents. La différence clé est
le **niveau d’événement** sur lequel chacun opère.

#### Middleware :

1. Niveau **HTTP request/response**.
2. Exécuté à chaque requête dans le pipeline global.
3. Adapté aux besoins web transverses.

Cas typiques :

- security headers
- auth/session flow
- logging/tracing/request-id
- locale/caching/compression

#### Signals :

1. Niveau **événements modèle/framework**.
2. Déclenchés sur `post_save`, `post_delete`, `m2m_changed`, etc.
3. Adaptés aux réactions sur changements de données.

Cas typiques :

- créer profil après création user
- synchroniser entités auxiliaires
- hooks légers post-modification

#### Différence principale :

- Middleware répond au cycle requête/réponse.
- Signals répondent aux événements modèle/données.

#### Quand choisir quoi :

1. Comportement HTTP global -> **middleware**.
2. Réaction à changement de modèle -> **signals**.
3. Contrôle explicite du business flow -> **couche service**.

#### Comparaison rapide :

| Critère | Middleware | Signals |
| --- | --- | --- |
| Niveau | Pipeline HTTP | Événements modèle/framework |
| Déclenchement | Avant/après view | Avant/après save/delete |
| Transparence flow | Plus élevée (`MIDDLEWARE`) | Plus faible (effet « magique » possible) |
| Type de tâches | Infrastructure | Effets secondaires événementiels |

#### Erreurs typiques :

1. Mettre logique métier modèle dans middleware.
2. Cacher flow critique dans signals sans orchestration explicite.
3. Dupliquer la même logique dans les deux couches.

#### Conclusion :

Middleware = infrastructure HTTP, signals = réactions aux événements de données.
Pour logique métier importante, mieux vaut des services explicites et testables.

</details>

<details>
<summary>71. Comment fonctionne le système d’authentification et d’autorisation ?</summary>

#### Django

Dans Django, le contrôle d’accès comprend deux parties :

1. **Authentification** - qui es-tu ?
2. **Autorisation** - que peux-tu faire ?

#### Authentification :

1. L’utilisateur envoie login/mot de passe.
2. Django vérifie via `authenticate()`.
3. Si succès -> `login()`, création d’une session.
4. Aux requêtes suivantes, `AuthenticationMiddleware` expose `request.user`.

Exemple :

```python
from django.contrib.auth import authenticate, login

user = authenticate(request, username=username, password=password)
if user is not None:
    login(request, user)
```

#### Autorisation :

- Django vérifie permissions, groupes et règles de rôle.
- Permissions modèles de base : `add`, `change`, `delete`, `view`.

Exemple :

```python
if request.user.has_perm("orders.change_order"):
    ...
```

#### Outils de contrôle d’accès :

1. `@login_required`
2. `@permission_required("app.perm_codename")`
3. `LoginRequiredMixin`, `PermissionRequiredMixin`
4. Groupes (`Group`) pour gérer des ensembles de permissions.

#### Modèle session (par défaut) :

- Après `login()`, Django crée une session (BD/cache).
- L’identifiant de session est stocké en cookie.
- Chaque requête identifie l’utilisateur via cette session.

#### Configuration :

- `AUTHENTICATION_BACKENDS`
- `LOGIN_URL`, `LOGIN_REDIRECT_URL`, `LOGOUT_REDIRECT_URL`
- `AUTH_USER_MODEL` (si modèle user custom)

#### Recommandations pratiques :

1. Ne jamais faire confiance uniquement au frontend pour l’accès.
2. Attribuer droits par rôles/groupes, pas individuellement quand possible.
3. Pour API, définir clairement token/session auth et policy d’accès.
4. Logger les actions admin sensibles.

#### Conclusion :

L’authentification identifie l’utilisateur, l’autorisation définit ses droits.
Ensemble, elles forment une base d’accès sûre et scalable pour web/API.

</details>

<details>
<summary>72. Comment implémenter l’inscription des utilisateurs ?</summary>

#### Django

L’inscription utilisateur en Django se compose généralement d’un formulaire,
une logique de vue, création de l’utilisateur avec mot de passe hashé, puis
(optionnel) connexion automatique.

#### Approche de base :

1. Créer un formulaire d’inscription (`UserCreationForm` ou custom).
2. Gérer le formulaire en view (`GET`/`POST`).
3. Sauvegarder l’utilisateur.
4. Rediriger vers login ou connecter automatiquement.

#### Exemple de formulaire :

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

#### Exemple de view :

```python
# users/views.py
from django.contrib.auth import login
from django.shortcuts import redirect, render
from .forms import SignUpForm

def signup_view(request):
    if request.method == "POST":
        form = SignUpForm(request.POST)
        if form.is_valid():
            user = form.save()  # mot de passe hashé automatiquement
            login(request, user)  # optionnel : autologin
            return redirect("home")
    else:
        form = SignUpForm()
    return render(request, "users/signup.html", {"form": form})
```

#### Template :

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">S’inscrire</button>
</form>
```

#### URL :

```python
path("signup/", signup_view, name="signup")
```

#### Règles sécurité importantes :

1. Ne jamais stocker un mot de passe en clair.
2. Utiliser `UserCreationForm` ou `set_password()`.
3. Ajouter protection brute force (rate limit/captcha selon besoin).
4. En production, privilégier validation email avant activation.

#### Extensions fréquentes :

1. Profil utilisateur (`OneToOne`).
2. Confirmation email par token.
3. Social login (Google/GitHub) via allauth.
4. Audit log des inscriptions.

#### Conclusion :

Django permet une inscription rapide via auth forms/views intégrés. Le point clé :
gestion correcte des mots de passe, CSRF et activation de compte robuste.

</details>

<details>
<summary>73. Comment créer son propre modèle utilisateur ?</summary>

#### Django

On crée un modèle utilisateur custom quand le `User` standard ne suffit pas
(email comme login, champs obligatoires supplémentaires, logique d’auth spécifique).

#### Règle clé :

Définir `AUTH_USER_MODEL` **au début du projet**, avant premières migrations.
Un changement tardif est coûteux et risqué.

#### Variante 1 (recommandée 90% des cas) : `AbstractUser`

- Hériter de l’utilisateur intégré et ajouter ses champs.
- Chemin le plus simple et stable.

```python
# users/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    phone = models.CharField(max_length=30, blank=True)
    timezone = models.CharField(max_length=64, blank=True, default="UTC")
```

Dans `settings.py` :

```python
AUTH_USER_MODEL = "users.User"
```

#### Variante 2 : `AbstractBaseUser` + `PermissionsMixin`

- Contrôle total sur modèle et champ login.
- Plus complexe : `UserManager` custom, `USERNAME_FIELD`, `REQUIRED_FIELDS`,
  compatibilité admin/forms/auth flow.

À utiliser seulement si besoin réellement non standard.

#### Référence au user custom depuis d’autres modèles :

```python
from django.conf import settings

class Order(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
```

#### Dans le code, éviter import direct `User` :

```python
from django.contrib.auth import get_user_model
User = get_user_model()
```

#### Recommandations pratiques :

1. En cas de doute, créer un user custom basé sur `AbstractUser` dès le départ.
2. Éviter `from django.contrib.auth.models import User` dans le code métier.
3. Vérifier compatibilité forms/admin/auth backend.
4. Tester inscription, login, reset password, permissions.

#### Erreurs typiques :

1. Changer de modèle utilisateur en production tardivement.
2. Imports rigides du `User` standard dans modèles/migrations.
3. Choisir `AbstractBaseUser` sans vraie nécessité.

#### Conclusion :

Le modèle utilisateur custom est une décision stratégique de démarrage.
Le chemin sûr : `AbstractUser` + `AUTH_USER_MODEL` + discipline sur `get_user_model()`.

</details>

<details>
<summary>74. À quoi sert login_required ?</summary>

#### Django

`login_required` est un décorateur qui limite l’accès à une view aux utilisateurs
authentifiés.

#### Fonctionnement :

1. Si l’utilisateur est connecté -> la view s’exécute.
2. Sinon -> redirection vers la page login (`LOGIN_URL`) avec `next`.

#### Exemple FBV :

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, "dashboard.html")
```

#### Login URL personnalisé :

```python
@login_required(login_url="/auth/login/")
def billing_page(request):
    ...
```

#### Équivalent CBV :

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import TemplateView

class DashboardView(LoginRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Réglages `settings.py` :

```python
LOGIN_URL = "login"
LOGIN_REDIRECT_URL = "home"
```

#### Usages typiques :

1. Protéger pages privées (compte, commandes, paramètres).
2. Contrôle d’accès de base en zone admin-like.
3. Éviter actions POST non authentifiées.

#### Ce que `login_required` ne fait pas :

1. Ne vérifie pas rôles/permissions (seulement login).
2. Ne remplace pas le contrôle d’autorisation fin.

Pour permissions :

- `permission_required`
- `user_passes_test`
- `PermissionRequiredMixin`

#### Recommandations :

1. Appliquer `login_required` à tous les endpoints privés par défaut.
2. Ne pas se fier au masquage frontend seul.
3. Vérifier la sécurité des redirections `next`.

#### Conclusion :

`login_required` est la protection de base indispensable des views privées.
Il répond à « utilisateur connecté ? », les droits fins se gèrent séparément.

</details>

<details>
<summary>75. Comment fonctionnent les sessions et les cookies ?</summary>

#### Django

Dans Django, sessions et cookies maintiennent l’état entre requêtes, car HTTP
est stateless.

#### Cookies :

- Petites données stockées côté navigateur.
- Renvoyées au serveur à chaque requête du même domaine.
- Contiennent souvent un session ID, pas les données sensibles elles-mêmes.

#### Session :

- Stockage serveur de l’état utilisateur (BD/cache/fichiers).
- Le navigateur conserve seulement la clé de session en cookie.
- Via `request.session`, Django lit/met à jour cet état.

#### Fonctionnement ensemble :

1. Après login, Django crée une session côté serveur.
2. La clé de session est stockée en cookie (`sessionid`).
3. À chaque requête, Django lit le cookie et recharge la session.

#### Exemple session :

```python
def set_theme(request):
    request.session["theme"] = "dark"
    return HttpResponse("ok")

def get_theme(request):
    theme = request.session.get("theme", "light")
    return HttpResponse(theme)
```

#### Exemple cookie explicite :

```python
response = HttpResponse("ok")
response.set_cookie("promo_seen", "1", max_age=3600)
```

#### Où Django stocke les sessions :

- Par défaut : en BD (`django.contrib.sessions`).
- Possible : cache, fichiers, signed cookies backend.

#### Réglages sécurité importants :

1. `SESSION_COOKIE_HTTPONLY = True`
2. `SESSION_COOKIE_SECURE = True`
3. `SESSION_COOKIE_SAMESITE = "Lax"` ou `"Strict"`
4. Idem côté CSRF cookie (`CSRF_COOKIE_SECURE`, etc.)

#### Recommandations pratiques :

1. Ne pas stocker données sensibles directement dans les cookies.
2. Garder la session compacte.
3. En scalabilité, préférer sessions backed by Redis.
4. Invalider session au logout et lors de changements de sécurité.

#### Conclusion :

Cookies = mécanisme client de transport léger, sessions = état côté serveur.
Dans Django, ils fonctionnent ensemble et constituent la base du flow auth
et d’un UX personnalisé.

</details>

<details>
<summary>76. Que sont les groupes et les permissions, et comment implémenter un modèle d’accès par rôles ?</summary>

#### Django

Dans Django, les **permissions** et les **groups** sont les mécanismes de base
pour implémenter le RBAC (Role-Based Access Control).

#### Que sont les permissions :

- Ce sont des droits au format `app_label.codename`, par exemple :
  `orders.view_order`, `orders.change_order`.
- Django crée automatiquement les permissions de base pour les modèles :
  `add`, `change`, `delete`, `view`.
- On peut ajouter des permissions personnalisées (`custom permissions`) dans `Meta`.

#### Que sont les groupes :

- Un groupe = un rôle auquel on assigne un ensemble de permissions.
- On ajoute l’utilisateur au groupe, et il hérite des droits de ce rôle.

#### Exemple de permission personnalisée dans un modèle :

```python
class Order(models.Model):
    ...
    class Meta:
        permissions = [
            ("approve_order", "Can approve order"),
        ]
```

#### Vérification d’accès dans le code :

```python
if request.user.has_perm("orders.approve_order"):
    ...
```

Décorateur :

```python
from django.contrib.auth.decorators import permission_required

@permission_required("orders.approve_order", raise_exception=True)
def approve_view(request, order_id):
    ...
```

#### Exemple de rôles (RBAC) :

1. **viewer** -> uniquement `view_*`
2. **manager** -> `view_*`, `change_*`, `approve_order`
3. **admin** -> ensemble complet des accès du domaine

#### Processus typique d’implémentation RBAC :

1. Décrire les rôles et leurs responsabilités.
2. Définir le mapping « rôle -> permissions ».
3. Créer les groupes et leur attribuer les permissions.
4. Ajouter les utilisateurs aux groupes (via admin ou scripts seed).
5. Vérifier les permissions dans les view/CBV/API.

#### Recommandations pratiques :

1. Assigne les droits via des rôles (groups), pas manuellement par utilisateur.
2. Garde la policy d’accès centralisée et documentée.
3. Vérifie l’accès côté backend, même si l’UI masque des boutons.
4. Pour les cas complexes, ajoute des permissions au niveau objet (si nécessaire).

#### Erreurs fréquentes :

1. Donner `is_superuser` là où des permissions de rôle suffisent.
2. Mélanger rôles et états métier sans règles claires.
3. Distribuer des droits « temporaires » sans audit ni durée de validité.

#### Conclusion :

Les groupes et permissions Django constituent une base fiable pour un modèle
d’accès par rôles. Le RBAC via les groups rend le système plus sûr,
plus transparent et plus facile à maintenir lors de la montée en charge.

</details>

<details>
<summary>77. Comment implémenter la réinitialisation de mot de passe ?</summary>

#### Django

Dans Django, la réinitialisation de mot de passe se fait le plus simplement via
les auth-views intégrées : elles incluent déjà un flow sécurisé avec token
à usage unique et vérification d’expiration.

#### Flow standard :

1. L’utilisateur saisit son email sur la page « Mot de passe oublié ».
2. Django envoie un email avec un lien (uid + token).
3. L’utilisateur suit le lien et définit un nouveau mot de passe.
4. Django confirme le changement réussi.

#### Configuration des URL :

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

#### Templates nécessaires :

- `registration/password_reset_form.html`
- `registration/password_reset_done.html`
- `registration/password_reset_confirm.html`
- `registration/password_reset_complete.html`
- template email, par exemple `registration/password_reset_email.html`

#### Paramètres email de base :

```python
EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "smtp.example.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "..."
EMAIL_HOST_PASSWORD = "..."
DEFAULT_FROM_EMAIL = "noreply@example.com"
```

#### Principes de sécurité importants :

1. Ne révèle pas si l’email existe dans le système (protection user enumeration).
2. Utilise HTTPS pour les liens de reset.
3. Limite la fréquence des demandes (rate limiting).
4. Après changement de mot de passe, invalide les sessions actives selon la policy.
5. Journalise les événements de reset pour l’audit.

#### Quand personnaliser :

- Design personnalisé des emails/pages.
- Modèle utilisateur custom avec connexion par email.
- Intégration avec auth externe/SSO.

#### Conclusion :

Django fournit un mécanisme prêt à l’emploi et sécurisé pour la
réinitialisation de mot de passe via les auth-views standard. En production,
il suffit de configurer correctement email, templates, HTTPS et protections anti-abus.

</details>

<details>
<summary>78. Qu’est-ce que le CSRF et comment fonctionne {% csrf_token %} ?</summary>

#### Django

Le **CSRF (Cross-Site Request Forgery)** est une attaque où un site malveillant
force un utilisateur authentifié à exécuter une action non désirée dans ton
application (par exemple, changer le mot de passe ou créer un paiement).

#### Comment Django protège contre le CSRF :

1. Un token CSRF est généré côté serveur.
2. Le token est injecté dans le formulaire (via `{% csrf_token %}`).
3. Pour les requêtes qui modifient l’état (`POST`, `PUT`, `PATCH`, `DELETE`),
   Django compare le token reçu avec le token attendu.
4. Si le token est absent/invalide -> `403 Forbidden`.

#### `{% csrf_token %}` dans un formulaire :

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Enregistrer</button>
</form>
```

#### Prérequis de fonctionnement :

1. `django.middleware.csrf.CsrfViewMiddleware` dans `MIDDLEWARE`.
2. Utiliser `{% csrf_token %}` dans tous les formulaires POST.
3. Politique cookie correcte (surtout en production avec HTTPS).

#### Pour les requêtes AJAX/fetch :

- Le token CSRF est envoyé dans l’en-tête `X-CSRFToken`.
- Le token est lu depuis le cookie (`csrftoken`) ou depuis le HTML (selon l’approche).

#### Erreurs fréquentes :

1. Oublier `{% csrf_token %}` dans le template du formulaire.
2. Désactiver `CsrfViewMiddleware` sans raison valable.
3. Mal configurer le domaine/les paramètres secure des cookies.
4. Utiliser `@csrf_exempt` « temporairement » puis oublier de remettre la protection.

#### Quand `csrf_exempt` est acceptable :

- Uniquement pour des endpoints spécifiques (ex. webhooks externes), et seulement
  s’il existe un autre mécanisme de validation fiable (signature HMAC, token, allowlist).

#### Recommandations pratiques :

1. Tous les formulaires browser-based qui modifient l’état doivent inclure `{% csrf_token %}`.
2. Pour API sans sessions cookie (Bearer/JWT), construis un modèle d’auth séparé.
3. En production, utilise HTTPS + `CSRF_COOKIE_SECURE = True`.

#### Conclusion :

`{% csrf_token %}` est un élément clé de la protection Django contre les attaques
CSRF dans les formulaires. Ce n’est pas une option, mais un standard de sécurité de base.

</details>

<details>
<summary>79. Comment Django protège contre XSS, CSRF et les injections SQL ?</summary>

#### Django

Django suit une approche « secure by default » et intègre des mécanismes de
protection contre les vulnérabilités web les plus courantes : XSS, CSRF et
injection SQL.

#### 1. Protection contre XSS (Cross-Site Scripting)

Comment cela fonctionne :

1. Les templates Django échappent automatiquement les variables dans `{{ ... }}`.
2. Les caractères HTML spéciaux sont transformés en forme sûre.
3. Le contenu potentiellement dangereux n’est pas exécuté comme script.

Important :

- `|safe` désactive l’échappement, à utiliser uniquement pour du HTML entièrement fiable.
- Ne rends pas du user input brut sans sanitation.

#### 2. Protection contre CSRF

Comment cela fonctionne :

1. `CsrfViewMiddleware` vérifie le token sur les requêtes qui modifient l’état.
2. `{% csrf_token %}` ajoute le token dans les formulaires HTML.
3. Sans token valide, Django renvoie `403`.

#### 3. Protection contre l’injection SQL

Comment cela fonctionne :

1. L’ORM utilise des requêtes paramétrées.
2. Les données sont transmises séparément de la structure SQL.
3. Cela bloque les injections classiques dans la majorité des scénarios standards.

Le risque apparaît si :

- on écrit du SQL brut avec concaténation manuelle de chaînes.

#### Protections supplémentaires intégrées dans Django :

1. `SecurityMiddleware` (headers, politiques liées à SSL).
2. `XFrameOptionsMiddleware` (protection clickjacking).
3. Hachage sécurisé des mots de passe (`PBKDF2` par défaut).
4. Vérification du host header (`ALLOWED_HOSTS`).

#### Recommandations production :

1. `DEBUG=False` en production.
2. HTTPS partout (`SECURE_SSL_REDIRECT`, secure cookies).
3. Définir `SESSION_COOKIE_SECURE`, `CSRF_COOKIE_SECURE`, `HTTPONLY`.
4. Utiliser une CSP (via en-têtes/packages).
5. Mettre à jour régulièrement Django et les dépendances.

#### Erreurs fréquentes des développeurs :

1. Usage incontrôlé de `|safe`.
2. `@csrf_exempt` sans validation alternative.
3. SQL brut avec f-string/format.
4. `DEBUG=True` laissé en production.

#### Conclusion :

Django fournit une protection de base solide contre XSS, CSRF et injection SQL.
Mais la sécurité dépend aussi de la discipline de code : templates corrects,
approche ORM, configuration production et revue sécurité continue.

</details>

<details>
<summary>80. Comment Django protège contre les injections SQL ?</summary>

#### Django

Django protège des injections SQL principalement via l’ORM et les requêtes
paramétrées : les données utilisateur sont passées comme paramètres,
pas injectées dans la chaîne SQL.

#### Mécanisme principal de protection :

1. Tu écris une requête ORM :
```python
User.objects.filter(email=user_input)
```
2. Django génère du SQL avec des placeholders paramétrés.
3. La valeur `user_input` ne peut pas « casser » la structure SQL.

#### Pourquoi c’est sûr :

- L’ORM sépare la logique SQL des données.
- Le SGBD traite les paramètres comme des valeurs, pas comme des commandes SQL.

#### Où le risque d’injection SQL reste possible :

1. **SQL brut avec concaténation de chaînes**
```python
# Dangereux
sql = f"SELECT * FROM users WHERE email = '{user_input}'"
```

2. Mauvaise utilisation de `.extra()` (approche legacy).
3. `ORDER BY`/noms de champs dynamiques sans vérification par allowlist.

#### SQL brut sécurisé (si vraiment nécessaire) :

```python
from django.db import connection

with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM users WHERE email = %s", [user_input])
    rows = cursor.fetchall()
```

#### Règles pratiques :

1. Par défaut, utilise l’ORM (`filter/get/exclude/annotate`).
2. Si le SQL brut est inévitable, uniquement des requêtes paramétrées.
3. N’insère jamais du user input dans du SQL via f-string ou `format`.
4. Pour champs/tri dynamiques, applique une allowlist :
- autoriser seulement des noms de colonnes prédéfinis.

#### Étapes de hardening supplémentaires :

1. Droits minimaux pour l’utilisateur DB (least privilege).
2. Logs des requêtes suspectes et monitoring des anomalies.
3. Mises à jour régulières de Django/drivers DB.

#### Conclusion :

L’ORM Django protège efficacement contre les injections SQL « out of the box ».
Les risques réels commencent quand on contourne l’ORM et qu’on construit du SQL
manuellement sans paramétrage ni validation.

</details>

<details>
<summary>81. Qu’est-ce que la Content Security Policy (CSP) dans Django ?</summary>

#### Django

La **Content Security Policy (CSP)** est une politique de sécurité HTTP qui limite
les sources depuis lesquelles le navigateur peut charger scripts, styles,
images, polices, etc. L’objectif principal est de réduire le risque de XSS
et l’exécution de contenu dangereux.

#### Ce que fait la CSP :

1. Définit une allowlist de sources (`self`, CDN, domaines API).
2. Bloque les ressources inconnues ou injectées.
3. Permet un déploiement progressif via `Report-Only`.

#### Exemple d’en-tête CSP :

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

#### Comment ajouter CSP dans Django :

Le plus pratique est d’utiliser le package `django-csp` :

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

#### Pratiques importantes :

1. Commence par `Content-Security-Policy-Report-Only` pour collecter les violations.
2. Réduis au minimum l’usage de `'unsafe-inline'` et `'unsafe-eval'`.
3. Pour les scripts inline, utilise une approche nonce/hash.
4. Resserre progressivement la policy vers les seules sources nécessaires.

#### Problèmes typiques à l’implémentation :

1. Widgets/analytics tiers cassés à cause de règles trop strictes.
2. Sources wildcard (`*`) qui affaiblissent fortement la CSP.
3. Absence de monitoring des violations CSP après release.

#### Conclusion :

La CSP dans Django est une couche de défense supplémentaire importante contre
XSS et les risques supply-chain. Meilleure approche : d’abord `Report-Only`,
puis durcissement progressif vers une allowlist stricte.

</details>

<details>
<summary>82. Que sont les custom management commands et quand les utiliser ?</summary>

#### Django

Les `custom management commands` sont des commandes CLI Django exécutées via
`python manage.py <command_name>`. Elles permettent d’implémenter des tâches
techniques et opérationnelles sous forme de code maintenable du projet.

#### Pourquoi c’est utile :

1. Automatiser les tâches répétitives (import/export, nettoyage, synchronisation).
2. Fournir des commandes opérationnelles pour DevOps/Support.
3. Exécuter des scripts de migration/backfill de données.
4. Alimenter CI/CD, staging et fenêtres de maintenance.

#### Structure des fichiers :

```text
my_app/
  management/
    __init__.py
    commands/
      __init__.py
      recalc_stats.py
```

#### Exemple de commande :

```python
from django.core.management.base import BaseCommand
from orders.models import Order

class Command(BaseCommand):
    help = "Recalcule les statistiques agrégées des commandes"

    def add_arguments(self, parser):
        parser.add_argument("--dry-run", action="store_true")

    def handle(self, *args, **options):
        total = Order.objects.count()
        if options["dry_run"]:
            self.stdout.write(self.style.WARNING(f"DRY RUN: orders={total}"))
            return
        # logique réelle
        self.stdout.write(self.style.SUCCESS(f"Done. orders={total}"))
```

Exécution :

```bash
python manage.py recalc_stats --dry-run
```

#### Quand c’est le bon choix :

1. La tâche est répétable et doit être reproductible.
2. Tu as besoin du contexte Django complet (ORM, settings, services).
3. Tu veux une commande contrôlée pour l’équipe/CI.

#### Recommandations pratiques :

1. Ajoute `--dry-run` pour une vérification sûre.
2. Privilégie des opérations idempotentes quand possible.
3. Utilise des transactions pour les changements batch critiques.
4. Journalise progression et résultats (`self.stdout`, structured logs).
5. Pour les tâches longues, envisage exécution via queues/workers.

#### Erreurs fréquentes :

1. Garder des scripts critiques « one-off » hors du repository.
2. Lancer des update/delete risqués sans dry-run ni plan de backup.
3. Écrire une commande monolithique illisible et non testée.

#### Conclusion :

Les custom management commands sont un outil standard de maturité
opérationnelle Django. Elles rendent les procédures techniques transparentes,
contrôlées et relançables dans un environnement d’équipe.

</details>

<details>
<summary>83. Que sont les context processors et comment les utiliser ?</summary>

#### Django

Les `context processors` sont des fonctions qui ajoutent automatiquement des
données au contexte des templates (tous ou certains), pour éviter de passer
les mêmes variables manuellement dans chaque view.

#### Comment fonctionne un context processor :

1. Django appelle la fonction pendant le rendu du template.
2. La fonction retourne un dictionnaire.
3. Ce dictionnaire est ajouté au template context.

#### Exemple :

```python
# core/context_processors.py
def app_meta(request):
    return {
        "APP_NAME": "My Django App",
        "SUPPORT_EMAIL": "support@example.com",
    }
```

Configuration dans `settings.py` :

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

Ensuite dans n’importe quel template :

```django
<footer>{{ APP_NAME }} · {{ SUPPORT_EMAIL }}</footer>
```

#### Quand les utiliser :

1. Données globales de layout (nom app, contacts, feature flags).
2. Données nécessaires dans de nombreux templates.
3. Valeurs légères et rapides, sans calcul coûteux.

#### Quand éviter :

1. Requêtes SQL lourdes à chaque rendu.
2. Données spécifiques à un ou deux view.
3. Logique métier complexe.

#### Context processors intégrés utiles :

1. `django.template.context_processors.request` (`request` dans template)
2. `django.contrib.auth.context_processors.auth` (`user`, `perms`)
3. `django.contrib.messages.context_processors.messages`
4. `django.template.context_processors.static`
5. `django.template.context_processors.media`

#### Recommandations pratiques :

1. Garde les context processors aussi légers que possible.
2. Évite les collisions de clés avec le contexte local.
3. Si les données sont coûteuses, cache-les ou passe-les depuis la view ciblée.
4. Documente les clés globales de contexte pour l’équipe.

#### Conclusion :

Les context processors sont un mécanisme pratique pour les données template
communes. Ils conviennent aux valeurs globales légères, mais pas à la logique
métier lourde.

</details>

<details>
<summary>84. Comment fonctionne le cache dans Django ? Principales approches.</summary>

#### Django

Le cache dans Django réduit le nombre d’opérations coûteuses (SQL, rendu
de templates, calculs) et accélère les réponses pour l’utilisateur.

#### Comment ça fonctionne :

1. Donnée/réponse stockée dans un backend rapide (Redis/Memcached).
2. La requête suivante lit le résultat depuis le cache, sans recalcul complet.
3. Après TTL ou invalidation, la valeur est recalculée.

#### Principales approches de cache dans Django :

1. **Site-wide cache (middleware)**
- Met en cache presque toute la réponse HTTP des pages.
- Adapté au contenu public avec faible personnalisation.

2. **Per-view cache (`cache_page`)**
- Met en cache une view spécifique pour une durée donnée.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)
def article_list(request):
    ...
```

3. **Template fragment cache**
- Met en cache un fragment de template, pas toute la page.

```django
{% load cache %}
{% cache 300 homepage_sidebar user.id %}
  ...
{% endcache %}
```

4. **Low-level cache API**
- Contrôle manuel du cache dans le code.

```python
from django.core.cache import cache

data = cache.get("popular_products")
if data is None:
    data = expensive_query()
    cache.set("popular_products", data, 300)
```

#### Configuration du backend :

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Quel choix selon le cas :

1. Pages publiques non personnalisées -> per-view/site-wide.
2. Pages partiellement dynamiques -> fragment cache.
3. Calculs métier/agrégations coûteux -> low-level cache API.

#### Règles pratiques :

1. Commence par cache ciblé (fragment/per-view), pas site-wide d’emblée.
2. Définis le TTL selon les exigences de fraîcheur des données.
3. Pour données personnalisées, ajoute des clés (user id, locale, role).
4. Prévois l’invalidation après changement de données.

#### Erreurs fréquentes :

1. Cacher du contenu personnalisé sans clé utilisateur.
2. Ne pas invalider le cache après update/delete.
3. TTL trop long pour des données « vivantes ».
4. Compter sur le cache au lieu d’optimiser des requêtes SQL médiocres.

#### Conclusion :

Le cache Django est une stratégie multi-niveaux : des fragments de template
jusqu’aux réponses complètes. Le meilleur résultat vient d’une combinaison
backend adapté (souvent Redis), TTL modéré et invalidation maîtrisée.

</details>

<details>
<summary>85. Comment optimiser les requêtes, le cache et l’indexation de la base de données ?</summary>

#### Django

L’optimisation Django est toujours un ensemble :
`requêtes ORM` + `cache` + `indexes DB` + `profiling`.
Une seule technique isolée donne rarement un résultat stable.

#### 1. Optimisation des requêtes ORM

1. Évite le N+1 via :
- `select_related()` pour FK/O2O
- `prefetch_related()` pour M2M/reverse FK

2. Récupère seulement les champs nécessaires :
- `values()`, `values_list()`, `only()`, `defer()`

3. Pour mises à jour massives, utilise :
- `update()` + `F()` au lieu de `save()` en boucle

4. Pour tester l’existence :
- `exists()` au lieu de charger tout le queryset

#### 2. Cache

1. Commence par fragment/per-view cache.
2. Pour calculs « chauds » -> low-level cache API.
3. En production, backend Redis dans la majorité des cas.
4. Prévois clés de cache (user/locale/role) et invalidation après modifications.

#### 3. Indexation DB

1. Ajoute des index sur les champs fréquemment utilisés dans :
- `WHERE`
- `ORDER BY`
- `JOIN`

2. Utilise `models.Index` et `UniqueConstraint` dans `Meta`.
3. N’indexe pas « tout » : chaque index a un coût sur `INSERT/UPDATE`.

Exemple :

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

#### 4. Profiling et mesure

1. Utilise Django Debug Toolbar en dev/staging.
2. Log les requêtes SQL lentes côté DB.
3. Vérifie `EXPLAIN ANALYZE` pour les requêtes critiques.
4. Mesure la latence p95/p99 avant/après changement.

#### Ordre typique d’optimisation :

1. Trouver le goulot d’étranglement (pas d’optimisation à l’aveugle).
2. Corriger l’ORM (N+1, champs inutiles, requêtes dupliquées).
3. Ajouter/vérifier les index.
4. Ajouter du cache pour les scénarios réellement chauds.
5. Re-mesurer le résultat.

#### Erreurs fréquentes :

1. Tout mettre en cache sans stratégie d’invalidation.
2. Ajouter des index sans analyser les requêtes réelles.
3. Optimiser le Python en ignorant le goulot SQL.
4. Faire de gros changements de schéma en production sans rollout progressif.

#### Conclusion :

Une performance Django stable ne s’obtient pas avec « un seul bouton », mais
avec une approche systémique : mesurer, optimiser l’ORM, indexer correctement
la DB et ne cacher que ce qui apporte un vrai gain sous charge.

</details>

<details>
<summary>86. Qu’est-ce que le Django testing framework ?</summary>

#### Django

Le `Django testing framework` est l’ensemble d’outils intégré pour tester
modèles, views, formulaires, API et intégrations dans un projet Django.

#### Ce que contient le framework :

1. `django.test.TestCase` - classe de base pour la majorité des tests.
2. `Client` - client HTTP de test pour interroger les view/URL.
3. Base de données de test (créée automatiquement avant exécution).
4. Assertions pour response, contexte, redirections, templates.
5. Outils d’override settings et d’isolation d’environnement.

#### Lancement des tests :

```bash
python manage.py test
```

#### Fonctionnement de la test DB :

1. Django crée une base de test séparée.
2. Applique migrations/schéma.
3. Chaque test est isolé transactionnellement (`TestCase`).
4. À la fin, la base de test est supprimée.

#### Classes de test principales :

1. **`TestCase`**
- Choix le plus fréquent ; rapide et isolé pour tests ORM/view.

2. **`TransactionTestCase`**
- Quand on a besoin d’un contrôle fin des transactions/commits.

3. **`SimpleTestCase`**
- Tests sans accès base de données.

4. **`LiveServerTestCase`**
- Tests d’intégration/browser avec serveur de test lancé.

#### Exemple de test simple :

```python
from django.test import TestCase
from django.urls import reverse

class HealthViewTests(TestCase):
    def test_health_endpoint_returns_200(self):
        response = self.client.get(reverse("health"))
        self.assertEqual(response.status_code, 200)
```

#### Recommandations pratiques :

1. Écris des tests pour les scénarios métier critiques, pas seulement pour le coverage.
2. Garde les tests déterministes (pas de dépendance au temps/réseau sans mock).
3. Utilise factories/fixtures pour une préparation de données lisible.
4. Exécute les tests en CI sur chaque PR.

#### Erreurs fréquentes :

1. Tests dépendants de l’ordre d’exécution.
2. Trop de tests d’intégration là où des unit tests suffisent.
3. Ignorer les edge cases et scénarios négatifs.

#### Conclusion :

Le Django testing framework fournit une infrastructure prête à l’emploi pour
tester le backend de façon fiable « out of the box ». C’est la base d’un
refactoring sûr et d’un processus de release stable en équipe.

</details>

<details>
<summary>87. Quelle est la différence entre tests unitaires et tests d’intégration ?</summary>

#### Django

Les tests `unit` et `integration` se distinguent par le niveau de vérification :

- **Unit test** : vérifie un morceau de logique isolé.
- **Integration test** : vérifie l’interaction de plusieurs composants ensemble.

#### Tests unitaires :

1. Testent une fonction/méthode/classe isolée du reste du système.
2. Utilisent souvent mock/stub pour les dépendances.
3. Très rapides et précis pour localiser l’erreur.

Exemple dans Django :

- test d’un validateur,
- test d’une fonction utilitaire,
- test d’une méthode de service sans HTTP/DB réel (ou avec isolation minimale).

#### Tests d’intégration :

1. Vérifient plusieurs couches ensemble (view + ORM + middleware + templates).
2. Utilisent souvent le test client et la base de test.
3. Plus lents, mais plus proches d’un scénario réel.

Exemple dans Django :

- `client.post(...)` -> view -> model save -> redirect -> vérification DB.

#### Différences clés :

1. **Vitesse**
- Unit : rapides.
- Integration : plus lents.

2. **Portée de couverture**
- Unit : focus étroit.
- Integration : scénario système plus large.

3. **Diagnostic**
- Unit : plus facile de trouver la cause exacte.
- Integration : capte mieux les problèmes d’assemblage des composants.

#### Exemple de pyramide de tests Django :

1. Beaucoup de unit tests (validateurs, services, utilitaires).
2. Moins d’integration tests (endpoints clés, flows métier critiques).
3. Encore moins de tests end-to-end/browser.

#### Recommandations pratiques :

1. Couvre fortement la logique métier critique avec des unit tests.
2. Ajoute obligatoirement des integration tests pour les core user journeys.
3. N’essaie pas de tout couvrir uniquement avec des tests d’intégration.
4. Chaque bug production doit se conclure par un nouveau test au bon niveau.

#### Conclusion :

Les tests unitaires et d’intégration ne se remplacent pas. Un projet Django
stable requiert la combinaison des deux : unit pour un feedback rapide,
integration pour valider les interactions réelles.

</details>

<details>
<summary>88. Qu’est-ce que le Django test client ?</summary>

#### Django

Le `Django test client` est un outil intégré qui simule des requêtes HTTP vers
ton application sans lancer de vrai navigateur ni serveur HTTP externe.

#### Ce que permet le test client :

1. Envoyer des requêtes `GET`, `POST`, `PUT`, `PATCH`, `DELETE`.
2. Vérifier status code, redirects, templates, context.
3. Travailler avec session, cookies et authentification utilisateur.
4. Tester la chaîne URL -> view -> response.

#### Exemple de base :

```python
from django.test import TestCase
from django.urls import reverse

class HomeTests(TestCase):
    def test_home_returns_200(self):
        response = self.client.get(reverse("home"))
        self.assertEqual(response.status_code, 200)
```

#### Exemple de requête POST :

```python
response = self.client.post(reverse("signup"), {
    "username": "testuser",
    "password1": "StrongPass123!",
    "password2": "StrongPass123!",
})
self.assertEqual(response.status_code, 302)
```

#### Login dans les tests :

1. Login technique rapide :

```python
self.client.force_login(user)
```

2. Login réaliste via credentials :

```python
logged_in = self.client.login(username="testuser", password="secret")
self.assertTrue(logged_in)
```

#### Ce qu’on peut vérifier :

1. `response.status_code`
2. `response.context`
3. `response.templates`
4. `assertRedirects(...)`
5. contenu de la réponse (`assertContains(...)`)

#### Limites du test client :

1. N’exécute pas JavaScript (ce n’est pas du browser automation).
2. Ne valide pas le runtime frontend réel comme Playwright/Selenium.
3. Ne reproduit pas toutes les nuances réseau d’un environnement production.

#### Recommandations pratiques :

1. Utilise le test client pour la majorité des tests d’intégration web/API Django.
2. Pour les flows JS, ajoute des tests e2e/browser séparés.
3. Combine avec factories/fixtures pour une préparation de données lisible.

#### Conclusion :

Le Django test client est un outil rapide et puissant pour vérifier le
comportement HTTP côté backend. C’est le choix standard pour tester views,
URL, auth et intégration de base des composants.

</details>

<details>
<summary>89. Comment tester formulaires, views et ORM ?</summary>

#### Django

Dans Django, formulaires, views et ORM se testent à des niveaux différents,
mais avec un style unique : preconditions claires -> action -> vérification.

#### 1. Tests de formulaires

À vérifier :

1. données valides/invalides
2. erreurs sur des champs précis
3. validation personnalisée (`clean_<field>`, `clean()`)

Exemple :

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

#### 2. Tests de views

À vérifier :

1. code de statut
2. template/contexte
3. redirections
4. comportement auth/permissions

Exemple :

```python
from django.test import TestCase
from django.urls import reverse

class DashboardViewTests(TestCase):
    def test_anonymous_redirected_to_login(self):
        response = self.client.get(reverse("dashboard"))
        self.assertEqual(response.status_code, 302)
```

#### 3. Tests ORM

À vérifier :

1. création/mise à jour/suppression de modèles
2. méthodes personnalisées manager/queryset
3. relations et contraintes (`unique`, `constraints`)

Exemple :

```python
from django.test import TestCase
from blog.models import Article

class ArticleORMTests(TestCase):
    def test_create_article(self):
        article = Article.objects.create(title="Test", is_published=True)
        self.assertEqual(Article.objects.count(), 1)
        self.assertTrue(article.is_published)
```

#### Recommandations pratiques :

1. Garde les tests indépendants les uns des autres.
2. Donne des noms descriptifs au format `should_<behavior>`.
3. Pour données de test, utilise factories/fixtures au lieu de setup dupliqué.
4. Teste les scénarios négatifs aussi rigoureusement que les positifs.

#### Ce qu’on oublie souvent :

1. Vérifications de permissions au niveau view.
2. Validation de formulaires avec entrées inattendues.
3. Comportement des méthodes manager/queryset sur jeux de données vides.

#### Conclusion :

Les formulaires testent la validation, les views le comportement HTTP,
l’ORM les données et relations. Ensemble, cela crée une base de test fiable
pour refactorer et livrer des changements Django en sécurité.

</details>

<details>
<summary>90. Comment utiliser les fixtures ?</summary>

#### Django

Les `fixtures` Django sont des données préparées à l’avance (JSON/YAML/XML)
qu’on peut charger en base pour les tests, démos ou seed initial.

#### Pourquoi utiliser des fixtures :

1. Monter rapidement un jeu de données standard.
2. Reproduire un état de test identique sur plusieurs environnements.
3. Tester des scénarios « réalistes » avec enregistrements liés.

#### Exemple de fixture :

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

Emplacement :

- `app/fixtures/articles.json` (cas typique)

#### Chargement d’une fixture :

```bash
python manage.py loaddata articles.json
```

#### Utilisation dans les tests :

```python
from django.test import TestCase
from blog.models import Article

class ArticleTests(TestCase):
    fixtures = ["articles.json"]

    def test_fixture_loaded(self):
        self.assertEqual(Article.objects.count(), 1)
```

#### Quand les fixtures sont pertinentes :

1. Petit jeu de données de référence stable.
2. Tests d’intégration avec relations complexes.
3. Données de démo/remplissage local pour environnements de review.

#### Limites des fixtures :

1. Fragiles lors des changements de schéma.
2. Plus difficiles à lire/maintenir en gros fichiers JSON.
3. Moins flexibles pour combiner des données selon les tests.

#### Alternative pratique :

- Pour la plupart des tests, mieux vaut des factories (factory_boy, model_bakery), car :
1. Les données sont générées par code.
2. Plus simple à adapter quand les modèles changent.
3. Moins de fichiers statiques « magiques ».

#### Approche recommandée côté tech lead :

1. Petites données partagées -> fixtures.
2. Majorité des tests unit/integration -> factories.
3. Ne pas mélanger chaotiquement les deux sans règles d’équipe.

#### Conclusion :

Les fixtures Django sont utiles pour un dataset de départ stable, mais pour
des jeux de test flexibles et durables, les approches par factories sont
souvent plus efficaces.

</details>

<details>
<summary>91. Comment fonctionnent les vues async et l’ORM async dans Django ?</summary>

#### Django

Django prend en charge les vues asynchrones (`async def`) et développe
progressivement sa pile async pour les scénarios fortement orientés I/O.
La valeur principale de l’async est une meilleure scalabilité quand il y a
beaucoup d’attentes simultanées (API externes, opérations réseau).

#### Vue async dans Django :

```python
from django.http import JsonResponse

async def async_health(request):
    return JsonResponse({"status": "ok"})
```

#### Quand l’async est vraiment utile :

1. Beaucoup d’attentes I/O (requêtes HTTP vers services tiers).
2. Patterns long-polling/websocket (avec la stack appropriée).
3. Forte concurrence de requêtes avec logique CPU relativement légère.

#### Sync vs Async dans Django :

1. `def view(...)` -> vue synchrone.
2. `async def view(...)` -> vue asynchrone.
3. Django peut adapter les frontières sync/async, mais chaque passage a un overhead.

#### Travail avec la base (ORM) :

- Historiquement, l’ORM Django est sync-first.
- Dans les versions récentes, il existe des variantes async pour certaines
  opérations (`aget`, `acreate`, `aupdate_or_create`, itération async, etc.),
  avec attention à la compatibilité de la version Django et du driver DB.

Exemple :

```python
user = await User.objects.aget(pk=user_id)
```

#### Limitations importantes :

1. Toutes les bibliothèques tierces ne sont pas async-safe.
2. Les tâches CPU-bound ne sont pas accélérées par async (préférer workers/queues/process).
3. Mélanger ORM sync dans du code async peut bloquer l’event loop.

#### Recommandations pratiques :

1. Utilise l’async là où il y a un vrai goulot I/O.
2. Si la stack est majoritairement sync, ne force pas l’async « pour la mode ».
3. Réduis les transitions sync<->async.
4. Pour CPU lourd/processing long, utilise Celery/RQ plutôt que `await` dans la vue.

#### Erreurs fréquentes :

1. Attendre un gain de performance sans changer le profil I/O de l’app.
2. Faire des appels sync bloquants à l’intérieur d’une vue async.
3. Ne pas tester le comportement sous charge concurrente.

#### Conclusion :

L’async dans Django est puissant pour les scénarios I/O-heavy, mais ce n’est
pas une solution universelle. L’efficacité dépend de la cohérence de toute la
stack : vues, ORM, clients externes et profil réel de charge.

</details>

<details>
<summary>92. Comment créer des tâches backend (@task, Celery) ?</summary>

#### Django

Les tâches backend (background jobs) dans Django servent aux opérations lourdes
ou différées qu’il faut éviter d’exécuter dans la requête HTTP : envoi d’emails,
imports, génération de fichiers, intégrations, retries.

#### Stack la plus courante :

- **Celery** + broker (souvent Redis ou RabbitMQ) + workers

#### Architecture de base :

1. Le code Django envoie une tâche dans la queue.
2. Le broker stocke le message.
3. Un worker Celery récupère et exécute la tâche async.
4. (Optionnel) le résultat est stocké dans un result backend.

#### Exemple de tâche :

```python
# app/tasks.py
from celery import shared_task

@shared_task
def send_welcome_email(user_id):
    # logique d’envoi d’email
    return {"user_id": user_id, "status": "sent"}
```

Appel depuis view/service :

```python
send_welcome_email.delay(user.id)
```

#### Intégration minimale de Celery avec Django :

1. Installer :
```bash
pip install celery redis
```
2. Ajouter `celery.py` dans la config du projet.
3. Définir le broker URL dans settings/env.
4. Lancer un worker :
```bash
celery -A config worker -l info
```

#### Tâches périodiques :

- Via `celery beat` ou `django-celery-beat` (scheduler type cron).

#### Recommandations pratiques :

1. Les tâches doivent être **idempotentes** (réexécution sans corruption).
2. Ajouter des `retry` pour les pannes temporaires (réseau, API tierces).
3. Ne pas passer d’objets lourds à la tâche : passer un `id`, charger en worker.
4. Journaliser statuts d’exécution et erreurs.
5. Définir timeouts et limites de concurrence des workers.

#### Erreurs fréquentes :

1. Exécuter des opérations longues directement dans la vue.
2. Absence de retry/policy sur intégrations externes.
3. Doublons inattendus de tâches à cause d’une logique non idempotente.
4. Absence de monitoring des queues et tâches bloquées.

#### Conclusion :

Celery dans Django est le standard pour le traitement asynchrone backend.
Les clés de fiabilité : idempotence, retries, monitoring et séparation claire
entre flow HTTP et traitement en arrière-plan.

</details>

<details>
<summary>93. Qu’est-ce que Django REST Framework ?</summary>

#### Django

**Django REST Framework (DRF)** est un framework populaire au-dessus de Django
pour construire des API REST : sérialisation, validation, autorisation,
routage, pagination et interface browsable API.

#### Pourquoi utiliser DRF :

1. Construire rapidement des API stables pour clients web/mobile.
2. Standardiser validation et format des réponses.
3. Gérer finement auth/permissions/throttling.
4. Réduire le boilerplate par rapport aux views `JsonResponse` « pures ».

#### Composants clés DRF :

1. **Serializer**
- Convertit modèle/objet <-> JSON.
- Valide les données entrantes.

2. **APIView / GenericAPIView / ViewSet**
- Couches pour la logique des endpoints.

3. **Routers**
- Génération automatique d’URL pour les ViewSet.

4. **Authentication / Permissions**
- Contrôle qui tu es et ce que tu peux faire.

5. **Pagination / Filtering / Ordering**
- Mécanismes prêts à l’emploi pour listes et recherche.

#### Exemple de serializer :

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Exemple de ViewSet :

```python
from rest_framework.viewsets import ModelViewSet
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
```

#### Exemple de router :

```python
from rest_framework.routers import DefaultRouter
from .views import ArticleViewSet

router = DefaultRouter()
router.register("articles", ArticleViewSet, basename="article")
urlpatterns = router.urls
```

#### Quand DRF est particulièrement pertinent :

1. Produit API-first ou multi-clients.
2. Exigences avancées de permissions/pagination/filtering.
3. Architecture API scalable et format d’erreurs standardisé.

#### Conclusion :

DRF est le standard de fait pour les API dans l’écosystème Django. Il apporte
une architecture API structurée, accélère le développement et simplifie la
maintenance des endpoints en production.

</details>

<details>
<summary>94. Qu’est-ce que la sérialisation et pourquoi est-elle nécessaire ?</summary>

#### Django

La sérialisation est la transformation d’objets Python/modèles vers un format
d’échange (généralement JSON), et la désérialisation est l’opération inverse
vers des objets validés.

#### Pourquoi la sérialisation est nécessaire :

1. Transmettre des données entre backend et clients frontend/mobile.
2. Standardiser le format des réponses API.
3. Valider les données entrantes avant écriture en DB.
4. Séparer le modèle de base du contrat API externe.

#### Sérialisation dans DRF :

- Réalisée via `Serializer` ou `ModelSerializer`.

Exemple :

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Transformation model -> JSON :

```python
article = Article.objects.first()
data = ArticleSerializer(article).data
```

#### Transformation JSON -> validated data/model :

```python
payload = {"title": "New", "is_published": True}
serializer = ArticleSerializer(data=payload)
serializer.is_valid(raise_exception=True)
obj = serializer.save()
```

#### Ce qu’apporte aussi le serializer :

1. Vérification des types et champs obligatoires.
2. Validation custom (`validate_<field>`, `validate`).
3. Contrôle des champs read-only/write-only.
4. Sérialiseurs imbriqués pour entités liées.

#### Recommandations pratiques :

1. Ne pas exposer le modèle brut sans contrat serializer explicite.
2. Garder le schéma API stable et backward-compatible.
3. Valider les règles métier custom dans serializer ou couche service.
4. Créer des serializers distincts selon use-cases (list/detail/create/update).

#### Conclusion :

La sérialisation est le cœur de la couche API Django/DRF : format des données,
validation et stabilité du contrat serveur-client.

</details>

<details>
<summary>95. Quelles sont les particularités de Django avec le framework REST (DRF) ?</summary>

#### Django

Django + DRF est une combinaison d’un framework web mature et d’une couche API
puissante. Elle convient très bien aux services REST de production avec un
modèle de domaine clair.

#### Principales particularités de DRF dans l’écosystème Django :

1. **Approche serializer-first**
- Contrat API clair, validation des entrées, contrôle fin des champs.

2. **Construction flexible des endpoints**
- `APIView`, `GenericAPIView`, `ViewSet`, `ModelViewSet`.

3. **Routage automatique**
- Les routers réduisent fortement le boilerplate CRUD.

4. **Auth + permissions**
- Session, Token, JWT (via packages), classes permission custom.

5. **Pagination, filtering, ordering**
- Mécanismes prêts à l’emploi pour les listes à grande échelle.

6. **Throttling**
- Limitation du débit de requêtes (anti-abuse / API hygiene).

7. **Content negotiation**
- Support de différents renderer/parser (JSON par défaut).

8. **Browsable API**
- Interface dev pratique pour tester les endpoints manuellement.

#### Stack production typique avec DRF :

1. API versionnée (`/api/v1/...`).
2. Serializers dédiés par scénario (`list/detail/create/update`).
3. Policy de permissions par endpoint.
4. Format d’erreurs standardisé.
5. Pagination + filtrage + indexation DB.

#### Points forts de l’approche :

1. Haute vitesse de développement sans perdre la structure.
2. Compatibilité avec auth/admin/ORM/migrations Django.
3. Facile à étendre via classes custom selon besoins métier.

#### Points d’attention :

1. Ne pas surcharger `ModelViewSet` de logique métier complexe.
2. Contrôler les requêtes N+1 dans serializer/viewset.
3. Bien séparer contrat API et modèle interne de données.

#### Conclusion :

DRF fait de Django un framework API solide niveau enterprise : démarrage rapide,
architecture structurée, sécurité mature et scalabilité pour des produits
multi-clients réels.

</details>

<details>
<summary>96. Quelle place occupe Django dans l’architecture des services et des API REST ?</summary>

#### Django

Dans une architecture moderne, Django occupe le plus souvent le rôle de
**backend métier principal** : logique de domaine, données transactionnelles,
processus admin et API REST pour clients web/mobile.

#### Rôles typiques de Django dans l’architecture :

1. **Monolithe modulaire (le plus fréquent)**
- Un service unique avec décomposition claire en apps/domaines.
- Évolution rapide du produit et périmètre opérationnel plus simple.

2. **Service API (DRF)**
- Backend pur pour SPA/mobile/intégrations partenaires.

3. **Service core dans un écosystème microservices**
- Django comme « source of truth » des domaines critiques (utilisateurs,
facturation, commandes).

4. **Service backoffice/admin**
- Circuit interne d’opérations et de gestion des données via Django Admin + UI custom.

#### Pourquoi Django convient bien à ce rôle :

1. Développement rapide de bout en bout du backend.
2. ORM puissant + modèle transactionnel.
3. Système auth/permissions mature.
4. DRF pour des API standardisées.
5. Admin robuste pour les équipes opérationnelles.

#### Où Django peut être moins idéal en « premier choix » :

1. API-only ultra-légères à très haute concurrence (parfois FastAPI est plus adapté).
2. Scénarios low-latency très spécifiques avec overhead framework minimal.

#### Approche architecturale pragmatique :

1. Démarrer avec un monolithe Django aux frontières de domaines claires.
2. Extraire des services séparés uniquement en cas de besoin réel de scalabilité.
3. Garder Django comme nœud core domaine/API/admin.

#### Intégration avec d’autres services :

- Celery/queues pour le traitement asynchrone
- Redis pour le cache
- Moteur de recherche pour full-text
- Object storage/CDN pour les médias
- Stack observabilité (logs, métriques, tracing)

#### Conclusion :

Django occupe une position forte comme backbone des services métier et API REST.
Pour la plupart des produits, c’est un compromis pratique entre vitesse
de développement, discipline architecturale et maintenabilité à long terme.

</details>

<details>
<summary>97. Comment déployer un projet Django (WSGI, ASGI, Nginx) ?</summary>

#### Django

Le déploiement Django en production suit généralement ce schéma :

1. **Nginx** - reverse proxy, static/media, TLS.
2. **App server** - Gunicorn (WSGI) ou Uvicorn/Daphne (ASGI).
3. **Django app** - logique métier.
4. **PostgreSQL/Redis** - données et cache/queues.

#### WSGI vs ASGI :

1. **WSGI (Gunicorn)**
- Variante classique et stable pour applications Django sync.

2. **ASGI (Uvicorn/Daphne)**
- Nécessaire pour async views, websockets et scénarios async modernes.

#### Flow production minimal :

1. Préparer l’environnement :
- `DEBUG=False`
- `ALLOWED_HOSTS`
- secrets via env

2. Installer les dépendances :
```bash
pip install gunicorn
```

3. Collecter les fichiers statiques :
```bash
python manage.py collectstatic --noinput
```

4. Appliquer les migrations :
```bash
python manage.py migrate
```

5. Lancer l’app server :
```bash
gunicorn config.wsgi:application --bind 127.0.0.1:8000 --workers 4
```

#### Exemple Nginx (simplifié) :

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

#### Pour un déploiement ASGI :

```bash
uvicorn config.asgi:application --host 127.0.0.1 --port 8000 --workers 4
```

#### Checklist sécurité/ops obligatoire :

1. HTTPS (Let’s Encrypt), cookies sécurisés.
2. `CSRF_TRUSTED_ORIGINS` et proxy headers corrects.
3. `SECURE_HSTS_SECONDS`, `SECURE_SSL_REDIRECT`, `X_FRAME_OPTIONS`.
4. Logs, monitoring, alertes (error rate, latency, santé DB).
5. Backup et plan de rollback testé.

#### Erreurs fréquentes :

1. `DEBUG=True` en production.
2. Oublier `collectstatic` avant release.
3. Mauvais `ALLOWED_HOSTS` / proxy headers -> problèmes CSRF/redirect.
4. Utiliser le serveur de dev Django (`runserver`) en production.

#### Conclusion :

Un déploiement Django stable repose sur Nginx + app server WSGI/ASGI +
configuration sécurité/observabilité de production. Techniquement simple,
à condition d’avoir une discipline de release.

</details>

<details>
<summary>98. Comment scaler une application Django ?</summary>

#### Django

Scaler Django n’est pas une action unique mais une suite de décisions sur
le code, la base, le cache, les queues et l’infrastructure. Meilleure stratégie :
scaler selon les métriques, pas « au cas où ».

#### 1. Optimisation de l’application (première étape)

1. Supprimer les requêtes N+1 (`select_related`, `prefetch_related`).
2. Optimiser les endpoints lourds (pagination, limites, index).
3. Réduire le payload API/HTML.
4. Ajouter du cache sur les requêtes répétées « chaudes ».

#### 2. Cache et accélération de lecture

1. Redis pour cache low-level/per-view/fragment.
2. CDN pour static/media.
3. En-têtes HTTP cache pour ressources publiques.

#### 3. Scalabilité horizontale au niveau app

1. Exécuter plusieurs instances Django derrière un load balancer.
2. Processus applicatifs stateless (sessions en Redis/DB, pas d’état local).
3. Autoscaling selon CPU/RPS/latency.

#### 4. Externaliser les tâches lourdes en arrière-plan

1. Celery/RQ pour jobs asynchrones.
2. Queues pour emails, rapports, intégrations, imports.
3. Retry/backoff et idempotency pour la fiabilité.

#### 5. Scalabilité de la base de données

1. Indexes et tuning des requêtes.
2. Connection pooling (PgBouncer).
3. Read replicas pour scénarios read-heavy.
4. Partitioning/sharding seulement si besoin réel et architecture claire.

#### 6. Évolution architecturale

1. De « monolithe sans frontières » -> monolithe modulaire.
2. Extraire des domaines ciblés en services si nécessaire.
3. Éviter le découpage microservices prématuré.

#### 7. Observabilité comme condition du scale

1. Métriques : p95/p99 latency, error rate, queue lag, DB locks.
2. Logs avec request-id.
3. Tracing entre services/queues.
4. Alertes sur violations SLA/SLO.

#### Erreurs fréquentes :

1. Scaler l’infra sans optimiser les requêtes.
2. Cacher sans stratégie d’invalidation.
3. Ignorer le goulot DB.
4. Complexité microservices prématurée.

#### Conclusion :

Le scaling Django est un processus piloté : d’abord optimiser code et DB,
ensuite cache et queues, puis scaling horizontal des instances app,
et seulement après complexifier l’architecture. Les métriques doivent guider.

</details>

<details>
<summary>99. Quelles approches pour le déploiement et le monitoring d’une application Django ?</summary>

#### Django

Une production Django fiable repose sur deux piliers :

1. **déploiement maîtrisé**
2. **monitoring complet (observability)**

#### Approches de déploiement :

1. **Déploiement VM/VPS classique**
- Nginx + Gunicorn/Uvicorn + systemd + PostgreSQL/Redis.
- Adapté à un environnement self-hosted maîtrisé.

2. **Container-based (Docker/Kubernetes)**
- Environnement prévisible, scaling par réplicas.
- Pratique pour équipes avec process DevOps.

3. **PaaS/plateformes managées**
- Mise en route plus rapide, moins de charge opérationnelle.
- Compromis sur la flexibilité infra.

#### Pipeline release recommandé :

1. CI : tests + linters + security checks.
2. Build d’un artifact immuable (image).
3. Déploiement en staging.
4. Smoke/health checks.
5. Rollout production (blue/green, rolling ou canary).
6. Rollback automatique en cas de dégradation.

#### Ce qu’il faut monitorer impérativement :

1. **Application metrics**
- RPS, p95/p99 latency, taux d’erreurs 4xx/5xx.

2. **Infrastructure metrics**
- CPU, RAM, disque, réseau, taux de redémarrage pods/containers.

3. **Database metrics**
- slow queries, locks, connexions, replication lag.

4. **Queue/worker metrics**
- queue depth, task latency, retry/failure rate.

5. **Logs + tracing**
- structured logs, request-id, distributed tracing.

#### Kit production minimal :

1. Health endpoints (`/health/live`, `/health/ready`).
2. Logs centralisés (ELK/Loki/Cloud logs).
3. APM/metrics (Prometheus + Grafana, Datadog, New Relic, Sentry).
4. Alertes sur violations SLO, pas seulement « serveur down ».

#### Recommandations pratiques :

1. Maintenir un runbook incident (qui fait quoi, comment restaurer).
2. Garder des migrations backward-compatible pour zero/min-downtime.
3. Automatiser secrets et config via env/secret manager.
4. Entraîner régulièrement rollback et disaster recovery.

#### Erreurs fréquentes :

1. Déployer sans health checks ni stratégie de rollback.
2. Monitorer seulement CPU sans métriques métier ni latence.
3. Pas de lien entre logs et request/trace id.
4. Hotfix manuels en serveur non reproduits dans le code.

#### Conclusion :

Un déploiement Django réussi est un processus CI/CD prévisible ;
la stabilité vient d’un monitoring qui détecte tôt les dégradations.
Sans observabilité, même un bon code perd vite sa maîtrise en production.

</details>

<details>
<summary>100. Que contiennent généralement les patch releases et pourquoi est-il important de se mettre à jour ?</summary>

#### Django

Les patch releases (ex. `5.1.2 -> 5.1.3`) contiennent en général des correctifs
**rétrocompatibles** sans changement d’API publique cassant au niveau major/minor.

#### Ce qu’on trouve généralement dans un patch release :

1. **Security fixes**
- Correction de vulnérabilités (souvent critique en production).

2. **Bug fixes**
- Corrections dans ORM, forms, middleware, admin, migrations, etc.

3. **Stability improvements**
- Meilleure compatibilité dépendances, corrections d’edge cases.

4. **Améliorations mineures docs/tests**
- Sans changement du contrat architectural de l’application.

#### Pourquoi les mises à jour sont importantes :

1. **Sécurité**
- Ignorer un patch sécurité peut laisser une faille connue en production.

2. **Fiabilité**
- Les patch releases retirent des bugs visibles sous charge.

3. **Compatibilité**
- Les bibliothèques modernes attendent des versions patch à jour.

4. **Chemin d’upgrade plus simple**
- Des mises à jour régulières et petites valent mieux que de gros sauts rares.

#### Processus pratique de mise à jour :

1. Mettre à jour la dépendance (`pip`/`poetry`/`uv`).
2. Exécuter tests et linters.
3. Vérifier changelog/release notes.
4. Déployer en staging.
5. Release en production via rollout contrôlé.

#### Fréquence :

- Vérifier les patch updates régulièrement (au moins mensuellement ou après security advisory).
- Pour les versions LTS : appliquer les security patches le plus vite possible.

#### Erreurs fréquentes :

1. Reporter les patch updates « à plus tard ».
2. Mettre à jour directement en production sans validation staging/CI.
3. Ignorer les release notes et possibles side effects.

#### Conclusion :

Les patch releases ne sont pas de la « cosmétique », mais de l’hygiène
opérationnelle du projet. Mettre Django à jour régulièrement réduit les risques
sécurité, améliore la stabilité et rend les futurs upgrades prévisibles.

</details>
