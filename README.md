# Plantilla NoExpertise · ONG y fundación

Web humana y a todo color para ONG, fundaciones y protectoras: impacto, proyectos, donativos y voluntariado.

- Sectores: ong, fundacion, voluntariado, cooperacion, protectora. Estilo: humano. Plan mínimo: gratis.
- Secciones: hero, cifras, sobre, proyectos, cita, ayudar, equipo, transparencia, noticias, opiniones, preguntas, contacto (y `texto` para apartados nuevos).
- Todo a ancho completo: bandas de borde a borde en azul, naranja y claro; hero a casi pantalla completa con foto a sangre; mosaico de proyectos sin márgenes; filas 50/50 con la foto tocando el borde; contacto partido.
- Ejemplo: Fundación Llar (Oviedo), ficticia.
- SEO de base incluido (`src/lib/seo.ts`): canónica, og:image, JSON-LD (`NGO`) y de las preguntas frecuentes, `robots.txt`, `sitemap.xml` y `llms.txt`; `noindex` si `seo.indexable: false`.
- Contenido editable en `site.yaml`; metadatos y guion del asistente en `template.yaml`; fotos que generar en `fotos.json`; reglas para el agente en `CLAUDE.md`; brief de diseño en `DISEÑO.md`.

## Campos propios
- `hero.titulo_destacado` (parte del título subrayada a pincel; también en `sobre` y `texto`) y `hero.sello` (texto del sello redondo).
- `cifras.items[]` {titulo, texto}: la cifra va en `titulo`, como texto.
- `proyectos.proyectos[]` {titulo, texto, lugar, imagen}.
- `cita` {declaracion, autor, cargo, imagen}.
- `ayudar.items[]` {titulo, texto, icono, url, boton} y `ayudar.nota`.
- `transparencia.reparto[]` {titulo, porcentaje} e `items[]` {titulo, texto, icono, url}.
- `noticias.noticias[]` {fecha, categoria, titulo, texto, imagen, url}; `opiniones.testimonios[]` {texto, autor, cargo}.

```
npm ci
npm run dev      # desarrollo
npm run build    # web estática en dist/
```

Basada en [AstroWind](https://github.com/onwidget/astrowind) © onWidget, licencia MIT (`LICENSE-ASTROWIND.md`). Imágenes de relleno (`public/placeholders/`) generadas para esta plantilla, sin licencias de terceros.
