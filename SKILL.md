---
name: frontend-design-prompt
description: Use this skill when users provide vague frontend UI requests like "不好看", "优化一下页面", "高级一点", "make it nicer", or only a requirement document without UI design. Expands short developer requests into structured UI briefs, downstream handoff prompts, and implementation acceptance criteria with a compact, visually polished UI direction.
version: 0.3.1
---

# Frontend Design Prompt Skill

## Purpose

This skill turns short, vague frontend design requests into actionable UI briefs and high-quality prompts for downstream design, UX, or implementation tools.

The common team situation:
- There is no UI designer.
- A frontend developer receives only a requirement document.
- The first implementation works but looks plain, crowded, inconsistent, or unpolished.
- Someone says "make it nicer" or "optimize this component" without explaining what better means.

Your job is to create the missing design direction.

## Default Behavior

Do not jump straight to CSS unless the user explicitly asks for code-only fixes.

When the input is vague, first produce or use a structured design brief that covers:
- page or component purpose
- target user and usage context
- information hierarchy
- visual direction
- layout and component composition
- interaction states
- responsive behavior
- accessibility and quality checks
- implementation constraints
- compact spacing expectations

This skill is tool-agnostic. The downstream capability may be Product Design, UI/UX PRO MAX, another design skill, an IDE assistant, a code agent, or a human designer/developer.

Product Design and UI/UX PRO MAX are examples, not required dependencies.

Default design direction:
- optimize for a better-looking, more intentional UI
- use compact, efficient layouts rather than spacious marketing-style spacing
- keep section gaps, paddings, and control spacing restrained
- do not inherit mediocre visual decisions from an old system unless the user explicitly asks for consistency

If the user asks to use Product Design, shape the output as a Product Design-ready prompt.

If the user also mentions UI/UX PRO MAX, use this skill as the brief expander and use UI/UX PRO MAX for design-system reasoning, UX quality checks, and implementation guidance.

If the user also mentions Product Design, use this skill as the brief expander and use Product Design for visual exploration, redesign, or prototype generation.

## Output Modes

Choose the output mode from the user's intent. If unclear, default to Handoff Prompt.

### Brief Only

Use when the user wants to clarify the UI direction, discuss with a team, or document what should be designed.

Output:
- structured UI brief
- assumptions
- constraints to respect
- quality checklist

Do not write a downstream command or edit code.

### Handoff Prompt

Use when the user asks for a prompt, mentions another tool/skill/agent, or needs to pass the task to someone else.

Output a ready-to-copy task prompt for the downstream tool or human.

The handoff prompt must include:
- original request
- inferred assumptions
- design goal and scope
- compact layout constraint
- downstream instructions
- UX/visual review criteria
- implementation acceptance criteria

### Implement After Brief

Use when the user asks the current agent to modify the project.

First create or state the brief, then implement code changes. Keep the brief short enough to guide the work without blocking implementation.

## Front-Loaded Handoff Pattern

Use this skill as the first step before handing work to the design or UX capability available in the current environment.

```text
Vague developer request
-> Frontend Design Prompt expands it into a brief
-> available downstream capability reviews or designs from the brief
-> coding agent implements
```

Common runtime pairings:
- Claude Code + UI/UX PRO MAX: expand the request into a brief, then use UI/UX PRO MAX to review UX, consistency, accessibility, component quality, and implementation direction.
- Codex + Product Design: expand the request into a Product Design-ready brief, then use Product Design for visual options, redesign, or prototype work.

These pairings are examples. For any other IDE, design tool, code agent, or human collaborator, still produce the same structured handoff prompt.

When the user names any downstream tool/person, says "generate a prompt", or asks for an optimized design prompt, output Handoff Prompt mode instead of generic advice.

The handoff prompt must contain:
- original short request
- inferred assumptions
- design goal
- compact layout requirement
- UX and visual quality requirements
- downstream instructions for Product Design or UI/UX PRO MAX
- implementation acceptance criteria

## Trigger Examples

Use this skill for requests like:
- "根据这个需求文档做一个页面"
- "这个页面不好看，优化一下"
- "这个组件太丑了，改好看点"
- "做得高级一点"
- "让它更专业/现代/清爽"
- "前端页面没有设计师，帮我生成提示词"
- "把这个简单需求扩写成设计 prompt"

Do not use this skill for:
- purely backend work
- bug fixes with no visual or UX dimension
- exact pixel-perfect implementation from an existing mockup
- brand/logo generation unless it is part of a UI brief

## Workflow

### 1. Identify the Input Type

Classify the request:

