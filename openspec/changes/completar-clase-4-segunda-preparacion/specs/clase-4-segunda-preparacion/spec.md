## Purpose

Segunda preparación para la Evaluación Regular I de Álgebra Lineal: un deck revealjs autocontenido que repasa todo el temario de la evaluación mediante ejercicios resueltos paso a paso y un problema contextualizado, siguiendo las convenciones del curso y con extensión menor que las clases previas.

## ADDED Requirements

### Requirement: Encabezado y formato del deck
El deck SHALL usar el encabezado de `header-revealjs.yaml` (formato revealjs, `transition: zoom`, `html-math-method: katex`, estilo de fuente 0.70em para `p,ul`) y SHALL titularse "Segunda Preparación Evaluación Regular I" con autor "Flavio Jara L.", y SHALL renderizar correctamente con `quarto render 4/class.qmd`.

#### Scenario: Renderizado del deck
- **WHEN** se ejecuta `quarto render 4/class.qmd` desde la raíz del repositorio
- **THEN** se genera `4/class.html` y `4/class_files/` sin errores de Quarto/KaTeX y el título visible es "Segunda Preparación Evaluación Regular I"

#### Scenario: Encabezado idéntico al patrón del curso
- **WHEN** se compara el bloque YAML de `4/class.qmd` con `header-revealjs.yaml`
- **THEN** los campos `format.revealjs.transition`, `html-math-method` y el bloque `include-in-header` coinciden exactamente

### Requirement: Cobertura del temario de la evaluación
El deck SHALL cubrir todos los temas del temario: operaciones con matrices y ecuaciones matriciales, determinantes y propiedades, matriz inversa y condiciones de invertibilidad, determinación de valores de parámetros para invertibilidad, sistemas de ecuaciones lineales, matriz aumentada y operaciones elementales por filas, resolución por Gauss/Gauss-Jordan, clasificación de sistemas (compatible determinado, compatible indeterminado e incompatible) y planteamiento y resolución de un problema contextualizado mediante sistema lineal.

#### Scenario: Temario completo presente
- **WHEN** un revisor recorre los ejercicios y secciones del deck
- **THEN** encuentra al menos un ejercicio o subsección dedicada a cada uno de los nueve ítems del temario listado

#### Scenario: Problema contextualizado incluido
- **WHEN** se busca el último ejercicio aplicado del deck
- **THEN** existe un problema con enunciado contextualizado (por ejemplo producción, mezcla, transporte o planificación) que define incógnitas, plantea el sistema $3\times 3$, resuelve por matriz aumentada y da interpretación en contexto

### Requirement: Estructura de ejercicios con números nuevos y extensión acotada
El deck SHALL contener entre 5 y 6 ejercicios principales (más cortos que las clases 1–3 que tienen 7–9 ejercicios) y SHALL reutilizar tipos de ejercicios de clases previas pero con números y datos distintos, de modo que no haya duplicación literal de enunciados.

#### Scenario: Conteo de ejercicios
- **WHEN** se cuentan los encabezados `## Ejercicio` en `4/class.qmd`
- **THEN** el total está entre 5 y 6 inclusive

#### Scenario: Números distintos a clases previas
- **WHEN** se comparan los datos numéricos (matrices, vectores, parámetros, términos independientes) de cada ejercicio con los de `1/class.qmd`, `2/class.qmd` y `3/class.qmd`
- **THEN** ningún ejercicio es copia literal; al menos los coeficientes, constantes o el parámetro del ejercicio de invertibilidad son diferentes

### Requirement: Sección explicativa de tipos de sistemas
El deck SHALL incluir una sección breve (1–2 slides, sin contar como ejercicio) que explique la clasificación de sistemas lineales antes de los ejercicios de Gauss, y SHALL definir con prose y bullets —sin tablas— los tres casos: compatible determinado (solución única, $\operatorname{rg}(A)=\operatorname{rg}(A\mid B)=n$ / $\det(A)\neq 0$ para $n\times n$), compatible indeterminado (infinitas soluciones, $\operatorname{rg}(A)=\operatorname{rg}(A\mid B)<n$, variable libre / forma paramétrica) e incompatible (ninguna solución, $\operatorname{rg}(A)\neq\operatorname{rg}(A\mid B)$, fila del tipo $[0\;\cdots\;0\mid b\neq 0]$), con criterio de rangos y mención de la interpretación del determinante cuando aplique. La sección SHALL incluir un diagrama (árbol o flujo) que visualice la clasificación —rama compatible vs. incompatible y, dentro de compatible, determinado vs. indeterminado— con sus criterios, implementado como bloque `mermaid` (nativo de Quarto revealjs) o HTML/CSS inline sin depender de imagen externa, y SHALL respetar las convenciones (sin tablas, sin emojis).

#### Scenario: Sección de tipos presente y concisa
- **WHEN** se recorre el deck de inicio a fin
- **THEN** antes del primer ejercicio de Gauss existe una sección titulada (por ejemplo `## Tipos de sistemas` o `## Clasificación de sistemas`) de 1–2 slides que define los tres tipos con sus criterios de rango/determinante y no usa tablas ni emojis

