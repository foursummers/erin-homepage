# Erin_xyal · 个人作品集主页

> macOS 桌面风格的个人作品集主页，展示独立开发者的应用作品。

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-部署中-brightgreen)](https://erin-xyal.github.io)

## ✨ 特性

- **macOS Big Sur 风格**：毛玻璃效果、Dock 栏、菜单栏、圆角图标
- **完全静态**：纯 HTML/CSS/JS，零依赖，可直接部署到 GitHub Pages
- **手机端优化**：完美适配 375px 宽度，支持触摸交互
- **星空背景**：动态星星闪烁动画，深色宇宙风格
- **实时时钟**：菜单栏显示 `HH:mm 星期X` 格式
- **应用卡片**：单击显示详情弹窗，双击直接打开应用

## 🖥️ 预览

| 功能 | 描述 |
|------|------|
| 菜单栏 | 点击名字展开个人简介，右侧显示实时时间 |
| 应用图标 | 单击查看详情，双击直接打开链接 |
| Dock 栏 | 固定在底部，悬停时图标放大动画 |
| 应用卡片 | 展示描述、技术栈、打开/GitHub 按钮 |

## 🚀 部署到 GitHub Pages

### 方法一：直接上传

1. 将 `index.html` 上传到 GitHub 仓库根目录
2. 进入仓库 **Settings → Pages**
3. Source 选择 `Deploy from a branch`，Branch 选 `main`，目录选 `/ (root)`
4. 保存后等待约 1 分钟，访问 `https://<username>.github.io/<repo-name>`

### 方法二：使用 GitHub Actions 自动部署

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pages: write
      id-token: write
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - uses: actions/deploy-pages@v4
```

## 📁 项目结构

```
erin-homepage/
├── index.html        # 主页面（全部代码在此文件中）
├── README.md         # 项目说明
└── .github/
    └── workflows/
        └── deploy.yml  # GitHub Actions 自动部署
```

## 🎨 自定义

### 修改个人信息

在 `index.html` 中找到以下部分修改：

```html
<!-- 菜单栏名字 -->
<span class="menubar-name" id="menubar-name-btn">Erin_xyal</span>

<!-- 个人简介卡片 -->
<div class="about-name">Erin_xyal</div>
<div class="about-subtitle">独立开发者 · 产品设计师</div>
<p class="about-bio">热爱将东方哲学与现代技术融合...</p>
```

### 添加新应用

在 `<script>` 标签内的 `apps` 数组中添加：

```js
{
  id: "my-app",
  name: "我的应用",
  subtitle: "应用副标题",
  description: "应用详细描述...",
  techStack: ["React", "TypeScript"],
  icon: "🚀",                    // emoji 或图片 URL
  iconBg: "linear-gradient(135deg, #1a1a2e, #16213e)",
  link: "https://myapp.com",
  githubLink: "https://github.com/erin-xyal/my-app",
  status: "live",
  badge: "LIVE",                 // 可选：图标右上角徽章
}
```

### 修改 Dock 应用

```js
const dockApps = [apps[0], apps[1]]; // 将想要的应用加入 Dock
```

## 🛠️ 技术栈

- **纯 HTML/CSS/JS**：零框架依赖
- **Google Fonts**：Noto Sans SC + Noto Serif SC
- **CSS 动画**：`@keyframes` 实现星星闪烁、弹出动画
- **毛玻璃效果**：`backdrop-filter: blur()`

## 📄 License

MIT License © Erin_xyal
