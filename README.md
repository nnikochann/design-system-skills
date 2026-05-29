# Design System Skills for Codex

> Two Codex skills that make frontend work start with a design-system contract, not improvised styling.

[Русская версия](README.ru.md)

## What This Is

This repository contains two lightweight Codex skills for design-system-first UI work:

- `design-system-research` documents the design system that already exists in a product, repo, website, Figma file, screenshots, component library, or brand material.
- `design-system-from-scratch` creates a new design system from a product brief and references before high-fidelity UI implementation begins.

The shared idea is simple: before generating polished screens, Codex should define the visual and component contract it will follow.

That contract usually lives in:

- `docs/design-system/manifest.json`
- `docs/design-system/design-system.md`
- `docs/design-system/component-map.md`
- optional references, screenshots, tokens, and visual-principle docs

## Why It Exists

AI-generated UI often fails for the same reasons:

- random accent colors;
- decorative cards without product logic;
- arbitrary gradients and glass effects;
- inconsistent spacing and typography;
- one-off components that do not fit the rest of the app;
- no source of truth for future changes.

These skills add a deliberate preflight step. Codex has to inspect or define the system first, then implement UI against that system.

## Included Skills

### `design-system-research`

Use this when an existing product should constrain the design:

- a live app or website;
- a component library;
- Figma or screenshots;
- Tailwind, CSS variables, shadcn, Radix, MUI, Chakra, or custom components;
- brand books, decks, or visual references.

The skill inventories evidence, extracts tokens, maps components, documents layout rules, records gaps, and creates design-system artifacts.

### `design-system-from-scratch`

Use this when the product has no stable UI yet:

- greenfield products;
- new startup MVPs;
- app concepts;
- new brands;
- reference-driven visual direction;
- early design-system exploration.

The skill starts from the brief and references, then defines direction, tokens, components, layout, accessibility, visual language, and governance rules.

## Install

Copy the skills into your Codex skills directory:

```sh
mkdir -p ~/.codex/skills
cp -R skills/design-system-research ~/.codex/skills/
cp -R skills/design-system-from-scratch ~/.codex/skills/
```

Or install them locally inside a project:

```sh
mkdir -p .agents/skills
cp -R skills/design-system-research .agents/skills/
cp -R skills/design-system-from-scratch .agents/skills/
```

## Usage

Ask Codex to use a skill explicitly:

```text
Use $design-system-research to audit this app UI and create docs/design-system artifacts.
```

```text
Use $design-system-from-scratch to define a design system for this new product from the brief and references.
```

## Recommended Project Rule

Add something like this to your project instructions if you want every UI task to follow the workflow:

```md
For UI, frontend components, landing pages, dashboards, app screens, redesigns, CSS, Tailwind, shadcn, animations, responsive layout, Figma, screenshots, brand references, or public site references:

1. Do not generate UI immediately.
2. If an existing product, repo UI, component library, website, Figma file, screenshot, or brand material should constrain the work, use $design-system-research first.
3. If the product has no stable UI and the task is to invent a new system from a brief or references, use $design-system-from-scratch first.
4. Create or update docs/design-system/manifest.json and docs/design-system/design-system.md before high-fidelity implementation.
5. Reuse existing components and tokens before introducing new ones.
6. If a token or component is missing, propose it in the manifest instead of hardcoding one-off values.
7. End UI work with visual QA notes, verification commands, and any design-system deviations.
```

## Repository Structure

```text
skills/
  design-system-from-scratch/
    SKILL.md
    agents/openai.yaml
    references/
      manifest-schema.md
      reference-intake.md
  design-system-research/
    SKILL.md
    agents/openai.yaml
    references/
      manifest-schema.md
```

## Design Philosophy

These skills are intentionally compact. They do not try to replace a designer or a full design-system team. They give Codex enough process and guardrails to stop treating UI as decoration and start treating it as a reusable product contract.

The goal is not to make every interface look the same. The goal is to make every interface explainable, consistent, inspectable, and easier to evolve.

## License

MIT
