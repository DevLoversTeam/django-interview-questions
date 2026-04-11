**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  Django <img src="./assets/django.svg" width="40" height="40" alt="Django logo"/>
</h1>

<h2>Most Popular Django Interview Questions and Answers</h2>

<details>
<summary>1. What is Django and what are its key capabilities?</summary>

#### Django

Django is a high-level Python web framework built around the "batteries
included" principle: most common development tasks are already available in its
ecosystem.

#### Key Django capabilities:

1. **Fast project bootstrap:** quick project/app scaffolding, ready structure,
   and clear conventions.
2. **Built-in admin panel:** auto-generated Django Admin for browser-based data
   management.
3. **Powerful ORM:** database access through Python models, with minimal need
   for raw SQL in most cases.
4. **Migration system:** controlled and versioned database schema evolution.
5. **URL routing and view layer:** clear separation of routing, business logic,
   and presentation.
6. **Template engine:** built-in HTML rendering with template inheritance
   support.
7. **Security by default:** protection against CSRF, XSS, SQL injection,
   clickjacking, and secure authentication practices.
8. **Built-in authentication:** users, groups, permissions, and sessions.
9. **Form handling:** Django Forms/ModelForms with server-side validation.
10. **Scalability and ecosystem:** caching, middleware, signals, and integration
    with Celery, DRF, Redis, PostgreSQL, etc.

#### When Django is especially effective:

- CRM/ERP and internal business systems.
- Content platforms, marketplaces, and user dashboards.
- Products with both API and web layers in one codebase.
- Projects where delivery speed, security, and maintainability are critical.

#### Short example of what Django gives you out of the box:

```bash
django-admin startproject config .
python manage.py startapp users
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

After these steps, you already have a working project skeleton, connected
database, migration workflow, and admin access.

#### Conclusion:

Django is a practical choice for fast and secure backend development, especially
when you need mature architecture, a stable stack, and quick product delivery.

</details>

<details>
<summary>2. What are the advantages of using Django?</summary>

#### Django

Django is often chosen for commercial development when teams need fast
time-to-market, stable architecture, and a secure backend without stitching
together dozens of third-party libraries.

#### Key advantages of Django:

1. **High development speed:** many common tasks are already built in (auth,
   admin, forms, ORM, sessions, cache).
2. **Security out of the box:** built-in protection against CSRF, XSS, SQL
   injection, clickjacking, and secure password handling practices.
3. **Clear project structure:** well-defined conventions simplify team
   onboarding and long-term code maintenance.
4. **Powerful ORM and migrations:** fast database work, controlled schema
   evolution, and strong PostgreSQL support.
5. **Admin panel for business operations:** Django Admin quickly provides an
   operational interface for content and back-office teams without separate
   frontend development.
6. **Strong architectural scalability:** apps, middleware, signals, and Celery
   integrate well into production scenarios.
7. **Mature ecosystem:** DRF, django-allauth, django-filter, django-celery-beat,
   and other battle-tested tools.
8. **Enterprise suitability:** predictable releases, a large community,
   high-quality documentation, and stable engineering practices.

#### Practical value for a team:

- Less infrastructure code at project start.
- Lower risk of baseline security mistakes.
- Faster MVP delivery and a clearer path to scaling.
- Better maintainability as the team and codebase grow.

#### When Django’s strengths are most noticeable:

- B2B SaaS, CRM/ERP, user dashboards, marketplaces.
- Products with substantial business logic and access-control rules.
- Teams that prioritize stability and predictable product evolution.

#### Conclusion:

Django’s advantage is that it delivers fast business outcomes without
compromising security or maintainability.

</details>

<details>
<summary>3. What is the difference between MVC and MVT architecture?</summary>

#### Django

In Django, people usually refer to **MVT (Model-View-Template)**, while many
other frameworks use the term **MVC (Model-View-Controller)**. Conceptually,
these approaches are very close; the main differences are in role boundaries and
naming.

#### MVC (classic):

1. **Model** - handles data and business logic.
2. **View** - presents data (UI / presentation layer).
3. **Controller** - handles incoming requests and coordinates flow between Model
   and View.

#### MVT in Django:

1. **Model** - data models and database access via ORM.
2. **View** - request handling, business logic execution, response preparation.
3. **Template** - presentation layer (HTML + template syntax).

#### How MVC maps to MVT:

- `Model (MVC)` ≈ `Model (Django MVT)`
- `View (MVC)` ≈ `Template (Django MVT)`
- `Controller (MVC)` ≈ `View + URL dispatcher (Django MVT)`

In other words, Django splits the "controller" role between `urls.py` (routing)
and `views.py` (request handling).

#### Simple Django (MVT) flow example:

1. A request comes to a URL, for example `/articles/`.
2. `urls.py` routes it to the corresponding `view`.
3. The `view` fetches data from the `Model`.
4. The `view` passes data to a `Template`.
5. The `Template` renders HTML and returns an `HttpResponse`.

#### Conclusion:

- Django does not "break" MVC; it implements it in its own MVT form.
- The key practical difference is that in Django, `view` handles request logic,
  while visual rendering belongs to the `template`.

</details>

<details>
<summary>4. Why is Django considered a loosely coupled framework?</summary>

#### Django

Django is considered **loosely coupled** because its components can be changed,
extended, or replaced independently, without rewriting the entire application.

#### What this means in practice:

1. **Components are separated by responsibility:** URL routing, views,
   templates, models, forms, and middleware work together but are not fused into
   one monolithic logic layer.
2. **Pluggable app architecture:** a project is composed of `apps` that can be
   enabled/disabled via `INSTALLED_APPS`.
3. **Replaceable subsystems:** for example, template engine, user model, cache
   backend, email backend, storage backend.
4. **Settings-driven configuration:** system behavior is controlled by settings,
   not hardcoded implementation details.
5. **Extension via middleware and signals:** functionality can be added without
   modifying the core business-logic layer.

#### Typical loosely coupled examples in Django:

- Switching from SQLite to PostgreSQL by changing `DATABASES` settings.
- Adding Redis cache without rewriting views or models.
- Moving from local file storage to S3-compatible storage via a backend.
- Using a custom user model (`AUTH_USER_MODEL`) without breaking the whole
  project architecture.

#### Why this matters for a team:

- Easier module-level scaling.
- Easier testing of isolated system parts.
- Lower refactoring risk.
- Better long-term maintainability.

#### Conclusion:

In Django, loosely coupled design means engineering flexibility: you can evolve
specific subsystems incrementally instead of rebuilding the whole application at
once.

</details>

<details>
<summary>5. What is the difference between Django and FastAPI?</summary>

#### Django

Django and FastAPI solve different problems. Both frameworks are strong, but
they are chosen for different product types and team needs.

#### Key difference:

- **Django** is a full-featured web framework out of the box (ORM, admin, auth,
  templates, forms, sessions, middleware).
- **FastAPI** is a lightweight and very fast ASGI framework focused primarily on
  API development with strong typing and automatic documentation.

#### Django vs FastAPI comparison:

1. **Primary use case**

- Django: full web systems and APIs in one project.
- FastAPI: API-first systems, microservices, high-concurrency services.

2. **Project startup speed**

- Django: very fast for CRUD/admin/dashboard products.
- FastAPI: fast for APIs, but requires assembling more pieces manually.

3. **Performance**

- Django: sufficient for most business scenarios; traditionally WSGI, with ASGI
  support available.
- FastAPI: often higher throughput for I/O-heavy workloads due to async-first
  design.

4. **ORM and database work**

- Django: mature built-in ORM + migrations.
- FastAPI: no built-in ORM; typically SQLAlchemy/SQLModel/Tortoise.

5. **Admin and back office**

- Django: powerful Django Admin out of the box.
- FastAPI: admin UI must be built or integrated separately.

6. **Validation and schemas**

- Django: forms / DRF serializers.
- FastAPI: Pydantic models as the de facto standard.

7. **API documentation**

- Django: usually via DRF + Swagger/OpenAPI tooling.
- FastAPI: OpenAPI/Swagger UI generated automatically.

8. **Ecosystem**

- Django: broad ecosystem for web products (CMS, auth, admin patterns).
- FastAPI: strong ecosystem for APIs/microservices and modern async workflows.

#### When to choose Django:

- You need an all-in-one backend with fast business delivery.
- You have complex role models, admin workflows, and many CRUD entities.
- Your team values stable conventions and long-term maintainability.

#### When to choose FastAPI:

- You need an API-first service with high concurrency.
- Priority is async integrations (external APIs, queues, streaming, websocket
  scenarios).
- The team wants a minimal and tightly controlled stack.

#### Conclusion:

- **Django** is optimal for rapid delivery of business functionality and complex
  web systems.
- **FastAPI** is optimal for high-performance modern APIs and microservice-style
  workloads.
- In large products, they often coexist: Django as core/admin and FastAPI for
  dedicated API services.

</details>

<details>
<summary>6. What are Django’s drawbacks and limitations compared to other frameworks?</summary>

#### Django

Django is a strong framework, but it is not universally the best choice for
every project type. Its limitations usually appear in specific technical
scenarios.

#### Main drawbacks and limitations of Django:

1. **Heavier entry point for very simple services**

- For a small microservice, Django can feel excessive because of its built-in
  component footprint.

2. **Less native async-first experience than FastAPI**

- Django supports async, but historically much of its ecosystem is
  sync-oriented.
- For high-load I/O APIs, FastAPI/Starlette can sometimes provide a simpler
  path.

3. **ORM is not ideal for highly complex SQL**

- Django ORM is powerful for most tasks, but very complex analytics queries or
  DB-specific optimizations may still require raw SQL.

4. **Stronger conventions**

- Django conventions are a team advantage, but engineers seeking maximum
  low-level control may see them as constraints.

5. **Monolithic-by-default style**

- Django naturally pushes toward a modular monolith rather than many small
  microservices.
- A microservice-first architecture requires strict boundary discipline.

6. **Additional steps for modern API-first DX**

- For full REST APIs, teams usually add DRF; for OpenAPI, extra tooling; for
  realtime, a separate stack (e.g., Channels).

7. **Out-of-the-box performance is not always maximal**

- Without caching, DB indexes, ORM query optimization, and proper profiling,
  large systems can become slow.

#### Common issues often mistaken for "Django weaknesses":

- N+1 queries caused by incorrect ORM usage.
- Lack of a cache strategy.
- Poor modular decomposition of apps.
- Mixing business logic into views without a service layer.

These are more often architecture/process issues than framework flaws.

#### When Django may not be the best choice:

- A very lightweight API service with minimal business logic.
- High-throughput async API as the primary requirement.
- A system requiring maximum low-level customization without a "heavy" framework
  core.

#### Conclusion:

Django’s limitations are real but predictable. For most business applications,
its advantages (development speed, security, maintainability) outweigh them. The
key is to choose a framework based on context, not trend.

</details>

<details>
<summary>7. How does Django work (request-response lifecycle)?</summary>

#### Django

The Django lifecycle is a sequence of steps from the moment an HTTP request
reaches the server to the moment the final HTTP response is returned to the
client.

#### Request processing sequence:

1. **The client sends an HTTP request**

- A browser or API client calls the Django application.

2. **A WSGI/ASGI server passes the request to Django**

- For example: Gunicorn/Uvicorn + Nginx.

3. **The request passes through middleware (request phase)**

- Middleware can modify/enrich the request: authentication, sessions, locale,
  security checks, etc.

4. **The URL resolver matches a route**

- Django matches the URL against rules in `urls.py`.
- If no match is found -> `404 Not Found`.

5. **A view is called**

- The view receives `request` and executes business logic: reads/writes data,
  checks permissions, prepares context.

6. **Models and database are accessed (if needed)**

- Via ORM (`Model.objects...`) or raw SQL for complex cases.

7. **A response is built**

- HTML via `render(...)` + template,
- or JSON via `JsonResponse`,
- or redirect / file response.

8. **The response passes back through middleware (response phase)**

- Middleware may add headers, cookies, cache controls, and logs.

9. **The response is returned to the client**

- The browser renders the page, or the client processes the API response.

#### What happens on errors:

- `Http404` or missing route -> 404 page.
- Unhandled exceptions -> 500 page.
- Exception handling also goes through the middleware chain.

#### Short pipeline:

`Client -> Server (WSGI/ASGI) -> Middleware (request) -> URLconf -> View -> Model/ORM -> Template/Serializer -> Middleware (response) -> Client`

#### Conclusion:

Django’s strength is its predictable request/response pipeline: it is easy to
debug, test, and scale because each stage has a clear responsibility.

</details>

<details>
<summary>8. How do you create a new Django project?</summary>

#### Django

A new Django project is typically created in a few standard steps: environment
setup, Django installation, project scaffolding, migrations, and server start.

#### Step by step:

1. **Create a project directory**

```bash
mkdir my_django_project
cd my_django_project
```

2. **Create and activate a virtual environment**

```bash
python -m venv .venv
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate         # Windows (PowerShell/CMD)
```

3. **Install Django**

```bash
pip install django
```

4. **Generate the project**

```bash
django-admin startproject config .
```

After that, the key files appear:

- `manage.py`
- `config/settings.py`
- `config/urls.py`
- `config/asgi.py`
- `config/wsgi.py`

5. **Apply initial migrations**

```bash
python manage.py migrate
```

6. **Create an admin user**

```bash
python manage.py createsuperuser
```

7. **Run the dev server**

```bash
python manage.py runserver
```

#### Verification:

- Open `http://127.0.0.1:8000/` — Django start page.
- Open `http://127.0.0.1:8000/admin/` — admin panel (after `createsuperuser`).

#### Recommended next step:

Create your first app and add it to `INSTALLED_APPS`:

```bash
python manage.py startapp core
```

This is the basic and correct starting point for most Django projects.

#### Conclusion:

Django’s standard bootstrap process is simple and predictable: in a few
commands, you get a working project skeleton ready for further development.

</details>

<details>
<summary>9. Why is it important to use a virtual environment in Django development?</summary>

#### Django

A virtual environment (`venv`) isolates one project's dependencies from the
system-wide Python environment. In Django projects, this is critical because
different projects often require different library versions.

#### Why this is important:

1. **Dependency isolation**

- Each project uses its own versions of `Django`, `djangorestframework`,
  `psycopg`, `celery`, etc., without conflicts with other projects.

2. **Environment reproducibility**

- It is easy to pin dependencies in `requirements.txt` and recreate the same
  environment on another machine or server.

3. **Deployment stability**

- Lower risk of "works on my machine" issues when local and CI/production
  package versions differ.

4. **Safe upgrades**

- You can test Django or third-party package upgrades without breaking other
  local projects.

5. **Clean system Python**

- OS-level tools are not affected by development packages installed for one app.

#### What happens without `venv`:

- Version conflicts between projects.
- Unpredictable import errors after installing new packages.
- Harder CI/CD debugging due to inconsistent environments.
- Broken local tools after global package changes.

#### Minimal team practice:

1. Create `.venv` in each repository root.
2. Always activate it before running `pip install` and `manage.py` commands.
3. Pin dependencies in `requirements.txt` (or `pyproject.toml` + lock file).
4. Add `.venv/` to `.gitignore`.

#### Conclusion:

In Django, `venv` is not optional; it is a baseline engineering standard. It
provides predictability, stability, and a healthy team workflow.

</details>

<details>
<summary>10. What is the structure of a Django project and the purpose of the main files: manage.py, settings.py, urls.py?</summary>

#### Django

A typical Django project has two key parts: the repository root and a
configuration package (often `config/`) that contains global application
settings.

#### Basic project structure:

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

#### Purpose of the main files:

1. **manage.py**

- CLI entry point for local project operations.
- Used to run commands like: `runserver`, `migrate`, `makemigrations`,
  `createsuperuser`, `test`, `shell`.
- Automatically points Django to the correct settings module.

2. **settings.py**

- Central project configuration.
- Defines: `INSTALLED_APPS`, `MIDDLEWARE`, `DATABASES`, `TEMPLATES`, `CACHES`,
  `STATIC_URL`, `MEDIA_URL`, `AUTH_PASSWORD_VALIDATORS`, `TIME_ZONE`, etc.
- In production, settings are usually split into modules: `settings/base.py`,
  `settings/dev.py`, `settings/prod.py`.

3. **urls.py**

- Global routing map (URL dispatcher).
- Accepts the requested path and delegates to the appropriate app via
  `include()`.
- Also commonly includes `admin/`, health-check routes, and API routing.

#### How these parts work together:

1. `manage.py` starts a Django command.
2. Django loads `settings.py`.
3. The HTTP request passes through middleware.
4. `urls.py` determines which `view` handles the request.
5. The `view` returns a response (HTML/JSON/redirect/file).

#### Practical lead-level recommendations:

- Keep `urls.py` thin: app-level routing should live inside apps.
- Do not turn `settings.py` into a dumping ground; use modular settings.
- Keep all secrets (keys, passwords, tokens) in environment variables, not code.
- Move business logic out of `views.py` into a service layer to simplify tests.

#### Conclusion:

`manage.py`, `settings.py`, and `urls.py` are the operational core of a Django
project: command control, configuration, and routing. Clear organization of
these files directly affects system scalability and maintainability.

</details>

<details>
<summary>11. What are Django apps used for, and how should a project with multiple apps be organized?</summary>

#### Django

In Django, an `app` is an isolated functional module with its own models, views,
URLs, templates, tests, and (if needed) API layer. Apps are used to separate
domains and enable controlled codebase growth.

#### What Django apps are used for:

1. **Modularity**

- Each app owns a specific business context (e.g., `users`, `billing`, `orders`,
  `notifications`).

2. **Reusability**

- An app can be reused internally or moved to another project.

3. **Change localization**

- Changes in one domain affect fewer other modules.

4. **Better maintainability**

- The team navigates code more easily when responsibilities are clearly split.

5. **Simpler testing**

- Tests are written and run per domain instead of across a chaotic monolith.

#### How to organize a multi-app project:

1. **Split by business domain, not by technical layer**

- Good: `users`, `catalog`, `checkout`, `payments`.
- Bad: `models_app`, `views_app`, `utils_app`.

2. **Each app has its own `urls.py`**

- Root `config/urls.py` should mostly delegate via `include()`.

3. **Keep each app autonomous**

- Each app should contain its own `models.py`, `views.py`, `tests.py`,
  `admin.py`, `apps.py`, and `migrations/`.

4. **Avoid cyclic dependencies between apps**

- For cross-module interactions, prefer a service layer or explicit interfaces,
  not direct "everything imports everything" coupling.

5. **Move truly shared code into a separate `common/core` module**

- Only for genuinely shared concerns; do not turn it into a dump folder.

#### Example multi-module project structure:

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

#### App routing connection example:

```python
# config/urls.py
from django.urls import include, path

urlpatterns = [
    path("users/", include("apps.users.urls")),
    path("orders/", include("apps.orders.urls")),
]
```

#### Common anti-patterns:

- One giant app for the entire project.
- Splitting by technical layers instead of business domains.
- Unowned shared code without clear contracts.
- Cross-imports between apps without dependency control.

#### Conclusion:

Django apps are the core mechanism for scaling code. When the system is split
into clear domain boundaries, the project remains manageable and stable much
longer.

</details>

<details>
<summary>12. How does URL routing work in Django?</summary>

#### Django

URL routing in Django determines which `view` should handle a specific HTTP
request. This is handled by the URL dispatcher configured in `urls.py`.

#### How URL routing works step by step:

1. **A request arrives at Django**

- For example: `GET /articles/42/`.

2. **Django reads the root `urlpatterns`**

- Usually in `config/urls.py`.

3. **Sequential route matching**

- Django checks patterns from top to bottom.
- The first match wins.

4. **`include()` is called when needed**

- Part of the route is delegated to a specific app’s `urls.py`.

5. **URL parameters are passed into the view**

- For example, `articles/<int:id>/` passes `id` as an argument.

6. **The view builds the response**

- HTML, JSON, redirect, or file response.

7. **If no match is found -> 404**

- Django returns `Not Found`.

#### Basic example:

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

#### Converters in `path()`:

- `<int:id>` -> integer
- `<str:slug>` -> string without `/`
- `<slug:slug>` -> slug format
- `<uuid:id>` -> UUID
- `<path:subpath>` -> arbitrary path including `/`

#### Practical maintainability rules:

1. Keep root `urls.py` short and delegate to apps.
2. Use `name=` for every route (useful for `reverse()` and templates).
3. Keep API/web URL structure stable (versioning, prefixes).
4. Route order matters: place specific patterns above generic ones.

#### Conclusion:

Django URL routing is a controlled request dispatch mechanism. Well-designed
routes make the code predictable, easier to scale, and safer to refactor.

</details>

<details>
<summary>13. What is the difference between path() and re_path()?</summary>

#### Django

`path()` and `re_path()` are two ways to define URL routes in Django. They solve
the same task, but with different levels of complexity and flexibility.

#### `path()`:

- Uses clear, declarative syntax with converters.
- Suitable for most standard routes.
- Easier to read and maintain in a team.

Example:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("posts/<int:post_id>/", views.post_detail, name="post_detail"),
    path("users/<slug:username>/", views.user_profile, name="user_profile"),
]
```

#### `re_path()`:

- Uses regular expressions (regex).
- Provides maximum flexibility for non-standard URL patterns.
- Harder to read, with a higher risk of regex mistakes.

Example:

```python
from django.urls import re_path
from . import views

