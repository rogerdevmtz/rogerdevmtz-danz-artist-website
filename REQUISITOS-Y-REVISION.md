# Requisitos y revisión de DANZ

Estado: versión aprobada por el estudiante el 12 de octubre de 2026. Vídeos reservados por petición del estudiante; actuaciones futuras pendientes de datos confirmados. Repositorio propio: https://github.com/rogerdevmtz/rogerdevmtz-danz-artist-website. El estado del envío a la plataforma figura en ENTREGA.md.

Enunciado consultado: [Muestra el talento de tu amigo artista con un website](https://learn.4geeks.com/es/main-cohort/spain-aie-pt-5/syllabus/web-ui-fundamentals-with-tailwind/project/html-css-artist-landing-seo-access?moduleId=1).

Releído completo el 12 de octubre de 2026, junto con la lección externa [Cómo comenzar un proyecto de programación](https://learn.4geeks.com/es/lesson/como-comenzar-un-proyecto-de-codificacion). La lección permite la alternativa local y explica la creación del repositorio propio. Véase [ENTREGA.md](ENTREGA.md) para el procedimiento pendiente y el texto preparado para el instructor. La subida a GitHub es parte de la entrega y su estado se registra en ENTREGA.md; el hosting público no es un requisito del enunciado.

## Los doce puntos del enunciado

| Punto | Requisito / criterio | Implementación o comprobación |
| --- | --- | --- |
| 1 | Crear `index.html` según las indicaciones | Página única con portada, sobre mí, trayectoria y próximas presentaciones; se añade el espacio audiovisual solicitado |
| 2 | Añadir estilos en `styles.css` | Hoja externa, variables, Grid, Flexbox, encuadres y media queries |
| 3 | Usar etiquetas de accesibilidad | Regiones con nombre, alternativas, enlace de salto, foco y controles nativos |
| 4 | HTML semántico y Schema.org | Etiquetas estructurales nativas y Microdata `Person` del artista real |
| 5 | HTML correctamente formateado | Indentación consistente; HTML Validate 11.16.2 pasa sin errores ni advertencias |
| 6 | Jerarquía de etiquetas | Un `h1`, `h2` por sección y `h3` para hitos y estado de agenda |
| 7 | Uso estricto de HTML semántico | `header`, `nav`, `main`, `section`, `article`, `figure`, `figcaption`, `time` y `footer`; agrupación visual con `div` |
| 8 | CSS atractivo y moderno | Dirección basada en las tres referencias aportadas; fotografías de DANZ, tipografía urbana y diseño adaptable. Valoración estética aprobada por el estudiante |
| 9 | Organización de archivos | HTML, CSS, imágenes, guía y fuentes documentales separados; sin paquetes de interfaz |
| 10 | Apto para lectores de pantalla | Idioma, orden de lectura, nombres de regiones y enlaces, alternativas y foco. Inspección semántica y prueba de teclado; sin sesión real con NVDA/VoiceOver |
| 11 | Schema.org describiendo artista u obra | Entidad `Person` con nombre, profesión, descripción factual, imagen y perfil social |
| 12 | Requerimientos deseados por el artista | Identidad de DANZ en A Coruña, reggaetón y dembow, biografía, archivo, agenda y booking. Vídeos preparados y cambios de texto solicitados aplicados; aprobación recibida |

## Condiciones adicionales

| Condición | Resultado |
| --- | --- |
| Una sola landing | Un documento HTML de la web |
| Barra con enlaces internos | Sobre mí, trayectoria y próximas fechas; booking en el pie |
| Primera sección de bienvenida | Retrato real, DANZ, actividad y géneros |
| Secciones aproximadamente de una pantalla en ordenador | Alturas mínimas de viewport y composición por escenas; el contenido crece cuando lo necesita. En móvil se apila y no se recorta |
| Solo HTML y CSS, sin JavaScript ni frameworks | Cero scripts; Microdata y navegación nativa. Google Fonts aporta solo CSS y fuentes |
| Plantilla oficial | `4GeeksAcademy/html-hello`, commit `a9b4fe4`, con historial conservado |
| Secciones no genéricas | Archivo con publicaciones verificadas, fotografías del artista y enlaces profesionales; sin servicios ni testimonios inventados |
| Sin flechas ni líneas decorativas | Aplicado; se conservan los contornos necesarios de foco |
| Evitar texto redundante | Eliminada la franja de ubicación y códigos de país, eslóganes de relleno y duplicaciones de agenda |
| Vídeos | Dos espacios con portada; archivos pendientes del estudiante. No se simula reproducción |
| Crear repositorio, subir y compartir | APROBADO. Repositorio propio creado; subida y enlace final se registran en ENTREGA.md |

## Revisión técnica

URL local: <http://127.0.0.1:8137/>. Chrome, mediante CUA y sus herramientas de DOM, capturas y navegación. Pruebas en pestaña independiente de la vista previa del estudiante.

- HTML Validate 11.16.2: sin errores ni advertencias en la versión revisada.
- CSS: formato y análisis sintáctico con Prettier.
- Cinco fotografías WebP y favicon local; imágenes informativas con texto alternativo.
- Navegación por fragmentos y región principal revisadas en el DOM y el árbol accesible.
- Diseño revisado en escritorio y a 390px; comprobación de reflujo a 320px.
- Enlace de salto comprobado con teclado; foco visible y sin controles de vídeo falsos.
- No hay scripts, eventos JavaScript, iframes ni un framework de interfaz.
- Se mantienen enlaces reales a Instagram, TikTok, publicaciones y press kit; booking es un `mailto` al contacto público verificado.

Contraste de la paleta sobre fondos sólidos:

| Texto / fondo | Relación |
| --- | --- |
| Crema `#f5f0df` sobre negro `#090909` | 17,46:1 |
| Secundario `#bdb7ad` sobre negro | 9,99:1 |
| Rojo `#ff4b26` sobre negro | 5,96:1 |
| Negro sobre rojo | 5,96:1 |

Las imágenes utilizan capas oscuras y se revisan visualmente. Los cálculos anteriores no son una medición píxel a píxel de cada texto sobre fotografía ni una certificación completa de WCAG.

## Pendientes y límites

- Los archivos de vídeo los aportará el estudiante. La preparación de los espacios está hecha; la reproducción y los subtítulos se comprobarán con esos archivos.
- La agenda no contiene fechas inventadas. Se añadirán actuaciones cuando se faciliten datos confirmados.
- Las fuentes dependen de Google Fonts y de la conexión. Hay familias de reserva; no se afirma funcionamiento visual idéntico sin conexión.
- No se ha probado en una sesión real de NVDA/VoiceOver ni en Safari o Firefox.
- La información estructurada se ha revisado frente a Schema.org y localmente; no se afirma una certificación del validador público ni de Google.
- La matriz no garantiza una nota. El estudiante ha revisado y aprobado la versión para preparar su entrega.

Consulta [FUENTES-Y-REFERENCIAS.md](FUENTES-Y-REFERENCIAS.md) para la procedencia y el uso de las tres referencias, y [GUIA-PASO-A-PASO.md](GUIA-PASO-A-PASO.md) para aprender del código.
