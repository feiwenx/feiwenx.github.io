# Feiwen Xiao 个人网站

© 2026 Feiwen Xiao. All rights reserved. Content and photos may not be reused without permission.

纯静态网站，不需要安装任何依赖，任何能放静态文件的地方都能部署。

## 文件说明

- `index.html`：首页（About、News、Recent Publications、Education）
- `research.html`：研究页，列出所有项目，每个项目有图片和一段简介
- `projects/`：每个项目的详情页（简介、Highlights、Findings、Selected Publications）
- `styles.css`：所有页面共用的样式，颜色和字体都集中写在文件最上面
- `assets/`：头像等图片；`assets/projects/` 放项目配图

## 本地预览

直接双击 `index.html`，用浏览器打开即可。

也可以在这个文件夹里运行：

```bash
python3 -m http.server 8080
```

然后在浏览器打开 http://localhost:8080 。

## 部署到 GitHub Pages（免费，全程在网页上操作）

1. 用 Feiwen 的 GitHub 账号（feiwenx）登录，点右上角 **+** → **New repository**。
2. Repository name 填 `feiwenx.github.io`，选 **Public**，点 **Create repository**。仓库名要用 `.github.io` 结尾，不要用 `.github.com`：GitHub 从 2013 年起就把个人网站统一放在 github.io 域名下，github.com 形式的地址只会被跳转到 github.io。
3. 在新仓库页面点 **uploading an existing file**，把本文件夹里的全部内容拖进去（`index.html`、`research.html`、`styles.css`、`README.md`，以及整个 `assets` 和 `projects` 文件夹），点 **Commit changes**。注意拖的是文件夹里面的东西，不要把外层文件夹本身拖进去。
4. 进入仓库的 **Settings** → **Pages**，在 **Build and deployment** 下：Source 选 **Deploy from a branch**，Branch 选 **main**，文件夹选 **/(root)**，点 **Save**。
5. 等一两分钟后刷新 Pages 设置页，页面顶部会显示网址。仓库名是 `feiwenx.github.io` 时，网址就是 https://feiwenx.github.io 。

如果仓库用别的名字（比如 `website`），网址会是 `https://feiwenx.github.io/website/`。

## 以后怎么改内容

- **在 GitHub 网页上改（最简单）**：在仓库里打开要改的文件，点右上角的铅笔图标，改完点 **Commit changes**。一两分钟后网站自动更新。
- **在电脑上改**：用 VS Code 等编辑器打开这个文件夹，改完按上面的方法本地预览，再用 GitHub Desktop 或 git 推送到仓库。
- **待补内容**：写着 `TODO` 的注释是还需要替换的内容（目前是 LinkedIn 链接）。

## 常见修改

- **加一条新闻或一篇论文**：复制 `index.html` 里对应的一整段 `<li> … </li>`，粘贴到列表最上面，改日期和文字。首页 News 保持 5 条左右、Recent Publications 保持 4–5 篇，加新的时把最旧的一条删掉。
- **换项目图片**：现在的项目配图是 `assets/projects/` 里的插画（`.svg`）。换成照片时，把照片（4:3，约 1200 × 900 像素）上传到 `assets/projects/`，再把 `research.html` 和 `projects/` 里对应页面中的图片路径改成新文件名（两处都要改），详情页里的 `alt` 也改成对图片的简短描述。
- **改项目内容**：直接编辑 `projects/` 里对应的页面。Highlights 和 Findings 每条是一个 `<li> … </li>`，Selected Publications 的格式和首页论文列表一样。
- **加一个项目**：复制 `projects/` 里任意一个页面改名、改内容；在 `research.html` 里复制一整段 `<article> … </article>`，改链接、图片和简介；最后更新相邻项目页面底部的 Previous / Next 链接。
- **Email 按钮**：点了会把邮箱地址复制到剪贴板，并在页面底部提示 "Email copied"，不依赖访客电脑上有没有设置邮件程序。要换邮箱，改 `index.html` 里 Email 按钮的 `data-copy-email` 和 `href`，以及置顶公告里的地址。
- **换头像**：用同名文件覆盖 `assets/portrait-photo.jpg`。
- **置顶公告**：改 `index.html` 里 `class="note"` 那段文字；不需要的话把整个 `<div class="note">…</div>` 删掉。
- **公告框改成黄色**：在 `styles.css` 最上面把 `--callout-bg` 改成 `#fcecab`，`--callout-border` 改成 `#e2bd3c`。
- **换主色**：改 `styles.css` 最上面的 `--accent` 和 `--accent-text`。
- **去掉顶部的浅点阵**：删掉每个页面里的 `<div class="dots" aria-hidden="true"></div>`。
- **鼠标悬停时的浅色渐变**：带 `class="zone"` 的区块会在鼠标移上去时从窗口边缘泛出很浅的颜色。`zone` 是从左边泛蓝，`zone-right` 和 `zone-warm` 是从右边泛暖黄；相邻区块交替用 `zone` 和 `zone-right`，所以蓝色和黄色会轮流出现。颜色在 `styles.css` 最上面的 `--glow-blue` 和 `--glow-warm` 里改；想整体关掉，删掉 `styles.css` 里 `.zone:hover::before` 那一条。
- **更新日期**：改每个页面底部的 `Last updated`，项目页还有一行 `Updated`。

## 绑定自己的域名（可选）

在仓库 **Settings** → **Pages** → **Custom domain** 填入域名，再按 GitHub 给出的提示到域名服务商那里添加 DNS 记录。
