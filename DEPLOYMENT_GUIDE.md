# 🚀 发布到 HighTorque-Robotics GitHub Pages

本文档说明如何将 `mini-pi-soccer-docs` 发布到 **HighTorque-Robotics** 组织下的 GitHub Pages，并对外提供统一访问地址：

<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>

## 📋 发布前准备

### 1. 必备权限

你需要具备以下 GitHub 权限：

- 可访问 `HighTorque-Robotics` 组织
- 可在组织下创建或维护 `mini-pi-soccer-docs` 仓库
- 可启用 GitHub Actions 与 GitHub Pages
- 可上传 Release 附件（如 SDK、策略文件）

### 2. 本地环境

- Node.js 20+
- npm
- git

## 🎯 首次发布步骤

### 步骤 1：准备组织仓库

优先在 GitHub 上使用同名仓库：

- 组织：`HighTorque-Robotics`
- 仓库：`mini-pi-soccer-docs`

推荐仓库地址：

```text
git@github.com:HighTorque-Robotics/mini-pi-soccer-docs.git
```

如果当前仓库还在个人账号下，可选择：

1. **转移仓库** 到组织名下；或
2. **在组织下新建仓库**，再把当前代码推送过去。

### 步骤 2：确认默认分支与工作流一致

本仓库使用 GitHub Actions 自动构建 Pages。

请确认：

- GitHub 仓库默认分支名称
- `.github/workflows/deploy.yml` 中 `on.push.branches` 的配置

如果默认分支是 `main`，需要把工作流触发分支改为 `main`；如果仍使用 `master`，则保持一致即可。

### 步骤 3：迁移 Release 资源

在切换正式下载链接前，先把原先依赖的发布附件上传到组织仓库对应的 Release（当前文档默认使用标签 `v1.0.0`）：

- `sim2real_master-feature-master_and_slave_orin_wuandhou.tar.gz`
- `pi_plus_autostart.zip`
- `football_strategy_files.tar.gz`

如果这些附件不存在，新站虽然可以打开，但下载按钮会失效。

### 步骤 4：安装依赖并本地构建

```bash
cd mini-pi-soccer-docs
npm install
npm run docs:build
```

构建成功后，可本地预览：

```bash
npm run docs:preview
```

## 🔄 推送与自动部署

### 1. 添加或更新远程仓库

如果当前仓库尚未指向组织仓库：

```bash
git remote set-url origin git@github.com:HighTorque-Robotics/mini-pi-soccer-docs.git
```

### 2. 提交变更

```bash
git add .
git commit -m "docs: migrate site to HighTorque-Robotics pages"
```

### 3. 推送到默认分支

```bash
git push origin HEAD
```

### 4. 查看部署状态

GitHub Actions 页面：

<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

如果构建与部署成功，GitHub Pages 会自动更新。

## 🌐 启用 GitHub Pages

在 GitHub 仓库设置中：

1. 打开 **Settings → Pages**
2. Source 选择 **GitHub Actions**
3. 保存设置

首次部署完成后，Pages 地址通常为：

<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>

## ✅ 发布后验收

发布完成后，至少检查以下内容：

1. 首页是否正常打开
2. 中文与英文页面是否都能访问
3. 下载按钮是否正常：
   - SDK 安装包
   - 自启动脚本
   - 足球策略文件
   - URDF 模型文件
4. 页脚 GitHub 链接是否指向组织仓库
5. 页面内容中是否还残留旧的个人仓库、旧 Pages 或 Vercel 链接

## 🐛 常见问题

### 工作流没有触发

常见原因：

- 推送的不是工作流监听的分支
- 组织仓库未启用 GitHub Actions
- Pages Source 不是 GitHub Actions

请先检查：

- `.github/workflows/deploy.yml`
- GitHub 仓库默认分支
- `Settings → Pages`

### 页面资源 404 / 样式丢失

通常是 `docs/.vitepress/config.mjs` 中的 `base` 与最终仓库路径不匹配。

当前若仓库名保持为 `mini-pi-soccer-docs`，则应使用：

```js
base: '/mini-pi-soccer-docs/'
```

### 下载链接失效

请确认组织仓库中对应 Release 的标签和附件已经上传完成。

### 本地构建失败

先清理缓存再重建：

```bash
rm -rf docs/.vitepress/cache docs/.vitepress/dist
npm install
npm run docs:build
```

## 📌 维护建议

- 将 GitHub Pages 作为唯一正式公网入口
- 避免继续在文档中保留旧 Vercel 公网地址
- 新增下载资源时，优先走 GitHub Release，并在文档中统一使用组织仓库链接
- 每次改动后都先本地构建，再推送上线

---

**发布完成后请以 GitHub Pages 新地址为准对外分享。**
