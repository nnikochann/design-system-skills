# Design System Skills for Codex

Two Codex skills for making UI work start from a documented design system instead of ad hoc styling.

## Skills

- `design-system-research`: audits an existing product UI, component library, website, Figma, screenshots, or brand materials, then writes a compact design-system contract.
- `design-system-from-scratch`: creates a new design system from a product brief and references before high-fidelity UI implementation starts.

Both skills are built around the same rule: write `docs/design-system/manifest.json` and companion documentation before implementing polished UI.

## Why

These skills are meant to reduce generic AI UI output by forcing the agent to establish:

- source evidence or product intent;
- semantic tokens;
- component rules and gaps;
- layout and responsive rules;
- accessibility and governance policy;
- explicit anti-patterns.

## Install

Copy either skill folder into your Codex skills directory:

```sh
mkdir -p ~/.codex/skills
cp -R skills/design-system-research ~/.codex/skills/
cp -R skills/design-system-from-scratch ~/.codex/skills/
```

For a project-local setup, copy them into the repository's agent skills directory:

```sh
mkdir -p .agents/skills
cp -R skills/design-system-research .agents/skills/
cp -R skills/design-system-from-scratch .agents/skills/
```

## Usage

Ask Codex to use the skill explicitly:

```text
Use $design-system-research to audit this app UI and create docs/design-system artifacts.
```

```text
Use $design-system-from-scratch to define a design system for this new product from the brief and references.
```

## Suggested Project Rule

Add a rule like this to your project instructions if you want every UI task to respect the design-system workflow:

```md
For UI, frontend components, dashboards, app screens, redesigns, CSS, Tailwind, shadcn, animations, responsive layout, Figma, screenshots, brand references, or public site references:

1. Do not generate UI immediately.
2. If existing UI, component library, website, Figma, screenshots, or brand material should constrain the work, use $design-system-research first.
3. If the product has no stable UI and the task is to invent a new system, use $design-system-from-scratch first.
4. Create or update docs/design-system/manifest.json and docs/design-system/design-system.md before high-fidelity implementation.
5. Reuse existing components and tokens before adding new ones.
6. End UI work with visual QA notes, verification commands, and design-system deviations.
```

## Repository Structure

```text
skills/
  design-system-from-scratch/
    SKILL.md
    agents/openai.yaml
    references/
  design-system-research/
    SKILL.md
    agents/openai.yaml
    references/
```

## License

MIT
