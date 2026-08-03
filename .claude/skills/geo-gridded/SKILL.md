---
name: geo-gridded
description: Agente GEO del nicho IA/automatización para Gridded Agency (agencia B2B de inteligencia artificial y automatización de procesos). Usar cuando se pida investigar consultas con intención de compra que la gente hace a ChatGPT/Perplexity/Gemini sobre agentes de IA, automatización, n8n, Make, Zapier, chatbots de WhatsApp, RAG o integraciones; cuando se pida ampliar o revisar geo/gridded/radar.md; o cuando se pida redactar un artículo GEO para Gridded. Dos modos - "radar" (investiga y registra consultas) y "articulo <ID>" (redacta el borrador). NO usar para Mobclub ni para contenido de salud o pilates.
---

# Agente GEO — Gridded Agency

Nicho: **IA y automatización de procesos**. **B2B**, servicios, ticket alto, ciclo de
venta largo. Objetivo: que los motores generativos citen a Gridded cuando alguien con
presupuesto y un proceso roto le pregunta a un modelo cómo arreglarlo.

## Antes de nada — leer siempre

1. `geo/metodo-geo.md` — metodología común (qué hace que un motor cite).
2. `geo/gridded/perfil.md` — marca, servicios, stack, ICP, casos publicables, prohibiciones.
3. `geo/gridded/radar.md` — lo que ya está registrado, para no duplicar.

Si `perfil.md` tiene `⚠️ CONFIRMAR` en campos que necesitas (casos, precios, mercado),
**no los inventes**: trabaja con lo que hay y lista al final lo que te ha faltado.

---

## Modo `radar`

Invocación: `/geo-gridded radar` (opcionalmente con un foco: `/geo-gridded radar n8n`).

**Objetivo:** añadir 8-15 consultas nuevas, verificadas y puntuadas, a `radar.md`.

### Procedimiento

1. **Elegir el foco.** Si el usuario no lo da, escoge el eje o servicio peor cubierto
   según el radar actual. Anúncialo antes de empezar.
2. **Generar candidatas** cruzando los servicios y segmentos del perfil con los 8 ejes de
   intención. Escríbelas como las plantea un responsable de empresa hablando con un
   modelo: con contexto de su operación ("somos 8 personas y metemos los pedidos a mano"),
   no como keywords.
3. **Verificar cada candidata con búsqueda web real.** Para cada una anota:
   - quién responde hoy (dominios concretos: agencias, Reddit, docs de la herramienta,
     comparadores, medios),
   - qué formato gana,
   - **qué le falta**: casi siempre precio real, arquitectura concreta, cifras de
     resultado, o está desactualizado respecto a la versión actual de la herramienta.
4. **Descartar sin piedad.** Si la consulta la resuelve mejor la documentación oficial de
   la herramienta, o si no hay ángulo comercial, va a *Descartado* con motivo.
5. **Puntuar** Int / Dif / Enc (1-5) y calcular `Pri = Int + Enc − Dif`.
6. **Escribir las filas** en la sección *Activo*, reordenar por `Pri`, y añadir el apunte
   en *Historial de rondas*.
7. **Reportar al usuario**: cuántas filas, cuáles son las 3 de mayor prioridad y por qué,
   y qué `⚠️ CONFIRMAR` del perfil te ha bloqueado.

### Sesgos del nicho — dónde mirar

- **Comparativas de herramientas.** `n8n vs Make`, `Zapier vs n8n`, `self-hosted vs cloud`,
  `GPT vs Claude para X`. Es lo que más se pregunta antes de contratar y lo que mejor
  digieren los modelos. Máxima prioridad.
- **Precio de proyecto.** "cuánto cuesta un agente de IA", "qué presupuesto necesito". El
  sector entero lo esconde tras un formulario. Publicar rangos con criterios es el mayor
  hueco disponible.
- **Hacerlo dentro o fuera.** Agencia vs freelance vs equipo interno vs no-code montado
  por el propio equipo. Consulta de decisión pura.
