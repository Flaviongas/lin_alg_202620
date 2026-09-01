## Why

La clase 4 (`4/class.qmd`) es la segunda sesión de preparación para la Evaluación Regular I y actualmente solo contiene el encabezado YAML sin contenido. Los estudiantes necesitan un repaso final que cubra todo el temario de la evaluación —operaciones con matrices, determinantes, invertibilidad, sistemas lineales y problemas contextualizados— en formato revealjs listo para proyectar. Sin esta clase, la secuencia didáctica queda incompleta a días de la evaluación.

## What Changes

- Completa `4/class.qmd` como deck revealjs con el header de `header-revealjs.yaml` (`transition: zoom`, `katex`, estilo de fuente 0.70em) y título "Segunda Preparación Evaluación Regular I".
- Cubre el temario completo de la evaluación: operaciones con matrices y ecuaciones matriciales, determinantes y propiedades, matriz inversa y condiciones de invertibilidad, determinación de valores de parámetros para invertibilidad, sistemas lineales, matriz aumentada, eliminación de Gauss/Gauss-Jordan, clasificación de sistemas (compatible determinado / indeterminado / incompatible) y problema contextualizado.
- Reutiliza tipos de ejercicios de las clases 1–3 con números distintos para reforzar sin repetir literalmente.
- Mantiene la clase más corta que las anteriores (objetivo ~5–6 ejercicios con sus desarrollos, frente a 7–9 de clases previas), para dejar tiempo de consulta en la sesión.
- Sigue las convenciones de `AGENTS.md` y `reference.qmd`: un `##` por ejercicio, `## ` (vacío) para continuar slide, `####` descriptivos con nombre (no numerados), pasos en bullets (no listas numeradas), prose antes de cada bloque matemático, sin tablas ni emojis, contenido en español.

## Capabilities

### New Capabilities
- `clase-4-segunda-preparacion`: Deck de la clase 4 — segunda preparación para la Evaluación Regular I. Cubre operaciones matriciales, determinantes, invertibilidad con parámetro, sistemas lineales (Gauss/Gauss-Jordan y clasificación) y un problema contextualizado. Define requisitos de contenido, estructura de slides y verificación matemática.

### Modified Capabilities
<!-- No se modifican capabilities existentes; el proyecto no tenía specs previas. -->

## Impact

- **Archivo afectado:** `4/class.qmd` (único archivo editado; no se toca `1/`, `2/`, `3/`).
- **Generados al renderizar:** `4/class.html` + `4/class_files/` (artefactos de `quarto render`, no versionados).
- **Dependencias:** Quarto + revealjs + KaTeX (ya usadas en el repo). Sin nuevas dependencias.
- **Riesgo:** Bajo — contenido docente autocontenido, sin cambios de tooling ni breaking changes.
