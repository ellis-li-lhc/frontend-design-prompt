# Existing Constraint Audit Checklist

Use this checklist before generating a redesign prompt for an existing project. The goal is to extract useful implementation and density constraints without blindly preserving weak legacy styling.

If exact values are available in code or design tokens, include them. If not, describe what the downstream tool or developer should inspect.

Keep this principle in mind:
- preserve workflow and technical constraints
- preserve compact density requirements
- do not preserve outdated visual choices by default

## Global Tokens

- Primary color, hover color, active color
- Background colors: page, section, surface, elevated surface
- Text colors: primary, secondary, muted, disabled, inverse
- Border color and divider color
- Shadow levels, if used
- Border radius scale
- Spacing scale
- Font family, base font size, title sizes, line heights
- Icon size and stroke style

Questions to ask:
- Which of these tokens are implementation constraints?
- Which of these are just old styling choices that can be improved?

## Buttons

- Heights: small, default, large
- Horizontal padding
- Border radius
- Primary, secondary, ghost, danger variants
- Hover, active, focus-visible, disabled, loading states
- Icon-only button size
- Button group spacing

## Form Controls

- Input/select/textarea height
- Padding and border style
- Label placement and required mark
- Helper text, error text, validation state
- Focus ring or focus border
- Disabled and readonly style
- Checkbox, radio, switch size and active color
- Form item vertical spacing

## Tables

- Table density and row height
- Header height and background
- Header text color, size, weight
- Cell padding and vertical alignment
- Border or divider style
- Zebra striping color
- Row hover color
- Selected row color
- Expanded row style
- Empty, loading, error states
- Status badge style
- Row action placement
- Pagination placement and size
- Horizontal scroll behavior for many columns

## Navigation

- Sidebar width and collapsed width
- Topbar height
- Active item color and background
- Hover state
- Icon and label spacing
- Breadcrumb style
- Tab height, active indicator, and spacing

## Cards And Panels

- Padding
- Radius
- Border/shadow/elevation style
- Header/footer treatment
- Section gap
- Background color

## Modals And Drawers

- Width presets
- Header height
- Title size and weight
- Body padding
- Footer layout
- Overlay style
- Close button size and placement
- Destructive action treatment

## Feedback And Status

- Toast style
- Alert style
- Badge/tag radius, padding, color rules
- Success/warning/error/info palette
- Skeleton loading style
- Empty state illustration or icon style

## Responsive Rules

- Main breakpoints
- Page padding on desktop/tablet/mobile
- Table behavior on narrow screens
- Form layout changes
- Toolbar wrapping behavior
- Minimum touch target size

Compact layout reminders:
- Prefer efficient spacing over airy composition
- Keep table, form, and toolbar density suitable for operational use
- Add breathing room only where it clarifies hierarchy
