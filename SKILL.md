---
name: quiet-tech-style
description: "静默科技风界面规范（科技感但成熟克制）。当用户要做技术博客首页、产品落地页、个人作品集、文档站首页，或提出「科技感」「克制」「高级感」「工业风」「单一强调色」「不要大红大紫」等设计要求时使用。提供九色令牌、字号阶、五条硬规则、组件规格与可直接粘贴的 prompt。"
version: 1.0.0
---

# 静默科技 · Quiet Tech Style

一套可执行的界面风格：**暗色只出现在首屏与页脚，强调色只有一个，分隔用发丝线而不是阴影。**

它的目标是让内容成为主角，不是让页面显得酷。任何装饰如果能删掉而不影响理解，就该删掉。

## 什么时候用

- 技术博客 / 文档站 / 作品集首页
- B 端工具、开发者产品的落地页
- 需要「专业、可信、不喧哗」气质的一页式介绍

**不要用在**：消费类营销页（缺情绪张力）、电商列表（信息密度不足）、儿童或娱乐产品（太冷）。

## 五条硬规则（违反即塌）

1. 只有一个强调色 `#2D6CDF`
2. 暗色只在首屏与页脚，正文区必须浅底
3. 用 1px 发丝线分隔，不用阴影
4. 等宽字体只做标记（编号/标签/数字），正文用无衬线
5. 圆角不超过 2px

## 怎么用

**方式一：直接拿代码**

```bash
cp tokens.css theme.css 你的项目/
```

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
  <div class="qt-scroll">Scroll to explore</div>
</header>
```

组件类名统一 `qt-` 前缀：`qt-hero` / `qt-stats` / `qt-sec` / `qt-head` / `qt-cards` / `qt-card` / `qt-list` / `qt-item` / `qt-about` / `qt-facts` / `qt-foot` / `qt-prose`。

**方式二：让模型照 prompt 生成**

把 `prompt.md` 整段复制给模型，替换末尾 `{{}}` 占位符。

**方式三：换个强调色**

只改 `tokens.css` 里的 `--qt-accent` 与 `--qt-accent-hover`。备选：深青 `#0E7490`（更冷、更像仪器）、石墨紫 `#5B5BD6`（更强 AI 感，易过时）、暖琥珀 `#B45309`（最克制，但科技感弱）。

## 落地顺序

1. 引入 `tokens.css`，先把色与字号定死
2. 搭 `.qt-hero`（主标题 / 副文 / 按钮 / 数字条 / 滚动提示）
3. 写 2–3 个 `.qt-sec`，先放占位内容
4. 填卡片与列表，内容进来后再调间距
5. 最后接 `.qt-reveal` 动效
6. 过一遍自检清单

## 两个必须守的实现细节

**动效要渐进增强。** 把 `opacity:0` 挂在 `.qt-ready` 下（该类由 JS 添加），脚本失效时内容照常可见。否则一次 JS 报错就是永久白屏。

**不要用锚点做路由跳转**（在 Docsify、Vue Router、hash 路由的站点上）：`href="#section"` 会被当成路由解析，导致 404。页内导航应指向真实路径或使用滚动 API。

## 参考文件

| 文件 | 内容 |
|---|---|
| `STYLEGUIDE.md` | 完整规范：色板、字号阶、组件规格、做与不做、已知边界 |
| `prompt.md` | 可直接粘贴给模型的生成指令 |
| `tokens.css` | 变量层，可单独引入做配色基线 |
| `theme.css` | 组件层，类名 `qt-*` |
| `demo.html` | 单文件演示，打开即看效果 |

## 已知边界

- 信息密度比列表式布局低约 30%，不适合数据看板
- 依赖系统字体栈，Linux 上字重观感偏轻
- 暗色首屏不适合打印
- 单一强调色意味着语义单一：需要区分错误/成功/警告时，必须另设压饱和的语义色
