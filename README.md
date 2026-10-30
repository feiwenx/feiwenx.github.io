# Feiwen Xiao 个人网站

纯静态网站，不需要安装任何依赖，任何能放静态文件的地方都能部署。

## 文件说明

- `index.html`：首页（About、News、Publications、Education）
- `research.html`：研究页
- `styles.css`：两个页面共用的样式，颜色和字体都集中写在文件最上面
- `assets/`：图片，以后的 CV PDF 也放这里

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
3. 在新仓库页面点 **uploading an existing file**，把本文件夹里的全部内容拖进去（`index.html`、`research.html`、`styles.css`、`README.md` 和整个 `assets` 文件夹），点 **Commit changes**。注意拖的是文件夹里面的东西，不要把外层文件夹本身拖进去。
4. 进入仓库的 **Settings** → **Pages**，在 **Build and deployment** 下：Source 选 **Deploy from a branch**，Branch 选 **main**，文件夹选 **/(root)**，点 **Save**。
5. 等一两分钟后刷新 Pages 设置页，页面顶部会显示网址。仓库名是 `feiwenx.github.io` 时，网址就是 https://feiwenx.github.io 。

如果仓库用别的名字（比如 `website`），网址会是 `https://feiwenx.github.io/website/`。

## 以后怎么改内容

- **在 GitHub 网页上改（最简单）**：在仓库里打开要改的文件，点右上角的铅笔图标，改完点 **Commit changes**。一两分钟后网站自动更新。
- **在电脑上改**：用 VS Code 等编辑器打开这个文件夹，改完按上面的方法本地预览，再用 GitHub Desktop 或 git 推送到仓库。
- **待补内容**：所有占位内容都写在方括号里，比如 `[Paper title]`、`[Year]`，在文件里搜索 `[` 就能找到。写着 `TODO` 的注释是需要替换的链接。

## 常见修改

- **加一条新闻或一篇论文**：复制 `index.html` 里对应的一整段 `<li> … </li>`，粘贴到列表最上面，改日期和文字。
- **换研究页的项目图片**：把照片（4:3，约 1200 × 900 像素）上传到 `assets` 文件夹，再把 `research.html` 里对应的 `src="assets/project-placeholder.png"` 改成新文件名，`alt` 也改成对图片的简短描述。
- **放 CV**：把 PDF 上传到 `assets`（例如 `assets/cv.pdf`），再把 `index.html` 里 CV 按钮和 `[Download CV]` 的 `href="#"` 改成 `assets/cv.pdf`。
- **换头像**：用同名文件覆盖 `assets/portrait-photo.jpg`。
- **置顶公告**：改 `index.html` 里 `class="note"` 那段文字；不需要的话把整个 `<div class="note">…</div>` 删掉。
- **公告框改成黄色**：在 `styles.css` 最上面把 `--callout-bg` 改成 `#fcecab`，`--callout-border` 改成 `#e2bd3c`。
- **换主色**：改 `styles.css` 最上面的 `--accent` 和 `--accent-text`。
- **去掉顶部的浅点阵**：删掉两个页面里的 `<div class="dots" aria-hidden="true"></div>`。
- **鼠标悬停时的浅色渐变**：带 `class="zone"` 的区块会在鼠标移上去时从窗口边缘泛出很浅的颜色。`zone` 是从左边泛蓝，`zone-right` 是从右边泛蓝，`zone-warm` 是从右边泛暖黄。颜色在 `styles.css` 最上面的 `--glow-blue` 和 `--glow-warm` 里改；想整体关掉，删掉 `styles.css` 里 `.zone:hover::before` 那一条。
- **更新日期**：改两个页面底部的 `Last updated`。

## 绑定自己的域名（可选）

在仓库 **Settings** → **Pages** → **Custom domain** 填入域名，再按 GitHub 给出的提示到域名服务商那里添加 DNS 记录。
