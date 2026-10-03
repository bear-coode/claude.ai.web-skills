Content from the zip file `questionnaire-solver.skill`:

## File: questionnaire-solver\SKILL.md

---
name: questionnaire-solver
description: Responde cuestionarios (opción múltiple, verdadero/falso, "marca el incorrecto") basándose únicamente en el material que el usuario adjunta (PDF, PPT, MD, texto), entregando solo la respuesta. Úsala siempre que el usuario diga que debe resolver un cuestionario, test, examen, quiz o preguntas "en base a" un material, o envíe preguntas con opciones A/B/C/D, aunque no mencione esta skill. Invócala también si pega preguntas una por una después de haber enviado un material.
---

# Questionnaire Solver

Responde preguntas de cuestionario usando el material del usuario como fuente principal. El usuario quiere velocidad y exactitud: la respuesta, nada de relleno, y cero información inventada.

## Flujo

1. **Material primero.** Si el usuario envía el material sin preguntas, responde en una línea que estás listo y pide las preguntas. No resumas el material.
2. **Una pregunta, una respuesta.** Cada pregunta nueva se responde de inmediato, sin preámbulo ni cierre.
3. **Fuente de verdad.** Responde con lo que dice el material. Interpreta el enunciado (p. ej. "marca el incorrecto", "la que no aparece") y descarta por contraste con el material.

## Cuándo buscar fuera del material

Solo en estos casos:
- La pregunta lo pide explícitamente.
- El material no cubre el tema (y el usuario no dio otra fuente).
- Aun teniendo material, es realmente necesario para responder con certeza.

Si buscas, haz lo mínimo (una búsqueda rápida suele bastar) y prioriza fuentes oficiales de la plataforma o institución mencionada.

## Cuando no se puede responder

No inventes. Si el material no cubre la pregunta y tampoco puedes verificarla fuera, dilo de inmediato en una línea y no elijas opción. Si la pregunta exige abrir una plataforma que no puedes usar (p. ej. "pasa el cursor sobre...", "configura Perú..."), responde con lo que el material y fuentes oficiales permitan y declara que no pudiste verificarlo en la plataforma.

## Formato de salida

```
**Opción X: [texto breve de la opción]**

([Una línea: en qué se basa. Si salió del material, indícalo; si es externo, dilo; si no se pudo verificar, dilo.])
```

Reglas:
- La respuesta va en negrita, con la letra de la opción.
- La línea entre paréntesis es breve (1-2 oraciones) y cita el dato clave, no explica de más. Sirve para que el usuario confíe en la respuesta.
- Sin saludos, sin validaciones, sin ofrecer ayuda adicional, sin repetir el enunciado.
- Respuesta abierta (no opción múltiple): da solo la respuesta, en la menor extensión que sea correcta, con la misma línea de base.
- Responde en el idioma del usuario.

## Ejemplos

**Ejemplo 1** (cubierto por el material)
Pregunta: STATISTA - Marca el incorrecto en la barra superior: A) Statistics B) Insights C) Research Investigation D) Services
Salida:
**Opción C: Research Investigation**

(El material menciona "Research AI", no "Research Investigation".)

**Ejemplo 2** (no cubierto, verificado fuera)
Pregunta: Marca el menú incorrecto en INSIGHTS: A) Trade insights B) Ecommerce insights C) Consumer insights D) Market insights
Salida:
**Opción A: Trade insights**

(El material no cubre el menú "Insights"; verifiqué en la web de Statista: ofrece Market, Consumer y eCommerce Insights, no "Trade insights".)

**Ejemplo 3** (no verificable en plataforma)
Pregunta: Marca lo que no aparece en los resultados de Research AI: ... C) Mapa de ubicación de puertos ...
Salida:
**Opción C: Mapa de ubicación de puertos**

(El material indica que Research AI entrega respuesta con fuentes; no menciona mapas. No lo pude verificar en la plataforma.)