# Prompt Patterns Reference

Use these templates when turning vague frontend requests into detailed prompts for downstream tools, IDE assistants, code agents, design agents, or human collaborators.

## Requirement Document to Page Design Prompt

```text
You are designing a production-ready frontend page from a requirement document.

Requirement summary:
[Paste or summarize the requirement here]

Design goal:
Create a [page type] that helps [target user] accomplish [primary task] efficiently and confidently.

Audience and scenario:
- Primary user: [role]
- Usage frequency: [high-frequency operational / occasional review / first-time conversion]
- Environment: [desktop-first admin / responsive web / mobile-heavy]

Visual direction:
- Style: [professional / clean / premium / friendly / technical]
- Information density: compact or balanced, never loose by default
- Use restrained color, clear hierarchy, consistent spacing, and polished component states.
- Avoid generic decorative gradients, excessive shadows, and card-heavy layouts unless they support the workflow.

Constraints to respect:
- First inspect the existing project's component library, business flow, and layout constraints.
- Keep density compact: restrained page padding, controlled section gaps, compact controls, efficient table/tool areas.
- Preserve implementation feasibility and workflow logic, but do not inherit weak old visual styling by default.

Layout requirements:
- Organize the page into clear functional areas.
- Make the primary action visually obvious.
- Group related information and separate unrelated sections with spacing, headings, or dividers.
- Ensure the page can be scanned quickly.

Component requirements:
- Include appropriate navigation, filters, forms, tables, lists, cards, status badges, actions, and feedback states based on the requirement.
- Cover loading, empty, error, disabled, hover, active, and focus-visible states where relevant.

Responsive requirements:
- Desktop layout should support efficient work.
- Mobile layout should preserve task completion without text overflow or cramped controls.

Accessibility requirements:
- Maintain readable contrast.
- Do not rely only on color to communicate state.
- Ensure keyboard focus is visible.
- Keep touch targets usable on mobile.

Acceptance criteria:
Must:
- Preserve required business flow, content, states, responsive behavior, and accessibility basics.
- Avoid text overflow and incoherent overlap.

Should:
- The result should look intentionally designed rather than merely functional.
- A frontend developer should be able to implement the layout and states directly.
- The visual style should fit the product type and user workflow.
- Spacing should feel controlled and efficient rather than loose.

Nice:
- Add subtle visual refinements or motion only when they support feedback, hierarchy, or task clarity.
```

## Generic Handoff Prompt Template

```text
Original request:
[Paste the user's short request]

Assumptions:
[List reasonable assumptions. If none, write "None."]

Constraints to respect:
[List technical, workflow, and compact-density constraints. Do not default to preserving old visual style.]

Design goal:
[Explain what better means for this page/component.]

Scope:
[Clarify what should change and what should remain unchanged.]

Downstream instructions:
[Write direct instructions for the target tool, agent, or human collaborator.]

Review criteria:
[Hierarchy, scanability, accessibility, consistency, responsiveness, states, implementation fit.]

Implementation acceptance criteria:
Must:
[Correctness, business flow, required states, responsive fit, accessibility basics.]

Should:
[Hierarchy, scanability, compact density, consistency, reusable components.]

Nice:
[Optional motion, empty-state polish, microcopy, or small visual refinements.]
```

## Existing Page Redesign Prompt

```text
You are redesigning an existing frontend page that currently feels [plain / crowded / inconsistent / unprofessional].

Current problems:
- [Problem 1: weak hierarchy, crowded spacing, unclear action, inconsistent components, etc.]
- [Problem 2]
- [Problem 3]

Redesign goal:
Improve visual polish, hierarchy, usability, and consistency while preserving the existing business flow and functional requirements.

Keep:
- [Existing features, data, actions, navigation, or constraints that must remain]
- Existing business flow, technical constraints, and compact density requirements

Improve:
- Layout hierarchy and grouping
- Spacing rhythm and alignment
- Typography scale and text readability
- Color usage and contrast
- Component consistency
- Interaction states and feedback
- Empty, loading, and error states

Visual direction:
Make the page feel [professional / modern / clean / premium] through restrained design choices, not through excessive decoration.

Constraints:
- Preserve the existing frontend framework and component library.
- Do not inherit weak old visual language by default.
- Avoid unrelated feature changes.
- Keep the design responsive and compact.

Acceptance criteria:
Must:
- Preserve existing business flow, required actions, data, states, and responsive behavior.
- The primary task and main action are clear.

Should:
- The interface feels coherent across sections.
- The primary task is easier to understand.
- The improved design is implementable by frontend developers.

Nice:
- Add subtle polish only where it improves feedback or hierarchy.
```

## Component Beautification Prompt

```text
You are improving a single UI component.

Component:
[button / card / table / modal / form / sidebar / navbar / list item / chart panel]

Current issue:
[too plain / too crowded / visually inconsistent / unclear state / weak hierarchy]

Goal:
Make the component feel polished, reusable, and consistent with a modern product interface.

Requirements:
- Preserve existing behavior and content.
- Match the product's implementation constraints and compact scale: height, padding, density, state coverage, and technical feasibility.
- Improve spacing, alignment, typography, color, and state clarity.
- Define normal, hover, active, focus-visible, disabled, loading, and error states when relevant.
- Ensure the component works in narrow and wide containers.
- Avoid visual effects that make the component harder to read or reuse.

Acceptance criteria:
Must:
- Preserve existing behavior and content.
- Text fits inside the component.
- State changes are visible and accessible.

Should:
- The component has clear affordance.
- Styling can be reused consistently across the product.

Nice:
- Add refined micro-interactions only when they improve feedback without reducing clarity.
```

## Short Request Expansion Examples

### "这个页面不好看，优化一下"

```text
Please redesign this page to feel more professional, coherent, and production-ready.

Focus on improving visual hierarchy, spacing rhythm, typography, alignment, component consistency, and interaction states. Preserve the existing business flow and functionality. Make the primary action and key information easier to scan. Use a restrained modern visual style suitable for the product type. Keep the layout compact and avoid oversized whitespace. Include responsive behavior, empty/loading/error states, and accessible focus states.
```

### "根据需求文档做一个页面"

```text
Please turn the requirement document into a complete frontend page design brief, then implement the page from that brief.

Infer the target user, page goal, information architecture, key modules, primary actions, and required component states from the document. Choose a visual direction appropriate to the product type. The output should look intentionally designed, not just assembled from raw requirements. Keep spacing controlled and efficient.
```

### "高级一点"

```text
Make the UI feel more refined and premium without adding unnecessary decoration.

Use precise spacing, confident typography, restrained color, subtle depth, clear hierarchy, and polished component states. Reduce visual noise, avoid overusing gradients or shadows, and make the interface feel calm, deliberate, and trustworthy while staying compact.
```

### "太挤了"

```text
Improve the layout rhythm so the interface feels clearer without becoming loose or spacious.

Improve grouping, alignment, and line height first. Add only restrained padding and section gaps where needed. Keep important actions visible and avoid making the page unnecessarily sparse.
```

## Anti-Patterns

Avoid prompt expansions that:
- only request "beautiful", "modern", or "premium" with no concrete direction
- over-prescribe colors before understanding the product context
- add animation or decoration as a substitute for hierarchy
- ignore responsive behavior
- ignore empty, loading, error, disabled, hover, and focus states
- ask for a landing-page style when the task is an operational admin workflow
- preserve ugly legacy styling just because it already exists