urlpatterns = [
    re_path(r"^archive/(?P<year>[0-9]{4})/$", views.archive_year),
    re_path(r"^file/(?P<path>.+\.(pdf|docx))/$", views.file_view),
]
```

#### When to use which:

1. **Use `path()` by default**

- It is the standard and recommended approach in modern Django.

2. **Use `re_path()` only when `path()` is not enough**

- For example, complex URL format validation at routing level or legacy URL
  schemes.

#### Comparison:

- Simplicity: `path()` > `re_path()`
- Flexibility: `re_path()` > `path()`
- Team maintainability: usually better with `path()`

#### Practical tip:

Do not overcomplicate routes with regex unless necessary. If the problem can be
solved with `path()` converters plus validation in view/serializer/form, that is
usually the better option.

#### Conclusion:

`path()` is the primary tool for about 90% of routes. `re_path()` is a targeted
solution for special cases where regex-level flexibility is required.

</details>

<details>
<summary>14. How do URL configurations and include() work?</summary>

#### Django

A URL configuration in Django is a set of rules (`urlpatterns`) that map request
paths to specific `view`s. The `include()` function lets you split large routing
trees into app-level modules.

#### What a URL configuration is:

- A Python module (usually `urls.py`) containing route definitions.
- Each route is defined with `path()` or `re_path()`.
- Django checks routes top to bottom and uses the first match.

#### Why `include()` is needed:

1. **Route decomposition**

- The root `urls.py` stays short and clean.

2. **App-level modularity**

- Each app keeps its own routes in its own `urls.py`.

3. **Better maintainability**

- Teams work with local routing context per domain.

#### Organization example:

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

#### How the include() chain works:

1. A request like `/blog/django-routing/` hits root `config/urls.py`.
2. The `blog/` prefix matches.
3. Django passes the remaining path (`django-routing/`) to `apps.blog.urls`.
4. The matching route is found there and the correct `view` is called.

#### Namespace and `app_name`:

- `app_name` + route `name` creates a namespaced route.
- This enables conflict-free reverse resolution, e.g.:
  `reverse("blog:detail", kwargs={"slug": "django-routing"})`.

#### Practical recommendations:

1. Always use `include()` at app level.
2. Define `app_name` in every app `urls.py`.
3. Keep URL prefixes stable (`api/v1/`, `admin/`, `auth/`).
4. Keep business logic out of the URL layer; routing only.

#### Conclusion:

URL configurations plus `include()` are the foundation of scalable Django
routing: clear app boundaries, a clean root router, and predictable navigation.

</details>

<details>
<summary>15. What is a view in Django?</summary>

#### Django

A `view` in Django is an HTTP request handler. The view receives the `request`,
executes the required logic, and returns an `HttpResponse` (HTML, JSON,
redirect, file response).

#### The role of a view in the request/response cycle:

1. Receive the request after URL matching.
2. Validate input parameters (path/query/body/files).
3. Execute business logic and/or ORM operations.
4. Prepare response data.
5. Return a valid HTTP response.

#### Types of views:

1. **FBV (Function-Based View)**

- A regular Python function.
- Suitable for simple or highly custom logic.

2. **CBV (Class-Based View)**

- A class with methods like `get()`, `post()`, etc.
- Scales better for typical CRUD scenarios, especially with Generic Views.

#### FBV example:

```python
from django.http import HttpResponse, JsonResponse
from django.shortcuts import render

def healthcheck(request):
    return HttpResponse("OK")

def home(request):
    return render(request, "home.html", {"title": "Home"})

def api_status(request):
    return JsonResponse({"status": "ok"})
```

#### Important things to remember:

- A view should not become a "god function".
- Complex business logic should be moved to a service layer.
- A view should stay thin: orchestration, validation, service calls, response.

#### Common mistakes:

- Writing heavy domain logic directly in views (hundreds of lines).
- Duplicating the same logic across multiple views.
- Ignoring permission/authorization checks at endpoint level.

#### Conclusion:

A view is where web protocol meets business logic. Well-designed views make code
predictable, testable, and easier to maintain.

</details>

<details>
<summary>16. What is the difference between function-based views (FBV) and class-based views (CBV)?</summary>

#### Django

Django has two main view styles: **FBV** (function-based views) and **CBV**
(class-based views). Both are valid approaches; the difference is in how logic
is organized and how code scales.

#### FBV (Function-Based Views):

- A view is defined as a function.
- Request/response logic reads top to bottom.
- Simple and transparent for small endpoints.

Example:

```python
from django.http import JsonResponse

def profile_detail(request, user_id):
    if request.method == "GET":
        return JsonResponse({"user_id": user_id})
    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### CBV (Class-Based Views):

- A view is defined as a class (`get`, `post`, `put`, `delete`, etc.).
- Logic can be reused via inheritance and mixins.
- Well suited for CRUD, list/form/detail/create/update/delete scenarios.

Example:

```python
from django.http import JsonResponse
from django.views import View

class ProfileDetailView(View):
    def get(self, request, user_id):
        return JsonResponse({"user_id": user_id})
```

#### Key differences:

1. **Learning curve**

- FBV: easier to start with.
- CBV: requires understanding class hierarchy and dispatch mechanics.

2. **Scalability**

- FBV: good for custom, short handlers.
- CBV: better for repeatable patterns in larger projects.

3. **Code reuse**

- FBV: via helper functions/decorators.
- CBV: via inheritance, mixins, and generic views.

4. **Readability**

- FBV: often clearer locally.
- CBV: can be less obvious due to inherited behavior.

5. **Testing**

- Both approaches are testable, as long as logic is not overembedded in views.

#### When to choose FBV:

- The endpoint is simple and highly custom.
- You need maximum code transparency for quick debugging.
- There is little benefit from class hierarchy.

#### When to choose CBV:

- You have many similar CRUD endpoints/screens.
- You need mixins, permission classes, and reusable patterns.
- The team follows a Generic CBV-oriented style.

#### Conclusion:

FBV vs CBV is not "right vs wrong"; it is contextual. In production, teams often
use both: FBV for focused custom tasks, CBV for structured repeatable scenarios.

</details>

<details>
<summary>17. When is it better to use CBV and generic class-based views?</summary>

#### Django

CBV and generic CBV are most useful when a project has many repeatable web/API
patterns and needs standardized behavior across endpoints.

#### When CBV clearly wins:

1. **CRUD scenarios**

- List/detail/create/update/delete flows.
- Typical classes: `ListView`, `DetailView`, `CreateView`, `UpdateView`,
  `DeleteView`.

2. **Many similar endpoints**

- When endpoints differ mostly by model, form, or permission rules.

3. **Need for logic reuse**

- Via mixins (`LoginRequiredMixin`, `PermissionRequiredMixin`, custom mixins).

4. **Unified style in a larger team**

- CBV helps standardize approach and reduce copy-paste.

5. **Extending base behavior via overrides**

- For example: `get_queryset()`, `get_context_data()`, `form_valid()`,
  `get_success_url()`.

#### When generic CBV is especially appropriate:

- Admin-like interfaces.
- Back-office pages.
- Standard forms and content sections.
- Fast MVP implementation without losing structure.

#### Generic CBV example:

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

#### When NOT to use generic CBV:

1. Logic is highly non-standard and does not fit CRUD patterns.
2. The endpoint has complex orchestration (multiple services/integrations).
3. Excessive overriding makes generic CBV less readable than a simple FBV.

#### Practical tech-lead rule:

- Start with generic CBV for standard cases.
- If the view breaks generic assumptions, switch to regular CBV or FBV.
- Do not keep generic classes just because they look elegant; prioritize
  maintainability and transparent logic.

#### Conclusion:

CBV/generic CBV is a tool for speed and standardization. It is best for
repeatable flows, while non-typical business logic is often better served by a
simpler and more explicit approach.

</details>

<details>
<summary>18. What are mixins in CBV and how are they used?</summary>

#### Django

In CBV, `mixins` are helper classes with reusable behavior that are attached to
views through multiple inheritance. They let you build flexible views without
code duplication.

#### Why mixins are useful:

1. **Logic reuse**

- Authentication, permissions, queryset filtering, shared context, etc.

2. **Behavior composition**

- A view is assembled from small building blocks instead of one large class.

3. **Less copy-paste**

- One mixin can be reused across dozens of views.

#### Most common built-in Django mixins:

- `LoginRequiredMixin` — authenticated users only.
- `PermissionRequiredMixin` — checks a specific permission.
- `UserPassesTestMixin` — custom access check.
- `ContextMixin` — adds data to template context.

#### Built-in mixins usage example:

```python
from django.contrib.auth.mixins import LoginRequiredMixin, PermissionRequiredMixin
from django.views.generic import ListView
from .models import Order

class OrderListView(LoginRequiredMixin, PermissionRequiredMixin, ListView):
    model = Order
    permission_required = "orders.view_order"
    template_name = "orders/list.html"
```

#### Custom mixin example:

```python
class StaffRequiredMixin:
    def dispatch(self, request, *args, **kwargs):
        if not request.user.is_staff:
            from django.http import HttpResponseForbidden
            return HttpResponseForbidden("Access denied")
        return super().dispatch(request, *args, **kwargs)
```

```python
class DashboardView(StaffRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Mixin order matters:

- Django uses MRO (Method Resolution Order).
- Restrictive mixins (e.g., `LoginRequiredMixin`) are typically placed leftmost.
- `View`/generic class usually comes to the right.

#### Practical rules:

1. One mixin = one responsibility.
2. Do not overload mixins with business logic.
3. Avoid deep inheritance chains that complicate debugging.
4. For complex domain logic, use services instead of mixins.

#### Common mistakes:

- Overly "smart" mixins with unpredictable behavior.
- Method conflicts caused by incorrect inheritance order.
- Duplicating the same checks across many views instead of using a shared mixin.

#### Conclusion:

Mixins are a powerful CBV tool for composition and reuse. They provide the most
value when they are small, responsibility-focused, and used with discipline.

</details>

<details>
<summary>19. How should HTTP methods (GET, POST) be handled?</summary>

#### Django

In Django, HTTP methods are handled in views: `GET` usually reads/displays data,
while `POST` creates or changes system state. Correct method separation is the
foundation of a secure and predictable API and web flow.

#### Handling in FBV:

```python
from django.http import JsonResponse

def contact_view(request):
    if request.method == "GET":
        return JsonResponse({"form": "render contact form"})

    if request.method == "POST":
        # read request.POST, validate, persist
        return JsonResponse({"status": "created"}, status=201)

    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### Handling in CBV:

```python
from django.http import JsonResponse
from django.views import View

class ContactView(View):
    def get(self, request):
        return JsonResponse({"form": "render contact form"})

    def post(self, request):
        # validate and persist
        return JsonResponse({"status": "created"}, status=201)
```

#### Restricting allowed methods (decorators):

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

#### Practical rules:

1. **GET**

- Must not change system state.
- Safe and cacheable in many scenarios.

2. **POST**

- Used for create/actions that modify data.
- HTML forms must include CSRF token protection.

3. **Validation**

- Always validate input data (Forms/Serializer/service layer).

4. **Response codes**

- `200` for successful reads,
- `201` for creation,
- `400` for validation errors,
- `405` for method not allowed.

#### Common mistakes:

- Changing data via GET (violates HTTP semantics).
- Mixing GET and POST logic into one chaotic block.
- Returning incorrect status codes.

#### Conclusion:

GET/POST handling in Django should be explicit: each method has a separate
responsibility, clear validation, and correct HTTP status codes. This improves
security, integrations, and long-term maintainability.

</details>

<details>
<summary>20. How do you implement redirects?</summary>

#### Django

In Django, redirects are used when, after an action, you need to send a user to
another page or endpoint.

#### Main approach:

```python
from django.shortcuts import redirect
```

`redirect(...)` returns an HTTP response with status code 302 (temporary
redirect) by default.

#### Usage options:

1. **To an absolute/relative URL**

```python
return redirect("/dashboard/")
```

2. **To a named route (recommended)**

```python
return redirect("orders:list")
```

3. **To a route with parameters**

```python
return redirect("orders:detail", order_id=order.id)
```

4. **To a model instance (if `get_absolute_url` exists)**

```python
return redirect(order)
```

#### FBV example (Post/Redirect/Get):

```python
from django.shortcuts import redirect, render

def create_order(request):
    if request.method == "POST":
        # save data
        return redirect("orders:list")
    return render(request, "orders/form.html")
```

#### CBV example:

```python
from django.urls import reverse_lazy
from django.views.generic import CreateView

class OrderCreateView(CreateView):
    model = Order
    fields = ["title", "amount"]
    success_url = reverse_lazy("orders:list")
```

#### Temporary vs permanent redirects:

- `302 Found` — temporary (default in Django).
- `301 Moved Permanently` — permanent (for SEO/canonical URLs).

When a permanent redirect is needed:

```python
from django.http import HttpResponsePermanentRedirect

return HttpResponsePermanentRedirect("/new-url/")
```

#### Practical tips:

1. Use named routes instead of hardcoded URL strings.
2. After successful POST, redirect (PRG pattern) to avoid duplicate form
   submission on refresh.
3. For post-login/logout redirects, use `next` with safe redirect target checks.

#### Common mistakes:

- Redirecting to a URL that redirects back (redirect loop).
- Hardcoding URLs instead of using route names.
- Returning 200 after POST in flows where PRG should be used.

#### Conclusion:

`redirect` is a core Django tool for controlling user flow. Best practice: named
URLs + PRG pattern + target-route safety checks.

</details>

<details>
<summary>21. What is JsonResponse and when is it used?</summary>

#### Django

`JsonResponse` is Django’s HTTP response class for returning data in JSON
format. It is most commonly used in API endpoints, AJAX requests, and
service-to-service integrations.

#### What `JsonResponse` does:

1. Serializes Python data into JSON.
2. Sets the correct `Content-Type: application/json` header.
3. Allows explicit HTTP status code control.

#### Basic example:

```python
from django.http import JsonResponse

def health(request):
    return JsonResponse({"status": "ok"})
```

#### Example with status code:

```python
def create_item(request):
    # ... creation logic
    return JsonResponse({"id": 123, "message": "created"}, status=201)
```

#### Important `safe` nuance:

- By default, `JsonResponse` expects a **dict** (`safe=True`).
- If you need to return a list, set `safe=False`.

```python
def tags(request):
    return JsonResponse(["python", "django", "api"], safe=False)
```

#### When `JsonResponse` is used:

1. Simple APIs without DRF.
2. Internal frontend endpoints (fetch/AJAX).
3. Webhook responses and service integrations.
4. Health-check/diagnostic endpoints.

#### When DRF is better than plain `JsonResponse`:

- You need serializers, schema validation, pagination, throttling, auth
  policies.
- You have many API endpoints and need a unified API architecture.

#### Practical recommendations:

1. Always return a clear JSON structure (e.g., `{"data": ...}`,
   `{"error": ...}`).
2. Use correct status codes (`200`, `201`, `400`, `404`, `500`).
3. Do not return raw exception traces in production.
4. Standardize one error format across the API.

#### Conclusion:

`JsonResponse` is a lightweight and convenient tool for JSON responses in
Django. It is enough for simple APIs; larger API systems usually move to DRF.

</details>

<details>
<summary>22. How do you return files (CSV, PDF) from a view?</summary>

#### Django

In Django, files are returned from views via `HttpResponse` or `FileResponse`
with correct HTTP headers (`Content-Type`, `Content-Disposition`).

#### Core principles:

1. **`Content-Type`** must match the file type.
2. **`Content-Disposition`** controls browser behavior:

- `attachment` -> download file
- `inline` -> display in browser (if supported)

#### Example: returning CSV

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

#### Example: returning PDF from file

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

#### If PDF is generated dynamically:

- Generate PDF in memory (`io.BytesIO`) or a temporary file.
- Return it via `HttpResponse`/`FileResponse`.
- Common libraries: `reportlab`, `weasyprint`, `xhtml2pdf`.

#### For large files:

1. Use `FileResponse` (streaming, lower RAM usage).
2. Avoid reading the entire file into memory (`read()` on large files is not
   ideal).
3. If needed, use Nginx/X-Accel-Redirect or CDN/object storage.

#### Practical tips:

1. Use clear file names in `filename=`.
2. Enforce file access checks (owner/permissions).
3. Add access audit for sensitive documents.
4. Return predictable API errors (`404` if file not found, `403` if access
   denied).

#### Conclusion:

Returning CSV/PDF in Django is primarily about correct response type and
headers. `HttpResponse` is enough for small files; for large files and
production load, `FileResponse` with streaming is the better choice.

</details>

<details>
<summary>23. How do you implement pagination?</summary>

#### Django

Pagination in Django is used to split large datasets into pages so you do not
render/send hundreds or thousands of records in a single response.

#### Core tool:

- `django.core.paginator.Paginator`

#### FBV example:

```python
from django.core.paginator import Paginator
from django.shortcuts import render
from .models import Article

def article_list(request):
    queryset = Article.objects.order_by("-created_at")
    paginator = Paginator(queryset, 10)  # 10 items per page
    page_number = request.GET.get("page")
    page_obj = paginator.get_page(page_number)  # safe variant

    return render(request, "articles/list.html", {"page_obj": page_obj})
```

#### Rendering pagination in template:

```django
{% for article in page_obj %}
  <h3>{{ article.title }}</h3>
{% endfor %}

<div class="pagination">
  {% if page_obj.has_previous %}
    <a href="?page=1">First</a>
    <a href="?page={{ page_obj.previous_page_number }}">Previous</a>
  {% endif %}

  <span>Page {{ page_obj.number }} of {{ page_obj.paginator.num_pages }}</span>

  {% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">Next</a>
    <a href="?page={{ page_obj.paginator.num_pages }}">Last</a>
  {% endif %}
</div>
```

#### CBV variant (even simpler):

```python
from django.views.generic import ListView
from .models import Article

class ArticleListView(ListView):
    model = Article
    paginate_by = 10
    ordering = ["-created_at"]
```

#### Practical recommendations:

1. Use stable ordering (`order_by`) for predictable navigation.
2. For large lists, optimize queryset:

- `select_related`, `prefetch_related`, DB indexes.

3. Preserve other query parameters (filters, search) when switching pages.
4. Avoid oversized page size unless there is a clear need.

#### Common mistakes:

- Pagination without ordering (records "jump" between pages).
- Using raw `page()` without handling invalid page numbers.
- Missing indexes on columns used for sorting/filtering.

#### Conclusion:

In Django, pagination is quick and clean with `Paginator` or `ListView`.
Performance depends on a correct queryset, stable ordering, and proper page
parameter handling.

</details>

<details>
<summary>24. How do you handle 404 and 500 errors?</summary>

#### Django

In Django, `404` and `500` errors are handled through the standard
error-handling mechanism: error templates, handler functions, and global
settings.

#### What these errors mean:

- **404 Not Found** — route or resource was not found.
- **500 Internal Server Error** — unhandled server-side exception.

#### Basic template-based handling:

In production (`DEBUG = False`), Django automatically looks for:

- `templates/404.html`
- `templates/500.html`

If these files exist, they are shown to the user.

#### Custom handlers in `urls.py`:

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

#### Important difference between dev and production:

1. **DEBUG=True (local)**

- Django shows a detailed debug traceback.

2. **DEBUG=False (production)**

- Users see custom 404/500 pages.
- Technical error details must not leak publicly.

#### Practical recommendations:

1. Always provide friendly custom 404/500 pages.
2. Log errors (Sentry/ELK/OpenTelemetry) instead of exposing stack traces.
3. Add correlation/request IDs to logs for faster incident investigation.
4. Return correct status codes (never 200 for error pages).
5. For APIs, return JSON errors in a unified format.

#### Testing:

- Verify 404 behavior for non-existing URLs.
- Test 500 handlers on staging with `DEBUG=False`.
- Ensure error templates are present in the built/deployed environment.

#### Conclusion:

Good 404/500 handling in Django combines UX and operational maturity: users get
clear error pages, and engineers get actionable logs for diagnosis.

</details>

<details>
<summary>25. What are templates and how do you pass data from a view to a template?</summary>

#### Django

Templates in Django are the presentation layer responsible for generating HTML
from data prepared in a `view`.

#### What a template is:

- An HTML file with Django template syntax (`{{ }}` and `{% %}`).
- Lets you render variables, loops, conditionals, and included page fragments.
- Separates UI markup from Python business logic.

#### How to pass data from a view to a template:

1. Build a `context` dictionary in the `view`.
2. Call `render(request, "template.html", context)`.

#### Example:

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

#### Using data in a template:

```django
<h1>{{ page_title }}</h1>
<p>Total: {{ total }}</p>

{% if articles %}
  <ul>
    {% for article in articles %}
      <li>{{ article.title }}</li>
    {% endfor %}
  </ul>
{% else %}
  <p>No published articles.</p>
{% endif %}
```

#### Where Django loads templates from:

- Directories listed in `TEMPLATES["DIRS"]`.
- `templates/` folders inside apps (when `APP_DIRS=True`).

#### Practical recommendations:

1. Keep business logic in Python (view/service), not in templates.
2. Pass only the data needed by the template.
3. Use named URLs (`{% url 'app:view' %}`) instead of hardcoded links.
4. Use `include`/partials for repeated UI fragments.

#### Security:

- Django auto-escapes template variables by default (XSS protection).
- Do not use `|safe` unless you trust and sanitize the data source.