| Input | Response Mode |
|---|---|
| Requirement document only | Create a full page design brief or handoff prompt |
| Existing ugly page/component | Create a redesign brief and implementation checklist |
| One-line style request | Expand into a detailed prompt |
| User asks for Product Design | Produce a Product Design-ready brief |
| User asks for code changes | Use the brief internally, then implement |

### 2. Infer Missing Context

Make reasonable assumptions when safe. Ask questions only when missing information would materially change the design.

Infer:
- Product type: SaaS, admin panel, CRM, e-commerce, consumer app, marketing page, docs, dashboard
- User role: admin, operator, analyst, customer, creator, manager
- Primary task: browse, compare, configure, review, submit, monitor, purchase, learn
- UI density: compact for operations, balanced for forms, restrained even when polished
- Visual tone: professional, clean, premium, friendly, technical, trustworthy
- Key risk: clutter, weak hierarchy, low contrast, inconsistent spacing, missing states

### 3. Extract Useful Constraints, Not Old Style Debt

For ongoing projects, do not blindly inherit an old system's visual language.

Preserve only constraints that materially support implementation and usability:
- component library or technical stack constraints: Ant Design, Element Plus, shadcn/ui, MUI, custom components, etc.
- operational density requirements: compact tables, tighter toolbars, efficient forms
- layout constraints: page width, sidebar presence, fixed headers, content regions
- critical behavior patterns: filters, pagination, batch actions, modal flows, navigation logic
- required interaction states: hover, active, focus-visible, disabled, loading, selected

Do not preserve outdated choices just because they already exist:
- weak typography
- muddy colors
- inconsistent spacing
- heavy borders
- awkward shadows
- poor visual hierarchy

When generating prompts, use a "Constraints to respect" section instead of "Existing style to preserve."

### 4. Translate Vague Words

| User Says | Design Meaning | Prompt Direction |
|---|---|---|
| 好看一点 / nicer | More polish | Improve spacing, hierarchy, typography, alignment, states |
| 高级感 / premium | Refined and restrained | Muted palette, precise spacing, subtle depth, confident typography |
| 现代感 / modern | Current product UI | Clean layout, crisp controls, responsive grid, subtle motion |
| 专业 / professional | Business-ready | Clear hierarchy, restrained color, strong data readability |
| 简洁 / clean | Less noise | Reduce decoration, group related items, keep whitespace controlled |
| 太挤 / crowded | Needs rhythm | Improve grouping and alignment first, then add only restrained spacing |
| 太素 / plain | Needs character | Add hierarchy, accent color, visual anchors, better empty states |
| 太花 / busy | Needs restraint | Reduce colors, effects, borders, competing emphasis |
| 没重点 / no focus | Weak hierarchy | Define primary action, key metric, visual path |
| 不协调 / inconsistent | System mismatch | Normalize spacing, radius, color, typography, icon sizing |

### 5. Generate the Design Brief

Use this structure unless the user asks for a different format:

```text
Design goal:
Audience and scenario:
Page/component type:
Constraints to respect:
Information architecture:
Visual direction:
Layout requirements:
Component requirements:
Interaction states:
Responsive requirements:
Accessibility requirements:
Implementation constraints:
Acceptance criteria:
```

Keep the brief specific enough that another AI can build from it without guessing the design taste.

### 6. Produce an AI Prompt

When the deliverable is a prompt, write it as an instruction to the next AI agent.

Good prompts include:
- what to design
- who uses it
- what the user needs to accomplish
- desired visual tone
- concrete layout expectations
- component/state requirements
- compact density constraints
- constraints and anti-patterns
- acceptance criteria

Avoid prompts that only say:
- "make it beautiful"
- "use modern design"
- "add animations"
- "make it like Apple/Stripe/Linear" without explaining the relevant qualities
- "redesign everything" when the task is only to improve an existing product screen

### 7. Implementation Guidance

If implementing the UI after creating the brief:
- Read the existing component/library constraints and business flow first.
- Preserve the app's framework and component library unless the user asks otherwise.
- Prefer small, targeted improvements over unrelated redesign unless the user wants a broader visual lift.
- Use real states: loading, empty, error, disabled, hover, focus-visible.
- Verify desktop and mobile layout.
- Check text wrapping, contrast, spacing, and interaction affordances.

## Runtime Coordination

Use the chain that matches the current environment.

### Claude Code + UI/UX PRO MAX

1. Use this skill to expand the vague request into a structured brief.
2. Use UI/UX PRO MAX to validate UX, component patterns, accessibility, layout, responsive behavior, and visual consistency.
3. Implement when the user asks for code changes.

