# Método GEO — metodología común

Base compartida por los dos agentes. Lo específico de cada nicho está en
`gridded/perfil.md` y `mobclub/perfil.md`, y esas reglas **prevalecen** sobre estas.

---

## 1. Qué es distinto respecto al SEO clásico

En buscador clásico compites por una posición en una lista. En motor generativo compites
por que un fragmento tuyo entre en la respuesta y aparezca la citación. Consecuencias
prácticas:

| SEO clásico | GEO |
|---|---|
| La unidad es la página | La unidad es el **pasaje citable** (2-5 frases autocontenidas) |
| Densidad de keyword | **Cobertura de entidades** y relaciones entre ellas |
| Título que gana el clic | Encabezado que **coincide con la pregunta literal** del usuario |
| Enlaces entrantes | Ser **corroborado en varias fuentes** (directorios, reseñas, prensa, foros) |
| Una consulta → una página | Una consulta se **descompone en sub-preguntas** que el motor resuelve por separado |
| Actualizar cuando cae el tráfico | **Fecha visible y datos frescos**: los motores penalizan lo que parece caducado |

## 2. Qué hace que un motor generativo cite una página

Por orden de impacto observado:

1. **Respuesta directa arriba.** La primera frase después de un encabezado responde la
   pregunta por completo, sin preámbulo. Si empieza con "En el mundo actual…", no se cita.
2. **Autocontención.** El pasaje se entiende sin haber leído el resto de la página. Nada
   de "como decíamos antes" ni "esto" sin antecedente.
3. **Dato concreto y extraíble.** Cifra, precio, plazo, comparación, lista numerada. Un
   párrafo de opinión sin dato no se cita casi nunca.
4. **Estructura literal pregunta→respuesta.** H2/H3 escritos como la pregunta que teclea
   la persona, no como un eslogan.
5. **Especificidad verificable.** Ubicación, nombres propios, versiones, fechas. La
   vaguedad es lo primero que se descarta.
6. **Corroboración externa.** Que lo que dices coincida con lo que dicen directorios,
   reseñas, fichas y terceros sobre ti. Un motor que encuentra tres fuentes coherentes
   cita con mucha más frecuencia.
7. **Frescura declarada.** Fecha de actualización visible en el cuerpo, no solo en el
   `<meta>`.

## 3. Anatomía de un artículo GEO

```
H1 = la pregunta o el tema, en el lenguaje del usuario
│
├─ Respuesta corta (40-60 palabras)   ← EL pasaje que se citará. Va antes que nada.
│                                        Autocontenido. Con el dato dentro. Sin intro.
├─ Bloque de datos duros              ← tabla o lista: precios, plazos, comparativa
│
├─ H2 = sub-pregunta 1                ← cada H2 es una pregunta literal
│   └─ respuesta directa + desarrollo
├─ H2 = sub-pregunta 2
│   └─ ...
│
├─ H2 = Preguntas frecuentes          ← 4-8 preguntas de cola larga
│   └─ cada respuesta: 2-4 frases, autocontenida
│
└─ Cierre: qué hacer ahora + señal de identidad (quién firma, dónde, desde cuándo)
```

Reglas de redacción:

- **Párrafos de 2-4 frases.** Un bloque de 10 líneas no se cita entero, y troceado pierde
  sentido.
- **Sin relleno de introducción.** Nada de "en los últimos años ha crecido el interés por…".
- **Repite el sujeto** en vez de usar pronombres al inicio de párrafo: el fragmento tiene
  que sostenerse solo.
- **Números en cifra**, no en letra ("45 minutos", no "cuarenta y cinco minutos").
- **Una idea por encabezado.** Si un H2 responde dos preguntas, son dos H2.
- **Fecha de actualización en el cuerpo**, visible, no solo en metadatos.
- **Extensión:** la mínima que responda bien. 900-1.600 palabras suele bastar. Alargar
  por alargar diluye los pasajes citables.

## 4. Cómo se investiga el radar

El objetivo no es "keywords con volumen": es **la pregunta con la que alguien que va a
comprar abre la conversación** con un modelo. Suelen ser largas, conversacionales y con
contexto personal ("tengo hernia discal, ¿puedo hacer pilates?", "somos 8 personas y
gastamos X horas en meter pedidos a mano, ¿qué me costaría automatizarlo?").

Procedimiento por ronda de radar:

1. **Partir del perfil**: servicios, ICP, problemas que resuelve, objeciones, competencia.
2. **Generar consultas semilla** por cada eje de intención (ver §5).
3. **Verificar con búsqueda real** cada consulta candidata: quién está respondiendo hoy,
   qué fuentes se citan, qué formato tiene el contenido que gana.
4. **Anotar el hueco**: qué le falta a lo que hay hoy (dato ausente, desactualizado,
   genérico, sin precio, sin contexto local).
5. **Puntuar** intención, dificultad y encaje (§6) y escribir la fila en `radar.md`.
6. **No duplicar**: antes de añadir, revisar el radar existente. Si una consulta es una
   variante de otra ya registrada, se anota como consulta secundaria de esa fila, no como
   fila nueva.

Cada ronda: **8-15 consultas nuevas**. Más que eso sale superficial y sin verificar.

## 5. Ejes de intención

Se cubren todos, no solo el último. Los motores generativos capturan la fase temprana, que
es donde el SEO clásico llegaba tarde.

| Eje | Forma típica | Para qué sirve |
|---|---|---|
| **Problema** | "por qué me duele X" / "por qué tardamos tanto en Y" | Entrada temprana, mucho volumen |
| **Solución** | "qué opciones hay para X" | Te mete en la lista de alternativas |
| **Comparación** | "A vs B", "mejor X para Y" | Altísima intención. Prioridad máxima |
| **Precio** | "cuánto cuesta X" | Máxima intención. Casi nadie publica cifras → hueco enorme |
| **Idoneidad** | "¿me sirve X si tengo/soy Z?" | Cualificación; convierte muy bien |
| **Proveedor** | "mejor X en \<sitio\>" / "agencias de X" | Consulta final antes de contactar |
| **Proceso** | "cómo funciona X", "qué pasa en la primera sesión" | Elimina fricción y objeciones |
| **Objeción** | "¿es seguro/caro/complicado X?" | Desactiva el motivo de no comprar |

## 6. Puntuación de una fila

- **Intención (1-5):** ¿cuán cerca está esa persona de pagar?
- **Dificultad (1-5):** ¿cómo de asentado está lo que hoy se cita? Un dominio de marca
  fuerte con respuesta completa = 5. Contenido genérico y viejo = 1.
- **Encaje (1-5):** ¿podemos responder mejor que nadie con lo que somos y sabemos?

**Prioridad = Intención + Encaje − Dificultad.** Se atacan primero las de prioridad ≥ 6.

## 7. Límites duros

- No inventar datos internos (precios, plazos, número de clientes, resultados). Si falta,
  se marca `⚠️ PENDIENTE:` en el borrador.
- Toda cifra externa lleva URL de fuente en el front-matter.
- No prometer resultados ("te curarás", "multiplicarás por 3 tus ventas").
- No copiar estructura ni frases de un competidor: se usa como referencia de qué falta.
- No publicar. El agente deja el fichero en `estado: listo`; publicar es acción humana.