#### Conclusion:

Templates in Django provide a clean, secure, and controlled way to render HTML.
The view prepares data, the template renders it — this enables maintainability
and clear separation of responsibilities.

</details>

<details>
<summary>26. How does template inheritance work (extends, block)?</summary>

#### Django

Template inheritance in Django lets you create a base layout and reuse it across
child pages. This eliminates HTML duplication and makes the frontend layer more
manageable.

#### Key tags:

1. **`{% extends "base.html" %}`**

- A child template inherits from a base template.

2. **`{% block ... %}{% endblock %}`**

- The base template defines "slots" that child templates can fill.

#### Base template:

```django
{# templates/base.html #}
<!doctype html>
<html lang="uk">
<head>
  <meta charset="utf-8">
  <title>{% block title %}My Site{% endblock %}</title>
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

#### Child template:

```django
{# templates/articles/list.html #}
{% extends "base.html" %}

{% block title %}Article List{% endblock %}

{% block content %}
  <h1>Articles</h1>
  <p>Page content...</p>
{% endblock %}
```

#### `block.super`:

If you want to extend a block rather than fully replace it:

```django
{% block title %}{{ block.super }} | Articles{% endblock %}
```

#### Practical recommendations:

1. Keep one main `base.html` (layout: head, header, footer, scripts).
2. Define separate blocks for `title`, `content`, `extra_css`, `extra_js`.
3. Do not duplicate common parts in every template — extract them to
   base/include.
4. Keep block naming consistent across the project.

#### Common mistakes:

- No unified block structure across pages.
- Putting business logic in templates instead of view/service layer.
- Duplicating layout markup instead of using `extends`.

#### Conclusion:

`extends` and `block` are the foundation of scalable template architecture in
Django: one shared shell, minimal duplication, and fast UI-wide changes.

</details>

<details>
<summary>27. What is {% include %} used for?</summary>

#### Django

`{% include %}` is used to insert one template into another. It is useful for
reusable interface parts: header, footer, cards, tables, pagination, etc.

#### Why `include` is useful:

1. **Removes HTML duplication**

- One fragment can be reused across many pages.

2. **Improves maintainability**

- Changes in a partial file are automatically applied everywhere it is included.

3. **Improves template readability**

- Large templates are split into smaller logical blocks.

#### Basic example:

```django
{# templates/base.html #}
<body>
  {% include "partials/header.html" %}
  <main>{% block content %}{% endblock %}</main>
  {% include "partials/footer.html" %}
</body>
```

#### Passing context to include:

```django
{% include "partials/user_badge.html" with user=request.user %}
```

You can restrict context to only explicitly passed variables:

```django
{% include "partials/user_badge.html" with user=request.user only %}
```

#### Practical use cases:

- Pagination component.
- Table row/product card component.
- Alerts/messages block.
- Shared layout elements.

#### Difference between `extends` and `include`:

- `extends` — template structure inheritance (layout level).
- `include` — local fragment insertion (component level).

#### Common mistakes:

1. Using `include` instead of `extends` for the base layout.
2. Passing overly broad implicit context.
3. Embedding heavy logic in partial templates.

#### Conclusion:

`{% include %}` is a core tool for modular Django template code. Use it for
small reusable fragments, and use `extends` for overall page structure.

</details>

<details>
<summary>28. What are template partials, and how do {% partial %} and {% partialdef %} work?</summary>

#### Django

Template partials are a way to define and reuse template fragments directly
inside template files. They use `{% partialdef %}` (definition) and
`{% partial %}` (invocation).

#### How it works:

1. **`{% partialdef name %}...{% endpartialdef %}`**

- Declares a named partial fragment.

2. **`{% partial name %}`**

- Renders that partial at the desired place in the template.

#### Basic example:

```django
{% partialdef product_card %}
  <article class="card">
    <h3>{{ product.title }}</h3>
    <p>{{ product.price }} UAH</p>
  </article>
{% endpartialdef %}

<section class="grid">
  {% for product in products %}
    {% partial product_card %}
  {% endfor %}
</section>
```

#### How this differs from `{% include %}`:

- `include` loads a separate file.
- `partial/partialdef` lets you define and call a fragment in the context of the
  current template without creating a separate file.

#### When partials are especially useful:

1. When you need to quickly reuse a small fragment within one template.
2. When you want to avoid splitting into dozens of tiny include files.
3. For local UI blocks that do not make sense as separate templates.

#### Practical recommendations:

1. For globally reused components across pages, keep using `{% include %}` or
   dedicated partial files.
2. For small local fragments, use `partial/partialdef`.
3. Keep business logic out of partials; presentation only.

#### Compatibility:

- In modern Django versions, partial tags are available as part of the template
  system.
- In older projects, similar behavior is typically achieved via `{% include %}`
  and custom template tags.

#### Conclusion:

`{% partialdef %}` and `{% partial %}` are tools for local template composition:
less duplication, better readability, and tighter UI structure control.

</details>

<details>
<summary>29. What are template tags and filters?</summary>

#### Django

`Template tags` and `filters` are Django template engine tools for controlled
data rendering in templates.

#### Template tags:

- Tags execute logic at template level.
- They are used in `{% ... %}` syntax.

Common built-in tags:

1. `{% if %}` / `{% elif %}` / `{% else %}` — conditional rendering.
2. `{% for %}` — collection iteration.
3. `{% url %}` — build links from route names.
4. `{% include %}` — include template fragments.
5. `{% csrf_token %}` — CSRF protection in forms.
6. `{% static %}` — static file references.

Example:

```django
{% if user.is_authenticated %}
  <a href="{% url 'profile' %}">Profile</a>
{% else %}
  <a href="{% url 'login' %}">Sign in</a>
{% endif %}
```

#### Filters:

- Filters transform variable values.
- They are used with `|` in `{{ ... }}` expressions.

Common built-in filters:

1. `|lower`, `|upper`, `|title`
2. `|length`
3. `|date:"d.m.Y"`
4. `|default:"-"`, `|default_if_none:"-"`
5. `|truncatechars:50`
6. `|safe` (use carefully)

Example:

```django
<p>{{ article.title|title }}</p>
<p>{{ article.created_at|date:"d.m.Y H:i" }}</p>
<p>{{ article.description|truncatechars:120 }}</p>
```

#### How to create a custom filter:

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

#### How to create a custom simple tag:

```python
@register.simple_tag
def app_version():
    return "1.0.0"
```

```django
{% load text_extras %}
<small>v{% app_version %}</small>
```

#### Practical rules:

1. Keep templates thin: minimal logic, maximum readability.
2. Move reusable presentation logic into custom filters/tags.
3. Do not move business logic into template tags.
4. Use `|safe` only for trusted/sanitized content.

#### Conclusion:

Template tags control rendering structure, while filters format values.
Together, they provide a flexible and secure way to build UI in Django
templates.

</details>

<details>
<summary>30. How do you include static files, and what does collectstatic do?</summary>

#### Django

Static files (`static`) are CSS, JS, images, fonts, and other assets that are
not generated dynamically per request.

#### Basic settings in `settings.py`:

```python
STATIC_URL = "/static/"
STATIC_ROOT = BASE_DIR / "staticfiles"   # for production build output
```

If extra directories are needed:

```python
STATICFILES_DIRS = [BASE_DIR / "static"]
```

#### How to include static files in templates:

```django
{% load static %}
<link rel="stylesheet" href="{% static 'css/main.css' %}">
<script src="{% static 'js/app.js' %}"></script>
<img src="{% static 'img/logo.svg' %}" alt="Logo">
```

#### Where to store static files:

1. In each app:

- `app_name/static/app_name/...`

2. Or in a shared project directory:

- `project_root/static/...`

#### What `collectstatic` does:

Command:

```bash
python manage.py collectstatic
```

Result:

1. Collects all static files from apps and `STATICFILES_DIRS`.
2. Copies them into one directory: `STATIC_ROOT`.
3. Produces the final static bundle served by web server/CDN in production.

#### Dev vs Production:

1. **Local development (`DEBUG=True`)**

- Django can serve static files itself.

2. **Production (`DEBUG=False`)**

- Static is usually served by Nginx, CDN, or object storage.
- The Django process should not serve static directly.

#### Common production practices:

- `ManifestStaticFilesStorage` for versioned/hashed files (cache busting).
- WhiteNoise for simpler deploys without separate Nginx setup.
- CDN for faster static asset delivery.

#### Common mistakes:

1. Not running `collectstatic` before deployment.
2. Hardcoding `/static/...` paths instead of using `{% static %}`.
3. Confusing `static` (app assets) with `media` (user uploads).
4. Not configuring `STATIC_ROOT` for production.

#### Conclusion:

Static setup in Django relies on `{% static %}` and correct settings.
`collectstatic` is a mandatory production build step that unifies all static
assets for fast and stable delivery.

</details>

<details>
<summary>31. What are MEDIA_ROOT and MEDIA_URL?</summary>

#### Django

`MEDIA_ROOT` and `MEDIA_URL` are used to handle user-uploaded files: avatars,
documents, photos, videos, etc.

#### What `MEDIA_ROOT` is:

- The absolute filesystem path on the server where uploaded files are physically
  stored.
- The "disk location" where Django writes files from `FileField`/`ImageField`.

#### What `MEDIA_URL` is:

- The URL prefix through which uploaded files are accessible in the browser.
- The "public path" to content stored in `MEDIA_ROOT`.

#### Basic configuration:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Model example:

```python
from django.db import models

class Profile(models.Model):
    avatar = models.ImageField(upload_to="avatars/")
```

If a user uploads `photo.jpg`, it will end up at:

- File on disk: `MEDIA_ROOT/avatars/photo.jpg`
- Browser URL: `MEDIA_URL + "avatars/photo.jpg"` -> `/media/avatars/photo.jpg`

#### URL setup in development:

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

#### Production approach:

1. Django stores files (locally or via a cloud storage backend).
2. File serving is handled by Nginx/CDN/S3, not by the Django process.
3. Access is controlled via permissions or pre-signed URLs (for private files).

#### Important difference between `static` and `media`:

- `static` — developer assets (CSS/JS/logo), collected via `collectstatic`.
- `media` — user-uploaded files, not handled by `collectstatic`.

#### Common mistakes:

1. Mixing up `STATIC_ROOT` and `MEDIA_ROOT`.
2. Storing user uploads in the git repository.
3. Serving media through Django in production without necessity.
4. Not validating uploaded file type/size.

#### Conclusion:

`MEDIA_ROOT` is where the file physically lives; `MEDIA_URL` is how clients
access it. Clear separation of media and static is a mandatory standard in
Django projects.

</details>

<details>
<summary>32. What approaches exist for template caching?</summary>

#### Django

Template caching in Django reduces CPU/DB load and speeds up page responses by
reusing previously rendered content.

#### Main approaches:

1. **Template fragment caching (recommended for page parts)**

- Caches only a template fragment, not the whole page.

```django
{% load cache %}
{% cache 300 sidebar user.id %}
  {# heavy block: menu, recommendations, widgets #}
  ...
{% endcache %}
```

2. **Per-view caching**

- Caches the full response of a specific view for a given TTL.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)  # 5 minutes
def article_list(request):
    ...
```

3. **Site-wide caching (via middleware)**

- Caches most of the site using global rules.
- Suitable for content-heavy sites with low personalization.

4. **Low-level cache API**

- Caches query/computation results in Python code.

```python
from django.core.cache import cache

data = cache.get("popular_articles")
if data is None:
    data = expensive_query()
    cache.set("popular_articles", data, 300)
```

#### Cache backend configuration:

In production, Redis or Memcached is typically used:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### What to choose when:

- Expensive UI fragments -> template fragment cache.
- Stable public page -> per-view cache.
- Mostly static site -> site-wide cache.
- Expensive business logic/queries -> low-level cache API.

#### Practical rules:

1. Start with the least aggressive caching (fragments), then scale.
2. Choose TTL according to business freshness requirements.
3. Add keys for personalized blocks (user id, locale, permissions).
4. Plan cache invalidation after data changes.

#### Common mistakes:

1. Caching personalized content without user-specific keys.
2. Not invalidating cache after update/delete operations.
3. Setting TTL too high for dynamic data.
4. Treating cache as a "fix" for inefficient SQL queries.

#### Conclusion:

The safest start in Django is fragment caching + Redis. Then add per-view or
site-wide cache when justified by traffic profile and UX requirements.

</details>

<details>
<summary>33. What are Django Forms and ModelForm?</summary>

#### Django

`Django Forms` is a mechanism for handling HTML forms: validation, data
cleaning, field rendering, and error handling.  
`ModelForm` is a specialized form type automatically generated from a Django
model.

#### Django Form:

- Defined via `forms.Form`.
- Fields are declared manually.
- Best for forms not directly tied to a model.

Example:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.CharField(widget=forms.Textarea)
```

#### ModelForm:

- Defined via `forms.ModelForm`.
- Fields are generated from the model.
- Saves to DB easily via `form.save()`.

Example:

```python
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ["title", "content", "is_published"]
```

#### Main difference:

1. **Field source**

- Form: fields are declared manually.
- ModelForm: fields come from the model.

2. **Data persistence**

- Form: manual processing and saving.
- ModelForm: `form.save()` out of the box.

3. **Use case**

- Form: contact forms, search, filters, login/reset, integration forms.
- ModelForm: model CRUD, admin-like interfaces.

#### View handling example:

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

#### General benefits of Django Forms:

- Centralized server-side validation.
- Protection against invalid input and incorrect data types.
- Convenient error message handling.
- Easy template integration.

#### Conclusion:

Use `Form` for custom scenarios not directly tied to a model.  
Use `ModelForm` as the fastest and cleanest path for model CRUD operations.

</details>

<details>
<summary>34. What is the difference between an HTML form and a Django form?</summary>

#### Django

An HTML form and a Django form solve the same problem (data input), but at
different layers. An HTML form is only browser markup, while a Django form is a
server-side validation and processing mechanism.

#### HTML form:

- Defines fields, buttons, `method`, and `action`.
- Runs on the client side (browser).
- Does not guarantee secure or correct data on the server.

Example:

```html
<form method="post" action="/contact/">
  <input type="text" name="name" />
  <input type="email" name="email" />
  <button type="submit">Send</button>
</form>
```

#### Django form:

- Defined in Python (`forms.Form` or `forms.ModelForm`).
- Performs server-side validation and cleaning (`cleaned_data`) and collects
  errors.
- Integrates easily with templates and CSRF protection.

Example:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
```

#### Key differences:

1. **Layer**

- HTML form: presentation layer.
- Django form: backend validation layer.

2. **Validation**

- HTML: basic client-side validation (easy to bypass).
- Django Form: mandatory, reliable server-side validation.

3. **Security**

- HTML alone does not protect against forged requests.
- Django forms work with `{% csrf_token %}` and built-in error handling.

4. **Maintainability**

- HTML-only often leads to duplicated validation logic.
- Django form centralizes rules and simplifies maintenance.

5. **Model integration**

- HTML: manual persistence.
- ModelForm: `form.save()` out of the box.

#### Practical rule:

In production, you must not rely only on HTML validation.  
Client-side validation is for UX; Django form validation is for correctness and
security.

#### Conclusion:

An HTML form handles interface, while a Django form handles data quality and
server reliability. In real projects, both work together, but critical
validation must always live on the backend.

</details>

<details>
<summary>35. How do you render forms in templates?</summary>

#### Django

In Django, forms are rendered in templates via the `form` object passed from a
view. There are multiple approaches: quick automatic rendering or controlled
manual rendering.

#### 1. Quick automatic rendering:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Save</button>
</form>
```

Available variants:

- `{{ form.as_p }}` — fields wrapped in `<p>`
- `{{ form.as_ul }}` — fields rendered as `<li>` list
- `{{ form.as_table }}` — fields rendered in table format

#### 2. Manual rendering (recommended for production UI):

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

  <button type="submit">Save</button>
</form>
```

#### What must be included:

1. `{% csrf_token %}` for POST forms.
2. Field error rendering (`field.errors`) and non-field errors
   (`non_field_errors`).
3. `enctype="multipart/form-data"` for file upload forms.

#### Upload form example:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Upload</button>
</form>
```

#### Practical recommendations:

1. For MVP, starting with `form.as_p` is fine.
2. For real products, prefer manual rendering for full UX/UI control.
3. Do not hide validation errors — show them near relevant fields.
4. Prefer clearly named submit actions and explicit submit flows.

#### Conclusion:

Form rendering in Django can be very fast or very controlled. For production
quality, teams usually choose manual rendering with explicit error display, CSRF
protection, and controlled markup.

</details>

<details>
<summary>36. How does form validation work, and how do you create custom validation?</summary>

#### Django

In Django, form validation runs on the server when `form.is_valid()` is called.
As a result, Django either returns cleaned data (`cleaned_data`) or populates
`form.errors`.

#### Validation flow step by step:

1. Django checks field types and basic rules (`required`, `max_length`,
   `EmailField`, `IntegerField`, etc.).
2. Runs custom field validators (if defined).
3. Runs field-specific `clean_<field>()` methods.
4. Runs global `clean()` for cross-field validation.
5. Produces `cleaned_data` or a list of errors.

#### Single-field validation (`clean_<field>()`):

```python
from django import forms
from django.core.exceptions import ValidationError

class RegisterForm(forms.Form):
    username = forms.CharField(max_length=50)

    def clean_username(self):
        value = self.cleaned_data["username"].strip()
        if "admin" in value.lower():
            raise ValidationError("Username contains a forbidden word.")
        return value
```

#### Cross-field validation (`clean()`):

```python
class PasswordForm(forms.Form):
    password = forms.CharField(widget=forms.PasswordInput)
    confirm_password = forms.CharField(widget=forms.PasswordInput)

    def clean(self):
        cleaned_data = super().clean()
        p1 = cleaned_data.get("password")
        p2 = cleaned_data.get("confirm_password")

        if p1 and p2 and p1 != p2:
            raise forms.ValidationError("Passwords do not match.")
        return cleaned_data
```

#### Custom validators:

```python
from django.core.exceptions import ValidationError

def validate_company_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Only corporate email is allowed.")
```

```python
email = forms.EmailField(validators=[validate_company_email])
```

#### For `ModelForm`:

- Form validation + model validation both apply.
- At model level, you can also use: `clean()`, `unique=True`,
  `UniqueConstraint`, `validators`.

#### View handling example:

```python
def submit_form(request):
    form = RegisterForm(request.POST or None)
    if request.method == "POST" and form.is_valid():
        # work with form.cleaned_data
        ...
    return render(request, "form.html", {"form": form})
```

#### Practical rules:

1. Validation must always exist on the server side (client-side is UX only).
2. Field-local logic -> `clean_<field>()`.
3. Multi-field logic -> `clean()`.
4. Reusable rules -> separate validators.
5. Domain-critical rules should be enforced at DB level too (constraints), not
   only in forms.

#### Conclusion:

A major strength of Django Forms is structured multi-level validation. It
improves data quality control, provides clear user errors, and keeps form
processing stable in production backends.

</details>

<details>
<summary>37. What are custom validators in Django, and how do you reuse them?</summary>

#### Django

Custom validators in Django are functions or classes that check a field value
against your rules and raise `ValidationError` if the data does not pass the
check.

#### Why they are needed:

1. **Rule reuse**

- One validation rule can be applied across many forms/models.

2. **Single source of truth**

- The business rule is not duplicated throughout the codebase.

3. **Cleaner architecture**

- Validation logic is extracted from views/forms into a separate layer.

#### Function-based validator example:

```python
from django.core.exceptions import ValidationError

def validate_corporate_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Only corporate email is allowed.")
```

Usage in a model:

```python
from django.db import models
from .validators import validate_corporate_email

class Employee(models.Model):
    email = models.EmailField(validators=[validate_corporate_email])
```

Usage in a form:

```python
from django import forms
from .validators import validate_corporate_email

class InviteForm(forms.Form):
    email = forms.EmailField(validators=[validate_corporate_email])
```

#### Class-based validator example:

```python
from django.core.exceptions import ValidationError

class MinWordsValidator:
    def __init__(self, min_words=3):
        self.min_words = min_words

    def __call__(self, value):
        if len(value.split()) < self.min_words:
            raise ValidationError(f"Minimum {self.min_words} word(s).")
```

```python
description = models.TextField(validators=[MinWordsValidator(5)])
```

#### Where to place them:

- `app/validators.py` or `app/domain/validators.py`
- In large projects, separate modules by domain.

#### Practical rules:

1. A validator should perform one specific check.
2. Error messages should be clear for users.
3. For critical rules, duplicate enforcement at DB level too
   (`UniqueConstraint`, check constraints).
4. Write validator tests separately from view tests.

#### Conclusion:

Custom validators are the right way to centralize validation business rules in
Django. They make code cleaner, more reusable, and reduce the risk of rule
desynchronization across different parts of the system.

</details>

<details>
<summary>38. How do you handle file uploads?</summary>

#### Django

File uploads in Django are handled through `request.FILES`,
`FileField`/`ImageField`, and properly configured `MEDIA_ROOT`/`MEDIA_URL`.

#### What is required for upload:

1. A file field in a form or model.
2. `enctype="multipart/form-data"` in the HTML form.
3. Passing `request.FILES` into the form.
4. Media settings configured in `settings.py`.

#### Model example:

```python
from django.db import models

class Document(models.Model):
    title = models.CharField(max_length=200)
    file = models.FileField(upload_to="documents/%Y/%m/")
```

#### ModelForm example:

```python
from django import forms
from .models import Document

class DocumentForm(forms.ModelForm):
    class Meta:
        model = Document
        fields = ["title", "file"]
```

#### View example:

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
  <button type="submit">Upload</button>
</form>
```

#### Media settings:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Security and production practices:

1. Validate file type, size, and extension.
2. Do not trust the original filename from the client.
3. Restrict access to private files through permissions.
4. For production, use external storage (S3-compatible) or a dedicated file
   server.
5. Scan potentially dangerous files (if the business case is risk-sensitive).

#### Common mistakes:

1. Forgetting `enctype="multipart/form-data"` -> `request.FILES` is empty.
2. Passing only `request.POST` without `request.FILES`.
3. Mixing static and media.
4. Not validating size/type and getting security or overload risks.

#### Conclusion:

In Django, file upload works reliably if you follow the basic rules: correct
form, `request.FILES`, validators, and file access control in production.

</details>

<details>
<summary>39. What is Django ORM?</summary>

#### Django

Django ORM (Object-Relational Mapping) is a data access layer that lets you work
with the database through Python objects instead of writing SQL manually in most
typical scenarios.

#### Core ORM idea:

1. **Python model = DB table**
2. **Model instance = table row**
3. **Model field = table column**
4. **QuerySet = SQL query(ies) generated by the ORM**

#### Example:

```python
# models.py
class Article(models.Model):
    title = models.CharField(max_length=200)
    is_published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

```python
# create
Article.objects.create(title="Django ORM", is_published=True)

# read
articles = Article.objects.filter(is_published=True).order_by("-created_at")

# update
article = Article.objects.get(pk=1)
article.title = "Updated title"
article.save()

# delete
article.delete()
```

#### Benefits of Django ORM:

1. **Fast development** - less boilerplate SQL.
2. **Readable code** - queries are expressed declaratively.
3. **Security** - query parameterization reduces SQL injection risk.
4. **Portability** - the same code works across different DB engines (mostly).
5. **Django integration** - forms, admin, migrations, validators.

#### Important concepts:

- `QuerySet` is lazy: the query is executed only when data is needed.
- `select_related` and `prefetch_related` help avoid N+1 issues.
- `annotate`, `aggregate`, `F`, `Q`, `Subquery` are used for more complex
  queries.

#### ORM limitations:

1. Very complex SQL constructs are sometimes easier to write with raw SQL.
2. Without profiling, it is easy to get inefficient queries.
3. Incorrect relation usage can seriously hurt performance.

#### When to use raw SQL:

- DB-engine-specific optimizations.
- Complex analytics/CTE/window functions where ORM code becomes unreadable.
- Migration/operational tasks where exact SQL control is required.

#### Conclusion:

Django ORM is one of the framework's key strengths: fast, safe, and convenient
for most business cases. But for production-grade results, you must understand
what SQL the ORM generates and optimize queries in time.

</details>

<details>
<summary>40. What is a model, and how do you create one?</summary>

#### Django

A Django model (`Model`) is a Python class that describes the data structure and
maps to a database table. Through models, you define fields, relations, and
data-level rules.

#### What a model is:

1. **Database schema description in Python**

- Model fields (`CharField`, `IntegerField`, `DateTimeField`, etc.) map to table
  columns.

2. **Domain entity layer**

- A model represents a business object: `User`, `Order`, `Invoice`, `Product`.

3. **ORM integration**

- Create, read, update, and delete records through `Model.objects`.

#### Model example:

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

#### How to create a model step by step:

1. Add the class to `app/models.py`.
2. Make sure the app is included in `INSTALLED_APPS`.
3. Create a migration:

```bash
python manage.py makemigrations
```

4. Apply the migration to the DB:

```bash
python manage.py migrate
```

#### Basic practices:

1. Use clear field names and constraints (`unique`, `db_index`).
2. Add service fields: `created_at`, `updated_at`.
3. Define `__str__` for readability in admin and shell.
4. Enforce domain-critical invariants at DB level (constraints), not only in
   views/forms.

#### Common mistakes:

1. Storing "everything as text" and ignoring data types.
2. Missing indexes for filter/search fields.
3. Mixing high-level business logic directly into the model without structure.
4. Delayed migrations that diverge across environments.

#### Conclusion:

In Django, the model is the foundation of data work. Well-designed models define
the performance, reliability, and scalability of the entire project.

</details>

<details>
<summary>41. What are ForeignKey, OneToOneField, and ManyToManyField?</summary>

#### Django

`ForeignKey`, `OneToOneField`, and `ManyToManyField` are relationship types
between models in Django ORM. They define how entities are connected in the DB.

#### 1. ForeignKey (one-to-many, 1:N)

- One "parent" object can have many "children".
- Each child record points to only one parent.

Example:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Use case: one author -> many books.

#### 2. OneToOneField (one-to-one, 1:1)

- Each record in model A corresponds to at most one record in model B.
- Essentially `ForeignKey(unique=True)` with clearer semantics.

Example:

```python
from django.conf import settings

class Profile(models.Model):
    user = models.OneToOneField(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    bio = models.TextField(blank=True)
```

Use case: one user -> one profile.

#### 3. ManyToManyField (many-to-many, M:N)

- Records from both tables can have many links to each other.
- Django creates an intermediate table automatically (or via `through=`).

Example:

```python
class Tag(models.Model):
    name = models.CharField(max_length=50, unique=True)

class Article(models.Model):
    title = models.CharField(max_length=200)
    tags = models.ManyToManyField(Tag, related_name="articles")
```

Use case: an article has many tags, and a tag belongs to many articles.

#### How to choose the relationship type:

1. `ForeignKey` - when there is a clear "owner" and multiple child records.
2. `OneToOneField` - when an extension entity should exist in only one instance.
3. `ManyToManyField` - when both sides can have many counterparts.

#### `on_delete` nuance for ForeignKey/OneToOne:

- `CASCADE` - delete child records with the parent.
- `PROTECT` - prevent deletion if dependencies exist.
- `SET_NULL` - clear the reference (field must be `null=True`).

#### Conclusion:

These three fields are the foundation of relational data modeling in Django. The
correctly chosen relationship type simplifies queries, migrations, and long-term
maintenance of the domain model.

</details>

<details>
<summary>42. What types of model inheritance exist?</summary>

#### Django

Django has three main types of model inheritance: **Abstract Base Classes**,
**Multi-table inheritance**, and **Proxy models**. They solve different tasks
and have different impact on the DB schema.

#### 1. Abstract Base Class (abstract inheritance)

- The parent model does not create its own DB table.
- Its fields are copied into child models.

Example:

```python
class TimeStampedModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True

class Article(TimeStampedModel):
    title = models.CharField(max_length=200)
```

When to use:

- For shared fields/methods across many models.
- The most common and most practical option in production.

#### 2. Multi-table inheritance (inheritance with separate tables)

- Each model in the inheritance chain has its own table.
- Django creates a `OneToOne` relation between parent and child.

Example:

```python
class Person(models.Model):
    name = models.CharField(max_length=120)

class Employee(Person):
    salary = models.DecimalField(max_digits=10, decimal_places=2)
```

When to use:

- When you need a real entity hierarchy in the DB.
- When it is important to keep separate tables for base and specialized models.

Drawback:

- Additional JOINs and more complex queries.

#### 3. Proxy model

- No new table is created.
- Works with the same table as the base model.
- Lets you change Python behavior (methods, manager, ordering) without changing
  the DB schema.

Example:

```python
class Order(models.Model):
    status = models.CharField(max_length=20)

class OpenOrder(Order):
    class Meta:
        proxy = True
        ordering = ["id"]
```

When to use:

- You need a different manager/behavior for the same model.
- You need a different representation in Django Admin without changing table
  structure.

#### Quick choice:

1. Shared fields without a separate table -> **abstract**.
2. Real data hierarchy with separate tables -> **multi-table**.
3. Different Python behavior without DB changes -> **proxy**.

#### Practical advice:

By default, choose **abstract base class**.  
Use `multi-table` carefully, only when dictated by the domain model, not just
for a "nice" hierarchy.

#### Conclusion:

The inheritance type in Django should be chosen by goal: field reuse, physical
table hierarchy, or behavior-only changes. The right choice simplifies the DB
schema and long-term project maintenance.

</details>

<details>
<summary>43. What is the Meta class used for?</summary>

#### Django

The inner `Meta` class in a Django model is used to configure model behavior at
the ORM and DB level without changing the model's business logic.

#### What is usually set in `Meta`:

1. **`ordering`** - default sorting.
2. **`db_table`** - custom DB table name.
3. **`verbose_name`, `verbose_name_plural`** - human-readable names in admin.
4. **`indexes`** - indexes for performance.
5. **`constraints`** - business constraints at DB level.
6. **`unique_together` / `UniqueConstraint`** - uniqueness of field
   combinations.
7. **`abstract` / `proxy`** - model inheritance type.

#### Example:

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
        verbose_name = "Product"
        verbose_name_plural = "Products"
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

#### Why `Meta` is important:

1. **Performance**

- Indexes and proper constraints reduce query cost.

2. **Data integrity**

- Constraints protect against invalid records, even if view/form validation is
  missed somewhere.

3. **Schema control**

- Explicit control of tables and rules in migrations.

4. **Admin usability**

- Human-readable model names in back-office.

#### Practical recommendations:

1. Use `UniqueConstraint` instead of deprecated `unique_together`.
2. Add indexes only on truly "hot" fields used for filtering/sorting.
3. Keep business-critical rules at DB level via `constraints`.
4. Do not overuse `db_table` unless explicit naming is required.

#### Conclusion:

`Meta` is the configuration center for model ORM behavior. Through it, you
control ordering, indexes, constraints, and DB schema quality, which directly
affects reliability and performance of a Django project.

</details>

<details>
<summary>44. What is the difference between `null=True` and `blank=True`?</summary>

#### Django

`null=True` and `blank=True` solve different tasks and work at different levels:

- `null=True` - **database level** (whether `NULL` can be stored).
- `blank=True` - **form/admin validation level** (whether a field can be empty).

#### `null=True`:

1. Allows writing `NULL` into the DB column.
2. Affects table schema and migrations.
3. Critical for fields where "missing value" must be stored as SQL `NULL`.

#### `blank=True`:

1. Allows leaving the field empty in forms, ModelForm, Django Admin.
2. Does not directly change DB column type.
3. Affects `form.is_valid()`, not SQL level.

#### Examples:

```python
class Profile(models.Model):
    bio = models.TextField(blank=True)  # optional in forms
    birth_date = models.DateField(null=True, blank=True)  # NULL in DB and empty in forms allowed
```

#### Important nuance for strings (`CharField`, `TextField`):

- In Django, you usually **do not set `null=True`** for string fields.
- Recommended practice: use empty string `""`, not `NULL`.
- So usually: `CharField(..., blank=True)` without `null=True`.

#### Quick matrix:

1. `null=False, blank=False` -> required both in DB and forms.
2. `null=True, blank=False` -> DB may contain `NULL`, but form requires value.
3. `null=False, blank=True` -> form allows empty, but DB stores non-`NULL`
   (often `""`).
4. `null=True, blank=True` -> maximally optional field (both form and DB).

#### Practical recommendations:

1. For `DateField`, `DateTimeField`, `ForeignKey`, and numeric fields, both are
   often needed: `null=True, blank=True`.
2. For `CharField/TextField`, `blank=True` is usually enough.
3. Keep a consistent project policy to avoid chaos between `NULL` and `""`.
4. Remember: wrong choice complicates filtering and analytics.

#### Conclusion:

`null` controls DB storage, `blank` controls Django-form validation. These are
different behavior axes and should be set consciously for your domain model.

</details>

<details>
<summary>45. What is the difference between CharField and TextField?</summary>

#### Django

`CharField` and `TextField` both store text, but they have different use cases
and model/DB-level constraints.

#### `CharField`:

1. Intended for short/medium text.
2. **Requires** `max_length`.
3. Fits fields where length should be controlled: name, slug, title, code,
   email, phone.

Example:

```python
title = models.CharField(max_length=200)
sku = models.CharField(max_length=64, unique=True)
```

#### `TextField`:

1. Intended for long free-form text.
2. Does not require `max_length` at model level (you can add validation).
3. Fits descriptions, article content, notes, comments.

Example:

```python
description = models.TextField(blank=True)
content = models.TextField()
```

#### Key differences:

1. **Length constraint**

- `CharField`: always has `max_length`.
- `TextField`: no hard limit by default.

2. **Data semantics**

- `CharField`: structured short text.
- `TextField`: large unstructured text.

3. **Forms/admin**

- `CharField` usually renders as `input`.
- `TextField` usually renders as `textarea`.

4. **Indexing and performance**

- Short indexed fields are usually more logical as `CharField`.
- For large texts, indexing depends on DB engine and often needs separate
  approaches (full-text search).

#### Practical tech-lead rules:

1. If the value has a natural length limit -> choose `CharField`.
2. If text is potentially large/free-form -> `TextField`.
3. Do not use `TextField` "just in case" when `CharField` is enough.
4. For searching in large texts, plan a separate search strategy (PostgreSQL
   FTS, Elasticsearch/OpenSearch, etc.).

#### Conclusion:

`CharField` is controlled short text, `TextField` is large content. Choosing the
right field affects validation, form UX, indexing, and query performance.

</details>

<details>
<summary>46. What are model managers, and how do you create a custom one?</summary>

#### Django

A Django `Model Manager` is the "entry point" for model queries through ORM. By
default, every model has the `objects` manager, but you can create custom
managers with domain-specific methods.

#### Why custom managers are useful:

1. **Centralized query logic**

- Avoid duplicating the same `filter(...)` across different views/services.

2. **Readable model API**

- For example: `Article.objects.published().recent()`.

3. **Control over the "default" dataset**

- For example, hide soft-deleted records.

#### Basic manager example:

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

Usage:

```python
Article.objects.published()
Article.objects.recent()
```

#### Manager + QuerySet combination (better scalability):

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

#### Practical recommendations:

1. Put only data-selection logic in manager/queryset.
2. Keep business orchestration in a service layer.
3. Use domain-specific method names (`active`, `paid`, `for_user`).
4. Do not make manager behavior "magical"; it should be obvious.

#### Common mistakes:

1. Duplicating the same filters across the codebase.
2. Mixing heavy business logic into manager methods.
3. Overriding the default manager so admin/migrations behave unexpectedly.

#### Conclusion:

Model managers are the right place for reusable ORM queries. A custom manager
makes code cleaner and queries more consistent across the project.

</details>

<details>
<summary>47. What are migrations, and why are they needed?</summary>

#### Django

Migrations in Django are a controlled history of database schema changes stored
in project code and applied with `makemigrations` and `migrate` commands.

#### What migrations provide:

1. **DB versioning**

- Changes to tables, fields, indexes, and constraints are captured as
  instruction files.

2. **Environment reproducibility**

- Dev, staging, and production receive the same DB schema.

3. **Safe schema evolution**

- Instead of manual SQL in "notes", the team gets a formal change process.

4. **Team collaboration**

- Migrations are committed to git and reviewed together with code.

#### How it works:

1. You change a model in `models.py`.
2. `python manage.py makemigrations` generates a migration file.
3. `python manage.py migrate` applies changes to the DB.
4. Django stores applied state in the `django_migrations` service table.

#### Examples of typical changes via migrations:

- Add/remove a field.
- Change a field type.
- Create an index.
- Add a `UniqueConstraint` or `CheckConstraint`.
- Rename a model/field.

#### Data migrations:

Besides schema changes, you can run data migrations (`RunPython`), for example:

- populate a new field,
- move data between columns,
- normalize existing records.

#### Practical rules:

1. Commit migrations together with model changes.
2. Do not edit old migrations if they are already applied in shared
   environments.
3. Validate migrations on staging before production.
4. For large tables, plan backward-compatible rollout (expand/contract).

#### Common mistakes:

1. Running code without up-to-date migrations.
2. Forgetting to commit migration files.
3. Performing dangerous blocking operations on large tables without a plan.
4. Editing already-applied migrations and breaking schema history.

#### Conclusion:

Migrations are a "version control system" for DB in Django. They are critical
for reliable deploys, team collaboration, and predictable data evolution.

</details>

<details>
<summary>48. What is the difference between `makemigrations` and `migrate`?</summary>

#### Django

`makemigrations` and `migrate` are two different phases of migration workflow:

- `makemigrations` **creates** migration files (the change plan).
- `migrate` **applies** those changes to the database.

#### `makemigrations`:

1. Analyzes changes in `models.py`.
2. Generates Python migration files in `app/migrations/`.
3. Does not change DB directly.

Command:

```bash
python manage.py makemigrations
```

#### `migrate`:

1. Reads migration files.
2. Executes SQL operations in DB (CREATE/ALTER/DROP, etc.).
3. Marks applied migrations in the `django_migrations` table.

Command:

```bash
python manage.py migrate
```

#### Simple workflow:

1. Changed models.
2. Ran `makemigrations`.
3. Reviewed generated migration.
4. Ran `migrate`.
5. Committed code + migration files.

#### Analogy:

- `makemigrations` = "write instructions".
- `migrate` = "execute instructions".

#### Useful commands:

```bash
python manage.py showmigrations
python manage.py sqlmigrate app_name 0001
```

- `showmigrations` shows which migrations are applied.
- `sqlmigrate` shows SQL that will be executed.

#### Common mistakes:

1. Running `migrate` without creating migrations after model changes.
2. Running `makemigrations` but not committing migration files.
3. Confusing local DB state with staging/production state.
4. Ignoring migration conflicts in team development.

#### Conclusion:

`makemigrations` prepares changes, `migrate` applies them. A stable deploy
process requires both steps, executed in sequence and under control.

</details>

<details>
<summary>49. How do you connect PostgreSQL or another DB?</summary>

#### Django

Database connection in Django is configured via `DATABASES` in `settings.py`.
For production, PostgreSQL is the most common choice, less often MySQL/MariaDB.

#### 1. Install DB driver

For PostgreSQL (recommended modern option):

```bash
pip install psycopg[binary]
```

Alternative: `psycopg2-binary`.

#### 2. Configure `DATABASES` in `settings.py`

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

#### 3. Run migrations

```bash
python manage.py migrate
```

#### Connection via env variables (recommended):

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

#### Other supported engines:

1. SQLite (default for local/prototypes)
2. PostgreSQL (main production choice)
3. MySQL / MariaDB
4. Oracle

#### Production recommendations:

1. Do not store DB passwords in repository.
2. Enable DB SSL where applicable.
3. Configure connection pooling (PgBouncer or DB-side parameters).
4. Add health checks and monitoring for latency/locks/slow queries.
5. Use separate access roles (least privilege).

#### Common mistakes:

1. Wrong `ENGINE` or missing driver.
2. Config works locally but fails in CI/prod due to env vars.
3. Using SQLite in production under concurrent load.
4. Missing timeouts/pooling under load.

#### Conclusion:

To connect PostgreSQL in Django, you need three steps: driver, `DATABASES`,
migrations. For production, the critical parts are env config, secure
credentials, SSL, and connection performance control.

</details>

<details>
<summary>50. What is a QuerySet? What is lazy evaluation?</summary>

#### Django

A `QuerySet` in Django ORM is an object that represents a set of DB records and
a chain of operations on them (`filter`, `exclude`, `order_by`, `annotate`,
etc.).

#### What is important to understand about QuerySet:

1. It is **lazy** by default.
2. Building a QuerySet does not execute SQL immediately.
3. SQL runs only when data is actually needed.

#### Lazy example:

```python
qs = Article.objects.filter(is_published=True).order_by("-created_at")
# At this stage, the DB query has NOT been executed yet
```

#### When QuerySet gets materialized (SQL is executed):

1. Iteration:

```python
for article in qs:
    ...
```

2. Conversion to list:

```python
items = list(qs)
```

3. Getting length/boolean value:

```python
len(qs)
bool(qs)
```

4. Calls like:

- `first()`, `last()`, `exists()`, `count()`, `get()`
- slicing (often with `LIMIT/OFFSET`), e.g. `qs[:10]`

#### Benefits of lazy evaluation:

1. **Query optimization**

- You can build a complex queryset step by step before execution.

2. **Flexibility**

- One base queryset can be reused with different conditions.

3. **Fewer unnecessary DB hits**

- If queryset is never used, query is never executed.

#### Common mistakes:

1. Calling querysets inside loops and getting N+1 queries.
2. Iterating the same queryset multiple times without caching the result.
3. Confusing `count()` and `len(qs)` (behavior/cost may differ).

#### Practical advice:

1. Use `select_related()` / `prefetch_related()` for relations.
2. If result is needed many times within one flow, materialize it:
   `items = list(qs)`.
3. For existence checks, use `exists()` instead of full iteration.
4. Profile SQL (Django Debug Toolbar, DB logs), do not rely on intuition.

#### Conclusion:

`QuerySet` is the central abstraction of Django ORM, and lazy evaluation is its
key optimization. Understanding when SQL is executed is critical for performance
in real Django projects.

</details>

<details>
<summary>51. How do `filter()`, `exclude()`, and `get()` work?</summary>

#### Django

`filter()`, `exclude()`, and `get()` are core Django ORM methods for data
retrieval. They look similar in syntax, but have different behavior and
guarantees.

#### `filter()`:

- Returns a `QuerySet` with all records matching the condition.
- If no matches are found, returns an empty `QuerySet` (no exception).

```python
active_users = User.objects.filter(is_active=True)
cheap_products = Product.objects.filter(price__lt=1000)
```

#### `exclude()`:

- Returns a `QuerySet` with records that do **not** match the condition.

```python
non_archived = Article.objects.exclude(status="archived")
```

#### `get()`:

- Returns **one** model object.
- Expects exactly one match.
- If 0 or >1 results are found, raises an exception.

```python
user = User.objects.get(pk=1)
```

#### Exceptions for `get()`:

1. `Model.DoesNotExist` - nothing found.
2. `Model.MultipleObjectsReturned` - more than one record found.

Safe handling example:

```python
from django.http import Http404

def profile_view(request, user_id):
    try:
        user = User.objects.get(pk=user_id)
    except User.DoesNotExist:
        raise Http404("User not found")
```

Or shorter:

```python
from django.shortcuts import get_object_or_404
user = get_object_or_404(User, pk=user_id)
```

#### When to use which:

1. **`filter()`** - when there may be many results or none.
2. **`exclude()`** - when you need to filter out part of the data.
3. **`get()`** - when you guarantee a unique result (PK, unique field).

#### Practical advice:

1. Do not use `get()` where uniqueness is not guaranteed.
2. For existence checks, use `exists()`, not `get()+try/except`.
3. Combine conditions with `Q` for complex logic.

#### Conclusion:

`filter()` and `exclude()` work with record sets via QuerySet, while `get()`
works with a single object and strict uniqueness requirements. Choosing the
right method reduces errors and simplifies edge-case handling.

</details>

<details>
<summary>52. What is the difference between `get()` and `filter()`?</summary>

#### Django

`get()` and `filter()` both query data in ORM, but they have fundamentally
different semantics: one returns **a single object**, the other returns **a set
of objects (QuerySet)**.

#### `get()`:

1. Returns one model instance.
2. Expects exactly one match.
3. Raises exceptions if 0 or more than 1 records are found.

```python
user = User.objects.get(pk=10)
```

Possible exceptions:

- `User.DoesNotExist`
- `User.MultipleObjectsReturned`

#### `filter()`:

1. Returns a `QuerySet`.
2. May return 0, 1, or many records.
3. Does not raise exception when nothing is found.

```python
users = User.objects.filter(is_active=True)
```

#### Key differences:

1. **Result type**

- `get()` -> one object.
- `filter()` -> QuerySet.

2. **Behavior when data is missing**

- `get()` -> exception.
- `filter()` -> empty QuerySet.

3. **Usage scenario**

- `get()` -> unique fields (`id`, `uuid`, `email` with `unique=True`).
- `filter()` -> conditional search where matches may be many.

#### Practical example:

```python
# correct: unique lookup
order = Order.objects.get(id=order_id)

# correct: user's order list
orders = Order.objects.filter(user=request.user).order_by("-created_at")
```

#### Common mistakes:

1. Using `get()` for a non-unique field (risk of `MultipleObjectsReturned`).
2. Expecting a single object from `filter()` and forgetting `.first()` or
   `get()`.
3. Not handling `get()` exceptions in API/view.

#### Conclusion:

`get()` is for a single unique record, `filter()` is for collections and
flexible search. If you are unsure about result cardinality, it is safer to
start with `filter()`.

</details>

<details>
<summary>53. How do you get all records or a single record?</summary>

#### Django

In Django ORM, there are different methods to fetch all records or one specific
record. The choice depends on whether you expect a collection or a single
result.

#### Get all records:

1. **All records of a model**

```python
articles = Article.objects.all()
```

2. **All records by condition**

```python
articles = Article.objects.filter(is_published=True)
```

3. **Optimized selection of specific fields**

```python
articles = Article.objects.values("id", "title")
```

#### Get one record:

1. **Exactly one record via `get()`**

```python
article = Article.objects.get(pk=article_id)
```

Suitable when uniqueness is guaranteed.

2. **Safe option in a web view**

```python
from django.shortcuts import get_object_or_404

article = get_object_or_404(Article, pk=article_id)
```

3. **First record from queryset**

```python
article = Article.objects.filter(is_published=True).first()
```

Returns an object or `None`, without exceptions.

#### When to use what:

1. Collection for lists/tables -> `all()` / `filter()`.
2. One unique record -> `get()`.
3. One record in web flow with 404 -> `get_object_or_404()`.
4. Optional single result -> `first()`.

#### Common mistakes:

1. Using `get()` for a non-unique field.
2. Pulling `all()` without filters/pagination on large tables.
3. Not handling `DoesNotExist` in API/view.

#### Conclusion:

For "all records", use QuerySet (`all/filter`); for "one record", use `get()` or
safe wrappers (`get_object_or_404`, `first()`) depending on error-handling and
UX requirements.

</details>

<details>
<summary>54. What is the difference between `select_related()` and `prefetch_related()`?</summary>

#### Django

`select_related()` and `prefetch_related()` are used for ORM optimization to
avoid the N+1 query problem when working with related models.

#### `select_related()`:

1. Works for **ForeignKey** and **OneToOne** relations (the "single" side).
2. Performs an **SQL JOIN** and fetches related data in one query.
3. Efficient for single-valued relations.

Example:

```python
orders = Order.objects.select_related("customer").all()
for order in orders:
    print(order.customer.email)  # no additional queries
```

#### `prefetch_related()`:

1. Works for **ManyToMany**, reverse ForeignKey, and can also be used for
   FK/O2O.
2. Performs multiple queries (main + additional), then "joins" results in
   Python.
3. Efficient for multi-valued relations.

Example:

```python
articles = Article.objects.prefetch_related("tags").all()
for article in articles:
    print([tag.name for tag in article.tags.all()])  # no N+1
```

#### Key difference:

1. **Mechanism**

- `select_related()` -> JOIN in one SQL query.
- `prefetch_related()` -> multiple SQL queries + merge in Python.

2. **Relation types**

- `select_related()` -> FK/O2O.
- `prefetch_related()` -> M2M, reverse FK (and others when needed).

3. **Data volume**

- `select_related()` may "inflate" rows due to JOINs.
- `prefetch_related()` is better for child object collections.

#### Combined usage:

```python
orders = (
    Order.objects
    .select_related("customer")
    .prefetch_related("items", "items__product")
)
```

#### Practical selection rule:

1. Need a field from FK/O2O -> start with `select_related`.
2. Need a list of related objects (M2M/reverse) -> use `prefetch_related`.
3. Profile queries (debug toolbar/logs), do not guess by intuition.

#### Common mistakes:

1. Using neither method and getting N+1.
2. Applying `select_related()` to M2M (does not solve the problem).
3. Calling `.all()` on a related manager inside a loop without prefetch.

#### Conclusion:

`select_related()` optimizes single relations via JOIN, while
`prefetch_related()` optimizes collection relations via additional queries. The
right combination of both gives the biggest performance gain in ORM code.

</details>

<details>
<summary>55. How do you optimize ORM queries (`annotate`, `aggregate`, `F()`, `Q()`)?</summary>

#### Django

ORM query optimization in Django is based on one idea: move heavy computation to
the DB and reduce both query count and fetched data volume.

#### 1. `annotate()` - per-row calculations

- Adds a "virtual" field to each object in a queryset.
- Useful for counters, sums, last-activity timestamps, etc.

```python
from django.db.models import Count

authors = Author.objects.annotate(books_count=Count("books"))
```

#### 2. `aggregate()` - summary over the whole queryset

- Returns a dictionary with aggregated values.

```python
from django.db.models import Avg, Sum

stats = Order.objects.aggregate(
    total_revenue=Sum("amount"),
    avg_revenue=Avg("amount"),
)
```

#### 3. `F()` - field-level operations in DB

- Lets you update values without reading objects into Python.
- Reduces race conditions in concurrent updates.

```python
from django.db.models import F

Product.objects.filter(pk=product_id).update(stock=F("stock") - 1)
```

#### 4. `Q()` - complex condition logic (`AND/OR/NOT`)

- For cases where simple `filter(a=..., b=...)` is not enough.

```python
from django.db.models import Q

users = User.objects.filter(
    Q(is_active=True) & (Q(role="admin") | Q(role="manager"))
).exclude(Q(email__isnull=True) | Q(email=""))
```

#### Combined example:

```python
from django.db.models import Count, Q

articles = (
    Article.objects
    .filter(is_published=True)
    .annotate(comments_count=Count("comments", filter=Q(comments__is_approved=True)))
    .order_by("-comments_count")
)
```

#### Practical optimization rules:

1. Compute in DB (`annotate/aggregate`), not in Python loops.
2. For bulk updates, use `update(..., F(...))`.
3. For complex conditions, use `Q` instead of multiple separate queries.
4. Combine with `select_related/prefetch_related` to avoid N+1.
5. Fetch only needed fields (`only`, `values`, `values_list`).

#### How to measure effect:

1. Inspect SQL via `queryset.query` or `django-debug-toolbar`.
2. Compare query count before/after.
3. Check execution plan on production-like DB (`EXPLAIN ANALYZE`).

#### Common mistakes:

1. Doing aggregations in Python after `list(qs)` instead of SQL.
2. Calling `save()` in a loop instead of one `update()`.
3. Building overly complex annotations without proper DB indexes.

#### Conclusion:

`annotate`, `aggregate`, `F`, and `Q` are key tools for high-performance ORM
code. They reduce query count, remove unnecessary Python-side computation, and
make DB work more stable under load.

</details>

<details>
<summary>56. How do you override `save()` and `delete()` methods?</summary>

#### Django

In Django, you can override model `save()` and `delete()` to add extra logic
before/after saving or deleting records.

#### How to override `save()`:

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

Key rule: always call `super().save(*args, **kwargs)`.

#### How to override `delete()`:

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

#### What to remember:

1. `QuerySet.update()` does not call `save()`.
2. `QuerySet.delete()` does not invoke each object's custom `delete()` in the
   same way as direct instance calls.
3. So logic critical for data integrity should also be enforced at DB/service
   level.

#### When overriding is appropriate:

1. Generating derived fields (slug, normalized value).
2. Local model invariants that do not depend on external services.
3. Careful cleanup of related local resources.

#### When another approach is better:

1. Complex business logic or orchestration across multiple models -> service
   layer.
2. Cross-module side effects -> signals (carefully) or domain events.
3. Bulk operations -> dedicated bulk commands instead of instance methods.

#### Practical rules:

1. Keep `save()/delete()` short and predictable.
2. Avoid slow external HTTP calls inside them.
3. Document side effects so the team does not get "magic" behavior.
4. Cover these places with tests (create/update/delete scenarios).

#### Conclusion:

Overriding `save()` and `delete()` is powerful but sensitive. Use it for local
model logic; keep complex domain behavior in a service layer for transparency
and control.

</details>

<details>
<summary>57. How does cascade deletion (`CASCADE`) work?</summary>

#### Django

Cascade deletion (`models.CASCADE`) means: if a "parent" object is deleted,
Django automatically deletes all related "child" records.

#### Where it is used:

- In `ForeignKey` and `OneToOneField` via the `on_delete` parameter.

#### Example:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

What happens:

- `author.delete()` -> Django deletes the author and all their books.

#### When `CASCADE` is appropriate:

1. Child data has no meaning without parent data.
2. You need to guarantee no orphan records.
3. The domain lifecycle of dependent entities is simple.

#### Potential risks:

1. Accidental mass deletion of large amounts of data.
2. More difficult audit/recovery after mistakes.
3. Unexpected side effects in related domains.

#### `on_delete` alternatives:

1. `PROTECT` - prevents parent deletion if dependencies exist.
2. `SET_NULL` - sets child field to `NULL` (`null=True` required).
3. `SET_DEFAULT` - sets a default value.
4. `RESTRICT` - blocks deletion when references exist (similar to strict
   protect).
5. `DO_NOTHING` - responsibility is on DB/developer side.

#### Practical recommendations:

1. For critical business data, `PROTECT/RESTRICT` is often preferable.
2. For clearly dependent technical entities (e.g., temporary records), `CASCADE`
   often fits.
3. Before mass delete, verify exactly what will be deleted.
4. Consider soft delete if historical audit is required.

#### Conclusion:

`CASCADE` is a convenient integrity mechanism, but behavior is aggressive. Use
it where child-data lifecycle fully depends on the parent object.

</details>

<details>
<summary>58. How do transactions work in Django?</summary>

#### Django

Transactions in Django guarantee that a group of DB changes is executed as a
single unit: either all changes are applied (`commit`) or none (`rollback`) if
an error occurs.

#### Main tool:

- `transaction.atomic()`

#### Basic example:

```python
from django.db import transaction

@transaction.atomic
def create_order(user, items):
    order = Order.objects.create(user=user)
    for item in items:
        OrderItem.objects.create(order=order, product=item["product"], qty=item["qty"])
    return order
```

If an exception happens inside, all changes in the block are rolled back.

#### Context manager:

```python
from django.db import transaction

def transfer(from_acc, to_acc, amount):
    with transaction.atomic():
        from_acc.balance -= amount
        to_acc.balance += amount
        from_acc.save()
        to_acc.save()
```

#### Nested transactions and savepoints:

- Nested `atomic()` blocks create savepoints.
- An error in an inner block can roll back only part of operations to that
  savepoint.

#### `ATOMIC_REQUESTS` mode:

In `settings.py`, you can enable transaction-per-request mode:

```python
DATABASES["default"]["ATOMIC_REQUESTS"] = True
```

This is convenient, but not always optimal for performance on complex endpoints.

#### Practical recommendations:

1. Wrap in `atomic()` only truly related operations.
2. Keep transactions short (minimal external calls inside).
3. Do not make HTTP/API calls inside transactions.
4. For concurrent scenarios, use `select_for_update()`.

#### Row-locking example:

```python
with transaction.atomic():
    account = Account.objects.select_for_update().get(pk=account_id)
    account.balance = F("balance") - amount
    account.save(update_fields=["balance"])
```

#### Common mistakes:

1. Doing part of operation before `atomic()` and part after.
2. Long transactions that hold locks and block other queries.
3. Assuming transaction covers external systems (queues, third-party APIs).
4. Ignoring DB isolation levels in high-concurrency scenarios.

#### Conclusion:

Transactions in Django are a core data-consistency mechanism.
`transaction.atomic()` should be standard for critical multi-step operations,
especially in finance, inventory, and workflow domains.

</details>

<details>
<summary>59. Does Django support NoSQL?</summary>

#### Django

Short answer: Django is **natively oriented toward relational databases**
(PostgreSQL, MySQL, SQLite, Oracle) via its ORM. NoSQL is not supported
out-of-the-box at the same level, but integration is possible.

#### What this means in practice:

1. **Django ORM is SQL-first**

- Most features (migrations, relations, admin, constraints) are designed for
  SQL.

2. **NoSQL can be connected via third-party libraries**

- For MongoDB and other solutions, there are third-party adapters/ODMs, but
  compatibility with Django ecosystem is often incomplete.

3. **Most common production approach is hybrid**

- Core transactional model in PostgreSQL.
- NoSQL storage for specialized tasks (cache, documents, search, events).

#### Typical NoSQL roles in Django projects:

1. Redis - cache, rate limiting, queue broker, sessions.
2. Elasticsearch/OpenSearch - full-text search and analytical queries.
3. Document DBs - separate domains with flexible schema (when needed).

#### When SQL in Django is usually better:

- Complex relations between entities.
- Transactions and strict consistency guarantees.
- Lots of standard CRUD + admin + clear domain model.

#### When NoSQL may be appropriate:

- Very flexible/changing data schema.
- High-speed key-value access.
- Search/log analytics scenarios where SQL is inefficient.

#### Practical tech-lead recommendations:

1. Do not replace relational DB with NoSQL "because of trend".
2. Start with PostgreSQL as the reliable default for Django.
3. Add NoSQL selectively for a specific non-functional requirement (latency,
   search, scale).
4. Design consistency between SQL and NoSQL explicitly (outbox/events/retry).

#### Conclusion:

Django is not a NoSQL-first framework, but it works well in a hybrid
architecture. The optimal strategy for most products: SQL as the foundation for
domain data + NoSQL as a specialized extension for specific workloads.

</details>

<details>
<summary>60. What common Django exceptions should you know?</summary>

#### Django

Django has a set of common exceptions that regularly appear in real projects.
Knowing them speeds up debugging and helps you build proper error handling in
views/APIs.

#### Most important exceptions:

1. **`Model.DoesNotExist`**

- Raised by `Model.objects.get(...)` when a record is not found.

2. **`Model.MultipleObjectsReturned`**

- `get()` returned more than one record.

3. **`ValidationError`**

- Validation errors in forms, models, custom validators.

4. **`IntegrityError`**

- DB constraint violation (`UNIQUE`, `FK`, `NOT NULL`, `CHECK`).

5. **`ObjectDoesNotExist`**

- Base exception for all `*.DoesNotExist`.

6. **`PermissionDenied`**

- No access to resource (returns 403).

7. **`SuspiciousOperation`**

- Suspicious/unsafe activity (e.g., invalid host/header).

8. **`Http404`**

- Used to explicitly return 404.

9. **`ImproperlyConfigured`**

- Configuration errors in settings, URL, middleware, apps.

10. **`OperationalError` (db backend)**

- DB connectivity/availability problems, timeouts, network failures.

#### Handling examples:

```python
from django.core.exceptions import ValidationError
from django.db import IntegrityError
from django.http import Http404

try:
    user = User.objects.get(pk=user_id)
except User.DoesNotExist:
    raise Http404("User not found")

try:
    create_order(...)
except ValidationError as exc:
    return JsonResponse({"errors": exc.message_dict}, status=400)
except IntegrityError:
    return JsonResponse({"error": "Data integrity violated"}, status=409)
```

#### Practical rules:

1. For 404 in views, use `get_object_or_404`.
2. Do not swallow exceptions without logging.
3. Separate user errors (4xx) from system errors (5xx).
4. In production, do not expose stack traces to clients.
5. For APIs, standardize error format (code, message, details).

#### Common anti-patterns:

1. `except Exception:` without specificity.
2. Ignoring `IntegrityError` and retrying inconsistent operations.
3. Mixing domain errors and technical exceptions into one generic "400 unknown".

#### Conclusion:

Proper exception handling in Django is about API quality control, service
stability, and fast incident investigation in production. Core exceptions should
be known and handled systematically, not ad hoc.

</details>

<details>
<summary>61. What is Django Admin? How do you register a model?</summary>

#### Django

`Django Admin` is a built-in admin panel for managing model data through a web
interface without building a separate back office from scratch.

#### What Django Admin provides:

1. Out-of-the-box CRUD for models.
2. Search, filters, sorting, pagination.
3. Work with related objects (inlines).
4. Fast back office for business teams.

#### How to register a model (minimal):

```python
# app/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

After that, the model appears at `/admin/`.

#### Recommended option via `ModelAdmin`:

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

#### Prerequisites for admin login:

1. Migrations are applied:

```bash
python manage.py migrate
```

2. Superuser is created:

```bash
python manage.py createsuperuser
```

3. Server is running and `/admin/` is open.

#### Practical recommendations:

1. Configure `list_display`, `search_fields`, `list_filter` for key models.
2. Restrict admin access with roles/permissions.
3. For large tables, optimize queryset in `ModelAdmin`
   (select_related/prefetch).
4. Do not use admin as a public interface for end users.

#### Conclusion:

Django Admin is a powerful tool for internal data management. Model registration
takes minutes, and with basic `ModelAdmin`, admin quickly becomes an effective
back office for the team.

</details>

<details>
<summary>62. What is a superuser?</summary>

#### Django

A `Superuser` in Django is a user with maximum administrative privileges in the
system, usually for accessing Django Admin and fully managing data.

#### Key superuser characteristics:

1. `is_superuser = True`
2. `is_staff = True`
3. Has all permissions without assigning each permission separately.
4. Can manage users, groups, models, and content via `/admin/`.

#### How to create a superuser:

```bash
python manage.py createsuperuser
```

Then Django will ask for:

- username
- email (depending on model)
- password

#### Where it is used:

1. Initial project administration.
2. Configuring roles/groups and access rights.
3. Operational support via Django Admin.

#### Important security notes:

1. Do not use a superuser account for daily operational work.
2. The number of superusers in production should be minimal.
3. Use strong passwords + 2FA (if available via SSO/admin solution).
4. Log admin actions and control access via IP/VPN.
5. Do not create "temporary" superusers without a removal process.

#### Practical role in a team:

- Superuser is needed for bootstrap stage.
- In mature processes, most tasks should be done via `staff` + groups + granular
  permissions, not full access.

#### Conclusion:

A superuser is the "root user" in Django. It is critically important for
administration, but access must be as limited and controlled as possible.

</details>

<details>
<summary>63. How do you customize Django Admin?</summary>

#### Django

Django Admin customization is done via `ModelAdmin` and related mechanisms
(inlines, actions, permissions, form overrides). This allows you to turn the
basic admin into an effective back-office tool.

#### Basic `ModelAdmin` customization:

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

#### Most common tools:

1. `list_display` - which columns are shown in list view.
2. `list_filter` - right-side filters.
3. `search_fields` - search by fields/relations.
4. `readonly_fields` - read-only fields.
5. `fieldsets` - grouping fields in edit form.
6. `actions` - bulk actions on selected records.

#### Inline editing of related models:

```python
class OrderItemInline(admin.TabularInline):
    model = OrderItem
    extra = 0

@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    inlines = [OrderItemInline]
```

#### Custom actions:

```python
@admin.action(description="Mark as published")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)
```

#### Access restrictions:

- `has_view_permission`, `has_change_permission`, `has_delete_permission`
- `get_queryset()` for data scoping (e.g., manager sees only their objects).

#### Admin performance optimization:

1. Use `list_select_related` for FK fields in `list_display`.
2. Be careful with `search_fields` on large tables (indexes are required).
3. Minimize heavy calculations in list view.
4. For very large lookups, use `autocomplete_fields`.

#### Additional customization:

- Override `form`/`get_form`.
- Override `save_model`/`delete_model`.
- Custom admin templates for specific UI needs.

#### Conclusion:

Django Admin scales well through `ModelAdmin`: from simple registration to a
full-featured internal dashboard with roles, filters, bulk actions, and
controlled performance.

</details>

<details>
<summary>64. What are Django Admin components and custom settings?</summary>

#### Django

Django Admin consists of several key components that can be flexibly customized
for team business processes: object list, edit form, filters, search, actions,
permissions, inlines, and global admin site configuration.

#### Main Django Admin components:

1. **Admin Site (`admin.site`)**

- Global admin panel; header/title/index can be customized.

2. **`ModelAdmin`**

- Configuration of how a specific model is shown in admin.

3. **Change List**

- Object list page (`list_display`, `list_filter`, `search_fields`).

4. **Change Form**

- Create/edit form (`fields`, `fieldsets`, `readonly_fields`).

5. **Inlines**

- Editing related models on one page.

6. **Actions**

- Bulk operations on selected records.

7. **Permissions**

- View/edit/delete access by roles.

#### Example of custom settings:

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
        ("Main", {"fields": ("email", "first_name", "last_name")}),
        ("Status", {"fields": ("is_active",)}),
        ("Service", {"fields": ("created_at", "updated_at")}),
    )
```

#### Global admin site settings:

```python
from django.contrib import admin

admin.site.site_header = "Admin Panel"
admin.site.site_title = "Backoffice"
admin.site.index_title = "System Management"
```

#### Role-based behavior customization:

- `get_queryset()` - limit what a specific staff user can see.
- `get_readonly_fields()` - make some fields read-only depending on role.
- `has_change_permission()` / `has_delete_permission()` - granular access
  control.

#### Components commonly added in production:

1. `autocomplete_fields` for heavy FK fields.
2. `list_select_related` for list-view optimization.
3. Custom `form` and `formfield_overrides` for better UX.
4. Custom templates for specific back-office scenarios.

#### Conclusion:

The strength of Django Admin is that from basic components, you can assemble a
managed internal interface tailored to team processes: fast, secure, and
operationally convenient.

</details>

<details>
<summary>65. What are Django Admin actions and how are they customized?</summary>

#### Django

`Admin actions` in Django are bulk operations on selected objects in the admin
list. They let you quickly perform routine actions without manually editing each
record.

#### What an action is:

- A function or method that accepts: `modeladmin`, `request`, `queryset`.
- It is called for the set of objects selected by the admin user in list view.

#### Basic action example:

```python
from django.contrib import admin
from .models import Article

@admin.action(description="Publish selected articles")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)

@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    list_display = ("id", "title", "is_published")
    actions = [make_published]
```

#### Action as a `ModelAdmin` method:

```python
@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    actions = ["mark_as_paid"]

    @admin.action(description="Mark as paid")
    def mark_as_paid(self, request, queryset):
        updated = queryset.update(status="paid")
        self.message_user(request, f"Orders updated: {updated}")
```

#### Action customization options:

1. Custom `description` for UI label.
2. Availability conditions depending on role/state.
3. Intermediate confirmation page (custom admin view).
4. Logging of executed bulk actions.

#### Practical recommendations:

1. For bulk changes, prefer `queryset.update()` (faster, fewer SQL queries).
2. If per-object business logic is required, iterate carefully inside a
   transaction.
3. Show summary via `message_user`.
4. Restrict dangerous actions for non-admin roles.

#### Important nuances:

1. `queryset.update()` does not call `save()` or `post_save` signals.
2. Bulk deletion via default action can be risky without extra control.
3. For critical operations, add a confirmation step.

#### Typical action use cases:

- Publish/Unpublish content.
- Batch status assignment.
- Export selected records to CSV.
- Trigger background processing for selected IDs.

#### Conclusion:

Admin actions are a fast operational automation tool in Django Admin. With
proper customization, they significantly speed up team workflows and reduce
manual routine work.

</details>

<details>
<summary>66. What is middleware and how does it work?</summary>

#### Django

`Middleware` in Django is a processing layer between HTTP request/response and
the view. It allows running code **before** the request reaches the view and
**after** the generated response goes back to the client.

#### How middleware pipeline works:

1. Request comes into Django.
2. It passes through middleware in sequence (request phase).
3. It reaches URL resolver and view.
4. Response goes back through middleware in reverse order (response phase).
5. It is sent to the client.

#### Important detail:

- Middleware order in `settings.py` (`MIDDLEWARE = [...]`) is critical.
- Top middleware sees request first and response last.

#### Typical middleware tasks:

1. Security (security headers, host checks).
2. Sessions and authentication.
3. CSRF protection.
4. Localization (locale/language).
5. Logging, request-id, metrics.
6. Request/response-level caching.

#### Middleware skeleton:

```python
class SimpleMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # before view
        response = self.get_response(request)
        # after view
        return response
```

#### Where it is configured:

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    # ...
]
```

#### Practical rules:

1. Keep middleware lightweight and fast.
2. Do not put heavy domain business logic there.
3. Avoid slow external calls in middleware.
4. Carefully control middleware order in the list.

#### Common mistakes:

1. Overly "smart" middleware with side effects.
2. Wrong order that breaks auth/csrf/session flow.
3. Duplicating logic between middleware and views.

#### Conclusion:

Middleware is Django's global request/response interceptor. Its strength is
centralized cross-cutting tasks (security, sessions, logging), not business
logic of specific endpoints.

</details>

<details>
<summary>67. What built-in middleware exist?</summary>

#### Django

Django provides a set of built-in middleware that cover core web app needs:
security, sessions, authentication, CSRF, caching, localization.

#### Most common built-in middleware:

1. **`django.middleware.security.SecurityMiddleware`**

- Security headers, HTTPS-related settings, baseline protection mechanisms.

2. **`django.contrib.sessions.middleware.SessionMiddleware`**

- Server-side user session support.

3. **`django.middleware.common.CommonMiddleware`**

- Common HTTP behaviors (e.g., `APPEND_SLASH`, `PREPEND_WWW`).

4. **`django.middleware.csrf.CsrfViewMiddleware`**

- CSRF protection for state-changing requests.

5. **`django.contrib.auth.middleware.AuthenticationMiddleware`**

- Adds `request.user` and integrates auth system into request flow.

6. **`django.contrib.messages.middleware.MessageMiddleware`**

- Flash message support (`messages.success`, `messages.error`).

7. **`django.middleware.clickjacking.XFrameOptionsMiddleware`**

- Clickjacking protection via `X-Frame-Options` header.

8. **`django.middleware.locale.LocaleMiddleware`**

- Language/locale detection for i18n.

9. **`django.middleware.gzip.GZipMiddleware`**

- Response compression (use carefully with already compressed content).

10. **`django.middleware.cache.UpdateCacheMiddleware` /
    `FetchFromCacheMiddleware`**

- Site-wide caching at middleware level.

#### Typical `MIDDLEWARE` order (shortened):

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

#### Practical notes:

1. Middleware order matters and affects behavior of the whole application.
2. Do not remove `SecurityMiddleware`, `CsrfViewMiddleware`,
   `AuthenticationMiddleware` without understanding consequences.
3. For production, verify security headers and cache policy after middleware
   changes.

#### Conclusion:

Django built-in middleware covers most infrastructure concerns out of the box.
The right middleware set and order directly impact security, stability, and
production behavior.

</details>

<details>
<summary>68. How do you create custom middleware?</summary>

#### Django

Custom middleware in Django is created as a class that accepts `get_response`
and intercepts `request/response` in the global request-processing pipeline.

#### Minimal middleware template:

```python
# app/middleware.py
class RequestIdMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # logic before view
        response = self.get_response(request)
        # logic after view
        return response
```

#### Request-id example:

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

#### Configuration in `settings.py`:

```python
MIDDLEWARE = [
    # ...
    "app.middleware.RequestIdMiddleware",
]
```

#### Where to place it in the list:

1. Security/session middleware is usually higher.
2. Custom logging/request-id middleware is often after base security/session
   middleware.
3. Order matters: it affects what middleware can see in `request`.

#### What middleware can do:

- Add headers.
- Log request/response.
- Add tracing context.
- Reject requests by global rules.

#### What it should not do:

1. Complex endpoint-specific business logic.
2. Slow external HTTP calls.
3. Heavy operations that block every request.

#### Conclusion:

Custom middleware is a tool for cross-cutting concerns at whole-application
level. Keep it lightweight, predictable, and correctly placed in `MIDDLEWARE` to
avoid side effects.

</details>

<details>
<summary>69. What are signals and when should you use them?</summary>

#### Django

`Signals` in Django are an event mechanism that lets you run code in response to
specific actions (for example, model save or delete) without directly calling
that logic from a view or service.

#### How it works:

1. An event (signal) occurs, e.g. `post_save`.
2. A receiver function subscribed to that event executes automatically.

#### Most commonly used signals:

1. `pre_save`, `post_save`
2. `pre_delete`, `post_delete`
3. `m2m_changed`
4. `request_started`, `request_finished` (less common for app logic)

#### `post_save` example:

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

Import/registration in `apps.py`:

```python
from django.apps import AppConfig

class UsersConfig(AppConfig):
    name = "users"

    def ready(self):
        import users.signals  # noqa
```

#### When signals are appropriate:

1. Loosely coupled side effects (e.g., create profile after user creation).
2. Technical hooks that should not clutter views.
3. Events where decoupling between modules is important.

#### When not to use signals:

1. Critical business logic where explicit step order is required.
2. Complex orchestration across multiple services.
3. Logic that should be transparent in one explicit use case.

#### Common signal problems:

1. "Magic" and unexpected side effects.
2. Hard debugging in large projects.
3. Duplicate calls due to careless registration.
4. Hard to control execution order across many receivers.

#### Practical rules:

1. Keep signals short and fast.
2. Send long/heavy tasks to a queue (Celery/RQ).
3. Document which events each module subscribes to.
4. Do not hide core transaction business logic in signals.

#### Conclusion:

Signals in Django are useful for moderate side effects and loose module
coupling. For core business processes, an explicit service layer is usually more
reliable because the flow is visible directly in code.

</details>

<details>
<summary>70. Difference between signals and middleware.</summary>

#### Django

`Middleware` and `signals` solve different problems, even though both may look
like a "place for additional logic." The key difference is the **event level**
at which they operate.

#### Middleware:

1. Works at **HTTP request/response** level.
2. Runs for every request in the global pipeline.
3. Used for cross-cutting web concerns.

Typical cases:

- security headers
- auth/session flow
- logging/tracing/request-id
- locale/caching/compression

#### Signals:

1. Work at **model/framework event** level.
2. Trigger on actions like `post_save`, `post_delete`, `m2m_changed`.
3. Used for reacting to domain model events.

Typical cases:

- create profile after user creation
- sync auxiliary entities
- lightweight hooks after data changes

#### Main difference:

- Middleware reacts to request/response.
- Signals react to data/model events.

#### When to choose which:

1. Need global HTTP behavior -> **middleware**.
2. Need reaction to model changes -> **signals**.
3. Need explicit business-flow control -> **service layer**, not
   signals/middleware.

#### Comparison table:

| Criterion         | Middleware                | Signals                        |
| ----------------- | ------------------------- | ------------------------------ |
| Level             | HTTP pipeline             | Model/framework events         |
| Trigger point     | Before/after view         | Before/after save/delete, etc. |
| Flow transparency | Higher (via `MIDDLEWARE`) | Lower (can become "magic")     |
| Task type         | Infrastructure            | Event-driven side effects      |

#### Common mistakes:

1. Putting model business logic in middleware.
2. Hiding critical business flow in signals without explicit orchestration.
3. Duplicating the same logic across both layers.

#### Conclusion:

Middleware is for HTTP infrastructure, signals are for model event reactions.
For important business logic, explicit services are better: they are most
transparent, most testable, and least prone to hidden side effects.

</details>

<details>
<summary>71. How does authentication and authorization work?</summary>

#### Django

In Django, access control consists of two parts:

1. **Authentication** - who are you?
2. **Authorization** - what are you allowed to do?

#### How authentication works:

1. User submits login/password.
2. Django verifies credentials via `authenticate()`.
3. If successful, `login()` is called and a session is created.
4. On next requests, `AuthenticationMiddleware` adds `request.user`.

Basic example:

```python
from django.contrib.auth import authenticate, login

user = authenticate(request, username=username, password=password)
if user is not None:
    login(request, user)
```

#### How authorization works:

- Django checks user permissions via permissions, groups, and role-based rules.
- Default model permissions: `add`, `change`, `delete`, `view`.

Permission check:

```python
if request.user.has_perm("orders.change_order"):
    ...
```

#### Access control tools:

1. `@login_required` - access only for authenticated users.
2. `@permission_required("app.perm_codename")`
3. `LoginRequiredMixin`, `PermissionRequiredMixin` for CBV.
4. `Group` for role-based permission sets.

#### Session model (default):

- After `login()`, Django creates a session in DB/cache.
- Session ID is stored in cookie.
- On each request, user is identified via this session.

#### Where it is configured:

- `AUTHENTICATION_BACKENDS`
- `LOGIN_URL`, `LOGIN_REDIRECT_URL`, `LOGOUT_REDIRECT_URL`
- `AUTH_USER_MODEL` (if custom user model is used)

#### Practical recommendations:

1. Do not enforce access only on frontend - backend must be source of truth.
2. Group permissions by roles, do not assign individually to each user.
3. For API, design token/session auth and access policy separately.
4. Log sensitive admin actions for audit.

#### Conclusion:

In Django, authentication identifies the user, authorization defines their
permissions. Together they form a secure and scalable access model for web and
API applications.

</details>

<details>
<summary>72. How do you implement user registration?</summary>

#### Django

User registration in Django usually consists of a form, view logic, user
creation with hashed password, and (optionally) automatic login.

#### Basic approach:

1. Create a registration form (`UserCreationForm` or custom).
2. Process the form in a view (`GET`/`POST`).
3. Save the user.
4. Redirect to login or perform auto-login.

#### Form example:

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

#### View example:

```python
# users/views.py
from django.contrib.auth import login
from django.shortcuts import redirect, render
from .forms import SignUpForm

def signup_view(request):
    if request.method == "POST":
        form = SignUpForm(request.POST)
        if form.is_valid():
            user = form.save()  # password is hashed automatically
            login(request, user)  # optional: log in immediately
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
  <button type="submit">Sign up</button>
</form>
```

#### URL:

```python
path("signup/", signup_view, name="signup")
```

#### Important security rules:

1. Never store password manually as plain text.
2. Use `UserCreationForm` or `set_password()`.
3. Add brute-force protection (rate limiting / captcha where needed).
4. For production, email verification before account activation is preferred.

#### Registration extensions:

1. User profile (via `OneToOne`).
2. Email confirmation token flow.
3. Social login (Google/GitHub) via allauth.
4. Registration event audit log.

#### Conclusion:

In Django, registration is implemented quickly via built-in auth forms and view
flow. The key points are correct password handling, CSRF protection, and a
well-designed account activation process in production.

</details>

<details>
<summary>73. How do you create a custom user model?</summary>

#### Django

A custom user model in Django is created when the standard `User` is not enough
(for example, email as login, additional required fields, custom identity
logic).

#### Key rule:

`AUTH_USER_MODEL` must be defined **at project start**, before first migrations.
Late replacement is expensive and risky.

#### Option 1 (recommended in 90% of cases): `AbstractUser`

- Inherit built-in user and add your fields.
- Simplest and most stable path.

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

#### Option 2: `AbstractBaseUser` + `PermissionsMixin`

- Full control over model and login field.
- Much more complex: custom `UserManager`, `USERNAME_FIELD`, `REQUIRED_FIELDS`,
  compatibility with admin/forms/auth flow.

Use only when you truly need non-standard auth model behavior.

#### Example referencing custom user in models:

```python
from django.conf import settings

class Order(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
```

#### In code, instead of direct `User` import:

```python
from django.contrib.auth import get_user_model
User = get_user_model()
```

#### Practical recommendations:

1. If unsure, create custom model via `AbstractUser` from day one.
2. Do not use `from django.contrib.auth.models import User` in domain code.
3. Ensure forms/admin/auth backend work with your model.
4. Cover registration, login, password reset, and permissions with tests.

#### Common mistakes:

1. Attempting to change user model after project is already in production.
2. Hard-importing default `User` in models and migrations.
3. Using `AbstractBaseUser` without real need and without full configuration.

#### Conclusion:

A proper custom user model in Django is a strategic startup decision. The safest
path: `AbstractUser` + `AUTH_USER_MODEL` + disciplined use of `get_user_model()`
and `settings.AUTH_USER_MODEL` across the project.

</details>

<details>
<summary>74. What is `login_required` used for?</summary>

#### Django

`login_required` is a decorator that restricts view access to authenticated
users only.

#### How it works:

1. If user is authenticated -> view is executed.
2. If not -> redirect to login page (`LOGIN_URL`) with `next` parameter.

#### FBV example:

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, "dashboard.html")
```

#### Custom login URL:

```python
@login_required(login_url="/auth/login/")
def billing_page(request):
    ...
```

#### CBV equivalent:

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import TemplateView

class DashboardView(LoginRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Settings in `settings.py`:

```python
LOGIN_URL = "login"
LOGIN_REDIRECT_URL = "home"
```

#### What it is used for:

1. Protecting private pages (dashboard, orders, profile settings).
2. Basic access control in admin-like sections.
3. Preventing unauthorized POST actions.

#### What `login_required` does NOT do:

1. Does not check roles/permissions (only login status).
2. Does not replace detailed authorization control.

For permissions, use:

- `permission_required`
- `user_passes_test`
- `PermissionRequiredMixin`

#### Practical tips:

1. Apply `login_required` to all private endpoints by default.
2. Do not rely only on hidden frontend buttons.
3. Ensure `next` redirect is safe (Django handles this by default).

#### Conclusion:

`login_required` is basic and mandatory protection for private Django views. It
answers "is user logged in", while detailed access rights should be enforced
with additional authorization mechanisms.

</details>

<details>
<summary>75. How do sessions and cookies work?</summary>

#### Django

In Django, sessions and cookies are used to keep state between requests, because
HTTP itself is stateless.

#### What cookies are:

- Small data stored by browser on client side.
- Sent back to server on each next request to the same domain.
- Often contain session ID, not sensitive data itself.

#### What a session is:

- Server-side storage of user data (DB/cache/files).
- Browser stores only session key in cookie.
- Via `request.session`, Django reads/updates session data.

#### How they work together:

1. After login, Django creates a session on server.
2. Session key is written to cookie (`sessionid`).
3. On each request, Django reads cookie and restores session.

#### Session usage example:

```python
def set_theme(request):
    request.session["theme"] = "dark"
    return HttpResponse("ok")

def get_theme(request):
    theme = request.session.get("theme", "light")
    return HttpResponse(theme)
```

#### Explicit cookie example:

```python
response = HttpResponse("ok")
response.set_cookie("promo_seen", "1", max_age=3600)
```

#### Where Django stores sessions:

- Default: in DB (`django.contrib.sessions`).
- Backend can be changed to cache, file, signed cookies.

#### Important security settings:

1. `SESSION_COOKIE_HTTPONLY = True` (protects cookie from JS access).
2. `SESSION_COOKIE_SECURE = True` (HTTPS only).
3. `SESSION_COOKIE_SAMESITE = "Lax"` or `"Strict"` when needed.
4. Same for CSRF cookie (`CSRF_COOKIE_SECURE`, `CSRF_COOKIE_HTTPONLY`).

#### Practical recommendations:

1. Do not store sensitive data directly in cookies.
2. Keep session payload minimal.
3. For scaling, use Redis-backed sessions.
4. Clear/invalidate session on logout and critical account changes.

#### Conclusion:

Cookies are a client-side mechanism for transferring small data, while sessions
are server-side user-state storage. In Django, they work together and form the
basis of classic auth flow and personalized UX.

</details>

<details>
<summary>76. What are groups and permissions, and how do you implement role-based access?</summary>

#### Django

In Django, **permissions** and **groups** are core authorization mechanisms for
implementing RBAC (Role-Based Access Control).

#### What permissions are:

- Rights in form `app_label.codename`, for example: `orders.view_order`,
  `orders.change_order`.
- Django automatically creates base model permissions: `add`, `change`,
  `delete`, `view`.
- You can add custom permissions in model `Meta`.

#### What groups are:

- Group = role that has a set of permissions.
- User is added to group and receives that role's permissions.

#### Example of custom permission in model:

```python
class Order(models.Model):
    ...
    class Meta:
        permissions = [
            ("approve_order", "Can approve order"),
        ]
```

#### Access check in code:

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

#### Example roles (RBAC):

1. **viewer** -> only `view_*`
2. **manager** -> `view_*`, `change_*`, `approve_order`
3. **admin** -> full domain access set

#### Typical RBAC implementation flow:

1. Define roles and responsibilities.
2. Define mapping "role -> permissions".
3. Create groups and assign permissions.
4. Add users to groups (via admin or seed scripts).
5. Check permissions in view/CBV/API.

#### Practical recommendations:

1. Assign rights by roles (groups), not manually per user.
2. Keep access policy centralized and documented.
3. Enforce access checks on backend, even if UI hides buttons.
4. For advanced cases, add object-level permissions if needed.

#### Common mistakes:

1. Granting `is_superuser` where role permissions are enough.
2. Mixing roles and business states without clear rules.
3. Giving "temporary" permissions without audit and expiration.

#### Conclusion:

Groups and permissions in Django are a reliable foundation for role-based
access. RBAC via groups makes the system more secure, transparent, and easier to
maintain as team and product scale.

</details>

<details>
<summary>77. How do you implement password reset?</summary>

#### Django

The easiest way to implement password reset in Django is via built-in auth
views: they already provide a secure flow with one-time token and expiration
validation.

#### Standard flow:

1. User enters email on "Forgot password" page.
2. Django sends an email with link (uid + token).
3. User opens link and sets a new password.
4. Django confirms successful change.

#### URL setup:

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

#### Required templates:

- `registration/password_reset_form.html`
- `registration/password_reset_done.html`
- `registration/password_reset_confirm.html`
- `registration/password_reset_complete.html`
- email template, e.g. `registration/password_reset_email.html`

#### Basic email settings:

```python
EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "smtp.example.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "..."
EMAIL_HOST_PASSWORD = "..."
DEFAULT_FROM_EMAIL = "noreply@example.com"
```

#### Important security principles:

1. Do not reveal whether email exists in system (prevent user enumeration).
2. Use HTTPS for reset links.
3. Limit reset request rate (rate limiting).
4. Invalidate active sessions after password change according to security
   policy.
5. Log password reset events for audit.

#### When customization is needed:

- Custom design for email/pages.
- Custom user model with email-based login.
- Integration with external auth/SSO.

#### Conclusion:

Django provides a ready secure password reset mechanism via standard auth views.
In production, it is enough to configure email, templates, HTTPS, and anti-abuse
protection correctly.

</details>

<details>
<summary>78. What is CSRF and how does `{% csrf_token %}` work?</summary>

#### Django

**CSRF (Cross-Site Request Forgery)** is an attack where a malicious site forces
an authenticated user to perform an unwanted action in your application (for
example, change password or create a payment).

#### How Django protects against CSRF:

1. CSRF token is generated on server side.
2. Token is embedded into form (via `{% csrf_token %}`).
3. For state-changing requests (`POST`, `PUT`, `PATCH`, `DELETE`), Django
   compares request token with expected token.
4. If token is missing/invalid -> `403 Forbidden`.

#### `{% csrf_token %}` in a form:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Save</button>
</form>
```

#### What is required for it to work:

1. `django.middleware.csrf.CsrfViewMiddleware` in `MIDDLEWARE`.
2. Use `{% csrf_token %}` in all POST forms.
3. Correct cookie policy (especially in production with HTTPS).

#### For AJAX/fetch requests:

- CSRF token is sent in `X-CSRFToken` header.
- Token is taken from cookie (`csrftoken`) or from HTML (depending on approach).

#### Common mistakes:

1. Forgetting `{% csrf_token %}` in form template.
2. Disabling `CsrfViewMiddleware` without valid reason.
3. Misconfiguring domain/secure cookie parameters.
4. Using `@csrf_exempt` "for speed" and forgetting to restore protection.

#### When `csrf_exempt` is acceptable:

- Only for special endpoints (e.g., external webhooks), and only when another
  reliable request validation mechanism exists (HMAC signature, token,
  allowlist).

#### Practical recommendations:

1. All browser-based state-changing forms must include `{% csrf_token %}`.
2. For APIs without cookie sessions (Bearer/JWT), build separate auth model.
3. In production use HTTPS + `CSRF_COOKIE_SECURE = True`.

#### Conclusion:

`{% csrf_token %}` is a key Django protection element against CSRF attacks in
forms. This is not optional, but a baseline security standard for any action
that changes system state.

</details>

<details>
<summary>79. How does Django protect against XSS, CSRF, and SQL injection?</summary>

#### Django

Django follows a secure-by-default approach and includes built-in protections
against common web vulnerabilities: XSS, CSRF, and SQL injection.

#### 1. XSS (Cross-Site Scripting) protection

How it works:

1. Django templates auto-escape variables in `{{ ... }}`.
2. HTML special characters are converted into safe output.
3. Potentially dangerous content is not executed as script.

Important:

- `|safe` disables escaping, use it only for fully trusted HTML.
- Do not render raw user input without sanitization.

#### 2. CSRF protection

How it works:

1. `CsrfViewMiddleware` validates token in state-changing requests.
2. `{% csrf_token %}` adds token to HTML forms.
3. Without valid token, Django returns `403`.

#### 3. SQL injection protection

How it works:

1. ORM uses parameterized queries.
2. Data is passed separately from SQL structure.
3. This blocks classic injections in most standard scenarios.

Risk appears when:

- writing raw SQL with manual string concatenation.

#### Additional built-in Django protections:

1. `SecurityMiddleware` (headers, SSL-related policies).
2. `XFrameOptionsMiddleware` (clickjacking protection).
3. Secure password hashing (`PBKDF2` by default).
4. Host header validation (`ALLOWED_HOSTS`).

#### Practical production recommendations:

1. `DEBUG=False` in production.
2. HTTPS everywhere (`SECURE_SSL_REDIRECT`, secure cookies).
3. Set `SESSION_COOKIE_SECURE`, `CSRF_COOKIE_SECURE`, `HTTPONLY`.
4. Use CSP (via headers/packages).
5. Regularly update Django and dependencies.

#### Common developer mistakes:

1. Uncontrolled use of `|safe`.
2. `@csrf_exempt` without alternative validation.
3. Raw SQL with f-string/format.
4. Leaving `DEBUG=True` in production.

#### Conclusion:

Django provides strong baseline protection against XSS, CSRF, and SQL injection.
But security also depends on coding discipline: proper template usage, ORM-first
approach, production settings, and ongoing security review.

</details>

<details>
<summary>80. How does Django protect against SQL injection?</summary>

#### Django

Django protects against SQL injection primarily via ORM and parameterized
queries: user data is passed as parameters, not interpolated into SQL strings.

#### Core protection mechanism:

1. You write an ORM query:

```python
User.objects.filter(email=user_input)
```

2. Django generates SQL with placeholder parameters.
3. `user_input` value does not break SQL structure.

#### Why this is safe:

- ORM separates SQL logic from data.
- DB engine treats parameters as values, not as SQL command parts.

#### Where SQL injection risk is still possible:

1. **Raw SQL with string concatenation**

```python
# Unsafe
sql = f"SELECT * FROM users WHERE email = '{user_input}'"
```

2. Incorrect `.extra()` usage (legacy approach).
3. Dynamic ORDER BY/field names without allowlist validation.

#### Safe raw SQL (if really needed):

```python
from django.db import connection

with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM users WHERE email = %s", [user_input])
    rows = cursor.fetchall()
```

#### Practical rules:

1. Use ORM by default (`filter/get/exclude/annotate`).
2. If raw SQL is unavoidable, use parameterized queries only.
3. Never insert user input into SQL via f-strings or `format`.
4. For dynamic fields/sorting, use allowlist:

- allow only pre-defined column names.

#### Additional hardening steps:

1. Minimal DB user permissions (least privilege).
2. Logging suspicious queries and anomaly monitoring.
3. Regular updates of Django/DB drivers.

#### Conclusion:

Django ORM provides strong out-of-the-box protection against SQL injection. Real
risks start where developers bypass ORM and build manual SQL without
parameterization and validation.

</details>

<details>
<summary>81. What is Content Security Policy (CSP) in Django?</summary>

#### Django

**Content Security Policy (CSP)** is an HTTP security policy that restricts the
sources from which the browser can load scripts, styles, images, fonts, etc. The
main goal is to reduce XSS risk and execution of unsafe content.

#### What CSP does:

1. Defines a source allowlist (`self`, CDN, API domains).
2. Blocks unknown or injected resources.
3. Enables gradual rollout via `Report-Only`.

#### Example CSP header:

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

#### How to add CSP in Django:

The most convenient way is using `django-csp` package:

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

#### Important practices:

1. Start with `Content-Security-Policy-Report-Only` to collect violations.
2. Minimize use of `'unsafe-inline'` and `'unsafe-eval'`.
3. For inline scripts, use nonce/hash approach.
4. Gradually tighten policy to the minimum required sources.

#### Common rollout problems:

1. Third-party widgets/analytics break under strict rules.
2. Broad wildcard sources (`*`) weaken CSP value.
3. No CSP violation monitoring after release.

#### Conclusion:

CSP in Django is an important extra layer against XSS and supply-chain risks.
Best approach: start with `Report-Only`, then gradually harden policy to a
strict allowlist model.

</details>

<details>
<summary>82. What are custom management commands and when should you use them?</summary>

#### Django

`Custom management commands` are custom Django CLI commands run via
`python manage.py <command_name>`. They let you formalize operational and
technical tasks as maintainable project code.

#### Why this is needed:

1. Automation of routine tasks (import/export, cleanup, synchronization).
2. Operational commands for DevOps/Support.
3. Scripts for data migration/backfill.
4. Commands for CI/CD, staging, and maintenance windows.

#### File structure:

```text
my_app/
  management/
    __init__.py
    commands/
      __init__.py
      recalc_stats.py
```

#### Command example:

```python
from django.core.management.base import BaseCommand
from orders.models import Order

class Command(BaseCommand):
    help = "Recalculates aggregated order statistics"

    def add_arguments(self, parser):
        parser.add_argument("--dry-run", action="store_true")

    def handle(self, *args, **options):
        total = Order.objects.count()
        if options["dry_run"]:
            self.stdout.write(self.style.WARNING(f"DRY RUN: orders={total}"))
            return
        # actual logic
        self.stdout.write(self.style.SUCCESS(f"Done. orders={total}"))
```

Run:

```bash
python manage.py recalc_stats --dry-run
```

#### When custom command is the right choice:

1. Task is repeatable and should be reproducible.
2. You need full Django context access (ORM, settings, services).
3. You need a controlled command for team/CI.

#### Practical recommendations:

1. Add `--dry-run` for safe verification.
2. Make operations idempotent when possible.
3. Use transactions for critical batch changes.
4. Log progress and summary (`self.stdout`, structured logs).
5. For long tasks, consider running via queues/workers.

#### Common mistakes:

1. Keeping important one-off scripts outside repository.
2. Running risky update/delete without dry-run and backup plan.
3. Writing command as unreadable monolith without tests.

#### Conclusion:

Custom management commands are a standard tool of Django operational maturity.
They make technical procedures transparent, controlled, and repeatable in a team
environment.

</details>

<details>
<summary>83. What are context processors and how are they used?</summary>

#### Django

`Context processors` are functions that automatically add data to template
context of every template (or selected templates), so you do not pass these
variables manually in each view.

#### How a context processor works:

1. Django calls the function during template rendering.
2. Function returns a dictionary.
3. That dictionary is added to template context.

#### Example:

```python
# core/context_processors.py
def app_meta(request):
    return {
        "APP_NAME": "My Django App",
        "SUPPORT_EMAIL": "support@example.com",
    }
```

Configuration in `settings.py`:

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

After that, in any template:

```django
<footer>{{ APP_NAME }} · {{ SUPPORT_EMAIL }}</footer>
```

#### When to use:

1. Global layout data (app name, contacts, feature flags).
2. Data needed across many templates.
3. Lightweight fast values without expensive computation.

#### When not to use:

1. Heavy SQL queries on every render.
2. Narrow data needed by one or two views only.
3. Complex business logic.

#### Useful built-in context processors:

1. `django.template.context_processors.request` (`request` in template)
2. `django.contrib.auth.context_processors.auth` (`user`, `perms`)
3. `django.contrib.messages.context_processors.messages`
4. `django.template.context_processors.static`
5. `django.template.context_processors.media`

#### Practical recommendations:

1. Keep context processors as lightweight as possible.
2. Avoid key collisions with local view context.
3. If data is expensive, cache it or pass it directly from view.
4. Document global context keys for the team.

#### Conclusion:

Context processors are a convenient mechanism for shared template data. They
work well for lightweight global values, but should not become a place for heavy
domain logic.

</details>

<details>
<summary>84. How does caching work in Django? Main caching approaches.</summary>

#### Django

Caching in Django reduces expensive operations (SQL, template rendering,
computations) and speeds up responses for users.

#### How it works:

1. Data/response is stored in fast storage (Redis/Memcached).
2. Repeated request gets result from cache without full recomputation.
3. After TTL or invalidation, value is recomputed.

#### Main caching approaches in Django:

1. **Site-wide cache (middleware)**

- Caches almost the entire HTTP response for pages.
- Good for public content with little personalization.

2. **Per-view cache (`cache_page`)**

- Caches specific view for a given time.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)
def article_list(request):
    ...
