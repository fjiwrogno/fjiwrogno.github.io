# Site Editing Guide

You should rarely need to touch the theme itself. Most updates are just Markdown files and images.

## 1. Profile and site-wide information

Edit:

- `_config.yml`
- `_data/navigation.yml`

Before publishing, check:

- `url`
- `repository`
- email
- GitHub / LinkedIn / Scholar links
- location
- employer
- optional profile photo

For a profile photo, place it at `images/profile.jpg` and set:

```yaml
author:
  avatar: "profile.jpg"
```

## 2. Project pages

Project pages live in:

```text
_portfolio/
```

The current structure is:

- `01-nami.md`
- `02-flamingo.md`
- `03-diffusion-policy.md`
- `04-underwater-robot.md`
- `05-robomaster.md`
- `06-navigation.md`

For every major robot, keep this structure:

1. Overview
2. My contribution
3. System / technical details
4. Representative results
5. Tech stack
6. Video / links

For recruitment, keep the strongest 3–4 systems on the site landing page. Additional projects can still live in `_portfolio`.

### Add project images

Put them under:

```text
images/projects/<project-name>/
```

Then reference them with:

```markdown
![Description]({{ '/images/projects/example/photo.jpg' | relative_url }})
```

### Add a video

For a short local MP4:

```html
<video controls muted playsinline style="width:100%;">
  <source src="{{ '/videos/demo.mp4' | relative_url }}" type="video/mp4">
</video>
```

For longer videos, YouTube or Bilibili embedding is preferable to keeping large video files in Git.

## 3. Blog

Draft first in:

```text
_drafts/
```

To publish, move/rename the file to:

```text
_posts/YYYY-MM-DD-title.md
```

Example front matter:

```yaml
---
title: "Lessons from Debugging In-Flight Transformation"
date: 2026-09-12
categories:
  - Robotics
tags:
  - control
  - real-robot
  - debugging
---
```

Good future topics for this site:

- Building a bidirectional underwater-thruster driver
- Lessons from debugging in-flight transformation
- Why real robots fail differently from simulation
- Notes while learning manipulation / Diffusion Policy
- From aerial robotics to robot learning

## 4. Photos

Place images in:

```text
images/photos/
```

Then edit `_pages/photos.md`.

For larger photo stories, create a blog post instead of putting every image on the main Photos page.

## 5. Publications

Each publication is one Markdown file in:

```text
_publications/
```

Add `paperurl`, `codeurl`, or project links when those become available.

## 6. CV

There is intentionally **no CV page and no downloadable CV PDF** on this site, for privacy reasons. If you ever want one back, re-create `_pages/cv.md`, put the PDF under `files/`, and add a "CV" entry to `_data/navigation.yml`.

## 7. Local preview

Academic Pages recommends Ruby + Bundler for local Jekyll preview. With Ruby installed:

```bash
bundle install
bundle exec jekyll serve
```

Then open:

```text
http://localhost:4000
```

Because the site uses a remote theme, the first build needs network access to retrieve the Academic Pages theme.

## 8. Academic Pages upstream

Framework:
`academicpages/academicpages.github.io`

Pinned theme commit:
`a4386d88512a52499f4cebff515a1bb9b310da9a`

To update the framework later, replace the ref after `@` in `remote_theme` and test the site before publishing.
