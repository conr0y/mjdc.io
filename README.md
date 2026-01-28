# mjdc.io

Personal website for Michael Conroy. Minimalist design — Courier Prime typewriter font, off-white background, no frameworks.

## Structure

```
index.html        — Home page
projects.html     — Projects listing
blog.html         — Blog index
contact.html      — Contact form (Formspree)
style.css         — Single stylesheet
blog/
  post.html       — Markdown post renderer (marked.js)
  hello-world.md  — Starter post
```

## Blog workflow

1. Write a new `.md` file in `blog/`
2. Add a link to `blog.html` pointing to `blog/post.html?post=filename`
3. That's it — no build step

## Local development

```
python3 -m http.server
```

Then visit `http://localhost:8000`. The local server is needed for blog post markdown rendering (fetch won't work over `file://`).
