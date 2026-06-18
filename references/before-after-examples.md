# Before And After Expansion Examples

Use these examples to match the expansion style for very short frontend requests.

## Example 1: Table Looks Bad

Short request:

```text
这个表格不好看，帮我优化一下。
```

Handoff prompt:

```text
Original request:
这个表格不好看，帮我优化一下。

Assumptions:
This is an existing product table in an admin or operational workflow. Preserve current business functionality.

Constraints to respect:
Inspect the current project before redesigning. Keep the table compact and operationally efficient. Preserve business behavior, state coverage, and implementation feasibility, but do not inherit weak old visual styling by default.

Design goal:
Make the table more professional, readable, and efficient to scan with a clearly improved visual result.

Downstream instructions:
Improve toolbar layout, search/filter grouping, table header hierarchy, row alignment, status badges, row actions, bulk selection, pagination, and empty/loading/error states. Keep actions discoverable but visually restrained. Maintain compact density and avoid oversized gaps.

Review criteria:
Check scanability, state clarity, text truncation, column density, keyboard focus, accessible contrast, responsive behavior, and consistency with the intended compact product UI.

Implementation acceptance criteria:
Must: The optimized table avoids text overflow, supports hover/selected/disabled/loading/empty/error states, works on desktop and narrow screens, and preserves existing behavior.
Should: It keeps density compact, improves scanability, and makes primary actions easy to identify.
Nice: Add subtle row feedback or empty-state polish only if it does not reduce readability.
```

## Example 2: Login Page Should Feel Premium

Short request:

```text
登录页高级一点。
```

Handoff prompt:

```text
Original request:
登录页高级一点。

Assumptions:
This is an existing login page for a web product. The goal is to improve trust and polish without adding distracting decoration.

Constraints to respect:
Inspect the current product's technical and workflow constraints. Keep the form compact, readable, and easy to complete, but do not copy dated visual styling by default.

Design goal:
Make the login page feel more refined, trustworthy, and easy to complete.

Downstream instructions:
Improve page composition, spacing, form hierarchy, input labels, password visibility, validation states, loading state, error message placement, and primary button emphasis. Use restrained visual depth and avoid decorative effects that reduce readability or make the page feel loose.

Review criteria:
Check first-impression trust, form completion clarity, accessibility, mobile fit, error recovery, keyboard navigation, and overall polish.

Implementation acceptance criteria:
Must: The login form remains readable, responsive, accessible, and complete in error/loading/disabled/focus-visible states.
Should: It feels refined and trustworthy while staying simple and compact.
Nice: Add subtle visual polish only if it does not distract from form completion.
```

## Example 3: User Management Page From Requirements

Short request:

```text
根据这份用户管理需求做一个页面。
```

Handoff prompt:

```text
Original request:
根据这份用户管理需求做一个页面。

Assumptions:
The page is for administrators who need to search, review, create, edit, disable, and manage users efficiently.

Constraints to respect:
Inspect existing admin pages for workflow and implementation constraints. Keep navigation, filters, forms, tables, buttons, modal/drawer patterns, and pagination feasible within the current stack. Keep the layout compact.

Design goal:
Create a user management page that supports efficient lookup, comparison, status recognition, and common user actions with a polished operational UI.

Downstream instructions:
Design a clear page header, primary create action, search/filter area, data table, status and role badges, row actions, batch actions if needed, pagination, empty/loading/error states, and create/edit flow entry points. Keep the layout operational, compact, and scan-friendly rather than marketing-like.

Review criteria:
Check task efficiency, information hierarchy, data readability, action discoverability, permission/status clarity, responsive behavior, and visual polish.

Implementation acceptance criteria:
Must: The page is implementable with the current stack, preserves required user actions, and handles all major states.
Should: Common admin actions are easy to find, and the layout stays compact without feeling cramped.
Nice: Add lightweight visual refinements only where they improve hierarchy or feedback.
```

## Example 4: Dialog Looks Rough

Short request:

```text
这个弹窗太丑了，优化一下。
```

Handoff prompt:

```text
Original request:
这个弹窗太丑了，优化一下。

Assumptions:
This is an existing modal or dialog. Preserve the current business action and copy unless changes are necessary for clarity.

Constraints to respect:
Inspect modal width, body density, footer actions, form controls, and destructive-action behavior from the existing project. Preserve workflow and feasibility, but improve the visual result instead of copying rough legacy styling.

Design goal:
Make the dialog feel clearer, calmer, and more consistent with the product.

Downstream instructions:
Improve title hierarchy, content grouping, spacing, footer actions, primary/secondary button hierarchy, close affordance, validation/error states, loading state, and narrow-screen behavior. Avoid oversized decorative panels, loose spacing, or unrelated layout changes.

Review criteria:
Check decision clarity, destructive-action safety, keyboard/focus behavior, copy readability, responsive fit, and overall polish.

Implementation acceptance criteria:
Must: The dialog has clear action hierarchy, supports focus-visible/disabled/loading/error states, and does not overflow on small screens.
Should: It keeps spacing compact and improves title, body, and footer hierarchy.
Nice: Add subtle transition or feedback polish only if it supports clarity.
```
