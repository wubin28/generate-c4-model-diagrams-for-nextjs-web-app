# Promptyoo-1 Next.js Web 应用迭代式开发计划

> 通过迭代式开发学习 Next.js 13 全栈开发
>
> 生成时间：2025-11-03 09:09
>
> 拆分策略：混合渐进式拆分（前期小步快跑，中期按功能模块，后期按特性）

---

## 📚 整体学习路线图概述

### 项目简介
Promptyoo-1 是一个 AI 提示词优化工具，帮助用户将简单的提示词优化为更专业、更完整的 AI 提示词。本项目采用 Next.js 13 全栈开发，通过 16 个渐进式迭代，从零开始构建完整的 Web 应用。

### 核心技术栈
- **框架**：Next.js 13.5.1 (App Router)
- **语言**：TypeScript 5.2.2
- **样式**：Tailwind CSS 3.3.3
- **UI 组件库**：Radix UI + shadcn/ui
- **状态管理**：React Context API
- **表单处理**：React Hook Form + Zod
- **主题管理**：next-themes
- **通知系统**：Sonner (Toast)
- **图标库**：Lucide React
- **API 集成**：DeepSeek API（支持流式响应）

### 学习阶段划分

#### 🌱 第一阶段：基础搭建与核心 UI（迭代 1-5）
**目标**：建立项目基础，实现基本的输入输出功能
- 小步快跑，建立信心
- 完成静态 UI 搭建
- 实现基础业务逻辑

#### 🚀 第二阶段：核心业务功能（迭代 6-10）
**目标**：实现核心的提示词优化功能
- 集成 AI API
- 实现流式响应
- 添加历史记录管理

#### ✨ 第三阶段：支持性功能与优化（迭代 11-16）
**目标**：完善用户体验，添加支持性功能
- 多语言和主题切换
- 用户认证系统
- 最终打磨和优化

---

## 🎯 详细迭代计划

### 迭代 1：初始化 Next.js 项目并创建 Hello World 页面

#### 📋 原子化业务需求
创建一个全新的 Next.js 项目，配置 TypeScript 和 Tailwind CSS，在浏览器中显示 "Hello, Promptyoo-1!" 文字，验证开发环境正常运行。

#### 🛠 技术选型概述
- **框架初始化**：使用 `npx create-next-app@13.5.1` 脚手架
- **App Router**：Next.js 13 的新路由系统（`app/` 目录）
- **TypeScript**：强类型语言，版本 5.2.2
- **Tailwind CSS**：实用优先的 CSS 框架，版本 3.3.3
- **开发服务器**：Next.js 内置的 dev server

#### 🎓 学习目标
- 掌握 Next.js 项目初始化流程和命令行工具
- 理解 App Router 的目录结构（`app/page.tsx`、`app/layout.tsx`）
- 学会配置 Tailwind CSS 和 TypeScript
- 了解 Next.js 开发服务器的启动和热重载机制

#### ✅ 验收标准
- [ ] 成功运行 `npm run dev`，开发服务器在 `http://localhost:3000` 启动
- [ ] 浏览器访问显示 "Hello, Promptyoo-1!" 文字
- [ ] Tailwind CSS 样式生效（可以通过添加 `text-blue-500` 等类验证）
- [ ] TypeScript 编译无错误，VSCode 中类型提示正常
- [ ] 项目目录结构符合 Next.js 13 App Router 规范

#### 📚 先决知识要求
- Node.js 和 npm 基础（了解如何安装和运行 npm 命令）
- React 基础概念（了解组件、JSX 语法）
- 基本的终端操作（cd、ls 等命令）
- HTML 和 CSS 基础

---

### 迭代 2：创建基础页面布局（Header + Main Content Area）

#### 📋 原子化业务需求
创建应用的基本页面结构，包含顶部 Header（显示应用标题 "AI Prompt Optimizer"）和主内容区域，采用上下分栏布局，为后续功能实现预留空间。

#### 🛠 技术选型概述
- **布局组件**：`app/layout.tsx`（根布局）+ `components/layouts/main-layout.tsx`（主布局）
- **Header 组件**：`components/layouts/header.tsx`
- **布局方案**：Tailwind CSS Flexbox（`flex flex-col h-screen`）
- **响应式设计**：使用 Tailwind 的响应式断点（`md:`、`lg:` 等）

#### 🎓 学习目标
- 理解 Next.js 的 Layout 系统和嵌套布局
- 学习组件化思维（将 Header 抽取为独立组件）
- 掌握 Tailwind CSS 的 Flexbox 布局类（`flex`、`flex-col`、`items-center` 等）
- 了解响应式设计原则和移动优先策略

#### ✅ 验收标准
- [ ] 页面顶部显示 Header，包含 "AI Prompt Optimizer" 标题
- [ ] Header 有明显的视觉分隔（如底部边框 `border-b`）
- [ ] 主内容区域占据剩余的垂直空间
- [ ] 布局在桌面端和移动端都正常显示
- [ ] 页面整体高度为 100vh，无滚动条（除非内容溢出）

#### 📚 先决知识要求
- 完成迭代 1
- CSS Flexbox 布局基础
- React 组件的 props 传递
- 基本的响应式设计概念

---

### 迭代 3：创建输入区域 UI 并配置 shadcn/ui

