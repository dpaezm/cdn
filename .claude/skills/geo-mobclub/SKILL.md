---
name: geo-mobclub
description: Agente GEO del nicho salud/pilates para Mobclub (mobclub.es, pilates máquinas 1:1 en A Coruña). Usar cuando se pida investigar consultas con intención de compra que la gente hace a ChatGPT/Perplexity/Gemini sobre pilates, suelo pélvico, posparto, embarazo, dolor de espalda o rehabilitación; cuando se pida ampliar o revisar geo/mobclub/radar.md; o cuando se pida redactar un artículo GEO para Mobclub. Dos modos - "radar" (investiga y registra consultas) y "articulo <ID>" (redacta el borrador). NO usar para Gridded Agency ni para contenido de IA/automatización.
---

# Agente GEO — Mobclub

Nicho: **salud y movimiento**. Negocio **local** (A Coruña), **B2C**, contenido **YMYL**.
Objetivo: que los motores generativos citen a mobclub.es cuando alguien de A Coruña con
un problema físico y dinero para resolverlo abre una conversación con un modelo.

## Antes de nada — leer siempre

1. `geo/metodo-geo.md` — metodología común (qué hace que un motor cite).
2. `geo/mobclub/perfil.md` — marca, servicios, ICP, entidades, prohibiciones.
3. `geo/mobclub/radar.md` — lo que ya está registrado, para no duplicar.

Si `perfil.md` tiene `⚠️ CONFIRMAR` en campos que necesitas (precios, titulaciones,
competencia), **no los inventes**: trabaja con lo que hay y lista al final lo que te ha
faltado.

---

## Modo `radar`

Invocación: `/geo-mobclub radar` (opcionalmente con un foco: `/geo-mobclub radar posparto`).

**Objetivo:** añadir 8-15 consultas nuevas, verificadas y puntuadas, a `radar.md`.

### Procedimiento

1. **Elegir el foco.** Si el usuario no lo da, escoge el eje o segmento peor cubierto
   según el radar actual. Anúncialo antes de empezar.
2. **Generar candidatas** cruzando los segmentos de cliente del perfil con los 8 ejes de
   intención. Escríbelas como las diría una persona real hablando con un modelo: largas,
   con contexto personal, en primera persona.
3. **Verificar cada candidata con búsqueda web real.** Sin este paso la fila no vale nada.
   Para cada una anota:
   - quién responde hoy (dominios concretos o tipo de fuente),
   - qué formato tiene lo que gana (listicle, foro, ficha de clínica, vídeo),
   - **qué le falta**: sin precios, datos viejos, cero contexto local, puro genérico,
     respuesta que no distingue entre grupo e individual…
4. **Descartar sin piedad.** Si es informativa pura sin recorrido comercial, o si no hay
   forma de que Mobclub responda mejor que quien está hoy, va a *Descartado* con motivo.
5. **Puntuar** Int / Dif / Enc (1-5) y calcular `Pri = Int + Enc − Dif`.
6. **Escribir las filas** en la sección *Activo*, reordenar por `Pri`, y añadir el apunte
   en *Historial de rondas*.
7. **Reportar al usuario**: cuántas filas, cuáles son las 3 de mayor prioridad y por qué,
   y qué `⚠️ CONFIRMAR` del perfil te ha bloqueado.

### Sesgos del nicho — dónde mirar

- **Local.** Cruza cada consulta relevante con "en A Coruña" y "cerca de mí". Las consultas
  con geo-intención son las que menos competencia real tienen y las que más convierten.
- **Momentos vitales.** Embarazo, posparto, menopausia, alta de fisioterapia, vuelta al
  deporte tras lesión, diagnóstico reciente. Son disparadores de compra con fecha: la
  persona busca *ahora* porque le acaba de pasar algo.
- **Miedo.** "¿me puedo hacer daño?", "¿es seguro con mi lesión?", "¿y si no puedo seguir
  el ritmo?". Eje `objecion`, altísima conversión, casi nadie lo trata en serio.
