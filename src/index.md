---
layout: page.njk
title: "Eleventy-bootstrap"
description: "This is a template for creating Eleventy sites using Bootstrap."
---

## Congratulations!

**Congratulations!** As you are seeing this message, you have successfully setup and launched the Eleventy-bootstrap template.

_All of the information contained on this page is duplicated from the `README`. If you'd rather just read that, you can delete everything (except the FrontMatter) from `src/index.md`._

## Configuration

This template is configured to use `/src` as the main directory, with `/docs` as the target directory. If you wish to change this, you will need to edit the `.eleventy.js` file.

### Updating included libraries

After updating dependencies, run `npm install` to get the latest versions of each.

#### Bootstrap

The single Bootstrap file is imported through `/src/sass/style.scss` using `/src/sass/_bootstrap.scss`. This file contains `@import "../../node_modules/bootstrap/scss/bootstrap.scss";`, so no scripts are needed to update this dependency. As Bootstrap is imported using `_bootstrap.scss`, there is no additional CSS file to remove from the site `<head>`.

#### Font Awesome

To update local Font Awesome files, run `npm run config`. This will copy over files from `/node_modules/@fortawesome/fontawesome-free` to your `/src/webfonts` and `/src/sass/fa` directories.

- If you wish to remove Font Awesome from the template, you will need to update the following files:
  - `package.json`
    remove `"@fortawesome/fontawesome-free": "6.4.2",` from the `devDependencies` list
  - `fontawesome.scss`
    delete this file
  - `style.scss`
    remove `@import "fontawesome.scss";`
  - `base.njk`
    remove `<link href="{{ '/css/fontawesome.css' | url }}" rel="stylesheet" />` from the `<head></head>` section
- Run `npm install` to update `/node_modules` and `package-lock.json`, which will remove Font Awesome from both.

## Directory structure
```json
/eleventy-bootstrap
  /node_modules
  /docs
  /src
    /_data
      meta.js
    /_generate
      feed.njk
      pages.njk
      sitemap.njk
      socialtemplate.njk
    /_includes
      base.njk
      footer.njk
      page.njk
      sitenav.njk
    /img
    /pages
      contact.md
      page.md
      pages.json
    /sass
      /fa
      _bootstrap.scss
      _footer.scss
      _page.scss
      _typography.scss
      fontawesome.scss
      style.scss
    /webfonts
    manifest.json
  .eleventy.js
  .gitignore
  .package-lock.json
  package.json
  README.md
```