#### 📋 原子化业务需求
在主内容区域添加一个卡片式输入区域，包含标题 "Your prompt to be optimized"（带红色星号必填标记）和多行文本输入框，输入框显示占位符文字。同时完成 shadcn/ui 组件库的安装和配置。

#### 🛠 技术选型概述
- **shadcn/ui 配置**：
  - 初始化命令：`npx shadcn-ui@latest init`
  - 配置文件：`components.json`
  - 组件安装：`npx shadcn-ui@latest add card textarea`
- **使用组件**：Card、CardHeader、CardTitle、CardContent、Textarea
- **底层依赖**：Radix UI（无障碍组件库）
- **样式工具**：class-variance-authority（CVA）、clsx、tailwind-merge

#### 🎓 学习目标
- 学习 shadcn/ui 的安装和配置流程
- 理解 shadcn/ui 的工作原理（组件代码直接复制到项目，可自定义）
- 掌握 Card 组件的结构和使用（CardHeader、CardTitle、CardContent）
- 学习 React 受控组件概念（使用 `useState` 管理输入状态）
- 了解 Radix UI 的无障碍特性

#### ✅ 验收标准
- [ ] shadcn/ui 成功配置，`components/ui/` 目录已创建
- [ ] `components.json` 文件存在且配置正确
- [ ] 页面显示一个居中的卡片式输入区域
- [ ] 卡片标题显示 "Your prompt to be optimized"，星号为红色（`text-destructive`）
- [ ] 多行文本框（Textarea）可以正常输入和换行
- [ ] 占位符文字：`e.g. "recommend me some prompt optimization tools"`
- [ ] 输入框至少 100px 高度，可调整大小

#### 📚 先决知识要求
- 完成迭代 2
- React Hooks 基础（`useState`）
- 表单受控组件概念
- npm/npx 命令的使用

---

### 迭代 4：创建输出区域 UI 并实现基础优化功能

#### 📋 原子化业务需求
在输入区域下方添加优化结果展示区域（卡片式），包含 "Optimized prompt" 标题和结果显示区域。实现基础提示词优化功能：当用户输入原始提示词后，点击 "Optimize prompt" 按钮，系统将原始提示词包装为固定格式并显示在输出区域。

**优化规则**：
```
你是专家。{原始提示词}。请提供主要观点的网页链接，以便核实。如遇不确定信息，请如实告知，不要编造。
```

#### 🛠 技术选型概述
- **新增组件**：Button（shadcn/ui）、CardFooter
- **状态管理**：使用 `useState` 管理输入、输出和按钮禁用状态
- **事件处理**：`onClick` 事件处理优化逻辑
- **字符串处理**：JavaScript 模板字符串（Template Literals）
- **条件渲染**：输出区域的空状态和有内容状态

#### 🎓 学习目标
- 学习 React 状态管理（多个相关状态的协调）
- 掌握事件处理和业务逻辑实现
- 理解基础的字符串拼接和模板字符串
- 学习条件渲染技巧（三元运算符、逻辑与运算符）
- 了解按钮禁用状态的用户体验设计

#### ✅ 验收标准
- [ ] 输入卡片的 CardFooter 中显示 "Optimize prompt" 按钮
- [ ] 按钮在输入框为空时禁用（`disabled={isInputEmpty}`）
- [ ] 点击按钮后，输出区域显示优化后的提示词
- [ ] 优化逻辑正确：包含前缀 "你是专家。"、原始提示词、后缀 "。请提供主要观点的网页链接，以便核实。如遇不确定信息，请如实告知，不要编造。"
- [ ] 输出区域初始状态显示占位符："Your Optimized prompt will be displayed here. Optimize your prompt now!"
- [ ] 输出区域有背景色区分（如 `bg-muted/50`）

#### 📚 先决知识要求
- 完成迭代 3
- React 事件处理（`onClick`、`onChange`）
- JavaScript 字符串操作和模板字符串
- 条件判断和状态更新

---

### 迭代 5：添加复制按钮和交互优化

#### 📋 原子化业务需求
在输出区域的右上角添加 "Copy" 按钮，点击后将优化后的提示词复制到剪贴板，并显示成功提示。同时优化按钮在处理中显示加载状态（虽然当前是同步操作，但为后续异步 API 调用做准备）。

#### 🛠 技术选型概述
- **浏览器 API**：Clipboard API（`navigator.clipboard.writeText`）
- **通知组件**：Sonner（shadcn/ui 的 Toast 组件）
  - 安装：`npx shadcn-ui@latest add sonner`
  - 组件：`Toaster`（全局）、`toast` 函数（调用）
- **图标库**：Lucide React（`lucide-react`）
  - 图标：Copy、Wand2（魔法棒）
- **加载状态**：`isOptimizing` 状态管理

#### 🎓 学习目标
- 学习浏览器 Clipboard API 的使用
- 掌握 Toast 通知系统的集成和使用
- 理解异步操作的 UI 反馈最佳实践
- 学习图标库的集成和使用方法
- 了解加载状态对用户体验的重要性

#### ✅ 验收标准
- [ ] 输出区域右上角显示复制按钮（Copy 图标）
- [ ] 按钮样式为 ghost variant，尺寸为 sm
- [ ] 点击复制按钮，优化后的提示词被复制到剪贴板
- [ ] 复制成功后显示 Toast 提示："Copied to clipboard!"
- [ ] 优化按钮点击后显示加载状态（文字变为 "Optimizing..."，图标旋转 `animate-spin`）
- [ ] 只有当输出区域有内容时才显示复制按钮
- [ ] Toaster 组件已添加到 `app/layout.tsx`

