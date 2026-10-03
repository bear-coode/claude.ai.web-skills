Content from the zip file `just-do-it.skill`:

## File: just-do-it\SKILL.md

---
name: just-do-it
description: "Activar SOLO con el comando manual \"/just-do-it\". Skill universal: el usuario lanza todo en un mensaje (instrucciones, datos, PDFs, PPTs, links, fichas) y Claude analiza, separa tarea de información, y entrega el resultado listo para usar sin preguntas innecesarias."
---

# Skill: /just-do-it

Skill de ejecución universal. El usuario te lanza TODO en un solo mensaje y tú lo procesas y entregas el resultado listo para usar.

---

## Paso 1 — Leer y clasificar todo lo recibido

Al recibir el mensaje, identifica:

**A) LA TAREA** — ¿Qué hay que hacer?
- Ejemplos: "completa esta ficha", "responde este formulario", "escribe un ensayo sobre X", "haz un resumen", "busca información sobre Y", "llena esta tabla"
- Puede estar explícita ("necesito que...") o implícita (una ficha en blanco = hay que completarla)

**B) LA INFORMACIÓN** — ¿Con qué datos se hace?
- Textos pegados, PDFs subidos, PPTs, imágenes, links, fichas con datos previos, instrucciones del docente, rúbricas, etc.

**C) RESTRICCIONES O FORMATO** — ¿Hay reglas?
- Extensión mínima/máxima, estilo (APA, MLA), idioma, tono (formal/informal), estructura pedida

Si algo no queda claro pero **es realmente necesario para poder hacer la tarea** (no solo conveniente), haz UNA sola pregunta breve antes de proceder. Si puedes asumir algo razonable, hazlo y menciona el supuesto al entregar.

---

## Paso 2 — Identificar el tipo de entrega

Elige el formato de salida según la tarea:

| Tipo de tarea | Cómo entregar |
|---|---|
| **Formulario / cuestionario** | Solo las respuestas (letra o texto), numeradas igual que las preguntas. Sin repetir el enunciado. |
| **Ficha para completar** | Cada campo con su etiqueta y el contenido listo para copiar/pegar. Si piden imagen: da el prompt para generarla o dónde conseguirla. |
| **Ensayo / trabajo académico** | Artifact Markdown o Word (.docx) según extensión. Si es largo (>2 páginas), genera archivo descargable. |
| **Tesis / informe largo** | Siempre archivo Word o PDF descargable, con portada, índice, secciones, referencias. |
| **Resumen / análisis** | Respuesta directa en chat si es corto. Artifact si supera ~500 palabras o lo pide el usuario. |
| **Tabla / comparativa** | Tabla visual en chat o artifact según tamaño. |
| **Presentación (slides)** | Usa Canva MCP si está disponible, o genera PPTX descargable. |
| **Búsqueda web requerida** | Usa web_search. Prioriza fuentes confiables de los últimos 4 años (journals, webs oficiales, repositorios académicos). Cita siempre. |
| **Diagrama / visualización** | Usa el Visualizer para generar inline. |
| **PDF para entregar** | Genera archivo PDF descargable. |

---

## Paso 3 — Buscar en la web (si la tarea lo requiere)

Si la tarea pide investigar, buscar fuentes, o la información no está en los archivos del usuario:

- Usa `web_search` con queries específicas
- Prioriza: artículos académicos, sitios .edu/.gov, publicaciones de los últimos 4 años
- Cita con formato claro (APA si no se especifica otro)
- Mínimo 3 fuentes para trabajos académicos, salvo que se pida menos

---

## Paso 4 — Ejecutar y entregar

### Reglas de entrega

1. **Ve directo al resultado.** No expliques lo que vas a hacer antes de hacerlo. Hazlo.
2. **Formato limpio.** El usuario debe poder copiar/pegar o descargar sin editar nada.
3. **Si generaste supuestos**, menciónalos brevemente AL FINAL, no al principio.
4. **Si se pide imagen** y no puedes generarla, entrega el prompt exacto para DALL-E, Midjourney, o Adobe Firefly, y/o un link de búsqueda en Unsplash/Freepik según corresponda.
5. **Si la tarea es muy larga**, divide en secciones claramente etiquetadas.

### Preguntar solo si es imprescindible

Solo pregunta cuando sin esa información sea imposible hacer la tarea. Ejemplos de cuándo SÍ preguntar:
- "El formulario pide tu número de DNI / matrícula y no lo encuentro en ningún archivo"
- "La ficha pide la fecha de entrega y no está especificada"

Ejemplos de cuándo NO preguntar (asumir):
- El tono → usa formal si es académico, informal si es conversacional
- La extensión → usa la que pide la rúbrica o un estándar razonable
- El idioma → el mismo del mensaje del usuario

---

## Paso 5 — Casos especiales

### Imágenes pedidas en fichas o formularios
- Si piden "adjuntar foto de perfil" o similar: `[Imagen requerida: foto de perfil del estudiante — no generada por IA]`
- Si piden "imagen ilustrativa sobre X": da un prompt de generación + alternativa en Unsplash

### Links / fuentes específicas pedidas
- Siempre busca en la web. No inventes URLs.
- Si no encuentras una fuente confiable, dilo explícitamente y sugiere dónde buscar.

### Archivos subidos (PDF, PPTX, DOCX, imágenes)
- Léelos completamente antes de responder
- Extrae solo la información relevante para la tarea

### Tesis / trabajos muy extensos
- Genera siempre como archivo descargable (.docx preferido, o .pdf si se pide)
- Incluye: portada, índice, introducción, desarrollo, conclusiones, referencias
- Usa normas APA 7ma edición por defecto salvo indicación contraria

---

## Recordatorio final

Tu objetivo es que el usuario reciba algo listo para usar. No a medias, no con instrucciones de cómo terminarlo. **Listo. Completo. Entregable.**