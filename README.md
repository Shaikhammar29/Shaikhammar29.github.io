# Ammar Ahmed Shaikh — Portfolio

Personal portfolio site for a Network Engineer and freelance QA Engineer, transitioning toward security operations.

## Contents

| File | Purpose |
|---|---|
| `index.html` | The whole site — HTML, CSS, JavaScript, **and the résumé PDF embedded inside it**. No build step, no dependencies. |
| `cv.pdf` | Optional. A loose copy of the résumé, kept only as a fallback and for easy replacement. |

## The CV download

The résumé is embedded in `index.html` as base64 and served to the browser from memory as a blob.
This means **the Download CV and View CV buttons work even if `cv.pdf` is missing from the server** —
there is no second file to 404. Visitors save it as `Ammar_Ahmed_Shaikh_CV.pdf`.

### Updating the résumé

Two options:

1. **Simplest** — delete the entire `<script id="cv-data">` block near the bottom of `index.html`.
   The links then fall back to their `href="cv.pdf"`, so just keep an up-to-date `cv.pdf`
   next to `index.html`.

2. **Keep it embedded** — regenerate the block:

   ```bash
   python3 -c "import base64; print(base64.b64encode(open('cv.pdf','rb').read()).decode())"
   ```

   Paste the output between the `<script id="cv-data" type="text/plain">` and `</script>` tags,
   replacing what is there.

## Editing

- **Contact details** — search for `shaikhammar20@outlook.com` and `+91 77026 49756`.
- **QA tooling** — the QA Engineer bullets omit specific tool names. Add yours (Jira, Azure DevOps,
  Selenium, pytest, Playwright, Postman) in the `<li>` items and the `.chips` row of that role.
- **Colours** — CSS variables in the `:root` block. Amber (`--amber`) marks the in-development security track.
- **Skill levels** — each skill card carries a `style="--lvl:90%"` attribute driving its bar.

## Running locally

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000
