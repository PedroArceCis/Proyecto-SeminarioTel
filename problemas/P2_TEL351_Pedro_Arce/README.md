---

### Problema 2 — Dinámicas de Opinión y Polarización en Redes Sociales durante una Crisis Nacional

---

**Curso:** TEL351: Seminario de Telemática

**Autor:** Pedro Arce

---

### Descripción

Este proyecto analiza la conversación en línea sobre el apagón eléctrico nacional ocurrido en Chile en febrero de 2025 a partir de datos de Reddit (principalmente del subreddit r/chile).

El objetivo es estudiar:

- El tono emocional de la discusión (opiniones negativas, neutras y positivas) mediante análisis de sentimientos.

- La estructura de la red de interacciones entre usuarios (quién responde a quién) y la formación de comunidades con posturas similares.

- La dinámica de opinión sobre esa red utilizando modelos de dinámica de opinión (en particular, el modelo de DeGroot), para evaluar si el sistema tiende al consenso, a la polarización o a la fragmentación.

- El efecto de intervenciones en la red (eliminar o reforzar conexiones entre comunidades) y las implicancias sociales y éticas de estos resultados en el contexto de desinformación y radicalización en plataformas digitales.

---

### Dependencias técnicas y librerías necesarias

El proyecto está desarrollado en Python 3 y se ejecuta en un Jupyter Notebook. Las principales dependencias son:

Jupyter: 

- *jupyter* o *jupyterlab* para ejecutar el notebook (todo esto ha sido trabajado a través de Google Colab).

Manejo y análisis de datos:

- *pandas*
- *numpy*

Análisis de redes:

- *networkx*

Visualización:

- *matplotlib*

Análisis de sentimientos en español:

- *pysentimiento*
- (y sus dependencias de modelos de transformadores, típicamente gestionadas automáticamente por la propia librería)

Opcionalmente, según el entorno:

- *tqdm* (para barras de progreso, si se usan)
- *random / itertools* (incluidas en la librería estándar de Python)

Instalación básica recomendada (ejemplo):


```
pip install jupyter pandas numpy networkx matplotlib pysentimiento
```

(Instalación de todo está considerado en la primera celda del archivo Jupyter Notebook)

---

### Instrucciones de ejecución

Teniendo todas las consideraciones anteriores cubiertas y los archivos ".json" de los hilos de Reddit dentro de la carpeta "/data" en la raíz donde mismo se ubica el archivo Jupyter Notebook, carpeta incluida en este trabajo, se puede proceder a ejecutar todas las celdas en una sesión sin problema:

1. Ubicar este proyecto en una **carpeta local** de tu elección.

2. **Ubicar los datos de Reddit:** Asegurarse de que los archivos `.json` de los hilos de Reddit relacionados con el apagón estén en la carpeta:

   ```text
   /data
   ```

   ubicada en la **misma raíz** donde está el archivo del Jupyter Notebook.
   La estructura mínima debería verse así:

   ```
   proyecto/
   ├─ data/
   │  ├─ apagon_thread1.json
   │  ├─ apagon_thread2.json
   │  ├─ apagon_thread3.json
   │  └─ apagon_thread4.json
   └─ P2_TEL351_Pedro_Arce.ipynb   (nombre de tu notebook)
   ```

3. **Crear entorno e instalar dependencias:**
   (Opcional pero recomendado)

   ```
   python -m venv venv
   source venv/bin/activate    # En Windows: venv\Scripts\activate
   ```

   ```
   pip install jupyter pandas numpy networkx matplotlib pysentimiento
   ```

4. **Abrir Jupyter Notebook:**

   ```
   jupyter notebook
   ```

   Luego abre el archivo del notebook (por ejemplo `P2_TEL351_Pedro_Arce.ipynb`).

5. **Ejecutar todas las celdas:**

   Con las dependencias instaladas y los `.json` en `/data`, se pueden ejecutar todas las celdas en orden:

   * Desde el menú: **Kernel → Restart & Run All**
   * O ejecutando cada celda manualmente (Shift+Enter).

   El notebook realizará de forma secuencial:

   * Carga y preprocesamiento de datos.
   * Análisis de sentimientos.
   * Construcción de la red y detección de comunidades.
   * Simulaciones de dinámica de opinión y visualizaciones.

---

### Consideraciones

- Los archivos incluidos en la carpeta "/data" pueden ser reemplazados igualmente por otros hilos de Reddit siguiendo el formato "apagon_threadX.json".

- De igual forma, se dejan los archivos .csv generados durante el testeo del código en la carpeta 'ejemplo csv resultados' en caso de que quieran ser revisados.

---