The handoff prompt should include:
- source context: requirement document, screenshot, existing page, or component
- specific areas to improve
- target design tone
- UI/UX PRO MAX review criteria
- compact layout requirement
- responsive and accessibility requirements
- implementation acceptance criteria

### Codex + Product Design

1. Use this skill to expand the vague request into a Product Design-ready brief.
2. Use Product Design to generate visual directions, redesign options, or prototype-ready output.
3. Implement after a visual direction or brief is accepted.

The handoff prompt should include:
- source context: requirement document, screenshot, existing page, or component
- specific areas to improve
- target design tone
- Product Design instructions
- component states
- compact layout requirement
- responsive and accessibility requirements
- acceptance criteria

### If Both Are Available

If Product Design and UI/UX PRO MAX are both available:

1. Use this skill to expand the vague request into a structured brief.
2. Use UI/UX PRO MAX to validate UX, component patterns, accessibility, layout, responsive behavior, and visual consistency.
3. Use Product Design to generate visual directions, redesign options, or prototype-ready output.
4. Feed Product Design concrete compact-layout and workflow constraints instead of a vague "make it beautiful" request.

The handoff prompt should include:
- source context: requirement document, screenshot, existing page, or component
- specific areas to improve
- target design tone
- component states
- compact layout requirement
- responsive and accessibility requirements
- acceptance criteria

Use this output shape for the handoff:

```text
Original request:
[the user's short request]

Assumptions:
[reasonable assumptions, or "none"]

Constraints to respect:
[technical stack, compact-density requirement, business flow constraints, or instructions to inspect them]

Brief for downstream design/UX capability:
[page/component goal, target user, layout, visual direction, states, responsive behavior]

Review or design criteria:
[Product Design instructions or UI/UX PRO MAX review criteria, depending on the current environment]

Implementation acceptance criteria:
[concrete checks the coding agent must satisfy]
```

## Visual Direction Rules

For B2B/admin/operational tools:
- prioritize scanability, density, and predictable navigation
- avoid oversized marketing heroes
- avoid decorative card stacks and excessive gradients
- make tables, filters, status, and actions easy to compare
- keep spacing compact and efficient instead of airy

For marketing/landing pages:
- define the offer clearly
- use one strong visual focus
- make the first viewport communicate the product or brand
- keep CTA hierarchy obvious

For forms:
- group related fields
- clarify required/optional information
- include validation, helper text, disabled/loading states
- optimize for completion, not decoration
- keep field spacing controlled rather than loose

For dashboards:
- establish metric hierarchy
- show relationships and trends clearly
- avoid chart decoration that weakens readability
- provide filters, date ranges, and empty/loading states

## Quality Checklist

Before finalizing a prompt or implementation, check:
- Does the design goal match the business/user task?
- Does it improve the UI even if the old system style was weak?
- Are the compact-density constraints explicit?
- Is there a clear primary action or focus?
- Is the information hierarchy obvious?
- Are spacing, typography, color, and radius consistent?
- Are all important component states covered?
- Does the design work on mobile and desktop?
- Does text fit without awkward overflow?
- Is contrast sufficient?
- Are decorative effects restrained and purposeful?
- Would a frontend developer know exactly what to build next?

## References

Load `references/prompt-patterns.md` when examples or reusable prompt templates are useful.

Load `references/style-audit-checklist.md` when the work needs implementation constraints, compact-density cues, or behavioral patterns from an existing product.

Load `references/before-after-examples.md` when the user gives a very short request and you need examples for expansion style.

Load `README.md` when you want ready-to-use Chinese best-practice prompts for Codex, Product Design, or direct implementation workflows.

## Version History

**v0.3.1** (2026-06-16):
- Repositioned the skill toward "make the UI look better" instead of preserving old visual style by default.
- Kept compact operational layout as a hard constraint.
- Replaced style-preservation guidance with constraint-preservation guidance.

**v0.3.0** (2026-06-15):
- Made the skill tool-agnostic.
- Added explicit output modes: Brief Only, Handoff Prompt, and Implement After Brief.
- Added stronger handoff rules for any downstream tool, agent, or human.
- Added references for style auditing and before/after expansion examples.

**v0.2.0** (2026-06-11):
- Repositioned skill from CSS polish guide to UI brief and prompt expansion workflow.
- Added Product Design-ready brief structure.
- Added vague request translation table and quality checklist.

**v0.1.0** (2026-06-11):
- Initial release with visual polish dimensions and CSS patterns.
