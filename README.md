# online-education-platform (README)

## Overview

**online-education-platform** is a single-page, front-end-only educational UI that showcases subjects, topics, subtopics and embedded resources (video/pdf). It’s built with plain HTML, CSS and vanilla JavaScript and includes polished UI touches like animated background shapes, glassmorphism cards, a progress bar and a responsive layout.

This repository is ideal as a lightweight prototype, design reference, or starter template for a larger LMS/dashboard.

---

## Live preview

Open `index.html` in your browser (double-click or `Open with` in your editor).
No build step or server required for basic usage.

---

## Features

* Responsive, modern UI with gradient background and floating animated shapes
* Subjects → Topics → Subtopics navigation flow
* Embedded resource viewer (YouTube videos + PDF previews via iframes)
* Progress bar that reflects navigation steps
* Doubts modal for contacting an instructor (placeholder)
* Keyboard (Esc) to close modal and subtle button click animation
* Parallax effect for background shapes (mouse move)
* Mobile-friendly breakpoints

---

## Tech stack

* HTML5
* CSS3 (including CSS animations & gradients)
* Vanilla JavaScript (ES6+)

No frameworks or build tools required.

---

## File structure

```
/ (project root)
├─ index.html           ← main HTML file (contains CSS & JS inline)
└─ README.md            ← this file
```

> Note: The project is currently a single-file demo. For larger projects split CSS/JS into separate files.

---

## How to use / run locally

1. Clone or download this repository.
2. Open `index.html` in any modern browser (Chrome, Firefox, Edge, Safari).
3. Click **Subjects** → pick a subject → pick a topic → pick a subtopic → open resource viewer.
4. Toggle between **Video** and **PDF** tabs inside the resource viewer.

### Optional: Serve with a local server

* Python 3:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

* Or use VS Code Live Server extension — click **Go Live**.

---

## Customization guide

* **Add subjects/topics/resources**: Edit the `resources` object in the `<script>` section of `index.html`. Use resource keys (e.g. `algebra-linear`) and set `title`, `video` (YouTube embed URL), and `pdf` (PDF preview URL).
* **Add more subject cards**: Duplicate a `.subject-card` in the `#subjectsGrid` with a new `onclick="showTopics('yourKey')"` and create the corresponding topics container: `<div id="yourKeyTopics" class="topics-container">…</div>`.
* **Move CSS/JS into separate files**: Create `styles.css` and `app.js` and move the inline code. Then link them from the HTML head and before `</body>` respectively.
* **Change theme**: Update gradient colors and button colors in the CSS.
* **Replace emojis with SVG icons**: For production, consider using SVG icons (Heroicons, Font Awesome, or custom SVGs).

---

## Accessibility & UX notes

* Add `aria-label` and semantic landmarks for screen readers.
* Add `alt` text for images if replacing emojis with images.
* Improve keyboard navigation (tab focus states, ARIA roles for dialogs).
* Iframe PDF resources may be blocked by some services — consider hosting PDFs or using a viewer service that supports embedding.

---

## Security considerations

* Embedded iframes (YouTube, Google Drive) can be blocked due to `X-Frame-Options` or CORS. If a PDF or video fails to display, check provider embed permissions.
* If moving to production, sanitize/validate any user input before embedding to avoid injection risks.
* Consider Content Security Policy (CSP) headers when serving from a web server.

---

## Suggestions & next steps

* Extract CSS/JS into dedicated files and set up a simple build pipeline (optional).
* Replace hardcoded `resources` object with data fetched from a JSON API or CMS.
* Add authentication and user progress tracking (localStorage or backend).
* Implement offline caching (service worker) for a PWA experience.
* Improve the Doubts modal to show a contact form and submit messages to an API.

---

## Contributing

1. Fork the repo.
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push and open a PR.

If you want, paste your improved code here and I can help integrate it.

---

## License

Use as you like — include a license file in your repo if you plan to publish. Suggested: MIT License.

---

## Credits

* Design and implementation by the project author.
* Uses public YouTube embed links and Google Drive preview links (placeholder). Make sure you have permission to embed any external content you add.

---

## Quick FAQ

**Q: Videos not loading?**
A: Check the `video` URL in the `resources` object — it should be a YouTube embed URL format (`https://www.youtube.com/embed/<VIDEO_ID>`). Also try serving over `http://localhost` if the browser blocks local file iframe content.

**Q: PDF not showing?**
A: Some Google Drive links won’t preview in an iframe due to sharing settings. Use properly shared public preview links or host the PDF on a server that allows embedding.
