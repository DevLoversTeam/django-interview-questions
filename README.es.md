**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  Django <img src="./assets/django.svg" width="40" height="40" alt="Django logo"/>
</h1>

<h2>Las preguntas y respuestas más populares de entrevista sobre Django</h2>

<details>
<summary>1. ¿Qué es Django y cuáles son sus capacidades clave?</summary>

#### Django

Django es un framework de alto nivel de Python para desarrollar aplicaciones web,
que sigue el principio de "batteries included": la mayoría de las tareas típicas
ya están resueltas dentro del ecosistema del framework.

#### Capacidades clave de Django:

1. **Inicio rápido del desarrollo:** generación de proyecto y apps, estructura lista
   y convenciones claras.
2. **Panel de administración integrado:** Django Admin se crea automáticamente para
   gestionar datos desde el navegador.
3. **ORM potente:** trabajo con la base de datos mediante modelos de Python sin SQL
   manual en la mayoría de los casos.
4. **Sistema de migraciones:** control y versionado de cambios en el esquema de BD.
5. **Enrutamiento URL y capa de views:** separación clara de rutas, lógica de negocio
   y presentación.
6. **Motor de plantillas:** templates integrados para renderizar HTML con soporte de
   herencia de plantillas.
7. **Seguridad por defecto:** protección contra CSRF, XSS, SQL injection,
   clickjacking y prácticas seguras de autenticación.
8. **Autenticación integrada:** usuarios, grupos, permisos y sesiones.
9. **Trabajo con formularios:** Django Forms/ModelForms con validación del lado del servidor.
10. **Escalabilidad y ecosistema:** caché, middleware, señales,
    integración con Celery, DRF, Redis, PostgreSQL, etc.

#### Cuándo Django es especialmente adecuado:

- CRM/ERP y sistemas internos de negocio.
- Plataformas de contenido, marketplaces, paneles de usuario.
- API + parte web en un mismo proyecto.
- Productos donde importan la velocidad de implementación, la seguridad y la mantenibilidad del código.

#### Ejemplo breve de "qué ofrece Django de fábrica":

```bash
django-admin startproject config .
python manage.py startapp users
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Después de esto, ya tienes un esqueleto básico del proyecto, la BD conectada,
el sistema de migraciones y acceso al panel de administración.

#### Conclusión:

Django es una elección práctica para desarrollo backend rápido y seguro, especialmente
cuando se necesita arquitectura madura, stack estable y lanzamiento veloz del producto.

</details>

<details>
<summary>2. ¿Cuáles son las ventajas de usar Django?</summary>

#### Django

Django se elige a menudo para desarrollo comercial cuando se necesita un time-to-market
rápido, una arquitectura estable y un backend seguro sin "pegar" decenas de
bibliotecas de terceros.

#### Ventajas clave de Django:

1. **Alta velocidad de desarrollo:** muchas tareas típicas ya están implementadas
   (auth, admin, forms, ORM, sessions, cache).
2. **Seguridad "de fábrica":** mecanismos integrados contra CSRF, XSS, SQL injection,
   clickjacking y manejo seguro de contraseñas.
3. **Estructura clara del proyecto:** convenciones comprensibles que simplifican el
   onboarding del equipo y el mantenimiento del código a largo plazo.
4. **ORM y migraciones potentes:** trabajo rápido con BD, control de la evolución
   del esquema y buen soporte para PostgreSQL y otros SGBD relacionales.
5. **Panel admin para negocio:** Django Admin permite dar rápidamente al equipo de
   contenido/operaciones una interfaz funcional sin frontend separado.
6. **Buena escalabilidad de arquitectura:** apps, middleware, signals, celery,
   cachés y colas se integran fácilmente en escenarios de producción.
7. **Ecosistema maduro:** DRF, django-allauth, django-filter, django-celery-beat
   y otras herramientas probadas.
8. **Apto para proyectos enterprise:** releases predecibles, gran comunidad,
   documentación de calidad y prácticas estables.

#### Valor práctico para el equipo:

- Menos código de infraestructura al inicio.
- Menos riesgo de errores de seguridad en la implementación base.
- Lanzamiento de MVP más rápido y ruta de escalado más clara.
- Mejor mantenibilidad al crecer el equipo y el código.

#### Cuándo las ventajas de Django se notan más:

- B2B SaaS, CRM/ERP, paneles de usuario, marketplaces.
- Proyectos con mucha lógica de negocio y roles de acceso.
- Equipos para los que son clave la estabilidad y el desarrollo predecible del producto.

#### Conclusión:

La ventaja de Django está en que ofrece resultado de negocio rápido sin comprometer
la seguridad ni la mantenibilidad del código.

</details>

<details>
<summary>3. ¿Cuál es la diferencia entre la arquitectura MVC y MVT?</summary>

#### Django

En Django se habla más de **MVT (Model-View-Template)**, mientras que en muchos
otros frameworks se usa el término **MVC (Model-View-Controller)**.
Conceptualmente son enfoques muy cercanos; la diferencia está sobre todo en roles y nombres.

#### MVC (clásico):

1. **Model** - trabajo con datos y lógica de negocio.
2. **View** - visualización de datos (UI / presentation layer).
3. **Controller** - procesa la solicitud entrante y controla el flujo entre Model y View.

#### MVT en Django:

1. **Model** - modelos de datos y acceso a BD mediante ORM.
2. **View** - procesamiento de la solicitud HTTP, ejecución de lógica de negocio, preparación de respuesta.
3. **Template** - capa de presentación (HTML + template syntax).

#### Relación entre MVC y MVT:

- `Model (MVC)` ≈ `Model (Django MVT)`
- `View (MVC)` ≈ `Template (Django MVT)`
- `Controller (MVC)` ≈ `View + URL dispatcher (Django MVT)`

Es decir, en Django el rol del "controller" se divide entre `urls.py` (routing) y
`views.py` (procesamiento de la solicitud).

#### Ejemplo simple de flujo en Django (MVT):

1. La solicitud llega a una URL, por ejemplo `/articles/`.
2. `urls.py` la envía al `view` correspondiente.
3. El `view` obtiene datos del `Model`.
4. El `view` pasa datos al `Template`.
5. El `Template` renderiza HTML y se devuelve `HttpResponse`.

#### Conclusión:

- Django no "rompe" MVC, sino que lo implementa en su propia variante MVT.
- Diferencia práctica clave: en Django `view` es lógica de procesamiento de solicitud,
  y la representación visual está en `template`.

</details>

<details>
<summary>4. ¿Por qué a Django se le llama un framework loosely coupled?</summary>

#### Django

A Django se le llama un framework **loosely coupled** (débilmente acoplado) porque
sus componentes se pueden cambiar, ampliar o sustituir de forma independiente,
sin reescribir toda la aplicación.

#### Qué significa esto en la práctica:

1. **Componentes separados por responsabilidad:** rutas URL, views, plantillas,
   modelos, formularios y middleware trabajan juntos, pero no están "fusionados"
   en una sola capa monolítica de lógica.
2. **Arquitectura de apps tipo plugin:** el proyecto se compone de `apps` que se
   pueden conectar/desconectar vía `INSTALLED_APPS`.
3. **Posibilidad de sustituir partes concretas:** por ejemplo, motor de plantillas,
   user model, backend de caché, email backend, storage backend.
4. **Configuración a través de settings:** el comportamiento del sistema se controla
   con configuración y no con lógica rígidamente incrustada.
5. **Extensión mediante middleware y signals:** se puede añadir funcionalidad
   sin modificar el núcleo de la lógica de negocio.

#### Ejemplos típicos del enfoque loosely coupled en Django:

- Cambiar SQLite por PostgreSQL solo mediante configuración de `DATABASES`.
- Añadir caché Redis sin reescribir views ni modelos.
- Pasar de almacenamiento local a S3-compatible storage a través del backend.
- Mover auth a un modelo de usuario personalizado (`AUTH_USER_MODEL`) sin romper
  la arquitectura de todo el proyecto.

#### Por qué esto es importante para el equipo:

- Es más fácil escalar el producto por módulos.
- Es más fácil testear partes aisladas del sistema.
- Hay menos riesgos durante refactorización.
- Es más fácil mantener el código en un ciclo de vida largo del proyecto.

#### Conclusión:

Loosely coupled en Django significa flexibilidad de ingeniería: puedes evolucionar
el proyecto gradualmente, cambiando subsistemas concretos en lugar de rehacer todo a la vez.

</details>

<details>
<summary>5. ¿Cuál es la diferencia entre Django y FastAPI?</summary>

#### Django

Django y FastAPI resuelven problemas distintos. Ambos frameworks son fuertes,
pero se eligen para tipos diferentes de producto y de equipo.

#### Diferencia clave:

- **Django** - framework web full-stack "de fábrica" (ORM, admin, auth,
  templates, forms, sessions, middleware).
- **FastAPI** - framework ASGI ligero y muy rápido, orientado sobre todo
  a construir API con tipado y documentación automática.

#### Comparación Django vs FastAPI:

1. **Propósito**
- Django: sistemas web completos y API en un mismo proyecto.
- FastAPI: API-first, microservicios, servicios high-concurrency.

2. **Velocidad de arranque del proyecto**
- Django: muy rápido para CRUD/admin/paneles.
- FastAPI: rápido para API, pero hay que ensamblar más decisiones por cuenta propia.

3. **Rendimiento**
- Django: suficiente para la mayoría de escenarios de negocio; clásicamente WSGI,
  pero también soporta modo ASGI.
- FastAPI: normalmente mayor rendimiento en carga I/O gracias al enfoque async-first.

4. **ORM y trabajo con BD**
- Django: ORM integrado y maduro + migraciones.
- FastAPI: ORM no integrado; normalmente SQLAlchemy/SQLModel/Tortoise.

5. **Admin y back-office**
- Django: potente Django Admin "de fábrica".
- FastAPI: el admin hay que construirlo o integrarlo aparte.

6. **Validación y esquemas**
- Django: forms/DRF serializers.
- FastAPI: modelos Pydantic como estándar de facto.

7. **Documentación API**
- Django: normalmente con DRF + paquetes Swagger/OpenAPI.
- FastAPI: OpenAPI/Swagger UI se genera automáticamente.

8. **Ecosistema**
- Django: muy amplio para productos web (CMS, auth, patrones de admin).
- FastAPI: fuerte en API/microservicios, stack async moderno.

#### Cuándo elegir Django:

- Se necesita un backend "all-in-one" con resultado de negocio rápido.
- Hay un modelo complejo de roles, admin y muchas entidades CRUD.
- El equipo prioriza convenciones estables y mantenibilidad a largo plazo.

#### Cuándo elegir FastAPI:

- Se necesita un servicio API-first con alta concurrencia de solicitudes.
- Prioridad: integraciones async (API externas, colas, streaming, escenarios websocket).
- El equipo quiere un stack lo más ligero y controlable posible.

#### Conclusión:

- **Django** - óptimo para lanzar rápido funcionalidad de negocio y sistemas web complejos.
- **FastAPI** - óptimo para APIs modernas de alto rendimiento y escenarios de microservicios.
- En productos grandes estos frameworks a menudo coexisten: Django como core/admin,
  FastAPI como servicios API separados.

</details>

<details>
<summary>6. ¿Cuáles son las desventajas y limitaciones de Django en comparación con otros frameworks?</summary>

#### Django

Django es un framework sólido, pero no es universalmente el mejor para todos los
tipos de proyectos. Sus limitaciones suelen aparecer en escenarios técnicos específicos.

#### Principales desventajas y limitaciones de Django:

1. **Entrada más "pesada" para servicios muy simples**
- Para un microservicio pequeño, Django puede ser excesivo por el volumen
  de componentes integrados.

2. **UX menos "native async-first" que FastAPI**
- Django soporta async, pero históricamente muchas partes del ecosistema están
  orientadas al enfoque sync.
- Para APIs I/O de alta carga, FastAPI/Starlette a veces ofrecen un camino más simple.

3. **El ORM no es ideal para SQL complejo**
- El ORM de Django es potente para la mayoría de tareas, pero para consultas
  analíticas muy complejas u optimizaciones específicas de BD, igual toca escribir raw SQL.

4. **Convenciones rígidas**
- Las convenciones de Django son una ventaja para el equipo, pero para ingenieros
  que quieren control máximo y "fino", pueden parecer una limitación.

5. **Estilo monolítico por defecto**
- Django empuja de forma natural a un monolito modular, no a microservicios pequeños.
- Para una arquitectura microservice-first se requiere disciplina clara de separación.

6. **Pasos extra para un DX moderno API-first**
- Para un REST API completo normalmente se añade DRF, para OpenAPI herramientas
  adicionales, y para realtime un stack aparte (por ejemplo, Channels).

7. **El rendimiento "de fábrica" no siempre es máximo**
- Sin caché, índices de BD, optimización de consultas ORM y profiling correcto,
  los sistemas grandes pueden funcionar lentamente.

#### Errores típicos que se confunden con "desventajas de Django":

- Consultas N+1 por uso incorrecto del ORM.
- Ausencia de estrategia de caché.
- Mala descomposición modular de apps.
- Mezcla de lógica de negocio en views sin capa de servicios.

Esto suele ser más un tema de arquitectura del equipo que una debilidad del framework.

#### Cuándo Django puede no ser la mejor opción:

- Un servicio API muy ligero con mínima lógica de negocio.
- API async de alto throughput como requisito principal.
- Un sistema donde se necesita control low-level máximo sin un core de framework "pesado".

#### Conclusión:

Las limitaciones de Django son reales, pero previsibles. Para la mayoría de aplicaciones
de negocio, sus ventajas (velocidad de desarrollo, seguridad, mantenibilidad) superan los costos.
Lo importante es elegir framework según el contexto de la tarea, no por "tendencia".

</details>

<details>
<summary>7. ¿Cómo funciona Django (ciclo de vida solicitud–respuesta)?</summary>

#### Django

El ciclo de vida en Django es una secuencia de pasos desde que una solicitud HTTP
llega al servidor hasta que se forma la respuesta HTTP final para el cliente.

#### Secuencia de procesamiento de la solicitud:

1. **El cliente envía una solicitud HTTP**
- El navegador o cliente API llama a la aplicación Django.

2. **El servidor WSGI/ASGI pasa la solicitud a Django**
- Por ejemplo: Gunicorn/Uvicorn + Nginx.

3. **La request pasa por middleware (fase request)**
- Los middleware pueden modificar/enriquecer la solicitud:
  autenticación, sesiones, locale, chequeos de seguridad, etc.

4. **El URL resolver busca la ruta correspondiente**
- Django compara la URL con las reglas en `urls.py`.
- Si no se encuentra ruta -> `404 Not Found`.

5. **Se llama al view**
- El view recibe `request` y ejecuta lógica de negocio:
  lee/escribe datos, valida acceso y forma contexto.

6. **Trabajo con modelos y BD (si hace falta)**
- Mediante ORM (`Model.objects...`) o raw SQL para casos complejos.

7. **Formación de la respuesta**
- HTML vía `render(...)` + template,
- o JSON vía `JsonResponse`,
- o redirect / file response.

8. **La response pasa por middleware (fase response)**
- Los middleware pueden añadir headers, cookies, control de caché y logging.

9. **La respuesta vuelve al cliente**
- El navegador renderiza la página o el cliente procesa la respuesta API.

#### Qué ocurre en caso de errores:

- `Http404` o ruta inexistente -> página 404.
- Excepciones no capturadas -> página 500.
- El manejo de excepciones también pasa por la cadena de middleware.

#### Cadena resumida:

`Client -> Server (WSGI/ASGI) -> Middleware (request) -> URLconf -> View -> Model/ORM -> Template/Serializer -> Middleware (response) -> Client`

#### Conclusión:

La fuerza de Django está en un pipeline request/response predecible: es fácil de
debuggear, testear y escalar porque cada etapa tiene responsabilidad clara.

</details>

<details>
<summary>8. ¿Cómo crear un nuevo proyecto Django?</summary>

#### Django

Un nuevo proyecto Django se crea en varios pasos estándar: preparar el entorno,
instalar Django, generar el proyecto, aplicar migraciones y ejecutar el servidor.

#### Paso a paso:

1. **Crea el directorio del proyecto**

```bash
mkdir my_django_project
cd my_django_project
```

2. **Crea y activa un entorno virtual**

```bash
python -m venv .venv
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate         # Windows (PowerShell/CMD)
```

3. **Instala Django**

```bash
pip install django
```

4. **Genera el proyecto**

```bash
django-admin startproject config .
```

Después aparecerán archivos clave:
- `manage.py`
- `config/settings.py`
- `config/urls.py`
- `config/asgi.py`
- `config/wsgi.py`

5. **Aplica las migraciones iniciales**

```bash
python manage.py migrate
```

6. **Crea un administrador**

```bash
python manage.py createsuperuser
```

7. **Inicia el servidor de desarrollo**

```bash
python manage.py runserver
```

#### Verificación:

- Abre `http://127.0.0.1:8000/` - página inicial de Django.
- Abre `http://127.0.0.1:8000/admin/` - panel admin (después de `createsuperuser`).

#### Siguiente paso recomendado:

Crea la primera app y conéctala en `INSTALLED_APPS`:

```bash
python manage.py startapp core
```

Este es un inicio básico y correcto para la mayoría de proyectos Django.

#### Conclusión:

El proceso estándar de bootstrap en Django es simple y predecible: en pocos comandos
otienes un esqueleto funcional de proyecto listo para seguir desarrollando.

</details>

<details>
<summary>9. ¿Por qué es importante usar un entorno virtual al trabajar con Django?</summary>

#### Django

Un entorno virtual (`venv`) aísla las dependencias de un proyecto concreto del
Python global del sistema. Para Django esto es crítico, porque los proyectos suelen
tener versiones de librerías y requisitos de compatibilidad distintos.

#### Por qué es importante:

1. **Aislamiento de dependencias**
- Cada proyecto usa sus propias versiones de `Django`, `djangorestframework`,
  `psycopg`, `celery`, etc., sin conflictos con otros proyectos.

2. **Reproducibilidad del entorno**
- Es fácil fijar el estado de dependencias en `requirements.txt` y reproducirlo
  en otra máquina o servidor.

3. **Estabilidad del deploy**
- Menos probabilidad del "works on my machine" cuando localmente hay una versión
  del paquete y en CI/production hay otra.

4. **Actualizaciones seguras**
- Puedes probar el upgrade de Django o de paquetes de terceros sin riesgo de romper
  otros proyectos locales.

5. **Limpieza del Python del sistema**
- Las herramientas del sistema operativo no dependen de paquetes instalados para desarrollo.

#### Qué pasa sin `venv`:

- Conflictos de versiones entre proyectos.
- Errores de importación impredecibles tras `pip install` de un paquete nuevo.
- Debug complejo de problemas en CI/CD por entornos distintos.
- Herramientas locales rotas por actualizaciones globales.

#### Práctica mínima para el equipo:

1. Crear `.venv` en la raíz de cada repositorio.
2. Activar siempre el entorno antes de `pip install` y comandos `manage.py`.
3. Fijar dependencias en `requirements.txt` (o `pyproject.toml` + lock file).
4. Añadir `.venv/` a `.gitignore`.

#### Conclusión:

`venv` en Django no es opcional, es un estándar base de disciplina de ingeniería.
Asegura previsibilidad, estabilidad y un workflow de equipo saludable.

</details>

<details>
<summary>10. ¿Cuál es la estructura de un proyecto Django y para qué sirven los archivos principales: manage.py, settings.py, urls.py?</summary>

#### Django

Un proyecto Django típico tiene dos partes clave: la raíz del repositorio y el
paquete de configuración (a menudo `config/`), donde están los ajustes globales.

#### Estructura base del proyecto:

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

#### Función de los archivos principales:

1. **manage.py**
- Punto de entrada CLI para trabajo local con el proyecto.
- Desde aquí se ejecutan comandos:
  `runserver`, `migrate`, `makemigrations`, `createsuperuser`, `test`, `shell`.
- Indica automáticamente a Django qué módulo de settings usar.

2. **settings.py**
- Configuración central del proyecto.
- Aquí se definen:
  `INSTALLED_APPS`, `MIDDLEWARE`, `DATABASES`, `TEMPLATES`, `CACHES`,
  `STATIC_URL`, `MEDIA_URL`, `AUTH_PASSWORD_VALIDATORS`, `TIME_ZONE`, etc.
- Para producción normalmente se separa en módulos:
  `settings/base.py`, `settings/dev.py`, `settings/prod.py`.

3. **urls.py**
- Mapa global de rutas (URL dispatcher).
- Toma la ruta solicitada y la delega a la app correspondiente vía `include()`.
- También suele conectar `admin/`, rutas de health-check y routing de API.

#### Cómo funciona todo junto:

1. `manage.py` ejecuta un comando Django.
2. Django carga `settings.py`.
3. La solicitud HTTP pasa por middleware.
4. `urls.py` define qué `view` procesará la solicitud.
5. El `view` devuelve respuesta (HTML/JSON/redirect/file).

#### Recomendaciones prácticas de tech lead:

- Mantén `urls.py` "fino": el routing principal debe vivir a nivel de app.
- No conviertas `settings.py` en un "vertedero": usa estructura modular.
- Todos los secretos (claves, contraseñas, tokens) guárdalos en variables de entorno, no en código.
- Saca la lógica de negocio de `views.py` hacia una capa de servicios para simplificar tests.

#### Conclusión:

`manage.py`, `settings.py` y `urls.py` son el núcleo operativo del proyecto Django:
gestión, configuración y routing. Una organización clara de estos archivos impacta
directamente en la escalabilidad y mantenibilidad del sistema.

</details>

<details>
<summary>11. ¿Para qué se usan las aplicaciones (apps) de Django y cómo organizar un proyecto con varias apps?</summary>

#### Django

En Django, una `app` es un módulo funcional aislado con sus propios modelos,
views, URLs, plantillas, tests y (si hace falta) capa API. Las apps se usan para
separar dominios y permitir un crecimiento controlado del código.

#### Para qué se usan las apps de Django:

1. **Modularidad**
- Cada app responde a un contexto de negocio concreto (por ejemplo: `users`,
  `billing`, `orders`, `notifications`).

2. **Reutilización**
- Una app puede moverse a otro proyecto o reutilizarse internamente.

3. **Localización de cambios**
- Los cambios en un dominio afectan menos a otros módulos.

4. **Mejor mantenibilidad**
- El equipo se orienta más fácil en el código cuando la responsabilidad está bien separada.

5. **Testing más simple**
- Los tests se escriben y ejecutan por dominios, no sobre un monolito caótico.

#### Cómo organizar un proyecto con múltiples apps:

1. **Divide por dominio, no por tipo técnico**
- Bien: `users`, `catalog`, `checkout`, `payments`.
- Mal: `models_app`, `views_app`, `utils_app`.

2. **Cada app con su propio `urls.py`**
- En `config/urls.py` raíz, solo conexión mediante `include()`.

3. **Mantén cada app autónoma**
- La app debe tener su `models.py`, `views.py`, `tests.py`, `admin.py`,
  `apps.py`, `migrations/`.

4. **Evita dependencias cíclicas entre apps**
- Para interacción entre módulos, mejor una capa de servicios o interfaces claras,
  no imports directos de "todo con todo".

5. **Saca el código compartido a un módulo `common/core`**
- Pero solo lo realmente común; no lo conviertas en un "cajón de sastre".

#### Ejemplo de estructura de proyecto multi-módulo:

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

#### Conexión de rutas por app:

```python
# config/urls.py
from django.urls import include, path

urlpatterns = [
    path("users/", include("apps.users.urls")),
    path("orders/", include("apps.orders.urls")),
]
```

#### Anti-patrones típicos:

- Una sola app "gigante" para todo el proyecto.
- Separación por capas técnicas en lugar de dominio de negocio.
- Código shared masivo sin propietario ni contratos.
- Cross-imports entre apps sin control de dependencias.

#### Conclusión:

Las apps de Django son una herramienta base para escalar código. Si separas el
sistema por dominios con límites claros, el proyecto permanece más tiempo controlable y estable.

</details>

<details>
<summary>12. ¿Cómo funciona el enrutamiento URL en Django?</summary>

#### Django

El enrutamiento URL en Django define qué `view` debe procesar una solicitud HTTP
concreta. De esto se encarga el URL dispatcher, configurado en `urls.py`.

#### Cómo funciona el routing URL paso a paso:

1. **La solicitud llega a Django**
- Por ejemplo: `GET /articles/42/`.

2. **Django lee el `urlpatterns` raíz**
- Normalmente en `config/urls.py`.

3. **Matching secuencial de rutas**
- Django evalúa patrones de arriba abajo.
- La primera coincidencia gana.

4. **Si hace falta, se llama `include()`**
- Una parte de la ruta se delega al `urls.py` de una app concreta.

5. **Los parámetros URL se pasan al view**
- Por ejemplo, `articles/<int:id>/` pasa `id` como argumento.

6. **El view forma la response**
- HTML, JSON, redirect o archivo.

7. **Si no hay coincidencia -> 404**
- Django devuelve `Not Found`.

#### Ejemplo básico:

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

#### Convertidores en `path()`:

- `<int:id>` -> número entero
- `<str:slug>` -> cadena sin `/`
- `<slug:slug>` -> formato slug
- `<uuid:id>` -> UUID
- `<path:subpath>` -> ruta arbitraria, incluyendo `/`

#### Reglas prácticas para mantenibilidad:

