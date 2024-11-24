---
title: "Showing Likes using Bluesky"
description: "how to show likes on your blog posts using bluesky"
pubDate: "Nov 22 2024"
published: true
heroImage: "/src/assets/blog-placeholder-3.jpg"
tags: ["setup"]
---

You can show likes on your blog posts using bluesky.

## How it works

Set the `BLUESKY_IDENTIFIER` in your `src/config.json` file to your bluesky handle (without the `@`).

Then just post a link to your blog post on bluesky and likes will be shown on your blog posts, looking something like this:

![likes]($assets/likes.png)

Note that no like button is shown if there is no post on bluesky linking to your blog post.

Likes are both server-side rendered on build and updated on the client when you navigate to the page 
(so they work without javascript, but might be a bit outdated).

See a live example below: