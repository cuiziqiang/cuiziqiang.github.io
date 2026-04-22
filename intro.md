# 项目使用说明 · How to Use This Project

本仓库 `cuiziqiang.github.io` 是基于 [Jekyll](https://jekyllrb.com/) 的
[GitHub Pages](https://pages.github.com/) 个人学术主页，部署后访问地址：

> **https://cuiziqiang.github.io**

视觉风格参考 [acad-homepage](https://rayeren.github.io/acad-homepage.github.io/)：
左侧为头像与联系信息的**固定侧栏**，右侧为带 emoji 小节标题的**单页长滚动**内容
（🔥 News、📝 Publications、🎖 Honors、📖 Educations、💬 Services 等）。

---

## 1. 目录结构 · Repository Layout

```
cuiziqiang.github.io/
├── _config.yml                 # 站点配置（姓名、邮箱、侧栏链接等）
├── index.md                    # 单页学术主页（所有内容都在这里）
├── _layouts/
│   ├── default.html            # 基础布局：侧栏 + 正文
│   └── home.html               # 首页布局（继承 default）
├── _includes/
│   └── profile.html            # 侧栏：头像 + 姓名 + 联系方式 + 社交链接
├── assets/
│   ├── css/
│   │   └── main.scss           # 主样式（acad-homepage 风格）
│   └── img/
│       ├── avatar.jpg          # 头像（需自行上传）
│       └── favicon.png         # 站点 favicon（可选）
├── Gemfile                     # 本地预览依赖
├── intro.md                    # 本说明文件（不会发布到线上）
├── README.md                   # 项目说明
└── .github/workflows/
    └── jekyll-gh-pages.yml     # 自动构建并部署到 GitHub Pages
```

## 2. 快速上手 · Quick Start

### 2.1 在线编辑（推荐）

1. 直接在 GitHub 上打开 `index.md` 修改对应小节；`_config.yml`
   用于维护姓名、邮箱、侧栏链接等站点级别的元数据。
2. 提交后自动触发 Actions 构建，1–2 分钟后刷新
   <https://cuiziqiang.github.io> 即可看到新页面。

### 2.2 本地预览

```bash
bundle install
bundle exec jekyll serve --livereload
# 浏览器访问 http://127.0.0.1:4000
```

## 3. 如何修改内容 · Filling in Your Content

### 3.1 姓名 / 邮箱 / 侧栏链接

集中维护在 **`_config.yml`** 的 `author` 字段：

```yaml
author:
  name: "Ziqiang Cui"
  name_cn: "崔自强"
  avatar: "/assets/img/avatar.jpg"
  email: "cuiziqiang@tju.edu.cn"
  phone: "+86 139-2089-0976"
  office: "Room E, Building 26, Tianjin University"
  links:
    - { label: "Google Scholar", icon: "fas fa-graduation-cap", url: "https://scholar.google.com/" }
    - { label: "GitHub",         icon: "fab fa-github",          url: "https://github.com/cuiziqiang" }
    # 继续添加 ORCID / DBLP / Twitter / ResearchGate 等
```

图标使用 [Font Awesome 6](https://fontawesome.com/search) 类名即可。

### 3.2 正文（News / Publications / Awards / …）

全部写在 **`index.md`**。每个小节以
`# 🔥 News` / `# 📝 Publications` 之类的 H1 标题分隔：

```markdown
# 🔥 News
<ul class="news-list">
  <li><span class="news-date">2026.04</span> 新的学术动态……</li>
</ul>

# 📝 Publications
<div class="pub">
  <div class="pub-thumb">IEEE TIM<br>2025</div>
  <div class="pub-body">
    <p><strong>论文标题 Paper Title.</strong></p>
    <p class="authors"><b>Ziqiang Cui*</b>, Co-author.</p>
    <p class="venue">Journal Name, 2025.</p>
    <p class="links"><a href="…">PDF</a><a href="…">DOI</a></p>
  </div>
</div>
```

样式 class `news-list` / `pub` / `pub-thumb` / `pub-body` 等均已在
`assets/css/main.scss` 中定义。

### 3.3 头像

把 1:1 比例的头像图片保存为
**`assets/img/avatar.jpg`**（推荐 ≥ 512×512）。
如果文件暂缺，侧栏会自动退回显示 Gravatar 占位图。

### 3.4 简历 PDF（可选）

将 PDF 放至 `assets/cv.pdf`，然后在 `index.md` 的合适位置添加下载链接：

```markdown
📄 [Download CV (PDF)]({{ '/assets/cv.pdf' | relative_url }})
```

## 4. 部署机制 · How Deployment Works

- 推送到 `main` 分支后，`.github/workflows/jekyll-gh-pages.yml`
  会使用 `actions/jekyll-build-pages` 构建站点，
  再通过 `actions/deploy-pages` 发布。
- 首次启用时，请到仓库 **Settings → Pages → Build and deployment →
  Source** 选择 **GitHub Actions**。
- 构建失败时，在 Actions 面板查看日志；常见问题是 Markdown 中未闭合的
  HTML 标签或缩进导致 Liquid 解析错误。

## 5. 常见问题 · FAQ

**Q: 为什么不用 acad-homepage 的原仓库 fork？**
A: 原仓库基于 Minimal Mistakes，依赖较多且定制成本高。本项目用一份精简
的自定义布局 + SCSS 就能复现核心视觉（侧栏 + emoji 分节 + 论文卡片）。
如果希望用完整版，可以直接 fork
<https://github.com/RayeRen/acad-homepage.github.io> 并把
`_config.yml`、`_pages/about.md` 替换成本仓库的同名文件。

**Q: 样式太深/太浅，想改配色？**
A: 在 `assets/css/main.scss` 的 `:root` 区域修改
`--color-accent` / `--color-text` / `--color-bg` 等 CSS 变量即可。

**Q: 如何加 Google Scholar 引用数徽章？**
A: 在 `index.md` 相应位置插入 acad-homepage 同款图片徽章：
```html
<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fcdn.jsdelivr.net%2Fgh%2FRayeRen%2Facad-homepage.github.io%40master%2Fgoogle_scholar_crawler%2Fresults%2Fgs_data_shieldsio.json&labelColor=f6f6f6&color=9cf&style=flat&label=citations" />
```
把 URL 换成自己主页的爬取结果即可。

**Q: 如何启用评论 / 数学公式 / 统计？**
A: 在 `_layouts/default.html` 的 `<head>` 或 `</body>` 之前引入对应脚本
（MathJax、giscus、百度统计等），无需动主题。

## 6. 许可 · License

文字内容版权归作者所有；模板代码可自由复用。如需添加正式协议，
在仓库根目录新增 `LICENSE` 文件即可。
