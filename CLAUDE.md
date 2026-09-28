# CLAUDE.md — Percent Decrease Practice

## What this is
A single-file practice app (`index.html`) for a middle-school student working on McGraw-Hill
"Determine the percent decrease" homework. Hosted on GitHub Pages. No build step, no dependencies
except the Lexend font from Google Fonts.

The app shows the problem and an answer box, and nothing else. The student works the arithmetic
out herself on paper, so there is deliberately no formula, no bar chart, no worked solution and
no mistake-specific hints. Do not add them back.

## Structure (all inside index.html)
- `<style>`: design tokens on `:root` (ink / paper / sky / mint / gold / rose / mark), dark mode via prefers-color-scheme.
- `const PROBLEMS = [...]`: the problem bank. Each item:
  `id, set ("Original" | "Practice"), level ("Basic" | "Standard" | "Challenge"), text, orig, new,
   prefix ("$" or ""), unit, diff, ratio, pct, answer`
  `answer` is what the input is checked against. `diff / ratio / pct` are kept as a record of how
   the answer was derived; nothing displays them.
- Progress is stored in localStorage under `percent-decrease-progress-v1`:
  `{ [id]: { status: "new"|"correct1"|"correct2"|"missed", tries, attempts, last } }`
- Views: Practice and Progress (stats, by-level, per-problem table).
  Practice leads with the problem card and Previous / Next. The 1–37 number grid, the filter and
  the colour legend live inside the collapsed `<details id="picker">` below it, so the student sees
  one problem at a time instead of a wall of buttons. Keep them there.

## Rules
- UI text and problems are in English (the student's class is in English). README is Japanese for the parent.
- Answers: percent decrease = (orig − new) / orig × 100, rounded half-up to 0.1.
  When adding problems, compute answers with exact decimal math (Python `decimal`, ROUND_HALF_UP),
  never by hand, and avoid values that make the rounding depend on floating-point error.
- Problems 1–7 are the original homework; keep their wording unchanged.
- 2 tries per problem, matching McGraw-Hill. A wrong first try says only "Not quite"; a wrong
  second try shows the correct answer and nothing more.
- Keep it a single self-contained file so it works on GitHub Pages and offline.
- Do not change the localStorage key without migrating existing progress.
