# application-builder
[README.md](https://github.com/user-attachments/files/32368083/README.md)
# Application Builder

A one-page web app that recreates your "Application for Employment" form. Staff fill in a
form on the left; a formatted application (with a small passport-style photo and one large
full-length photo) builds itself live on the right, ready to download as a PDF.

- No install, no build step, no backend — it's a single `index.html` file.
- All photos and data stay in the browser. Nothing is uploaded anywhere.
- Works on desktop and mobile.

## Try it locally

Just double-click `index.html`, or open it in any browser.

## Put it on GitHub and deploy for free with GitHub Pages

1. **Create a new repository** on GitHub (e.g. `application-builder`). Make it public.
2. **Upload the file.** On the repository page, click **Add file → Upload files**, drag in
   `index.html`, and commit.
   (Or, if you use git on your computer:
   ```
   git init
   git add index.html README.md
   git commit -m "Add application builder"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/application-builder.git
   git push -u origin main
   ```
   )
3. **Turn on Pages.** In the repository, go to **Settings → Pages**. Under "Build and
   deployment", set **Source** to `Deploy from a branch`, pick branch `main` and folder `/root`,
   then click **Save**.
4. **Get your link.** After a minute, GitHub shows a live URL at the top of that same Pages
   settings page, usually:
   ```
   https://YOUR-USERNAME.github.io/application-builder/
   ```
   That's the site your staff can open, fill in, and download a PDF from — on any computer or
   phone, no login needed.

## Customizing it for your business

Open `index.html` in any text editor:

- **Company name / licence number / tagline** — these are pre-filled as editable fields at
  the top of the form itself (`Company details` section), so staff can also just type over
  them in the browser and it'll show correctly on the generated PDF. If you want them locked
  in permanently, search for `id="companyName"` etc. near the top of the `<body>` and change
  the `value="..."` text.
- **Colors** — near the top of the `<style>` block, under `:root`, `--navy` and `--gold`
  control the two main colors used throughout.
- **Add or remove fields** — each field is a small block like:
  ```html
  <div class="field"><label>Religion</label><input id="religion"></div>
  ```
  Copy a block, change the `label` text and the `id`, then add a matching line in the
  `bindings` array near the bottom of the file (in the `<script>` section) so the preview
  updates automatically, e.g.:
  ```js
  ["religion","pReligion"],
  ```
  and add the matching preview cell in the HTML preview table with `id="pReligion"`.

## How the photos work

- **Small photo** — meant for the passport-style headshot (top-right box on the original
  form).
- **Large photo** — meant for the full-length photo.

Click either box to choose a photo from your computer or phone; it appears immediately in the
live preview and is baked into the downloaded PDF.

## Notes

- The PDF is generated in the browser using `html2canvas` and `jsPDF`, loaded from a public
  CDN — an internet connection is needed the first time each browser loads the page, but no
  data is sent anywhere.
- If a page ever looks broken, hard-refresh the browser (Ctrl/Cmd+Shift+R) to clear any old
  cached version.
