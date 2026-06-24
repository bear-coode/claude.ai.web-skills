---
name: prezi
description: "Skill manual activada ÚNICAMENTE con el comando \"/prezi\". Automatiza la creación de presentaciones: el usuario adjunta todo su material en un solo mensaje, Claude analiza, separa instrucciones de contenido, detecta si hay plantilla o no, y entrega todo listo para usar. Usar siempre que el usuario escriba \"/prezi\"."
---

# Prezi — Automatizador de Presentaciones

## Activación

Esta skill se activa **únicamente** con el comando `/prezi`.

Cuando se activa, Claude recibe en un solo mensaje todo el material del usuario y realiza el proceso completo sin interrupciones (salvo que falte información crítica).

---

## Paso 1 — Analizar el material recibido

Al recibir el mensaje con `/prezi`, Claude debe:

1. **Leer y procesar cada archivo adjunto** (PDFs, PPTs, Word, imágenes, texto pegado, etc.)
2. **Separar claramente dos cosas:**
   - **Instrucciones**: lo que el profesor o usuario pide que tenga la presentación (tema, estructura, extensión, enfoque, requisitos de entrega, etc.)
   - **Contenido**: el material informativo que se usará para construir las slides (apuntes, artículos, fichas, libros, PPTs de clase, etc.)
3. **Detectar automáticamente si hay plantilla** (archivo PPT/PDF que define la estructura visual que debe completarse)
4. **Evaluar si se necesitan fuentes externas** ANTES de generar la presentación:
   - ¿Las instrucciones del profesor exigen fuentes o bibliografía?
   - ¿El usuario pide explícitamente links o referencias?
   - ¿El tema requiere respaldo externo evidente?
5. **Si algo crítico no está claro → preguntar antes de continuar.** Si es interpretable, proceder con la opción más razonable e indicarlo.

---

## Paso 2 — Fuentes externas (solo si aplica)

Si se detecta necesidad de fuentes externas:

- Usar `web_search` para buscar fuentes reales y verificadas
- Priorizar: Google Scholar, repositorios universitarios, organismos internacionales, museos, sitios institucionales
- Solo fuentes de los **últimos 4 años** salvo que el tema requiera fuentes históricas específicas
- **Nunca inventar URLs ni citar links que no se hayan verificado**
- Si no se encuentran fuentes confiables suficientes → indicarlo al usuario antes de continuar
- Incorporar las fuentes al contenido de las slides correspondientes

Si **NO** se necesitan fuentes → silencio total. No mencionar este paso.

---

## Paso 3 — Detectar opción y entregar

### 🔀 DOS OPCIONES SEGÚN LO QUE SE RECIBA

---

### 📌 OPCIÓN A — Sin plantilla

**Cuándo aplica:** El usuario mandó material e instrucciones pero no hay plantilla definida.

**Qué entrega Claude:** Dos bloques separados.

---

#### SECCIÓN 1 — Contenido completo para pegar en Gamma

Por cada slide, con este formato exacto:

```
Diapositiva [N]: [Título]

Contenido:
[Texto principal de la slide — listo para copiar y pegar en Gamma]

Prompt de imagen para Gamma:
[Descripción detallada en inglés optimizada para AI Image de Gamma,
siempre terminando con: Wide 16:9 horizontal format]

Notas del presentador:
[Lo que dirías en voz alta durante la presentación]

⚠️ [AGREGAR MANUALMENTE]: [Instrucción específica, si aplica]
```

---

#### SECCIÓN 2 — Miniprompt final personalizado

Separado del contenido. Listo para pegar en el chat de Gamma **después** de haber pegado todo el contenido.

Formato exacto:

