# Amin’s website

A small Jekyll site for GitHub Pages. No theme, JavaScript, external fonts, or custom plugins. Content is Markdown; layouts and one CSS file handle presentation.

## First-time setup

1. Review `index.html`, `about.md`, and `work.md`. These contain starter copy based on the design brief; replace it with your own details.
2. In `_config.yml`, set `url` to your live origin (for example `https://USERNAME.github.io`, without a trailing slash). For a repository named `USERNAME.github.io`, leave `baseurl: ""`. For a project repository named `personal_website`, use `baseurl: "/personal_website"`. A custom domain at its root uses an empty baseurl.
3. Optionally fill in `email`, `github_url`, and `linkedin_url`; empty contact links remain hidden.
4. Remove `_posts/2026-09-23-sample-post.md`. It is only a typography/content sample.
5. Push this folder’s contents to your GitHub repository. In **Settings → Pages**, select **Deploy from a branch**, your publishing branch (usually `main`), and **/(root)**. Save. GitHub builds Jekyll automatically; no custom workflow is needed.

See [GitHub’s publishing-source instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Publish a post

Create `_posts/YYYY-MM-DD-short-title.md`, using the intended publication date:

```markdown
---
title: "A thought worth keeping"
---

Your opening paragraph.

## A heading

The rest of your writing.
```

Commit and push. Home lists the latest four posts, and Writing lists all posts by year, newest first. No manual archive updates are needed. Future-dated posts stay hidden until a build after their date; GitHub does not schedule that build automatically. Add `published: false` to the front matter to keep a draft unpublished.

The filename supplies the date and URL slug. Keep the slug stable after publishing so existing links keep working. To rename the file while preserving a URL, add `permalink: /writing/original-slug/` to its front matter. Use unique slugs across posts.

## Images

Put images in `assets/images/` (subfolders are fine). In a post:

```liquid
![A useful description of the image]({{ '/assets/images/photo.jpg' | relative_url }})
```

`relative_url` keeps image and internal page links working on both a root domain and a project site. Resize large photos before committing them.

## Optional local preview

With Ruby and Bundler installed, run in this folder:

```sh
bundle install
bundle exec jekyll serve
```

Open http://localhost:4000 (append your `baseurl` if set). Restart the server after changing `_config.yml`. To include drafts/future posts locally, use `bundle exec jekyll serve --drafts --future`.

For a build only: `bundle exec jekyll build`. `_site/` is generated output and is ignored by Git. Normal publishing needs only Markdown and a push; local preview is optional.

## Where things live

- `index.html`: introduction and automatic recent writing list.
- `about.md`, `work.md`: editable standalone pages.
- `writing.html`: automatic chronological archive.
- `_posts/`: dated Markdown posts.
- `_layouts/`: shared document and article markup.
- `_includes/`: navigation and footer.
- `assets/css/main.css`: all styling, including mobile and print rules.
- `_config.yml`: site identity, contact links, and publishing URL.

The site intentionally leaves out categories, tags, analytics, comments, and a CMS.