#### 📚 先决知识要求
- 完成迭代 4
- 异步 JavaScript 基础（虽然当前是同步，但需理解概念）
- Promise 和 async/await 概念
- 浏览器 API 的使用

---

### 迭代 6：集成 DeepSeek API（非流式智能优化）

#### 📋 原子化业务需求
实现智能提示词优化模式：用户点击 "Optimize prompt" 后，如果是首次使用，弹出对话框要求输入 DeepSeek API 密钥。系统将原始提示词按照智能优化提示词模板发送给 DeepSeek API，接收完整响应后显示结果。如果 API 调用失败（网络问题、密钥无效等），自动降级到基础优化模式。

**智能优化提示词模板**：
```
请按以下步骤优化用户给出的原始提示词：

1. 创建一个空的"辅助优化提示词"，用于优化用户提供的原始提示词（见后文）。

2. 如果原始提示词未指定AI要扮演的角色，请根据提示词内容确定相关领域，然后在"辅助优化提示词"后添加"你是xxx领域的专家"。这里的"xxx"指你根据提示词确定的专业领域。

3. 如果原始提示词未说明回复格式要求，在"辅助优化提示词"后添加"请提供主要观点的网页链接，以便核实"。

4. 如果原始提示词未提及用户对AI的顾虑，在"辅助优化提示词"后添加"如遇不确定信息，请如实告知，不要编造"。

5. 使用整理好的"辅助优化提示词"优化下面的原始提示词。确保优化后的提示词清晰流畅，且只提供优化后的提示词，不要在结果提示词之前和之后附加其他说明。

用户的原始提示词是：{原始提示词}
```

#### 🛠 技术选型概述
- **后端 API**：Next.js API Routes
  - 文件：`app/api/api-key/route.ts`
  - 方法：GET（检查）、POST（存储）、DELETE（清除）
- **Session 管理**：内存存储（Map）+ HttpOnly Cookie
- **前端 Hook**：
  - `hooks/use-api-key.ts`：API 密钥管理
  - `hooks/use-optimizer.ts`：优化逻辑
- **对话框组件**：`components/ui/api-key-prompt.tsx`（Dialog + Input）
- **HTTP 请求**：Fetch API
- **错误处理**：try-catch + 降级策略

**DeepSeek API 规格**：
- Endpoint: `https://api.deepseek.com/v1/chat/completions`
- Method: POST
- Headers: `Authorization: Bearer {apiKey}`, `Content-Type: application/json`
- Body: `{ model: "deepseek-chat", messages: [...], temperature: 0.7, max_tokens: 1000 }`

#### 🎓 学习目标
- 学习 Next.js API Routes 的创建和使用
- 理解前后端数据交互流程（Request/Response）
- 掌握 RESTful API 调用方法
- 学习错误处理和降级策略（Fallback）
- 了解 Session 管理和 Cookie 的基础知识
- 理解自定义 Hook 的封装和复用

#### ✅ 验收标准
- [ ] 首次点击优化按钮时弹出 API 密钥输入对话框
- [ ] 对话框包含输入框和提交按钮
- [ ] 输入 API 密钥后可成功调用 DeepSeek API
- [ ] API 密钥安全存储在后端 Session 中（不存储在前端）
- [ ] 后端设置 HttpOnly Cookie 标识 Session
- [ ] 优化结果正确显示在输出区域
- [ ] API 调用失败时自动使用基础优化模式，并在终端输出日志
- [ ] 终端输出详细的 API 调用状态日志（请求、响应、错误等）
- [ ] 刷新页面后，如果 Session 有效，无需重新输入 API 密钥

#### 📚 先决知识要求
- 完成迭代 5
- HTTP 协议基础（GET、POST、请求头、请求体）
- REST API 概念
- async/await 语法
- 基础的后端概念（服务器、路由、Session）
- try-catch 错误处理

---

### 迭代 7：实现 DeepSeek API 流式响应

#### 📋 原子化业务需求
优化用户体验，将 DeepSeek API 调用改为流式响应（Streaming）：优化过程中，输出区域逐字逐句显示 AI 返回的内容（类似打字机效果），让用户能够尽早看到优化结果的开头部分，提升使用体验和期待感。

#### 🛠 技术选型概述
- **流式 API**：Server-Sent Events (SSE)
- **DeepSeek API 参数**：`stream: true`
- **浏览器 API**：ReadableStream（`response.body.getReader()`）
- **数据解析**：SSE 格式解析（`data: {json}\n\n`）
- **增量更新**：回调函数模式（`onStreamUpdate`）
- **UI 增强**：
  - 流式状态指示器（"正在流式输出..."）
  - 脉冲动画（`animate-pulse`）
  - 光标效果（模拟打字）

**SSE 数据格式**：
```
data: {"choices":[{"delta":{"content":"你"}}]}

data: {"choices":[{"delta":{"content":"是"}}]}

data: [DONE]
```

#### 🎓 学习目标
- 理解流式响应（Streaming）的工作原理和优势
- 学习 ReadableStream API 的使用
- 掌握 SSE（Server-Sent Events）数据格式的解析
- 学习增量式 UI 更新技巧
- 了解异步迭代器和事件驱动编程
- 掌握流式数据的错误处理

