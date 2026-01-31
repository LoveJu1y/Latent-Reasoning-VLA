# 项目主页填写指南（Academic-project-page-template）

你现在要做的是**项目主页**（paper/project landing page），主要编辑：

- `Academic-project-page-template/index.html`（内容）
- `Academic-project-page-template/static/`（图片/视频/PDF 资源）

## 最快上手（建议顺序）

1. 打开 `index.html`，搜索 `TODO:`，按提示替换：
   - 标题、作者、单位、会议/期刊
   - Paper/PDF、Code、arXiv、Demo/Project 链接
   - teaser 文案、摘要、结果说明
   - SEO meta（description、keywords、og:url、og:image 等）
2. 替换资源文件：
   - `static/videos/banner_video.mp4`：teaser 视频
   - `static/images/carousel*.jpg`：结果图
   - `static/pdfs/sample.pdf`：Poster/附录/论文 PDF
   - `static/images/favicon.ico`：站点图标（强烈建议换掉）
3. 本地预览：

```bash
python -m http.server 5173
```

浏览器打开：`http://localhost:5173/Academic-project-page-template/`

## 资源建议

- **分享预览图**：`static/images/social_preview.png`，尺寸 1200×630
- **视频大小**：>10MB 建议放到 YouTube（或其他视频平台），页面用 iframe 引入
- **图片压缩**：建议压到 200KB~800KB（视细节而定）

## 常见改动点

- **只想做一个项目页**：保留 teaser / abstract / results / poster / bibtex；不需要的 section 直接删除
- **不需要 More Works 下拉**：删除 `more-works-container` 整个块即可

