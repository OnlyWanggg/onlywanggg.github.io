# Weiyi Wang's homepage

Source of my personal academic homepage, built with [al-folio](https://github.com/alshedivat/al-folio) v1.2 (Jekyll) and deployed to GitHub Pages by GitHub Actions.

## 内容在哪里改

| 想改的内容 | 文件 |
|---|---|
| 姓名、网址、站点描述、功能开关 | `_config.yml` |
| 首页简介、头像旁的单位信息 | `_pages/about.md`；头像 `assets/img/prof_pic.jpg` |
| 联系方式图标（邮箱、GitHub、Scholar、ORCID、CV） | `_data/socials.yml` |
| 论文列表 | `_bibliography/papers.bib`（`selected = {true}` 会出现在首页；缩略图放 `assets/img/publication_preview/`，PDF 放 `assets/pdf/`） |
| 会议 / 期刊徽章颜色 | `_data/venues.yml` |
| 新闻 | `_news/` 下每条一个 `.md` 文件 |
| 项目页 | `_projects/` 下每个项目一个 `.md` 文件；图片放 `assets/img/projects/` |
| CV 页面与 PDF 简历 | `_data/cv.yml`；推送后 `Render a CV` workflow 用 RenderCV 生成 `assets/rendercv/rendercv_output/Weiyi_Wang_CV.pdf` |

## 中英文内容

英文页面保持现有网址，中文版在 `/zh/`。导航栏自动连接同一页面的另一种语言。更新简介、项目或简历时，同步编辑 `_pages/zh/` 中的中文版。动态在同一个 `_news/` 文件中维护英文正文和 `content_zh`。两种语言共用图片、BibTeX 和公开 PDF；中文版简历页面链接的是英文 PDF。

## 部署（GitHub Pages）

1. 仓库 `OnlyWanggg/onlywanggg.github.io` 的 Settings → Pages → Source 选 **GitHub Actions**。
2. 推送到 `main` 后，**Deploy site** 会构建并发布。也可在 Actions 手动运行。
3. 访问 `https://onlywanggg.github.io`。

修改 `_data/cv.yml` 后，Render a CV 会把新的 PDF 提交回仓库。GitHub 不会因为这次提交再次触发部署，所以需要等它完成后，到 Actions → Deploy site → **Run workflow** 手动重新部署一次。

## 本站相对 al-folio 模板的改动

- 删除了模板自带的示例内容，包括博客、书架、课程、示例论文和图片，以及只服务于模板仓库本身的 workflow 和文档。只保留 `deploy.yml` 和 `render-cv.yml` 两个 workflow。
- `third_party_libraries.download: true`：构建时把 JS/CSS 库、Google Fonts 和图标字体下载到本站，国内访客不再依赖 jsDelivr 和 Google。另外为 Font Awesome 和 Academicons 补充了字体目录的下载地址，否则图标会缺字体。
- 双语布局覆盖了 al-folio 的首页、导航、页脚和页面元数据。`_includes/news.liquid` 按页面语言显示动态，日期精确到年月。
- `assets/rendercv/design.yaml` 已按 RenderCV 2.x 重写。`render-cv.yml` 现在显式传入 `--design` 和 `--locale-catalog`，因为 RenderCV 2.x 不会读取 settings.yaml 里写的这两个路径。

## License

Site theme: al-folio, MIT License (see `LICENSE`). Paper PDFs in `assets/pdf/` are published under CC BY 4.0 by their authors.
