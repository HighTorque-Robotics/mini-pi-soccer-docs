# 📤 文档上传与维护说明

本文档用于说明如何在 `mini-pi-soccer-docs` 中新增、修改并发布文档内容。

正式站点与仓库：

- 站点：<https://hightorque-robotics.github.io/mini-pi-soccer-docs/>
- 仓库：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs>
- Actions：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

## 🎯 常见维护流程

### 方式 1：直接编辑 Markdown（推荐）

1. 在 `docs/` 下找到对应目录，例如：
   - `docs/guide/`
   - `docs/soccer/`
   - `docs/tutorials/`
   - `docs/en/`
2. 新增或修改 Markdown 文件
3. 如需出现在导航/侧边栏中，更新 `docs/.vitepress/config.mjs`
4. 本地预览确认
5. 提交并推送到 GitHub

示例：新增教程 `basic-kick.md`

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs

cat > docs/tutorials/basic-kick.md <<'EOF'
# 基础踢球动作

## 学习目标

- 学会机器人基础踢球动作
- 理解动作调用与参数控制
EOF

git add docs/tutorials/basic-kick.md
git commit -m "docs: add basic kick tutorial"
git push origin HEAD
```

发布后访问：

<https://hightorque-robotics.github.io/mini-pi-soccer-docs/tutorials/basic-kick>

### 方式 2：添加图片或视频资源

将资源复制到 `docs/public/` 下，再在文档中引用。

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
cp /path/to/image.png docs/public/
git add docs/public/image.png
git commit -m "docs: add image asset"
git push origin HEAD
```

Markdown 引用示例：

```markdown
![图片描述](/image.png)
```

视频示例：

```html
<video controls width="100%">
  <source src="/demo.mp4" type="video/mp4">
</video>
```

### 方式 3：修改导航或侧边栏

编辑：

```bash
nano /home/sunteng/开源工作空间/mini-pi-soccer-docs/docs/.vitepress/config.mjs
```

推送后 GitHub Actions 会自动发布。

## 🧪 发布前建议检查

每次推送前建议先本地确认：

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
npm install
npm run docs:build
npm run docs:preview
```

检查内容：

- 页面是否能正常打开
- 中英文导航是否正确
- 图片、视频、下载资源是否能访问
- 新增页面是否已出现在导航中

## 🔧 常用 Git 命令

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs

git status
git add .
git commit -m "docs: describe your change"
git push origin HEAD
git log --oneline -5
```

## ❓常见问题

### Q: 推送后多久能看到更新？
A: 通常 1-3 分钟。可在 Actions 页面查看构建和部署状态：

<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/actions>

### Q: 页面没有更新怎么办？
A: 先检查：

1. 是否已成功推送到默认分支
2. GitHub Actions 是否执行成功
3. `docs/.vitepress/config.mjs` 中链接与路径是否正确
4. GitHub Pages 是否仍设置为 **GitHub Actions**

### Q: 如何删除文档？
A: 直接删除对应 Markdown 文件并提交：

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
rm docs/tutorials/unwanted-file.md
git add .
git commit -m "docs: remove unwanted tutorial"
git push origin HEAD
```

### Q: 如何修改已有文档？
A: 直接编辑文件后提交：

```bash
cd /home/sunteng/开源工作空间/mini-pi-soccer-docs
nano docs/tutorials/basic-motion.md
git add .
git commit -m "docs: update basic motion tutorial"
git push origin HEAD
```

## 📞 需要帮助？

如果遇到问题：

1. 查看 GitHub Actions 日志
2. 检查文件路径和链接是否正确
3. 在仓库中提交 Issue：<https://github.com/HighTorque-Robotics/mini-pi-soccer-docs/issues>

---

**建议始终以 GitHub Pages 新站地址作为对外分享链接。**