1. Mantén corto el `urls.py` raíz; delega en apps.
2. Usa `name=` para cada ruta (útil para `reverse()` y plantillas).
3. Sigue una estructura estable para API/web URL (versionado, prefijos).
4. El orden importa: coloca patrones específicos por encima de los generales.

#### Conclusión:

El URL routing en Django es un mecanismo controlado de despacho de solicitudes.
Rutas bien diseñadas hacen el código predecible, escalable y seguro para refactorizar.

</details>

<details>
<summary>13. Diferencia entre path() y re_path().</summary>

#### Django

`path()` y `re_path()` son dos formas de describir rutas URL en Django.
Resuelven la misma tarea, pero con distinto nivel de complejidad y flexibilidad.

#### `path()`:

- Usa sintaxis declarativa y legible con convertidores.
- Sirve para la mayoría de rutas comunes.
- Se lee mejor y es más fácil de mantener en equipo.

Ejemplo:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("posts/<int:post_id>/", views.post_detail, name="post_detail"),
    path("users/<slug:username>/", views.user_profile, name="user_profile"),
]
```

#### `re_path()`:

- Usa expresiones regulares (regex).
- Da máxima flexibilidad para patrones URL no estándar.
- Es más difícil de leer y tiene mayor riesgo de errores regex.

Ejemplo:

```python
from django.urls import re_path
from . import views

urlpatterns = [
    re_path(r"^archive/(?P<year>[0-9]{4})/$", views.archive_year),
    re_path(r"^file/(?P<path>.+\.(pdf|docx))/$", views.file_view),
]
```

#### Cuándo usar cada uno:

1. **Usa `path()` por defecto**
- Es el enfoque estándar y recomendado en Django moderno.

2. **Usa `re_path()` solo cuando `path()` no alcance**
- Por ejemplo, validación compleja del formato URL a nivel de ruta o esquemas legacy.

#### Comparación:

- Simplicidad: `path()` > `re_path()`
- Flexibilidad: `re_path()` > `path()`
- Mantenibilidad en equipo: normalmente `path()` gana

#### Consejo práctico:

No compliques URLs con regex sin necesidad. Si puedes resolverlo con
convertidores de `path()` + validación en view/serializer/form, suele ser mejor.

#### Conclusión:

`path()` es la herramienta principal para el 90% de las rutas. `re_path()` es una
solución puntual para casos especiales donde se necesita flexibilidad regex.

</details>

<details>
<summary>14. ¿Cómo funcionan las configuraciones URL y include()?</summary>

#### Django

La configuración URL en Django es un conjunto de reglas (`urlpatterns`) que
asocian la ruta solicitada con un `view` concreto. La función `include()` permite
dividir un routing grande en módulos por app.

#### Qué es una URL-configuración:

- Es un módulo Python (normalmente `urls.py`) con lista de rutas.
- Cada ruta se describe con `path()` o `re_path()`.
- Django recorre la lista de arriba abajo y toma la primera coincidencia.

#### Para qué sirve `include()`:

1. **Descomposición de rutas**
- El `urls.py` raíz se mantiene corto.

2. **Modularidad por apps**
- Cada app tiene sus rutas en su propio `urls.py`.

3. **Mejor mantenibilidad**
- El equipo trabaja con un contexto de routing local por dominio.

#### Ejemplo de organización:

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

#### Cómo funciona la cadena con `include()`:

1. La solicitud `/blog/django-routing/` llega a `config/urls.py` raíz.
2. El prefijo `blog/` coincide.
3. Django pasa el resto de la ruta (`django-routing/`) a `apps.blog.urls`.
4. Allí se encuentra la ruta correcta y se llama al `view` correspondiente.

#### Namespace y `app_name`:

- `app_name` + `name` de ruta da un namespace nombrado.
- Esto permite hacer reverse sin conflictos:
  `reverse("blog:detail", kwargs={"slug": "django-routing"})`.

#### Recomendaciones prácticas:

1. Usa siempre `include()` a nivel app.
2. Añade `app_name` en cada `urls.py` de app.
3. Mantén prefijos estables (`api/v1/`, `admin/`, `auth/`).
4. No dupliques lógica de negocio en capa URL; solo routing.

#### Conclusión:

URL-configuraciones + `include()` son la base de un routing escalable en Django:
límites claros entre apps, routing raíz limpio y navegación predecible.

</details>

<details>
<summary>15. ¿Qué es un view en Django?</summary>

#### Django

Un `view` en Django es el manejador de una solicitud HTTP. El view recibe `request`,
ejecuta la lógica necesaria y devuelve `HttpResponse` (HTML, JSON, redirect, archivo).

#### Rol del view en el ciclo request/response:

1. Recibir la solicitud después del URL-matching.
2. Validar parámetros de entrada (path/query/body/files).
3. Llamar lógica de negocio y/o ORM.
4. Preparar datos para la respuesta.
5. Devolver una response HTTP válida.

#### Tipos de view:

1. **FBV (Function-Based View)**
- Función Python normal.
- Adecuada para lógica simple o muy personalizada.

2. **CBV (Class-Based View)**
- Clase con métodos `get()`, `post()`, etc.
- Escala mejor para CRUD típico, especialmente con Generic Views.

#### Ejemplo FBV:

```python
from django.http import HttpResponse, JsonResponse
from django.shortcuts import render

def healthcheck(request):
    return HttpResponse("OK")

def home(request):
    return render(request, "home.html", {"title": "Inicio"})

def api_status(request):
    return JsonResponse({"status": "ok"})
```

#### Qué conviene recordar:

- El view no debe convertirse en una "god function".
- La lógica de negocio compleja conviene moverla a capa de servicios.
- El view debe ser delgado: orquestación, validación, llamada a servicios y response.

#### Errores típicos:

- Escribir lógica de dominio pesada de cientos de líneas directamente en view.
- Duplicar mucha lógica en distintos views.
- Ignorar controles de acceso/autorización a nivel endpoint.

#### Conclusión:

El view es el punto donde el protocolo web se encuentra con la lógica de negocio.
Views bien diseñados hacen el código predecible, testeable y fácil de mantener.

</details>

<details>
<summary>16. Diferencia entre vistas funcionales (FBV) y vistas basadas en clases (CBV).</summary>

#### Django

En Django hay dos estilos principales de vistas: **FBV** (function-based views) y
**CBV** (class-based views). Ambos enfoques son válidos; la diferencia está en cómo
se organiza la lógica y cómo escala el código.

#### FBV (Function-Based Views):

- La vista se define como función.
- La lógica request/response se lee de arriba abajo.
- Enfoque simple y transparente para endpoints pequeños.

Ejemplo:

```python
from django.http import JsonResponse

def profile_detail(request, user_id):
    if request.method == "GET":
        return JsonResponse({"user_id": user_id})
    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### CBV (Class-Based Views):

- La vista se define como clase (métodos `get`, `post`, `put`, `delete`, etc.).
- Se puede reutilizar lógica mediante herencia y mixins.
- Encaja bien en CRUD, listas, formularios y escenarios detail/create/update/delete.

Ejemplo:

```python
from django.http import JsonResponse
from django.views import View

class ProfileDetailView(View):
    def get(self, request, user_id):
        return JsonResponse({"user_id": user_id})
```

#### Diferencias clave:

1. **Simplicidad de entrada**
- FBV: más simple para empezar.
- CBV: requiere entender jerarquía de clases y mecánica de dispatch.

2. **Escalabilidad**
- FBV: bien para manejadores cortos y personalizados.
- CBV: mejor para patrones repetitivos y proyectos grandes.

3. **Reutilización de código**
- FBV: mediante helper functions/decorators.
- CBV: mediante herencia, mixins y generic views.

4. **Legibilidad**
- FBV: suele ser más obvio localmente.
- CBV: puede ser más complejo por comportamiento "oculto" de clases base.

5. **Testing**
- Ambos enfoques se testean bien si la lógica no está "incrustada" en la vista.

#### Cuándo elegir FBV:

- El endpoint es simple y muy personalizado.
- Se necesita máxima transparencia para debug rápido.
- No hay ventaja real en jerarquía de clases.

#### Cuándo elegir CBV:

- Hay muchos endpoints/pantallas CRUD similares.
- Se necesitan mixins, clases de permisos y patrones repetibles.
- El equipo trabaja con Generic CBV y mantiene estilo unificado.

#### Conclusión:

FBV y CBV no son "correcto/incorrecto", sino una elección de contexto. En
proyectos production se suelen usar ambos: FBV para tareas puntuales, CBV para
escenarios estructurados y repetibles.

</details>

<details>
<summary>17. ¿Cuándo conviene usar CBV y generic class-based views?</summary>

#### Django

CBV y generic CBV conviene usarlos cuando el proyecto tiene muchos patrones web/API
repetitivos y se necesita estandarizar el comportamiento entre endpoints.

#### Cuándo CBV realmente gana:

1. **Escenarios CRUD**
- Listas, detalle, creación, actualización y eliminación.
- Clases típicas: `ListView`, `DetailView`, `CreateView`, `UpdateView`, `DeleteView`.

2. **Muchos endpoints similares**
- Cuando la diferencia entre endpoints está solo en modelo, formulario o permisos.

3. **Necesidad de reutilizar lógica**
- Mediante mixins (`LoginRequiredMixin`, `PermissionRequiredMixin`, mixins propios).

4. **Estilo unificado en equipos grandes**
- CBV facilita unificar enfoque y reducir copy-paste.

5. **Extender comportamiento base con override**
- Por ejemplo, `get_queryset()`, `get_context_data()`, `form_valid()`,
  `get_success_url()`.

#### Cuándo generic CBV es especialmente apropiado:

- Interfaces tipo admin.
- Páginas back-office.
- Formularios estándar y secciones de contenido.
- Implementación rápida de MVP sin perder estructura.

#### Ejemplo generic CBV:

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

#### Cuándo NO conviene usar generic CBV:

1. La lógica es muy no estándar y no entra en paradigma CRUD.
2. El endpoint tiene orquestación compleja (varios servicios/integraciones).
3. El exceso de override vuelve la clase menos legible que una FBV simple.

#### Regla práctica de tech lead:

- Empieza con generic CBV para casos estándar.
- Si la vista "rompe" el modelo de comportamiento generic, pasa a CBV normal o FBV.
- No te aferres a generic solo "porque se ve más bonito": prioridad a mantenibilidad y claridad.

#### Conclusión:

CBV/generic CBV es una herramienta de aceleración y estandarización. Es mejor para
escenarios repetibles, pero para lógica de negocio atípica conviene enfoque más
simple y explícito.

</details>

<details>
<summary>18. ¿Qué son los mixins en CBV y cómo usarlos?</summary>

#### Django

Los `mixins` en CBV son clases auxiliares con comportamiento reutilizable que se
agregan a la vista vía herencia múltiple. Permiten construir vistas flexibles sin
duplicar código.

#### Para qué sirven los mixins:

1. **Reutilización de lógica**
- Autenticación, permisos, filtrado de queryset, contexto común, etc.

2. **Composición de comportamiento**
- La vista se compone de varios bloques pequeños, no de una sola clase enorme.

3. **Reducción de copy-paste**
- Un mixin puede usarse en decenas de vistas.

#### Mixins built-in más comunes en Django:

- `LoginRequiredMixin` - acceso solo para usuarios autenticados.
- `PermissionRequiredMixin` - verificación de permiso concreto.
- `UserPassesTestMixin` - chequeo de acceso personalizado.
- `ContextMixin` - agrega datos al contexto de plantilla.

#### Ejemplo con built-in mixins:

```python
from django.contrib.auth.mixins import LoginRequiredMixin, PermissionRequiredMixin
from django.views.generic import ListView
from .models import Order

class OrderListView(LoginRequiredMixin, PermissionRequiredMixin, ListView):
    model = Order
    permission_required = "orders.view_order"
    template_name = "orders/list.html"
```

#### Ejemplo de mixin personalizado:

```python
class StaffRequiredMixin:
    def dispatch(self, request, *args, **kwargs):
        if not request.user.is_staff:
            from django.http import HttpResponseForbidden
            return HttpResponseForbidden("Acceso denegado")
        return super().dispatch(request, *args, **kwargs)
```

```python
class DashboardView(StaffRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### El orden de mixins importa:

- Django usa MRO (Method Resolution Order).
- Normalmente los mixins "restrictivos" (`LoginRequiredMixin`) se ponen más a la izquierda.
- `View`/generic class va más a la derecha.

#### Reglas prácticas:

1. Un mixin, una responsabilidad.
2. No cargues mixins con lógica de negocio pesada.
3. Evita jerarquías de herencia profundas que dificultan debug.
4. Para lógica de dominio compleja usa servicios, no mixins.

#### Errores típicos:

- Mixins demasiado "inteligentes" que alteran comportamiento de forma impredecible.
- Conflictos de métodos por orden incorrecto de herencia.
- Duplicar chequeos iguales en muchas vistas en lugar de un mixin común.

#### Conclusión:

Los mixins son una herramienta potente en CBV para composición y reutilización.
Aportan máximo valor cuando son pequeños, claros en responsabilidad y usados con disciplina.

</details>

<details>
<summary>19. ¿Cómo manejar métodos HTTP (GET, POST)?</summary>

#### Django

En Django, los métodos HTTP se manejan en las vistas: `GET` normalmente lee/muestra
información, y `POST` crea o cambia el estado del sistema. Separar métodos
correctamente es base de un API y web-flow seguros y predecibles.

#### Manejo en FBV:

```python
from django.http import JsonResponse

def contact_view(request):
    if request.method == "GET":
        return JsonResponse({"form": "render contact form"})

    if request.method == "POST":
        # leer request.POST, validar, guardar
        return JsonResponse({"status": "created"}, status=201)

    return JsonResponse({"error": "Method not allowed"}, status=405)
```

#### Manejo en CBV:

```python
from django.http import JsonResponse
from django.views import View

class ContactView(View):
    def get(self, request):
        return JsonResponse({"form": "render contact form"})

    def post(self, request):
        # validación y guardado
        return JsonResponse({"status": "created"}, status=201)
```

#### Limitar métodos permitidos (decorators):

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

#### Reglas prácticas:

1. **GET**
- No debe cambiar el estado del sistema.
- Es seguro y cacheable en muchos escenarios.

2. **POST**
- Se usa para creación/acciones que modifican datos.
- Para formularios HTML, CSRF token obligatorio.

3. **Validación**
- Siempre valida datos de entrada (Forms/Serializer/capa de servicios).

4. **Códigos de respuesta**
- `200` para lectura exitosa,
- `201` para creación,
- `400` para errores de validación,
- `405` para método no permitido.

#### Errores típicos:

- Cambiar datos vía GET (rompe semántica HTTP).
- Mezclar lógica GET y POST en un bloque caótico.
- No devolver status code correcto.

#### Conclusión:

El manejo de GET/POST en Django debe ser explícito: cada método con su
responsabilidad, validación clara y códigos HTTP correctos. Esto mejora seguridad,
integraciones y mantenibilidad.

</details>

<details>
<summary>20. ¿Cómo implementar redirección (redirect)?</summary>

#### Django

La redirección (`redirect`) en Django se usa cuando, tras una acción, hay que
enviar al usuario a otra página o endpoint.

#### Forma principal:

```python
from django.shortcuts import redirect
```

`redirect(...)` devuelve una respuesta HTTP con código 302 (redirección temporal)
por defecto.

#### Variantes de uso:

1. **A URL absoluta/relativa**

```python
return redirect("/dashboard/")
```

2. **A ruta nombrada (recomendado)**

```python
return redirect("orders:list")
```

3. **A ruta con parámetros**

```python
return redirect("orders:detail", order_id=order.id)
```

4. **A instancia de modelo (si tiene `get_absolute_url`)**

```python
return redirect(order)
```

#### Ejemplo en FBV (Post/Redirect/Get):

```python
from django.shortcuts import redirect, render

def create_order(request):
    if request.method == "POST":
        # guardar datos
        return redirect("orders:list")
    return render(request, "orders/form.html")
```

#### Ejemplo en CBV:

```python
from django.urls import reverse_lazy
from django.views.generic import CreateView

class OrderCreateView(CreateView):
    model = Order
    fields = ["title", "amount"]
    success_url = reverse_lazy("orders:list")
```

#### Redirección temporal vs permanente:

- `302 Found` - temporal (por defecto en Django).
- `301 Moved Permanently` - permanente (para SEO/URL canónica).

Si necesitas redirección permanente:

```python
from django.http import HttpResponsePermanentRedirect

return HttpResponsePermanentRedirect("/new-url/")
```

#### Consejos prácticos:

1. Usa rutas nombradas en lugar de strings URL hardcodeadas.
2. Después de POST exitoso, haz redirect (patrón PRG) para evitar reenvío del
   formulario al hacer refresh.
3. Para redirect tras login/logout, usa `next` y validaciones seguras de destino.

#### Errores típicos:

- Redirect a URL que redirige de vuelta (redirect loop).
- Hardcodear URL en vez de usar `name=`.
- Devolver 200 tras POST-form sin PRG en flujos donde no conviene.

#### Conclusión:

`redirect` en Django es una herramienta base para controlar user flow. Mejor práctica:
rutas nombradas + patrón PRG + control de seguridad del destino.

</details>

<details>
<summary>21. ¿Qué es JsonResponse y cuándo se usa?</summary>

#### Django

`JsonResponse` es una respuesta HTTP de Django para devolver datos en formato JSON.
Se usa con mayor frecuencia en endpoints API, solicitudes AJAX e integraciones
entre servicios.

#### Qué hace `JsonResponse`:

1. Serializa datos de Python a JSON.
2. Establece el `Content-Type: application/json` correcto.
3. Permite indicar explícitamente el status code HTTP.

#### Ejemplo básico:

```python
from django.http import JsonResponse

def health(request):
    return JsonResponse({"status": "ok"})
```

#### Ejemplo con status code:

```python
def create_item(request):
    # ... lógica de creación
    return JsonResponse({"id": 123, "message": "created"}, status=201)
```

#### Matiz importante de `safe`:

- Por defecto, `JsonResponse` espera un **dict** (`safe=True`).
- Si necesitas devolver una lista, usa `safe=False`.

```python
def tags(request):
    return JsonResponse(["python", "django", "api"], safe=False)
```

#### Cuándo usar `JsonResponse`:

1. API simple sin DRF.
2. Endpoints internos para frontend (fetch/AJAX).
3. Respuestas de webhook e integraciones de servicio.
4. Endpoints de health-check/diagnóstico.

#### Cuándo conviene DRF en lugar de `JsonResponse` puro:

- Se necesitan serializers, validación de esquemas, paginación, throttling, políticas auth.
- Hay muchos endpoints API y se requiere arquitectura unificada de capa API.

#### Recomendaciones prácticas:

1. Devuelve siempre una estructura JSON clara (por ejemplo, `{"data": ...}`,
   `{"error": ...}`).
2. Usa status codes correctos (`200`, `201`, `400`, `404`, `500`).
3. No devuelvas tracebacks crudos de excepciones en production.
4. Define un formato de errores consistente para toda la API.

#### Conclusión:

`JsonResponse` es una herramienta ligera y cómoda para respuestas JSON en Django.
Para APIs simples suele bastar; para sistemas API grandes normalmente se migra a DRF.

</details>

<details>
<summary>22. ¿Cómo devolver archivos (CSV, PDF) desde una view?</summary>

#### Django

En Django, los archivos desde una view se devuelven mediante `HttpResponse` o
`FileResponse` con headers HTTP correctos (`Content-Type`, `Content-Disposition`).

#### Principios básicos:

1. **`Content-Type`** debe corresponder al tipo de archivo.
2. **`Content-Disposition`** define el comportamiento del navegador:
- `attachment` -> descargar archivo
- `inline` -> mostrar en navegador (si se soporta)

#### Ejemplo: devolver CSV

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

#### Ejemplo: devolver PDF desde archivo

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

#### Si el PDF se genera dinámicamente:

- Genera el PDF en memoria (`io.BytesIO`) o en archivo temporal.
- Luego devuélvelo vía `HttpResponse`/`FileResponse`.
- Librerías comunes: `reportlab`, `weasyprint`, `xhtml2pdf`.

#### Para archivos grandes:

1. Usa `FileResponse` (streaming, menos RAM).
2. No leas todo el archivo en memoria (`read()` de archivos grandes es no deseable).
3. Si hace falta, usa Nginx/X-Accel-Redirect o CDN/object storage.

#### Consejos prácticos:

1. Añade nombres de archivo claros en `filename=`.
2. Controla acceso a archivos (validación de owner/permisos).
3. Para documentos sensibles, añade auditoría de acceso.
4. En API devuelve errores previsibles (`404` si no existe archivo, `403` si acceso denegado).

#### Conclusión:

Devolver CSV/PDF en Django trata principalmente de tipo de response y headers correctos.
Para archivos pequeños basta `HttpResponse`; para archivos grandes y carga production,
conviene `FileResponse` y streaming.

</details>

<details>
<summary>23. ¿Cómo implementar paginación?</summary>

#### Django

La paginación en Django sirve para dividir listas grandes en páginas y no renderizar
ni enviar cientos o miles de registros en una sola solicitud.

#### Herramienta básica:

- `django.core.paginator.Paginator`

#### Ejemplo en FBV:

```python
from django.core.paginator import Paginator
from django.shortcuts import render
from .models import Article

def article_list(request):
    queryset = Article.objects.order_by("-created_at")
    paginator = Paginator(queryset, 10)  # 10 elementos por página
    page_number = request.GET.get("page")
    page_obj = paginator.get_page(page_number)  # variante segura

    return render(request, "articles/list.html", {"page_obj": page_obj})
```

#### Render de paginación en plantilla:

```django
{% for article in page_obj %}
  <h3>{{ article.title }}</h3>
{% endfor %}

