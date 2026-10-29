# Plantilla «ONG y fundación» (NoExpertise)

Web estática Astro 5 + Tailwind 4, derivada de AstroWind (MIT, ver `LICENSE-ASTROWIND.md`). Estilo: **humano**
(bandas a todo el ancho en azul, naranja y blanco; serif cálida enorme con subrayado a pincel). El brief de diseño
está en `DISEÑO.md`. Todo en castellano de España, frases cortas, sin jerga.

## Dónde está cada cosa
- **Textos, contacto, menú, SEO y secciones**: `site.yaml` (raíz). Es la única fuente de contenido. `src/data/site.ts` lo carga y lo tipa; no pongas textos fijos en los componentes.
- **Colores**: `site.yaml → colores` (primario = azul, acento = naranja, fondo, texto). `src/layouts/Base.astro` los convierte en variables CSS (`--c-primario`…); `src/styles/global.css` saca de ellos los derivados (`--c-noche`, `--c-cielo`, `--c-arena`, `--c-sobre-acento`) con `color-mix`. Sobre el naranja el texto va siempre oscuro (`--c-sobre-acento`), nunca blanco.
- **Tipografías y aspecto general**: `src/styles/global.css` (fuentes del sistema: serif para títulos, palo seco para el texto; botones `.btn` naranja, `.btn-azul`, `.btn-sec` de contorno; bandas `.banda-*`; filas 50/50 `.mitad`; subrayado `.pincel`; cabecera `.cabecera--humana` y pie `.pie--humano`). No añadas fuentes externas.
- **Imágenes**: en `public/`. Las de relleno, en `public/placeholders/`. En `site.yaml` van con ruta absoluta (`/fotos/hero.jpg`). Las fotos del cliente van en `public/fotos/`. Fotos de personas: `/placeholders/persona.svg` mientras no haya una propia.
- **Logo**: `site.yaml → logo` (ruta en `public/`); vacío = inicial y nombre en texto.
- **Pie «Web creada con NoExpertise»**: `site.yaml → marca_pie` (true en plan gratis).
- **Cabecera**: fija; con JavaScript se vuelve transparente sobre el hero (si es la primera sección, `data-hero-sangre`) y sólida al bajar.

## Secciones
Cada sección es un componente que solo se pinta si `site.yaml → secciones.<id>.activa` es `true`, en el orden de `site.yaml`.
- `hero` → `hero.astro`: foto a sangre con velo, titular enorme, `titulo_destacado` (parte del título subrayada a pincel), `sello` (texto corto del sello redondo), `cta` y `cta_secundario`.
- `cifras` → `cifras.astro`: banda naranja con `items[]` {titulo = la cifra como texto, texto}. Sin cifras no se pinta.
- `sobre` → `sobre.astro`: fila 50/50 a sangre (foto a la izquierda) con `titulo_destacado`, párrafos (`texto` con líneas en blanco), `items[]` {titulo, texto} numerados y `cta` como enlace.
- `proyectos` → `proyectos.astro`: mosaico de fotos de borde a borde, `proyectos[]` {titulo, texto, lugar, imagen}; el primero en grande; `cta` en la cabecera.
- `cita` → `cita.astro`: cita enorme sobre foto a sangre: `declaracion`, `autor`, `cargo`, `imagen` (decorativa).
- `ayudar` → `ayudar.astro`: paneles de color de borde a borde, `items[]` {titulo, texto, icono, url, boton}; sin `url` el botón va a `/#contacto`; sin `boton`, usa el título. `nota`: aviso debajo (desgravación…).
- `equipo` → `equipo.astro`: retratos `personas[]` {nombre, cargo, foto}.
- `transparencia` → `transparencia.astro`: banda azul con `reparto[]` {titulo, porcentaje «84 %»} en barra y leyenda, `items[]` {titulo, texto, icono, url opcional} y `cta`.
- `noticias` → `noticias.astro`: `noticias[]` {fecha, categoria, titulo, texto, imagen, url opcional}.
- `opiniones` → `opiniones.astro`: `testimonios[]` {texto, autor, cargo}.
- `preguntas` → `preguntas.astro`: acordeón `details/summary` con `preguntas[]` {pregunta, respuesta}; sin preguntas no se pinta.
- `contacto` → `contacto.astro`: mitad azul con los datos de `contacto` y mitad clara con el formulario.
- `texto` → `texto.astro`: diseño genérico para apartados nuevos (`tipo: texto`): con `imagen`, fila 50/50 a sangre; sin ella, título y párrafos en dos columnas.

Iconos disponibles (`icono`): corazon, mano, usuarios, casa, gota, libro, cesta, mundo, huella, escudo, grafico, balanza, hoja, sol, calendario, mensaje, euro, regalo, nino, estrella, check, telefono, reloj, mapa, correo.

## Reglas para órdenes
1. **Activar o quitar una sección**: cambia `activa: true|false` en `site.yaml`. No borres componentes.
2. **Reordenar secciones**: mueve el bloque dentro de `secciones:` en `site.yaml`. El hero debe seguir siendo el primero para que la cabecera se vea transparente encima.
3. **Cambiar textos, teléfonos, horarios, fotos**: solo en `site.yaml`. Si un texto contiene comas o «: » dentro de `{ … }`, ponlo entre comillas. Listas planas (nunca una lista dentro de un elemento) y como mucho 24 elementos; cifras y porcentajes siempre como texto entre comillas.
4. **Página nueva**: crea `src/pages/<slug>.astro` con `import Base from '../layouts/Base.astro'` y `<Base titulo="…" descripcion="…">…</Base>`; enlázala en `site.yaml → menu`. Ejemplo: `src/pages/aviso-legal.astro`.
5. **Sección nueva**: mejor un apartado con `tipo:` (el diseño de otra sección o `texto`). Si hace falta un diseño nuevo, crea `src/components/secciones/<id>.astro` (copia la estructura de una existente: `seccion(id)`, `Seccion` o banda propia, `Titular`) y añade `secciones.<id>` en `site.yaml`. `src/pages/index.astro` la recoge sola.
6. **No tocar** `src/layouts/Base.astro`, `tailwind.config.mjs` ni `src/styles/comun.css` salvo orden explícita de diseño. Tampoco `src/lib/seo.ts` ni `src/pages/robots.txt.ts`, `sitemap.xml.ts` y `llms.txt.ts`: son el SEO de base (canónica, og:image, `noindex` si `seo.indexable: false`, JSON-LD del negocio y de las preguntas, robots, sitemap y llms.txt), salen solos de `site.yaml` y el fichero es el mismo en todas las plantillas. `seo.url` y `seo.indexable` los pone la plataforma: no los cambies.
7. Mantén: `lang="es-ES"`, imágenes con `Imagen.astro` (carga diferida), sin JavaScript nuevo salvo necesidad real, bandas a todo el ancho con el contenido en `.contenedor` (16 px de margen lateral en móvil), sin scroll horizontal en móvil, botones de 44 px de alto como mínimo. Imágenes de contenido con `alt` sacado del contenido (`altHero`, `altFicha`, `altSeccion` de `src/lib/seo.ts`, o el nombre de la persona); las decorativas, `alt=""`.
8. El formulario no tiene servidor: abre el correo (`mailto`) con el email de `site.yaml`. Para envío real, cambia `action` en `src/components/ui/FormularioContacto.astro`.

## Construir
```
npm ci && npm run build      # resultado en dist/
npx astro preview            # ver dist/ en http://localhost:4321
```
Antes de dar una orden por buena: `npm run build` sin errores.
