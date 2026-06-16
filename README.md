# Frontend Design Prompt

Frontend Design Prompt is a prompt-expansion skill for teams without dedicated UI designers.

It turns short frontend requests such as "这个表格不好看，帮我优化一下" into structured UI design briefs and handoff prompts that can be given to any downstream design tool, IDE assistant, code agent, or human collaborator.

## What It Does

Use it as the first step:

```text
Developer's vague request
-> Frontend Design Prompt expands the request into a concrete UI brief
-> the available downstream tool uses the brief
-> Codex/Claude implements the result
```

Example pairings:

- Claude Code + UI/UX PRO MAX
- Codex + Product Design

These are examples, not dependencies. Use whichever downstream tool, skill, IDE agent, or human reviewer is available.

The skill is especially useful when:

- there is a requirement document but no UI mockup
- a page works but looks plain or inconsistent
- a developer says "make it nicer" or "optimize this component"
- the design should become noticeably better-looking without becoming loose or spacious

## Version 0.3.1 Updates

This release makes the skill more opinionated in the direction of visual improvement:

- Renamed the skill to `frontend-design-prompt`.
- Made the skill tool-agnostic. Product Design and UI/UX PRO MAX are examples, not required dependencies.
- Added explicit output modes:
  - Brief only: turn a vague request into a clear UI brief.
  - Handoff prompt: create a ready-to-copy task prompt for another tool, agent, or teammate.
  - Implement after brief: create the brief first, then modify the current project.
- Removed "preserve the old system look" as the default goal.
- Kept compact layout and restrained spacing as a hard constraint.
- Added `references/style-audit-checklist.md` for extracting practical constraints from existing projects.
- Added `references/before-after-examples.md` with realistic short-request expansions.
- Updated `references/prompt-patterns.md` with a generic downstream handoff template.

## Install in Codex

Copy this folder to:

```text
C:\Users\<your-user>\.codex\skills\frontend-design-prompt\
```

Expected structure:

```text
frontend-design-prompt/
├── SKILL.md
├── README.md
└── references/
    ├── before-after-examples.md
    ├── prompt-patterns.md
    └── style-audit-checklist.md
```

Then use it in Codex with Product Design like this:

```text
Use frontend-design-prompt + @Product Design.

Request: 这个表格不好看，帮我优化一下。

First expand this vague request into a Product Design-ready brief.
Do not copy the old system's visual style by default if it looks dated. Optimize for a better-looking UI while keeping the page compact and efficient.
Respect only the practical constraints:
- compact table density
- compact control height
- efficient filter/tool area
- existing business flow and states
- current framework/component library

Output the handoff prompt first. Do not implement until the brief is clear.
```

## Install in Claude Code

Copy this folder to either personal or project skills:

```text
C:\Users\<your-user>\.claude\skills\frontend-design-prompt\
```

or inside a project:

```text
<project>\.claude\skills\frontend-design-prompt\
```

Then call it with:

```text
/frontend-design-prompt

这个表格不好看，帮我优化一下。
请先把这句话扩写成详细 UI 设计 brief，再交给 UI/UX PRO MAX 做 UX、一致性、可访问性和实现质量检查。
不要默认延续旧系统的视觉风格。目标是更好看，但布局必须保持紧凑，间距不要过大，业务流程和组件能力要可实现。
```

## Recommended Prompt Pattern

Use this when you want the skill to behave as a front-loaded step:

```text
Use frontend-design-prompt as the first step.

Short request:
[paste the developer's vague request]

Context:
[requirement document, screenshot, current route, component name, or code path]

Constraints:
- optimize for a better-looking UI
- keep the layout compact and efficient
- do not use oversized spacing or airy marketing-page composition
- respect the current framework/component constraints and business flow

Output:
1. design/UX handoff brief
2. downstream review or design criteria
3. implementation acceptance criteria
```

## Output Modes

Use one of these modes depending on what you need:

- Brief only: turn a vague request into a clear UI brief for discussion.
- Handoff prompt: create a ready-to-copy task prompt for another tool, agent, or teammate.
- Implement after brief: create the brief first, then modify the current project.

Default to Handoff prompt when the user mentions another tool, asks for a prompt, or wants to pass the task forward.

## Claude Code + UI/UX PRO MAX Prompt

```text
Use frontend-design-prompt as the first step, then use UI/UX PRO MAX.

Short request:
这个表格不好看，帮我优化一下。

First expand this into a structured UI brief.
Then use UI/UX PRO MAX to review hierarchy, scanability, accessibility, responsive behavior, component states, and overall polish.

Keep these constraints:
- compact table row height
- compact control height
- efficient toolbar/filter layout
- restrained spacing
- existing business flow and component-library feasibility

Output:
1. expanded UI brief
2. UI/UX PRO MAX review criteria
3. implementation acceptance criteria
```