<div class="pagination">
  {% if page_obj.has_previous %}
    <a href="?page=1">Primera</a>
    <a href="?page={{ page_obj.previous_page_number }}">Atrás</a>
  {% endif %}

  <span>Página {{ page_obj.number }} de {{ page_obj.paginator.num_pages }}</span>

  {% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">Siguiente</a>
    <a href="?page={{ page_obj.paginator.num_pages }}">Última</a>
  {% endif %}
</div>
```

#### Variante CBV (aún más simple):

```python
from django.views.generic import ListView
from .models import Article

class ArticleListView(ListView):
    model = Article
    paginate_by = 10
    ordering = ["-created_at"]
```

#### Recomendaciones prácticas:

1. Usa orden estable (`order_by`) para navegación predecible.
2. Para listas grandes, optimiza queryset:
- `select_related`, `prefetch_related`, índices en BD.
3. Conserva otros query params (filtros, búsqueda) al cambiar de página.
4. No pongas page size demasiado grande sin necesidad.

#### Errores típicos:

- Paginación sin orden (los datos "saltan" entre páginas).
- Uso de `page()` sin manejar número de página inválido.
- Falta de índices en columnas de orden/filtro.

#### Conclusión:

En Django la paginación se implementa rápido y limpio con `Paginator` o `ListView`.
La clave de rendimiento es queryset correcto, orden estable y control de parámetros de página.

</details>

<details>
<summary>24. ¿Cómo manejar errores 404 y 500?</summary>

#### Django

Los errores `404` y `500` en Django se manejan con el mecanismo estándar de
error-handling: plantillas de error, funciones handler y configuración global.

#### Qué significan estos errores:

- **404 Not Found** - ruta o recurso no encontrado.
- **500 Internal Server Error** - error no capturado en el servidor.

#### Manejo básico mediante plantillas:

En production (`DEBUG = False`), Django busca automáticamente:

- `templates/404.html`
- `templates/500.html`

Si estos archivos existen, se muestran al usuario.

#### Handlers personalizados en `urls.py`:

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

#### Diferencia importante entre dev y production:

1. **DEBUG=True (local)**
- Django muestra traceback detallado de debug.

2. **DEBUG=False (production)**
- El usuario ve páginas 404/500 personalizadas.
- Los detalles técnicos no deben filtrarse hacia afuera.

#### Recomendaciones prácticas:

1. Ten siempre páginas 404/500 personalizadas y amigables.
2. Loguea errores (Sentry/ELK/OpenTelemetry), no muestres stack trace al usuario.
3. Añade correlation/request ID en logs para investigación rápida.
4. Devuelve status codes correctos (no 200 en páginas de error).
5. Para API, devuelve errores JSON en formato unificado.

#### Testing:

- Verifica 404 para URL inexistentes.
- Prueba handlers 500 en staging con `DEBUG=False`.
- Asegúrate de que las plantillas de error estén disponibles en entorno compilado.

#### Conclusión:

Un buen manejo de 404/500 en Django combina UX y madurez operativa:
el usuario ve una página clara y el equipo recibe logs completos para diagnóstico.

</details>

<details>
<summary>25. ¿Qué son las plantillas (templates) y cómo pasar datos desde view a template?</summary>

#### Django

Las plantillas (`templates`) en Django son la capa de presentación responsable de
generar HTML a partir de datos preparados en la `view`.

#### Qué es un template:

- Archivo HTML con Django template syntax (`{{ }}` y `{% %}`).
- Permite mostrar variables, bucles, condiciones e inclusión de partes de página.
- Separa UI de la lógica de negocio en código Python.

#### Cómo pasar datos de view a template:

1. En la `view`, formar `context` (diccionario).
2. Llamar `render(request, "template.html", context)`.

#### Ejemplo:

```python
from django.shortcuts import render
from .models import Article

def article_list(request):
    articles = Article.objects.filter(is_published=True).order_by("-created_at")
    context = {
        "page_title": "Artículos",
        "articles": articles,
        "total": articles.count(),
    }
    return render(request, "articles/list.html", context)
```

#### Uso de datos en plantilla:

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
  <p>No hay artículos publicados.</p>
{% endif %}
```

#### De dónde toma Django las plantillas:

- De directorios indicados en `TEMPLATES["DIRS"]`.
- De carpetas `templates/` dentro de apps (cuando `APP_DIRS=True`).

#### Recomendaciones prácticas:

1. Mantén la lógica de negocio en Python (view/service), no en plantilla.
2. Pasa al context solo los datos necesarios.
3. Usa URL nombradas (`{% url 'app:view' %}`), no enlaces hardcodeados.
4. Para elementos repetidos usa `include`/partials.

#### Seguridad:

- Django auto-escapa variables en plantillas (protección XSS por defecto).
- No uses `|safe` si no confías en el origen de los datos.

#### Conclusión:

Templates en Django son una forma limpia, segura y controlada de renderizar HTML.
La view prepara datos y la template los muestra: así se logra mantenibilidad y
separación de responsabilidades en el proyecto.

</details>

<details>
<summary>26. ¿Cómo funciona la herencia de plantillas (extends, block)?</summary>

#### Django

La herencia de plantillas en Django permite crear un layout base y reutilizarlo
en páginas hijas. Esto elimina duplicación de HTML y hace más manejable la parte
frontend del proyecto.

#### Etiquetas clave:

1. **`{% extends "base.html" %}`**
- La plantilla hija hereda de la base.

2. **`{% block ... %}{% endblock %}`**
- En la plantilla base se definen "slots" que la hija puede rellenar.

#### Plantilla base:

```django
{# templates/base.html #}
<!doctype html>
<html lang="uk">
<head>
  <meta charset="utf-8">
  <title>{% block title %}Mi sitio{% endblock %}</title>
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

#### Plantilla hija:

```django
{# templates/articles/list.html #}
{% extends "base.html" %}

{% block title %}Lista de artículos{% endblock %}

{% block content %}
  <h1>Artículos</h1>
  <p>Contenido de la página...</p>
{% endblock %}
```

#### `block.super`:

Si necesitas complementar y no reemplazar por completo un bloque:

```django
{% block title %}{{ block.super }} | Artículos{% endblock %}
```

#### Recomendaciones prácticas:

1. Mantén un `base.html` principal (layout: head, header, footer, scripts).
2. Añade bloques separados para `title`, `content`, `extra_css`, `extra_js`.
3. No dupliques partes iguales en cada template; mueve a base/include.
4. Sé consistente con los nombres de bloques en todo el proyecto.

#### Errores típicos:

- Falta de estructura única de bloques entre páginas.
- Mover lógica de negocio a template en lugar de view/service.
- Duplicar código de layout sin `extends`.

#### Conclusión:

`extends` y `block` son la base de una arquitectura de plantillas escalable en Django:
una carcasa común del sitio, mínimo duplicado y cambios de UI más rápidos.

</details>

<details>
<summary>27. ¿Para qué se usa {% include %}?</summary>

#### Django

`{% include %}` se usa para insertar una plantilla dentro de otra. Es útil para
partes repetibles de interfaz: header, footer, tarjetas, tablas, paginación.

#### Para qué sirve `include`:

1. **Elimina duplicación de HTML**
- Un fragmento se reutiliza en muchas páginas.

2. **Mejora mantenibilidad**
- Cambios en el archivo partial se aplican automáticamente en todos los lugares.

3. **Simplifica la lectura de plantillas**
- Una plantilla grande se divide en bloques lógicos pequeños.

#### Ejemplo básico:

```django
{# templates/base.html #}
<body>
  {% include "partials/header.html" %}
  <main>{% block content %}{% endblock %}</main>
  {% include "partials/footer.html" %}
</body>
```

#### Pasar contexto a include:

```django
{% include "partials/user_badge.html" with user=request.user %}
```

Se puede limitar el contexto solo a las variables pasadas:

```django
{% include "partials/user_badge.html" with user=request.user only %}
```

#### Casos prácticos:

- Componente de paginación.
- Fila de tabla/tarjeta de producto.
- Bloque de alertas/mensajes.
- Elementos comunes de layout.

#### Diferencia entre `extends` e `include`:

- `extends` - herencia de estructura de plantilla (nivel layout).
- `include` - inserción de fragmento local (nivel componente).

#### Errores típicos:

1. Usar `include` en vez de `extends` para layout base.
2. Pasar un contexto implícito demasiado amplio.
3. Meter lógica pesada dentro de partials.

#### Conclusión:

`{% include %}` es una herramienta base para código template modular en Django.
Úsala para fragmentos pequeños reutilizables, y `extends` para estructura global de página.

</details>

<details>
<summary>28. ¿Qué son los template partials y cómo funcionan {% partial %} y {% partialdef %}?</summary>

#### Django

Template partials es una forma de definir y reutilizar fragmentos de plantilla
directamente dentro de archivos template. Para esto se usan las etiquetas
`{% partialdef %}` (declaración) y `{% partial %}` (invocación).

#### Cómo funciona:

1. **`{% partialdef name %}...{% endpartialdef %}`**
- Declara un fragmento parcial con nombre.

2. **`{% partial name %}`**
- Renderiza el parcial en el lugar requerido.

#### Ejemplo básico:

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

#### Diferencia con `{% include %}`:

- `include` conecta un archivo separado.
- `partial/partialdef` permite describir y llamar fragmento en el contexto
  de la plantilla actual sin crear archivo aparte.

#### Cuándo son especialmente útiles:

1. Cuando hay que reutilizar rápido un fragmento pequeño dentro de una sola plantilla.
2. Cuando importa evitar fragmentar en decenas de includes diminutos.
3. Para bloques UI locales que no tiene sentido mover a template separado.

#### Recomendaciones prácticas:

1. Para componentes globalmente reutilizables entre páginas, mantén
   `{% include %}` o partials en archivos separados.
2. Para fragmentos locales y pequeños, usa `partial/partialdef`.
3. No metas lógica de negocio en partials; solo capa de presentación.

#### Compatibilidad:

- En versiones modernas de Django, las etiquetas partial están disponibles como parte del sistema template.
- Si el proyecto está en una versión más antigua, la misma tarea suele resolverse con
  `{% include %}` y template tags personalizados.

#### Conclusión:

`{% partialdef %}` y `{% partial %}` son una herramienta de composición local
de plantillas: menos duplicación, mejor legibilidad y más control sobre estructura UI.

</details>

<details>
<summary>29. ¿Qué son template tags y filters?</summary>

#### Django

`Template tags` y `filters` son herramientas del motor de plantillas de Django para
renderizar datos de forma controlada.

#### Template tags:

- Las tags ejecutan lógica a nivel de plantilla.
- Se usan en formato `{% ... %}`.

Tags built-in típicas:

1. `{% if %}` / `{% elif %}` / `{% else %}` - render condicional.
2. `{% for %}` - iteración de colecciones.
3. `{% url %}` - construcción de enlace por nombre de ruta.
4. `{% include %}` - inserción de parte de plantilla.
5. `{% csrf_token %}` - protección CSRF en formularios.
6. `{% static %}` - enlace a archivos static.

Ejemplo:

```django
{% if user.is_authenticated %}
  <a href="{% url 'profile' %}">Perfil</a>
{% else %}
  <a href="{% url 'login' %}">Iniciar sesión</a>
{% endif %}
```

#### Filters:

- Los filtros transforman valores de variables.
- Se usan con `|` dentro de `{{ ... }}`.

Filters built-in típicos:

1. `|lower`, `|upper`, `|title`
2. `|length`
3. `|date:"d.m.Y"`
4. `|default:"-"`, `|default_if_none:"-"`
5. `|truncatechars:50`
6. `|safe` (con cuidado)

Ejemplo:

```django
<p>{{ article.title|title }}</p>
<p>{{ article.created_at|date:"d.m.Y H:i" }}</p>
<p>{{ article.description|truncatechars:120 }}</p>
```

#### Cómo crear un filter propio:

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

#### Cómo crear un simple tag propio:

```python
@register.simple_tag
def app_version():
    return "1.0.0"
```

```django
{% load text_extras %}
<small>v{% app_version %}</small>
```

#### Reglas prácticas:

1. Mantén plantillas "delgadas": mínima lógica, máxima legibilidad.
2. Mueve lógica de presentación repetida a filters/tags personalizados.
3. No muevas lógica de negocio a template tags.
4. Usa `|safe` solo para contenido verificado.

#### Conclusión:

Template tags controlan la estructura de render, y filters el formato de valores.
Juntos ofrecen una forma flexible y segura de construir UI en plantillas Django.

</details>

<details>
<summary>30. ¿Cómo conectar archivos estáticos (static) y qué hace collectstatic?</summary>

#### Django

Los archivos estáticos (`static`) son CSS, JS, imágenes, fuentes y otros recursos
que no se generan dinámicamente para cada solicitud.

#### Configuración base en `settings.py`:

```python
STATIC_URL = "/static/"
STATIC_ROOT = BASE_DIR / "staticfiles"   # para build de production
```

Si hacen falta directorios adicionales:

```python
STATICFILES_DIRS = [BASE_DIR / "static"]
```

#### Cómo conectar static en plantilla:

```django
{% load static %}
<link rel="stylesheet" href="{% static 'css/main.css' %}">
<script src="{% static 'js/app.js' %}"></script>
<img src="{% static 'img/logo.svg' %}" alt="Logo">
```

#### Dónde guardar static:

1. En cada app:
- `app_name/static/app_name/...`

2. O en carpeta compartida del proyecto:
- `project_root/static/...`

#### Qué hace `collectstatic`:

Comando:

```bash
python manage.py collectstatic
```

Resultado:

1. Reúne todos los archivos static de apps y `STATICFILES_DIRS`.
2. Los copia en una sola carpeta `STATIC_ROOT`.
3. Prepara el conjunto de archivos que sirve el webserver/CDN en production.

#### Dev vs Production:

1. **Desarrollo local (`DEBUG=True`)**
- Django puede servir static por sí mismo.

2. **Production (`DEBUG=False`)**
- Static normalmente lo sirve Nginx, CDN u object storage.
- El proceso Django no debería servir static directamente.

#### Prácticas production comunes:

- `ManifestStaticFilesStorage` para archivos versionados/hasheados (cache busting).
- WhiteNoise para deploy simple sin Nginx separado.
- CDN para entrega rápida de recursos estáticos.

#### Errores típicos:

1. No ejecutar `collectstatic` antes del deploy.
2. Hardcodear rutas `/static/...` sin `{% static %}`.
3. Confundir `static` (assets) con `media` (uploads de usuario).
4. No configurar `STATIC_ROOT` para production.

#### Conclusión:

La conexión de static en Django se basa en `{% static %}` y settings correctos.
`collectstatic` es un paso obligatorio del build de producción que unifica todos
los recursos estáticos para una entrega rápida y estable.

</details>

<details>
<summary>31. ¿Qué son MEDIA_ROOT y MEDIA_URL?</summary>

#### Django

`MEDIA_ROOT` y `MEDIA_URL` se usan para trabajar con archivos que suben los
usuarios (uploads): avatares, documentos, fotos, videos, etc.

#### Qué es `MEDIA_ROOT`:

- Ruta absoluta en el sistema de archivos del servidor donde se guardan físicamente los uploads.
- Es el "disco" donde Django escribe archivos de `FileField`/`ImageField`.

#### Qué es `MEDIA_URL`:

- Prefijo URL por el que esos archivos están disponibles desde el navegador.
- Es la "ruta pública" al contenido de `MEDIA_ROOT`.

#### Configuración básica:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Ejemplo de modelo:

```python
from django.db import models

class Profile(models.Model):
    avatar = models.ImageField(upload_to="avatars/")
```

Si el usuario sube el archivo `photo.jpg`, quedará en:

- Archivo en disco: `MEDIA_ROOT/avatars/photo.jpg`
- URL en navegador: `MEDIA_URL + "avatars/photo.jpg"` -> `/media/avatars/photo.jpg`

#### Configuración URL en development:

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

#### Enfoque production:

1. Django guarda el archivo (local o en cloud storage backend).
2. La entrega del archivo la hace Nginx/CDN/S3, no el proceso Django.
3. El acceso se controla con permisos o pre-signed URL (para archivos privados).

#### Diferencia importante entre `static` y `media`:

- `static` - archivos del desarrollador (CSS/JS/logo), se recogen con `collectstatic`.
- `media` - archivos de usuario, no pasan por `collectstatic`.

#### Errores típicos:

1. Mezclar `STATIC_ROOT` y `MEDIA_ROOT`.
2. Guardar uploads de usuario en el repositorio git.
3. Servir media desde Django en production sin necesidad.
4. No validar tipo/tamaño de archivos subidos.

#### Conclusión:

`MEDIA_ROOT` es dónde vive físicamente el archivo, `MEDIA_URL` es cómo lo solicita
el cliente. Separar claramente media/static es estándar obligatorio en proyectos Django.

</details>

<details>
<summary>32. ¿Qué enfoques existen para cachear plantillas?</summary>

#### Django

El caché de plantillas en Django reduce carga en CPU/BD y acelera las respuestas
al reutilizar contenido ya renderizado.

#### Enfoques principales:

1. **Template fragment caching (recomendado para partes de página)**
- Cachea solo un fragmento de plantilla, no toda la página.

```django
{% load cache %}
{% cache 300 sidebar user.id %}
  {# bloque pesado: menú, recomendaciones, widgets #}
  ...
{% endcache %}
```

2. **Per-view caching**
- Cachea la respuesta completa de una view durante un TTL definido.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)  # 5 min

def article_list(request):
    ...
```

3. **Site-wide caching (vía middleware)**
- Cachea casi todo el sitio con reglas globales.
- Adecuado para sitios de contenido con baja personalización.

4. **Low-level cache API**
- Caché de resultados de consultas/cálculos dentro de código Python.

```python
from django.core.cache import cache

data = cache.get("popular_articles")
if data is None:
    data = expensive_query()
    cache.set("popular_articles", data, 300)
```

#### Configuración del backend de caché:

En production normalmente se usa Redis o Memcached:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Cuándo elegir cada uno:

- Fragmentos UI con render costoso -> template fragment cache.
- Página pública estable -> per-view cache.
- Sitio mayormente estático -> site-wide cache.
- Lógica/consultas costosas -> low-level cache API.

#### Reglas prácticas:

1. Empieza por el caché menos agresivo (fragmentos), luego escala.
2. Ajusta TTL según requisitos de frescura de datos.
3. Para bloques personalizados, agrega claves (user id, locale, permisos).
4. Prevé invalidación de caché tras cambios de datos.

#### Errores típicos:

1. Cachear contenido personalizado sin clave de usuario.
2. No invalidar caché tras update/delete.
3. TTL demasiado largo para datos dinámicos.
4. Usar caché como "cura" de consultas SQL ineficientes.

#### Conclusión:

El inicio más seguro en Django es fragment caching + Redis. Después se añade
per-view o site-wide caché cuando lo justifica el perfil de carga y UX.

</details>

<details>
<summary>33. ¿Qué son Django Forms y ModelForm?</summary>

#### Django

`Django Forms` es el mecanismo para procesar formularios HTML: validación,
limpieza de datos, render de campos y manejo de errores.
`ModelForm` es un tipo especial de formulario que se construye automáticamente a
partir de un modelo Django.

#### Django Form:

- Se define con `forms.Form`.
- Los campos se describen manualmente.
- Sirve para formularios no ligados directamente a un modelo.

Ejemplo:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.CharField(widget=forms.Textarea)
```

#### ModelForm:

- Se define con `forms.ModelForm`.
- Los campos se generan desde el modelo.
- Guarda fácilmente en BD mediante `form.save()`.

Ejemplo:

```python
from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ["title", "content", "is_published"]
```

#### Diferencia principal:

1. **Origen de campos**
- Form: defines los campos manualmente.
- ModelForm: los campos vienen del modelo.

2. **Persistencia de datos**
- Form: manejo y guardado manual.
- ModelForm: `form.save()` "de fábrica".

3. **Escenario de uso**
- Form: contacto, búsqueda, filtros, login/reset, formularios de integración.
- ModelForm: CRUD de modelos, interfaces tipo admin.

#### Ejemplo de manejo en view:

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

#### Ventajas generales de Django Forms:

- Validación centralizada en servidor.
- Protección frente a tipos/entradas incorrectas.
- Manejo cómodo de mensajes de error.
- Integración simple con plantillas.

#### Conclusión:

Usa `Form` para escenarios personalizados sin modelo directo.
`ModelForm` es la vía más rápida y limpia para CRUD sobre modelos Django.

</details>

<details>
<summary>34. ¿Cuál es la diferencia entre formulario HTML y formulario Django?</summary>

#### Django

El formulario HTML y el formulario Django resuelven la misma tarea (entrada de
datos), pero en niveles distintos. El HTML form es solo marcado en navegador,
y el Django form es mecanismo server-side de validación y procesamiento.

#### Formulario HTML:

- Describe campos, botones, `method`, `action`.
- Funciona del lado cliente (navegador).
- No garantiza por sí solo seguridad ni corrección de datos en servidor.

Ejemplo:

```html
<form method="post" action="/contact/">
  <input type="text" name="name" />
  <input type="email" name="email" />
  <button type="submit">Enviar</button>
</form>
```

#### Formulario Django:

- Se define en Python (`forms.Form` o `forms.ModelForm`).
- Ejecuta validación server-side, limpieza (`cleaned_data`) y arma errores.
- Se integra fácilmente con plantillas y protección CSRF.

Ejemplo:

```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
```

#### Diferencias clave:

1. **Nivel**
- HTML form: presentation layer.
- Django form: backend validation layer.

2. **Validación**
- HTML: validación cliente básica (fácil de saltar).
- Django Form: validación server-side obligatoria y confiable.

3. **Seguridad**
- HTML por sí solo no protege contra requests falsificadas.
- Django form trabaja con `{% csrf_token %}` y manejo integrado de errores.

4. **Mantenibilidad**
- Enfoque HTML-only suele duplicar validaciones.
- Django form centraliza reglas y simplifica mantenimiento.

5. **Trabajo con modelos**
- HTML: guardado manual.
- ModelForm: `form.save()` "de fábrica".

#### Regla práctica:

En production no se puede confiar solo en validación HTML.
La validación cliente es para UX; Django form es para correctness y seguridad.

#### Conclusión:

El formulario HTML responde por la interfaz, Django form por calidad de datos y
fiabilidad server-side. En proyectos reales se usan juntos, pero la validación
crítica siempre debe estar en backend.

</details>

<details>
<summary>35. ¿Cómo renderizar formularios en plantilla?</summary>

#### Django

Los formularios en Django se renderizan en plantilla mediante el objeto `form`
que se pasa desde la view. Hay varios enfoques: render automático rápido o
render manual controlado.

#### 1. Render automático rápido:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Guardar</button>
</form>
```

Opciones disponibles:

- `{{ form.as_p }}` - campos envueltos en `<p>`
- `{{ form.as_ul }}` - campos como lista `<li>`
- `{{ form.as_table }}` - campos en formato tabla

#### 2. Render manual (recomendado para UI de production):

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

  <button type="submit">Guardar</button>
</form>
```

#### Qué es obligatorio agregar:

1. `{% csrf_token %}` para formularios POST.
2. Visualización de errores de campo (`field.errors`) y errores globales (`non_field_errors`).
3. `enctype="multipart/form-data"` para formularios con archivos.

#### Ejemplo para formulario de upload:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Subir</button>
</form>
```

#### Recomendaciones prácticas:

1. Para MVP se puede empezar con `form.as_p`.
2. Para producto real, mejor render manual para control total de UX/UI.
3. No ocultes errores de validación; muéstralos junto al campo.
4. Prioriza botones de acción nombrados y un submit-flow claro.

#### Conclusión:

El render de formularios en Django puede ser muy rápido o muy controlado. Para
calidad production normalmente se elige render manual con errores explícitos,
protección CSRF y maquetación controlada.

</details>

<details>
<summary>36. ¿Cómo funciona la validación de formularios y cómo crear la tuya?</summary>

#### Django

La validación de formularios en Django ocurre en el servidor al llamar `form.is_valid()`.
Como resultado, Django devuelve datos limpios (`cleaned_data`) o llena
`form.errors`.

#### Cómo funciona la validación paso a paso:

1. Django valida tipos y reglas básicas de campos (`required`, `max_length`,
   `EmailField`, `IntegerField`, etc.).
2. Llama validadores personalizados del campo (si existen).
3. Llama métodos `clean_<field>()` para campos concretos.
4. Llama `clean()` global para lógica entre campos.
5. Forma `cleaned_data` o lista de errores.

#### Validación de un campo (`clean_<field>()`):

```python
from django import forms
from django.core.exceptions import ValidationError

class RegisterForm(forms.Form):
    username = forms.CharField(max_length=50)

    def clean_username(self):
        value = self.cleaned_data["username"].strip()
        if "admin" in value.lower():
            raise ValidationError("El nombre de usuario contiene una palabra prohibida.")
        return value
```

#### Validación entre campos (`clean()`):

```python
class PasswordForm(forms.Form):
    password = forms.CharField(widget=forms.PasswordInput)
    confirm_password = forms.CharField(widget=forms.PasswordInput)

    def clean(self):
        cleaned_data = super().clean()
        p1 = cleaned_data.get("password")
        p2 = cleaned_data.get("confirm_password")

        if p1 and p2 and p1 != p2:
            raise forms.ValidationError("Las contraseñas no coinciden.")
        return cleaned_data
```

#### Validadores personalizados:

```python
from django.core.exceptions import ValidationError

def validate_company_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Solo se permite email corporativo.")
```

```python
email = forms.EmailField(validators=[validate_company_email])
```

#### Para `ModelForm`:

- Funciona validación del formulario + validación del modelo.
- En el modelo también puedes usar:
  `clean()`, `unique=True`, `UniqueConstraint`, `validators`.

#### Cómo manejar en view:

```python
def submit_form(request):
    form = RegisterForm(request.POST or None)
    if request.method == "POST" and form.is_valid():
        # trabajar con form.cleaned_data
        ...
    return render(request, "form.html", {"form": form})
```

#### Reglas prácticas:

1. La validación siempre debe existir en servidor (la de cliente es solo para UX).
2. Lógica local de campo -> `clean_<field>()`.
3. Lógica dependiente de varios campos -> `clean()`.
4. Reglas reutilizables -> validadores separados.
5. Reglas de negocio de nivel dominio duplícalas en BD (constraints), no solo en formulario.

#### Conclusión:

La fortaleza de Django Forms es la validación estructurada en varios niveles.
Esto da control de calidad de datos, errores claros para usuario y flujo backend
estable de formularios en production.

</details>

<details>
<summary>37. ¿Qué son los validadores personalizados en Django y cómo reutilizarlos?</summary>

#### Django

Los validadores personalizados en Django son funciones o clases que verifican un
valor de campo según tus reglas y lanzan `ValidationError` si los datos no pasan
la validación.

#### Para qué sirven:

1. **Reutilizar reglas**
- Una misma validación se aplica en muchas forms/models.

2. **Fuente única de verdad**
- La regla de negocio no se duplica por todo el código.

3. **Arquitectura más limpia**
- La lógica de validación sale de view/forms a una capa separada.

#### Ejemplo de validador funcional:

```python
from django.core.exceptions import ValidationError

def validate_corporate_email(value):
    if not value.endswith("@company.com"):
        raise ValidationError("Solo se permite email corporativo.")
```

Uso en modelo:

```python
from django.db import models
from .validators import validate_corporate_email

class Employee(models.Model):
    email = models.EmailField(validators=[validate_corporate_email])
```

Uso en formulario:

```python
from django import forms
from .validators import validate_corporate_email

class InviteForm(forms.Form):
    email = forms.EmailField(validators=[validate_corporate_email])
```

#### Ejemplo de validador class-based:

```python
from django.core.exceptions import ValidationError

class MinWordsValidator:
    def __init__(self, min_words=3):
        self.min_words = min_words

    def __call__(self, value):
        if len(value.split()) < self.min_words:
            raise ValidationError(f"Mínimo {self.min_words} palabra(s).")
```

```python
description = models.TextField(validators=[MinWordsValidator(5)])
```

#### Dónde colocarlos mejor:

- `app/validators.py` o `app/domain/validators.py`
- En proyectos grandes, módulos separados por dominios.

#### Reglas prácticas:

1. Cada validador debe hacer una sola comprobación concreta.
2. Los mensajes de error deben ser claros para el usuario.
3. Para reglas críticas, duplica control a nivel BD (`UniqueConstraint`, check constraints).
4. Escribe tests para validadores por separado de las views.

#### Conclusión:

Los validadores personalizados son la forma correcta de centralizar reglas de
validación de negocio en Django. Hacen el código más limpio, reutilizable y
reducen riesgo de desalineación de reglas en distintas partes del sistema.

</details>

<details>
<summary>38. ¿Cómo procesar subida de archivos?</summary>

#### Django

La subida de archivos en Django se procesa mediante `request.FILES`, campos
`FileField`/`ImageField` y configuración correcta de `MEDIA_ROOT`/`MEDIA_URL`.

#### Qué necesitas para uploads:

1. Campo de archivo en formulario o modelo.
2. `enctype="multipart/form-data"` en formulario HTML.
3. Pasar `request.FILES` al formulario.
4. Configurar media en `settings.py`.

#### Ejemplo de modelo:

```python
from django.db import models

class Document(models.Model):
    title = models.CharField(max_length=200)
    file = models.FileField(upload_to="documents/%Y/%m/")
```

#### Ejemplo de ModelForm:

```python
from django import forms
from .models import Document

class DocumentForm(forms.ModelForm):
    class Meta:
        model = Document
        fields = ["title", "file"]
```

#### Ejemplo de view:

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

#### Plantilla:

```django
<form method="post" enctype="multipart/form-data">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Subir</button>
</form>
```

#### Configuración media:

```python
# settings.py
MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"
```

#### Seguridad y prácticas production:

1. Valida tipo, tamaño y extensión de archivo.
2. No confíes en filename original del cliente.
3. Limita acceso a archivos privados con permisos.
4. En production usa storage externo (S3-compatible) o servidor de archivos separado.
5. Escanea archivos potencialmente peligrosos (si el caso de negocio lo requiere).

#### Errores típicos:

1. Olvidar `enctype="multipart/form-data"` -> `request.FILES` vacío.
2. Pasar solo `request.POST` sin `request.FILES`.
3. Mezclar static y media.
4. No validar tamaño/tipo y crear riesgo de seguridad o sobrecarga.

#### Conclusión:

En Django el upload funciona de forma fiable si se respetan reglas básicas:
formulario correcto, `request.FILES`, validadores y control de acceso a archivos
en production.

</details>

<details>
<summary>39. ¿Qué es Django ORM?</summary>

#### Django

Django ORM (Object-Relational Mapping) es la capa de acceso a datos que permite
trabajar con la base usando objetos Python en lugar de escribir SQL manual en la
mayoría de escenarios típicos.

#### Idea principal del ORM:

1. **Modelo Python = tabla BD**
2. **Instancia de modelo = fila de tabla**
3. **Campo de modelo = columna de tabla**
4. **QuerySet = consulta(s) SQL generadas por ORM**

#### Ejemplo:

```python
# models.py
class Article(models.Model):
    title = models.CharField(max_length=200)
    is_published = models.BooleanField(default=False)
    created_at = models.DateTimeField(auto_now_add=True)
```

```python
# crear
Article.objects.create(title="Django ORM", is_published=True)

# leer
articles = Article.objects.filter(is_published=True).order_by("-created_at")

# actualizar
article = Article.objects.get(pk=1)
article.title = "Updated title"
article.save()

# eliminar
article.delete()
```

#### Ventajas de Django ORM:

1. **Desarrollo rápido** - menos boilerplate SQL.
2. **Código legible** - consultas declarativas.
3. **Seguridad** - parametrización reduce riesgo de SQL injection.
4. **Portabilidad** - mismo código funciona con distintas BD (en gran parte).
5. **Integración Django** - forms, admin, migrations, validators.

#### Conceptos importantes:

- `QuerySet` es lazy: la consulta corre solo cuando se necesitan datos.
- `select_related` y `prefetch_related` ayudan a evitar N+1.
- `annotate`, `aggregate`, `F`, `Q`, `Subquery` para consultas más complejas.

#### Limitaciones del ORM:

1. Construcciones SQL muy complejas a veces son más simples en raw SQL.
2. Sin profiling es fácil obtener consultas ineficientes.
3. Mal uso de relaciones puede impactar fuerte el rendimiento.

#### Cuándo usar raw SQL:

- Optimizaciones específicas para una BD concreta.
- Analítica compleja/CTE/window functions donde ORM se vuelve ilegible.
- Tareas de migración/operación que requieren control SQL exacto.

#### Conclusión:

Django ORM es una de las mayores ventajas del framework: rápido, seguro y cómodo
para la mayoría de casos de negocio. Pero en production hay que entender qué SQL
genera y optimizar consultas a tiempo.

</details>

<details>
<summary>40. ¿Qué es un modelo y cómo crearlo?</summary>

#### Django

Un modelo (`Model`) en Django es una clase Python que describe la estructura de
datos y corresponde a una tabla en base de datos. A través del modelo defines
campos, relaciones y reglas a nivel de datos.

#### Qué es un modelo:

1. **Descripción del esquema BD en Python**
- Campos del modelo (`CharField`, `IntegerField`, `DateTimeField`...) corresponden
  a columnas de tabla.

2. **Capa de entidades de dominio**
- El modelo representa un objeto de negocio: `User`, `Order`, `Invoice`, `Product`.

3. **Integración con ORM**
- Crear, leer, actualizar y eliminar registros vía `Model.objects`.

#### Ejemplo de modelo:

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

#### Cómo crear un modelo paso a paso:

1. Añade la clase en `app/models.py`.
2. Asegúrate de que la app está en `INSTALLED_APPS`.
3. Crea migración:

```bash
python manage.py makemigrations
```

4. Aplica migración a BD:

```bash
python manage.py migrate
```

#### Prácticas básicas:

1. Usa nombres de campo claros y restricciones (`unique`, `db_index`).
2. Añade campos de servicio `created_at`, `updated_at`.
3. Define `__str__` para legibilidad en admin y shell.
4. Fija invariantes de dominio importantes en BD (constraints), no solo en view/forms.

#### Errores típicos:

1. Guardar "todo como text" ignorando tipos de datos.
2. Falta de índices en campos de filtrado/búsqueda.
3. Mezclar lógica de negocio de alto nivel directamente en modelo sin estructura.
4. Migraciones tardías que divergen entre entornos.

#### Conclusión:

El modelo en Django es la base del trabajo con datos. Modelos bien diseñados
marcan rendimiento, fiabilidad y escalabilidad de todo el proyecto.

</details>

<details>
<summary>41. ¿Qué son ForeignKey, OneToOneField y ManyToManyField?</summary>

#### Django

`ForeignKey`, `OneToOneField` y `ManyToManyField` son tipos de relaciones entre
modelos en Django ORM. Definen cómo las entidades se vinculan entre sí en la BD.

#### 1. ForeignKey (uno-a-muchos, 1:N)

- Un objeto "padre" puede tener muchos "hijos".
- Cada registro hijo apunta solo a un padre.

Ejemplo:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Caso: un autor -> muchos libros.

#### 2. OneToOneField (uno-a-uno, 1:1)

- A cada registro del modelo A le corresponde como máximo un registro del modelo B.
- En esencia es `ForeignKey(unique=True)` con semántica más clara.

Ejemplo:

```python
from django.conf import settings

class Profile(models.Model):
    user = models.OneToOneField(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    bio = models.TextField(blank=True)
```

Caso: un usuario -> un perfil.

#### 3. ManyToManyField (muchos-a-muchos, M:N)

- Registros de ambas tablas pueden tener muchas relaciones entre sí.
- Django crea una tabla intermedia automáticamente (o vía `through=`).

Ejemplo:

```python
class Tag(models.Model):
    name = models.CharField(max_length=50, unique=True)

class Article(models.Model):
    title = models.CharField(max_length=200)
    tags = models.ManyToManyField(Tag, related_name="articles")
```

Caso: un artículo tiene muchas etiquetas, y una etiqueta pertenece a muchos artículos.

#### Cómo elegir el tipo de relación:

1. `ForeignKey` - cuando hay un "propietario" claro y múltiples registros hijos.
2. `OneToOneField` - cuando la entidad de extensión debe existir en una sola instancia.
3. `ManyToManyField` - cuando ambos lados pueden tener múltiples correspondencias.

#### Matiz de `on_delete` para ForeignKey/OneToOne:

- `CASCADE` - borra hijos junto al padre.
- `PROTECT` - prohíbe borrar si hay dependencias.
- `SET_NULL` - pone referencia en null (el campo debe ser `null=True`).

#### Conclusión:

Estos tres campos son la base para modelar datos relacionales en Django. Elegir
bien el tipo de relación simplifica consultas, migraciones y mantenimiento de la
arquitectura de dominio a largo plazo.

</details>

<details>
<summary>42. ¿Qué tipos de herencia de modelos existen?</summary>

#### Django

En Django hay tres tipos principales de herencia de modelos: **Abstract Base Classes**,
**Multi-table inheritance** y **Proxy models**. Resuelven problemas distintos y
tienen impacto diferente en el esquema de BD.

#### 1. Abstract Base Class (herencia abstracta)

- El modelo padre no crea su propia tabla en BD.
- Sus campos se copian en los modelos hijos.

Ejemplo:

```python
class TimeStampedModel(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    class Meta:
        abstract = True

class Article(TimeStampedModel):
    title = models.CharField(max_length=200)
```

Cuándo usar:

- Para campos/métodos comunes entre muchos modelos.
- Es la variante más frecuente y práctica en production.

#### 2. Multi-table inheritance (herencia con tablas separadas)

- Cada modelo en la cadena de herencia tiene tabla propia.
- Django crea relación `OneToOne` entre padre e hijo.

Ejemplo:

```python
class Person(models.Model):
    name = models.CharField(max_length=120)

class Employee(Person):
    salary = models.DecimalField(max_digits=10, decimal_places=2)
```

Cuándo usar:

- Cuando necesitas jerarquía real de entidades en BD.
- Cuando importa tener tablas separadas para modelo base y especializado.

Desventaja:

- JOINs extra y consultas más complejas.

#### 3. Proxy model (modelo proxy)

- No crea tabla nueva.
- Trabaja con la misma tabla del modelo base.
- Permite cambiar comportamiento Python (métodos, manager, ordering) sin cambiar la BD.

Ejemplo:

```python
class Order(models.Model):
    status = models.CharField(max_length=20)

class OpenOrder(Order):
    class Meta:
        proxy = True
        ordering = ["id"]
```

Cuándo usar:

- Necesitas manager/comportamiento distinto para el mismo modelo.
- Necesitas representación diferente en Django Admin sin cambiar estructura de tablas.

#### Selección rápida:

1. Campos comunes sin tabla separada -> **abstract**.
2. Jerarquía real con tablas separadas -> **multi-table**.
3. Comportamiento Python distinto sin cambio de BD -> **proxy**.

#### Consejo práctico:

Por defecto elige **abstract base class**.
Usa `multi-table` con cuidado, solo cuando lo exige el dominio y no "por estética".

#### Conclusión:

El tipo de herencia se elige según objetivo: reutilización de campos,
jerarquía física de tablas o solo cambio de comportamiento. Elegir bien simplifica
esquema BD y mantenimiento futuro.

</details>

<details>
<summary>43. ¿Para qué se usa la clase Meta?</summary>

#### Django

La clase interna `Meta` en un modelo Django se usa para configurar comportamiento
del modelo a nivel ORM y BD sin cambiar la lógica de negocio del modelo.

#### Qué se suele definir en `Meta`:

1. **`ordering`** - orden por defecto.
2. **`db_table`** - nombre de tabla custom en BD.
3. **`verbose_name`, `verbose_name_plural`** - nombres legibles en admin.
4. **`indexes`** - índices para rendimiento.
5. **`constraints`** - restricciones de negocio en BD.
6. **`unique_together` / `UniqueConstraint`** - unicidad de combinaciones de campos.
7. **`abstract` / `proxy`** - tipo de herencia del modelo.

#### Ejemplo:

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
        verbose_name = "Producto"
        verbose_name_plural = "Productos"
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

#### Por qué `Meta` es importante:

1. **Rendimiento**
- Índices y restricciones correctas reducen costo de consultas.

2. **Integridad de datos**
- Constraints protegen de registros inválidos incluso si falta validación en view/form.

3. **Control del esquema**
- Control explícito de tablas y reglas en migraciones.

4. **Comodidad en admin**
- Nombres humanos en back-office.

#### Recomendaciones prácticas:

1. Usa `UniqueConstraint` en lugar de `unique_together` obsoleto.
2. Añade índices solo en campos realmente "calientes" para filtro/orden.
3. Mantén reglas críticas de negocio en BD vía `constraints`.
4. No abuses de `db_table` si no hace falta naming explícito.

#### Conclusión:

`Meta` es el centro de configuración ORM del modelo. Desde ahí controlas orden,
índices, restricciones y calidad del esquema BD, lo que impacta directamente
fiabilidad y rendimiento del proyecto Django.

</details>

<details>
<summary>44. ¿Cuál es la diferencia entre null=True y blank=True?</summary>

#### Django

`null=True` y `blank=True` resuelven tareas distintas y operan en capas distintas:

- `null=True` - capa **base de datos** (si puede guardar `NULL`).
- `blank=True` - capa **validación de forms/admin** (si el campo puede ir vacío).

#### `null=True`:

1. Permite guardar `NULL` en la columna BD.
2. Afecta esquema de tabla y migraciones.
3. Es crítico para campos donde "sin valor" debe guardarse como SQL `NULL`.

#### `blank=True`:

1. Permite no completar el campo en forms, ModelForm, Django Admin.
2. No cambia directamente el tipo de columna en BD.
3. Afecta `form.is_valid()`, no la capa SQL.

#### Ejemplos:

```python
class Profile(models.Model):
    bio = models.TextField(blank=True)  # opcional en formulario
    birth_date = models.DateField(null=True, blank=True)  # NULL en BD y vacío en formulario
```

#### Matiz importante para strings (`CharField`, `TextField`):

- En Django normalmente **no se usa `null=True`** para campos string.
- Práctica recomendada: usar cadena vacía `""` en lugar de `NULL`.
- Es decir, usualmente:
  `CharField(..., blank=True)` sin `null=True`.

#### Matriz rápida:

1. `null=False, blank=False` -> obligatorio en BD y en formularios.
2. `null=True, blank=False` -> BD permite `NULL`, pero formulario exige valor.
3. `null=False, blank=True` -> formulario permite vacío, en BD no es `NULL` (a menudo `""`).
4. `null=True, blank=True` -> campo totalmente opcional (form y BD).

#### Recomendaciones prácticas:

1. Para `DateField`, `DateTimeField`, `ForeignKey` y campos numéricos suele
   hacer falta `null=True, blank=True`.
2. Para `CharField/TextField` normalmente basta `blank=True`.
3. Mantén política consistente en el proyecto para evitar caos entre `NULL` y `""`.
4. Recuerda: mala elección complica filtrado y analítica.

#### Conclusión:

`null` controla almacenamiento en BD, `blank` controla validación en forms Django.
Son ejes distintos de comportamiento y deben configurarse según el dominio.

</details>

<details>
<summary>45. ¿Cuál es la diferencia entre CharField y TextField?</summary>

#### Django

`CharField` y `TextField` guardan texto, pero tienen escenarios de uso y
restricciones distintas a nivel modelo/BD.

#### `CharField`:

1. Diseñado para texto corto/medio.
2. **Siempre** requiere `max_length`.
3. Encaja para campos con longitud controlada:
   nombre, slug, title, código, email, phone.

Ejemplo:

```python
title = models.CharField(max_length=200)
sku = models.CharField(max_length=64, unique=True)
```

#### `TextField`:

1. Diseñado para texto largo libre.
2. No requiere `max_length` a nivel modelo (se puede validar aparte).
3. Encaja para descripciones, contenido de artículos, notas, comentarios.

Ejemplo:

```python
description = models.TextField(blank=True)
content = models.TextField()
```

#### Diferencias clave:

1. **Límite de longitud**
- `CharField`: siempre `max_length`.
- `TextField`: sin límite rígido por defecto.

2. **Semántica de datos**
- `CharField`: texto corto estructurado.
- `TextField`: texto grande no estructurado.

3. **Forms/admin**
- `CharField` suele renderizarse como `input`.
- `TextField` suele renderizarse como `textarea`.

4. **Indexación y rendimiento**
- Campos cortos indexados suelen vivir mejor en `CharField`.
- Para textos grandes, indexación depende de la BD y suele requerir
  estrategias aparte (full-text search).

#### Reglas prácticas de tech lead:

1. Si el valor tiene límite natural de longitud -> `CharField`.
2. Si el texto es potencialmente grande/libre -> `TextField`.
3. No uses `TextField` "por si acaso" cuando `CharField` basta.
4. Para búsqueda en textos grandes, planifica estrategia de search (PostgreSQL FTS,
   Elasticsearch/OpenSearch, etc.).

#### Conclusión:

`CharField` es texto corto controlado, `TextField` es contenido largo.
Elegir bien afecta validación, UX de formularios, indexación y rendimiento de consultas.

</details>

<details>
<summary>46. ¿Qué son los model managers y cómo crear uno propio?</summary>

#### Django

Un `Model Manager` en Django es el "punto de entrada" para consultas al modelo
vía ORM. Por defecto cada modelo tiene el manager `objects`, pero puedes crear
managers propios con métodos de dominio.

#### Para qué sirven managers propios:

1. **Centralizar lógica de consultas**
- Para no duplicar `filter(...)` iguales en distintas views/servicios.

2. **API legible para el modelo**
- Por ejemplo: `Article.objects.published().recent()`.

3. **Control del conjunto "por defecto"**
- Por ejemplo, ocultar registros soft-deleted.

#### Ejemplo básico de manager:

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

Uso:

```python
Article.objects.published()
Article.objects.recent()
```

#### Combinación Manager + QuerySet (mejor escalabilidad):

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

#### Recomendaciones prácticas:

1. Pon en manager/queryset solo lógica de selección de datos.
2. Deja la orquestación de negocio en capa de servicios.
3. Usa nombres de método de dominio (`active`, `paid`, `for_user`).
4. No hagas manager "mágico": el comportamiento debe ser evidente.

#### Errores típicos:

1. Duplicar filtros iguales por todo el código.
2. Mezclar lógica de negocio pesada en manager.
3. Sobrescribir default manager y romper comportamientos de admin/migraciones.

#### Conclusión:

Model managers es el lugar correcto para consultas ORM reutilizables.
Un manager propio limpia el código y vuelve consistentes las consultas del proyecto.

</details>

<details>
<summary>47. ¿Qué son las migraciones y para qué sirven?</summary>

#### Django

Las migraciones en Django son un historial controlado de cambios del esquema de BD
que se guarda en el código del proyecto y se aplica con `makemigrations` y
`migrate`.

#### Qué aportan las migraciones:

1. **Versionado de BD**
- Cambios de tablas, campos, índices y constraints quedan fijados como archivos-instrucción.

2. **Reproducibilidad de entornos**
- Dev, staging y production reciben el mismo esquema de BD.

3. **Evolución segura del esquema**
- En lugar de SQL manual en notas, el equipo usa un proceso formalizado.

4. **Trabajo en equipo**
- Las migraciones se commitean en git y pasan code review junto con el código.

#### Cómo funciona:

1. Cambias modelo en `models.py`.
2. `python manage.py makemigrations` genera archivo de migración.
3. `python manage.py migrate` aplica cambios en BD.
4. Django registra estado en tabla de servicio `django_migrations`.

#### Ejemplos de cambios típicos vía migraciones:

- Añadir/eliminar campo.
- Cambiar tipo de campo.
- Crear índice.
- Añadir `UniqueConstraint` o `CheckConstraint`.
- Renombrar modelo/campo.

#### Data migrations:

Además de estructura, puedes hacer migraciones de datos (`RunPython`), por ejemplo:
- rellenar campo nuevo,
- mover datos entre columnas,
- normalizar registros existentes.

#### Reglas prácticas:

1. Commitea migraciones junto con cambios de modelos.
2. No edites migraciones antiguas si ya se aplicaron en entornos compartidos.
3. Prueba migraciones en staging antes de production.
4. Para tablas grandes, planifica rollout backward-compatible (expand/contract).

#### Errores típicos:

1. Ejecutar código sin migraciones actualizadas.
2. Olvidar commitear archivos de migración.
3. Hacer operaciones bloqueantes peligrosas en tablas grandes sin plan.
4. Editar migraciones aplicadas y romper historial de esquema.

#### Conclusión:

Las migraciones son el "control de versiones" de la BD en Django. Son críticas
para deploy fiable, trabajo en equipo y evolución predecible de datos.

</details>

<details>
<summary>48. ¿Cuál es la diferencia entre makemigrations y migrate?</summary>

#### Django

`makemigrations` y `migrate` son dos fases distintas del flujo de migraciones:

- `makemigrations` **crea** archivos de migración (plan de cambios).
- `migrate` **aplica** esos cambios a la base de datos.

#### `makemigrations`:

1. Analiza cambios en `models.py`.
2. Genera archivos Python de migración en `app/migrations/`.
3. No cambia la BD directamente.

Comando:

```bash
python manage.py makemigrations
```

#### `migrate`:

1. Lee archivos de migración.
2. Ejecuta operaciones SQL en BD (CREATE/ALTER/DROP, etc.).
3. Marca migraciones aplicadas en tabla `django_migrations`.

Comando:

```bash
python manage.py migrate
```

#### Workflow simple:

1. Cambias modelos.
2. Ejecutas `makemigrations`.
3. Revisas migración generada.
4. Ejecutas `migrate`.
5. Commit de código + archivos de migración.

#### Analogía:

- `makemigrations` = "escribir la instrucción".
- `migrate` = "ejecutar la instrucción".

#### Comandos útiles:

```bash
python manage.py showmigrations
python manage.py sqlmigrate app_name 0001
```

- `showmigrations` muestra qué migraciones están aplicadas.
- `sqlmigrate` muestra SQL que se ejecutará.

#### Errores típicos:

1. Ejecutar `migrate` sin crear migraciones tras cambiar modelos.
2. Hacer `makemigrations` y no commitear archivos.
3. Confundir estado local de BD con staging/production.
4. Ignorar conflictos de migraciones en desarrollo en equipo.

#### Conclusión:

`makemigrations` prepara cambios, `migrate` los aplica. Para un deploy estable
hacen falta ambos pasos, en orden y bajo control.

</details>

<details>
<summary>49. ¿Cómo conectar PostgreSQL u otra BD?</summary>

#### Django

La conexión de BD en Django se configura en `DATABASES` dentro de `settings.py`.
En production se usa más PostgreSQL; con menos frecuencia MySQL/MariaDB.

#### 1. Instala driver de BD

Para PostgreSQL (opción moderna recomendada):

```bash
pip install psycopg[binary]
```

Alternativa: `psycopg2-binary`.

#### 2. Configura `DATABASES` en `settings.py`

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

#### 3. Ejecuta migraciones

```bash
python manage.py migrate
```

#### Conexión vía variables de entorno (recomendado):

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

#### Otros engines soportados:

1. SQLite (por defecto para local/prototipos)
2. PostgreSQL (opción principal para production)
3. MySQL / MariaDB
4. Oracle

#### Recomendaciones production:

1. No guardes passwords de BD en repositorio.
2. Activa SSL hacia BD (cuando aplique).
3. Configura pooling de conexiones (PgBouncer o parámetros DB-side).
4. Añade health-check y monitoreo de latency/locks/slow queries.
5. Usa roles de acceso separadas (least privilege).

#### Errores típicos:

1. `ENGINE` incorrecto o driver ausente.
2. Funciona local y falla en CI/prod por variables de entorno.
3. Usar SQLite en production bajo carga concurrente.
4. No configurar timeouts/pooling bajo carga.

#### Conclusión:

Para conectar PostgreSQL en Django necesitas tres pasos: driver, `DATABASES`,
migraciones. En production son críticos: env config, credenciales seguras, SSL y
control de rendimiento de conexiones.

</details>

<details>
<summary>50. ¿Qué es QuerySet? ¿Qué es evaluación lazy?</summary>

#### Django

`QuerySet` en Django ORM es un objeto que representa un conjunto de registros de
BD y una cadena de operaciones sobre ellos (`filter`, `exclude`, `order_by`,
`annotate`, etc.).

#### Qué es clave entender sobre QuerySet:

1. Es **lazy** por defecto.
2. Construir QuerySet no ejecuta SQL de inmediato.
3. SQL se ejecuta solo cuando los datos realmente se necesitan.

#### Ejemplo de lazy:

```python
qs = Article.objects.filter(is_published=True).order_by("-created_at")
# En este punto la consulta a BD todavía NO se ejecutó
```

#### Cuándo QuerySet se materializa (ejecuta SQL):

1. Iteración:

```python
for article in qs:
    ...
```

2. Conversión a lista:

```python
items = list(qs)
```

3. Obtener longitud/valor booleano:

```python
len(qs)
bool(qs)
```

4. Llamadas como:
- `first()`, `last()`, `exists()`, `count()`, `get()`
- slicing (a menudo con `LIMIT/OFFSET`), por ejemplo `qs[:10]`

#### Ventajas de lazy evaluation:

1. **Optimización de consultas**
- Puedes construir queryset complejo por pasos antes de ejecutar.

2. **Flexibilidad**
- Un queryset base se reutiliza con condiciones distintas.

3. **Menos llamadas innecesarias a BD**
- Si no se usa el queryset, la consulta no corre.

#### Errores típicos:

1. Llamar querysets en bucles y obtener N+1 consultas.
2. Iterar varias veces el mismo queryset sin cachear resultado.
3. Confundir `count()` con `len(qs)` (coste/comportamiento pueden diferir).

#### Consejos prácticos:

1. Para relaciones usa `select_related()` / `prefetch_related()`.
2. Si el resultado se usa muchas veces en un mismo flow, materializa:
   `items = list(qs)`.
3. Para verificar existencia usa `exists()`, no iteración completa.
4. Perfila SQL (Django Debug Toolbar, logs BD), no te fíes solo de intuición.

#### Conclusión:

`QuerySet` es la abstracción central del ORM de Django, y lazy evaluation su
optimización clave. Entender cuándo se ejecuta SQL es crítico para rendimiento
en proyectos Django reales.

</details>

<details>
<summary>51. ¿Cómo funcionan filter(), exclude() y get()?</summary>

#### Django

`filter()`, `exclude()` y `get()` son métodos base de Django ORM para consultar
datos. Su sintaxis es parecida, pero su comportamiento y garantías son distintas.

#### `filter()`:

- Devuelve un `QuerySet` con todos los registros que cumplen la condición.
- Si no hay coincidencias, devuelve `QuerySet` vacío (sin excepción).

```python
active_users = User.objects.filter(is_active=True)
cheap_products = Product.objects.filter(price__lt=1000)
```

#### `exclude()`:

- Devuelve un `QuerySet` con registros que **no** cumplen la condición.

```python
non_archived = Article.objects.exclude(status="archived")
```

#### `get()`:

- Devuelve **un** objeto del modelo.
- Espera exactamente una coincidencia.
- Si hay 0 o >1 resultados, lanza excepción.

```python
user = User.objects.get(pk=1)
```

#### Excepciones de `get()`:

1. `Model.DoesNotExist` - no se encontró nada.
2. `Model.MultipleObjectsReturned` - se encontró más de un registro.

Ejemplo de manejo seguro:

```python
from django.http import Http404

def profile_view(request, user_id):
    try:
        user = User.objects.get(pk=user_id)
    except User.DoesNotExist:
        raise Http404("Usuario no encontrado")
```

O más corto:

```python
from django.shortcuts import get_object_or_404
user = get_object_or_404(User, pk=user_id)
```

#### Cuándo usar cada uno:

1. **`filter()`** - cuando puede haber muchos o cero resultados.
2. **`exclude()`** - cuando hay que filtrar fuera parte del conjunto.
3. **`get()`** - cuando garantizas resultado único (PK, campo unique).

#### Consejos prácticos:

1. No uses `get()` donde la unicidad no está garantizada.
2. Para comprobar existencia usa `exists()`, no `get()+try/except`.
3. Combina condiciones con `Q` para lógica compleja.

#### Conclusión:

`filter()` y `exclude()` trabajan con conjuntos vía QuerySet; `get()` con un
objeto único y requisitos estrictos de unicidad. Elegir bien reduce errores y
simplifica casos límite.

</details>

<details>
<summary>52. ¿Diferencia entre get() y filter()?</summary>

#### Django

`get()` y `filter()` buscan datos en ORM, pero su semántica es distinta: uno
retorna **un objeto**, el otro **un conjunto (QuerySet)**.

#### `get()`:

1. Devuelve una instancia de modelo.
2. Espera exactamente una coincidencia.
3. Lanza excepciones si hay 0 o más de 1.

```python
user = User.objects.get(pk=10)
```

Excepciones posibles:

- `User.DoesNotExist`
- `User.MultipleObjectsReturned`

#### `filter()`:

1. Devuelve `QuerySet`.
2. Puede devolver 0, 1 o muchos registros.
3. No lanza excepción si no encuentra nada.

```python
users = User.objects.filter(is_active=True)
```

#### Diferencias clave:

1. **Tipo de resultado**
- `get()` -> un objeto.
- `filter()` -> QuerySet.

2. **Comportamiento sin datos**
- `get()` -> excepción.
- `filter()` -> QuerySet vacío.

3. **Escenario de uso**
- `get()` -> campos únicos (`id`, `uuid`, `email` con `unique=True`).
- `filter()` -> búsqueda por condiciones donde puede haber muchos matches.

#### Ejemplo práctico:

```python
# correcto: búsqueda única
order = Order.objects.get(id=order_id)

# correcto: lista de pedidos del usuario
orders = Order.objects.filter(user=request.user).order_by("-created_at")
```

#### Errores típicos:

1. Usar `get()` sobre campo no único (riesgo de `MultipleObjectsReturned`).
2. Esperar un objeto de `filter()` y olvidar `.first()` o `get()`.
3. No manejar excepciones de `get()` en API/view.

#### Conclusión:

`get()` es para un registro único puntual; `filter()` para colecciones y
búsqueda flexible. Si dudas sobre cardinalidad, empieza con `filter()`.

</details>

<details>
<summary>53. ¿Cómo obtener todos los registros o un solo registro?</summary>

#### Django

En Django ORM hay distintos métodos para obtener todos los registros o uno solo.
La elección depende de si esperas colección o resultado único.

#### Obtener todos los registros:

1. **Todos los registros del modelo**

```python
articles = Article.objects.all()
```

2. **Todos los registros por condición**

```python
articles = Article.objects.filter(is_published=True)
```

3. **Selección optimizada de campos concretos**

```python
articles = Article.objects.values("id", "title")
```

#### Obtener un registro:

1. **Registro único estricto con `get()`**

```python
article = Article.objects.get(pk=article_id)
```

Sirve cuando la unicidad está garantizada.

2. **Variante segura en web-view**

```python
from django.shortcuts import get_object_or_404

article = get_object_or_404(Article, pk=article_id)
```

3. **Primer registro del queryset**

```python
article = Article.objects.filter(is_published=True).first()
```

Devuelve objeto o `None`, sin excepciones.

#### Cuándo usar cada uno:

1. Colección para listas/tablas -> `all()` / `filter()`.
2. Registro único -> `get()`.
3. Registro único con 404 en web-flow -> `get_object_or_404()`.
4. Resultado opcional único -> `first()`.

#### Errores típicos:

1. Usar `get()` con campo no único.
2. Traer `all()` sin filtros/paginación en tablas grandes.
3. No manejar `DoesNotExist` en API/view.

#### Conclusión:

Para "todos los registros" usa QuerySet (`all/filter`); para "uno" usa `get()`
o envolturas seguras (`get_object_or_404`, `first()`) según UX y manejo de error.

</details>

<details>
<summary>54. ¿Diferencia entre select_related() y prefetch_related()?</summary>

#### Django

`select_related()` y `prefetch_related()` se usan para optimizar ORM y evitar
N+1 queries al trabajar con modelos relacionados.

#### `select_related()`:

1. Funciona para relaciones **ForeignKey** y **OneToOne** (lado "uno").
2. Hace **SQL JOIN** y trae datos relacionados en una sola query.
3. Es eficiente para relaciones "single-valued".

Ejemplo:

```python
orders = Order.objects.select_related("customer").all()
for order in orders:
    print(order.customer.email)  # sin queries adicionales
```

#### `prefetch_related()`:

1. Funciona para **ManyToMany**, reverse ForeignKey y también puede en FK/O2O.
2. Hace varias queries (principal + adicionales) y luego une resultados en Python.
3. Es eficiente para relaciones "multi-valued".

Ejemplo:

```python
articles = Article.objects.prefetch_related("tags").all()
for article in articles:
    print([tag.name for tag in article.tags.all()])  # sin N+1
```

#### Diferencia clave:

1. **Mecanismo**
- `select_related()` -> JOIN en un SQL.
- `prefetch_related()` -> varios SQL + merge en Python.

2. **Tipo de relaciones**
- `select_related()` -> FK/O2O.
- `prefetch_related()` -> M2M, reverse FK (y otros si conviene).

3. **Volumen de datos**
- `select_related()` puede inflar fila por JOINs.
- `prefetch_related()` suele ser mejor para colecciones hijas.

#### Uso combinado:

```python
orders = (
    Order.objects
    .select_related("customer")
    .prefetch_related("items", "items__product")
)
```

#### Regla práctica de elección:

1. Necesitas campo en FK/O2O -> empieza con `select_related`.
2. Necesitas lista de relacionados (M2M/reverse) -> `prefetch_related`.
3. Perfila queries (debug toolbar/logs), no adivines.

#### Errores típicos:

1. No usar ninguno y sufrir N+1.
2. Aplicar `select_related()` a M2M (no resuelve).
3. Llamar `.all()` de related manager en bucle sin prefetch.

#### Conclusión:

`select_related()` optimiza relaciones "únicas" por JOIN;
`prefetch_related()` optimiza relaciones de "colección" con queries extra.
La combinación correcta da mayor mejora de rendimiento ORM.

</details>

<details>
<summary>55. ¿Cómo optimizar consultas ORM (annotate, aggregate, F(), Q())?</summary>

#### Django

Optimizar consultas ORM en Django se basa en mover cómputo pesado a BD y reducir
cantidad de queries y volumen de datos leídos.

#### 1. `annotate()` - cálculo por cada fila

- Añade campo "virtual" a cada objeto del queryset.
- Útil para contadores, sumas, fechas de última actividad, etc.

```python
from django.db.models import Count

authors = Author.objects.annotate(books_count=Count("books"))
```

#### 2. `aggregate()` - resumen sobre todo el queryset

- Devuelve diccionario con valores agregados.

```python
from django.db.models import Avg, Sum

stats = Order.objects.aggregate(
    total_revenue=Sum("amount"),
    avg_revenue=Avg("amount"),
)
```

#### 3. `F()` - operaciones entre campos en BD

- Permite actualizar sin leer objeto en Python.
- Reduce race conditions en updates concurrentes.

```python
from django.db.models import F

Product.objects.filter(pk=product_id).update(stock=F("stock") - 1)
```

#### 4. `Q()` - lógica compleja de condiciones (`AND/OR/NOT`)

- Cuando un `filter(a=..., b=...)` simple no alcanza.

```python
from django.db.models import Q

users = User.objects.filter(
    Q(is_active=True) & (Q(role="admin") | Q(role="manager"))
).exclude(Q(email__isnull=True) | Q(email=""))
```

#### Ejemplo combinado:

```python
from django.db.models import Count, Q

articles = (
    Article.objects
    .filter(is_published=True)
    .annotate(comments_count=Count("comments", filter=Q(comments__is_approved=True)))
    .order_by("-comments_count")
)
```

#### Reglas prácticas de optimización:

1. Calcula en BD (`annotate/aggregate`), no con bucles Python.
2. Para updates masivos usa `update(..., F(...))`.
3. Para condiciones complejas usa `Q`, no varias queries.
4. Combina con `select_related/prefetch_related` para evitar N+1.
5. Trae solo campos necesarios (`only`, `values`, `values_list`).

#### Cómo medir el efecto:

1. Revisa SQL vía `queryset.query` o `django-debug-toolbar`.
2. Compara cantidad de queries antes/después.
3. Evalúa execution plan en BD real (`EXPLAIN ANALYZE`).

#### Errores típicos:

1. Hacer agregaciones en Python tras `list(qs)` en vez de SQL.
2. Llamar `save()` en bucle en vez de `update()` único.
3. Construir anotaciones complejas sin índices en BD.

#### Conclusión:

`annotate`, `aggregate`, `F`, `Q` son herramientas clave para ORM de alto
rendimiento. Ayudan a reducir queries, quitar cómputo extra en Python y mantener
trabajo de BD estable bajo carga.

</details>

<details>
<summary>56. ¿Cómo sobrescribir métodos save() y delete()?</summary>

#### Django

En Django se puede sobrescribir `save()` y `delete()` en el modelo para añadir
lógica adicional antes/después de guardar o eliminar un registro.

#### Cómo sobrescribir `save()`:

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

Regla clave: siempre llamar `super().save(*args, **kwargs)`.

#### Cómo sobrescribir `delete()`:

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

#### Qué hay que recordar:

1. `QuerySet.update()` no llama `save()`.
2. `QuerySet.delete()` no llama el `delete()` individual de cada instancia en el mismo sentido que la llamada directa.
3. Por eso, la lógica crítica para integridad conviene duplicarla en BD/capa de servicios.

#### Cuándo conviene sobrescribir:

1. Generar campos derivados (slug, valor normalizado).
2. Invariantes locales del modelo que no dependen de servicios externos.
3. Limpieza cuidadosa de recursos locales relacionados.

#### Cuándo conviene otro enfoque:

1. Lógica de negocio compleja u orquestación de varios modelos -> capa de servicios.
2. Efectos colaterales cross-módulo -> signals (con cuidado) o eventos de dominio.
3. Operaciones masivas -> comandos bulk separados en lugar de métodos de instancia.

#### Reglas prácticas:

1. `save()/delete()` deben mantenerse cortos y predecibles.
2. No hacer dentro llamadas HTTP externas lentas.
3. Documentar efectos colaterales para evitar "magia" en el equipo.
4. Cubrir estos puntos con tests (escenarios create/update/delete).

#### Conclusión:

Sobrescribir `save()` y `delete()` es potente pero delicado.
Úsalo para lógica local del modelo; comportamiento de dominio complejo conviene
mantenerlo en capa de servicios para claridad y control.

</details>

<details>
<summary>57. ¿Cómo funciona el borrado en cascada (CASCADE)?</summary>

#### Django

El borrado en cascada (`models.CASCADE`) significa: si se elimina el objeto
"padre", Django elimina automáticamente todos los registros "hijos" relacionados.

#### Dónde se usa:

- En `ForeignKey` y `OneToOneField` mediante parámetro `on_delete`.

#### Ejemplo:

```python
class Author(models.Model):
    name = models.CharField(max_length=120)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE, related_name="books")
```

Qué pasa:

- `author.delete()` -> Django elimina autor y todos sus libros.

#### Cuándo CASCADE es adecuado:

1. Los datos hijos no tienen sentido sin el padre.
2. Se quiere garantizar ausencia de registros "huérfanos".
3. Lifecycle de dominio simple para entidades dependientes.

#### Riesgos potenciales:

1. Borrado masivo accidental de gran volumen de datos.
2. Auditoría/recuperación compleja tras error.
3. Efectos secundarios inesperados en dominios relacionados.

#### Alternativas de `on_delete`:

1. `PROTECT` - bloquea borrado del padre si hay dependencias.
2. `SET_NULL` - pone `NULL` en campo hijo (`null=True` obligatorio).
3. `SET_DEFAULT` - coloca valor por defecto.
4. `RESTRICT` - restringe borrado con referencias existentes (similar a protect estricto).
5. `DO_NOTHING` - responsabilidad del lado BD/desarrollador.

#### Recomendaciones prácticas:

1. Para datos críticos de negocio, suele preferirse `PROTECT/RESTRICT`.
2. Para entidades técnicas claramente dependientes, `CASCADE` suele encajar.
3. Antes de borrado masivo, verifica qué se eliminará realmente.
4. Considera soft delete si se necesita auditoría histórica.

#### Conclusión:

`CASCADE` mantiene integridad de forma cómoda, pero es agresivo en comportamiento.
Úsalo donde el ciclo de vida de datos hijos dependa totalmente del padre.

</details>

<details>
<summary>58. ¿Cómo funcionan las transacciones en Django?</summary>

#### Django

Las transacciones en Django garantizan que un grupo de cambios en BD se ejecute
como unidad: o se aplican todos (`commit`) o ninguno (`rollback`) si hay error.

#### Herramienta principal:

- `transaction.atomic()`

#### Ejemplo básico:

```python
from django.db import transaction

@transaction.atomic
def create_order(user, items):
    order = Order.objects.create(user=user)
    for item in items:
        OrderItem.objects.create(order=order, product=item["product"], qty=item["qty"])
    return order
```

Si hay excepción dentro, todos los cambios del bloque se revierten.

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

#### Transacciones anidadas y savepoints:

- `atomic()` anidado crea savepoints.
- Error en bloque interno puede revertir solo esa parte al savepoint.

#### Modo `ATOMIC_REQUESTS`:

En `settings.py` se puede activar transacción para toda la request HTTP:

```python
DATABASES["default"]["ATOMIC_REQUESTS"] = True
```

Es cómodo, pero no siempre óptimo para rendimiento en endpoints complejos.

#### Recomendaciones prácticas:

1. Encierra en `atomic()` solo operaciones realmente relacionadas.
2. Mantén transacciones cortas (mínimas llamadas externas dentro).
3. No hagas HTTP/API externos dentro de transacción.
4. Para concurrencia, usa `select_for_update()`.

#### Ejemplo de bloqueo de fila:

```python
with transaction.atomic():
    account = Account.objects.select_for_update().get(pk=account_id)
    account.balance = F("balance") - amount
    account.save(update_fields=["balance"])
```

#### Errores típicos:

1. Ejecutar parte de operación fuera de `atomic()`.
2. Transacciones largas que mantienen locks y bloquean otras requests.
3. Suponer que transacción cubre sistemas externos (colas, APIs de terceros).
4. Ignorar niveles de aislamiento BD en escenarios de alta concurrencia.

#### Conclusión:

Las transacciones en Django son base de consistencia de datos. `transaction.atomic()`
debe ser estándar en operaciones críticas de varios pasos, sobre todo en dominios
financieros, inventario y workflows.

</details>

<details>
<summary>59. ¿Django soporta NoSQL?</summary>

#### Django

En corto: Django está **orientado nativamente a BD relacionales** (PostgreSQL,
MySQL, SQLite, Oracle) mediante su ORM. NoSQL no está al mismo nivel "de fábrica",
pero la integración es posible.

#### Qué significa en práctica:

1. **ORM principal de Django = SQL-first**
- La mayoría de features (migrations, relations, admin, constraints) están pensadas para SQL.

2. **NoSQL se conecta con librerías de terceros**
- Para MongoDB y otros hay adaptadores/ODM externos, pero la compatibilidad con
  el ecosistema Django suele ser parcial.

3. **En production, lo más común es arquitectura híbrida**
- Modelo transaccional principal en PostgreSQL.
- Almacén NoSQL para tareas especializadas (cache, documentos, búsqueda, eventos).

#### Roles típicos de NoSQL en proyectos Django:

1. Redis - caché, rate limit, broker de colas, sesiones.
2. Elasticsearch/OpenSearch - búsqueda full-text y analítica.
3. BD documental - dominios específicos con esquema flexible (si aplica).

#### Cuándo SQL en Django suele ser mejor:

- Relaciones complejas entre entidades.
- Transaccionalidad y garantías estrictas de consistencia.
- Mucho CRUD estándar + admin + modelo de dominio claro.

#### Cuándo NoSQL puede encajar:

- Esquema de datos muy flexible/cambiante.
- Acceso key-value de muy baja latencia.
- Escenarios de búsqueda/log-analítica donde SQL no rinde bien.

#### Recomendaciones de tech lead:

1. No reemplaces BD relacional por NoSQL "por tendencia".
2. Empieza con PostgreSQL como default confiable para Django.
3. Añade NoSQL de forma puntual para requisito no funcional concreto (latencia, search, escala).
4. Diseña aparte la consistencia entre SQL y NoSQL (outbox/events/retry).

#### Conclusión:

Django no es un framework NoSQL-first, pero funciona bien en arquitectura híbrida.
Estrategia óptima para la mayoría: SQL como base de datos de dominio + NoSQL como
complemento especializado para cargas concretas.

</details>

<details>
<summary>60. ¿Qué excepciones típicas de Django conviene conocer?</summary>

#### Django

Django tiene un conjunto de excepciones típicas que aparecen con frecuencia en
proyectos reales. Conocerlas acelera debug y ayuda a manejar errores correctamente
en view/API.

#### Excepciones más importantes:

1. **`Model.DoesNotExist`**
- Aparece con `Model.objects.get(...)` si no existe registro.

2. **`Model.MultipleObjectsReturned`**
- `get()` devolvió más de un registro.

3. **`ValidationError`**
- Errores de validación en forms, modelos y validadores custom.

4. **`IntegrityError`**
- Violación de constraints BD (`UNIQUE`, `FK`, `NOT NULL`, `CHECK`).

5. **`ObjectDoesNotExist`**
- Excepción base para todos los `*.DoesNotExist`.

6. **`PermissionDenied`**
- No hay acceso al recurso (403).

7. **`SuspiciousOperation`**
- Actividad sospechosa/peligrosa (por ejemplo, host/header inválido).

8. **`Http404`**
- Se usa para devolver 404 explícitamente.

9. **`ImproperlyConfigured`**
- Error de configuración de settings, URL, middleware, apps.

10. **`OperationalError` (db backend)**
- Problemas de conexión/disponibilidad de BD, timeouts, fallos de red.

#### Ejemplos de manejo:

```python
from django.core.exceptions import ValidationError
from django.db import IntegrityError
from django.http import Http404

try:
    user = User.objects.get(pk=user_id)
except User.DoesNotExist:
    raise Http404("Usuario no encontrado")

try:
    create_order(...)
except ValidationError as exc:
    return JsonResponse({"errors": exc.message_dict}, status=400)
except IntegrityError:
    return JsonResponse({"error": "Se violó la integridad de datos"}, status=409)
```

#### Reglas prácticas:

1. Para 404 en view usa `get_object_or_404`.
2. No "tragues" excepciones sin logging.
3. Separa errores de usuario (4xx) de errores del sistema (5xx).
4. En production no devuelvas stack trace al cliente.
5. En API estandariza formato de error (código, message, details).

#### Anti-patrones típicos:

1. `except Exception:` sin especificidad.
2. Ignorar `IntegrityError` y repetir operaciones inconsistentes.
3. Mezclar errores de dominio y excepciones técnicas en un único "400 unknown".

#### Conclusión:

Trabajar bien con excepciones en Django es clave para calidad de API, estabilidad
del servicio y diagnóstico rápido en production. Las excepciones base deben
conocerse y manejarse de forma sistemática.

</details>

<details>
<summary>61. ¿Qué es Django Admin? ¿Cómo registrar un modelo?</summary>

#### Django

`Django Admin` es el panel administrativo integrado para gestionar datos del
modelo por interfaz web sin crear un back-office desde cero.

#### Qué ofrece Django Admin:

1. CRUD de modelos "de fábrica".
2. Búsqueda, filtros, orden y paginación.
3. Trabajo con objetos relacionados (inlines).
4. Back-office rápido para equipo de negocio.

#### Cómo registrar un modelo (mínimo):

```python
# app/admin.py
from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

Después de esto, el modelo aparece en `/admin/`.

#### Variante recomendada con `ModelAdmin`:

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

#### Requisitos para entrar en admin:

1. Migraciones aplicadas:
```bash
python manage.py migrate
```
2. Superuser creado:
```bash
python manage.py createsuperuser
```
3. Servidor iniciado y abrir `/admin/`.

#### Recomendaciones prácticas:

1. Configura `list_display`, `search_fields`, `list_filter` en modelos clave.
2. Restringe acceso a admin por roles/permisos.
3. Para tablas grandes, optimiza queryset en `ModelAdmin` (select_related/prefetch).
4. No uses admin como interfaz pública para usuarios finales.

#### Conclusión:

Django Admin es una herramienta potente para gestión interna de datos. Registrar
un modelo toma minutos, y con `ModelAdmin` básico se vuelve un back-office
realmente productivo para el equipo.

</details>

<details>
<summary>62. ¿Qué es superuser?</summary>

#### Django

`Superuser` en Django es un usuario con permisos administrativos máximos en el
sistema, normalmente para acceso a Django Admin y control total de datos.

#### Características clave de superuser:

1. `is_superuser = True`
2. `is_staff = True`
3. Tiene todos los permisos sin asignar cada uno manualmente.
4. Puede gestionar usuarios, grupos, modelos y contenido desde `/admin/`.

#### Cómo crear superuser:

```bash
python manage.py createsuperuser
```

Luego Django solicitará:
- username
- email (según modelo)
- password

#### Dónde se usa:

1. Administración inicial del proyecto.
2. Configuración de roles/grupos y accesos.
3. Soporte operativo vía Django Admin.

#### Notas de seguridad importantes:

1. No uses la cuenta superuser para operación diaria.
2. Cantidad de superusers en production debe ser mínima.
3. Usa contraseñas fuertes + 2FA (si disponible vía SSO/admin).
4. Registra acciones de administrador y controla acceso por IP/VPN.
5. No crees superusers "temporales" sin proceso de eliminación.

#### Rol práctico en el equipo:

- Superuser es necesario para bootstrap.
- En operación estable, la mayoría de tareas deben ir con `staff` + grupos +
  permisos granulares, no con acceso total.

#### Conclusión:

Superuser es el "usuario root" en Django. Es crítico para administración, pero
su acceso debe estar estrictamente limitado y controlado.

</details>

<details>
<summary>63. ¿Cómo personalizar Django Admin?</summary>

#### Django

La personalización de Django Admin se hace con `ModelAdmin` y mecanismos
relacionados (inlines, actions, permissions, form overrides). Esto permite
convertir el admin base en un back-office eficiente.

#### Personalización base de `ModelAdmin`:

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

#### Herramientas más usadas:

1. `list_display` - columnas visibles en lista.
2. `list_filter` - filtros laterales.
3. `search_fields` - búsqueda por campos/relaciones.
4. `readonly_fields` - campos solo lectura.
5. `fieldsets` - agrupación de campos en formulario.
6. `actions` - acciones masivas sobre registros seleccionados.

#### Edición inline de modelos relacionados:

```python
class OrderItemInline(admin.TabularInline):
    model = OrderItem
    extra = 0

@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    inlines = [OrderItemInline]
```

#### Acciones personalizadas (actions):

```python
@admin.action(description="Marcar como publicadas")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)
```

#### Restricción de acceso:

- `has_view_permission`, `has_change_permission`, `has_delete_permission`
- `get_queryset()` para data-scoping (por ejemplo, manager ve solo sus objetos).

#### Optimización de rendimiento en admin:

1. Usa `list_select_related` para FK en `list_display`.
2. Cuidado con `search_fields` en tablas grandes (índices obligatorios).
3. Reduce cálculos pesados en list view.
4. Para catálogos grandes usa `autocomplete_fields`.

#### Personalización adicional:

- Override de `form`/`get_form`.
- Override de `save_model`/`delete_model`.
- Templates admin custom para UI específica.

#### Conclusión:

Django Admin escala bien con `ModelAdmin`: desde registro simple hasta un panel
interno completo con roles, filtros, acciones masivas y rendimiento controlado.

</details>

<details>
<summary>64. ¿Qué componentes tiene Django Admin y qué ajustes individuales hay?</summary>

#### Django

Django Admin se compone de varios elementos clave que pueden ajustarse según
procesos de negocio: lista de objetos, formulario de edición, filtros, búsqueda,
actions, permisos, inlines y configuración global del sitio admin.

#### Componentes principales de Django Admin:

1. **Admin Site (`admin.site`)**
- Panel global; header/title/index se pueden personalizar.

2. **`ModelAdmin`**
- Configuración de cómo se muestra una modelo concreta en admin.

3. **Change List**
- Página de lista (`list_display`, `list_filter`, `search_fields`).

4. **Change Form**
- Formulario crear/editar (`fields`, `fieldsets`, `readonly_fields`).

5. **Inlines**
- Edición de modelos relacionados en la misma página.

6. **Actions**
- Operaciones masivas sobre registros seleccionados.

7. **Permissions**
- Acceso de ver/editar/borrar por roles.

#### Ejemplo de ajustes individuales:

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
        ("Estado", {"fields": ("is_active",)}),
        ("Servicio", {"fields": ("created_at", "updated_at")}),
    )
```

#### Ajustes globales de admin site:

```python
from django.contrib import admin

admin.site.site_header = "Admin Panel"
admin.site.site_title = "Backoffice"
admin.site.index_title = "Gestión del sistema"
```

#### Comportamiento individual por rol:

- `get_queryset()` - limitar qué ve cada usuario staff.
- `get_readonly_fields()` - hacer campos readonly según rol.
- `has_change_permission()` / `has_delete_permission()` - control granular.

#### Componentes comunes en production:

1. `autocomplete_fields` para FK pesados.
2. `list_select_related` para optimizar list-view.
3. `form` custom y `formfield_overrides` para mejor UX.
4. Templates custom para casos específicos de back-office.

#### Conclusión:

La fuerza de Django Admin es que, con componentes base, puedes construir una
interfaz interna ajustada al proceso del equipo: rápida, segura y operativamente útil.

</details>

<details>
<summary>65. ¿Qué son Django Admin actions y su personalización?</summary>

#### Django

`Admin actions` en Django son operaciones masivas sobre objetos seleccionados en
el listado de admin. Permiten ejecutar tareas típicas sin editar registro por registro.

#### Qué es una action:

- Función o método que recibe:
  `modeladmin`, `request`, `queryset`.
- Se ejecuta para el conjunto de objetos marcados por el usuario admin.

#### Ejemplo básico de action:

```python
from django.contrib import admin
from .models import Article

@admin.action(description="Publicar artículos seleccionados")
def make_published(modeladmin, request, queryset):
    queryset.update(is_published=True)

@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    list_display = ("id", "title", "is_published")
    actions = [make_published]
```

#### Ejemplo action como método `ModelAdmin`:

```python
@admin.register(Order)
class OrderAdmin(admin.ModelAdmin):
    actions = ["mark_as_paid"]

    @admin.action(description="Marcar como pagados")
    def mark_as_paid(self, request, queryset):
        updated = queryset.update(status="paid")
        self.message_user(request, f"Pedidos actualizados: {updated}")
```

#### Personalización de actions:

1. `description` propio para UI.
2. Condiciones de disponibilidad según rol/estado.
3. Página intermedia de confirmación (custom admin view).
4. Logging de acciones masivas ejecutadas.

#### Recomendaciones prácticas:

1. Para cambios masivos prioriza `queryset.update()` (más rápido, menos SQL).
2. Si necesitas lógica por objeto, itera con cuidado dentro de transacción.
3. Muestra resultado con `message_user`.
4. Restringe actions peligrosas para roles no administrativos.

#### Matices importantes:

1. `queryset.update()` no llama `save()` ni señales `post_save`.
2. El borrado masivo de acción estándar puede ser riesgoso sin control adicional.
3. Para operaciones críticas, añade paso de confirmación.

#### Casos típicos de actions:

- Publicar/Despublicar contenido.
- Asignación batch de estado.
- Exportar seleccionados a CSV.
- Lanzar procesamiento en background para IDs seleccionados.

#### Conclusión:

Admin actions es una herramienta rápida de automatización operativa en Django
Admin. Bien personalizadas, aceleran el trabajo del equipo y reducen tareas manuales.

</details>

<details>
<summary>66. ¿Qué es middleware y cómo funciona?</summary>

#### Django

`Middleware` en Django es una capa entre request/response HTTP y la view.
Permite ejecutar código **antes** de que el request llegue a view y **después**
de que la respuesta vuelva al cliente.

#### Cómo funciona el pipeline middleware:

1. La request llega a Django.
2. Pasa secuencialmente por middleware (request phase).
3. Llega a URL resolver y view.
4. La response vuelve por middleware en orden inverso (response phase).
5. Se envía al cliente.

#### Detalle importante:

- El orden en `settings.py` (`MIDDLEWARE = [...]`) es crítico.
- Middleware superiores ven primero la request y últimos la response.

#### Tareas típicas de middleware:

1. Seguridad (security headers, host checks).
2. Sesiones y autenticación.
3. Protección CSRF.
4. Localización (locale/language).
5. Logging, request-id, métricas.
6. Caché a nivel request/response.

#### Esqueleto middleware:

```python
class SimpleMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # antes de view
        response = self.get_response(request)
        # después de view
        return response
```

#### Dónde se conecta:

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    # ...
]
```

#### Reglas prácticas:

1. Mantén middleware ligero y rápido.
2. No pongas lógica de negocio pesada ahí.
3. Evita llamadas externas lentas dentro de middleware.
4. Controla con cuidado el orden de middleware.

#### Errores típicos:

1. Middleware demasiado "inteligente" con efectos secundarios.
2. Orden incorrecto que rompe auth/csrf/session flow.
3. Duplicar lógica entre middleware y view.

#### Conclusión:

Middleware es un interceptor global de requests/responses en Django. Su fuerza
está en tareas cross-cutting (seguridad, sesiones, logging), no en lógica de
negocio de endpoints concretos.

</details>

<details>
<summary>67. ¿Qué middleware integrados existen?</summary>

#### Django

Django incluye un conjunto de middleware built-in que cubren necesidades base:
seguridad, sesiones, autenticación, CSRF, caché y localización.

#### Middleware built-in más comunes:

1. **`django.middleware.security.SecurityMiddleware`**
- Security headers, ajustes HTTPS y mecanismos de protección base.

2. **`django.contrib.sessions.middleware.SessionMiddleware`**
- Soporte de sesiones server-side.

3. **`django.middleware.common.CommonMiddleware`**
- Comportamientos HTTP comunes (por ejemplo, `APPEND_SLASH`, `PREPEND_WWW`).

4. **`django.middleware.csrf.CsrfViewMiddleware`**
- Protección frente a ataques CSRF en requests que cambian estado.

5. **`django.contrib.auth.middleware.AuthenticationMiddleware`**
- Agrega `request.user` e integra auth en el flujo request.

6. **`django.contrib.messages.middleware.MessageMiddleware`**
- Soporte de mensajes flash (`messages.success`, `messages.error`).

7. **`django.middleware.clickjacking.XFrameOptionsMiddleware`**
- Protección clickjacking con header `X-Frame-Options`.

8. **`django.middleware.locale.LocaleMiddleware`**
- Detección de idioma/locale para i18n.

9. **`django.middleware.gzip.GZipMiddleware`**
- Compresión de responses (con cuidado para contenido ya comprimido).

10. **`django.middleware.cache.UpdateCacheMiddleware` / `FetchFromCacheMiddleware`**
- Caché site-wide a nivel middleware.

#### Orden típico en `MIDDLEWARE` (resumen):

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

#### Notas prácticas:

1. El orden importa y afecta comportamiento de toda la app.
2. No elimines `SecurityMiddleware`, `CsrfViewMiddleware`, `AuthenticationMiddleware`
   sin entender consecuencias.
3. En production, valida headers de seguridad y cache-policy tras cambios.

#### Conclusión:

Los middleware integrados de Django cubren gran parte de la infraestructura "de
fábrica". El set y orden correctos impactan directamente seguridad, estabilidad
y comportamiento en production.

</details>

<details>
<summary>68. ¿Cómo crear middleware propio?</summary>

#### Django

El middleware propio en Django se crea como clase que recibe `get_response` y
intercepta `request/response` dentro del pipeline global de requests.

#### Plantilla mínima de middleware:

```python
# app/middleware.py
class RequestIdMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        # lógica antes de view
        response = self.get_response(request)
        # lógica después de view
        return response
```

#### Ejemplo con request-id:

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

#### Conexión en `settings.py`:

```python
MIDDLEWARE = [
    # ...
    "app.middleware.RequestIdMiddleware",
]
```

#### Dónde ubicarlo en la lista:

1. Middleware de seguridad/sesión normalmente arriba.
2. Logging/request-id custom suele ir tras security/session base.
3. El orden importa: afecta qué información ve middleware en `request`.

#### Qué puedes hacer en middleware:

- Añadir headers.
- Loguear request/response.
- Añadir contexto de tracing.
- Rechazar requests por reglas globales.

#### Qué no conviene hacer:

1. Lógica de negocio compleja de endpoint concreto.
2. Llamadas HTTP externas lentas.
3. Operaciones pesadas que bloqueen cada request.

#### Conclusión:

Middleware custom es herramienta para tareas cross-cutting de toda la app.
Debe ser ligero, predecible y bien ubicado en `MIDDLEWARE` para evitar efectos
colaterales.

</details>

<details>
<summary>69. ¿Qué son signals y cuándo usarlos?</summary>

#### Django

`Signals` en Django es un mecanismo de eventos que permite ejecutar código como
reacción a acciones específicas (por ejemplo, guardar o borrar modelo) sin llamar
esa lógica directamente desde view/servicio.

#### Cómo funciona:

1. Ocurre un evento (signal), por ejemplo `post_save`.
2. Una función receiver suscrita al evento se ejecuta automáticamente.

#### Signals más usados:

1. `pre_save`, `post_save`
2. `pre_delete`, `post_delete`
3. `m2m_changed`
4. `request_started`, `request_finished` (menos comunes para lógica de app)

#### Ejemplo `post_save`:

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

Import/registro en `apps.py`:

```python
from django.apps import AppConfig

class UsersConfig(AppConfig):
    name = "users"

    def ready(self):
        import users.signals  # noqa
```

#### Cuándo signals es adecuado:

1. Efectos secundarios débilmente acoplados (por ejemplo, crear perfil tras crear usuario).
2. Hooks técnicos que no deben ensuciar view.
3. Eventos donde conviene desacoplar módulos.

#### Cuándo mejor evitar signals:

1. Lógica de negocio crítica que requiere secuencia explícita.
2. Orquestaciones complejas entre varios servicios.
3. Lógica que debe ser visible en un único use-case explícito.

#### Problemas típicos de signals:

1. "Magia" y efectos secundarios inesperados.
2. Debug difícil en proyectos grandes.
3. Doble ejecución por registro descuidado.
4. Orden de ejecución difícil de controlar con muchos receivers.

#### Reglas prácticas:

1. Signals debe ser corto y rápido.
2. Tareas largas/pesadas llévalas a cola (Celery/RQ).
3. Documenta eventos a los que se suscribe cada módulo.
4. No escondas en signal la lógica principal de transacción.

#### Conclusión:

Signals en Django es útil para efectos secundarios moderados y bajo acoplamiento.
Para procesos core de negocio, suele ser más fiable una capa de servicios explícita.

</details>

<details>
<summary>70. Diferencia entre signals y middleware.</summary>

#### Django

`Middleware` y `signals` resuelven problemas distintos, aunque ambos parezcan
"lugar para lógica adicional". La diferencia clave es el **nivel de evento** en
el que trabajan.

#### Middleware:

1. Funciona a nivel **HTTP request/response**.
2. Se ejecuta para cada request en pipeline global.
3. Se usa para tareas web cross-cutting.

Casos típicos:

- security headers
- auth/session flow
- logging/tracing/request-id
- locale/caching/compression

#### Signals:

1. Funciona a nivel **eventos de modelo/framework**.
2. Se dispara en acciones tipo `post_save`, `post_delete`, `m2m_changed`.
3. Se usa para reaccionar a eventos del dominio de datos.

Casos típicos:

- crear perfil tras crear usuario
- sincronizar entidades auxiliares
- hooks ligeros tras cambios de datos

#### Diferencia principal:

- Middleware responde a request/response.
- Signals responde a eventos de datos/modelos.

#### Cuándo elegir cada uno:

1. Necesitas comportamiento HTTP global -> **middleware**.
2. Necesitas reacción a cambios de modelo -> **signals**.
3. Necesitas control explícito del flujo de negocio -> **capa de servicios**, no signals/middleware.

#### Tabla comparativa:

| Criterio | Middleware | Signals |
| --- | --- | --- |
| Nivel | HTTP pipeline | Model/framework events |
| Punto de ejecución | Antes/después de view | Antes/después de save/delete, etc. |
| Transparencia del flujo | Más alta (vía `MIDDLEWARE`) | Más baja (puede haber "magia") |
| Tipo de tareas | Infraestructura | Efectos secundarios por eventos |

#### Errores típicos:

1. Meter lógica de negocio de modelo en middleware.
2. Ocultar flow crítico de negocio en signals sin orquestación explícita.
3. Duplicar misma lógica en ambas capas.

#### Conclusión:

Middleware es para infraestructura HTTP; signals para reacción a eventos de
modelo. Para lógica de negocio importante, los servicios explícitos son lo más
transparente, testeable y robusto.

</details>

<details>
<summary>71. ¿Cómo funciona el sistema de autenticación y autorización?</summary>

#### Django

En Django, el sistema de acceso consta de dos partes:

1. **Autenticación (authentication)** - ¿quién eres?
2. **Autorización (authorization)** - ¿qué te está permitido?

#### Cómo funciona la autenticación:

1. El usuario envía login/password.
2. Django valida credenciales con `authenticate()`.
3. Si es correcto, se llama `login()` y se crea sesión.
4. En requests siguientes, `AuthenticationMiddleware` agrega `request.user`.

Ejemplo básico:

```python
from django.contrib.auth import authenticate, login

user = authenticate(request, username=username, password=password)
if user is not None:
    login(request, user)
```

#### Cómo funciona la autorización:

- Django valida permisos vía permissions, grupos y reglas role-based.
- Permisos base por modelo:
  `add`, `change`, `delete`, `view`.

Comprobación de permiso:

```python
if request.user.has_perm("orders.change_order"):
    ...
```

#### Herramientas de control de acceso:

1. `@login_required` - acceso solo para usuarios autenticados.
2. `@permission_required("app.perm_codename")`
3. `LoginRequiredMixin`, `PermissionRequiredMixin` para CBV.
4. Grupos (`Group`) para gestión por roles de permisos.

#### Modelo de sesión (por defecto):

- Tras `login()`, Django crea sesión en BD/caché.
- El identificador de sesión se guarda en cookie.
- En cada request, el usuario se identifica por esa sesión.

#### Dónde se configura:

- `AUTHENTICATION_BACKENDS`
- `LOGIN_URL`, `LOGIN_REDIRECT_URL`, `LOGOUT_REDIRECT_URL`
- `AUTH_USER_MODEL` (si usas modelo custom)

#### Recomendaciones prácticas:

1. No valides acceso solo en frontend; backend debe ser fuente de verdad.
2. Agrupa permisos por roles, no usuario por usuario.
3. Para API diseña por separado token/session auth y policy de acceso.
4. Registra acciones admin sensibles para auditoría.

#### Conclusión:

En Django, autenticación resuelve identidad del usuario y autorización define
sus permisos. Juntas forman un modelo de acceso seguro y escalable para apps
web y API.

</details>

<details>
<summary>72. ¿Cómo implementar registro de usuarios?</summary>

#### Django

El registro de usuarios en Django normalmente incluye formulario, lógica de view,
creación de usuario con password hasheado y (opcional) login automático.

#### Enfoque base:

1. Crear formulario de registro (`UserCreationForm` o custom).
2. Procesar formulario en view (`GET`/`POST`).
3. Guardar usuario.
4. Redirigir a login o hacer autologin.

#### Ejemplo de formulario:

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

#### Ejemplo de view:

```python
# users/views.py
from django.contrib.auth import login
from django.shortcuts import redirect, render
from .forms import SignUpForm

def signup_view(request):
    if request.method == "POST":
        form = SignUpForm(request.POST)
        if form.is_valid():
            user = form.save()  # password se hashea automáticamente
            login(request, user)  # opcional: login inmediato
            return redirect("home")
    else:
        form = SignUpForm()
    return render(request, "users/signup.html", {"form": form})
```

#### Plantilla:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Registrarse</button>
</form>
```

#### URL:

```python
path("signup/", signup_view, name="signup")
```

#### Reglas importantes de seguridad:

1. Nunca guardes password en texto plano manualmente.
2. Usa `UserCreationForm` o `set_password()`.
3. Añade protección brute force (rate limiting / captcha, si aplica).
4. En production, mejor confirmar email antes de activar cuenta.

#### Extensiones del registro:

1. Perfil de usuario (vía `OneToOne`).
2. Confirmación email por token.
3. Social login (Google/GitHub) vía allauth.
4. Audit log de eventos de registro.

#### Conclusión:

En Django, el registro se implementa rápido con auth forms y flujo de view.
Lo clave es gestión correcta de contraseñas, protección CSRF y proceso de
activación bien diseñado en production.

</details>

<details>
<summary>73. ¿Cómo crear tu propio modelo de usuario?</summary>

#### Django

Un modelo de usuario propio en Django se crea cuando el `User` estándar no basta
(por ejemplo, email como login, campos adicionales obligatorios o lógica custom).

#### Regla clave:

`AUTH_USER_MODEL` debe definirse **al inicio del proyecto**, antes de primeras
migraciones. Cambiarlo tarde es costoso y riesgoso.

#### Opción 1 (recomendada en 90% de casos): `AbstractUser`

- Heredas usuario built-in y agregas campos.
- Es el camino más simple y estable.

```python
# users/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    phone = models.CharField(max_length=30, blank=True)
    timezone = models.CharField(max_length=64, blank=True, default="UTC")
```

En `settings.py`:

```python
AUTH_USER_MODEL = "users.User"
```

#### Opción 2: `AbstractBaseUser` + `PermissionsMixin`

- Control total de modelo y campo de login.
- Mucho más complejo: `UserManager` custom, `USERNAME_FIELD`,
  `REQUIRED_FIELDS`, compatibilidad admin/forms/auth flow.

Úsalo solo si realmente necesitas auth no estándar.

#### Ejemplo de referencia al usuario custom en modelos:

```python
from django.conf import settings

class Order(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
```

#### En código, en vez de importar `User` directo:

```python
from django.contrib.auth import get_user_model
User = get_user_model()
```

#### Recomendaciones prácticas:

1. Si dudas, crea modelo custom con `AbstractUser` desde el inicio.
2. No uses `from django.contrib.auth.models import User` en código de dominio.
3. Verifica que forms/admin/auth backend funcionen con tu modelo.
4. Cubre con tests registro, login, reset password y permisos.

#### Errores típicos:

1. Intentar cambiar user model después de arrancar en production.
2. Importar `User` estándar de forma rígida en modelos/migraciones.
3. Usar `AbstractBaseUser` sin necesidad real y sin configuración completa.

#### Conclusión:

Un user model custom correcto en Django es decisión estratégica de inicio.
Camino más seguro: `AbstractUser` + `AUTH_USER_MODEL` + disciplina de uso de
`get_user_model()` y `settings.AUTH_USER_MODEL` en todo el proyecto.

</details>

<details>
<summary>74. ¿Para qué se usa login_required?</summary>

#### Django

`login_required` es un decorador que restringe acceso a una view solo para
usuarios autenticados.

#### Cómo funciona:

1. Si usuario autenticado -> view se ejecuta.
2. Si no -> redirect a login (`LOGIN_URL`) con parámetro `next`.

#### Ejemplo para FBV:

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, "dashboard.html")
```

#### Login URL custom:

```python
@login_required(login_url="/auth/login/")
def billing_page(request):
    ...
```

#### Equivalente para CBV:

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import TemplateView

class DashboardView(LoginRequiredMixin, TemplateView):
    template_name = "dashboard.html"
```

#### Configuración en `settings.py`:

```python
LOGIN_URL = "login"
LOGIN_REDIRECT_URL = "home"
```

#### Para qué se usa:

1. Proteger páginas privadas (cabinet, pedidos, ajustes de perfil).
2. Control de acceso base en secciones tipo admin.
3. Evitar POST no autorizados.

#### Lo que `login_required` NO hace:

1. No valida roles/permisos (solo estado de login).
2. No sustituye control de autorización detallado.

Para permisos usa:

- `permission_required`
- `user_passes_test`
- `PermissionRequiredMixin`

#### Consejos prácticos:

1. Pon `login_required` por defecto en endpoints privados.
2. No dependas solo de ocultar botones en frontend.
3. Verifica que `next` redirect sea seguro (Django lo maneja estándar).

#### Conclusión:

`login_required` es protección base y obligatoria para views privadas en Django.
Resuelve "si el usuario inició sesión"; permisos finos se construyen con
mecanismos adicionales de autorización.

</details>

<details>
<summary>75. ¿Cómo funcionan sesiones y cookies?</summary>

#### Django

En Django, sesiones y cookies se usan para mantener estado entre requests, ya que
HTTP por sí mismo es stateless.

#### Qué son cookies:

- Datos pequeños almacenados por el navegador en cliente.
- Se envían de vuelta al servidor en cada request al mismo dominio.
- A menudo contienen session ID, no datos sensibles directos.

#### Qué es una sesión:

- Almacenamiento server-side de datos de usuario (BD/caché/archivos).
- Navegador guarda solo la clave de sesión en cookie.
- Con `request.session`, Django lee/actualiza datos de sesión.

#### Cómo trabajan juntos:

1. Tras login, Django crea sesión en servidor.
2. Session key se guarda en cookie (`sessionid`).
3. En cada request, Django lee cookie y reconstruye sesión.

#### Ejemplo de trabajo con sesión:

```python
def set_theme(request):
    request.session["theme"] = "dark"
    return HttpResponse("ok")

def get_theme(request):
    theme = request.session.get("theme", "light")
    return HttpResponse(theme)
```

#### Ejemplo de cookie explícita:

```python
response = HttpResponse("ok")
response.set_cookie("promo_seen", "1", max_age=3600)
```

#### Dónde se guardan sesiones en Django:

- Por defecto: en BD (`django.contrib.sessions`).
- Se puede cambiar backend a cache, file, signed cookies.

#### Ajustes de seguridad importantes:

1. `SESSION_COOKIE_HTTPONLY = True` (protección frente acceso JS a cookie).
2. `SESSION_COOKIE_SECURE = True` (solo vía HTTPS).
3. `SESSION_COOKIE_SAMESITE = "Lax"` o `"Strict"` según caso.
4. Igual para CSRF cookie (`CSRF_COOKIE_SECURE`, `CSRF_COOKIE_HTTPONLY`).

#### Recomendaciones prácticas:

1. No guardes datos sensibles directamente en cookie.
2. Minimiza volumen de datos en sesión.
3. Para escalar, usa sesiones con backend Redis.
4. Limpia/invalida sesión en logout y cambios críticos de cuenta.

#### Conclusión:

Cookies son mecanismo cliente para pasar pocos datos; sesiones son almacenamiento
server-side de estado de usuario. En Django trabajan juntas y son base del
flujo auth clásico y UX personalizado.

</details>

<details>
<summary>76. ¿Qué son grupos y permisos, y cómo implementar un modelo de acceso por roles?</summary>

#### Django

En Django, **permissions** (permisos) y **groups** (grupos) son mecanismos base
de autorización para implementar RBAC (Role-Based Access Control).

#### Qué son permisos (permissions):

- Son derechos tipo `app_label.codename`, por ejemplo:
  `orders.view_order`, `orders.change_order`.
- Django crea automáticamente permisos base por modelo:
  `add`, `change`, `delete`, `view`.
- Se pueden agregar custom permissions en `Meta`.

#### Qué son grupos (groups):

- Grupo = rol al que se le asigna un conjunto de permisos.
- Al agregar usuario al grupo, recibe permisos del rol.

#### Ejemplo de custom permission en modelo:

```python
class Order(models.Model):
    ...
    class Meta:
        permissions = [
            ("approve_order", "Can approve order"),
        ]
```

#### Verificación de acceso en código:

```python
if request.user.has_perm("orders.approve_order"):
    ...
```

Decorador:

```python
from django.contrib.auth.decorators import permission_required

@permission_required("orders.approve_order", raise_exception=True)
def approve_view(request, order_id):
    ...
```

#### Ejemplo de roles (RBAC):

1. **viewer** -> solo `view_*`
2. **manager** -> `view_*`, `change_*`, `approve_order`
3. **admin** -> acceso completo del dominio

#### Proceso típico para implementar RBAC:

1. Definir roles y responsabilidades.
2. Definir mapping "rol -> permisos".
3. Crear grupos y asignar permisos.
4. Añadir usuarios a grupos (admin o scripts seed).
5. Validar permisos en view/CBV/API.

#### Recomendaciones prácticas:

1. Asigna permisos por roles (groups), no manualmente por usuario.
2. Mantén policy de acceso centralizada y documentada.
3. Valida acceso en backend aunque UI oculte botones.
4. Para casos complejos, añade object-level permissions (si hace falta).

#### Errores típicos:

1. Dar `is_superuser` donde bastan permisos de rol.
2. Mezclar roles y estados de negocio sin reglas claras.
3. Asignar permisos "temporales" sin auditoría ni vencimiento.

#### Conclusión:

Grupos y permisos en Django son base robusta para acceso por roles.
RBAC vía groups vuelve el sistema más seguro, transparente y mantenible cuando
crecen equipo y producto.

</details>

<details>
<summary>77. ¿Cómo implementar recuperación de contraseña?</summary>

#### Django

La recuperación de contraseña en Django se implementa más fácil con auth-views
integradas: incluyen flow seguro con token de un solo uso y validación de vigencia.

#### Flow estándar:

1. Usuario introduce email en "Olvidé contraseña".
2. Django envía email con enlace (uid + token).
3. Usuario abre enlace y define nueva contraseña.
4. Django confirma cambio exitoso.

#### Configuración de URL:

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

#### Plantillas necesarias:

- `registration/password_reset_form.html`
- `registration/password_reset_done.html`
- `registration/password_reset_confirm.html`
- `registration/password_reset_complete.html`
- plantilla email, por ejemplo `registration/password_reset_email.html`

#### Configuración base de email:

```python
EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "smtp.example.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "..."
EMAIL_HOST_PASSWORD = "..."
DEFAULT_FROM_EMAIL = "noreply@example.com"
```

#### Principios de seguridad importantes:

1. No revelar si email existe o no (evitar user enumeration).
2. Usar HTTPS en enlaces de reset.
3. Limitar frecuencia de solicitudes reset (rate limiting).
4. Tras cambio de password, invalidar sesiones activas según policy.
5. Registrar eventos de recuperación para auditoría.

#### Cuándo hace falta customización:

- Diseño propio de emails/páginas.
- Modelo de usuario custom con login por email.
- Integración con auth externa/SSO.

#### Conclusión:

Django aporta mecanismo seguro listo para recuperación de contraseña vía
auth-views estándar. En production basta configurar bien email, plantillas,
HTTPS y protección anti-abuso.

</details>

<details>
<summary>78. ¿Qué es CSRF y cómo funciona {% csrf_token %}?</summary>

#### Django

**CSRF (Cross-Site Request Forgery)** es un ataque en el que un sitio malicioso
fuerza a un usuario autenticado a ejecutar acciones no deseadas en tu aplicación
(por ejemplo, cambiar password o crear un pago).

#### Cómo protege Django contra CSRF:

1. En servidor se genera token CSRF.
2. El token se inserta en formulario (con `{% csrf_token %}`).
3. Para requests que cambian estado (`POST`, `PUT`, `PATCH`, `DELETE`), Django
   compara token recibido con token esperado.
4. Si token falta o es inválido -> `403 Forbidden`.

#### `{% csrf_token %}` en formulario:

```django
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}
  <button type="submit">Guardar</button>
</form>
```

#### Qué se necesita para que funcione:

1. `django.middleware.csrf.CsrfViewMiddleware` en `MIDDLEWARE`.
2. Uso de `{% csrf_token %}` en todos los formularios POST.
3. Política correcta de cookies (especialmente production con HTTPS).

#### Para requests AJAX/fetch:

- El token se manda en header `X-CSRFToken`.
- Se toma desde cookie (`csrftoken`) o HTML (según enfoque).

#### Errores típicos:

1. Olvidar `{% csrf_token %}` en plantilla de formulario.
2. Desactivar `CsrfViewMiddleware` sin motivo sólido.
3. Configurar mal dominio/secure flags de cookie.
4. Usar `@csrf_exempt` "rápido" y olvidar restaurar protección.

#### Cuándo `csrf_exempt` puede ser válido:

- Solo para endpoints especiales (por ejemplo, webhooks externos), y solo si hay
  otro mecanismo de validación fiable (HMAC signature, token, allowlist).

#### Recomendaciones prácticas:

1. Todos los formularios browser-based que cambian estado deben incluir `{% csrf_token %}`.
2. Para API sin cookie-session (Bearer/JWT), diseña modelo auth separado.
3. En production usa HTTPS + `CSRF_COOKIE_SECURE = True`.

#### Conclusión:

`{% csrf_token %}` es pieza clave de protección Django frente a CSRF en formularios.
No es opcional: es estándar base de seguridad para acciones que cambian estado.

</details>

<details>
<summary>79. ¿Cómo protege Django contra XSS, CSRF y SQL injection?</summary>

#### Django

Django sigue enfoque "secure by default" y trae mecanismos integrados contra
vulnerabilidades web comunes: XSS, CSRF y SQL injection.

#### 1. Protección contra XSS (Cross-Site Scripting)

Cómo funciona:

1. Django templates auto-escapan variables en `{{ ... }}`.
2. Caracteres HTML especiales se convierten a forma segura.
3. Contenido potencialmente peligroso no se ejecuta como script.

Importante:

- `|safe` desactiva escape; úsalo solo con HTML completamente confiable.
- No renderices user input crudo sin sanitización.

#### 2. Protección contra CSRF

Cómo funciona:

1. `CsrfViewMiddleware` valida token en requests que cambian estado.
2. `{% csrf_token %}` agrega token en formularios HTML.
3. Sin token válido, Django responde `403`.

#### 3. Protección contra SQL injection

Cómo funciona:

1. ORM usa queries parametrizadas.
2. Datos se pasan separados de estructura SQL.
3. Esto bloquea inyecciones clásicas en escenarios estándar.

El riesgo aparece si:

- escribes raw SQL concatenando strings manualmente.

#### Protecciones adicionales built-in de Django:

1. `SecurityMiddleware` (headers, policies SSL-related).
2. `XFrameOptionsMiddleware` (protección clickjacking).
3. Hash seguro de contraseñas (`PBKDF2` por defecto).
4. Checks de host header (`ALLOWED_HOSTS`).

#### Recomendaciones production:

1. `DEBUG=False` en production.
2. HTTPS en todo (`SECURE_SSL_REDIRECT`, secure cookies).
3. Configurar `SESSION_COOKIE_SECURE`, `CSRF_COOKIE_SECURE`, `HTTPONLY`.
4. Usar CSP (headers/paquetes).
5. Actualizar Django y dependencias regularmente.

#### Errores típicos de desarrollo:

1. Uso sin control de `|safe`.
2. `@csrf_exempt` sin validación alternativa.
3. Raw SQL con f-string/format.
4. `DEBUG=True` en production.

#### Conclusión:

Django da base fuerte de protección para XSS, CSRF y SQL injection. Pero la
seguridad también depende de disciplina de código: templates correctos, uso ORM,
settings de production y security-review continuo.

</details>

<details>
<summary>80. ¿Cómo protege Django contra SQL injection?</summary>

#### Django

Django protege contra SQL injection sobre todo mediante ORM y queries
parametrizadas: el input de usuario se pasa como parámetro, no incrustado en SQL.

#### Mecanismo principal de protección:

1. Escribes query ORM:
```python
User.objects.filter(email=user_input)
```
2. Django genera SQL con placeholders.
3. El valor `user_input` no rompe estructura SQL.

#### Por qué es seguro:

- ORM separa lógica SQL de los datos.
- La BD trata parámetros como valores, no como parte del comando SQL.

#### Dónde SQL injection aún puede aparecer:

1. **Raw SQL con concatenación de strings**
```python
# Inseguro
sql = f"SELECT * FROM users WHERE email = '{user_input}'"
```

2. Uso incorrecto de `.extra()` (enfoque legacy).
3. ORDER BY/field name dinámico sin allowlist.

#### Raw SQL seguro (si realmente hace falta):

```python
from django.db import connection

with connection.cursor() as cursor:
    cursor.execute("SELECT * FROM users WHERE email = %s", [user_input])
    rows = cursor.fetchall()
```

#### Reglas prácticas:

1. Por defecto usa ORM (`filter/get/exclude/annotate`).
2. Si raw SQL es inevitable, solo queries parametrizadas.
3. Nunca insertes user input en SQL con f-string o `format`.
4. Para campos/orden dinámicos usa allowlist:
- solo nombres de columnas predefinidos.

#### Hardening adicional:

1. Privilegios mínimos para usuario de BD (least privilege).
2. Logs de queries sospechosas y monitoreo de anomalías.
3. Actualizaciones regulares de Django/drivers BD.

#### Conclusión:

Django ORM protege bien contra SQL injection "de fábrica". Los riesgos reales
aparecen cuando se evita ORM y se construye SQL manual sin parametrización ni
validación.

</details>

<details>
<summary>81. ¿Qué es Content Security Policy (CSP) en Django?</summary>

#### Django

**Content Security Policy (CSP)** es una política de seguridad HTTP que limita
las fuentes desde las que el navegador puede cargar scripts, estilos, imágenes,
fuentes, etc. Su objetivo principal es reducir el riesgo de XSS y la ejecución de contenido peligroso.

#### Qué hace CSP:

1. Define una allowlist de fuentes (`self`, CDN, dominios de API).
2. Bloquea recursos desconocidos o inyectados.
3. Permite introducir la política gradualmente mediante `Report-Only`.

#### Ejemplo de encabezado CSP:

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

#### Cómo agregar CSP en Django:

La forma más conveniente es usar el paquete `django-csp`:

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

#### Prácticas importantes:

1. Empieza con `Content-Security-Policy-Report-Only` para recopilar violaciones.
2. Minimiza el uso de `'unsafe-inline'` y `'unsafe-eval'`.
3. Para scripts inline, usa el enfoque nonce/hash.
4. Restringe gradualmente la política a las fuentes estrictamente necesarias.

#### Problemas típicos durante la implementación:

1. Widgets/analítica de terceros se rompen por reglas demasiado estrictas.
2. Fuentes wildcard poco pensadas (`*`) reducen el valor de CSP.
3. Falta de monitoreo de violaciones CSP después del release.

#### Conclusión:

CSP en Django es una capa adicional importante de protección contra XSS y
riesgos de supply chain. El mejor enfoque: primero `Report-Only`, después un
endurecimiento gradual de la política hacia un modelo estricto de allowlist.

</details>

<details>
<summary>82. ¿Qué son los custom management commands y cuándo conviene usarlos?</summary>

#### Django

`Custom management commands` son comandos CLI propios de Django que se ejecutan
con `python manage.py <command_name>`. Permiten formalizar tareas operativas y
técnicas como código mantenible del proyecto.

#### Para qué sirve:

1. Automatización de tareas rutinarias (importación/exportación, limpieza, sincronización).
2. Comandos operativos para DevOps/Support.
3. Scripts para migración/backfill de datos.
4. Comandos para CI/CD, staging y ventanas de mantenimiento.

#### Estructura de archivos:

```text
my_app/
  management/
    __init__.py
    commands/
      __init__.py
      recalc_stats.py
```

#### Ejemplo de comando:

```python
from django.core.management.base import BaseCommand
from orders.models import Order

class Command(BaseCommand):
    help = "Recalcula estadísticas agregadas de pedidos"

    def add_arguments(self, parser):
        parser.add_argument("--dry-run", action="store_true")

    def handle(self, *args, **options):
        total = Order.objects.count()
        if options["dry_run"]:
            self.stdout.write(self.style.WARNING(f"DRY RUN: orders={total}"))
            return
        # lógica real
        self.stdout.write(self.style.SUCCESS(f"Done. orders={total}"))
```

Ejecución:

```bash
python manage.py recalc_stats --dry-run
```

#### Cuándo un custom command es la elección correcta:

1. La tarea debe repetirse y ser reproducible.
2. Se necesita acceso al contexto completo de Django (ORM, settings, services).
3. Se necesita un comando controlado para el equipo/CI.

#### Recomendaciones prácticas:

1. Agrega `--dry-run` para validación segura.
2. Haz operaciones idempotentes cuando sea posible.
3. Usa transacciones para cambios batch críticos.
4. Registra progreso y resultados (`self.stdout`, structured logs).
5. Para tareas largas, considera ejecutarlas mediante colas/workers.

#### Errores típicos:

1. Guardar scripts importantes de "one-off" fuera del repositorio.
2. Ejecutar update/delete riesgosos sin dry-run y sin plan de backup.
3. Escribir el comando como un monolito difícil de mantener y sin tests.

#### Conclusión:

Custom management commands son una herramienta estándar de madurez operativa en
Django. Hacen que los procedimientos técnicos sean transparentes, controlables y
aptos para ejecución repetida en un entorno de equipo.

</details>

<details>
<summary>83. ¿Qué son los context processors y cómo se usan?</summary>

#### Django

Los `context processors` son funciones que agregan automáticamente datos al
contexto de cada plantilla (o de ciertas plantillas), para no pasar estas
variables manualmente en cada view.

#### Cómo funciona un context processor:

1. Django llama a la función durante el render de la plantilla.
2. La función devuelve un diccionario.
3. Ese diccionario se añade al template context.

#### Ejemplo:

```python
# core/context_processors.py
def app_meta(request):
    return {
        "APP_NAME": "My Django App",
        "SUPPORT_EMAIL": "support@example.com",
    }
```

Conexión en `settings.py`:

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

Después de esto, en cualquier plantilla:

```django
<footer>{{ APP_NAME }} · {{ SUPPORT_EMAIL }}</footer>
```

#### Cuándo usarlo:

1. Datos globales para el layout (nombre de la app, contactos, feature flags).
2. Datos necesarios en muchas plantillas.
3. Valores ligeros y rápidos, sin cálculos costosos.

#### Cuándo no conviene:

1. Para consultas SQL pesadas en cada render.
2. Para datos muy específicos de una o dos views.
3. Para lógica de negocio compleja.

#### Context processors integrados útiles:

1. `django.template.context_processors.request` (`request` en la plantilla)
2. `django.contrib.auth.context_processors.auth` (`user`, `perms`)
3. `django.contrib.messages.context_processors.messages`
4. `django.template.context_processors.static`
5. `django.template.context_processors.media`

#### Recomendaciones prácticas:

1. Mantén los context processors lo más ligeros posible.
2. Evita duplicar claves que puedan entrar en conflicto con el contexto local.
3. Si los datos son costosos, cachea o pásalos puntualmente desde la view.
4. Documenta las claves globales de contexto para el equipo.

#### Conclusión:

Los context processors son un mecanismo conveniente para datos comunes de
plantillas. Funcionan bien para valores globales ligeros, pero no deben
convertirse en un lugar para lógica de dominio pesada.

</details>

<details>
<summary>84. ¿Cómo funciona el caching en Django? Enfoques principales de caching.</summary>

#### Django

El caching en Django reduce la cantidad de operaciones costosas (SQL, render de
plantillas, cálculos) y acelera las respuestas para el usuario.

#### Cómo funciona:

1. Los datos/la respuesta se guardan en un almacenamiento rápido (Redis/Memcached).
2. Una solicitud repetida obtiene el resultado desde caché, sin recalcular todo.
3. Después del TTL o de la invalidación, el valor se recalcula.

#### Enfoques principales de caching en Django:

1. **Site-wide cache (middleware)**
- Cachea casi toda la respuesta HTTP de las páginas.
- Bueno para contenido público con poca personalización.

2. **Per-view cache (`cache_page`)**
- Cachea una view específica durante un tiempo definido.

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 5)
def article_list(request):
    ...
