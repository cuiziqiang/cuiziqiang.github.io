# 项目使用说明 · How to Use This Project

本仓库 `cuiziqiang.github.io` 是基于 [Jekyll](https://jekyllrb.com/) 的
[GitHub Pages](https://pages.github.com/) 个人学术主页模板，部署后访问地址为：

> **https://cuiziqiang.github.io**

页面结构参考国内高校教师主页样式（如
<https://seea.tju.edu.cn/info/1117/2037.htm>），
默认包含：个人简介、研究方向、论文发表、教学工作、简历等模块。

---

## 1. 目录结构 · Repository Layout

```
cuiziqiang.github.io/
├── _config.yml                 # Jekyll 站点配置
├── index.md                    # 首页（个人简介 / Home）
├── research.md                 # 研究方向 Research
├── publications.md             # 论文发表 Publications
├── teaching.md                 # 教学工作 Teaching
├── cv.md                       # 简历 CV
├── Gemfile                     # 本地预览依赖
├── intro.md                    # 本说明文件
├── README.md                   # 项目说明
└── .github/workflows/
    └── jekyll-gh-pages.yml     # 自动构建与部署到 GitHub Pages
```

所有页面使用 Markdown 编写，文件头部的 YAML `---` 区域称为 **front matter**，
用于声明页面标题、布局和访问路径（`permalink`），一般无需改动。

## 2. 快速上手 · Quick Start

### 2.1 直接在 GitHub 上编辑（推荐新手）

1. 打开对应的 `.md` 文件（例如 `index.md`）。
2. 点击右上角 ✏️ 铅笔图标进入编辑模式。
3. 修改内容后点击 **Commit changes** 提交。
4. 提交到 `main` 分支会触发 `.github/workflows/jekyll-gh-pages.yml`
   工作流，约 1–2 分钟后新的页面即可在
   <https://cuiziqiang.github.io> 访问。

### 2.2 本地预览 · Local Preview

需要 Ruby ≥ 3.1 与 Bundler。

```bash
# 安装依赖
bundle install

# 启动本地服务，默认地址 http://127.0.0.1:4000
bundle exec jekyll serve --livereload
```

如在 Windows 上首次运行遇到 `tzinfo` 报错，`Gemfile` 已包含
`tzinfo-data` 与 `wdm`，执行一次 `bundle install` 即可。

## 3. 如何填充内容 · Filling in Your Content

建议按以下顺序逐个文件修改，每个文件内的占位文字（中文“在此填写…”与英文
*italic hints*）都可直接替换为您自己的信息。

| 文件 File | 要替换的内容 What to edit |
| --- | --- |
| `_config.yml` | 站点标题、描述、邮箱、URL |
| `index.md` | 姓名、职位、单位、研究方向概述、最新动态 |
| `research.md` | 研究兴趣分组、在研与已结题项目 |
| `publications.md` | 按年份的期刊/会议论文、专利、学术服务 |
| `teaching.md` | 本科/研究生课程、指导学生名单 |
| `cv.md` | 教育背景、工作经历、获奖情况 |

### 添加头像 · Adding a Profile Photo

1. 将图片放到 `assets/img/avatar.jpg`（目录不存在时自己创建）。
2. 在 `index.md` 中插入：
   ```markdown
   ![avatar]({{ '/assets/img/avatar.jpg' | relative_url }}){: width="180" }
   ```

### 添加简历 PDF · Adding a CV PDF

将 PDF 放到 `assets/cv.pdf`，`cv.md` 中已准备好下载链接。

### 新增页面 · Creating a New Page

在仓库根目录新建 `yourpage.md`，开头加上：

```yaml
---
layout: page
title: 页面标题 Your Title
permalink: /yourpage/
---
```

若希望出现在导航栏，再将文件名加入 `_config.yml` 的 `header_pages` 列表。

## 4. 部署机制 · How Deployment Works

- 推送到 `main` 分支后，GitHub Actions 会运行
  `.github/workflows/jekyll-gh-pages.yml`。
- 该工作流使用 `actions/jekyll-build-pages` 构建站点，再通过
  `actions/deploy-pages` 部署到 GitHub Pages 环境。
- 首次启用时，请在仓库的 **Settings → Pages → Build and deployment →
  Source** 选择 **GitHub Actions**。
- 部署成功后，可在 Actions 面板查看 `page_url` 输出。

## 5. 常见问题 · FAQ

**Q: 修改了文件，网站却没有更新？**
A: 打开 Actions 面板查看最近一次工作流是否失败；失败时点击查看日志。
也可清理浏览器缓存或用隐身模式访问。

**Q: 可以换主题吗？**
A: 可以。将 `_config.yml` 中 `theme: minima` 改为任意
[GitHub Pages 支持的主题](https://pages.github.com/themes/)，
或改用 `remote_theme:` 使用远程主题。

**Q: 如何启用评论 / 统计 / 数学公式？**
A: 可在 `_includes/` 中加入自定义片段（如 giscus、百度统计、MathJax），
并在页面或默认布局中引用。Minima 主题支持 `_includes/head.html` 覆盖。

## 6. 许可 · License

站点文字内容版权归作者所有；代码部分（模板结构）可自由复用。
如需更严格声明，请在仓库根目录添加 `LICENSE` 文件。