#### ✅ 验收标准
- [ ] 点击优化按钮后，输出区域开始逐字显示内容
- [ ] 流式过程中显示 "正在流式输出..." 状态提示
- [ ] 输出区域左侧有彩色边框高亮（`border-l-4 border-primary`）
- [ ] 内容逐步累积显示，无闪烁
- [ ] 流式完成后移除状态指示器
- [ ] 优化按钮在流式过程中显示 "流式优化中..." 状态
- [ ] 终端输出详细的流式数据接收日志（每个 chunk）
- [ ] 流式过程中可以看到内容逐步增长
- [ ] 流式结束标记 `[DONE]` 被正确处理

#### 📚 先决知识要求
- 完成迭代 6
- Stream API 基础概念
- 事件驱动编程思想
- 异步迭代器（async iterator）
- JSON 解析和字符串处理

---

### 迭代 8：添加左侧边栏布局

#### 📋 原子化业务需求
在页面左侧添加固定宽度的侧边栏，包含以下元素：
- 顶部：应用名称 "Promptyoo-1"
- 中上部："New optimization" 按钮（黑底白字，突出显示）
- 中间：历史记录区域（当前显示 "No history yet"）
- 底部：用户认证区域（当前显示 "Sign in" 和 "Sign up" 按钮）

点击 "New optimization" 按钮时，清空输入和输出区域，重置为初始状态。

#### 🛠 技术选型概述
- **布局方案**：Flexbox 左右分栏（`flex flex-row`）
- **侧边栏组件**：`components/layouts/sidebar.tsx`
- **主布局更新**：`components/layouts/main-layout.tsx`
- **宽度控制**：固定宽度 `w-72`（288px）
- **侧边栏内部布局**：Flexbox 垂直布局（`flex flex-col`）
- **状态管理**：新增 `newOptimization` 函数清空状态

#### 🎓 学习目标
- 学习复杂布局的实现（左右分栏 + 内部垂直布局）
- 掌握固定宽度侧边栏与自适应内容区的配合
- 理解组件间状态传递和通信
- 学习 Flexbox 的 `flex-1`（占据剩余空间）
- 了解侧边栏的响应式处理（移动端可隐藏或抽屉式）

#### ✅ 验收标准
- [ ] 页面左侧显示宽度为 288px 的侧边栏
- [ ] 侧边栏右侧有边框分隔（`border-r`）
- [ ] 侧边栏顶部显示 "Promptyoo-1" 标题
- [ ] "New optimization" 按钮样式为黑底白字（`bg-primary text-primary-foreground`）
- [ ] 按钮有图标（PlusCircle）
- [ ] 历史记录区域显示 "No history yet" 占位文字
- [ ] 底部显示 "Sign in" 和 "Sign up" 两个并排按钮
- [ ] 点击 "New optimization" 清空输入和输出区域
- [ ] 侧边栏和主内容区高度都占满整个视口
- [ ] 布局在不同屏幕尺寸下正常显示

#### 📚 先决知识要求
- 完成迭代 7
- CSS Grid 或 Flexbox 进阶
- React 状态提升（Lifting State Up）
- 组件通信模式

---

### 迭代 9：实现历史记录存储与展示

#### 📋 原子化业务需求
每次成功完成提示词优化后，自动将记录保存到浏览器本地存储（localStorage）。历史记录显示在侧边栏的历史记录区域，按时间分组（Today、Yesterday、更早日期），每条记录显示原始提示词的前 16 个字符作为标题（超过 16 字显示 "..."）。点击历史记录可以在右侧查看完整的原始提示词和优化后的提示词，选中的记录有浅灰色背景高亮。

#### 🛠 技术选型概述
- **数据存储**：localStorage API
- **数据结构**：
  ```typescript
  interface HistoryItem {
    id: string;
    title: string;  // 前30个字符
    originalPrompt: string;
    optimizedPrompt: string;
    timestamp: string;  // ISO格式
  }
  ```
- **状态管理**：React Context API
  - Provider: `components/providers/history-provider.tsx`
  - Hook: `hooks/use-history.ts`
- **时间处理**：date-fns 库（格式化和分组）
- **列表渲染**：分组后的数组 map 渲染
- **类型定义**：`types/index.ts`

#### 🎓 学习目标
- 学习浏览器 localStorage API 的使用
- 掌握 React Context API 进行全局状态管理
- 理解数据持久化的概念和实现
- 学习时间处理和格式化（date-fns）
- 掌握复杂的列表渲染和分组展示
- 了解数组的高级操作（sort、filter、reduce、groupBy）

#### ✅ 验收标准
- [ ] 优化成功后记录自动保存到 localStorage（key: `promptyoo-history`）
- [ ] 侧边栏历史记录区域显示历史记录列表
- [ ] 记录按时间倒序排列（最新的在最上面）
- [ ] 记录按日期分组：Today、Yesterday、具体日期（如 "November 1, 2025"）
- [ ] 每条记录显示最多 16 个字符，超过显示 "..."
- [ ] 点击记录后右侧显示完整的原始和优化后的提示词
- [ ] 选中的记录有浅灰色背景（`bg-muted`）
- [ ] 查看历史记录时输入框禁用，优化按钮禁用
- [ ] 历史记录为空时显示 "No history yet"
- [ ] 页面刷新后历史记录仍然存在