```

3. **Template fragment cache**
- Cachea una parte de la plantilla, no toda la página.

```django
{% load cache %}
{% cache 300 homepage_sidebar user.id %}
  ...
{% endcache %}
```

4. **Low-level cache API**
- Caching manual de resultados en el código.

```python
from django.core.cache import cache

data = cache.get("popular_products")
if data is None:
    data = expensive_query()
    cache.set("popular_products", data, 300)
```

#### Configuración del backend:

```python
CACHES = {
    "default": {
        "BACKEND": "django.core.cache.backends.redis.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379/1",
    }
}
```

#### Qué enfoque elegir según el caso:

1. Páginas públicas sin personalización -> per-view/site-wide.
2. Páginas parcialmente dinámicas -> fragment cache.
3. Cálculos/agregaciones de dominio costosos -> low-level cache API.

#### Reglas prácticas:

1. Empieza con cache puntual (fragment/per-view), no directamente con site-wide.
2. Define TTL según los requisitos de frescura de datos.
3. Para datos personalizados, añade claves (user id, locale, role).
4. Planifica invalidación de caché después de cambios de datos.

#### Errores típicos:

1. Cachear contenido personalizado sin clave de usuario.
2. No invalidar caché después de update/delete.
3. TTL demasiado largo para datos "vivos".
4. Confiar en caché en vez de optimizar consultas SQL deficientes.

#### Conclusión:

El caching en Django es una estrategia multinivel: desde fragmentos de
plantilla hasta respuestas completas. El mejor resultado lo da la combinación de
backend correcto (normalmente Redis), TTL moderado e invalidación controlada.

</details>

<details>
<summary>85. ¿Cómo optimizar consultas, caching e indexación de BD?</summary>

#### Django

La optimización en Django siempre es integral:  
`consultas ORM` + `caching` + `índices correctos en BD` + `profiling`.
Una técnica aislada rara vez da un resultado estable.

#### 1. Optimización de consultas ORM

1. Evita N+1 mediante:
- `select_related()` para FK/O2O
- `prefetch_related()` para M2M/reverse FK

2. Extrae solo los campos necesarios:
- `values()`, `values_list()`, `only()`, `defer()`

3. Para actualizaciones masivas usa:
- `update()` + `F()` en lugar de `save()` en un bucle

4. Para comprobar existencia:
- `exists()` en lugar de cargar todo el queryset

#### 2. Caching

1. Empieza con fragment/per-view cache.
2. Para cálculos "hot" usa low-level cache API.
3. Para producción normalmente Redis backend.
4. Diseña claves de caché (user/locale/role) e invalidación tras cambios de datos.

#### 3. Indexación de BD

1. Añade índices en campos usados frecuentemente en:
- `WHERE`
- `ORDER BY`
- `JOIN`

2. Usa `models.Index` y `UniqueConstraint` en `Meta`.
3. No indexar "todo": cada índice tiene costo en `INSERT/UPDATE`.

Ejemplo:

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

#### 4. Profiling y medición

1. Usa Django Debug Toolbar en dev/staging.
2. Registra consultas SQL lentas a nivel de BD.
3. Verifica `EXPLAIN ANALYZE` para consultas críticas.
4. Mide latencia p95/p99 antes y después de cambios.

#### Orden típico de optimización:

1. Encontrar el punto lento (no optimizar "a ciegas").
2. Corregir ORM (N+1, campos de más, consultas duplicadas).
3. Añadir/verificar índices.
4. Añadir caché para escenarios consistentemente calientes.
5. Volver a medir el resultado.

#### Errores típicos:

1. Cachear todo sin estrategia de invalidación.
2. Añadir índices sin analizar consultas reales.
3. Optimizar código Python ignorando el cuello de botella SQL.
4. Hacer grandes cambios de esquema en producción sin rollout por etapas.

#### Conclusión:

El rendimiento estable en Django no se logra con "un solo botón", sino con un
enfoque sistemático: medir, optimizar ORM, indexar correctamente la BD y
cachear solo lo que aporta beneficio real bajo carga.

</details>

<details>
<summary>86. ¿Qué es el Django testing framework?</summary>

#### Django

`Django testing framework` es un conjunto integrado de herramientas para probar
modelos, views, formularios, API e integraciones dentro de un proyecto Django.

#### Qué incluye el framework:

1. `django.test.TestCase`: clase base para la mayoría de las pruebas.
2. `Client`: cliente HTTP de pruebas para requests a view/URL.
3. Base de datos de pruebas (se crea automáticamente antes de ejecutar tests).
4. Assertions para response, contexto, redirects y templates.
5. Herramientas para override de settings y aislamiento del entorno.

#### Cómo se ejecutan las pruebas:

```bash
python manage.py test
```

#### Cómo funciona la BD de pruebas:

1. Django crea una test-DB separada.
2. Aplica migraciones/esquema.
3. Cada prueba se aísla transaccionalmente (`TestCase`).
4. Al finalizar, la test-DB se elimina.

#### Clases principales de pruebas:

1. **`TestCase`**
- La opción más común; rápida y aislada para pruebas de ORM/views.

2. **`TransactionTestCase`**
- Cuando se necesita control de transacciones/comportamiento de commit.

3. **`SimpleTestCase`**
- Pruebas sin acceso a la BD.

4. **`LiveServerTestCase`**
- Pruebas de integración/browser con servidor de pruebas levantado.

#### Ejemplo de prueba simple:

```python
from django.test import TestCase
from django.urls import reverse

