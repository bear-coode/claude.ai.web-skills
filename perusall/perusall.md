Content from the zip file `perusall.skill`:

## File: perusall\SKILL.md

---
name: perusall
description: Automatiza tareas de lectura en Perusall (responder la pregunta de la profesora y comentar oraciones subrayadas por el usuario). Activar SOLO con el comando manual /perusall. Nunca auto-activar.
license: MIT
compatibility: claude-ai
---

# Perusall: Preguntas de lectura + comentarios de subrayado

Skill para el flujo de trabajo en Perusall (app de lectura académica donde se sube un PDF, se responde una pregunta de comprobación de lectura, y se subrayan oraciones con comentarios).

## Cuándo se usa

Activar SOLO con el comando manual `/perusall`. El usuario puede pedir dos cosas, por separado o juntas:

1. **Responder la pregunta de lectura** que la profesora dejó (normalmente viene en captura de pantalla del panel de comentarios de Perusall, con el nombre de la profesora/instructor y el texto de la pregunta).
2. **Comentar oraciones subrayadas**: el usuario pega el texto exacto que subrayó en el PDF (puede venir cortado, con saltos de línea raros, o texto de OCR con errores menores) y se le da un comentario para cada una.

## Proceso

### Parte 1: Responder la pregunta de lectura

1. Identifica la pregunta exacta (viene de una captura del panel de comentarios de Perusall, o el usuario la escribe directo).
2. Si el material del capítulo ya está en contexto (imágenes subidas, PDF, etc.), úsalo como fuente. Si no está, pide el material — no inventes contenido del libro.
3. Responde de forma completa y directa, en el idioma del material (normalmente español), tono universitario, sin relleno.
4. Si aplica /humanizer en la conversación, se puede combinar, pero /perusall no auto-activa /humanizer ni viceversa — son independientes.
5. Entrega la respuesta lista para copiar/pegar en el campo de texto de Perusall (sin encabezados tipo "Respuesta:", va directo al contenido).

### Parte 2: Comentar oraciones subrayadas

Aquí el usuario es quien decide qué subrayar — no Claude. El flujo es:

1. El usuario pega el fragmento de texto que subrayó (tal cual salga del PDF, con cortes de línea o palabras pegadas por el copy-paste; no hace falta que esté perfecto).
2. Claude identifica la idea central de ese fragmento dentro del contexto del capítulo ya visto en la conversación.
3. Da UN comentario por fragmento, formato:

   **Comentario:**

   [texto del comentario en bloque de codigo]

4. El comentario debe:
   - Explicar por qué esa oración es relevante o qué principio/concepto ilustra.
   - Conectar con otra parte del capítulo cuando aporte (ejemplo, principio relacionado, contraste).
   - Ser específico al fragmento pegado, no genérico. Si el fragmento se corta a media frase, trabaja con la idea que sí se alcanza a leer.
   - 1-3 oraciones. Nada de relleno ("Este es un buen punto porque...", "Es importante notar que...").
5. No subrayes ni sugieras qué subrayar salvo que el usuario lo pida explícitamente. El usuario manda el fragmento, Claude solo comenta.
6. Si el usuario pega varios fragmentos de corrido, se responde uno por uno, no se agrupan en un solo comentario.

## Formato de salida

- Sin preámbulos ni "aquí tienes tu comentario".
- Un comentario = una respuesta corta. Si son varios fragmentos en un mismo mensaje, un comentario por fragmento, separados con claridad.
- Listo para copiar/pegar en el campo de comentario de Perusall.

## Notas

- Esta skill no reemplaza el criterio del profesor. Si las instrucciones del profesor en la pregunta contradicen algo, priorizar siempre lo que pide el profesor.
- Si falta contexto crítico (no se ha compartido el capítulo, o el fragmento no aparece en el material visto), preguntar una sola vez antes de inventar contenido.