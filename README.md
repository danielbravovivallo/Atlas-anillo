Atlas CD — primera entrega
Mapa navegable de cartas de resoluciones Column–Diamond para
$M = R/(x_1)$ sobre $R = k[x_1,\dots,x_n]/I$, con $I$ ideal monomial
cuadrático y $|I| \le 3$, $n \le 5$, módulo la simetría $S_{n-1}$ que fija $x_1$.
Qué hay en este paquete
archivo	qué es
`atlas-bundle.html`	SPA único, autocontenido. Abrir directamente con doble click — no requiere servidor. Cytoscape se carga desde CDN al primer abrir.
`atlas.html` + `atlas.json` + `cd-core.js`	Versión modular para publicar en Netlify (Cytoscape vía CDN, datos vía `fetch`).
`cd-core.js`	Núcleo CD con el fix del signo en dos fases. Reutilizable en Node y en navegador (`window.CDCore`).
`enumerate.js`	Regenera `atlas.json` desde cero. `node enumerate.js`.
`tests.js`	Suite con nueve casos canónicos ($n{=}1$ trivial, periódico $x_1^2$, Fibonacci, cubo, línea mixta, abanico, etc.). `node tests.js`.
`PATCH_column_diamond.md`	Tres reemplazos puntuales para aplicar al `column-diamond.html` existente sin tocar la UI.
Verificación incluida
Suite de nueve casos canónicos: PASS (Betti correctos contra valores conocidos).
Las 139 cartas del catálogo se construyen sin excepción y satisfacen $d\circ d = 0$.
La verificación de cancelación se hace simbólicamente: para cada par de
caminos componibles $p \to q \to r$ con $x_i x_j \notin I$, la suma de
coeficientes signados es cero.
Cómo está construido el mapa
Posición de cada carta: eje horizontal por $n$, eje vertical por $|I|$,
con jitter intra-bin para distinguir.
Color por familia: fan-at-$x_1$, fan, path-like, squares-only, mixed, free.
Aristas:
subideal — dos cartas en el mismo $n$ que difieren por un generador.
embed — la misma $I$ vista en $k[x_1,\dots,x_{n+1}]$ (extensión por una
variable extra). Mostrada en punteado ámbar.
Limitaciones conscientes de esta versión
La canonicalización por $S_{n-1}$ es por fuerza bruta. Para $n = 5$, $|S_4|=24$,
todavía es trivial; para $n \ge 6$ habría que cambiar a una invariante combinatoria.
La familia mixed es un cajón de sastre. Se puede refinar más adelante
(Koszul puro, complete intersection, etc.).
No se computa todavía la serie de Poincaré como función racional explícita
ni se identifica el periodo $p$ — se reporta la sucesión Betti, suficiente
como punto de partida.
Las aristas por misma familia no están como aristas del grafo;
se infieren visualmente por color. Si más adelante quieres aristas explícitas
por familia, basta añadirlas en `enumerate.js`.
Próximos pasos naturales
Aplicar `PATCH_column_diamond.md` al visualizador interactivo para que
también tenga el signo corregido.
Refinar el grafo: añadir aristas por isomorfismo de grafo asociado
(los ideales squarefree cuadráticos ↔ grafos simples). Esto da la
identificación combinatoria que el Atlas necesita para conectar
familias entre $n$.
Calcular la serie de Poincaré donde se conozca su forma cerrada
y enriquecer cada carta con el polinomio mínimo del denominador.
Sembrar el Atlas con las animaciones de Manim que ya tienes
(n=1 Koszul vs CD, escalera puro-columna, primer diamante).