class HealthViewTests(TestCase):
    def test_health_endpoint_returns_200(self):
        response = self.client.get(reverse("health"))
        self.assertEqual(response.status_code, 200)
```

#### Recomendaciones prácticas:

1. Escribe pruebas para escenarios de negocio críticos, no solo "por coverage".
2. Haz pruebas deterministas (sin dependencia de tiempo/red sin mocks).
3. Separa fábricas/fixtures para una preparación de datos legible.
4. Ejecuta pruebas en CI para cada PR.

#### Errores típicos:

1. Pruebas con dependencia del orden de ejecución.
2. Pruebas demasiado integracionales donde basta nivel unitario.
3. Ignorar edge cases y escenarios negativos.

#### Conclusión:

Django testing framework ofrece infraestructura lista para pruebas confiables
del backend "out of the box". Es la base para refactorización segura y un
proceso de release estable en desarrollo en equipo.

</details>

<details>
<summary>87. ¿Cuál es la diferencia entre pruebas unitarias e integration tests?</summary>

#### Django

Las pruebas `unit` e `integration` se diferencian por el nivel de verificación:

- **Unit test** verifica una parte de lógica aislada.
- **Integration test** verifica la interacción de varios componentes juntos.

#### Pruebas unitarias:

1. Prueban una función/método/clase aislada del resto del sistema.
2. A menudo usan mock/stub para dependencias.
3. Son muy rápidas y precisas para localizar errores.

Ejemplo en Django:

- prueba de validador,
- prueba de función helper,
- prueba de método de servicio sin HTTP/BD real (o con aislamiento mínimo).

#### Integration tests:

1. Verifican varios layers juntos (view + ORM + middleware + templates).
2. A menudo usan test client y test-DB.
3. Son más lentas, pero más cercanas al comportamiento real.

Ejemplo en Django:

- `client.post(...)` -> view -> model save -> redirect -> validación en BD.

#### Diferencias clave:

1. **Velocidad**
- Unit: rápidas.
- Integration: más lentas.

2. **Cobertura**
- Unit: foco estrecho.
- Integration: escenario de sistema más amplio.

3. **Diagnóstico**
- Unit: más fácil encontrar causa puntual.
- Integration: mejor para detectar fallos de integración entre componentes.

#### Ejemplo de pirámide de tests para Django:

1. Muchas pruebas unitarias (validadores, servicios, utilidades).
2. Menos integration tests (endpoints clave, flujos críticos de negocio).
3. Aún menos pruebas end-to-end/browser.

#### Recomendaciones prácticas:

1. Mantén la lógica de dominio crítica bien cubierta con unit tests.
2. Para core user journeys añade integration tests obligatoriamente.
3. No intentes cubrir todo solo con integration tests: es lento y frágil.
4. Cada bug en producción debe terminar en un nuevo test del nivel adecuado.

#### Conclusión:

Unit e integration tests no se sustituyen. Un proyecto Django estable necesita
la combinación: unit para feedback rápido e integration para validar la
interacción real entre componentes.

</details>

<details>
<summary>88. ¿Qué es Django test client?</summary>

#### Django

`Django test client` es una herramienta integrada para simular requests HTTP a
tu aplicación sin ejecutar un navegador real ni un servidor HTTP externo.

#### Qué puede hacer test client:

1. Ejecutar requests `GET`, `POST`, `PUT`, `PATCH`, `DELETE`.
2. Verificar status code, redirects, templates y context.
3. Trabajar con sesión, cookies y autenticación de usuario.
4. Probar la cadena URL -> view -> response.

#### Ejemplo básico:

```python
from django.test import TestCase
from django.urls import reverse