#### Scenario: Diagrama de clasificación renderizable
- **WHEN** se inspecciona la sección de tipos y se ejecuta `quarto render 4/class.qmd`
- **THEN** la sección contiene un bloque ```mermaid (o equivalente renderizable sin imagen externa) que muestra el árbol Sistema → Compatible / Incompatible → Determinado / Indeterminado con los criterios de rango, y el render no produce errores ni requiere assets externos

#### Scenario: Definiciones verificables en ejercicios posteriores
- **WHEN** se leen los dos ejercicios de sistemas que siguen a la sección
- **THEN** cada uno clasifica explícitamente su sistema usando la terminología introducida (compatible determinado / indeterminado / incompatible) y el criterio correspondiente, de modo que la sección, el diagrama y los ejercicios son coherentes

### Requirement: Ejercicio de operaciones y ecuación matricial
El deck SHALL incluir un ejercicio de operaciones con matrices y despeje de ecuación matricial (tipo $AX+B=C$, $MX+N=P$ o $XA=B$) que exija distinguir multiplicación por izquierda vs. derecha y SHALL mostrar el despeje analítico antes del cálculo numérico.

#### Scenario: Ecuación matricial con no conmutatividad
- **WHEN** el lector sigue el ejercicio de ecuación matricial
- **THEN** ve el despeje simbólico (por ejemplo $X=A^{-1}(C-B)$ o $X=(P-N)M^{-1}$) explicado con la no conmutatividad, seguido del cálculo numérico completo y verificación

### Requirement: Ejercicio de determinante y condición de invertibilidad con parámetro
El deck SHALL incluir un ejercicio que calcule $\det(A(k))$ o $\det(A(m))$ para una matriz con parámetro, factorice el polinomio y determine los valores del parámetro para los cuales la matriz es invertible / no invertible, y SHALL clasificar el sistema asociado cuando corresponda.

#### Scenario: Parámetro y factorización
- **WHEN** se revisa el ejercicio de parámetro
- **THEN** se encuentra el cálculo del determinante, la factorización (raíz racional/Ruffini o equivalente) y la conclusión explícita del tipo "invertible si y solo si $k\neq\ldots$" o "no invertible cuando $k=\ldots$"

#### Scenario: Determinante $3\times 3$ con expansión por cofactores
- **WHEN** el ejercicio calcula un determinante $3\times 3$
- **THEN** muestra la expansión por cofactores (indicando fila/columna elegida) y el valor numérico verificado

### Requirement: Ejercicios de sistemas lineales con Gauss y clasificación
El deck SHALL incluir al menos dos sistemas resueltos por matriz aumentada y operaciones elementales: uno con solución única (compatible determinado) y uno que ilustre el caso incompatible o compatible indeterminado, con clasificación explícita y lectura de la solución desde la forma escalonada reducida, y SHALL incluir un ejercicio de inversa por Gauss-Jordan o de resolución vía $X=A^{-1}B$ con verificación $AX=B$.

#### Scenario: Sistema compatible determinado por Gauss
- **WHEN** se sigue el ejercicio de sistema determinado
- **THEN** se ve la matriz aumentada, las operaciones $F_i\leftarrow F_i+kF_j$ anotadas, la forma escalonada reducida y la solución única verificada por sustitución

#### Scenario: Clasificación de sistema (incompatible o indeterminado)
- **WHEN** se sigue el segundo ejercicio de sistema
- **THEN** la reducción produce una fila del tipo $[0\;0\;0\mid b\neq0]$ (incompatible) o una variable libre con forma paramétrica (indeterminado), y el texto clasifica el sistema con esa terminología

#### Scenario: Inversa o $X=A^{-1}B$ con Gauss-Jordan
- **WHEN** se revisa el ejercicio de inversa
- **THEN** se muestra el proceso $(A\mid I)\to(I\mid A^{-1})$ o el cálculo $X=A^{-1}B$ con producto matricial explícito y comprobación $AX=B$

### Requirement: Convenciones de estilo y verificación matemática
El deck SHALL seguir las convenciones de `AGENTS.md` y `reference.qmd`: un slide `##` por ejercicio, `## ` (encabezado vacío) para continuar al siguiente slide, subencabezados `####` descriptivos (no numerados como "1."), pasos en bullets (no listas numeradas), prosa explicativa antes de cada bloque matemático, contenido en español, sin tablas ni emojis. Todos los cálculos numéricos SHALL ser verificados (determinantes, inversas, productos y soluciones de sistemas) mediante script reproducible bajo `nix-shell -p python3Packages.sympy`.

#### Scenario: Estilo de slides conforme
- **WHEN** se inspecciona el Markdown de `4/class.qmd`
- **THEN** no hay listas numeradas de pasos, no hay `#### 1.` o similares, no hay tablas Markdown ni emojis, todos los `####` tienen nombre descriptivo, y los `## ` vacíos se usan para paginar soluciones largas

#### Scenario: Verificación matemática reproducible
- **WHEN** se ejecuta el script de verificación en `nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"`
- **THEN** todos los determinantes, inversas, productos $AX$ y soluciones de sistemas del deck coinciden con los valores del script sin discrepancias
