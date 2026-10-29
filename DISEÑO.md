# ONG y fundación: brief de diseño

Plantilla `ong-fundacion` creada el 29/10/2026 a partir de `asociacion` con `php artisan plantillas:nueva`
y rediseñada entera. Este fichero se queda en el repo: es lo que lee quien (persona o agente) rediseñe la plantilla.

## Brief

- **Para quién**: ONG, fundaciones, entidades de voluntariado, de cooperación y protectoras de animales
  (`sectores`: ong, fundacion, voluntariado, cooperacion, protectora). Quien entra quiere saber tres cosas: qué
  hacen y si se nota (impacto, proyectos), si son de fiar (transparencia, equipo) y cómo ayudar (donar, hacerse
  socio, voluntariado).
- **Qué tiene que conseguir la web**: que la gente colabore. Botón naranja «Dona ahora» en la cabecera, en la
  portada y en los paneles de «Cómo ayudar»; formulario de contacto para todo lo demás (pedir ayuda incluida).
- **Tono y estilo** (`estilo: humano`): cálido, cercano y serio a la vez. Referencia que sí: losmartesnohayluna.com
  (bandas a sangre, color pleno, cifras y cita gigantes) llevada a una fundación de barrio. Que no: la caja centrada
  con tarjetas blancas de `asociacion`; la estética de «campaña de catástrofe» (negro, rojo, fotos dramáticas).
- **Paleta de ejemplo**: primario `#123e7c` (azul), acento `#ff7a1a` (naranja), fondo `#ffffff`, texto `#16233b`.
  Derivados en `global.css` con `color-mix`: `--c-noche` (azul + negro: hero, cita, pie), `--c-cielo` (azul muy
  claro: proyectos, contacto, aviso), `--c-arena` (naranja muy claro: opiniones, tercer panel), `--c-sobre-acento`
  (azul casi negro: texto sobre naranja, que nunca va en blanco). Si el cliente cambia los cuatro colores, todo se
  recalcula.
- **Tipografía**: del sistema. Títulos en serif con peso 700 (Iowan Old Style, Sitka Heading, Charter, Cambria,
  Georgia), muy grandes (hero 6,8 rem en escritorio, 2,7 rem en móvil; secciones hasta 4,4 rem), con la parte de
  `titulo_destacado` subrayada con una pincelada naranja (máscara SVG que sigue el color de acento). Texto en
  palo seco del sistema. Antetítulos en mayúsculas espaciadas (0,18 em) con una raya naranja delante. Botones
  píldora de 52 px.
- **Forma propia**: la «esquina de casa»: las fotos llevan una sola esquina muy redondeada (abajo a la derecha en
  «Quiénes somos», arriba en equipo y noticias), y la marca es un círculo con una esquina recta. Sello redondo
  naranja girado en el hero.
- **Ritmo de bandas** (todas de borde a borde; contenido a 90 rem como mucho, 16 px de margen en móvil):
  1. `hero` — 92 svh, foto a sangre con velo azul noche; titular serif enorme abajo a la izquierda, texto, dos
     botones y el sello. La cabecera fija se vuelve transparente encima.
  2. `cifras` — naranja pleno; titular y nota partidos; 4 cifras enormes separadas por filetes; corazón de contorno.
  3. `sobre` — 50/50 a sangre: foto hasta el borde izquierdo; titular con pincel, párrafos, tres valores
     numerados y enlace.
  4. `proyectos` — azul cielo arriba y, debajo, mosaico de fotos sin márgenes (el primero 2×2), con lugar en
     etiqueta naranja, título y texto sobre la foto.
  5. `cita` — foto a sangre con velo, comillas naranjas gigantes y frase en serif cursiva enorme.
  6. `ayudar` — titular sobre blanco y tres paneles de color pleno de borde a borde (naranja, azul, arena), cada
     uno con icono, número, título, texto y botón; franja azul cielo con la nota de desgravación.
  7. `equipo` — blanco; cinco retratos con esquina de casa.
  8. `transparencia` — azul; barra del reparto de fondos con leyenda en cifras grandes y compromisos en filas.
  9. `noticias` — blanco; tres columnas con foto, categoría y título serif.
  10. `opiniones` — arena; tres opiniones en serif separadas por filetes.
  11. `preguntas` — blanco; titular fijo a la izquierda, acordeón grande a la derecha.
  12. `contacto` — partido a sangre: mitad azul con el teléfono enorme y los datos; mitad cielo con el formulario.
  13. Pie azul noche con franja naranja arriba y cuatro columnas (marca y redes, contacto, web, colabora).
- **Responsive**: móvil primero. A 375 px todo en una columna con 16 px de margen (fotos y fondos a sangre), menú
  plegable `details`, botones a todo el ancho en el hero. A 768 px: cifras 2×2, mosaico de 2 columnas, paneles de
  dos en dos (el impar a todo el ancho), filas 50/50. A 1440 px: 4 cifras, mosaico de 4 columnas, 3 paneles,
  5 retratos, columnas partidas.
- **Fotos** (`fotos.json`, 11): calle de Oviedo al atardecer con voluntarios de espaldas (hero), manos con una
  taza de café (sobre), proyectos (banco del parque, despensa, refuerzo escolar, sala de taller, fuente en
  Matagalpa), puerta entreabierta con luz (cita) y tres noticias. Sin caras reconocibles, sin texto ni logotipos.
  Personas del equipo con la silueta `/placeholders/persona.svg`.
- **Qué no hacer**: tarjetas blancas encajonadas; texto blanco sobre naranja; fotos de sufrimiento o de niños con
  la cara visible; cifras inventadas en los componentes (solo en `site.yaml`).

## Hecho

- [x] `site.yaml` de ejemplo (Fundación Llar, Oviedo, ficticia), todo activo, listas planas, cifras como texto.
- [x] Secciones nuevas: cifras, sobre, proyectos, cita, ayudar, transparencia, opiniones; rediseñadas hero, equipo,
      noticias, preguntas, contacto y texto. Fuera las de `asociacion` (actividades, hazte-socio).
- [x] `template.yaml` con sectores con nombre, secciones, `asistente:` de 11 pasos.
- [x] `fotos.json` (11 fotos) y placeholders SVG propios; favicon propio.
- [ ] Fotos generadas y previews definitivas (paso de fotos; las de `preview/` son provisionales con placeholders).
