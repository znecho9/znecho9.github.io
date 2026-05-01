# znecho9.github.io

这是 [znecho9.github.io](https://znecho9.github.io/) 的源码仓库。网站使用 Jekyll + Minimal Mistakes remote theme 构建，主要内容和样式都保存在这个仓库里。

## 文件结构

最常改的文件：

- `index.md`: 首页内容。首页的大标题、介绍文字、按钮、Recent Publications、Recent News、Recent Blog Posts 都从这里组织。
- `_sass/_custom-styles.scss`: 自定义视觉样式。首页布局、字体、颜色、卡片、hero 区域、导航微调都在这里。
- `_data/navigation.yml`: 顶部导航栏。
- `_config.yml`: 站点全局配置，包括站点标题、作者信息、头像、邮箱、GitHub 链接、集合配置。
- `_includes/head/custom.html`: 额外插入到 `<head>` 的内容，目前用于加载 Google Fonts。
- `assets/images/`: 图片资源，包括头像、首页图片、logo 和默认卡片图。
- `_posts/`: 博客文章。
- `_publications/`: publications 条目。
- `_pages/`: 独立页面，比如 CV、Publications、Teaching、Talks、Portfolio、Blog archive。
- `_talks/`, `_teaching/`, `_portfolio/`: 对应栏目内容。

主题源码不在仓库里。仓库通过 `_config.yml` 里的 `remote_theme: "mmistakes/minimal-mistakes@4.27.3"` 在 GitHub Pages 构建时自动加载主题。

## 修改首页

编辑 `index.md`。

常见位置：

- `Zinan Lin`: 首页大标题。
- `kf-lead` 段落：hero 区域的第一段介绍。
- `kf-actions`: 首页按钮。
- `kf-news`: 右侧 Recent News。
- `recent_publications`: 自动读取 `_publications/` 里的内容。
- `recent_posts`: 自动读取 `_posts/` 里的内容。

修改 Recent News 时，按这个格式新增或替换：

```html
<div class="kf-news__item">
  <time datetime="2026-05">May 2026</time>
  <p>这里写新闻内容。</p>
</div>
```

## 修改导航栏

编辑 `_data/navigation.yml`。

格式如下：

```yaml
main:
  - title: Home
    url: /
  - title: Publications
    url: /publications/
```

如果是外部链接，可以加 `target: _blank`：

```yaml
  - title: GitHub
    url: https://github.com/znecho9
    target: _blank
```

## 修改个人信息

编辑 `_config.yml` 里的 `author` 区域：

```yaml
author:
  name: "Zinan Lin"
  avatar: "/assets/images/bio-photo.jpg"
  bio: "Independent Engineer & Researcher..."
  location: "China"
  email: "znecho9@gmail.com"
  github: "znecho9"
```

这里会影响侧边栏作者卡片、站点元信息、页脚链接等。

## 添加博客文章

在 `_posts/` 新建文件，文件名格式必须是：

```text
YYYY-MM-DD-title.md
```

示例：

```markdown
---
layout: single
title: "My New Post"
date: 2026-05-01
categories: notes
header:
  image: /assets/images/screenshot.jpeg
excerpt: "一句简短摘要。"
---

正文内容写在这里。
```

博客会自动出现在首页的 Recent Blog Posts 和 `/year-archive/` 页面。

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
image: "/assets/images/screenshot.jpeg"
tags:
  - AI Tools
  - Research
excerpt: "这篇文章的一句话摘要。"
---

这里写 publication 的详细说明。
```

Publication 会自动出现在首页 Recent Publications 和 `/publications/` 页面。

## 修改视觉样式

编辑 `_sass/_custom-styles.scss`。

常见样式入口：

- `:root`: 全站颜色变量。
- `.kf-hero`: 首页 hero 区域背景、间距、两栏布局。
- `.kf-hero__copy h1`: 首页大标题字号。
- `.kf-card`: publication/blog 卡片样式。
- `.kf-news`: 右侧 Recent News 栏。
- `.masthead` 和 `.greedy-nav`: 顶部导航栏样式。

改颜色时优先改顶部变量：

```scss
:root {
  --kf-text: #212529;
  --kf-muted: #6c757d;
  --kf-soft: #f8f9fa;
  --kf-link: #1f4fbf;
}
```

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
- 图片路径是否以 `/assets/images/...` 开头。
- 新文章文件名是否符合 `YYYY-MM-DD-title.md`。
- 首页 Liquid 语法 `{% ... %}`、`{{ ... }}` 不要误删。

## 最小维护原则

这个仓库已经清理为轻量结构。日常维护时优先改内容文件和 `_sass/_custom-styles.scss`，不要重新复制整套 Minimal Mistakes 主题源码进仓库。需要覆盖主题时，只添加具体需要覆盖的单个 include、layout 或样式文件。
