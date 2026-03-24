**Problema 1 — Difusión y Bots en X (Elecciones Presidenciales Chile 2025)**

Curso: TEL351
Autor: Pedro Arce Cisternas

**Descripción**

Se construye un pipeline reproducible para:

- Extraer publicaciones de X/Twitter relacionadas con las elecciones presidenciales de Chile 2025, centrado en candidatos y contexto electoral chileno.

- Procesar hilos completos (tweet principal + respuestas + citas) y etiquetar señales de desinformación mediante heurísticas (“fraude”, “actas adulteradas”, etc.) y desmentidos (“falso”, “fact-check”, …).

- Exportar dos datasets listos para análisis posterior:
election_posts_candidates.csv → universo de publicaciones recolectadas.
tweets_fake_candidates.csv → subconjunto filtrado con señales “fake”.

- El scraping prioriza estabilidad (Playwright), comportamiento humano básico (pausas/scroll), y soporte opcional de cookies de sesión para mejorar cobertura en X.

**Dependencias técnicas**

Requisitos mínimos

- Python 3.10+
- SO: Linux / macOS / Windows
- Conexión a Internet
- Algún medio para poder ejecutar un archivo Jupyter Notebook (Visual Studio, Google Colab, etc)

**Librerias necesarias**

De terceros (instalables con pip):

pandas
numpy
networkx
matplotlib
playwright
nest_asyncio
community (paquete: python-louvain)
pyvis

Biblioteca estándar de Python:

os
re
collections
itertools
json
unicodedata
asyncio
csv
datetime
html
importlib
math
pathlib
random
subprocess
sys
time
urllib
zipfile

(Instalación de todas está considerada en la primera celda del archivo Jupyter Notebook)

**Instrucciones de ejecución**

Teniendo todas las consideraciones anteriores cubiertas y el archivo 'cookies.json', incluido en este trabajo, en la raíz donde mismo se ubica el archivo
Jupyter Notebook, se puede proceder a ejecutar todas las celdas en una sesión sin problema. (De igual forma, se dejan los archivos generados en el testeo durante el testeo del código en la carpeta 'Jupyter files example' en caso de que quieran ser revisados).


**Consideraciones**

- Contexto horario configurado a `America/Santiago`.
- Uso académico. Revisar Términos de X y respetar límites de tráfico; evitar almacenar datos sensibles.

**Troubleshooting**

- Playwright/Chromium no instalado:
python -m playwright install chromium

- Tiempos de espera o pocos resultados:
subir MAX_TWEETS; bajar MIN_RETWEETS/MIN_REPLIES a 0; ampliar SINCE_DAYS; usar SEARCH_SOURCES = ["live","top"]; correr con cookies.

- CSV vacío: relajar filtros (mantener STRICT_CANDIDATE_ONLY=True sólo para el principal y APPLY_KEYWORDS_ON_REPLIES=False); 
confirmar que aparecen article en la búsqueda; si la query es muy larga, dividir candidatos por lotes.

- Rate limiting (429) o “Something went wrong”: reducir CONCURRENCY (p. ej., 2); aumentar pausas; usar cookies válidas; evitar sesiones paralelas.

- No hay pestaña de “Citas”: X la oculta si no existen citas; es normal.

- Recaptcha / login constante: generar cookies.json con headless=False e iniciar sesión; luego volver a headless=True.

- Acentos/ñ mal en Excel: abrir como UTF-8 (en Windows, Datos → Desde texto/CSV).
