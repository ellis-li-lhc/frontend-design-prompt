# Anti-Patterns And Acceptance Criteria

Use this reference when a brief or prompt needs stricter design guardrails or implementation acceptance criteria.

## Common Anti-Patterns

Operational pages:
- turning admin, CRM, approval, data-entry, or monitoring pages into marketing layouts
- using oversized hero sections where users need filters, tables, forms, or actions
- making table rows, filters, sidebars, or forms too spacious for high-frequency use
- placing core actions below decorative content

Visual polish:
- adding gradients, shadows, glass effects, or motion without improving hierarchy
- wrapping every section in a decorative card
- using too many accent colors
- relying on color alone for status
- using low-contrast muted text for important information

Layout and hierarchy:
- no clear primary action
- every section has equal emphasis
- labels, values, actions, and metadata are poorly aligned
- text overflows containers or buttons
- mobile layout only shrinks desktop UI instead of reflowing it

State coverage:
- missing hover, active, focus-visible, disabled, loading, empty, error, selected, or validation states
- destructive actions lack confirmation or clear hierarchy
- form errors appear far away from the relevant field

Prompt quality:
- asking only for "beautiful", "premium", or "modern"
- copying a named brand without explaining the relevant design qualities
- asking to redesign everything when the task is scoped to one screen or component
- preserving old visual style when it is the source of the problem

## Acceptance Criteria Levels

Use Must/Should/Nice to keep core usability ahead of decoration.

### Must

- Preserve required business flow, data, actions, and permissions.
- Use the current framework and component library unless explicitly told otherwise.
- Cover loading, empty, error, disabled, hover, focus-visible, selected, and validation states where relevant.
- Work at desktop and narrow widths without incoherent overlap or text overflow.
- Provide readable contrast and visible keyboard focus.
- Make the primary action and main information path clear.

### Should

- Improve visual hierarchy, grouping, spacing rhythm, alignment, and typography.
- Keep operational layouts compact and scan-friendly.
- Make status, filters, row actions, form fields, and navigation easier to compare.
- Reuse existing shared components or tokens where they support quality and consistency.
- Avoid inheriting weak legacy colors, borders, shadows, or spacing by default.

### Nice

- Add subtle motion only when it clarifies feedback or transition.
- Improve empty states with concise guidance or lightweight visuals.
- Add refined details such as better icon sizing, badges, or microcopy when they do not distract.