```

3. **Template fragment cache**

- Caches part of template, not whole page.

```django
{% load cache %}
{% cache 300 homepage_sidebar user.id %}
  ...
{% endcache %}
```

4. **Low-level cache API**

- Manual caching of results in code.

```python
from django.core.cache import cache

data = cache.get("popular_products")
if data is None:
    data = expensive_query()
    cache.set("popular_products", data, 300)
```

#### Backend configuration:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### When to choose each approach:

1. Public pages without personalization -> per-view/site-wide.
2. Partially dynamic pages -> fragment cache.
3. Expensive domain computations/aggregations -> low-level cache API.

#### Practical rules:

1. Start with targeted cache (fragment/per-view), not site-wide immediately.
2. Set TTL based on data freshness requirements.
3. For personalized data add keys (user id, locale, role).
4. Plan cache invalidation after data changes.

#### Common mistakes:

1. Caching personalized content without user-specific key.
2. Not invalidating cache after update/delete.
3. Too long TTL for "live" data.
4. Relying on cache instead of fixing poor SQL queries.

#### Conclusion:

Caching in Django is a multi-layer strategy: from template fragments to full
responses. Best results come from combining proper backend (usually Redis),
reasonable TTL, and controlled invalidation.

</details>

<details>
<summary>85. How do you optimize queries, caching, and DB indexing?</summary>

#### Django

Optimization in Django is always a combination of: `ORM queries` + `caching` +
`proper DB indexes` + `profiling`. A single technique rarely gives stable
results.

#### 1. ORM query optimization

1. Avoid N+1 via:

- `select_related()` for FK/O2O
- `prefetch_related()` for M2M/reverse FK

2. Fetch only required fields:

- `values()`, `values_list()`, `only()`, `defer()`

3. For bulk updates use:

- `update()` + `F()` instead of `save()` in loops

4. For existence checks:

- `exists()` instead of loading full queryset

#### 2. Caching

1. Start with fragment/per-view cache.
2. For "hot" computations use low-level cache API.
3. In production, Redis is usually the backend.
4. Design cache keys (user/locale/role) and invalidation after data changes.

#### 3. DB indexing

1. Add indexes on fields frequently used in:

- `WHERE`
- `ORDER BY`
- `JOIN`

2. Use `models.Index` and `UniqueConstraint` in `Meta`.
3. Do not index everything: every index has `INSERT/UPDATE` cost.

Example:

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

#### 4. Profiling and measurement

1. Use Django Debug Toolbar on dev/staging.
2. Log slow SQL queries at DB level.
3. Check `EXPLAIN ANALYZE` for critical queries.
4. Measure p95/p99 latency before/after changes.

#### Typical optimization order:

1. Find bottleneck (do not optimize blindly).
2. Fix ORM issues (N+1, extra fields, duplicate queries).
3. Add/verify indexes.
4. Add cache for consistently hot scenarios.
5. Measure results again.

#### Common mistakes:

1. Caching everything without invalidation strategy.
2. Adding indexes without real query analysis.
3. Optimizing Python code while ignoring SQL bottleneck.
4. Doing major schema changes in production without phased rollout.

#### Conclusion:

Stable Django performance is achieved not by one trick, but by a systematic
approach: measure, optimize ORM, index DB correctly, and cache only what gives
real benefit under load.

</details>

<details>
<summary>86. What is the Django testing framework?</summary>

#### Django

The `Django testing framework` is a built-in set of tools for testing models,
views, forms, APIs, and integrations within a Django project.

#### What the framework includes:

1. `django.test.TestCase` - base class for most tests.
2. `Client` - test HTTP client for requests to views/URLs.
3. Test database (created automatically before run).
4. Assertions for response, context, redirects, templates.
5. Tools for overriding settings and environment isolation.

#### How tests are run:

```bash
python manage.py test
```

#### How test DB works:

1. Django creates a separate test DB.
2. Applies migrations/schema.
3. Each test is transactionally isolated (`TestCase`).
4. After completion, test DB is removed.

#### Main test classes:

1. **`TestCase`**

- Most common choice; fast and isolated for ORM/view tests.

2. **`TransactionTestCase`**

- When transaction/commit behavior must be tested directly.

3. **`SimpleTestCase`**

- Tests without DB access.

4. **`LiveServerTestCase`**

- Integration/browser tests with a running test server.

#### Example of a simple test:

```python
from django.test import TestCase
from django.urls import reverse

