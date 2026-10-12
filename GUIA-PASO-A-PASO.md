# Cómo está hecha la web de DANZ

La web usa HTML y CSS. Las fotos son archivos WebP y el favicon es SVG. No contiene JavaScript ni frameworks. Esta guía explica las decisiones para que puedas modificar el proyecto y defenderlo en una revisión.

## 1. Del enunciado al contenido

El curso pide una página con portada, sobre mí, trayectoria y próximas presentaciones. Se mantienen esos cuatro destinos y se añade una sección de vídeo solicitada por el estudiante. El booking queda en el pie. Todo vive en `index.html`.

```html
<header>...</header>
<main id="contenido" tabindex="-1">
  <section id="inicio">...</section>
  <section id="sobre-mi">...</section>
  <section id="trayectoria">...</section>
  <section id="en-directo">...</section>
  <section id="presentaciones">...</section>
</main>
<footer id="contacto">...</footer>
```

`header` identifica la cabecera, `nav` la navegación, `main` el contenido principal y `section` un tema con encabezado. Cada hito de trayectoria es un `article`. Los `div` solo agrupan elementos para distribuirlos.

Un ID identifica un elemento único. Una clase permite aplicar el mismo estilo a varias piezas. Por ejemplo, `screen` comparte una altura mínima y `solid-button` comparte la presentación de enlaces importantes.

## 2. Trabajar con información real

El artista es DANZ. Se consultaron su press kit de MavelPoint y las publicaciones profesionales de Instagram. No se copiaron datos personales ajenos a su actividad, cifras de audiencia, premios ni supuestos lanzamientos.

La trayectoria usa fechas de publicaciones verificadas. No confundas «publicado el 23 de julio de 2025» con «actuó ese día»: son afirmaciones distintas. La agenda muestra «Por anunciar» porque no se han facilitado fechas futuras confirmadas. Los vídeos están reservados porque el estudiante aportará los archivos.

La revisión de texto eliminó la franja «A Coruña, España / HN / ES», los eslóganes y las frases que repetían información. La portada expresa el nombre, la actividad, la ciudad y los géneros; los botones indican acciones concretas.

## 3. Conectar la presentación

```html
<link rel="stylesheet" href="styles.css?v=danz-7">
```

La consulta `?v=danz-7` evita reutilizar una versión anterior del CSS durante la revisión. No es otra tecnología ni otro archivo. Los estilos se encuentran en `styles.css`.

Las variables al principio del CSS reúnen colores y fuentes:

```css
:root {
  --black: #090909;
  --paper: #f5f0df;
  --red: #ff4b26;
  --display: "Anton", "Impact", sans-serif;
}
```

Una variable se utiliza como `color: var(--red)`. Cambiarla actualiza todos los lugares que la referencian. Anton se usa para titulares, Barlow Condensed para lectura y controles, y Permanent Marker para acentos manuscritos. Las fuentes se solicitan mediante CSS de Google Fonts, sin JavaScript.

Prueba: cambia temporalmente el rojo y observa qué partes cambian. Restáuralo antes de comparar con las capturas.

## 4. Construir una portada fotográfica

La fotografía ocupa una capa de fondo, mientras el nombre y los controles siguen siendo HTML real. `position: absolute` coloca la imagen dentro de una sección `position: relative`. `isolation: isolate` crea un contexto de apilamiento local: los índices negativos de las capas permanecen dentro de esa composición.

```css
.hero { position: relative; isolation: isolate; }
.hero-photo { position: absolute; z-index: -3; }
.hero-photo img {
  height: 100%;
  object-fit: cover;
  object-position: 50% 35%;
}
```

`cover` llena el marco y recorta lo que sobra. `object-position` decide qué parte queda visible. El archivo fotográfico no se modifica cuando cambia ese recorte. Una capa oscura sobre la imagen ayuda a leer el contenido.

El nombre no forma parte de una imagen: es el `h1`, seleccionable, legible por tecnología de asistencia y comprensible para buscadores. `transform: skew()` inclina el titular; no cambia su significado.

Prueba: cambia la posición de la foto y comprueba el rostro en móvil. No ajustes solo la vista de escritorio.

## 5. Grid, Flexbox y alturas

Grid distribuye las dos columnas de la biografía y las composiciones de archivo y vídeo. Flexbox reparte la navegación y los enlaces de booking. Cada herramienta organiza elementos; no sustituye las etiquetas semánticas.

```css
.screen { min-height: 100svh; }
```

La altura mínima conserva una experiencia próxima a una pantalla en ordenador. Si el contenido necesita más espacio, crece. En móvil la trayectoria se apila y ocupa más altura: no se recorta para encajar artificialmente en una pantalla.