#### 📚 先决知识要求
- 完成迭代 8
- localStorage API 基础
- React Context API 和 useContext
- 数组的高级操作（sort、reduce）
- TypeScript 接口定义

---

### 迭代 10：实现历史记录编辑与删除功能

#### 📋 原子化业务需求
为历史记录添加完整的 CRUD 操作：
- **编辑**：鼠标悬停在历史记录上时，右侧显示编辑图标（Edit）。点击后标题变为可编辑状态（Input），按 Enter 保存修改，清空后按 Enter 保持原标题。
- **删除**：悬停时显示删除图标（红色 Trash2）。点击后弹出确认对话框，显示 "是否删除？" 和记录标题，确认后永久删除记录。
- **Tooltip**：超过 16 个字符的标题，悬停时显示 Tooltip，展示前 30 个字符。

#### 🛠 技术选型概述
- **Tooltip 组件**：shadcn/ui Tooltip（基于 Radix UI）
- **确认对话框**：shadcn/ui AlertDialog
- **输入组件**：shadcn/ui Input
- **图标**：Lucide React（Edit, Trash2）
- **悬停状态**：CSS 伪类（`group-hover:`）+ React 状态
- **编辑状态管理**：`editingId` 和 `editTitle` 状态
- **CRUD 操作**：Context 中添加 `editHistoryTitle` 和 `deleteHistory` 方法

#### 🎓 学习目标
- 学习复杂的用户交互实现（悬停、编辑、确认）
- 掌握 Tooltip 和 AlertDialog 组件的使用
- 理解 CRUD 操作的完整流程
- 学习悬停状态的 CSS 技巧（`group` 和 `group-hover`）
- 了解用户友好的交互设计（确认对话框、输入验证）
- 掌握条件渲染的复杂场景

#### ✅ 验收标准
- [ ] 鼠标悬停在历史记录上时，右侧显示编辑和删除图标
- [ ] 图标默认隐藏，悬停时才显示（`hidden group-hover:flex`）
- [ ] 点击编辑图标后，标题变为 Input 组件，自动聚焦
- [ ] 在 Input 中按 Enter 保存修改，更新 localStorage 和 UI
- [ ] 清空 Input 后按 Enter，保持原标题不变
- [ ] 点击删除图标弹出 AlertDialog 确认对话框
- [ ] 对话框显示 "确认删除" 标题和记录标题
- [ ] 确认删除后记录从 localStorage 和 UI 中移除
- [ ] 超过 16 个字符的标题悬停时显示 Tooltip（展示前 30 个字符）
- [ ] 所有操作实时同步到 localStorage

#### 📚 先决知识要求
- 完成迭代 9
- 表单编辑状态管理
- 对话框组件的使用
- CSS group 和 group-hover 技巧

---

### 迭代 11：实现多语言切换功能

#### 📋 原子化业务需求
添加中英文切换功能。在 Header 右上角添加语言切换按钮（Languages 图标，位于主题切换按钮左侧），点击后在中英文之间切换，所有界面文字相应改变。默认显示英文，语言选择保存到 localStorage，刷新后保持用户选择。

#### 🛠 技术选型概述
- **i18n 实现**：自定义国际化方案（基于 Context）
- **Provider**: `components/providers/language-provider.tsx`
- **Hook**: `hooks/use-language.ts`
- **翻译文件**: `lib/translations.ts`
- **数据结构**：
  ```typescript
  export const translations = {
    en: { key: 'English text', ... },
    zh: { key: '中文文字', ... }
  };
  ```
- **类型定义**: `type Language = 'en' | 'zh';`
- **持久化**: localStorage (key: `promptyoo-language`)

**需要翻译的文本**：
- 所有界面标题、按钮文字、占位符、提示信息
- 历史记录的时间分组标签（Today, Yesterday 等）
- Toast 通知消息
- 对话框文字

#### 🎓 学习目标
- 学习国际化（i18n）的基础实现
- 掌握多语言内容的管理和组织
- 理解语言切换的状态管理和传递
- 学习文本外部化的最佳实践
- 了解 TypeScript 在 i18n 中的类型安全

#### ✅ 验收标准
- [ ] Header 右上角显示语言切换按钮（Languages 图标）
- [ ] 按钮位于主题切换按钮左侧
- [ ] 点击按钮在中英文之间切换
- [ ] 所有界面文字正确翻译（包括按钮、标题、占位符等）
- [ ] 历史记录的时间分组标签支持多语言（Today/今天、Yesterday/昨天）
- [ ] Toast 通知消息支持多语言
- [ ] 语言选择保存到 localStorage
- [ ] 刷新页面后保持用户选择的语言
- [ ] 默认语言为英文

#### 📚 先决知识要求
- 完成迭代 10
- 基础的国际化（i18n）概念
- 对象键值映射和访问
- TypeScript 字面量类型

---

### 迭代 12：实现主题切换功能（浅色/深色模式）

#### 📋 原子化业务需求
添加浅色和深色主题切换功能。在 Header 右上角最右侧添加主题切换按钮，浅色模式显示 Moon 图标，深色模式显示 Sun 图标。点击按钮在两种主题之间切换，所有组件的颜色和样式相应改变。默认为浅色模式，主题选择保存到 localStorage。

#### 🛠 技术选型概述
- **主题库**：next-themes（Next.js 官方推荐）
- **安装**：`npm install next-themes`
- **Provider**: `components/providers/theme-provider.tsx`
- **配置**：
  ```typescript
  <ThemeProvider
    attribute="class"
    defaultTheme="light"
    enableSystem={false}
    storageKey="promptyoo-theme"
  >
  ```
