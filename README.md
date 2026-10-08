# glassmorphism-ui

An **Agent Skill** that turns any project's existing UI into a frosted-glass
(glassmorphism) design — **using the colours the project already has**.

No new palette. No new framework. No new build step.

```
┌──────────────────────────────┐      ╭─ glass app bar ─╮
│  ╭──────────────────────╮    │
│  │  frosted glass card  │    │      drifting aurora blobs
│  ╰──────────────────────╯    │      behind every surface
│   ╭────────────────────╮     │
│   │   gradient button  │     │
│   ╰────────────────────╯     │
└──────────────────────────────┘
```

---

## What it does

The skill walks an agent through ten steps:

| # | Step |
| --- | --- |
| 1 | **Recon** — report the stack, theme mechanism and existing colours before writing code |
| 2 | **Derive tokens** — map the project's own colours onto the glass token set |
| 3 | **Aurora background** — the drifting blurred layer that makes glass visible at all |
| 4 | **The glass recipe** — one blurred, saturated, translucent surface with a lit 1px edge |
| 5 | **Motion** — press feedback, entrances, staggering; `transform`/`opacity` only |
| 6 | **Apply** — restyle the components the project already has |
| 7 | **RTL / locale** — logical properties so the layout mirrors automatically |
| 8 | **Gates** — WCAG AA, target sizes, reduced motion, `@supports` fallback |
| 9 | **Pitfalls** — the seven mistakes that make glass look broken or janky |
| 10 | **Deliver** — incrementally, checking in after the first screen |

### Why it is colour-agnostic

The skill never dictates a palette. It gives a **mapping table**:

| Token | Derived from |
| --- | --- |
| `--primary` | the project's brand / accent colour |
| `--blob-1..4` | 3–4 saturated hues derived from that same brand colour |
| `--glass` | the surface colour at ~55% alpha |
| `--ring` | `--primary` at 35–45% alpha |

So a green-branded project ends up with green glass, a red one with red glass —
each keeps its own identity.

---

## Install

The skill is a directory containing `SKILL.md`. Because a skill's directory name
must match its `name`, clone it **as `glassmorphism-ui`**.

### Claude Code

```bash
# project-scoped
git clone https://github.com/hoboho/glassmorphism-ui .claude/skills/glassmorphism-ui

# or user-scoped (available in every project)
git clone https://github.com/hoboho/glassmorphism-ui ~/.claude/skills/glassmorphism-ui
```

### Codex

```bash
# repo-scoped
git clone https://github.com/hoboho/glassmorphism-ui .agents/skills/glassmorphism-ui

# or user-scoped
git clone https://github.com/hoboho/glassmorphism-ui ~/.agents/skills/glassmorphism-ui
```

### Cursor / Copilot / other agents

Paste the contents of `SKILL.md` **without the YAML frontmatter** as a system
prompt or instruction file:

- Cursor → `.cursor/rules/glassmorphism-ui.mdc`
- Copilot → `.github/copilot-instructions.md` (or a prompt file)
- Any chat model → paste it as the first message

### Anywhere, as a plain prompt

```bash
# strip the frontmatter and use it directly
sed '1,/^---$/d; 1,/^---$/d' SKILL.md | pbcopy   # macOS
```

---

## Usage

Once installed, just ask naturally — the `description` field is written to
trigger on these:

> "Make this UI glassy"
> "Add frosted glass to my dashboard"
> "Apply glassmorphism to this project"
> "Modernise this interface"
> "Port this glass design into my app"

Or invoke it explicitly where supported: `$glassmorphism-ui` (Codex) /
`/glassmorphism-ui` (Claude Code).

---

## Live demo

Open [`examples/demo.html`](examples/demo.html) in a browser — a single
self-contained file with no dependencies.

It has two controls:

- **theme** — light / dark
- **accent** — swaps `--primary` and re-derives the whole glass palette on the fly

Switch the accent and watch every surface, glow and gradient follow. That is the
core idea: the glass inherits the project's colour instead of imposing one.

---

## The one thing to remember

> **Glass with nothing behind it is just grey.**

`backdrop-filter` blurs whatever is behind the element. Over a flat background
there is nothing to blur, so the result looks like a translucent grey box.
Always build the **aurora layer first**, then the glass on top.

---

## Compatibility

| | |
| --- | --- |
| Works with | any stack that can edit CSS and markup |
| Network | none required |
| Baseline | `backdrop-filter` with an `@supports` fallback |
| Tested on | Chromium, Safari (iOS), Android WebView |

---

## License

MIT — see [`LICENSE`](LICENSE).
