Content from the zip file `problem-solver.skill`:

## File: problem-solver\SKILL.md

---
name: problem-solver
description: Resuelve ejercicios y tareas académicas (cálculo, matemática, física, estadística, economía, finanzas, contabilidad) paso a paso, como una persona en una hoja de papel. Úsala siempre que el usuario envíe ejercicios, una tarea o la foto/PDF de un enunciado y pida resolverlo. El formato de entrega lo indica el usuario.
---

# Resolución de ejercicios estilo hoja de papel

Entrega la resolución como si una persona la hubiera escrito a mano en una hoja: solo procedimiento, ordenado, sin adornos.

## Flujo

1. Lee el enunciado completo (si es imagen o archivo, extrae todos los datos y el formulario que traiga).
2. Resuelve y **verifica el resultado** antes de escribir (reemplaza en las condiciones del problema, prueba valores cercanos en inecuaciones).
3. Redacta con el formato de abajo.
4. Entrega en el formato que el usuario indique. Si no indica ninguno, responde en el chat con el mismo estilo. No asumas Word ni ningún archivo.

## Formato de la resolución

- Texto plano. **Sin tablas, sin colores, sin recuadros, sin viñetas decorativas, sin íconos.**
- Una sola fuente (Times New Roman 12), negro, alineado a la izquierda, A4.
- Encabezado mínimo: solo el nombre si el usuario lo dio. Sin portada ni título decorativo.
- Estructura:
  1. **Datos:** variables definidas y datos del enunciado, en líneas cortas.
  2. **Pasos numerados** `1) Qué se calcula`, en negrita, uno por cada cosa que se halla.
  3. Bajo cada paso, una línea por operación, en el orden en que lo haría un estudiante: fórmula → reemplazo → operación → resultado.
  4. Resultados clave del paso en **negrita** (ej. **C(q) = 80q + 900**).
  5. **Comprobación** cuando aporte (reemplazar en la condición, probar q−1 y q en desigualdades).
  6. **Conclusión:** respuesta redactada en 2–4 líneas, respondiendo exactamente lo que pide el enunciado (decisión, cantidad mínima, sobrante/faltante, etc.).
- Ecuaciones en una línea con símbolos Unicode (−, ·, ×, ÷, ≥, >, →, ✓, subíndices ₁ ₂). Nada de LaTeX ni imágenes de ecuaciones.
- Sub-pasos o despejes: sangría pequeña, una operación por línea (ej. `5300 = 80(55) + Cf` → `Cf = 900`).
- **No saltar procedimientos**: ningún despeje, resta o reemplazo queda implícito.
- Sin explicaciones teóricas, sin preámbulos, sin relleno. Justifica solo cuando el enunciado lo exija ("justifique", "argumente").
- Varios ejercicios: numerarlos (**Ejercicio 1**, **Ejercicio 2**…), separados por una línea en blanco.

## Cuando la entrega es un archivo

- **Word:** usa la skill `docx` (docx-js). Párrafos simples, sin tablas, sin estilos de color, sin bordes. Línea en blanco entre pasos.
- **PDF:** usa la skill `pdf` con las mismas reglas.
- Presenta solo el archivo final y un resumen de 3–5 líneas con las respuestas clave. Sin postámbulo.

## Si algo falla

Si el enunciado es ambiguo, faltan datos o la imagen es ilegible, dilo de inmediato y señala exactamente qué falta. Si el planteamiento del usuario es incorrecto, indícalo y resuelve de la forma correcta.

## Ejemplo de referencia

Ver `references/ejemplo.md` (modelo exacto del estilo esperado).

## File: problem-solver\references\ejemplo.md

# Ejemplo de estilo (texto exacto esperado)

Datos:
q = cantidad de pantalones, C = costo total, I = ingreso, U = utilidad (en soles).
C(55) = 5300     C(100) = 8900     Punto de equilibrio: q = 30 → U = 0, es decir I = C
Meta: U > 15% de C     Capital: 6000 soles

**1) Función de costo C(q) = Cu·q + Cf**
Puntos: (55; 5300) y (100; 8900)
Cu = m = (y₂ − y₁)/(x₂ − x₁) = (8900 − 5300)/(100 − 55) = 3600/45 = 80
Reemplazo el punto (55; 5300) en C = 80q + Cf:
    5300 = 80(55) + Cf
    5300 = 4400 + Cf
    Cf = 900
**C(q) = 80q + 900**

**2) Función de ingreso I(q) = p·q**
En el equilibrio (q = 30): I = C
C(30) = 80(30) + 900 = 2400 + 900 = 3300
Entonces I(30) = 3300
p·30 = 3300  →  p = 3300/30 = 110
**I(q) = 110q**

**3) Función de utilidad U(q) = I − C**
U(q) = 110q − (80q + 900)
U(q) = 110q − 80q − 900
**U(q) = 30q − 900**
Verifico: U(30) = 30(30) − 900 = 900 − 900 = 0 ✓

**4) Meta de setiembre: U > 15% de C**
U > 0,15·C
30q − 900 > 0,15(80q + 900)
30q − 900 > 12q + 135
30q − 12q > 135 + 900
18q > 1035
q > 1035/18
q > 57,5
Como q es un número entero de pantalones, el mínimo es q = 58.

Compruebo con q = 57 y q = 58:
q = 57:  U = 30(57) − 900 = 810;   C = 80(57) + 900 = 5460;   0,15(5460) = 819
    810 < 819  → no cumple
q = 58:  U = 30(58) − 900 = 840;   C = 80(58) + 900 = 5540;   0,15(5540) = 831
    840 > 831  → sí cumple

**5) ¿Alcanza el capital?**
El capital necesario es el costo de producir 58 pantalones:
C(58) = 80(58) + 900 = 4640 + 900 = 5540 soles
Capital disponible = 6000 soles
6000 − 5540 = 460
**Sí alcanza, y sobran 460 soles.**

**Conclusión:**
La empresa debe vender como mínimo 58 pantalones en setiembre. Con ello logra una utilidad de S/ 840, mayor al 15% de sus costos (S/ 831), por lo que cumple la meta y en octubre continuará con la línea ecológica (no la suspende). El capital de S/ 6000 sí le alcanza, pues necesita S/ 5540 y le sobran S/ 460.