- **Tailwind 配置**：`tailwind.config.ts` 中启用 `darkMode: ['class']`
- **CSS 变量**：在 `app/globals.css` 中定义浅色和深色主题的颜色变量
- **Hook**: `useTheme()` from next-themes

#### 🎓 学习目标
- 学习 next-themes 库的安装和使用
- 理解 CSS 变量在主题切换中的作用
- 掌握 Tailwind CSS dark mode 的配置和使用
- 学习 `dark:` 前缀的使用方法
- 了解主题持久化和系统主题检测
- 理解 `suppressHydrationWarning` 的作用

#### ✅ 验收标准
- [ ] Header 右上角最右侧显示主题切换按钮
- [ ] 浅色模式显示 Moon 图标，深色模式显示 Sun 图标
- [ ] 点击按钮平滑切换主题（无闪烁）
- [ ] 所有 shadcn/ui 组件在两种主题下正常显示
- [ ] 背景、文字、边框等颜色在两种主题下对比度适宜
- [ ] 主题选择保存到 localStorage (key: `promptyoo-theme`)
- [ ] 刷新页面后保持用户选择的主题
- [ ] 默认主题为浅色（light）
- [ ] 页面加载时无主题闪烁（FOUC）

#### 📚 先决知识要求
- 完成迭代 11
- CSS 变量（Custom Properties）基础
- Tailwind CSS dark mode 概念
- React Provider 模式

---

### 迭代 13：实现用户注册与登录功能

#### 📋 原子化业务需求
在侧边栏底部添加用户认证功能：
- **未登录状态**：显示 "Sign in" 和 "Sign up" 两个并排按钮
- **注册流程**：点击 "Sign up" 弹出注册对话框，输入用户名和两次密码，密码一致后注册成功，自动登录，用户获得默认头像
- **登录流程**：点击 "Sign in" 弹出登录对话框，输入用户名和密码，验证成功后登录
- **登录状态**：显示用户头像（Avatar，显示用户名首字母）和 "My profile" 文字

用户信息存储在 localStorage 中（模拟后端数据库）。

#### 🛠 技术选型概述
- **认证 Context**: `components/providers/auth-provider.tsx`
- **Hook**: `hooks/use-auth.ts`
- **对话框组件**: `components/features/auth-dialog.tsx`（统一的认证对话框）
- **表单处理**: React Hook Form + Zod 验证
  - 安装：`npm install react-hook-form zod @hookform/resolvers`
- **Avatar 组件**: shadcn/ui Avatar（显示首字母）
- **数据存储**:
  - 用户列表：`promptyoo-users` (localStorage)
  - 当前用户：`promptyoo-user` (localStorage)
- **数据结构**:
  ```typescript
  interface User {
    id: string;
    username: string;
  }
  ```

**验证规则**：
- 用户名：非空
- 密码：非空，两次输入一致
- 用户名唯一性检查（注册时）

#### 🎓 学习目标
- 学习表单验证库（React Hook Form + Zod）
- 掌握用户认证流程的实现（模拟）
- 理解状态机概念（未登录/已登录状态）
- 学习用户会话管理基础
- 了解密码处理的基本概念（虽然是模拟）
- 掌握 Avatar 组件的使用

#### ✅ 验收标准
- [ ] 侧边栏底部未登录时显示 "Sign in" 和 "Sign up" 按钮
- [ ] 点击 "Sign up" 弹出注册对话框
- [ ] 注册对话框包含用户名、密码、确认密码输入框
- [ ] 密码不匹配时显示错误提示
- [ ] 用户名重复时显示错误提示
- [ ] 注册成功后自动登录，关闭对话框
- [ ] 点击 "Sign in" 弹出登录对话框
- [ ] 登录对话框包含用户名和密码输入框
- [ ] 登录失败时显示错误提示
- [ ] 登录成功后底部显示用户头像和 "My profile"
- [ ] 头像显示用户名首字母的大写
- [ ] 用户信息保存到 localStorage
- [ ] 刷新页面后保持登录状态

#### 📚 先决知识要求
- 完成迭代 12
- 表单处理基础
- 数据验证概念
- React Hook Form 基础
- Zod schema 定义

---

### 迭代 14：实现用户个人资料设置功能

#### 📋 原子化业务需求
为登录用户添加个人资料管理功能：
- **用户菜单**：点击 "My profile" 显示下拉菜单，包含：
  - 菜单标签：当前用户名
  - Settings 选项（带 Settings 图标）
  - Log out 选项（带 LogOut 图标）
- **设置功能**：点击 Settings 打开设置对话框，用户可以修改密码（输入两次新密码，无需验证原密码）
- **退出登录**：点击 Log out 退出登录，侧边栏恢复为 "Sign in" 和 "Sign up" 按钮，历史记录清空显示

#### 🛠 技术选型概述
- **DropdownMenu 组件**: shadcn/ui DropdownMenu
  - 组件：DropdownMenuTrigger、DropdownMenuContent、DropdownMenuItem 等
- **设置对话框**: 复用 AuthDialog 组件，mode='settings'
- **表单处理**: React Hook Form（密码修改）
- **状态更新**: Context 中的 `updateProfile` 和 `logout` 方法
- **历史记录联动**: 退出登录时清空历史记录显示（但不删除数据）

