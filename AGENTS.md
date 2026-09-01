# AGENTS.md

Course slides for Álgebra Lineal (Universidad Autónoma de Chile, semester 2026), in Spanish. Each numbered directory (`1/`, `2/`, ...) is one class session with a `class.qmd` (Quarto revealjs deck), a PDF/txt of the source problem set, and sometimes `teacher_instructions.md`.

## Build & render

- Render a deck: `quarto render 2/class.qmd` (from repo root). Generates `class.html` + `class_files/`.
- Never commit anything

## Conventions

- **YAML header:** copy the block in `header.yaml` (revealjs, `transition: zoom`, `katex`, small-font `<style>`). Do not change format options.
- **Slide body style:** follow `reference.qmd` at repo root — one `##` slide per exercise, `## ` (empty heading) continues to the next slide, `####` subheadings inside a solution, prose explaining each step before the math.
- **Exercise statements:** list the required steps as bullets, NOT numbered items. Name `####` subheadings descriptively (e.g. `#### Associated system`), not numbered (`#### 1. ...`).
- **No tables, no emojis** in slide content (convert tables from the source PDF into prose).
- Content is written in Spanish.

## Author style — inferred from 4/class.qmd (second preparation)

- **Clarity over brevity:** each elementary row operation on its own line/`$$` with the resulting matrix (`F_i \leftarrow F_i + kF_j \implies (...)`), even if it adds slides/lines beyond the “shorter” limit. The OpenSpec plan expected `<256` lines; the manual style prioritizes granularity (16 `## `, 28 `F_`).
- **Justification before procedure:** explain why before enumerating. E.g. rational candidates preceded by the full rational root theorem (`p` divides constant term, `q` divides leading coefficient → divisors of 6 for `k^3-7k+6` with leading 1) and after Ruffini expand the quotient `q(k)=k^2+k-6` step by step (search for two numbers, discriminant `Δ=25`, roots `2,-3`, recombination `(k-1)(k-2)(k+3)` and verification by expansion).
- **Fraction typography:** always use braced form `\frac{a}{b}`, `\dfrac{a}{b}`, `\tfrac{a}{b}` (never `\frac27`). Outer scalar as `\dfrac{1}{7}\begin{pmatrix}` and dense `3×6` interior fractions as compact `\tfrac{2}{7}`; add vertical breathing room `\\[6pt]` between `\begin{array}` rows to avoid collision with the `0.70em` font.
- **Mermaid diagrams:** always executable cell ` ```{mermaid}` with `%%| fig-align: center`, wrapped in `::: {style="text-align:center; width:80%; margin-left: auto; margin-right: auto;"}`. Labels in quotes (`S["Sistema AX = B"]`, `C{"rg A = rg Ab ?"}`), avoid `|` in nodes (use `Ab` for `A|B`), use correct `<br>` and preserve accents (`Sí`, `única solución`, `Determinado`).
- **Narrative:** prose in Spanish before each `$$` block, one `##` per exercise + `## ` to continue, descriptive `####` headings, bullets `-` never numbered, no tables/emojis.

## Verifying math answers

Bash rules deny `py*` commands directly; run Python through a temp script under nix-shell:
```
nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"
```
