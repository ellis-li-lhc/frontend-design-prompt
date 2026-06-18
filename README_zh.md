# Frontend Design Prompt

**[English](README.md) | [中文](README_zh.md)**

`frontend-design-prompt` 是一个 Codex skill，用来把模糊的前端 UI 请求扩写成清晰的设计 brief、下游 handoff prompt 和实现验收标准。

当前版本：1.1.0

它适合没有专职 UI 设计师的团队，也适合处理“功能已经能用，但页面看起来普通、拥挤、不协调、不够精致”的情况。

## 适用场景

- 把“优化一下页面”“高级一点”“不好看”这类请求变成可执行的 UI 方向。
- 为 Product Design、UI/UX PRO MAX、其他设计工具、代码 agent 或人工协作者生成 handoff prompt。
- 保留业务流程、组件库限制、交互状态、紧凑密度等实际约束。
- 避免默认继承旧系统里不美观的视觉样式。
- 判断输入属于短请求、需求文档、截图、现有页面、代码路径，还是下游 handoff 任务。
- 针对表格、仪表盘、表单、详情页、设置页、弹窗、登录页和落地页生成更具体的页面类型指导。

## 核心原则

提升 UI 的视觉质量和可用性，同时保持产品工作流高效。

对于后台、SaaS、dashboard、CRM 等业务系统，优先选择紧凑、易扫描的布局，而不是松散的营销页式留白。保留对实现和业务流程真正重要的内容，不默认保留过时的颜色、间距、边框或层级。

处理现有项目时，先检查技术栈、组件库、相邻页面、设计 token、业务流程和状态覆盖，再输出最终 redesign 指令。

## 输出模式

### 仅 Brief

用于在设计或实现前先澄清方向。

输出：

- 结构化 UI brief
- 推断假设
- 需要遵守的约束
- Must/Should/Nice 验收标准

### Handoff Prompt

用于把任务交给其他工具、agent、设计师或开发者。

输出：

- 原始请求
- 推断假设
- 需要遵守的约束
- 设计目标和范围
- 下游执行说明
- UX 和视觉评审标准
- Must/Should/Nice 实现验收标准

### 先 Brief 后实现

用于让 Codex 直接修改项目。

先输出一个简短 brief，再基于当前技术栈、业务流程和组件约束实施 UI 修改。

## 推荐 Prompt

```text
Use frontend-design-prompt as the first step.

Short request:
[粘贴模糊的前端请求]

Context:
[需求文档、截图、路由、组件名称或代码路径]

Constraints:
- 让 UI 看起来更有设计感、更精致、更明确
- 布局保持紧凑高效
- 保留业务流程、组件库限制和重要交互状态
- 不默认继承旧系统里不美观的视觉样式
- 避免过大的间距、过度渐变、装饰性卡片堆叠或营销页式布局

Output:
1. 扩写后的 UI brief
2. 下游 handoff prompt 或评审标准
3. Must/Should/Nice 实现验收标准
```

## 示例：表格优化

```text
Use frontend-design-prompt + Product Design.

需求：
这个表格不好看，帮我优化一下。

请先扩写成 Product Design-ready brief。
表格需要保持紧凑，并适合高频业务操作。
保留当前框架、组件库、业务流程和交互状态。
不要默认继承旧页面里粗糙的视觉样式。

输出：
1. Product Design-ready brief
2. 视觉优化指令
3. 实现验收标准
```

## 示例：直接实现

```text
Use frontend-design-prompt in Implement After Brief mode.

我希望你直接改这个页面，不只是给建议。

目标：
- 让页面明显更好看
- 布局保持紧凑
- 保留当前框架、组件库、业务流程和交互逻辑
- 优先优化层级、分组、间距、排版、状态样式和操作区设计
- 不默认沿用旧系统里不美观的视觉风格

请先给一个简短 brief，然后直接实施修改。
```

## 安装

复制整个 `frontend-design-prompt/` 文件夹，包括 `SKILL.md` 和 `references/`。

### Codex

作为个人 Codex skill 安装：

```text
C:\Users\<your-user>\.codex\skills\frontend-design-prompt\
```

然后这样使用：

```text
Use frontend-design-prompt as the first step.
```

### Claude Code

作为个人 Claude Code skill 安装：

```text
~/.claude/skills/frontend-design-prompt/
```

或只安装到某个项目：

```text
<project>/.claude/skills/frontend-design-prompt/
```

直接调用：

```text
/frontend-design-prompt
```

Claude Code 也会在请求匹配 skill 描述时自动加载。参考 [Claude Code skills 文档](https://code.claude.com/docs/en/skills)。

### opencode

作为全局 opencode skill 安装：

```text
~/.config/opencode/skills/frontend-design-prompt/
```

或只安装到某个项目：

```text
<project>/.opencode/skills/frontend-design-prompt/
```

opencode 也会发现 Claude 兼容和 Agent Skills 兼容的位置：

```text
<project>/.claude/skills/frontend-design-prompt/
~/.claude/skills/frontend-design-prompt/
<project>/.agents/skills/frontend-design-prompt/
~/.agents/skills/frontend-design-prompt/
```

使用时可以让 opencode 加载 `frontend-design-prompt`，也可以直接提出匹配该 skill 描述的请求。参考 [opencode Agent Skills 文档](https://opencode.ai/docs/skills/)。

期望目录结构：

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
