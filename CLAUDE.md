# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a document-authoring repository, not a software project. It contains a LaTeX manual — "Good Practices for AI-Assisted Coding" — produced for the ONDA Lab (Open methodologies for Neurorehabilitation and Data Analysis), plus supporting reference material. There is no source code, build system, or test suite to run.

## Repository contents

- `Good_Practices_AI_Coding.tex` — the manual itself, the main content file. Rendered with `pdflatex` (noted in a comment at the top of the file).
- `Good_Practices_AI_Coding.pdf` — the compiled output, committed to the repo.
- `Figures/` — images referenced by the `.tex` file via `\includegraphics` (logos, opening illustration).
- `BetterCodeBetterScience_Summary.md` / `.pdf` — a standalone bullet-point summary of Russell Poldrack's *Better Code, Better Science*, used as background reference material, not part of the manual itself.
- `DEVELOPMENT_LOG.md` — records the editorial decisions, conceptual framing, and iteration history behind the manual. Read this before making substantive edits to the `.tex` content — it explains *why* sections are structured the way they are, including caveats (e.g. the "predict → observe → update loop" is explicitly *not* a named established framework and should not be cited as one).
- `README.md` — one-line project description.

## Working with the LaTeX manual

- Compile with `pdflatex` (per the in-file comment), not `xelatex`.
- Encoding is `utf8` (via `inputenc`) to support Italian characters — do not revert to `latin1`.
- Custom commands defined in the preamble: `\mybox{}` (grey rounded box, tikz), `\Hint{}` (bordered box, tikz), `\code{}` (monospace), `\oq`/`\cq` (curly quotes).
- Section structure follows a deliberate progression (see `DEVELOPMENT_LOG.md` for the rationale): Introduction → The Core Problem (Bloom's Taxonomy framing) → Define the Problem First (universal prerequisite) → Practices for Experienced Programmers → Practices for Junior Researchers → Using LLMs and Privacy → Quick Reference table. New sections should generally slot into this progression rather than being appended arbitrarily.
- The title page carries an explicit AI-collaboration disclaimer (drafted with Claude, author retains editorial ownership) — preserve this framing if the title page is edited.
- Generated build artifacts (`.aux`, `.log`, `.out`, `.toc`, `.synctex.gz`) are present in the working tree but matched by `.gitignore`; don't treat them as source.

## Companion presentation (lives outside this repo)

`DEVELOPMENT_LOG.md` references a companion Quarto/Beamer slide deck (`AI_assisted_coding.qmd`) that mirrors this manual's content, located in a sibling `Presentations/2025-05-AI-assited-coding/` directory outside this repository. If asked to keep the manual and presentation in sync, note that the two live in different repos/folders.