class HomeTests(TestCase):
    def test_home_returns_200(self):
        response = self.client.get(reverse("home"))
        self.assertEqual(response.status_code, 200)
```

#### Ejemplo de request POST:

```python
response = self.client.post(reverse("signup"), {
    "username": "testuser",
    "password1": "StrongPass123!",
    "password2": "StrongPass123!",
})
self.assertEqual(response.status_code, 302)
```

#### Login en pruebas:

1. Login técnico rápido:

```python
self.client.force_login(user)
```

2. Login realista por credenciales:

```python
logged_in = self.client.login(username="testuser", password="secret")
self.assertTrue(logged_in)
```

#### Qué se puede verificar:

1. `response.status_code`
2. `response.context`
3. `response.templates`
4. `assertRedirects(...)`
5. contenido de respuesta (`assertContains(...)`)

#### Limitaciones de test client:

1. No ejecuta JavaScript (no es browser automation).
2. No valida runtime real de frontend como Playwright/Selenium.
3. No modela todos los matices de red del entorno de producción.

#### Recomendaciones prácticas:

1. Usa test client para la mayoría de pruebas de integración web/API en Django.
2. Para flujos JS, añade pruebas e2e/browser separadas.
3. Combínalo con fábricas/fixtures para preparar datos de forma legible.

#### Conclusión:

Django test client es una herramienta rápida y potente para validar el
comportamiento HTTP de la app a nivel backend. Es la opción estándar para probar
views, URL, autenticación e integración básica de componentes.

</details>

<details>
<summary>89. ¿Cómo probar formularios, views y ORM?</summary>

#### Django

En Django, formularios, views y ORM se prueban en distintos niveles, pero con
el mismo estilo: precondiciones claras -> acción -> validación del resultado.

#### 1. Pruebas de formularios

Qué verificar:

1. datos válidos/no válidos
2. errores en campos concretos
3. validación custom (`clean_<field>`, `clean()`)

Ejemplo:

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

#### 2. Pruebas de views

Qué verificar:

1. status code
2. template/context
3. redirects
4. comportamiento de auth/permisos

Ejemplo:

```python
from django.test import TestCase
from django.urls import reverse