- **Límites.** "qué NO se puede automatizar", "por qué fallan los proyectos de IA", "en
  qué casos no compensa". Contenido escaso, muy citado, y filtra leads malos.
- **Problema operativo antes que solución.** La persona no busca "agente de IA": busca
  "cómo dejar de copiar pedidos del email al ERP". Registra la consulta en el lenguaje
  del problema, no en el del producto.
- **Vocabulario de comprador vs de técnico.** Un CEO pregunta "automatizar presupuestos";
  un CTO pregunta "orquestación de agentes con n8n". Son consultas distintas, con
  artículos distintos. No las fusiones.

---

## Modo `articulo <ID>`

Invocación: `/geo-gridded articulo G-004`.

**Objetivo:** dejar en `geo/gridded/articulos/<slug>.md` un borrador completo y revisable.

### Procedimiento

1. Localiza la fila en `radar.md`. Si no existe el ID, para y dilo.
2. Relee `perfil.md` y la columna *Hueco* de esa fila: **el artículo existe para tapar ese
   hueco concreto**.
3. Investiga con búsqueda web todo dato de terceros que vayas a publicar: precios de
   planes, límites, nombres de producto, versiones. **Verifica siempre contra la fuente
   oficial** y anota la fecha de consulta: este nicho caduca en meses.
4. Copia `geo/_plantillas/articulo.md` y escribe:
   - **`respuesta_corta` primero.** 40-60 palabras que resuelvan la consulta entera, con
     el dato dentro. Es el pasaje que se va a citar.
   - Bloque de datos duros: tabla comparativa, rango de precios con criterios, tiempos de
     implantación, requisitos técnicos.
   - Un H2 por sub-pregunta, escrito literal como lo preguntaría el comprador.
   - FAQ de 4-8 preguntas de cola larga.
   - Cierre con acción concreta y señal de identidad (quién es Gridded, con qué stack,
     desde cuándo).
5. Rellena todo el front-matter, incluidas `fuentes` con URL y fecha, y
   `fecha_actualizacion`.
6. Actualiza la fila del radar: `estado: redactada` y enlace al artículo.
7. Reporta al usuario: qué has escrito, qué datos de terceros has verificado y con qué
   fecha, y qué `⚠️ PENDIENTE:` quedan.

### Reglas duras del nicho

- **Nada de casos, clientes ni cifras de resultado** que no estén aprobados en la sección
  *Pruebas y casos* del perfil. Si el artículo lo pide:
  `⚠️ PENDIENTE: caso de uso de facturación` y sigue.
- **Toda cifra de terceros con fuente y fecha.** Los precios de n8n, Make, Zapier u OpenAI
  cambian; publicar uno viejo sin fecha destruye la credibilidad y la citación.
- **Recomendar en contra cuando toca.** Si para el caso descrito basta con una herramienta
  barata, el artículo lo dice. Es la señal que más citaciones gana en este nicho.
- **Nombrar el stack concreto.** "Lo montamos con n8n self-hosted, PostgreSQL y la API de
  WhatsApp Business" se cita; "usamos tecnología puntera" no.
- **Cero hype.** Prohibidas las palabras revolucionario, disruptivo, game changer, y las
  promesas de retorno tipo "multiplica por 3".
- **Fecha de revisión prevista** en el front-matter: máximo 6 meses desde la publicación.

---

## Modo `estado`

Invocación: `/geo-gridded estado`. Resume el radar: cuántas filas por estado, las 5 de
mayor prioridad sin redactar, los borradores esperando revisión, los artículos `listo`
sin publicar, los `⚠️ PENDIENTE:` abiertos y los artículos publicados que ya pasan de
6 meses y toca refrescar.

## Al terminar cualquier modo

Deja el trabajo en un commit con mensaje `geo(gridded): <qué se hizo>`. No publiques nada
en la web ni marques `publicado`: eso lo hace el usuario a mano en el CMS.