```
🔧 MINIPROMPT FINAL PERSONALIZADO — Pegar en el chat de Gamma después de haber pegado todo el contenido:

DESIGN: Apply a cohesive theme using [COLORES EXACTOS con códigos hex], consistent typography and layout across all slides. The mood should be [MOOD ESPECÍFICO].

IMAGES: Analyze the content of each slide individually and generate an AI image that matches exactly the information of that slide. For example:

Slide 1 should show [DESCRIPCIÓN ESPECÍFICA]
Slide 2 should show [DESCRIPCIÓN ESPECÍFICA]
Slide N should show [DESCRIPCIÓN ESPECÍFICA]

Place each image so it complements the text without covering important information.

CONSISTENCY: The logo and visual identity from slide 1 ([DESCRIPCIÓN EXACTA DEL LOGO O IMAGEN PRINCIPAL]) must appear consistently throughout the presentation wherever relevant.

FORMAT: Make sure every single slide is in 16:9 horizontal format. Fix any misaligned or displaced element so everything looks clean and well distributed.

CANVA COMPATIBILITY: Use only basic and standard elements such as text boxes, images, simple shapes and solid color backgrounds. Do not use animations, transitions, special effects, embedded videos or any element that could break or disappear when exported to Canva. Keep the layout simple and clean so it imports perfectly into Canva.
```

---

#### Flujo de trabajo OPCIÓN A (para indicarle al usuario):

```
PASO 1: Copia y pega el BLOQUE 1 completo en Gamma
PASO 2: Gamma genera el diseño inicial
PASO 3: Copia y pega el BLOQUE 2 en el chat de Gamma
PASO 4: Gamma corrige diseño, imágenes, formato y consistencia
PASO 5: Descarga desde Gamma
PASO 6: Abre en Canva para retoques finales
```

---

### 📌 OPCIÓN B — Con plantilla

**Cuándo aplica:** El usuario adjuntó una plantilla (PPT o PDF) que define la estructura visual que debe completarse.

**Qué entrega Claude:** Toda la información ordenada slide por slide, lista para que el usuario seleccione y copie lo que necesita.

---

#### Reglas de entrega OPCIÓN B:

- Analizar la plantilla slide por slide e identificar cada campo que debe completarse
- Presentar la información en el mismo orden que aparece en la plantilla
- **Las indicaciones de Claude van SIEMPRE antes de la sección a la que se refieren, nunca dentro**
- Si la plantilla pide imágenes:
  - **Imagen con IA** → indicación breve antes del prompt + prompt listo para pegar en Gemini, DALL·E o Midjourney
  - **Imagen a buscar** → palabras clave de búsqueda + enlace sugerido donde encontrarla (verificado con web_search)

---

#### Formato de entrega OPCIÓN B:

```
[Indicación de Claude si necesita decirte algo sobre esta slide — SIEMPRE ANTES DE LA SECCIÓN]

═══════════════════════════════════════════
SECCIÓN [N] — SLIDE [N]: [NOMBRE DE LA SLIDE]
═══════════════════════════════════════════

[Campo 1 tal como aparece en la plantilla]:
[Contenido completo listo para usar]

[Campo 2 tal como aparece en la plantilla]:
[Contenido completo listo para usar]

[Campo N tal como aparece en la plantilla]:
[Contenido completo listo para usar]

═══════════════════════════════════════════

[Si hay imagen que generar con IA, Claude lo indica ANTES del prompt]

PROMPT DE IMAGEN — SLIDE [N]:
[Prompt listo para pegar en Gemini, DALL·E o Midjourney]

[Si hay imagen que buscar, Claude indica las palabras clave y un enlace sugerido]
```

---

## Reglas generales

- Si falta información clave → preguntar antes de generar
- Si no hay plantilla → aplicar OPCIÓN A automáticamente
- Si hay plantilla → aplicar OPCIÓN B automáticamente
- Si algo requiere hacerlo el usuario → marcarlo con ⚠️ AGREGAR MANUALMENTE
- Si el material es ambiguo → interpretar la opción más razonable e indicarlo
- Si hay conflicto entre archivos → priorizar las instrucciones del profesor
- Si hay consistencia visual entre slides → indicarlo en el miniprompt final personalizado (solo OPCIÓN A)
- El miniprompt final solo aplica en OPCIÓN A, siempre separado del contenido y personalizado al tema, colores, logo y contenido real de la PPT
- Las indicaciones en OPCIÓN B van SIEMPRE antes de la sección, nunca dentro
- **Nunca inventar fuentes, links ni URLs** — si se usan fuentes externas, deben haber sido verificadas con web_search
