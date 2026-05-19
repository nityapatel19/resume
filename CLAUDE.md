# CLAUDE.md

## Purpose

This repo is a LaTeX resume project. Work happens in `latex/`.

## Structure

- `latex/main.tex` — LaTeX source; this is where all editing takes place
- `resume_additions.md` — source of truth for all resume content; edit here first, then update the LaTeX
- `index.html`, `resume.pdf`, `n.ico` — static site for GitHub Pages hosting; treat as read-only

## Compiling

Requires a LaTeX distribution (TeX Live, MiKTeX, etc.). From `latex/`:

```
pdflatex main.tex
```

## PDFs

- `latex/main.pdf` — compiled on every commit via the pre-commit hook; always reflects the current state of `main.tex`. Tracked in git.
- `resume.pdf` (repo root) — updated manually as a release step only, when a new version is finalized. Do not update automatically or as part of regular commits.

## Pre-commit Hook

`.git/hooks/pre-commit` runs `pdflatex -jobname=main main.tex` and stages `latex/main.pdf` before every commit. If compilation fails, the commit is blocked. Requires pdflatex to be available on PATH.
