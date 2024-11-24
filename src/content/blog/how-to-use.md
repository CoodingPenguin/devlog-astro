---
title: "Minimal setup with github pages"
description: "Learn how to use this blog template with github pages (for free, with no coding required)"
pubDate: "Oct 26 2024"
published: true
heroImage: "/src/assets/blog-placeholder-2.jpg"
tags: ["setup"]
---

1. Fork [the repository of this blog](https://github.com/flo-bit/blog-template) (note: this repository per default uses github actions which are only free for public repositories)

2. In your repository settings, set up github pages to deploy using github actions (*SETTINGS* -> *PAGES* -> *SOURCE*: **Github Actions**)

3. Your blog should be live in about 1 minute at `https://<your-github-username>.github.io/<your-repo-name>`

For editing the blog you can either edit the code directly or use the preconfigured [pagescms](https://next.pagescms.org).

### Editing with pagescms

4. Go to [pagescms](https://next.pagescms.org) and log in with your github account and authorize the app.

5. Add your repository to pagescms and open it.

6. Now you can edit your website configuration, about page, description and blog posts directly in the browser.

7. Your changes will be automatically pushed to your repository and deployed to github pages in about 1 minute everytime you hit save.

### Editing the code

4. Set up your blog info in `src/config.json` (leaving SITE, BASE, and MANUAL_SITE_BASE, as they are).

5. Add your blog posts in `src/content/blog/`

6. Add your info in `src/content/info/`:

- `description.md` is used for the homepage description
- `about.md` is used for the about page
