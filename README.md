# 静默科技 · Quiet Tech Style

> 一套「有科技感但成熟克制」的界面规范：暗色只在首屏，强调色只有一个，分隔用发丝线不用阴影。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

这不是一套主题皮肤，是一套**带理由的约束**。每条规则都写清了"为什么"，因为风格会被模仿，理由才会被复用。

## 快速开始

```bash
git clone https://github.com/CommitByRyan/quiet-tech-style.git
open quiet-tech-style/index.html     # 直接看效果
```

把 `tokens.css` 与 `theme.css` 拷进你的项目：

```html
<link rel="stylesheet" href="tokens.css">
<link rel="stylesheet" href="theme.css">

<header class="qt-hero">
  <div class="qt-eyebrow">Product · 2026</div>
  <h1>把复杂的事<br>讲得干净<em>。</em></h1>
  <p class="qt-lead">一句话说清这是什么、给谁用。</p>
  <nav class="qt-nav">
    <a class="is-primary" href="#">开始使用 →</a>
    <a href="#">文档</a>
  </nav>
  <div class="qt-stats">
    <div><b>01</b><span>强调色</span></div>
    <div><b>2px</b><span>圆角上限</span></div>
  </div>
</header>
```

## 五条硬规则

| # | 规则 | 为什么 |
|---|---|---|
| 1 | 只有一个强调色 `#2D6CDF` | 第二种彩色一出现，读者就无法判断什么最重要 |
| 2 | 暗色只在首屏与页脚 | 长文黑底阅读疲劳，截图也不好看 |
| 3 | 1px 发丝线分隔，不用阴影 | 阴影制造"浮起"错觉，与克制的语气冲突 |
| 4 | 等宽字体只做标记 | 等宽是仪器刻度，不是正文语体 |
| 5 | 圆角不超过 2px | 大圆角=柔和亲切，与"精确"的定位相反 |

## 文件

| 文件 | 内容 |
|---|---|
| [`STYLEGUIDE.md`](STYLEGUIDE.md) | 完整规范：色板、字号阶、间距、组件规格、动效、无障碍、做与不做、已知边界 |
| [`prompt.md`](prompt.md) | 可直接粘贴给 AI 的生成指令，替换 `{{}}` 占位符即可 |
| [`SKILL.md`](SKILL.md) | 技能包形态（WorkBuddy / Agent Skill），放入技能目录即可自动触发 |
| [`tokens.css`](tokens.css) | 变量层：九色、字号阶、间距、动效曲线 |
| [`theme.css`](theme.css) | 组件层：首屏、数字条、版块、卡片、列表、两栏、页脚、长文 |
| [`index.html`](index.html) | 单文件演示，含全部组件与滚动入场；已开启 Pages 在线预览 |

## 设计令牌

```
墨   #0B0B0C     纸   #FFFFFF     强调 #2D6CDF
墨2  #14161A     纸2  #F5F6F7     悬停 #1F55B8
标题 #111318     正文 #3F444C     辅助 #8A9099
```

字距方向相反的两次调整，是这套排版"精密感"的来源：

- 大标题 `-0.02em`（收紧）
- 等宽标签 `+0.22em`（拉开）

## 组件

| 类名 | 用途 |
|---|---|
| `.qt-hero` | 首屏：点阵纹理 + 一处光晕 + 大标题 + 数字条 + 滚动提示 |
| `.qt-eyebrow` | 眉标：等宽大写 + 28px 强调色短线 |
| `.qt-nav` | 按钮组：一个 `is-primary`，其余描边 |
| `.qt-stats` | 数字条：`gap:1px` 造分割线 |
| `.qt-sec` | 版块：`is-alt` 交替底色，`is-dark` 反转 |
| `.qt-head` | 版块头：编号 + 标题 + 右侧说明，基线对齐 |
| `.qt-card` | 卡片：等宽小标 + 标题 + 说明 + 底部元信息 |
| `.qt-item` | 列表行：编号 + 标题 + 箭头 |
| `.qt-about` / `.qt-facts` | 两栏：左论述 / 右事实表 |
| `.qt-prose` | 长文排版：行高 1.85，链接去下划线 |

## 换强调色

只改一个变量：

```css
:root { --qt-accent: #0E7490; --qt-accent-hover: #0B5C73; }
```

| 备选 | 色值 | 气质 | 风险 |
|---|---|---|---|
| 靛蓝（默认） | `#2D6CDF` | 中性、清晰 | 略"企业感" |
| 深青 | `#0E7490` | 更冷、更像仪器 | 与绿色高亮易糊 |
| 石墨紫 | `#5B5BD6` | AI / 未来感 | 三五年易显旧 |
| 暖琥珀 | `#B45309` | 最克制、最易读 | 科技感最弱 |

## 两个必须守的实现细节

**动效渐进增强。** `opacity: 0` 必须挂在由 JS 添加的 `.qt-ready` 之下。否则一次脚本报错，整页就是永久白屏——动效退化为"没有动画"，绝不能退化为"没有内容"。

**不要在 hash 路由站点上用页内锚点。** `href="#section"` 在 Docsify / Vue Router 下会被当作路由解析导致 404，应指向真实路径或改用滚动 API。

## 适用与不适用

**适用**：技术博客、文档站、作品集、开发者产品落地页。

**不适用**：消费类营销页（缺情绪张力）、电商列表（密度不足）、儿童与娱乐产品（太冷）、需要打印的文档（暗色首屏不友好）。

## License

MIT © 2026 Ryan
