# Guangxuan Zhang — personal site

A static, dependency-free personal site built for **GitHub Pages**. No build step, no framework, no tracking. Everything is plain HTML, CSS, and a small amount of JavaScript.

## 快速开始（中文）

1. 打开 `assets/js/site.js`，把 `YOUR_GITHUB_USERNAME` 和 `YOUR_LINKEDIN` 换成你的地址（邮箱已填好）。
2. 在 GitHub 新建仓库 `<你的用户名>.github.io`，把**本文件夹里的内容**放到仓库根目录（不是再套一层文件夹）。
3. 推到 `main` 分支；在仓库 **Settings → Pages → Build and deployment → Source** 选 **GitHub Actions**。
4. 等 Actions 变绿，访问 `https://<你的用户名>.github.io/`。

如果想让网址是 `https://<你的用户名>.github.io/portfolio/`，把仓库名改成 `portfolio` 即可，站内链接都是相对路径，不需要改。详细说明见下文。

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

## Before you publish: replace 3 placeholders

Open `assets/js/site.js` and replace:

```js
window.SITE_CONFIG = {
  github: "https://github.com/YOUR_GITHUB_USERNAME",
  linkedin: "https://www.linkedin.com/in/YOUR_LINKEDIN",
  email: "20465685@qq.com",
  siteName: "Guangxuan Zhang"
};
```

- `github` — your GitHub profile URL.
- `linkedin` — your LinkedIn URL (or remove the LinkedIn link from the footer/about page if you do not have one).
- `email` — already set to `20465685@qq.com`; change if you prefer another address.

The footer and About page read these values at runtime. If JavaScript is disabled, the links fall back to the placeholder in the HTML; edit those too if you want a no-JS fallback.

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
