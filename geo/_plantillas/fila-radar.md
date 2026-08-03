# Definición de las columnas del radar

`radar.md` es el índice maestro de cada web: una tabla Markdown, una fila por consulta.

```markdown
| ID | Consulta | Eje | Int | Dif | Enc | Pri | Hoy se cita | Hueco | Estado | Artículo |
|----|----------|-----|-----|-----|-----|-----|-------------|-------|--------|----------|
```

| Columna | Qué va | Reglas |
|---|---|---|
| **ID** | `M-001` (Mobclub) o `G-001` (Gridded) | Correlativo. **Nunca se reutiliza ni se renumera**, aunque la fila se descarte. |
| **Consulta** | La pregunta literal, en el lenguaje del usuario | En minúsculas, sin comillas. Las variantes no abren fila: van en la ficha del artículo como `consultas_secundarias`. |
| **Eje** | Uno de los 8 ejes de intención | `problema`, `solucion`, `comparacion`, `precio`, `idoneidad`, `proveedor`, `proceso`, `objecion` |
| **Int** | Intención de compra, 1-5 | 5 = está a un paso de pagar |
| **Dif** | Dificultad, 1-5 | 5 = lo que se cita hoy es sólido, completo y de marca fuerte |
| **Enc** | Encaje con la marca, 1-5 | 5 = podemos responder mejor que nadie con lo que ya somos |
| **Pri** | `Int + Enc − Dif` | Se calcula, no se opina. Se ataca primero ≥ 6 |
| **Hoy se cita** | Quién responde hoy esa consulta | Dominios o tipo de fuente: `reddit + blogs genéricos`, `directorios`, `competidor X` |
| **Hueco** | Qué le falta a lo que hay hoy | En 5-10 palabras: `sin precios`, `datos de 2023`, `no menciona A Coruña`, `solo teoría, cero ejemplos` |
| **Estado** | Ciclo de vida | `detectada` → `planificada` → `redactada` → `listo` → `publicado`, o `descartada` |
| **Artículo** | Enlace relativo al `.md` | Vacío hasta que exista el borrador: `[slug](articulos/slug.md)` |

## Convenciones

- **Orden de la tabla:** por `Pri` descendente. Las `descartada` y `publicado` bajan al
  final, a sus propias secciones, para que arriba quede solo lo accionable.
- **Descartar no es borrar.** Una fila descartada se queda con el motivo en la columna
  *Hueco* (`descartada: fuera de servicio`). Evita reinvestigar lo mismo cada ronda.
- **Fecha de ronda:** cada ejecución del radar añade un apunte en la sección
  *Historial de rondas* al final del fichero: fecha, nº de filas nuevas, qué se exploró.
- **Un cambio de estado = un commit.** El historial de Git es el log de la operación.