#### 🎓 学习目标
- 学习下拉菜单组件的使用
- 掌握用户资料更新流程
- 理解用户数据与业务数据的关联
- 学习退出登录的状态清理
- 了解组件复用的策略（一个对话框多种模式）

#### ✅ 验收标准
- [ ] 点击 "My profile" 显示下拉菜单
- [ ] 菜单顶部显示当前用户名（DropdownMenuLabel）
- [ ] 菜单有分隔线（DropdownMenuSeparator）
- [ ] Settings 和 Log out 选项有对应图标
- [ ] 点击 Settings 打开设置对话框
- [ ] 设置对话框标题为 "Settings"
- [ ] 对话框包含新密码和确认新密码输入框
- [ ] 密码不匹配时显示错误提示
- [ ] 密码修改成功后更新到 localStorage，显示成功提示
- [ ] 点击 Log out 退出登录
- [ ] 退出后侧边栏恢复显示 "Sign in" 和 "Sign up"
- [ ] 退出后历史记录区域显示 "No history yet"
- [ ] localStorage 中的 `promptyoo-user` 被移除

#### 📚 先决知识要求
- 完成迭代 13
- DropdownMenu 交互模式
- 状态清理和重置
- 组件 mode 切换模式

---

### 迭代 15：完善 API 密钥管理功能

#### 📋 原子化业务需求
优化 API 密钥的用户体验：
- **状态指示器**：在输入区域标题行添加 API 密钥状态显示
  - 已保存：绿色 Key 图标 + "API密钥已保存" 文字 + 红色删除按钮（Trash2 图标）
  - 未保存：不显示状态
- **删除功能**：点击删除按钮清除已保存的 API 密钥，显示成功提示，下次使用需重新输入
- **视觉提示**：优化按钮在未保存 API 密钥时显示半透明钥匙图标，提示用户需要输入密钥
- **自动检查**：页面加载时自动检查后端 Session 中是否有有效的 API 密钥

#### 🛠 技术选型概述
- **API 路由增强**: 完善 `app/api/api-key/route.ts` 的 DELETE 方法
- **Hook 更新**: `hooks/use-api-key.ts` 添加 `clearApiKey` 方法
- **UI 组件更新**: `components/features/prompt-optimizer.tsx`
- **状态管理**: `isChecking` 状态（检查中）、`hasApiKey` 状态（是否有密钥）
- **视觉反馈**: Key 图标、Trash2 图标、颜色类（`text-green-500`、`text-red-500`）

#### 🎓 学习目标
- 学习用户友好的状态提示设计
- 掌握 API 密钥的完整生命周期管理
- 理解安全性与便利性的平衡
- 学习用户反馈的最佳实践
- 了解加载状态的多种表现形式

#### ✅ 验收标准
- [ ] 输入区域标题行右侧显示 API 密钥状态
- [ ] API 密钥已保存时显示：绿色 Key 图标 + "API密钥已保存" + 红色删除按钮
- [ ] 删除按钮为 ghost variant，尺寸为 sm，带 Trash2 图标
- [ ] 点击删除按钮后调用 DELETE API
- [ ] 删除成功后显示 Toast："API密钥已清除，下次使用时需要重新输入"
- [ ] 删除后状态更新，下次点击优化按钮会弹出输入对话框
- [ ] 未保存 API 密钥时，优化按钮右侧显示半透明 Key 图标（`opacity-50`）
- [ ] 页面加载时显示 "检查API密钥..." 状态（按钮禁用）
- [ ] 检查完成后按钮恢复正常状态
- [ ] 后端 Session 中的 API 密钥和 Cookie 都被正确清除

#### 📚 先决知识要求
- 完成迭代 14
- HTTP DELETE 方法
- 状态指示器设计模式
- 用户体验优化思维

---

### 迭代 16：用户历史记录关联与最终优化

#### 📋 原子化业务需求
实现历史记录的用户隔离和最终的 UI 打磨：
- **历史记录隔离**：
  - 未登录用户：历史记录保存在 `promptyoo-history`
  - 登录用户：历史记录保存在 `promptyoo-history-{userId}`
  - 用户登录后自动加载其专属历史记录
  - 退出登录后侧边栏清空历史记录（但不删除 localStorage 数据）
- **动画优化**：
  - 优化结果显示时淡入动画（`animate-fade-in`）
  - 流式输出时左边框高亮和脉冲动画
  - "New optimization" 按钮点击时有微交互反馈
- **代码优化**：
  - 清理未使用的代码和注释
  - 统一代码风格
  - 添加关键注释说明

#### 🛠 技术选型概述
- **localStorage 分区策略**: 根据用户 ID 使用不同的存储 key
- **动画实现**: Tailwind CSS 动画类 + `app/globals.css` 自定义动画
  ```css
  @keyframes fade-in {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .animate-fade-in {
    animation: fade-in 0.3s ease-out;
  }
  ```
- **状态联动**: AuthProvider 和 HistoryProvider 的协调
- **最终检查**: ESLint、TypeScript 类型检查、构建测试

#### 🎓 学习目标
- 学习数据隔离和用户数据管理
- 掌握 CSS 动画的定义和使用
- 理解用户体验的细节打磨
- 学习代码优化和重构技巧
- 了解项目交付前的检查清单