class HealthViewTests(TestCase):
    def test_health_endpoint_returns_200(self):
        response = self.client.get(reverse("health"))
        self.assertEqual(response.status_code, 200)
```

#### Practical recommendations:

1. Write tests for critical business scenarios, not only for coverage numbers.
2. Keep tests deterministic (no time/network dependency without mocks).
3. Use factories/fixtures for readable test data setup.
4. Run tests in CI on every PR.

#### Common mistakes:

1. Tests that depend on execution order.
2. Overusing integration tests where unit level is sufficient.
3. Ignoring edge cases and negative scenarios.

#### Conclusion:

Django testing framework provides ready-to-use infrastructure for reliable
backend testing out of the box. It is the foundation of safe refactoring and a
stable release process in team development.

</details>

<details>
<summary>87. What is the difference between unit and integration tests?</summary>

#### Django

`Unit` and `integration` tests differ by validation scope:

- **Unit test** checks an isolated piece of logic.
- **Integration test** checks interaction of multiple components together.

#### Unit tests:

1. Test one function/method/class in isolation from the rest of the system.
2. Often use mocks/stubs for dependencies.
3. Very fast, precise for localizing failures.

Django examples:

- validator test,
- helper-function test,
- service-method test without real HTTP/DB (or with minimal isolation).

#### Integration tests:

1. Verify several layers together (view + ORM + middleware + templates).
2. Often use test client and test DB.
3. Slower, but closer to real behavior scenario.

Django example:

- `client.post(...)` -> view -> model save -> redirect -> DB assertions.

#### Key differences:

1. **Speed**

- Unit: fast.
- Integration: slower.

2. **Coverage scope**

- Unit: narrow focus.
- Integration: broader system scenario.

3. **Diagnostics**

- Unit: easier to find exact root cause.
- Integration: better at catching component interaction issues.

#### Example test pyramid for Django:

1. Many unit tests (validators, services, utilities).
2. Fewer integration tests (key endpoints, critical business flows).
3. Even fewer end-to-end/browser tests.

#### Practical recommendations:

1. Keep critical domain logic well covered by unit tests.
2. Add integration tests for core user journeys.
3. Do not try to cover everything only with integration tests - it is slow and
   brittle.
4. Every production bug should end with a new test at the right level.

#### Conclusion:

Unit and integration tests do not replace each other. A stable Django project
needs both: unit tests for fast feedback and integration tests for real
component interaction validation.

</details>

<details>
<summary>88. What is the Django test client?</summary>

#### Django

`Django test client` is a built-in tool for simulating HTTP requests to your
application without running a real browser or external HTTP server.

#### What test client can do:

1. Send `GET`, `POST`, `PUT`, `PATCH`, `DELETE` requests.
2. Validate status code, redirects, templates, context.
3. Work with session, cookies, and user authentication.
4. Test URL -> view -> response chain.

#### Basic example:

```python
from django.test import TestCase
from django.urls import reverse

