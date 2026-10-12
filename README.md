# DANZ · DJ en A Coruña

Portfolio de DANZ, DJ hondureño establecido en A Coruña, para el proyecto de HTML, CSS, SEO y accesibilidad de 4Geeks. Nueva versión urbana basada en las tres referencias visuales aportadas por el estudiante y en el material profesional del artista. Versión aprobada por el estudiante el 12 de octubre de 2026. Repositorio de entrega: [rogerdevmtz-danz-artist-website](https://github.com/rogerdevmtz/rogerdevmtz-danz-artist-website).

## Abrir

Abre `index.html` directamente o sirve esta carpeta con:

```sh
python -m http.server 8137 --bind 127.0.0.1
```

Visita <http://127.0.0.1:8137/>. Ctrl+C detiene el servidor. Python es solo una herramienta de previsualización; el navegador recibe HTML, CSS e imágenes. No hay JavaScript, frameworks ni dependencias npm de ejecución.

## Contenido

- Portada: DANZ, DJ en A Coruña, reggaetón y dembow.
- Sobre mí: origen hondureño, selección musical y press kit.
- Trayectoria: publicaciones verificadas de La Bu, Los Bandoleros y Tulum Rooftop. Las fechas son de publicación, no fechas futuras ni una certificación del día de actuación.
- En directo: dos espacios de vídeo solicitados por el estudiante, con portadas reales. Se incorporarán los archivos cuando los facilite.
- Próximas presentaciones: estado «Por anunciar» y enlace al Instagram del artista.
- Booking: enlace al email publicado en su press kit, sin enviar ningún mensaje automáticamente.

Solo se han utilizado fotos profesionales del press kit. No se han generado imágenes del artista. Las cinco imágenes están optimizadas en WebP y conservan su encuadre original como archivo; los recortes de presentación se realizan con CSS.

Las fuentes son Anton, Barlow Condensed y Permanent Marker, servidas mediante la hoja de estilos de Google Fonts. La tipografía requiere conexión; hay familias de reserva. No se han añadido scripts de Google, analítica, cookies de publicidad ni incrustaciones de Instagram.

## Archivos

```text
index.html                  Contenido, estructura, metadatos y Microdata
styles.css                  Diseño, adaptación, foco y sección activa
assets/danz/                Cinco fotografías WebP y favicon SVG
GUIA-PASO-A-PASO.md          Explicación para aprender del código
REQUISITOS-Y-REVISION.md    Matriz de criterios y comprobaciones
FUENTES-Y-REFERENCIAS.md    Procedencia del contenido y decisiones visuales
ENTREGA.md                 Revisión del enunciado y procedimiento de entrega
```

## Validar

Herramienta de comprobación externa al proyecto:

```sh
npx --yes --package html-validate html-validate index.html
```

No se necesita para abrir la web. Se ha usado HTML Validate 11.16.2, además de revisión visual y pruebas de navegación. Los resultados y límites están en el documento de requisitos.

## Vídeos y entrega

Los espacios `#video-show` y `#video-sesion` esperan los archivos del propietario. No muestran controles de reproducción que no funcionen. La guía explica cómo sustituir las portadas por un reproductor HTML nativo.

No se han inventado próximas actuaciones. Se podrán añadir cuando haya fechas confirmadas.

El estudiante aprobó la versión y la preparación de la entrega. `origin` apunta al repositorio propio de GitHub; `plantilla` conserva la procedencia de `4GeeksAcademy/html-hello`. El estado del envío a 4Geeks se registra en `ENTREGA.md`.

## Plantilla

Base oficial: [4GeeksAcademy/html-hello](https://github.com/4GeeksAcademy/html-hello), commit `a9b4fe4`. Se conserva su historial, `README.plantilla.md`, los README de otros idiomas, `.vscode`, `learn.json` y `server.py`. Son archivos auxiliares de la plantilla; la web no ejecuta Python ni Flask en el navegador.
