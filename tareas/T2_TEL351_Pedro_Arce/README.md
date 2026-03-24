* **Relevancia temática**: ¿Qué temas (o comunidades) dominan el corpus? ¿Cómo los identificaste?





Los temas dominantes, a partir de términos, títulos y la posición en el layout:



-Política chilena (partidos, ministerios, figuras): alta densidad interna porque comparten muchas PERSON/ORG (ej: partidos + autoridades).



-Fútbol nacional (Colo Colo, U. de Chile, jugadores/estadios): comunidad muy cohesiva; repite ORG/LOC de clubes y recintos, elevando similitudes.



-Clima/territorio (frentes, lluvias + GPE/LOC regionales): cluster territorial que crece por co-mención de ciudades/regiones.



-Bloques medianos: beneficios/Fiestas Patrias/economía doméstica (instituciones + términos sociales) y tecnología/IA (marcas globales).



A cada noticia se le extraen entidades (PERSON/ORG/LOC) y se construye un grafo no dirigido y ponderado donde el peso entre dos noticias es su similitud (Jaccard sobre entidades). Luego, se aplica Louvain ponderado sobre ese grafo (τ≈0.20; N≈180, E≈638, grado prom.≈7.1, modularidad≈0.44) para, finalmente, etiquetar cada comunidad con los 5 términos/entidades más frecuentes de sus noticias (a partir de features\_t2.json).



Con esto, los temas con entidades icónicas y repetidas (clubes, partidos, ministerios, marcas) generan similitudes altas, crecen en Louvain y aparecen como comunidades dominantes.









* **Noticias/Agentes influyentes**: ¿Qué noticias resultan más influyentes según diferentes centralidades? ¿Coinciden o difieren? ¿Por qué?





-PageRank (ponderado) y Strength (suma de pesos):

Destacan las noticias más representativas del bloque político y del fútbol: están rodeadas de muchas noticias similares y, además, conectadas a nodos que también son fuertes. Suelen coincidir con Degree cuando el tema es grande y homogéneo.



-Betweenness (intermediación):

Resalta notas “bisagra” que mezclan entidades de comunidades distintas (p.ej., clima + gobierno/servicios, beneficios + ministerios + ciudades, IA + políticas públicas). Aunque no sean las más populares dentro de su cluster, son estratégicas porque unen bloques del grafo.



-Closeness (cercanía):

Favorece piezas ubicadas en el centro funcional de la componente gigante: quizá no tienen el mayor degree, pero quedan a pocos “saltos” del resto cuando medimos distancia como 1/similitud.



Coinciden (PR/strength/degree) al señalar el núcleo del tema: noticias muy conectadas dentro de su comunidad.



Difieren cuando miramos betweenness (aparecen puentes entre temas) y, en menor medida, closeness (nodos céntricos en la malla global, no necesariamente los más populares).



