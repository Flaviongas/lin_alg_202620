# AGENTS.md

Course slides for Álgebra Lineal (Universidad Autónoma de Chile, semestre 2026), in Spanish. Each numbered directory (`1/`, `2/`, ...) is one class session with a `class.qmd` (Quarto revealjs deck), a PDF/txt of the source problem set, and sometimes `teacher_instructions.md`.

## Build & render

- Render a deck: `quarto render 2/class.qmd` (from repo root). Generates `class.html` + `class_files/`.
- Never commit anything

## Conventions

- **YAML header:** copy the block in `header.yaml` (revealjs, `transition: zoom`, `katex`, small-font `<style>`). Do not change format options.
- **Slide body style:** follow `reference.qmd` at repo root — one `##` slide per exercise, `## ` (empty heading) continues to the next slide, `####` subheadings inside a solution, prose explaining each step before the math.
- **Exercise statements:** list the required steps as bullets, NOT numbered items. Name `####` subheadings descriptively (e.g. `#### Sistema asociado`), not numbered (`#### 1. ...`).
- **No tables, no emojis** in slide content (convert tables from the source PDF into prose).
- Content is written in Spanish.

## Verifying math answers

Bash rules deny `py*` commands directly; run Python through a temp script under nix-shell:
```
nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"
```
