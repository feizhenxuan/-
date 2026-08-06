# Ant Design 组件使用分析

> 分析项目中用了哪些 antd 组件，哪些没用，以及原因。

---

## 一、Chat 页面（对话页面）

**文件**：`src/pages/Chat/index.tsx`

### 用了的组件

| 组件 | 位置 | 用途 | 为什么用 |
|------|------|------|---------|
| **Avatar** | L219 | 区分用户/AI 头像 | 需要图标 + 背景色区分对话双方 |
| **Button** | L284, L350 | 发送按钮 + 复制按钮 | 需要 loading 状态防重复提交，需要图标切换 |
| **Input** | L335 | 消息输入框 | 需要 onPressEnter 回车发送，disabled 防止重复发送 |
| **message** | L51, L54 | 全局提示 | 复制成功/失败反馈 |

### 没用的组件

| 组件 | 为什么没用 |
|------|-----------|
| **Card** | 卡片用 div + 内联样式手写，更灵活 |
| **List** | 消息列表用 div + map 循环渲染 |
| **Spin** | 加载动画用 CSS 动画（三个跳动圆点） |
| **Modal** | 没有弹窗需求 |
| **Form** | 没有表单需求，直接用 useState 管理输入 |
| **Tag** | 没有标签需求 |
| **Badge** | 没有角标需求 |
| **Empty** | 空状态自己写了欢迎页面 |
| **Skeleton** | 没有骨架屏需求 |

---

## 二、MainLayout（主布局）

**文件**：`src/layouts/MainLayout.tsx`

### 用了的组件

| 组件 | 位置 | 用途 | 为什么用 |
|------|------|------|---------|
| **Input** | L200 | 搜索城市 | 需要 Input.Search 组件，带搜索按钮 |
| **message** | L53, L72, L74, L134 | 全局提示 | 定位成功/失败、切换城市反馈 |
| **Popover** | L371 | 定位弹窗 | 需要点击弹出定位选项 |
| **Spin** | L170 | 定位中加载 | 需要加载状态提示 |

### 没用的组件

| 组件 | 为什么没用 |
|------|-----------|
| **Menu** | 导航栏用 div + 内联样式手写 |
| **Dropdown** | 用 Popover 代替 |
| **Avatar** | 没有头像需求 |

---

## 三、其他页面

### Login 页面

**文件**：`src/pages/Login/index.tsx`

| 组件 | 用途 |
|------|------|
| **Button** | 登录/注册按钮 |
| **Checkbox** | 记住我 |
| **Form** | 表单验证 |
| **Input** | 用户名/密码输入 |
| **message** | 登录成功/失败提示 |

### Home 页面

**文件**：`src/pages/Home/index.tsx`

| 组件 | 用途 |
|------|------|
| **Avatar** | 用户/AI 头像 |
| **Button** | 发送按钮 |
| **Input** | 消息输入框 |
| **message** | 全局提示 |
| **Modal** | 弹窗 |
| **Popconfirm** | 确认弹窗 |

### 其他页面

| 页面 | 用了的组件 |
|------|-----------|
| Movies | Empty, Input, Spin |
| Cinemas | Empty, Spin |
| CinemaDetail | Empty, message, Spin |
| MovieDetail | Empty, message, Spin |
| SeatSelection | message, Spin |
| Profile | Button, Empty, message, Modal, Spin, Tabs, Tag |
| Discover | Button, Spin, Empty, message, Tabs |
| Location | Spin, Empty, message, Input, Button, List |
| PayReturn | Button, Result, Spin |

---

## 四、组件使用统计

### 用了的组件（按使用频率）

| 组件 | 使用次数 | 使用页面 |
|------|---------|---------|
| **message** | 8 个页面 | Chat, MainLayout, Login, Home, MovieDetail, CinemaDetail, SeatSelection, Profile, Discover, Location |
| **Button** | 6 个页面 | Chat, Login, Home, Profile, Discover, Location, PayReturn |
| **Input** | 5 个页面 | Chat, MainLayout, Login, Home, Movies, Location |
| **Spin** | 7 个页面 | MainLayout, Movies, Cinemas, CinemaDetail, MovieDetail, SeatSelection, Profile, Discover, Location, PayReturn |
| **Empty** | 6 个页面 | Movies, Cinemas, CinemaDetail, MovieDetail, Profile, Discover, Location |
| **Avatar** | 2 个页面 | Chat, Home |
| **Modal** | 2 个页面 | Home, Profile |
| **Popover** | 1 个页面 | MainLayout |
| **Popconfirm** | 1 个页面 | Home |
| **Form** | 1 个页面 | Login |
| **Checkbox** | 1 个页面 | Login |
| **Tabs** | 2 个页面 | Profile, Discover |
| **Tag** | 2 个页面 | Profile, CinemaCard, MovieCard, SessionCard |
| **Card** | 3 个页面 | CinemaCard, MovieCard, SessionCard |
| **Rate** | 1 个页面 | MovieCard |
| **List** | 1 个页面 | Location |
| **Result** | 1 个页面 | PayReturn |

### 没用的组件

| 组件 | 为什么没用 |
|------|-----------|
| **Table** | 没有表格需求 |
| **Tree** | 没有树形结构需求 |
| **Select** | 没有下拉选择需求 |
| **DatePicker** | 没有日期选择需求 |
| **Upload** | 没有上传需求 |
| **Drawer** | 没有抽屉需求 |
| **Tooltip** | 没有悬停提示需求 |
| **Badge** | 没有角标需求 |
| **Skeleton** | 没有骨架屏需求 |
| **Progress** | 没有进度条需求 |
| **Steps** | 没有步骤条需求 |
| **Timeline** | 没有时间轴需求 |
| **Collapse** | 没有折叠面板需求 |
| **Carousel** | 没有轮播图需求 |
| **Calendar** | 没有日历需求 |

---

## 五、为什么 Chat 页面只用 4 个组件

### 原因

Chat 页面的 UI 比较轻量，主要是消息列表和输入框，不需要重型组件。

**用了的 4 个组件**：
- Avatar：区分用户/AI 头像
- Button：发送 + 复制
- Input：消息输入
- message：全局提示

**没用的重型组件**：
- Card：卡片用 div + 内联样式手写，更灵活
- List：消息列表用 div + map 循环渲染
- Spin：加载动画用 CSS 动画（三个跳动圆点）
- Modal：没有弹窗需求
- Form：没有表单需求

### 设计决策

**为什么用 div + 内联样式手写？**

1. **更灵活**：可以完全控制样式，不受组件限制
2. **减少包体积**：不引入重型组件，减少打包体积
3. **性能更好**：减少组件层级，提升渲染性能

**为什么用 CSS 动画而不是 Spin？**

1. **更轻量**：CSS 动画不需要引入组件
2. **更自然**：三个跳动圆点比 Spin 更像"正在输入"

---

## 六、总结

| 类别 | 组件 | 原因 |
|------|------|------|
| **高频使用** | message, Button, Input, Spin, Empty | 全局提示、按钮、输入框、加载、空状态是通用需求 |
| **低频使用** | Avatar, Modal, Popover, Form, Tabs, Tag, Card, Rate, List, Result | 特定页面需求 |
| **没用** | Table, Tree, Select, DatePicker, Upload, Drawer, Tooltip, Badge, Skeleton, Progress, Steps, Timeline, Collapse, Carousel, Calendar | 没有对应需求 |
| **Chat 页面手写** | Card, List, Spin, Modal, Form | 轻量 UI 用 div + 内联样式更灵活 |
