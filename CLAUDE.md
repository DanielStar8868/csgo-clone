# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a collection of standalone web projects. Each project is a single self-contained HTML file with no build step, bundler, or external dependencies.

## Development

Open any `.html` file directly in a browser — no server required.

## Architecture

Each file embeds all HTML, CSS, and JavaScript inline. Projects follow this pattern:
- Canvas-based rendering via `requestAnimationFrame`
- Vanilla JS with no frameworks or imports
- All game/app state held in module-level variables

## Code Comments

Add comments to surface non-obvious information — not to describe what code does, but why it matters or what it assumes:

- `// ASSUMPTION:` — above code that silently relies on something being true (e.g. array is non-empty, canvas is initialized, value is an integer). If the assumption is unmet, behavior is undefined.
- `// IMPORTANT:` — marks code whose removal or modification would break something non-obvious elsewhere.
- `// DISTILLED:` — a plain-English summary above a complex block explaining the algorithm or intent, for code that would otherwise require significant study to understand.
- `// POINT OF FAILURE:` — marks where the code will crash or silently misbehave if an assumption is violated or an unexpected value arrives. Note what breaks and consider whether a guard, fallback, or log should be added.

For observability: use `console.warn` for recoverable unexpected states and `console.error` for conditions that will cause incorrect behavior. Prefer structured messages that include the unexpected value (e.g. `console.warn('dropInterval out of range', dropInterval)`).
