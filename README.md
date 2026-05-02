# znecho9.github.io

这是 [znecho9.github.io](https://znecho9.github.io/) 的源码仓库。网站使用 Jekyll + Bootstrap 构建，视觉结构已经按 Kyle Fogarty 个人主页源码重写：固定顶部导航、黄色 hero、PT Sans / PT Serif 字体、卡片式 publications 和 blog 列表、右侧 news/sidebar。

主题代码来自下载的参考源码并保留在仓库内，授权信息见 `LICENSE.txt`。个人内容、图片和导航已经替换为 Zinan Lin 的网站信息。

## 文件结构

最常改的文件：

- `index.md`: 首页内容，包括 hero 文案、按钮、Recent Publications、Recent Blog Posts。
- `_data/menus.yml`: 顶部导航栏和页脚导航。
- `assets/css/custom.css`: 当前网站的定制样式，用于覆盖参考主题的细节。
- `assets/css/theme.scss`: Bootstrap 主题主样式入口，通常不需要频繁修改。
- `_layouts/default.html`: 全站 HTML 骨架、顶部导航、页脚和脚本引用。
- `_layouts/page.html`: 普通页面布局。
- `_layouts/post.html`: 博客文章布局。
- `_includes/postbox.html`: 首页和归档页的卡片组件。
- `_includes/sidebar.html`: 首页 Recent News 侧边栏。
- `_includes/pub_menu.html`: Publications 页面条目组件。
- `_config.yml`: 站点标题、作者、集合、插件、Sass 编译等全局配置。
- `assets/images/`: 图片资源，包括头像、首页图片、logo 和卡片图。
- `_posts/`: 博客文章。
- `_publications/`: publications 条目。
- `_pages/`: 独立页面，比如 CV、Publications、Teaching、Talks、Portfolio、Blog archive。
- `_talks/`, `_teaching/`, `_portfolio/`: 对应栏目内容。

## 修改首页

编辑 `index.md`。

常见位置：

- `Zinan Lin`: 首页大标题。
- hero 区域两段 `<p>`: 首页简介。
- `About me` 按钮: 修改按钮文字或链接。
- `recent_publications`: 自动读取 `_publications/`。
- `recent_posts`: 自动读取 `_posts/`。
- 右侧 Recent News 不在首页文件里，而是在 `_includes/sidebar.html`。

首页 hero 图目前使用：

```html
<img class="intro" height="500" src="{{ '/assets/images/bio-photo.jpg' | relative_url }}" alt="Zinan Lin profile artwork">
```

如果只想替换图片，保持文件名 `assets/images/bio-photo.jpg` 不变即可。

## 修改导航栏

编辑 `_data/menus.yml`。

顶部导航格式：

```yaml
topmenu:
  - title: Home
    url: ""
  - title: Publications
    url: "publications/"
```

外部链接需要加 `external: true`：

```yaml
  - title: GitHub
    url: "https://github.com/znecho9"
    external: true
```

页脚导航在同一个文件的 `footermenu` 区域。

## 修改个人信息

编辑 `_config.yml` 里的这些字段：

```yaml
title: "Zinan Lin"
email: znecho9@gmail.com
url: "https://znecho9.github.io"
logo: "assets/images/logo.svg"

authors:
  Zinan:
    name: Zinan Lin
    avatar: "assets/images/bio-photo.jpg"
    email: znecho9@gmail.com
    github: https://github.com/znecho9
```

这里会影响站点标题、SEO 信息、作者头像、邮箱和社交链接。

## 添加博客文章

在 `_posts/` 新建文件，文件名格式必须是：

```text
YYYY-MM-DD-title.md
```

示例：

```markdown
---
layout: post
title: "My New Post"
date: 2026-05-01
categories: notes
image: assets/images/screenshot.jpeg
excerpt: "一句简短摘要。"
---

正文内容写在这里。
```

博客会自动出现在首页 Recent Blog Posts 和 `/year-archive/` 页面。

## 添加 Publication

在 `_publications/` 新建 Markdown 文件，例如：

```text
_publications/2026-my-paper.md
```

内容格式：

```markdown
---
title: "My Paper Title"
collection: publications
date: 2026-05-01
venue: "Working paper"
status: "draft"
authors: "Zinan Lin"
image: assets/images/screenshot.jpeg
tags:
  - AI Tools
  - Research
excerpt: "这篇文章的一句话摘要。"
---

这里写 publication 的详细说明。
```

Publication 会自动出现在首页 Recent Publications 和 `/publications/` 页面。

## 修改视觉样式

优先编辑 `assets/css/custom.css`，不要直接大改 `assets/css/theme.scss`，除非你确实想调整整套主题。

常见样式入口：

- `.hero`: 首页黄色 hero 区域背景、间距。
- `.hero .intro`: 首页头像/主图尺寸、裁切、圆形效果。
- `.navbar-brand img`: 顶部 logo 尺寸。
- `.card img`: publication/blog 卡片图片比例。
- `.publication-entry`: Publications 页面条目。
- `.article-post`: 正文区域。

参考主题的核心样式在 `assets/css/theme.scss`，Bootstrap Sass 文件在 `_sass/bootstrap/`。

## 替换图片

图片放在 `assets/images/`。

当前常用图片：

- `assets/images/bio-photo.jpg`: 首页 hero 图和作者头像。
- `assets/images/screenshot.jpeg`: 默认卡片图。
- `assets/images/logo.svg`: 导航栏 logo。

如果替换文件但保持文件名不变，页面引用不需要改。如果换了文件名，需要同步修改 `index.md`、`_config.yml` 或对应文章 front matter 里的路径。

## 本地预览

本地需要 Ruby 和 Bundler。安装依赖并启动：

```bash
bundle install
bundle exec jekyll serve
```

然后打开：

```text
http://127.0.0.1:4000/
```

如果本地 Ruby 版本太旧导致 `bundle install` 失败，也可以直接把代码推到 GitHub，通过 GitHub Pages 的 Actions 构建结果确认是否正常。

## 发布到 GitHub Pages

正常流程：

```bash
git status
git add .
git commit -m "Describe your change"
git push origin main
```

推送到 `main` 后，GitHub Pages 会自动构建并发布。可以在仓库的 Actions 页面查看构建是否成功。

## 修改前检查

建议每次改完先看：

```bash
git diff --check
git status
```

重点确认：

- Markdown front matter 的 `---` 是否成对。
- YAML 缩进是否使用空格，不要用 Tab。
- 图片路径是否写成 `assets/images/...` 或 `/assets/images/...`。
- 新文章文件名是否符合 `YYYY-MM-DD-title.md`。
- Liquid 语法 `{% ... %}`、`{{ ... }}` 不要误删。

## 维护原则

当前仓库已经从 remote theme 改为本地主题源码结构。日常维护优先改内容文件、`_data/menus.yml` 和 `assets/css/custom.css`。如果要继续贴近参考网页，建议只对 `assets/css/custom.css` 和 `_layouts/default.html` 做小范围调整，避免整套重新覆盖导致个人内容丢失。