class HomeTests(TestCase):
    def test_home_returns_200(self):
        response = self.client.get(reverse("home"))
        self.assertEqual(response.status_code, 200)
```

#### POST request example:

```python
response = self.client.post(reverse("signup"), {
    "username": "testuser",
    "password1": "StrongPass123!",
    "password2": "StrongPass123!",
})
self.assertEqual(response.status_code, 302)
```

#### Login in tests:

1. Fast technical login:

```python
self.client.force_login(user)
```

2. Realistic login via credentials:

```python
logged_in = self.client.login(username="testuser", password="secret")
self.assertTrue(logged_in)
```

#### What you can assert:

1. `response.status_code`
2. `response.context`
3. `response.templates`
4. `assertRedirects(...)`
5. response content (`assertContains(...)`)

#### Test client limitations:

1. Does not execute JavaScript (not browser automation).
2. Does not validate real frontend runtime like Playwright/Selenium.
3. Does not model all production network environment nuances.

#### Practical recommendations:

1. Use test client for most Django web/API integration tests.
2. For JS flows, add separate e2e/browser tests.
3. Combine with factories/fixtures for readable test data setup.

#### Conclusion:

Django test client is a fast and powerful tool for validating backend HTTP
behavior of your application. It is the standard choice for testing views, URLs,
authentication, and basic component integration.

</details>

<details>
<summary>89. How do you test forms, views, and ORM?</summary>

#### Django

In Django, forms, views, and ORM are tested at different levels, but in one
consistent style: clear preconditions -> action -> result assertions.

#### 1. Testing forms

What to verify:

1. valid/invalid data
2. errors on specific fields
3. custom validation (`clean_<field>`, `clean()`)

Example:

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

#### 2. Testing views

What to verify:

1. status code
2. template/context
3. redirects
4. auth/permission behavior

Example:

```python
from django.test import TestCase
from django.urls import reverse

