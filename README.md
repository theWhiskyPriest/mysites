# 我的个人小站

基于 [Hugo](https://gohugo.io/) 的静态个人网站，含两类内容：

- **说说**（`content/notes/`）：每天几句话，首页时间线展示
- **长文**（`content/posts/`）：正式文章，在 `/posts` 列表展示

## 日常写作

在本站目录下运行（`hugo` 已装在 `~/.local/bin`，新终端可直接用）：

```bash
# 写一条说说（文件名随意，用日期或关键词都行）
hugo new notes/2026-07-24.md

# 写一篇长文
hugo new posts/我的标题.md
```

编辑生成的 Markdown 文件写内容。写完发布：

```bash
git add -A
git commit -m "更新"
git push
```

push 后 GitHub Actions 会自动构建并部署，约 1 分钟后网站更新。

## 本地预览

```bash
hugo server -D
```

浏览器打开 http://localhost:1313 实时预览（改文件自动刷新）。

## 隐私说明

- 全站输出 `noindex` 标签 + `robots.txt` 屏蔽爬虫，搜索引擎不收录。
- **但网站本身仍是公开的**：任何人拿到网址都能访问。这不是真正的"仅自己可见"。真正私密的内容请勿放在这里。
- 相关开关在 `hugo.yaml` 的 `params.noindex`。

## 部署到 GitHub Pages

1. 在 GitHub 新建一个**私有**仓库。
2. 把本目录推上去：
   ```bash
   git remote add origin git@github.com:USERNAME/REPO.git
   git branch -M main
   git push -u origin main
   ```
3. 仓库 Settings → Pages → Build and deployment → Source 选 **GitHub Actions**。
4. 等 Actions 跑完，Pages 会给出网址。

> baseURL 由 Actions 自动注入，`hugo.yaml` 里的 `USERNAME` 只影响本地构建，可不改。

## 目录结构

```
content/notes/    说说
content/posts/    长文
layouts/          页面模板（想改样式改这里）
static/css/       样式表
static/robots.txt 爬虫屏蔽
hugo.yaml         全站配置
.github/workflows/deploy.yml  自动部署
```