class DashboardViewTests(TestCase):
    def test_anonymous_redirected_to_login(self):
        response = self.client.get(reverse("dashboard"))
        self.assertEqual(response.status_code, 302)
```

#### 3. Pruebas de ORM

Qué verificar:

1. creación/actualización/eliminación de modelos
2. métodos custom de manager/queryset
3. relaciones y restricciones (`unique`, `constraints`)

Ejemplo:

```python
from django.test import TestCase
from blog.models import Article

class ArticleORMTests(TestCase):
    def test_create_article(self):
        article = Article.objects.create(title="Test", is_published=True)
        self.assertEqual(Article.objects.count(), 1)
        self.assertTrue(article.is_published)
```

#### Recomendaciones prácticas:

1. Mantén las pruebas independientes entre sí.
2. Usa nombres descriptivos de tests con regla `should_<behavior>`.
3. Para datos de prueba usa factories/fixtures, no setup duplicado.
4. Prueba escenarios negativos con el mismo rigor que los positivos.

#### Qué suele olvidarse:

1. Verificación de permisos a nivel view.
2. Validación de formularios con entradas inesperadas.
3. Comportamiento de métodos manager/queryset con colecciones vacías.

#### Conclusión:

Los formularios prueban validación, las views prueban comportamiento HTTP y el
ORM prueba datos y relaciones. Juntos forman una base de pruebas confiable que
permite refactorizar código Django y lanzar cambios con estabilidad.

</details>

<details>
<summary>90. ¿Cómo usar fixtures?</summary>

#### Django

`Fixtures` en Django son datos preparados de antemano (JSON/YAML/XML) que se
pueden cargar en la BD para tests, demos o seed inicial.

#### Para qué se usan fixtures:

1. Levantar rápido un conjunto estándar de datos.
2. Reproducir el mismo estado de prueba en distintos entornos.
3. Probar escenarios con registros relacionados "realistas".

#### Ejemplo de archivo fixture:

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

Ubicación:

- `app/fixtures/articles.json` (opción típica)

#### Carga de fixture:

```bash
python manage.py loaddata articles.json
```

#### Uso en tests:

```python
from django.test import TestCase
from blog.models import Article

