# Frontend Design Prompt

**[English](README.md) | [中文](README_zh.md)**

Frontend Design Prompt 是一个面向无专职 UI 设计师团队的 prompt 扩展技能。

它能将模糊的前端请求（如"这个表格不好看，帮我优化一下"）自动扩写为结构化的 UI 设计 brief、下游 handoff prompt 和实现验收标准。

## 工作原理

作为第一步使用：

```text
开发者的模糊请求
-> Frontend Design Prompt 将请求扩展为具体的 UI brief
-> 可用的下游工具使用该 brief
-> Codex/Claude 实现最终结果
```

示例搭配：

- Claude Code + UI/UX PRO MAX
- Codex + Product Design

这些只是示例，不是依赖。使用当前环境中可用的任何下游工具、技能、IDE agent 或人工评审。

该技能在以下场景特别有用：

- 有需求文档但没有 UI 设计稿
- 页面功能正常但看起来普通或不一致
- 开发者说"做好看一点"或"优化这个组件"
- 设计需要明显更好看，但不能变得松散或过于宽松

## v0.3.1 更新

此版本让技能更明确地偏向视觉改进方向：

- 将技能重命名为 `frontend-design-prompt`。
- 技能与工具无关。Product Design 和 UI/UX PRO MAX 是示例，不是必需依赖。
- 新增明确的输出模式：
  - 仅 Brief：将模糊请求转为清晰的 UI brief。
  - Handoff prompt：为其他工具、agent 或队友创建可直接复制的任务 prompt。
  - 先 Brief 后实现：先创建 brief，再修改当前项目。
- 移除"保留旧系统外观"作为默认目标。
- 保留紧凑布局和克制间距作为硬性约束。
- 新增 `references/style-audit-checklist.md` 用于从现有项目提取实用约束。
- 新增 `references/before-after-examples.md` 包含真实的短请求扩展示例。
- 更新 `references/prompt-patterns.md` 包含通用的下游 handoff 模板。

## 在 Codex 中安装

将此文件夹复制到：

```text
C:\Users\<your-user>\.codex\skills\frontend-design-prompt\
```

期望的目录结构：

```text
frontend-design-prompt/
├── SKILL.md
├── README.md
└── references/
    ├── before-after-examples.md
    ├── prompt-patterns.md
    └── style-audit-checklist.md
```

然后在 Codex 中配合 Product Design 使用：

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

## 在 Claude Code 中安装

将此文件夹复制到个人或项目技能目录：

```text
C:\Users\<your-user>\.claude\skills\frontend-design-prompt\
```

或在项目内部：

```text
<project>\.claude\skills\frontend-design-prompt\
```

然后这样调用：

```text
/frontend-design-prompt

这个表格不好看，帮我优化一下。
请先把这句话扩写成详细 UI 设计 brief，再交给 UI/UX PRO MAX 做 UX、一致性、可访问性和实现质量检查。
不要默认延续旧系统的视觉风格。目标是更好看，但布局必须保持紧凑，间距不要过大，业务流程和组件能力要可实现。
```

## 推荐的 Prompt 模式

当希望技能作为前置步骤时使用：

```text
Use frontend-design-prompt as the first step.

Short request:
[粘贴开发者的模糊请求]

Context:
[需求文档、截图、当前路由、组件名称或代码路径]

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

## 输出模式

根据需要选择以下模式：

- 仅 Brief：将模糊请求转为清晰的 UI brief 用于讨论。
- Handoff prompt：为其他工具、agent 或队友创建可直接复制的任务 prompt。
- 先 Brief 后实现：先创建 brief，再修改当前项目。

当用户提到其他工具、请求 prompt 或想将任务传递给下游时，默认使用 Handoff prompt 模式。

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

## 示例

输入：

```text
这个表格不好看，帮我优化一下。@Product Design
```

期望输出：

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

## 中文最佳实践 Prompt

当希望技能可靠地生成更好看的 UI 同时保持布局紧凑时，使用以下示例。

### 1. 现有后台页面视觉升级

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

### 2. 从需求文档创建新页面

```text
Use frontend-design-prompt as the first step.

需求：
根据这份需求文档设计一个新页面。

要求：
- 页面要以"更好看"为优先，不要参考旧系统里不美观的视觉样式
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

### 3. 表格优化

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

### 4. 表单或弹窗优化

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

### 5. Codex 直接实现 Prompt

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