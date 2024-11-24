<img width="1473" alt="template-1-wide" src="https://github.com/user-attachments/assets/5debfd0f-e2ee-40f1-919e-d05c6bec82b4">

# astro blog template

minimalistic but opinionated blog template using [astro](https://astro.build/) and [svelte](https://svelte.dev/). aims to be super easy to deploy and use, with a focus on performance and SEO, ease-of-use and design.

See a [live demo here](https://flo-bit.dev/blog-template/) (also doubles as a tutorial on how to use this template).

Features:

- ✅ 100/100 Lighthouse performance
- ✅ SEO-friendly with canonical URLs and OpenGraph data (automatically generated)
- ✅ Sitemap support
- ✅ RSS Feed support
- ✅ Markdown support
- ✅ Pagination
- ✅ Syntax highlighting (+ copy button)
- ✅ Dark and light mode with toggle button or auto-detect
- ✅ Search included
- ✅ Tags for posts
- ✅ Super easy to deploy as a static site
- ✅ Includes some prebuilt components for you to use
- ✅ Easy to edit using [pagecms](https://pagescms.org) or by editing the markdown directly

## tutorials

the demo blog doubles as a tutorial on how to use this template:

- [minimal setup with github pages](https://flo-bit.dev/blog-template/posts/how-to-use)

- [adding content](https://flo-bit.dev/blog-template/posts/adding-content)

- [supported markdown features](https://flo-bit.dev/blog-template/posts/markdown-style-guide)

## Minimal setup with github pages

1. Fork this repository by clicking on "Use template" (note: this repository per default uses github actions which are only free for public repositories).

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

## Notes

Search currently only works in production mode (i.e. when running `npm run build`) not in dev mode (`npm run dev`).

## Credits

Adopted from the default astro blog template when running `npm create astro@latest`.

## License

MIT.