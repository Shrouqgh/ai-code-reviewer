# AI Code Review Assistant

An interactive browser tool that reviews code snippets using the Anthropic Claude API; giving instant feedback on readability, structure, and maintainability before a human reviewer looks at the code.

Built it as part of a FDE AI Challenge.

## What it does

Paste a code snippet, select a language, and get:

- **4 scores** (1–10): Readability, Structure, Maintainability, Overall
- **3 improvement findings** — each with a title, explanation, and concrete corrected snippet
- **1 positive note** - what the code already does well
- **A critical flag** - if a real bug or security issue is detected
- **A 2–3 sentence summary** of the code's overall health

Supports (for now): Python, JavaScript, SQL, and R.

## Try it

Open `index.html` in your browser. You'll need an [Anthropic API key](https://console.anthropic.com/).

> **Note:** The API key is sent directly from your browser. This is fine for personal/demo use - do not deploy this publicly without adding a backend proxy.

## How it works

The core is a single prompt that instructs Claude to act as a senior reviewer and return **strict JSON only** — no markdown, no preamble. The JSON schema is specified in the prompt, which makes parsing safe and predictable.

The prompt is in `index.html` inside the `runReview()` function - clearly commented, easy to edit. Tweaking the prompt is how you change review behaviour (e.g. stricter security checks, different scoring dimensions, adding a "test coverage" note).


## Things I'd add in the future

- [ ] Backend proxy so the API key isn't in the browser
- [ ] Side-by-side diff view for the suggestion snippets
- [ ] History of past reviews in the session
- [ ] Additional support for other programming languages
- [ ] Severity threshold config (e.g. "flag anything below 6")
- [ ] Export findings as a markdown comment for GitHub PRs

## Built with

- [Anthropic Claude API](https://www.anthropic.com)
- [Tabler Icons](https://tabler-icons.io) - icon webfont
- Vanilla HTML/CSS/JS - no framework, no build step