- **Precio.** El sector esconde las tarifas. Publicarlas con claridad es el mayor hueco
  disponible en este nicho.
- **Comparación.** Pilates vs gimnasio · máquinas vs suelo · individual vs grupo ·
  pilates vs fisioterapia vs entrenamiento personal.
- **Terminología de paciente, no de profesional.** La gente busca "se me abre la barriga",
  no "diástasis de rectos". Registra la forma en que lo dice la persona y usa el término
  técnico dentro del artículo como entidad.

---

## Modo `articulo <ID>`

Invocación: `/geo-mobclub articulo M-007`.

**Objetivo:** dejar en `geo/mobclub/articulos/<slug>.md` un borrador completo y revisable.

### Procedimiento

1. Localiza la fila en `radar.md`. Si no existe el ID, para y dilo.
2. Relee `perfil.md` y la columna *Hueco* de esa fila: **el artículo existe para tapar ese
   hueco concreto**, no para hablar del tema en general.
3. Investiga con búsqueda web lo que necesites para respaldar las afirmaciones clínicas.
   Fuentes admisibles: sociedades científicas, guías clínicas, revisiones, organismos
   públicos de salud. **No** blogs de gimnasios, **no** contenido de marca de competidores.
4. Copia `geo/_plantillas/articulo.md` y escribe:
   - **`respuesta_corta` primero.** 40-60 palabras que resuelvan la consulta entera. Es
     el pasaje que se va a citar; si no es bueno, el resto da igual.
   - Bloque de datos duros (tabla de precios, comparativa, tiempos, requisitos).
   - Un H2 por sub-pregunta, escrito literal como lo preguntaría la persona.
   - FAQ de 4-8 preguntas de cola larga.
   - Cierre con acción concreta (reservar la primera sesión) y señal de identidad.
5. Rellena todo el front-matter, incluidas `fuentes` con URL y fecha de consulta.
6. Actualiza la fila del radar: `estado: redactada` y enlace al artículo.
7. Reporta al usuario: qué has escrito, qué fuentes has usado, qué `⚠️ PENDIENTE:` quedan
   y quién tiene que firmar la revisión clínica.

### Reglas duras del nicho (YMYL)

- **`revisado_por` es obligatorio** en cualquier artículo con carga clínica. El estado no
  puede pasar de `borrador` con ese campo vacío. El agente nunca lo rellena solo.
- **Cero diagnóstico y cero promesa de curación.** Se describe qué se trabaja y para
  quién. Nunca "cura", "elimina el dolor", "corrige la hernia".
- **Toda afirmación clínica lleva fuente** con URL en el front-matter.
- **Frase de seguridad** cuando hay patología: recomendar consultar con su profesional
  sanitario antes de empezar.
- **Pilates ≠ fisioterapia.** No atribuir a Mobclub competencias sanitarias que no consten
  en el perfil.
- **A Coruña aparece de forma natural** en todo artículo con intención local, junto con la
  información operativa (horario, cómo reservar) escrita en el cuerpo.
- **Nada de testimonios ni reseñas** que no estén confirmadas en el perfil.
- Si el artículo necesita un precio, una duración o una titulación que no está en
  `perfil.md`: escribe `⚠️ PENDIENTE: precio bono 10 sesiones` y sigue. **Nunca inventes.**

---

## Modo `estado`

Invocación: `/geo-mobclub estado`. Resume el radar: cuántas filas por estado, las 5 de
mayor prioridad sin redactar, los borradores esperando revisión, los artículos `listo`
sin publicar y los `⚠️ PENDIENTE:` abiertos en los borradores.

## Al terminar cualquier modo

Deja el trabajo en un commit con mensaje `geo(mobclub): <qué se hizo>`. No publiques
nada en la web ni marques `publicado`: eso lo hace el usuario a mano en el CMS.
