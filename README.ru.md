# Design System Skills for Codex

> Два навыка для Codex, которые заставляют UI-разработку начинаться с дизайн-системы, а не с случайных стилей.

[English version](README.md)

## Что Это

В репозитории лежат два легких Codex skills для работы с интерфейсами через дизайн-систему:

- `design-system-research` описывает дизайн-систему, которая уже существует в продукте, репозитории, сайте, Figma, скриншотах, библиотеке компонентов или бренд-материалах.
- `design-system-from-scratch` создает новую дизайн-систему из продуктового брифа и референсов до начала high-fidelity реализации.

Общая идея простая: перед тем как генерировать отполированные экраны, Codex должен сначала зафиксировать визуальный и компонентный контракт, которому будет следовать.

Обычно этот контракт живет в:

- `docs/design-system/manifest.json`
- `docs/design-system/design-system.md`
- `docs/design-system/component-map.md`
- дополнительных референсах, скриншотах, токенах и визуальных принципах

## Зачем Это Нужно

AI-интерфейсы часто ломаются по одним и тем же причинам:

- случайные акцентные цвета;
- декоративные карточки без продуктовой логики;
- произвольные градиенты и glass-эффекты;
- непоследовательные отступы и типографика;
- одноразовые компоненты, которые не живут вместе с остальным приложением;
- нет источника правды для следующих изменений.

Эти skills добавляют обязательный предварительный шаг. Codex сначала исследует или проектирует систему, а уже потом реализует UI по этой системе.

## Навыки Внутри

### `design-system-research`

Используйте, когда существующий продукт должен ограничивать дизайн:

- живое приложение или сайт;
- библиотека компонентов;
- Figma или скриншоты;
- Tailwind, CSS variables, shadcn, Radix, MUI, Chakra или кастомные компоненты;
- брендбуки, презентации или визуальные референсы.

Навык инвентаризирует источники, извлекает токены, описывает компоненты, фиксирует правила layout, записывает gaps и создает артефакты дизайн-системы.

### `design-system-from-scratch`

Используйте, когда у продукта еще нет стабильного UI:

- greenfield-продукты;
- новые MVP;
- концепты приложений;
- новые бренды;
- визуальное направление из референсов;
- раннее проектирование дизайн-системы.

Навык начинает с брифа и референсов, затем определяет направление, токены, компоненты, layout, accessibility, визуальный язык и правила развития системы.

## Установка

Скопируйте skills в директорию Codex:

```sh
mkdir -p ~/.codex/skills
cp -R skills/design-system-research ~/.codex/skills/
cp -R skills/design-system-from-scratch ~/.codex/skills/
```

Или установите их локально внутри проекта:

```sh
mkdir -p .agents/skills
cp -R skills/design-system-research .agents/skills/
cp -R skills/design-system-from-scratch .agents/skills/
```

## Использование

Попросите Codex явно использовать нужный skill:

```text
Use $design-system-research to audit this app UI and create docs/design-system artifacts.
```

```text
Use $design-system-from-scratch to define a design system for this new product from the brief and references.
```

## Рекомендуемое Правило Для Проекта

Можно добавить примерно такое правило в инструкции проекта:

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

## Структура Репозитория

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

## Философия

Эти skills специально компактные. Они не пытаются заменить дизайнера или полноценную команду дизайн-системы. Они дают Codex достаточно процесса и ограничений, чтобы UI перестал быть украшательством и стал переиспользуемым продуктовым контрактом.

Цель не в том, чтобы все интерфейсы выглядели одинаково. Цель в том, чтобы каждый интерфейс был объяснимым, последовательным, проверяемым и удобным для развития.

## Лицензия

MIT