`clamp()` limita tamaños fluidos. Una media query a 680px apila columnas y adapta la cabecera. Un mismo HTML sirve para todos los tamaños.

## 6. Navegar sin JavaScript

```html
<a href="#trayectoria">Trayectoria</a>
<section id="trayectoria">...</section>
```

El navegador encuentra el ID, cambia el fragmento de la URL y desplaza la página. `scroll-padding-top` reserva espacio para que la cabecera fija no tape el destino.

La sección activa se indica con `:target` y `:has()`:

```css
body:has(#trayectoria:target) .masthead a[href="#trayectoria"] {
  color: var(--red);
}
```

Esto refleja el fragmento seleccionado. No es un sistema de seguimiento continuo del scroll: desplazar manualmente la página no cambia la URL ni esa selección.

Prueba: activa Trayectoria, observa el fragmento y después desplázate manualmente. Así distingues el destino elegido del lugar visible.

## 7. Accesibilidad

- `lang="es"` declara el idioma.
- Un enlace de salto permite enfocar `main` sin recorrer la cabecera.
- Un solo `h1` identifica al artista; los `h2` organizan secciones y los `h3` sus contenidos.
- Las imágenes informativas tienen alternativas; la imagen decorativa de agenda tiene `alt=""` y queda fuera del árbol accesible.
- Los enlaces repetidos del archivo tienen nombres accesibles distintos que incluyen su texto visible.
- `:focus-visible` conserva un contorno visible al navegar con teclado.
- Los enlaces importantes se reconocen por su contexto y tratamiento, no solo por una diferencia mínima de color.
- `prefers-reduced-motion` desactiva el desplazamiento suave y las transiciones.

No hay flechas ni líneas decorativas. El contorno de foco se conserva porque informa de qué control está activo.

Prueba con Tab, Mayús+Tab y Enter. El enlace «Saltar al contenido» debe aparecer al recibir foco y enfocar el contenido al activarlo. No actives el correo durante una prueba si no quieres abrir tu aplicación de email.

## 8. SEO y Schema.org

`title` y la descripción explican qué ofrece la página. Los encabezados y el texto contienen información real. Las fotos tienen dimensiones declaradas y las que no son de portada usan `loading="lazy"`.

Se usa Microdata para describir una persona sin etiquetas `script`:

```html
<section itemscope itemtype="https://schema.org/Person">
  <h1 itemprop="name">DANZ</h1>
  <span itemprop="jobTitle">DJ</span>
  <a itemprop="sameAs" href="https://www.instagram.com/danzhn_/">Instagram</a>
</section>
```

`itemscope` abre una entidad, `itemtype` declara su tipo y `itemprop` marca una propiedad. La imagen de portada se relaciona mediante `image` y una descripción factual mediante un `meta` con `itemprop`.

No se inventan un dominio de producción, un canonical o enlaces musicales. El contenido de localhost no está publicado. Schema.org tampoco garantiza resultados enriquecidos ni posicionamiento.

## 9. Preparar los vídeos

Ahora hay dos `figure` con portada y estado «Vídeo próximamente». No hay un botón de reproducción falso. Cuando recibamos los archivos, se sustituirá la imagen de cada espacio por HTML nativo, por ejemplo:

```html
<video controls playsinline preload="metadata"
       poster="assets/danz/danz-mr-jay.webp"
       aria-label="Los Bandoleros Show, Danz y Mr Jay">
  <source src="assets/danz/los-bandoleros.mp4" type="video/mp4">
  Tu navegador no admite este vídeo.
</video>
```

Este fragmento es una explicación, no un archivo de vídeo ya incorporado. No se añade una ruta inexistente a la web activa. Se revisarán el encuadre, el sonido y las alternativas necesarias cuando llegue el material; si hay voz relevante, habrá que preparar subtítulos o transcripción según su contenido.

## 10. Comprobar y entregar

HTML Validate detecta problemas de estructura y uso de atributos que no se ven en una captura. La revisión del navegador comprueba carga, encuadre, navegación, lectura y reflujo. Una validación sintáctica no demuestra por sí sola accesibilidad completa.

Antes de entregar, el estudiante revisa la web, sus referencias y la matriz de requisitos. Después de su aprobación se preparará el repositorio propio y el envío. La aprobación no se infiere de que la vista previa esté abierta.

Para practicar: cambia un encuadre, modifica un título por otro dato verificable y añade una actuación real cuando tengas sus datos. Comprueba móvil y teclado después de cada cambio.