class ArticleTests(TestCase):
    fixtures = ["articles.json"]

    def test_fixture_loaded(self):
        self.assertEqual(Article.objects.count(), 1)
```

#### Cuándo fixtures son adecuadas:

1. Conjunto pequeño y estable de datos de referencia.
2. Integration tests con relaciones complejas.
3. Carga demo/local para entornos de review.

#### Limitaciones de fixtures:

1. Frágiles cuando cambia el esquema de modelos.
2. JSON grandes son más difíciles de leer y mantener.
3. Más difícil combinar datos con flexibilidad para distintos tests.

#### Alternativa práctica:

- Para la mayoría de tests es mejor usar factories (factory_boy, model_bakery), porque:
1. Los datos se generan por código.
2. Es más fácil adaptarse a cambios de modelo.
3. Menos archivos estáticos "mágicos".

#### Enfoque recomendado de tech lead:

1. Datos compartidos pequeños -> fixtures.
2. La mayoría de unit/integration tests -> factories.
3. No mezclar ambos enfoques de forma caótica sin reglas claras de equipo.

#### Conclusión:

Las fixtures en Django son útiles para un set de datos inicial estable, pero
para sets de prueba flexibles y de largo plazo normalmente son más eficaces los
enfoques basados en factories.

</details>

<details>
<summary>91. ¿Cómo funcionan async views y async ORM en Django?</summary>

#### Django

Django soporta views asíncronas (`async def`) y desarrolla gradualmente un
stack async para escenarios con alta carga de I/O. El principal valor de async
es una mejor escalabilidad con muchas esperas simultáneas (APIs externas,
operaciones de red).

#### Async view en Django:

```python
from django.http import JsonResponse

async def async_health(request):
    return JsonResponse({"status": "ok"})
```

#### Cuándo async realmente es útil:

1. Muchas esperas de I/O (requests HTTP a servicios externos).
2. Patrones long-polling/websocket (con el stack correspondiente).
3. Alta concurrencia de requests con lógica CPU relativamente ligera.

#### Sync vs Async en Django:

1. `def view(...)` -> view síncrona.
2. `async def view(...)` -> view asíncrona.
3. Django puede adaptar fronteras sync/async, pero transiciones innecesarias añaden overhead.

#### Trabajo con BD (ORM):

- Históricamente el ORM fue sync-first.
- En versiones modernas de Django existen variantes async de parte de las operaciones (`aget`, `acreate`,
  `aupdate_or_create`, iteración async, etc.), pero hay que considerar
  compatibilidad de versión y driver de BD.

Ejemplo:

```python
user = await User.objects.aget(pk=user_id)
```

#### Limitaciones importantes:

1. No todas las librerías de terceros tienen API async-safe.
2. Async no acelera tareas CPU-bound (para eso: workers/colas/procesos).
3. Mezclar ORM sync en código async puede bloquear el event loop.

#### Recomendaciones prácticas:

1. Usa async donde exista un cuello de botella real de I/O.
2. Si el stack es mayormente sync, no fuerces async "por moda".
3. Minimiza transiciones sync<->async.
4. Para CPU en segundo plano/procesamiento largo usa Celery/RQ, no `await` en la view.

#### Errores típicos:

1. Esperar mejora de rendimiento sin cambiar el perfil I/O de la app.
2. Hacer llamadas sync bloqueantes dentro de async views.
3. No probar comportamiento bajo carga concurrente.

#### Conclusión:

Async en Django es una herramienta potente para escenarios I/O-heavy, pero no
es una panacea universal. La eficiencia depende de la coherencia de todo el
stack: views, ORM, clientes externos y perfil real de carga.

</details>

<details>
<summary>92. ¿Cómo crear tareas backend (@task, Celery)?</summary>

#### Django

Las tareas backend (background jobs) en Django se usan para operaciones pesadas
o diferidas que no conviene ejecutar dentro del request HTTP: envío de emails,
importaciones, generación de archivos, integraciones, reintentos.

#### Stack más común:

- **Celery** + broker (normalmente Redis o RabbitMQ) + workers

#### Arquitectura básica:

1. El código Django coloca una tarea en la cola.
2. El broker almacena el mensaje.
3. El worker de Celery toma la tarea y la ejecuta de forma asíncrona.
4. (Opcional) el resultado se guarda en el result backend.

#### Ejemplo de tarea:

```python
# app/tasks.py
from celery import shared_task

@shared_task
def send_welcome_email(user_id):
    # lógica de envío de email
    return {"user_id": user_id, "status": "sent"}
```

Llamada desde view/servicio:

```python
send_welcome_email.delay(user.id)
```

#### Integración mínima de Celery con Django:

1. Instalar:
```bash
pip install celery redis
```
2. Añadir `celery.py` en la configuración del proyecto.
3. Definir broker URL en settings/env.
4. Ejecutar worker:
```bash
celery -A config worker -l info
```

#### Tareas periódicas:

- Con `celery beat` o `django-celery-beat` (scheduler tipo cron).

#### Recomendaciones prácticas:

1. Las tareas deben ser **idempotentes** (re-ejecución no rompe datos).
2. Agrega `retry` para fallos temporales (red, APIs externas).
3. No pases objetos "pesados" a la tarea: pasa `id` y recupera datos en el worker.
4. Registra estado de ejecución y errores.
5. Define timeouts y límites de concurrencia de workers.

#### Errores típicos:

1. Ejecutar operaciones largas directamente en la view en vez de usar cola.
2. Falta de retry/policy en integraciones con servicios externos.
3. Duplicados inesperados por lógica no idempotente.
4. Falta de monitoreo de colas y tareas "atascadas".

#### Conclusión:

Celery en Django es el estándar para procesamiento asíncrono de tareas backend.
La clave de fiabilidad: idempotencia, reintentos, monitoreo y separación clara
entre HTTP-flow y procesamiento en background.

</details>

<details>
<summary>93. ¿Qué es Django REST Framework?</summary>

#### Django

**Django REST Framework (DRF)** es un framework popular sobre Django para
construir REST API: serialización de datos, validación, autorización, routing,
paginación y una interfaz browsable API conveniente.

#### Para qué se usa DRF:

1. Construir rápidamente APIs estables para clientes web/mobile.
2. Estandarizar validación y formato de respuestas.
3. Controlar con flexibilidad auth/permissions/throttling.
4. Reducir boilerplate frente a views con JsonResponse "puro".

#### Componentes clave de DRF:

1. **Serializer**
- Convierte modelo/objeto <-> JSON.
- Ejecuta validación de datos de entrada.

2. **APIView / GenericAPIView / ViewSet**
- Capas para construir lógica de endpoints.

3. **Routers**
- Generación automática de URL para ViewSet.

4. **Authentication / Permissions**
- Control de quién eres y qué puedes hacer.

5. **Pagination / Filtering / Ordering**
- Mecanismos listos para listas y búsqueda.

#### Ejemplo de serializer:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Ejemplo de ViewSet:

```python
from rest_framework.viewsets import ModelViewSet
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
```

#### Ejemplo de router:

```python
from rest_framework.routers import DefaultRouter
from .views import ArticleViewSet

router = DefaultRouter()
router.register("articles", ArticleViewSet, basename="article")
urlpatterns = router.urls
```

#### Cuándo DRF es especialmente adecuado:

1. Se necesita un producto API-first o multi-cliente.
2. Hay requisitos complejos de permisos/paginación/filtrado.
3. Se necesita arquitectura API escalable y formato de error estandarizado.

#### Conclusión:

DRF es el estándar de facto para API en el ecosistema Django. Añade una
arquitectura API estructurada, acelera el desarrollo y simplifica el soporte de
endpoints en producción.

</details>

<details>
<summary>94. ¿Qué es la serialización y para qué se necesita?</summary>

#### Django

La serialización es la conversión de objetos Python/modelos a un formato de
intercambio de datos (normalmente JSON), y la deserialización es la conversión
inversa a objetos con validación.

#### Para qué se necesita serialización:

1. Transferir datos entre backend y clientes frontend/mobile.
2. Estandarizar el formato de respuestas API.
3. Validar datos de entrada antes de guardar en BD.
4. Separar el modelo de BD del contrato externo del API.

#### Serialización en DRF:

- Se realiza con `Serializer` o `ModelSerializer`.

Ejemplo:

```python
from rest_framework import serializers
from .models import Article

class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ["id", "title", "is_published", "created_at"]
```

#### Conversión model -> JSON:

```python
article = Article.objects.first()
data = ArticleSerializer(article).data
```

#### Conversión JSON -> validated data/model:

```python
payload = {"title": "New", "is_published": True}
serializer = ArticleSerializer(data=payload)
serializer.is_valid(raise_exception=True)
obj = serializer.save()
```

#### Qué más aporta serializer:

1. Verificación de tipos y campos obligatorios.
2. Validación custom (`validate_<field>`, `validate`).
3. Control de campos read-only/write-only.
4. Serializadores anidados para entidades relacionadas.

#### Recomendaciones prácticas:

1. No expongas el modelo "tal cual" sin contrato explícito de serializer.
2. Mantén el esquema API estable y backward-compatible.
3. Valida reglas de negocio custom en serializer o en capa de servicios.
4. Para distintos use-cases crea serializers separados (list/detail/create/update).

#### Conclusión:

La serialización es el núcleo de la capa API en Django/DRF: define formato de
datos, validación y estabilidad del contrato entre servidor y clientes.

</details>

<details>
<summary>95. ¿Qué características tiene Django con el framework REST (DRF)?</summary>

#### Django

Django + DRF es una combinación de un framework web maduro y una capa API
potente. Encaja bien en servicios REST de producción con modelo de dominio claro.

#### Características clave de DRF en el ecosistema Django:

1. **Enfoque serializer-first**
- Contrato API claro, validación de entrada, control de campos.

2. **Construcción flexible de endpoints**
- `APIView`, `GenericAPIView`, `ViewSet`, `ModelViewSet`.

3. **Routing automático**
- Routers reducen significativamente el boilerplate para CRUD API.

4. **Auth + permissions**
- Session, Token, JWT (vía paquetes), clases de permisos custom.

5. **Pagination, filtering, ordering**
- Mecanismos listos para listados en sistemas grandes.

6. **Throttling**
- Límite de frecuencia de requests (anti-abuse / higiene API).

7. **Content negotiation**
- Soporte de distintos renderer/parser (JSON por defecto).

8. **Browsable API**
- Interfaz dev conveniente para validar endpoints manualmente.

#### Stack típico de producción con DRF:

1. API versionada (`/api/v1/...`).
2. Serializers por escenario (`list/detail/create/update`).
3. Política de permisos por endpoint.
4. Formato de errores estandarizado.
5. Paginación + filtrado + indexación de BD.

#### Fortalezas del enfoque:

1. Alta velocidad de desarrollo sin perder estructura.
2. Compatibilidad con Django auth/admin/ORM/migrations.
3. Fácil de ampliar con clases custom para requisitos de negocio.

#### A qué prestar atención:

1. No sobrecargar `ModelViewSet` con lógica de dominio compleja.
2. Controlar consultas N+1 en serializer/viewset.
3. Separar claramente contrato API y modelo de datos interno.

#### Conclusión:

DRF convierte Django en un framework API sólido de nivel enterprise: inicio
rápido, arquitectura estructurada, seguridad madura y escalabilidad para
productos multi-cliente reales.

</details>

<details>
<summary>96. ¿Qué lugar ocupa Django en la arquitectura de servicios y REST API?</summary>

#### Django

En arquitectura moderna, Django normalmente ocupa el rol de **backend principal de negocio**:
gestiona lógica de dominio, datos transaccionales, procesos administrativos y REST API
para clientes web/mobile.

#### Roles típicos de Django en arquitectura:

1. **Monolito modular (lo más común)**
- Un servicio con descomposición clara en apps/domínios.
- Desarrollo rápido del producto y contorno operativo más simple.

2. **Servicio API (DRF)**
- Backend puro para SPA/mobile/integraciones de partners.

3. **Servicio core en ecosistema de microservicios**
- Django como "source of truth" para dominios críticos (usuarios, billing, pedidos).

4. **Servicio Backoffice/Admin**
- Circuito interno de operaciones y gestión de datos vía Django Admin + custom UI.

#### Por qué Django encaja bien en este rol:

1. Desarrollo rápido de todo el ciclo backend.
2. ORM sólido + modelo transaccional.
3. Sistema maduro de auth/permissions.
4. DRF para API estandarizada.
5. Admin confiable para equipos operativos.

#### Dónde Django puede no ser la primera elección ideal:

1. Servicios API-only ultraligeros de alta concurrencia (a veces FastAPI encaja mejor).
2. Escenarios low-latency muy específicos con overhead mínimo de framework.

#### Enfoque arquitectónico práctico:

1. Empezar con monolito Django con límites de dominio claros.
2. Extraer servicios separados solo con necesidad real de escalado.
3. Mantener Django como nodo core de domain/API/admin.

#### Integración con otros servicios:

- Celery/colas para async processing
- Redis para caché
- Motor de búsqueda para full-text
- Object storage/CDN para media
- Stack de observabilidad (logs, metrics, tracing)

#### Conclusión:

Django ocupa una posición fuerte como backbone de servicios de negocio y REST API.
En la mayoría de productos es un compromiso práctico entre velocidad de desarrollo,
disciplina arquitectónica y mantenibilidad a largo plazo.

</details>

<details>
<summary>97. ¿Cómo desplegar un proyecto Django (WSGI, ASGI, Nginx)?</summary>

#### Django

El deploy de Django en producción normalmente se construye así:

1. **Nginx** - reverse proxy, static/media, TLS.
2. **App server** - Gunicorn (WSGI) o Uvicorn/Daphne (ASGI).
3. **Django app** - lógica de negocio.
4. **PostgreSQL/Redis** - datos y caché/colas.

#### WSGI vs ASGI:

1. **WSGI (Gunicorn)**
- Variante clásica y estable para apps Django sync.

2. **ASGI (Uvicorn/Daphne)**
- Necesario para async views, websocket y escenarios async modernos.

#### Flujo mínimo de producción:

1. Preparar entorno:
- `DEBUG=False`
- `ALLOWED_HOSTS`
- secretos vía env

2. Instalar dependencias:
```bash
pip install gunicorn
```

3. Recopilar static:
```bash
python manage.py collectstatic --noinput
```

4. Aplicar migraciones:
```bash
python manage.py migrate
```

5. Iniciar app server:
```bash
gunicorn config.wsgi:application --bind 127.0.0.1:8000 --workers 4
```

#### Ejemplo Nginx (simplificado):

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

#### Para deploy ASGI:

```bash
uvicorn config.asgi:application --host 127.0.0.1 --port 8000 --workers 4
```

#### Checklist obligatorio de security/ops:

1. HTTPS (Let’s Encrypt), cookies seguras.
2. `CSRF_TRUSTED_ORIGINS` y proxy headers correctos.
3. `SECURE_HSTS_SECONDS`, `SECURE_SSL_REDIRECT`, `X_FRAME_OPTIONS`.
4. Logs, monitoreo, alertas (error rate, latency, salud de BD).
5. Backup y plan de rollback validado.

#### Errores típicos:

1. `DEBUG=True` en producción.
2. Falta de `collectstatic` antes del release.
3. `ALLOWED_HOSTS` / proxy headers incorrectos -> problemas CSRF/redirect.
4. Ejecutar servidor de desarrollo Django (`runserver`) en producción.

#### Conclusión:

Un deploy Django estable es Nginx + app server WSGI/ASGI + configuración
correcta de seguridad y observabilidad de producción. Técnicamente no es
complejo si hay disciplina de proceso de release.

</details>

<details>
<summary>98. ¿Cómo escalar una aplicación Django?</summary>

#### Django

Escalar Django no es un solo paso, sino una secuencia de decisiones a nivel de
código, BD, caché, colas e infraestructura. La mejor estrategia es escalar con
base en métricas, no "por si acaso".

#### 1. Optimización de aplicación (primera etapa)

1. Eliminar consultas N+1 (`select_related`, `prefetch_related`).
2. Optimizar endpoints pesados (pagination, límites, índices).
3. Minimizar payload API/HTML.
4. Agregar caché donde haya requests repetitivas "calientes".

#### 2. Caché y aceleración de lectura

1. Redis para low-level/per-view/fragment cache.
2. CDN para static/media.
3. Headers HTTP-cache para recursos públicos.

#### 3. Escalado horizontal a nivel app

1. Ejecutar varias instancias Django detrás de load balancer.
2. Procesos stateless (sesiones en Redis/BD, sin estado local).
3. Autoscaling basado en CPU/RPS/latency.

#### 4. Mover tareas pesadas a background

1. Celery/RQ para jobs asíncronos.
2. Colas para email, reportes, integraciones, importaciones.
3. Retry/backoff e idempotency para confiabilidad.

#### 5. Escalado de BD

1. Índices y query tuning.
2. Connection pooling (PgBouncer).
3. Read replicas para escenarios read-heavy.
4. Partitioning/sharding solo con necesidad real y arquitectura clara.

#### 6. Evolución arquitectónica

1. De "monolito sin límites" -> monolito modular.
2. Si hace falta, extraer dominios puntuales a servicios separados.
3. No fragmentar en microservicios prematuramente.

#### 7. Observabilidad como condición de escalado

1. Métricas: p95/p99 latency, error rate, queue lag, DB locks.
2. Logs con request-id.
3. Tracing entre servicios/colas.
4. Alertas ante violaciones SLA/SLO.

#### Errores típicos:

1. Escalar infraestructura sin optimizar queries.
2. Cachear sin estrategia de invalidación.
3. Ignorar el cuello de botella de BD.
4. Complejidad prematura de microservicios.

#### Conclusión:

Escalar Django es un proceso controlado: primero optimizar código y BD,
después agregar caché y colas, luego escalar horizontalmente instancias app, y
solo después complejizar arquitectura. Las métricas deben guiar todas las decisiones.

</details>

<details>
<summary>99. ¿Qué enfoques existen para deploy y monitoreo de una app Django?</summary>

#### Django

Una producción confiable en Django se sostiene sobre dos pilares:

1. **deploy gestionado**
2. **monitoreo completo (observabilidad)**

#### Enfoques de deploy:

1. **Deploy clásico en VM/VPS**
- Nginx + Gunicorn/Uvicorn + systemd + PostgreSQL/Redis.
- Adecuado para entorno self-hosted controlado.

2. **Container-based (Docker/Kubernetes)**
- Entorno predecible, escalado vía réplicas.
- Conveniente para equipos con procesos DevOps.

3. **Plataformas PaaS/Managed**
- Arranque más rápido, menos costo operativo.
- Compromiso en flexibilidad de infraestructura.

#### Pipeline de release recomendado:

1. CI: tests + linters + security checks.
2. Build de artifact inmutable (image).
3. Deploy a staging.
4. Smoke/health checks.
5. Production rollout (blue/green, rolling o canary).
6. Rollback automático ante degradación.

#### Qué monitorear obligatoriamente:

1. **Application metrics**
- RPS, p95/p99 latency, tasa de error 4xx/5xx.

2. **Infrastructure metrics**
- CPU, RAM, disk, network, tasa de restart de pod/container.

3. **Database metrics**
- slow queries, locks, conexiones, replication lag.

4. **Queue/worker metrics**
- queue depth, task latency, retry/failure rate.

5. **Logs + tracing**
- structured logs, request-id, distributed tracing.

#### Set mínimo de producción:

1. Health endpoints (`/health/live`, `/health/ready`).
2. Logs centralizados (ELK/Loki/Cloud logs).
3. APM/metrics (Prometheus + Grafana, Datadog, New Relic, Sentry).
4. Alertas por violación de SLO, no solo por "servidor caído".

#### Recomendaciones prácticas:

1. Implementa runbook para incidentes (quién, qué, cómo recupera).
2. Mantén migraciones backward-compatible para releases zero/min-downtime.
3. Automatiza secretos y config vía env/secret manager.
4. Entrena rollback y disaster recovery regularmente.

#### Errores típicos:

1. Deploy sin health checks ni estrategia de rollback.
2. Monitoreo solo de CPU sin métricas de negocio y latency.
3. Sin vínculo entre logs y request/trace id.
4. "Hot fixes" manuales en servidor sin reproducir en código.

#### Conclusión:

Un deploy Django exitoso es un proceso CI/CD predecible, y una operación estable
requiere monitoreo que detecte degradación de forma temprana. Sin observabilidad,
incluso buen código pierde control rápidamente en producción.

</details>

<details>
<summary>100. ¿Qué cambios suelen incluir los patch releases y por qué es importante actualizar?</summary>

#### Django

Los patch releases (por ejemplo, `5.1.2 -> 5.1.3`) normalmente incluyen fixes
**backward-compatible** sin cambios de API pública que rompan la app a nivel major/minor.

#### Qué suele incluir un patch release:

1. **Security fixes**
- Cierre de vulnerabilidades (a menudo crítico para producción).

2. **Bug fixes**
- Correcciones de errores en ORM, forms, middleware, admin, migrations, etc.

3. **Stability improvements**
- Mejor compatibilidad con dependencias, fixes de edge-cases.

4. **Mejoras menores de docs/tests**
- Sin cambios en el contrato arquitectónico de la app.

#### Por qué es importante actualizar:

1. **Seguridad**
- Omitir un security patch puede dejar una vulnerabilidad conocida en producción.

2. **Confiabilidad**
- Los patch releases eliminan bugs que pueden aparecer bajo carga.

3. **Compatibilidad**
- Librerías actuales esperan versiones patch al día del framework.

4. **Camino de upgrade más simple**
- Actualizaciones pequeñas y regulares son más fáciles que "saltos grandes" esporádicos.

#### Proceso práctico de actualización:

1. Actualizar dependencia (`pip`/`poetry`/`uv`).
2. Ejecutar tests y linters.
3. Revisar changelog/release notes.
4. Desplegar en staging.
5. Lanzar a producción mediante rollout controlado.

#### Frecuencia:

- Revisar patch updates regularmente (mínimo mensual o tras security advisory).
- Para versiones LTS, aplicar security patches lo antes posible.

#### Errores típicos:

1. Posponer patch updates "para después".
2. Actualizar en producción sin validación staging/CI.
3. Ignorar release notes y posibles side effects.

#### Conclusión:

Los patch releases no son "cosmética", son higiene operativa del proyecto.
Actualizar Django regularmente reduce riesgos de seguridad, mejora estabilidad y
hace predecibles los upgrades futuros.

</details>
