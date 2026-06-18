# Page Type Templates

Use this reference when a vague request maps to a common frontend page or component type. Pick only the relevant template and adapt it to the user's product context.

## Admin List Or Table Page

Goal:
- Help operators search, compare, filter, inspect, and act on records quickly.

Include:
- page title with concise context
- primary action
- compact search and filter toolbar
- table with readable columns, status badges, row actions, sorting, selection, pagination
- empty, loading, error, disabled, hover, selected, and focus-visible states
- responsive behavior for narrow screens or horizontal overflow

Avoid:
- oversized hero areas
- loose row heights
- decorative cards around every table region
- status colors without text labels

## Dashboard Or Analytics Page

Goal:
- Help users understand current state, trends, anomalies, and next actions.

Include:
- metric hierarchy
- date range and filters
- chart panels with clear labels and units
- comparison or trend context
- alerts or notable changes
- empty/loading/error states for each data region

Avoid:
- chart decoration that weakens readability
- equal emphasis on every metric
- unclear time ranges
- overly large cards that reduce scanability

## Form Or Wizard

Goal:
- Help users complete input accurately and recover from errors.

Include:
- grouped fields
- required and optional cues
- helper text where decisions are ambiguous
- validation, error, disabled, loading, and success states
- clear primary/secondary actions
- mobile-friendly field layout

Avoid:
- decorative layout that makes completion slower
- loose spacing that separates labels from fields
- errors shown only after submit when inline feedback is possible

## Detail Page

Goal:
- Help users review one entity, understand status, and take context-aware actions.

Include:
- entity title, status, metadata, and primary actions
- summary section for key facts
- tabs or sections for related data
- activity/history where relevant
- edit, delete, export, or workflow actions with clear hierarchy

Avoid:
- hiding critical status in low-emphasis text
- mixing actions with unrelated metadata
- making every section visually equal

## Settings Page

Goal:
- Help users configure options confidently without losing track of scope.

Include:
- clear category navigation
- grouped settings
- save/cancel or autosave feedback
- disabled, loading, validation, and success states
- explanations for risky or irreversible changes

Avoid:
- too many unrelated settings in one long page
- ambiguous save behavior
- destructive actions near routine controls

## Modal Or Drawer

Goal:
- Help users complete a focused decision or task without context loss.

Include:
- concise title
- scoped body content
- clear primary and secondary actions
- close affordance
- loading, disabled, validation, and error states
- keyboard and focus behavior

Avoid:
- using a modal for complex multi-step work that needs a full page
- weak destructive-action hierarchy
- footer buttons with unclear priority

## Login Or Auth Page

Goal:
- Build trust and make account access simple.

Include:
- compact form
- clear labels
- password visibility control
- validation and error recovery
- loading and disabled states
- mobile fit and keyboard-friendly flow

Avoid:
- decorative visuals that distract from form completion
- vague error messages
- weak contrast or tiny inputs

## Landing Or Marketing Page

Goal:
- Communicate the offer and drive one primary conversion action.

Include:
- clear product or offer signal in the first viewport
- primary CTA and secondary path
- credible proof, product visuals, and key benefits
- responsive layout that hints at the next section

Avoid:
- generic gradient-only hero sections
- split layouts where neither side establishes the product clearly
- vague value propositions
