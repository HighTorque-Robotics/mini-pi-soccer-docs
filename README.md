# ⚽ Mini Pi+ 足球机器人开发文档

基于 VitePress 构建的 Mini Pi+ 机器人足球应用开发文档网站，当前正式发布目标为 **HighTorque-Robotics 组织下的 GitHub Pages**。

- 正式站点：<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>
- 仓库地址：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs>

## ✨ 特性

- ⚽ **足球绿茵科技风格** - 专业的足球主题设计，绿色渐变配色
- 📚 **完整的开发文档** - 从入门到进阶的完整教程体系
- 🔍 **全文搜索功能** - 快速查找所需内容
- 💻 **代码语法高亮** - 支持多种编程语言
- 🌙 **深色模式支持** - 护眼的暗色主题
- 📱 **响应式设计** - 完美适配各种设备
- 🚀 **GitHub Pages 自动发布** - 推送后自动构建并上线

## 🚀 快速开始

### 前置要求

- Node.js 20+（推荐）
- npm

### 安装依赖

```bash
cd mini-pi-soccer-docs
npm install
```

### 启动开发服务器

```bash
# 启动文档网站（端口 5173）
npm run docs:dev

# 启动上传服务器（端口 3001，可选）
npm run server:dev
```

访问：
- 📚 文档网站：<http://localhost:5173>
- 📤 上传 API：<http://localhost:3001>

### 构建生产版本

```bash
npm run docs:build
```

构建产物位于 `docs/.vitepress/dist`。

### 预览生产版本

```bash
npm run docs:preview
```

## 🌐 发布方式

本项目当前以 **GitHub Pages** 作为正式公网入口。

### 自动发布

仓库默认通过 GitHub Actions 构建并发布到：

<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>

每次向默认分支推送更新后，GitHub Actions 会自动重新构建站点并部署到 GitHub Pages。

详细步骤见 [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)。

## 📁 项目结构

```text
mini-pi-soccer-docs/
├── docs/                          # 文档内容
│   ├── .vitepress/               # VitePress 配置
│   │   ├── config.mjs            # 网站配置（导航、侧边栏、搜索）
│   │   └── theme/                # 自定义主题
│   │       ├── index.js          # 主题入口
│   │       └── custom.css        # 足球绿茵风格样式
│   ├── guide/                    # 开发指南文档
│   ├── soccer/                   # 足球应用文档
│   ├── tutorials/                # 教程文档
│   ├── en/                       # 英文文档
│   └── public/                   # 静态资源（图片、下载文件等）
├── server/                       # 上传服务器（可选）
├── .github/workflows/            # GitHub Actions 工作流
├── DOCS_UPDATE_GUIDE.md          # 文档维护指南
├── DEPLOYMENT_GUIDE.md           # GitHub Pages 发布指南
├── UPLOAD_GUIDE.md               # 文档上传与维护说明
├── vercel.json                   # 旧 Vercel 配置（仅保留兼容）
└── package.json
```

## 📝 更新文档

详细维护说明见 [DOCS_UPDATE_GUIDE.md](./DOCS_UPDATE_GUIDE.md)。

常见更新流程：

1. 编辑 `docs/` 下对应的 Markdown 文件
2. 如有需要，更新 `docs/.vitepress/config.mjs` 中的导航和侧边栏
3. 本地预览确认无误
4. 提交并推送到 GitHub

```bash
git add .
git commit -m "docs: update site content"
git push origin HEAD
```

推送后可在 GitHub Actions 查看部署日志：

<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

## 🎨 主题样式

主题样式文件：`docs/.vitepress/theme/custom.css`

```css
:root {
  --vp-c-brand: #10b981;
  --vp-c-brand-light: #34d399;
  --vp-c-brand-dark: #059669;
}
```

## 🔧 技术栈

- **VitePress** - 静态文档站点生成器
- **Vue 3** - 前端运行时
- **Express** - 可选的本地上传服务
- **GitHub Pages** - 正式公网托管
- **GitHub Actions** - 自动构建与部署

## 📚 相关文档

- 📖 [文档更新指南](./DOCS_UPDATE_GUIDE.md)
- 🚀 [部署指南](./DEPLOYMENT_GUIDE.md)
- 📤 [上传说明](./UPLOAD_GUIDE.md)
- 🎨 主题样式：`docs/.vitepress/theme/custom.css`
- ⚙️ 网站配置：`docs/.vitepress/config.mjs`

## 🎯 常用命令

```bash
# 开发
npm run docs:dev
npm run server:dev

# 构建
npm run docs:build
npm run docs:preview

# Git 发布
git add .
git commit -m "docs: update content"
git push origin HEAD
```

## 🐛 故障排除

### Node 版本问题

```bash
node -v
```

如版本不是 20+，请切换到较新的 Node.js 版本后再执行 `npm install`。

### 页面资源或样式异常

```bash
rm -rf docs/.vitepress/cache
rm -rf docs/.vitepress/dist
npm run docs:build
```

### 查看部署状态

前往 GitHub Actions：

<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

## 🤝 贡献

欢迎通过 Issue 或 Pull Request 共同维护文档：

<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs>

---

**需要帮助？** 请优先查看站内文档或在仓库中提交 Issue。
