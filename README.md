# 📄 Resume as Code

> My resume is written in HTML/CSS and automatically compiled into a
> pixel-perfect PDF using a GitHub Actions CI/CD pipeline — on every push.

---

## 🚀 How it works

1. Resume content lives in `resume.html`
2. Styling is in `style.css`
3. On every push to `main`, GitHub Actions:
   - Spins up an Ubuntu runner
   - Installs Node.js and Puppeteer (headless Chrome)
   - Renders the HTML+CSS into a pixel-perfect PDF
   - Publishes it as a GitHub Release automatically

No manual exporting. No outdated copies. Always up to date.

---

## 📁 Project Structure
```
resume/
├── .github/
│   └── workflows/
│       └── build.yml
├── resume.html
├── style.css
└── README.md
```
---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| GitHub Actions | CI/CD pipeline |
| Puppeteer | HTML → PDF rendering |
| Node.js | Runtime for Puppeteer |
| HTML + CSS | Resume source of truth |

---

## 📥 Download Latest Resume

Head to the [**Releases**](https://github.com/Shushankranjan/resume/releases) tab
and download the latest `KumarShushankRanjan_Resume.pdf`

---

## 💡 Why Resume as Code?

- **Version controlled** — full history of every change ever made
- **Always current** — push a change, PDF is auto-generated
- **No design tools needed** — content and style are separated
- **Recruiter friendly** — one link, always the latest version

---

## 🔧 Run Locally

```bash
# Clone the repo
git clone https://github.com/Shushankranjan/resume.git
cd resume

# Install dependencies
npm install puppeteer

# Generate PDF
node -e "
const puppeteer = require('puppeteer');
const path = require('path');
(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('file://' + path.resolve('resume.html'), { waitUntil: 'networkidle0' });
  await page.pdf({
    path: 'KumarShushankRanjan_Resume.pdf',
    format: 'A4',
    printBackground: true,
    margin: { top: '15mm', bottom: '15mm', left: '18mm', right: '18mm' }
  });
  await browser.close();
})();
"
```

---

*Auto-generated with ❤️ using GitHub Actions*