#### ✅ 验收标准
- [ ] 未登录用户的历史记录保存在 `promptyoo-history`
- [ ] 登录用户的历史记录保存在 `promptyoo-history-{userId}`
- [ ] 用户登录后自动调用 `loadHistoryFromStorage()`，加载其专属历史
- [ ] 不同用户的历史记录完全隔离
- [ ] 退出登录后侧边栏清空历史记录显示
- [ ] 再次登录同一用户，历史记录恢复显示
- [ ] 优化结果显示时有平滑的淡入动画
- [ ] 流式输出时左边框有彩色高亮（`border-l-4 border-primary`）
- [ ] 流式输出过程中有脉冲动画（`animate-pulse`）
- [ ] 所有交互流畅，无明显延迟或卡顿
- [ ] 运行 `npm run build` 无错误和警告
- [ ] TypeScript 类型检查全部通过
- [ ] 代码注释清晰，关键逻辑有说明

#### 📚 先决知识要求
- 完成迭代 15
- CSS 动画基础（@keyframes）
- 代码重构思想
- 项目构建和发布流程

---

## 📝 实施检查清单（IMPLEMENTATION CHECKLIST）

1. 初始化 Next.js 13.5.1 项目，配置 TypeScript 和 Tailwind CSS，创建 Hello World 页面
2. 创建基础页面布局（Header 组件 + Main Content Area）
3. 配置 shadcn/ui，创建输入区域 UI（Card + Textarea）
4. 创建输出区域 UI，实现基础提示词优化功能（字符串拼接）
5. 添加复制按钮和交互优化（Clipboard API + Toast）
6. 创建 Next.js API Routes，集成 DeepSeek API（非流式）
7. 实现 DeepSeek API 流式响应
8. 添加左侧边栏布局和 "New optimization" 功能
9. 实现历史记录存储与展示（localStorage + Context API）
10. 实现历史记录编辑与删除功能（CRUD 完整）
11. 实现多语言切换功能（中英文 i18n）
12. 实现主题切换功能（浅色/深色模式）
13. 实现用户注册与登录功能（React Hook Form + Zod）
14. 实现用户个人资料设置功能（密码修改 + 退出登录）
15. 完善 API 密钥管理功能（状态指示 + 删除功能）
16. 实现用户历史记录关联与最终优化（数据隔离 + 动画效果）

---

## 🎯 学习成果总结

完成本项目所有迭代后，您将掌握：

### 前端技能
- ✅ Next.js 13 App Router 架构
- ✅ TypeScript 在 React 中的应用
- ✅ Tailwind CSS 实用优先的样式开发
- ✅ shadcn/ui 组件库的使用和自定义
- ✅ React Hooks（useState, useEffect, useContext, 自定义 Hook）
- ✅ React Context API 全局状态管理
- ✅ React Hook Form + Zod 表单验证
- ✅ 响应式设计和移动端适配
- ✅ 动画和微交互设计

### 后端技能
- ✅ Next.js API Routes 后端接口开发
- ✅ RESTful API 设计和实现
- ✅ Session 管理和 Cookie 使用
- ✅ HTTP 请求和响应处理
- ✅ 流式响应（Streaming）实现

### 全栈技能
- ✅ 前后端数据交互
- ✅ 第三方 API 集成（DeepSeek API）
- ✅ 用户认证流程（模拟）
- ✅ 数据持久化（localStorage）
- ✅ 国际化（i18n）实现
- ✅ 主题切换（深色/浅色模式）
- ✅ 错误处理和降级策略

### 工程能力
- ✅ 组件化思维和代码组织
- ✅ TypeScript 类型系统
- ✅ 代码重构和优化
- ✅ 用户体验设计
- ✅ 项目构建和部署

---

## 📌 注意事项

1. **环境要求**：
   - Node.js 16+
   - npm 或 yarn
   - 现代浏览器（支持 ES6+）

2. **API 密钥**：
   - 需要自行注册 DeepSeek 账号并获取 API 密钥
   - API 密钥在后端 Session 中存储，关闭浏览器后失效（安全）

3. **数据存储**：
   - 用户数据和历史记录存储在 localStorage（仅用于学习演示）
   - 生产环境应使用真实的后端数据库

4. **学习建议**：
   - 按照迭代顺序逐步实现，不要跳过
   - 每个迭代完成后测试验收标准
   - 遇到问题先查阅文档，再寻求帮助
   - 尝试理解每行代码的作用，不要盲目复制

5. **扩展方向**：
   - 集成真实的数据库（PostgreSQL、MongoDB）
   - 实现真实的用户认证（JWT、OAuth）
   - 添加更多 AI 模型支持（OpenAI、Claude）
   - 实现服务端渲染（SSR）优化
   - 部署到生产环境（Vercel、AWS）

---

## 🔗 相关资源

- [Next.js 官方文档](https://nextjs.org/docs)
- [React 官方文档](https://react.dev/)
- [TypeScript 手册](https://www.typescriptlang.org/docs/)
- [Tailwind CSS 文档](https://tailwindcss.com/docs)
- [shadcn/ui 组件库](https://ui.shadcn.com/)
- [Radix UI 文档](https://www.radix-ui.com/docs/primitives/overview/introduction)
- [DeepSeek API 文档](https://platform.deepseek.com/api-docs/)

---

**祝您学习愉快！通过这 16 个迭代，您将从 Next.js 初学者成长为能够独立开发全栈 Web 应用的开发者。** 🚀