## Codex + Product Design Prompt

```text
Use frontend-design-prompt as the first step, then use @Product Design.

Short request:
这个表格不好看，帮我优化一下。

First expand this into a Product Design-ready brief.
Before creating visual options, do not inherit the old page's weak visual choices by default.
Keep these constraints:
- compact table row height
- compact control height
- efficient toolbar/filter layout
- restrained spacing
- existing business flow and component-library feasibility

Output:
1. Product Design-ready brief
2. Product Design instructions
3. implementation acceptance criteria
```

## Example

Input:

```text
这个表格不好看，帮我优化一下。@Product Design
```

Expected output:

```text
Original request:
这个表格不好看，帮我优化一下。

Assumptions:
This is an existing product table in an operational/admin workflow.

Constraints to respect:
Keep the table compact and efficient to use. Respect current framework and component-library constraints, preserve business behavior and states, but do not inherit weak old visual styling by default.

Brief for Product Design:
Redesign the table so it feels professional, coherent, and easy to scan while preserving existing business functionality. Improve table hierarchy, toolbar layout, filters, status badges, row actions, empty/loading/error states, and pagination. Keep the density compact and spacing restrained.

Product Design instructions:
Create a redesign direction that improves scanability, state clarity, toolbar organization, row actions, pagination, empty/loading/error states, and overall polish. Avoid loose spacing or airy marketing-style composition.

Implementation acceptance criteria:
The optimized table must avoid text overflow, support hover/selected/disabled/loading/empty/error states, work on desktop and narrow screens, keep density compact, and make primary actions easy to identify.
```

## Chinese Best-Practice Prompts

Use these examples when you want the skill to reliably generate a better-looking UI while keeping the layout compact.

### 1. Existing Admin Page Visual Upgrade

```text
Use frontend-design-prompt as the first step.

需求：
这个后台页面不好看，帮我优化一下。

要求：
- 目标是比现在更好看、更有设计感、更精致
- 不要默认继承旧系统的视觉风格
- 只保留业务流程、组件库限制、交互状态和紧凑布局要求
- 页面整体要紧凑，间距不要过大，不要做成松散的营销页
- 重点优化信息层级、排版、间距节奏、按钮和表单观感、表格工具栏、状态样式

输出：
1. 扩写后的 UI brief
2. 可交给 Product Design 或其他设计 agent 的 handoff prompt
3. 实现验收标准
```

### 2. New Page From Requirement Document

```text
Use frontend-design-prompt as the first step.

需求：
根据这份需求文档设计一个新页面。

要求：
- 页面要以“更好看”为优先，不要参考旧系统里不美观的视觉样式
- 整体风格要专业、现代、克制
- 布局必须紧凑，不能为了高级感把留白做得很夸张
- 要考虑后台/业务系统的高频使用场景，保证扫描效率
- 保留当前技术栈、组件库和业务流程可实现性

输出：
1. 页面设计 brief
2. 页面模块划分与信息架构
3. 下游设计/实现 prompt
4. 验收标准
```

### 3. Table Optimization

```text
Use frontend-design-prompt + @Product Design.

需求：
这个表格太丑了，帮我优化一下。

要求：
- 目标是让表格更专业、更清晰、更精致
- 不要继承旧页面里粗糙的颜色、边框、间距和排版
- 保留表格的紧凑密度，行高和工具栏都不要太松
- 强化表头层级、筛选区、状态标签、行操作、分页、空状态、加载状态
- 风格要克制，不要过度装饰

输出：
1. Product Design-ready brief
2. 视觉优化指令
3. 实现验收标准
```

### 4. Form Or Dialog Polish

```text
Use frontend-design-prompt as the first step.

需求：
这个表单 / 弹窗不好看，优化一下。

要求：
- 重点提升精致感、层级、对齐、按钮主次关系、输入区观感
- 不需要延续旧样式，只保留业务逻辑和组件能力
- 控件间距要克制，整体保持紧凑
- 补齐 hover、focus、disabled、error、loading 等状态
- 移动端和窄宽度下也要成立

输出：
1. 扩写后的优化 brief
2. 下游设计 prompt
3. 前端实现检查清单
```

### 5. Codex Direct Implementation Prompt

```text
Use frontend-design-prompt in Implement After Brief mode.

我希望你直接改这个页面，不只是给建议。

目标：
- 让页面明显更好看
- 不要默认沿用旧系统不好看的视觉风格
- 保留当前框架、组件库、业务流程和交互逻辑
- 整体布局保持紧凑，间距不要过大
- 优先优化视觉层级、模块分组、间距、排版、状态样式和操作区设计

请先给一个简短 brief，然后直接实施修改。
```
