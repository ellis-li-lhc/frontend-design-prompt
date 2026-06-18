# Frontend Design Prompt

**[English](README.md) | [中文](README_zh.md)**

`frontend-design-prompt` is a Codex skill for turning vague frontend UI requests into clear design briefs, handoff prompts, and implementation acceptance criteria.

Current version: 1.1.0

It is useful when a team has requirements but no dedicated UI designer, or when a page works functionally but feels plain, crowded, inconsistent, or unpolished.

## What It Helps With

- Expanding requests like "make it nicer", "优化一下页面", or "高级一点" into actionable UI direction.
- Creating prompts for Product Design, UI/UX PRO MAX, another design tool, a code agent, or a human teammate.
- Preserving practical constraints such as business flow, component library limits, interaction states, and compact density.
- Avoiding blind inheritance of weak legacy visual styling.
- Diagnosing whether the input is a short request, requirement document, screenshot, existing page, code path, or downstream handoff task.
- Producing page-type-aware guidance for tables, dashboards, forms, detail pages, settings pages, modals, auth pages, and landing pages.

## Core Principle

Improve the UI's visual quality and usability while keeping product workflows efficient.

For admin, SaaS, dashboard, CRM, and other operational interfaces, prefer compact and scan-friendly layouts over loose marketing-style spacing. Preserve what matters for implementation and workflow, not outdated colors, spacing, borders, or hierarchy.

When working with an existing project, inspect the stack, component library, nearby screens, tokens, business flow, and state coverage before writing final redesign instructions.

## Output Modes

### Brief Only

Use when the goal is to clarify direction before design or implementation.

Output:

- structured UI brief
- assumptions
- constraints
- Must/Should/Nice acceptance criteria

### Handoff Prompt

Use when the result will be passed to another tool, agent, designer, or developer.

Output:

- original request
- inferred assumptions
- constraints to respect
- design goal and scope
- downstream instructions
- UX and visual review criteria
- Must/Should/Nice implementation acceptance criteria

### Implement After Brief

Use when Codex should directly modify the project.

Output a short brief first, then implement the UI changes while respecting the current stack, business flow, and component constraints.

## Recommended Prompt

```text
Use frontend-design-prompt as the first step.

Short request:
[paste the vague frontend request]

Context:
[requirement document, screenshot, route, component name, or code path]

Constraints:
- improve the UI so it looks more intentional and polished
- keep the layout compact and efficient
- preserve business flow, component-library constraints, and important states
- do not copy weak legacy styling by default
- avoid oversized spacing, excessive gradients, decorative card stacks, or marketing-page composition

Output:
1. expanded UI brief
2. downstream handoff prompt or review criteria
3. Must/Should/Nice implementation acceptance criteria
```

## Example: Existing Table Redesign

```text
Use frontend-design-prompt + Product Design.

Request:
这个表格不好看，帮我优化一下。

First expand this into a Product Design-ready brief.
Keep the table compact and operationally efficient.
Respect the current framework, component library, business flow, and interaction states.
Do not inherit weak old visual styling by default.

Output:
1. Product Design-ready brief
2. visual redesign instructions
3. implementation acceptance criteria
```

## Example: Direct Implementation

```text
Use frontend-design-prompt in Implement After Brief mode.

I want you to directly improve this page, not just give suggestions.

Goals:
- make the page noticeably better-looking
- keep the layout compact
- preserve the current framework, component library, business flow, and interaction logic
- improve hierarchy, grouping, spacing, typography, states, and action areas
- avoid copying dated legacy visual styling by default

First provide a short brief, then implement the changes.
```

## Installation

Copy the whole `frontend-design-prompt/` folder, including `SKILL.md` and `references/`.

### Codex

Install as a personal Codex skill:

```text
C:\Users\<your-user>\.codex\skills\frontend-design-prompt\
```

Then use it with:

```text
Use frontend-design-prompt as the first step.
```

### Claude Code

Install as a personal Claude Code skill:

```text
~/.claude/skills/frontend-design-prompt/
```

Or install it only for one project:

```text
<project>/.claude/skills/frontend-design-prompt/
```

Invoke it directly with:

```text
/frontend-design-prompt
```

Claude Code also loads matching skills automatically when the request matches the skill description. See the [Claude Code skills docs](https://code.claude.com/docs/en/skills).

### opencode

Install as a global opencode skill:

```text
~/.config/opencode/skills/frontend-design-prompt/
```

Or install it only for one project:

```text
<project>/.opencode/skills/frontend-design-prompt/
```

opencode also discovers Claude-compatible and Agent Skills-compatible locations:

```text
<project>/.claude/skills/frontend-design-prompt/
~/.claude/skills/frontend-design-prompt/
<project>/.agents/skills/frontend-design-prompt/
~/.agents/skills/frontend-design-prompt/
```

Use the skill by asking opencode to load `frontend-design-prompt`, or by making a request that matches its description. See the [opencode Agent Skills docs](https://opencode.ai/docs/skills/).

Expected structure:

```text
frontend-design-prompt/
├── SKILL.md
├── README.md
├── README_zh.md
└── references/
    ├── anti-patterns-and-acceptance.md
    ├── before-after-examples.md
    ├── page-type-templates.md
    ├── project-aware-audit.md
    ├── prompt-patterns.md
    └── style-audit-checklist.md
```
