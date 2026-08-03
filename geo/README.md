# Sistema GEO — Gridded Agency · Mobclub

Sistema para detectar qué consultas hacen las personas **con intención de compra** cuando
arrancan su búsqueda en motores generativos (ChatGPT, Perplexity, Gemini, Copilot, AI
Overviews) y convertirlas en artículos optimizados para ser **citados** por esos motores.

Dos nichos, dos agentes separados. No hay agente GEO genérico: lo que hace ganar una
citación en pilates clínico local no se parece en nada a lo que la hace ganar en
automatización con IA B2B.

| Web | Nicho | Modelo | Skill |
|---|---|---|---|
| Gridded Agency | IA y automatización de procesos | B2B, servicios, ticket alto | `/geo-gridded` |
| Mobclub | Pilates máquinas, sesiones individuales (A Coruña) | B2C local, salud/YMYL | `/geo-mobclub` |

---

## Cómo funciona

Todo se ejecuta **a mano desde el editor**. No hay cron, no hay n8n, no hay webhook, no hay
base de datos. El estado vive en Markdown versionado en Git.

```
Tú abres el editor
   │
   ├─ /geo-mobclub radar          → el agente investiga y añade filas a radar.md
   │                                 (cada fila = una consulta con intención de compra)
   │
   ├─ (revisas radar.md, marcas lo que quieres atacar: estado → planificada)
   │
   ├─ /geo-mobclub articulo M-014 → el agente escribe geo/mobclub/articulos/….md
   │
   ├─ (revisas el borrador, lo apruebas: estado → listo)
   │
   └─ copias/pegas en el CMS → anotas la URL publicada → estado: publicado
```

## Estructura de ficheros

```
geo/
├── README.md              ← este fichero
├── metodo-geo.md          ← metodología común: qué hace que un motor te cite
├── _plantillas/
│   ├── articulo.md        ← plantilla de artículo (front-matter + esqueleto)
│   └── fila-radar.md      ← definición de las columnas del radar
├── gridded/
│   ├── perfil.md          ← marca, ICP, servicios, entidades, tono, límites
│   ├── radar.md           ← ÍNDICE MAESTRO de consultas detectadas
│   └── articulos/*.md     ← un fichero por artículo
└── mobclub/
    ├── perfil.md
    ├── radar.md
    └── articulos/*.md
```

### Por qué Markdown y no una base de datos

- El radar es una **tabla Markdown**: se lee en GitHub sin herramientas, se edita en el
  editor, y el historial de Git es el log de cambios (quién cambió una prioridad y cuándo).
- Cada artículo es **un fichero con front-matter YAML**: portable a cualquier CMS
  (WordPress, Webflow, Framer) con copiar y pegar, y el front-matter te da los campos que
  el CMS te pide (título SEO, meta, FAQ) sin tener que reinventarlos.
- Volumen esperado: decenas o pocos cientos de filas por web. Una tabla Markdown aguanta
  eso de sobra. Si algún día pasa de ~300 filas, se parte `radar.md` por año.

## Estados de una consulta

| Estado | Significado |
|---|---|
| `detectada` | El agente la encontró. Nadie la ha validado todavía. |
| `descartada` | Revisada y descartada. Se queda en la tabla con el motivo, para no reinvestigarla. |
| `planificada` | Validada por ti. Toca escribirla. |
| `redactada` | Existe borrador en `articulos/`. Pendiente de tu revisión. |
| `listo` | Revisado y aprobado. Pendiente de pegar en el CMS. |
| `publicado` | Vivo en la web. Con `url_publicada` rellena. |

## Reglas de trabajo

1. **El agente nunca marca `publicado`.** Ese estado lo pones tú cuando pegas en el CMS.
2. **El agente nunca inventa datos propios** (precios, número de clientes, resultados de
   casos). Si le hace falta un dato interno, deja `⚠️ PENDIENTE:` en el borrador.
3. **Toda cifra o afirmación externa lleva fuente** con URL en el front-matter.
4. **Un commit por ejecución**, con mensaje del tipo `geo(mobclub): radar 2026-08` o
   `geo(gridded): artículo n8n-vs-make`.

## Fases

- **Fase 1 (montada aquí):** radar de consultas + redacción de artículos.
- **Fase 2 (cuando haya 15-20 artículos publicados):** auditoría del contenido ya
  publicado en cada web y refuerzo de las páginas que ya reciben citaciones.
- **Fase 3:** seguimiento de citaciones — preguntar periódicamente a cada motor las
  consultas del radar y registrar si aparece tu dominio. Requiere que las Fases 1-2 lleven
  meses funcionando, porque antes no hay nada que medir.
