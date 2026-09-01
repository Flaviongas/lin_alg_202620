## Context

El repo contiene tres clases previas en `1/`, `2/`, `3/` (cada una con `class.qmd` compilable vía `quarto render`) y un `4/class.qmd` vacío con solo el header YAML. Las clases 1–3 cubren progresivamente matrices, determinantes, sistemas y problemas contextualizados; la clase 4 debe cerrar el ciclo como repaso final antes de la evaluación. Ver `proposal.md` — Why para la motivación y `specs/clase-4-segunda-preparacion/spec.md` para los requisitos.

Restricciones: header fijo de `header-revealjs.yaml`, estilo de `reference.qmd` y `AGENTS.md` (no tablas, no emojis, bullets no numerados, `####` descriptivos, paginación con `## `), verificación matemática vía `nix-shell -p python3Packages.sympy`, y extensión menor que clases previas.

## Goals / Non-Goals

**Goals:**
- Entregar un `4/class.qmd` completo, autocontenido y renderizable que repase todo el temario en 5–6 ejercicios con desarrollos paso a paso.
- Reutilizar tipos de ejercicios de clases 1–3 con números distintos para reforzar sin duplicar.
- Mantener verificabilidad matemática total y conformidad estricta con las convenciones del curso.
- Dejar tiempo de consulta en la sesión al ser más corta que las anteriores.

**Non-Goals:**
- No se modifican `1/class.qmd`, `2/class.qmd`, `3/class.qmd`, `reference.qmd` ni headers.
- No se añaden dependencias, tooling nuevo ni cambios de configuración de Quarto.
- No se crean guías `teacher_instructions.md` para esta clase (no requeridas por el temario).
- No se aborda contenido fuera del temario (por ejemplo autovalores, espacios vectoriales).

## Decisions

### Decisión 1: Estructura del deck en 5 ejercicios + cierre
**Elección:** 5 ejercicios principales que mapean el temario en bloques: (1) operaciones y ecuación matricial, (2) determinantes $3\times3$ + parámetro/invertibilidad, (3) sistema $3\times3$ compatible determinado por Gauss, (4) sistema con clasificación (incompatible/indeterminado) + inversa por Gauss-Jordan o $X=A^{-1}B$, (5) problema contextualizado $3\times3$. Cierre con slide de agradecimiento.

**Alternativas consideradas:**
- 6 ejercicios separando determinante y parámetro en dos ejercicios independientes → descartado: alarga el deck y rompe el objetivo "más corta"; el parámetro ya exige calcular un determinante.
- 7+ ejercicios replicando clase 2 → descartado: contradice el requisito de brevedad y deja sin tiempo de consulta.
- 4 ejercicios fusionando Gauss y Gauss-Jordan → descartado: no deja espacio suficiente para mostrar clasificación de sistemas, que es parte explícita del temario.

**Rationale:** 5 ejercicios cubren los 9 ítems del temario sin redundancia, mantienen el conteo dentro de 5–6 y dejan ~15–20 min de consulta en una sesión de 90 min.

### Decisión 2: Selección de matrices y números nuevos con verificación previa
**Elección:** Elegir matrices con determinantes pequeños no nulos (ej. $\pm 2,\pm 4$) para que la inversa tenga fracciones simples, y un polinomio cúbico con raíz entera evidente para el ejercicio de parámetro (similar al de clase 3 pero con coeficientes distintos). Todos los valores se verifican antes de escribir mediante script SymPy en `/tmp/opencode/verify.py`.

**Alternativas:**
- Números aleatorios grandes → descartado: fracciones engorrosas que dificultan la pizarra.
- Reutilizar matrices idénticas de clases previas → descartado: viola el requisito de números distintos.

**Rationale:** Facilita el cálculo manual en clase y asegura corrección; el script previo evita erratas que son comunes en determinantes $3\times 3$.

### Decisión 3: Estilo de paginación y notación
**Elección:** Un `## Ejercicio N` por ejercicio, con `## ` (vacío) para cada paso adicional de la solución; `####` descriptivos como `#### Sistema asociado`, `#### Cálculo del determinante`, `#### Factorización`, `#### Clasificación`; bullets con `-` para pasos requeridos; prose breve antes de cada bloque `$$...$$`.

**Alternativas:**
- Un slide por paso con `##` numerado → descartado: rompe la convención de `reference.qmd` y dificulta la navegación.
- `#### 1. ...` numerado → descartado: prohibido por `AGENTS.md`.

**Rationale:** Consistencia visual con clases 1–3 y cumplimiento literal de las convenciones del proyecto.

### Decisión 4: Problema contextualizado de cierre
**Elección:** Problema de producción/mezcla con 3 incógnitas y sistema $3\times 3$ determinado, con interpretación final en contexto (unidades enteras o discusión de fracciones si aparecen).

**Alternativas:**
- Problema de transporte/cafetería → válido pero ya usado en clase 2; producción es el más genérico y reutilizable.
- Sistema $2\times 2$ contextualizado → descartado: no ejercita la matriz aumentada $3\times 3$ que es el foco de la evaluación.

## Risks / Trade-offs

- **Riesgo: Errata numérica en determinantes/inversas** → Mitigación: script SymPy obligatorio que calcula determinantes, inversas, productos $AX$ y soluciones de sistemas antes de redactar; se guarda como evidencia en `/tmp/opencode/verify.py`.
- **Riesgo: Deck demasiado largo pese al límite de 5–6 ejercicios** → Mitigación: cada ejercicio acotado a 2–4 slides (total objetivo ~18–22 slides); si un desarrollo se extiende, se recorta prose redundante antes que añadir slides.
- **Riesgo: Números nuevos generan fracciones incómodas** → Mitigación: selección intencional de matrices con $\det=\pm 1,\pm 2,\pm 4$ y sistemas con solución entera; verificación previa lo confirma.
- **Trade-off: Reutilizar tipos de ejercicios vs. originalidad** → Se prioriza la reutilización pedagógica (refuerzo) con variación numérica; la originalidad total no es objetivo de un repaso.
- **Riesgo: Inconsistencia de header** → Mitigación: copiar literalmente el bloque de `header-revealjs.yaml`; validación por diff en tareas.

## Migration Plan

1. Escribir `4/class.qmd` completo en una sola edición (sin commits intermedios de contenido parcial).
2. Verificar matemática con `nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"`.
3. Renderizar con `quarto render 4/class.qmd`.
4. Rollback: restaurar `4/class.qmd` al header vacío (15 líneas) si el contenido no satisface revisión.

## Open Questions

- Ninguna — el temario, la extensión, los tipos de ejercicios y las convenciones están completamente definidos por el input del usuario y los archivos de referencia.
