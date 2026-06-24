[README.md](https://github.com/user-attachments/files/29281192/README.md)
# History Paper Format Checker · 历史论文格式检查工具

<p align="center">
  <b>English</b> | <a href="#中文说明">中文</a>
</p>

A lightweight, **fully client-side** tool that checks whether a history paper conforms to academic formatting standards — either the Chinese journal *Historical Research* (《历史研究》) standard or the **Chicago Manual of Style, 18th Edition** — and can **auto-generate a corrected `.docx`** with one click.

Everything runs in your browser. **No server, no AI API, no cost, and your files never leave your device.**

> 🔗 **Live demo:** `https://<your-username>.github.io/<repo-name>/`
> *(replace with your own link after deploying — see [Deployment](#deployment))*

---

## Features

- 📤 **Upload `.docx` / `.pdf` / `.txt`**, or paste text directly — files are parsed locally in the browser.
- 🌐 **Auto-detects language** (Chinese / English) and applies the matching standard; manual override available.
- 🔍 **Rule-based checks** for things with clear, deterministic rules:
  - Footnote / endnote numbering style (circled ①②③ vs. Arabic; position relative to punctuation)
  - Heading hierarchy (一、（一）1.（1） vs. I. A. 1. a.)
  - Citation punctuation and field order for books, journals, newspapers, etc.
  - Structural completeness (abstract, keywords, bibliography…)
  - Punctuation issues (Chinese/English mixing, en-dash vs. hyphen)
- 🎯 **`.docx` only:** also checks **font, font size, line spacing, and page margins** against the standard.
- ⚡ **One-click "Generate compliant `.docx`"** *(new)*: automatically fixes global formatting — **font, size, line spacing, page margins** — while keeping all of your original text. Complex items (footnotes, citations) are listed as suggestions for manual adjustment.
- 📄 **Export** the issue list as a `.txt` file, or print / save as PDF.

---

## Limitations (please read)

This is a **rule-based tool**, not an AI. It is honest about what it cannot do:

- **Font / size / spacing / margins are only detectable (and fixable) from `.docx` files.** PDFs and pasted text do not carry reliable formatting data, so those checks are skipped with a note to verify manually in Word.
- The **"Generate compliant `.docx`"** feature corrects **global formatting only**. It does not rewrite footnotes, citation entries, or heading numbers — those are reported as suggestions, because automatically rewriting them risks corrupting the document. For documents with heavy footnotes or tables, review the result in Word.
- It checks **format**, not academic content — it cannot verify whether a citation's facts are correct.
- Results are for **reference only**. Always confirm against the official standard before submission.

---

## Usage

**Option 1 — Just open the file**
Download `index.html` and double-click it. It opens in any modern browser. Works offline.

**Option 2 — Use the hosted link**
If deployed (see below), simply share the URL. Anyone can use it with one click — no installation, no account.

**Typical workflow:**
1. Upload a `.docx` (or paste text).
2. Click **Check Format** to see a full diagnostic report.
3. *(for `.docx`)* Click **⚡ Generate compliant `.docx`** to download an auto-corrected version.
4. Use the exported issue list to manually fix footnotes / citations.

---

## Deployment

Want a shareable link instead of passing a file around? Host it free on **GitHub Pages**:

1. Create a new GitHub repository (e.g. `history-format-checker`) and upload `index.html`.
   - The file is already named `index.html`, so the page will load at the root URL automatically.
2. Go to the repo's **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Select branch `main` and folder `/ (root)`, then click **Save**.
5. Wait ~1 minute. Your tool will be live at:
   `https://<your-username>.github.io/<repo-name>/`

That URL is free, handles any amount of traffic, and you can share it directly with classmates.

---

## Tech

Single self-contained HTML file. Uses two open-source libraries via CDN:
- [JSZip](https://stuk.github.io/jszip/) — to read and rewrite `.docx` (which is a zip archive)
- [PDF.js](https://mozilla.github.io/pdf.js/) — to extract text from `.pdf`

The compliant-`.docx` generator works by editing the original document's underlying XML (`styles.xml` and `document.xml`), so your original content is preserved exactly.

No build step, no framework, no backend.

---

## License

[MIT](LICENSE) © Kira Zhang

---
---

<a name="中文说明"></a>

# 中文说明

<p align="center">
  <a href="#history-paper-format-checker--历史论文格式检查工具">English</a> | <b>中文</b>
</p>

一个轻量、**纯浏览器本地运行**的工具，用于检查历史论文是否符合学术格式规范——支持中文期刊《历史研究》规范，以及 **Chicago Manual of Style 第18版**——并能**一键自动生成修正后的 `.docx`**。

所有处理都在你的浏览器里完成。**无需服务器、不调用 AI、不花一分钱，文件也不会离开你的设备。**

> 🔗 **在线使用：** `https://<你的用户名>.github.io/<仓库名>/`
> *（部署后替换成你自己的链接——见 [部署教程](#部署教程)）*

---

## 功能

- 📤 **上传 `.docx` / `.pdf` / `.txt`**，或直接粘贴文本——文件在浏览器本地解析。
- 🌐 **自动判断语言**（中文 / 英文）并套用对应规范，也可手动强制选择。
- 🔍 对**有明确规则**的格式项进行检查：
  - 脚注 / 尾注序号样式（圈号①②③ vs. 阿拉伯数字；序号在标点前还是后）
  - 标题层级（一、（一）1.（1） vs. I. A. 1. a.）
  - 专著、期刊、报纸等文献著录的标点与字段顺序
  - 结构完整性（摘要、关键词、参考文献等）
  - 标点规范（中英文混用、连接号 - vs. –）
- 🎯 **仅限 `.docx`：** 还能检测**字体、字号、行距、页边距**是否符合规范。
- ⚡ **一键「生成合规版 `.docx`」**（新功能）：自动修正**字体、字号、行距、页边距**等全局格式，并完整保留原文内容。脚注、文献著录等复杂内容以建议清单形式呈现，供手动调整。
- 📄 **导出**问题清单为 `.txt`，或打印 / 存为 PDF。

---

## 使用限制（请务必阅读）

这是一个**规则检查工具**，不是 AI。它对自己做不到的事情很诚实：

- **字体 / 字号 / 行距 / 页边距只能从 `.docx` 文件检测（和修正）。** PDF 和粘贴文本不含可靠的格式信息，这些项会跳过并提示在 Word 中人工核对。
- **「生成合规版 `.docx`」只修正全局格式**，不会改写脚注、文献著录条目或标题序号——这些以建议形式列出，因为自动改写它们有破坏文档的风险。对脚注或表格较多的文档，请在 Word 中复查生成结果。
- 它检查的是**格式**，不是学术内容——无法核实引文中的史实是否准确。
- 检查结果**仅供参考**。投稿前请务必对照规范原文确认。

---

## 怎么用

**方式一 —— 直接打开文件**
下载 `index.html`，双击即可在任何现代浏览器中打开。支持离线使用。

**方式二 —— 使用在线链接**
如果已部署（见下方），直接把网址发给别人即可。任何人点链接就能用，无需安装、无需账号。

**典型流程：**
1. 上传一个 `.docx`（或粘贴文本）。
2. 点击**检查格式**，查看完整诊断报告。
3. *（针对 `.docx`）* 点击 **⚡ 生成合规版 `.docx`**，下载自动修正后的版本。
4. 对照导出的问题清单，手动修改脚注 / 文献著录。

---

## 部署教程

想要一个能直接分享的链接，而不是来回传文件？用 **GitHub Pages** 免费托管：

1. 新建一个 GitHub 仓库（例如 `history-format-checker`），上传 `index.html`。
   - 文件已命名为 `index.html`，访问根网址即可自动打开页面。
2. 进入仓库的 **Settings（设置）→ Pages**。
3. 在 **Build and deployment → Source** 下，选择 **Deploy from a branch**。
4. 选择分支 `main`、文件夹 `/ (root)`，点击 **Save**。
5. 等待约 1 分钟，你的工具就会上线，网址为：
   `https://<你的用户名>.github.io/<仓库名>/`

这个网址免费、能承载任意访问量，可以直接发给同学使用。

---

## 技术说明

单个独立的 HTML 文件。通过 CDN 引用两个开源库：
- [JSZip](https://stuk.github.io/jszip/) —— 读取并改写 `.docx`（本质是 zip 压缩包）
- [PDF.js](https://mozilla.github.io/pdf.js/) —— 提取 `.pdf` 文本

合规版 `.docx` 的生成原理是直接编辑原文档底层的 XML（`styles.xml` 与 `document.xml`），因此你的原文内容会被完整保留。

无需构建、无框架、无后端。

---

## 许可证

[MIT](LICENSE) © Kira Zhang
