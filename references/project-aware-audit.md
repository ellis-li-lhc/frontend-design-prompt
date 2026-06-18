# Project-Aware Audit

Use this reference before writing a redesign prompt for an existing codebase, route, component, screenshot, or product surface.

## Audit Order

1. Identify the product surface:
   - route, page, component name, screenshot, or requirement source
   - user role and primary task
   - frequency of use: operational, occasional, or conversion-oriented

2. Inspect implementation constraints:
   - framework and routing
   - component library
   - shared layout, shell, sidebar, topbar, or page container
   - CSS strategy: tokens, theme config, utility classes, modules, or global styles
   - sibling screens that establish reusable patterns

3. Extract workflow constraints:
   - required data, filters, table columns, forms, actions, permissions, and navigation
   - modal, drawer, create/edit, delete, batch, export, or approval flows
   - loading, empty, error, disabled, selected, hover, active, and focus-visible states

4. Diagnose UI issues:
   - weak hierarchy
   - unclear primary action
   - crowded or overly loose spacing
   - poor alignment
   - inconsistent typography, radius, color, or icon sizing
   - text overflow or bad wrapping
   - low contrast
   - hidden or ambiguous states

5. Convert findings into prompt constraints:
   - keep business behavior and implementation feasibility
   - keep compact density when the workflow is operational
   - improve weak visual decisions instead of preserving them
   - name the specific modules and states to redesign

## Output Shape

```text
Project context found:
[framework, component library, route/component, neighboring patterns]

Practical constraints:
[business flow, component limits, density, states, responsive rules]

Current UI risks:
[hierarchy, spacing, contrast, overflow, missing states, unclear actions]

Design brief:
[target user, page goal, information architecture, visual direction, layout and components]

Acceptance criteria:
Must:
[correctness, states, accessibility, responsive fit]

Should:
[hierarchy, compact density, consistency, scanability]

Nice:
[subtle motion or optional polish]
```
