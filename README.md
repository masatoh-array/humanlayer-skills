# skills

Skills from [HumanLayer](https://humanlayer.dev), packaged in this fork for Claude Code and Codex.

## Installation

### Codex plugins

This fork provides all seven plugins through a Codex marketplace. The Codex and Claude Code plugins share the existing `skills/` directories; the Claude Code manifests and skill instructions are unchanged.

Register the marketplace with a Codex CLI that supports plugins:

```bash
codex plugin marketplace add masatoh-array/humanlayer-skills --ref main
```

Install only the plugins you need:

```bash
codex plugin add rpi@humanlayer-skills
codex plugin add improve-claude-md@humanlayer-skills
codex plugin add narrow-react-prop-types@humanlayer-skills
codex plugin add build-iterated-agentic-loop@humanlayer-skills
codex plugin add design-control-loop@humanlayer-skills
codex plugin add show-me@humanlayer-skills
codex plugin add visual-pr@humanlayer-skills
```

Start a new Codex session after installation. Invoke skills with `$<skill-name>`, for example `$rpi` or `$show-me`. The `rpi`, `show-me`, and `visual-pr` skills require explicit invocation. `improve-claude-md` still edits `CLAUDE.md`; installing it in Codex does not change its target to `AGENTS.md`.

To update, refresh the marketplace and repeat `codex plugin add` for each installed plugin:

```bash
codex plugin marketplace upgrade humanlayer-skills
codex plugin add rpi@humanlayer-skills
```

### Individual skills (upstream)

The original standalone-skill installation remains available from upstream:

```bash
npx skills add humanlayer/skills --skill SKILLNAME
```

## Available Skills

### rpi

Researches a change, works through design choices with you, and implements it from local documents. Choose design discussion, PRD followed by TDD, technical design, or research followed by implementation. Each phase works in a fresh session by default.

```bash
npx skills add humanlayer/skills --skill rpi
```

Then invoke `/rpi` with your task, or request a step directly:

```text
/rpi research how the collections connect to the database
/rpi make a PRD
/rpi what's next .agents/artifacts/my-change
/rpi implement .agents/artifacts/my-change
```

In Codex, use `$rpi` instead of `/rpi`, for example `$rpi research how the collections connect to the database`. Its default sandbox can make `.agents` read-only; grant the session write access to `.agents/artifacts`, or pass a writable task directory such as `artifacts/my-change`. RPI asks before changing a blocked destination.

### show-me

Explains the current topic with concise diagrams, code-shape sketches, and focused HTML artifacts.

```bash
npx skills add humanlayer/skills --skill show-me
```

Then invoke:

```
/show-me
```

### visual-pr

Creates or updates a pull request with a concise visual outline that helps reviewers understand the change.

```bash
npx skills add humanlayer/skills --skill visual-pr
```

Then invoke:

```
/visual-pr
```

### improve-claude-md

Rewrites your CLAUDE.md using `<important if>` blocks to improve instruction adherence.

```bash
npx skills add humanlayer/skills --skill improve-claude-md
```

Then in your project:

```
/improve-claude-md
```

### narrow-react-prop-types

Narrows React component prop types to match live code paths instead of Storybook, test, or mock-only states.

```bash
npx skills add humanlayer/skills --skill narrow-react-prop-types
```

Then in your project:

```
/narrow-react-prop-types
```

### build-iterated-agentic-loop

Builds a repo-local skill plus an iterated coding-agent GitHub Actions workflow, prompt, memory file, and reference templates.

```bash
npx skills add humanlayer/skills --skill build-iterated-agentic-loop
```

Then in your project:

```
/build-iterated-agentic-loop
```

### design-control-loop

Interviews you to design an agentic control loop — sensor, controller, actuator, and disturbances — tailored to your codebase, then builds it as locally-runnable components plus a scheduled coding-agent workflow.

```bash
npx skills add humanlayer/skills --skill design-control-loop
```

Then in your project:

```
/design-control-loop
```