class DashboardViewTests(TestCase):
    def test_anonymous_redirected_to_login(self):
        response = self.client.get(reverse("dashboard"))
        self.assertEqual(response.status_code, 302)
```

#### 3. Testing ORM

What to verify:

1. model create/update/delete
2. custom manager/queryset methods
3. relations and constraints (`unique`, `constraints`)

Example:

```python
from django.test import TestCase
from blog.models import Article

class ArticleORMTests(TestCase):
    def test_create_article(self):
        article = Article.objects.create(title="Test", is_published=True)
        self.assertEqual(Article.objects.count(), 1)
        self.assertTrue(article.is_published)
```

#### Practical recommendations:

1. Keep tests independent from each other.
2. Use descriptive test names by `should_<behavior>` pattern.
3. For test data setup, use factories/fixtures instead of duplicated setup.
4. Test negative scenarios as carefully as positive ones.

#### Commonly forgotten checks:

1. Permission checks at view level.
2. Form validation with unexpected input data.
3. Manager/queryset behavior on empty datasets.

#### Conclusion:

Forms test validation, views test HTTP behavior, ORM tests data and relations.
Together this creates a reliable testing foundation for safe Django refactoring
and stable releases.

</details>

<details>
<summary>90. How do you use fixtures?</summary>

#### Django

`Fixtures` in Django are pre-prepared data files (JSON/YAML/XML) that can be
loaded into DB for tests, demos, or initial seed.

#### Why fixtures are used:

1. Quickly bootstrap a standard data set.
2. Reproduce the same test state across environments.
3. Test scenarios with realistic related records.

#### Fixture file example:

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

Placement:

- `app/fixtures/articles.json` (typical option)

#### Load fixture:

```bash
python manage.py loaddata articles.json
```

#### Usage in tests:

```python
from django.test import TestCase
from blog.models import Article

