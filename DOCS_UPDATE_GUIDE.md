# 📝 Mini Pi+ 文档更新指南

本指南说明如何在 `mini-pi-soccer-docs` 仓库中维护文档，并通过 **HighTorque-Robotics** 组织下的 GitHub Pages 自动发布。

- 站点地址：<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>
- 仓库地址：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs>
- Actions：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

## 🚀 本地开发

### 启动文档站

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
npm install
npm run docs:dev
```

默认访问：<http://localhost:5173>

### 可选：启动上传服务

```bash
npm run server:dev
```

## 📂 目录说明

```text
mini-pi-soccer-docs/
├── docs/
│   ├── .vitepress/               # VitePress 配置
│   ├── guide/                    # 中文开发指南
│   ├── soccer/                   # 中文足球应用文档
│   ├── tutorials/                # 中文教程
│   ├── en/                       # 英文文档
│   └── public/                   # 静态资源和下载文件
├── server/                       # 本地上传服务（可选）
├── .github/workflows/            # GitHub Actions 工作流
├── README.md
├── DEPLOYMENT_GUIDE.md
└── UPLOAD_GUIDE.md
```

## ✍️ 如何新增或修改文档

### 1. 编辑 Markdown 文件

例如新增一篇开发指南：

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs/docs/guide
nano new-guide.md
```

文档内容示例：

```markdown
# 文档标题

这是文档内容。

## 二级标题

```python
def hello():
    print("Hello Mini Pi+")
```
```

### 2. 更新导航或侧边栏

如果希望新文档出现在站点导航中，编辑：

```bash
nano /home/sunteng/开源工作空间/mini-pi-soccer-docs/docs/.vitepress/config.mjs
```

示例：

```js
sidebar: {
  '/guide/': [
    {
      text: '⚡ 快速开始',
      items: [
        { text: '简介', link: '/guide/' },
        { text: '新文档', link: '/guide/new-guide' }
      ]
    }
  ]
}
```

### 3. 添加图片、视频和下载资源

将资源文件放到 `docs/public/` 下：

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
cp /path/to/image.png docs/public/images/
cp /path/to/demo.mp4 docs/public/videos/
```

Markdown 中的引用示例：

```markdown
![图片描述](/mini-pi-soccer-docs/images/image.png)
```

HTML 视频示例：

```html
<video controls width="100%">
  <source src="/mini-pi-soccer-docs/videos/demo.mp4" type="video/mp4">
</video>
```

> 如果未来仓库名变化，需要同步检查 `docs/.vitepress/config.mjs` 中的 `base` 配置以及所有带 `/mini-pi-soccer-docs/` 前缀的静态资源路径。

## 🧪 提交前检查

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
npm run docs:build
npm run docs:preview
```

建议检查：

- 首页、中英文导航是否正常
- 新文档是否可访问
- 图片、视频和下载文件是否能打开
- 页脚 GitHub 链接是否正确

## 🚀 发布流程

本项目使用 GitHub Actions 自动发布到 GitHub Pages。

### 提交与推送

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
git add .
git commit -m "docs: update content"
git push origin HEAD
```

### 查看构建与部署状态

<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

### 正式发布地址

<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>

## 📦 关于下载资源

SDK、策略文件等下载链接当前使用 GitHub Release：

- 仓库：`HighTorque-Robotics/mini-pi-soccer-docs`
- 标签：`v1.0.0`

如果新增或替换附件，请先上传到对应 Release，再更新文档中的下载按钮链接。

## 🔧 常见问题

### 页面样式异常或资源 404

通常是以下问题导致：

1. `docs/.vitepress/config.mjs` 中的 `base` 配置不正确
2. 静态资源路径缺少 `/mini-pi-soccer-docs/` 前缀
3. GitHub Pages 还未完成最新部署

### 推送后页面没有更新

请检查：

1. 是否已推送到默认分支
2. GitHub Actions 是否构建成功
3. GitHub Pages 是否设置为 **GitHub Actions** 作为发布源

### 下载链接失效

请确认：

1. Release 标签存在
2. 附件已经上传到组织仓库
3. 文档中的下载 URL 指向 `HighTorque-Robotics/mini-pi-soccer-docs`

## 📞 获取帮助

- 提交 Issue：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/issues>
- 查看部署日志：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

---

**建议所有文档维护与对外分享都统一使用组织仓库和 GitHub Pages 新地址。**
