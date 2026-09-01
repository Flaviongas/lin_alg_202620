## 1. Preparación y verificación matemática previa

- [x] 1.1 Crear script `/tmp/opencode/verify.py` que calcule con SymPy todos los valores numéricos del deck (determinantes, factorización del polinomio con parámetro, inversas, productos $AX$, soluciones de sistemas) y verificar que no hay discrepancias ejecutando `nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"`
- [x] 1.2 Definir las 5 matrices/sistemas finales con números distintos a clases 1–3 (verificar por diff textual que ningún enunciado es copia literal) y confirmar que $\det\neq 0$ donde se necesita inversa y que las soluciones son enteras o fracciones simples

## 2. Redacción del deck `4/class.qmd` — estructura y ejercicios

- [x] 2.1 Escribir el encabezado YAML copiado de `header-revealjs.yaml` (revealjs, `transition: zoom`, `katex`, estilo 0.70em) con título "Segunda Preparación Evaluación Regular I" y autor "Flavio Jara L.", y verificar por diff que coincide con `header-revealjs.yaml`
- [x] 2.2 Redactar Ejercicio 1 — operaciones y ecuación matricial (tipo $AX+B=C$ o $MX+N=P$) con despeje analítico por lado correcto, desarrollo numérico y verificación $AX=B$, siguiendo bullets, `####` descriptivo y paginación con `## `
- [x] 2.3 Redactar Ejercicio 2 — determinantes $3\times 3$ por cofactores y matriz con parámetro $A(k)$: cálculo de $\det(A(k))$, factorización (Ruffini/raíz racional) y conclusión de valores de $k$ para invertibilidad, con prose antes de cada bloque matemático
- [x] 2.4 Redactar sección breve `## Tipos de sistemas` / `## Clasificación de sistemas` (1–2 slides, no cuenta como ejercicio) que defina compatible determinado / indeterminado / incompatible con criterios de rango y determinante, en prose con bullets y sin tablas, e incluir diagrama árbol/flujo (bloque ```mermaid renderizable en Quarto revealjs, sin imagen externa) que visualice Sistema → Compatible/Incompatible → Determinado/Indeterminado con criterios; verificar que aparece antes del primer ejercicio de Gauss y que `quarto render` no reporta errores de mermaid
- [x] 2.5 Redactar Ejercicio 3 — sistema $3\times 3$ compatible determinado por matriz aumentada y Gauss/Gauss-Jordan, con operaciones $F_i$ anotadas, forma escalonada reducida, lectura de solución y verificación por sustitución
- [x] 2.6 Redactar Ejercicio 4 — sistema con clasificación (incompatible con fila $[0\;0\;0\mid b]$ o indeterminado con variable libre) + cálculo de inversa por Gauss-Jordan $(A\mid I)\to(I\mid A^{-1})$ o resolución $X=A^{-1}B$ con comprobación, usando la terminología introducida en la sección de tipos
- [x] 2.7 Redactar Ejercicio 5 — problema contextualizado $3\times 3$ (producción/mezcla/transporte) con definición de incógnitas, planteamiento del sistema, matriz aumentada, reducción y interpretación en contexto

## 3. Cierre y conformidad de estilo

- [x] 3.1 Añadir slide de cierre `# Gracias por su atención` y verificar que el conteo total de `## Ejercicio` en `4/class.qmd` está entre 5 y 6
- [x] 3.2 Revisar conformidad de estilo: sin tablas Markdown, sin emojis, sin listas numeradas de pasos, sin `#### 1.` numerado, todos los `####` con nombre descriptivo, contenido en español, y paginación con `## ` donde el desarrollo excede un slide — verificar con `grep` sobre `4/class.qmd`
- [x] 3.3 Verificar que la extensión total es menor que clases previas (comparar `wc -l 4/class.qmd` con `1/class.qmd` (279), `2/class.qmd` (328), `3/class.qmd` (256) — debe ser el menor)

## 4. Validación final

- [x] 4.1 Ejecutar `quarto render 4/class.qmd` desde la raíz y verificar que genera `4/class.html` sin errores y que la presentación abre correctamente en navegador
- [x] 4.2 Re-ejecutar `nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"` contra los valores finales de `4/class.qmd` y confirmar cero discrepancias
- [x] 4.3 Ejecutar `openspec validate --change completar-clase-4-segunda-preparacion --strict` y corregir cualquier observación hasta que pase sin errores