class ArticleTests(TestCase):
    fixtures = ["articles.json"]

    def test_fixture_loaded(self):
        self.assertEqual(Article.objects.count(), 1)
```

#### When fixtures are appropriate:

1. Small stable reference dataset.
2. Integration tests with complex relations.
3. Demo/local seed for review environments.

#### Fixture limitations:

1. Fragile when model schema changes.
2. Harder to read and maintain large JSON files.
3. Less flexible for combining data across diverse tests.

#### Practical alternative:

- For most tests, factories are better (`factory_boy`, `model_bakery`) because:

1. Data is generated programmatically.
2. Easier to adapt to model changes.
3. Fewer "magic" static files.

#### Recommended tech-lead approach:

1. Small shared data -> fixtures.
2. Most unit/integration tests -> factories.
3. Do not mix both approaches chaotically without team rules.

#### Conclusion:

Fixtures in Django are useful for stable starter datasets, but for flexible and
long-term test data, factory-based approaches are usually more effective.

</details>

<details>
<summary>91. How do async views and async ORM work in Django?</summary>

#### Django

Django supports asynchronous views (`async def`) and is gradually evolving an
async stack for I/O-heavy scenarios. The main value of async is better
scalability with many concurrent waits (external APIs, network operations).

#### Async view in Django:

```python
from django.http import JsonResponse

async def async_health(request):
    return JsonResponse({"status": "ok"})
```

#### When async is truly useful:

1. Lots of I/O waiting (HTTP calls to third-party services).
2. Long-polling/websocket patterns (with the appropriate stack).
3. High request concurrency with relatively light CPU logic.

#### Sync vs Async in Django:

1. `def view(...)` -> synchronous view.
2. `async def view(...)` -> asynchronous view.
3. Django can bridge sync/async boundaries, but extra transitions add overhead.

#### Working with DB (ORM):

- Historically, ORM was sync-first.
- In modern Django versions, async variants exist for some operations (`aget`,
  `acreate`, `aupdate_or_create`, async iteration, etc.), but you must consider
  compatibility of your Django version and DB driver.

Example:

```python
user = await User.objects.aget(pk=user_id)
```

#### Important limitations:

1. Not all third-party libraries provide async-safe APIs.
2. Async does not speed up CPU-bound tasks (use workers/queues/processes).
3. Mixing sync ORM calls in async code can block event loop.

#### Practical recommendations:

1. Use async where there is a real I/O bottleneck.
2. If stack is mostly sync, do not force async "for trend".
3. Minimize sync<->async transitions.
4. For background CPU/long processing use Celery/RQ, not `await` in views.

#### Common mistakes:

1. Expecting performance gain without changing app's I/O profile.
2. Doing blocking sync calls inside async views.
3. Not testing behavior under concurrent load.

#### Conclusion:

Async in Django is a powerful tool for I/O-heavy scenarios, but not a universal
solution. Effectiveness depends on alignment of whole stack: views, ORM,
external clients, and actual load profile.

</details>

<details>
<summary>92. How do you create backend tasks (`@task`, Celery)?</summary>

#### Django

Backend tasks (background jobs) in Django are used for heavy or deferred
operations that should not run directly in HTTP request flow: email sending,
imports, file generation, integrations, retries.

#### Most common stack:

- **Celery** + broker (usually Redis or RabbitMQ) + workers

#### Basic architecture:

1. Django code enqueues a task.
2. Broker stores the message.
3. Celery worker picks task and executes it asynchronously.
4. (Optional) result is saved in a result backend.

#### Task example:

```python
# app/tasks.py
from celery import shared_task

@shared_task
def send_welcome_email(user_id):
    # email sending logic
    return {"user_id": user_id, "status": "sent"}
```

Call from view/service:

```python
send_welcome_email.delay(user.id)
```

#### Minimal Celery integration with Django:

1. Install:

```bash
pip install celery redis
```

2. Add `celery.py` in project config.
3. Set broker URL in settings/env.
4. Start worker:

```bash
celery -A config worker -l info
```

#### Periodic tasks:

- Via `celery beat` or `django-celery-beat` (cron-like scheduler).

#### Practical recommendations:

1. Tasks should be **idempotent** (rerun does not corrupt data).
2. Add `retry` for temporary failures (network, third-party APIs).
3. Do not pass heavy objects to task; pass `id` and load data in worker.
4. Log execution status and errors.
5. Define worker timeouts and concurrency limits.

#### Common mistakes:

1. Running long operations in view instead of queue.
2. Missing retry policy for external service integrations.
3. Unexpected duplicate tasks due to non-idempotent logic.
4. No monitoring for queues and stuck tasks.

#### Conclusion:

Celery in Django is the standard for asynchronous backend processing. Key to
reliability: idempotency, retries, monitoring, and clear separation between HTTP
flow and background processing.

</details>

<details>
<summary>93. What is Django REST Framework?</summary>

#### Django

**Django REST Framework (DRF)** is a popular framework on top of Django for
building REST APIs: data serialization, validation, authorization, routing,
pagination, and a convenient browsable API interface.

#### Why DRF is used:

1. Quickly build stable APIs for web/mobile clients.
2. Standardize validation and response format.
3. Flexibly control auth/permissions/throttling.
4. Reduce boilerplate compared to plain `JsonResponse` views.

#### Key DRF components:

1. **Serializer**

- Converts model/object <-> JSON.
- Validates input data.

2. **APIView / GenericAPIView / ViewSet**

- Layers for implementing endpoint logic.

3. **Routers**

- Automatic URL generation for ViewSets.

4. **Authentication / Permissions**

- Control who you are and what you are allowed to do.

5. **Pagination / Filtering / Ordering**

- Built-in mechanisms for lists and search.

#### Serializer example:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### ViewSet example:

```python
from rest_framework.viewsets import ModelViewSet
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
```

#### Router example:

```python
from rest_framework.routers import DefaultRouter
from .views import ArticleViewSet

router = DefaultRouter()
router.register("articles", ArticleViewSet, basename="article")
urlpatterns = router.urls
```

#### When DRF is especially appropriate:

1. You need API-first or multi-client product.
2. You have complex permission/pagination/filtering requirements.
3. You need scalable API architecture and standardized error format.

#### Conclusion:

DRF is the de facto API standard in Django ecosystem. It adds structured API
architecture, speeds up development, and simplifies support of production
endpoints.

</details>

<details>
<summary>94. What is serialization and why is it needed?</summary>

#### Django

Serialization is transforming Python objects/models into a transferable format
(usually JSON), while deserialization is the reverse transformation into objects
with validation.

#### Why serialization is needed:

1. Transfer data between backend and frontend/mobile clients.
2. Standardize API response format.
3. Validate input data before writing to DB.
4. Decouple DB model from external API contract.

#### Serialization in DRF:

- Done via `Serializer` or `ModelSerializer`.

Example:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Transform model -> JSON:

```python
article = Article.objects.first()
data = ArticleSerializer(article).data
```

#### Transform JSON -> validated data/model:

```python
payload = {"title": "New", "is_published": True}
serializer = ArticleSerializer(data=payload)
serializer.is_valid(raise_exception=True)
obj = serializer.save()
```

#### What serializers also provide:

1. Type and required-field validation.
2. Custom validation (`validate_<field>`, `validate`).
3. Read-only/write-only field control.
4. Nested serializers for related entities.

#### Practical recommendations:

1. Do not expose model "as is" without explicit serializer contract.
2. Keep API schema stable and backward-compatible.
3. Validate custom business rules in serializer or service layer.
4. Use separate serializers for different use cases (list/detail/create/update).

#### Conclusion:

Serialization is the core of API layer in Django/DRF: it defines data format,
validation, and contract stability between server and clients.

</details>

<details>
<summary>95. What are key Django features when used with REST framework (DRF)?</summary>

#### Django

Django + DRF is a combination of a mature web framework and a powerful API
layer. It fits production REST services with a clear domain model.

#### Key DRF features in Django ecosystem:

1. **Serializer-first approach**

- Clear API contract, input validation, field-level control.

2. **Flexible endpoint construction**

- `APIView`, `GenericAPIView`, `ViewSet`, `ModelViewSet`.

3. **Automatic routing**

- Routers significantly reduce CRUD API boilerplate.

4. **Auth + permissions**

- Session, Token, JWT (via packages), custom permission classes.

5. **Pagination, filtering, ordering**

- Built-in mechanisms for list endpoints in large systems.

6. **Throttling**

- Request rate limiting (anti-abuse / API hygiene).

7. **Content negotiation**

- Support for different renderer/parser types (JSON by default).

8. **Browsable API**

- Convenient developer UI for manual endpoint inspection.

#### Typical production stack with DRF:

1. Versioned API (`/api/v1/...`).
2. Scenario-specific serializers (`list/detail/create/update`).
3. Permission policy per endpoint.
4. Standardized error format.
5. Pagination + filtering + DB indexing.

#### Strengths of this approach:

1. High development speed without losing structure.
2. Compatibility with Django auth/admin/ORM/migrations.
3. Easy extension via custom classes for business requirements.

#### What to watch out for:

1. Do not overload `ModelViewSet` with complex domain logic.
2. Control N+1 queries in serializer/viewset.
3. Clearly separate API contract from internal data model.

#### Conclusion:

DRF makes Django a strong enterprise-level API framework: fast start, structured
architecture, mature security, and scalability for real multi-client products.

</details>

<details>
<summary>96. What role does Django play in service architecture and REST API?</summary>

#### Django

In modern architecture, Django most often acts as the **core business backend**:
it manages domain logic, transactional data, admin processes, and REST APIs for
web/mobile clients.

#### Typical Django roles in architecture:

1. **Modular monolith (most common)**

- One service with clear decomposition into apps/domains.
- Fast product delivery and simpler operations.

2. **API service (DRF)**

- Pure backend for SPA/mobile/partner integrations.

3. **Core service in microservice ecosystem**

- Django as source of truth for critical domains (users, billing, orders).

4. **Backoffice/Admin service**

- Internal operations and data management via Django Admin + custom UI.

#### Why Django fits this role well:

1. Fast full backend-cycle development.
2. Strong ORM + transactional model.
3. Mature auth/permissions system.
4. DRF for standardized API.
5. Reliable admin interface for operations teams.

#### Where Django may not be ideal as first choice:

1. Ultra-light high-concurrency API-only services (sometimes FastAPI fits
   better).
2. Specific low-latency scenarios with minimal framework overhead.

#### Practical architectural approach:

1. Start with Django monolith and clear domain boundaries.
2. Split into separate services only when real scaling needs appear.
3. Keep Django as core domain/API/admin node.

#### Integration with other services:

- Celery/queues for async processing
- Redis for cache
- Search engine for full-text search
- Object storage/CDN for media
- Observability stack (logs, metrics, tracing)

#### Conclusion:

Django has a strong position as backbone for business services and REST APIs.
For most products, it is a practical balance between development speed,
architectural discipline, and long-term maintainability.

</details>

<details>
<summary>97. How do you deploy a Django project (WSGI, ASGI, Nginx)?</summary>

#### Django

Django production deployment is usually built as:

1. **Nginx** - reverse proxy, static/media, TLS.
2. **App server** - Gunicorn (WSGI) or Uvicorn/Daphne (ASGI).
3. **Django app** - business logic.
4. **PostgreSQL/Redis** - data and cache/queues.

#### WSGI vs ASGI:

1. **WSGI (Gunicorn)**

- Classic stable option for sync Django applications.

2. **ASGI (Uvicorn/Daphne)**

- Required for async views, websockets, and modern async scenarios.

#### Minimal production flow:

1. Prepare environment:

- `DEBUG=False`
- `ALLOWED_HOSTS`
- secrets via env

2. Install dependencies:

```bash
pip install gunicorn
```

3. Collect static files:

```bash
python manage.py collectstatic --noinput
```

4. Apply migrations:

```bash
python manage.py migrate
```

5. Start app server:

```bash
gunicorn config.wsgi:application --bind 127.0.0.1:8000 --workers 4
```

#### Example Nginx config (simplified):

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

#### For ASGI deployment:

```bash
uvicorn config.asgi:application --host 127.0.0.1 --port 8000 --workers 4
```

#### Required security/ops checklist:

1. HTTPS (Let's Encrypt), secure cookies.
2. `CSRF_TRUSTED_ORIGINS` and correct proxy headers.
3. `SECURE_HSTS_SECONDS`, `SECURE_SSL_REDIRECT`, `X_FRAME_OPTIONS`.
4. Logs, monitoring, alerts (error rate, latency, DB health).
5. Backup and tested rollback plan.

#### Common mistakes:

1. `DEBUG=True` in production.
2. Missing `collectstatic` before release.
3. Wrong `ALLOWED_HOSTS` / proxy headers -> CSRF/redirect issues.
4. Running Django development server (`runserver`) in production.

#### Conclusion:

A stable Django deployment is Nginx + WSGI/ASGI app server + correct production
security and observability settings. Technically straightforward when release
process discipline is in place.

</details>

<details>
<summary>98. How do you scale a Django application?</summary>

#### Django

Scaling Django is not one step, but a sequence of decisions across code, DB,
cache, queues, and infrastructure. Best strategy is to scale by metrics, not
"just in case".

#### 1. Application optimization (first stage)

1. Remove N+1 queries (`select_related`, `prefetch_related`).
2. Optimize heavy endpoints (pagination, limits, indexes).
3. Minimize API/HTML payload.
4. Add caching where repeated "hot" queries exist.

#### 2. Caching and read acceleration

1. Redis for low-level/per-view/fragment cache.
2. CDN for static/media.
3. HTTP cache headers for public resources.

#### 3. Horizontal scaling at app level

1. Run multiple Django instances behind load balancer.
2. Keep app processes stateless (sessions in Redis/DB, no local state).
3. Autoscale based on CPU/RPS/latency.

#### 4. Move heavy tasks to background

1. Celery/RQ for async jobs.
2. Queues for email, reports, integrations, imports.
3. Retry/backoff and idempotency for reliability.

#### 5. Database scaling

1. Indexing and query tuning.
2. Connection pooling (PgBouncer).
3. Read replicas for read-heavy scenarios.
4. Partitioning/sharding only with real need and clear architecture.

#### 6. Architecture evolution

1. From "monolith without boundaries" -> to modular monolith.
2. If needed, extract narrow domains into services.
3. Do not split to microservices prematurely.

#### 7. Observability as scaling prerequisite

1. Metrics: p95/p99 latency, error rate, queue lag, DB locks.
2. Logs with request-id.
3. Tracing across services/queues.
4. Alerts on SLA/SLO violations.

#### Common mistakes:

1. Scaling infra without optimizing queries first.
2. Caching without invalidation strategy.
3. Ignoring DB bottleneck.
4. Premature microservice complexity.

#### Conclusion:

Scaling Django is a managed process: first optimize code and DB, then add cache
and queues, then scale app instances horizontally, and only after that increase
architectural complexity. Metrics should drive all decisions.

</details>

<details>
<summary>99. What are deployment and monitoring approaches for a Django app?</summary>

#### Django

Reliable Django production is built on two pillars:

1. **controlled deployment**
2. **full monitoring (observability)**

#### Deployment approaches:

1. **Classic VM/VPS deployment**

- Nginx + Gunicorn/Uvicorn + systemd + PostgreSQL/Redis.
- Fits controlled self-hosted environments.

2. **Container-based (Docker/Kubernetes)**

- Predictable environment, scaling via replicas.
- Convenient for teams with DevOps processes.

3. **PaaS/Managed platforms**

- Faster launch, lower ops overhead.
- Trade-off in infrastructure flexibility.

#### Recommended release pipeline:

1. CI: tests + linters + security checks.
2. Build immutable artifact (image).
3. Deploy to staging.
4. Smoke/health checks.
5. Production rollout (blue/green, rolling, or canary).
6. Automatic rollback on degradation.

#### What must be monitored:

1. **Application metrics**

- RPS, p95/p99 latency, 4xx/5xx error rate.

2. **Infrastructure metrics**

- CPU, RAM, disk, network, pod/container restart rate.

3. **Database metrics**

- slow queries, locks, connections, replication lag.

4. **Queue/worker metrics**

- queue depth, task latency, retry/failure rate.

5. **Logs + tracing**

- structured logs, request-id, distributed tracing.

#### Minimal production set:

1. Health endpoints (`/health/live`, `/health/ready`).
2. Centralized logs (ELK/Loki/Cloud logs).
3. APM/metrics (Prometheus + Grafana, Datadog, New Relic, Sentry).
4. Alerts on SLO violations, not only on "server is down".

#### Practical recommendations:

1. Create incident runbook (who does what and how recovery happens).
2. Keep migrations backward-compatible for zero/min-downtime releases.
3. Automate secrets/config via env/secret manager.
4. Regularly drill rollback and disaster recovery.

#### Common mistakes:

1. Deploying without health checks and rollback strategy.
2. Monitoring only CPU without business metrics and latency.
3. No link between logs and specific request/trace id.
4. Manual hotfixes on server without codified reproducibility.

#### Conclusion:

Successful Django deployment is a predictable CI/CD process, and stable
operation requires monitoring that gives early degradation signals. Without
observability, even good code quickly loses production manageability.

</details>

<details>
<summary>100. What changes do patch releases usually include, and why is it important to update?</summary>

#### Django

Patch releases (for example, `5.1.2 -> 5.1.3`) usually include
**backward-compatible** fixes without major/minor-level public API changes that
break applications.

#### What patch releases usually include:

1. **Security fixes**

- Vulnerability patches (often critical for production).

2. **Bug fixes**

- Fixes in ORM, forms, middleware, admin, migrations, etc.

3. **Stability improvements**

- Better dependency compatibility, edge-case fixes.

4. **Minor docs/test improvements**

- Without changing architectural contract.

#### Why it is important to update:

1. **Security**

- Missing a security patch can leave known vulnerabilities in production.

2. **Reliability**

- Patch releases remove bugs that may surface under load.

3. **Compatibility**

- Modern libraries expect up-to-date framework patch versions.

4. **Easier upgrade path**

- Regular small updates are easier than rare big jumps.

#### Practical update process:

1. Update dependency (`pip`/`poetry`/`uv`).
2. Run tests and linters.
3. Review changelog/release notes.
4. Roll out to staging.
5. Release to production through controlled rollout.

#### Frequency:

- Check patch updates regularly (at least monthly or after security advisory).
- For LTS versions, apply security patches as quickly as possible.

#### Common mistakes:

1. Postponing patch updates "for later".
2. Updating in production without staging/CI checks.
3. Ignoring release notes and potential side effects.

#### Conclusion:

Patch releases are not "cosmetic"; they are operational hygiene of a project.
Regular Django updates reduce security risks, improve stability, and make future
upgrades more predictable.

</details>
