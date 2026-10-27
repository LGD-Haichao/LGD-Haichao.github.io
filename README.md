# Guangxuan Zhang — personal site

A static, dependency-free personal site built for **GitHub Pages**. No build step, no framework, no tracking. Everything is plain HTML, CSS, and a small amount of JavaScript.

## 已部署（Live）

- 网址：**https://lgd-haichao.github.io/**
- 仓库：**https://github.com/LGD-Haichao/LGD-Haichao.github.io**
- GitHub 链接已写入 `assets/js/site.js` 和 HTML fallback；LinkedIn 暂未填写，页面会自动隐藏，填好后刷新即可显示。
- 以后更新：在本文件夹修改 → `git add -A && git commit -m "update" && git push`；GitHub Actions 会自动部署。
- 如果重新建站：把本文件夹内容放到 `<username>.github.io` 仓库根目录，Pages 的 Source 选 **GitHub Actions**。

## What is in here

```
.
├── index.html                  # home
├── projects/
│   ├── index.html              # all projects
│   ├── xinju-liaoshen.html     # field research / consulting
│   ├── ziyun-xinghuo.html      # digital health
│   ├── cishen-weiju.html       # rural teaching
│   ├── low-vision-assistant.html
│   ├── gas-detection.html
│   └── fire-robot.html
├── experience.html             # roles, awards, skills
├── about.html                  # longer bio
├── resume.html                 # print-friendly resume (Print → Save as PDF)
├── zh.html                     # Chinese overview
├── 404.html
├── assets/
│   ├── css/style.css
│   ├── js/site.js              # ← your links live here
│   ├── js/main.js
│   ├── img/favicon.svg
│   └── Guangxuan_Zhang_Resume.pdf
├── .github/workflows/pages.yml # deploy to GitHub Pages
├── .nojekyll
└── robots.txt
```

All internal links are relative, so the site works both at `https://<username>.github.io/` and at `https://<username>.github.io/<repo>/`.

## Links

`assets/js/site.js` currently contains:

```js
window.SITE_CONFIG = {
  github: "https://github.com/LGD-Haichao",
  linkedin: "",
  email: "20465685@qq.com",
  siteName: "Guangxuan Zhang"
};
```

- `github` — live GitHub profile.
- `linkedin` — empty, so the footer and About page hide the LinkedIn link. Add `https://www.linkedin.com/in/...` and refresh to show it.
- `email` — already set to `20465685@qq.com`; change if you prefer another address.

The footer and About page read these values at runtime. The HTML fallbacks already point to the real GitHub profile and the LinkedIn homepage, so there are no `YOUR_...` placeholders left.

## Deploy to GitHub Pages

### Option A — user site (`https://<username>.github.io/`)

1. Create a new public repository named exactly `<username>.github.io`.
2. Put the **contents of this folder** at the repository root (not inside a subfolder).
3. Push to `main`.
4. In the repository: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
5. The included workflow (`.github/workflows/pages.yml`) runs on every push to `main`. Wait for the green check, then open `https://<username>.github.io/`.

### Option B — project site (`https://<username>.github.io/portfolio/`)

1. Create a repository, e.g. `portfolio`.
2. Put the contents of this folder at the repository root.
3. Push to `main`.
4. **Settings → Pages → Source: GitHub Actions**.
5. Open `https://<username>.github.io/portfolio/`.

Relative links mean no configuration is needed for the subpath.

### Alternative: deploy from a branch

If you prefer not to use Actions:

1. Push the files to `main`.
2. **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.
3. Delete `.github/workflows/pages.yml` if you want to avoid a duplicate deployment.

### Custom domain (optional)

Buy a domain (e.g. `guangxuanzhang.com`), add a `CNAME` file at the root containing the domain, and point the DNS records to GitHub Pages. Do this only after the default `github.io` URL works.

## Preview locally

From this folder:

```bash
python -m http.server 8080
```

Open `http://localhost:8080/`. A local server is better than double-clicking `index.html` because root-relative paths and the 404 page behave more like production.

## Editing content

- **Home** — `index.html` (hero, selected projects, principles, metrics, snapshot).
- **Project pages** — `projects/*.html`. Each page has the same structure: hero + meta, prose sections, sidebar, metrics. Copy one page to add a new project, then add a card in `index.html` and `projects/index.html`.
- **Experience / awards** — `experience.html`.
- **Resume** — `resume.html`. Use the “Print / Save as PDF” button; the print stylesheet produces an A4 document. A pre-generated copy lives at `assets/Guangxuan_Zhang_Resume.pdf`; regenerate it after editing the resume content.
- **Chinese overview** — `zh.html`.
- **Colors / type** — CSS variables at the top of `assets/css/style.css` (`--bg`, `--ink`, `--accent`, `--serif`, `--sans`). Dark mode is automatic and stored in `localStorage`.

## Privacy and accuracy

This site is intentionally conservative:

- No phone number, student ID, ID number, or home address.
- No scanned certificates with personal data; project pages cite public articles and the project website instead.
- Team outcomes are labelled as team outcomes; individual awards say “personally named”.
- Internal reports and policy briefs are not uploaded. The project pages describe what was done and note that materials are available on request.
- The site does not use the SAP logo or imply an SAP affiliation. “Targeting SAP STAR 2028” is a statement of intent, not a claim of employment.
- Names of teammates and advisors appear only where they are already public in project materials. If someone asks to be removed, edit the Credits section of the relevant page.

## License

- Code (HTML/CSS/JS): MIT.
- Text, project descriptions, and images: © Guangxuan Zhang, all rights reserved.

## A note on the old resume files

The repository root of the workspace also contains DOCX/PDF resumes. They are deliberately **not** part of this site. The site's `resume.html` is the canonical web version; use the print button to generate a PDF. If you update the DOCX, update `resume.html` too, or replace the print page with a link to the new PDF.
