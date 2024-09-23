# Eleventy-bootstrap

This is a template for creating [Eleventy](https://www.11ty.dev "Link to eleventy website") sites using [Bootstrap](https://getbootstrap.com "Link to bootstrap website").

> As of release, this template utilizes the Eleventy 3.0.0-beta.1 release. If you do not wish to use this version, change over to the [**11ty-2**](https://github.com/AdamJ/eleventy-bootstrap.git) branch.

## Installation

Dependencies are installed with `npm install`. Once dependencies are installed, there are additional commands (found under [configuration](#configuration)) for advanced setups.

After installation, you should see the directory structure now containing an `npm_modules` folder, along with a `package-lock.json` file.
> The package-lock.json is excluded so that when you first install dependencies, you will get the latest versions available.

### Directory structure

```json
/eleventy-bootstrap
  /docs
  /node_modules
  /social
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
      navbar-logo.png
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
    index.md
    manifest.json
    sitemap.njk
  .eleventy.js
  .gitignore
  .nvmrc
  .stylelintignore
  .stylelintrc.json
  GitHub_Repo_Card_Template.png
  package-lock.json
  package.json
  README.md
```

## Configuration

This template is configured to use `/src` as the main directory, with `/docs` as the target directory. If you wish to change this, you will need to edit the [`.eleventy.js`](.eleventy.js) file.

### Included libraries

Any dependencies can be updated, removed, and/or replaced as you see fit. If you want to get up and running as quickly as possible, run `npm install` to get the latest versions of each included dependency.

[Bootstrap](#bootstrap) | [Font Awesome](#font-awesome)  |  [Stylelint]()

#### Bootstrap

Bootstrap file is imported through `/src/sass/style.scss` using `/src/sass/_bootstrap.scss`. This file contains `@import "../../node_modules/bootstrap/scss/bootstrap.scss";`, so no scripts are needed to update this dependency. As Bootstrap is a pivotal aspect of this template, removing it is not recommended.

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

#### Stylelint

In order to create consistent and maintainable code, Stylelint is used to process the `.scss` files under `src/sass/`. By default, Stylelint has been configured to ignore Bootstrap and Font Awesome files, as those packages are linted by their respective owners.

[`src/.stylelintrc.json`](/src/.stylelintrc.json)  |  [`src/.stylelintignore`](/src/.stylelintignore)

---

## Building the Site

As an 11ty site, the build is governed by settings under `.eleventy.js`. Each page for the site is built using Nunjucks files located under `src/_generate` and `src/_includes`.

`src/_generate` contains the following:

- `feed.njk`
- `pages.njk`
- `sitemap.njk`
- `socialtemplate.njk`

Each of these files references meta data found in [`meta.js`](src/_data/meta.js) and are generated for use through the Eleventy build process.

The template's pages are broken into manageable parts, and kept under `src/_includes` so that the Eleventy build configuration can located them and included them when referenced. As part of this template, the following files are available:

- `base.njk`

> This file pulls in the footer and sitenav pages using `{% include 'sitenav.njk' %}` and `{% include 'footer.njk' %}` with `{{ content | safe }}` calling content from the `page.njk` file.

- `footer.njk`

> Site footer and references to JavaScript CDN links

- `page.njk`

> The primary template for displaying content from any markdown files under `/src/pages/`. This template is called by the site's content pages using the page `json` file. In the front-matter of `pages.njk`, the `base.njk` layout file is called, completing the page construction process.

- `sitenav.njk`

> Navigation bar for the template

### Sitemap.njk

Located under `src`, [`sitemap.njk`](src/sitemap.njk) needs to have certain meta data available to it to correctly fill in the URL. Under`src/_data/meta.js`, update **siteURL** to your site's URL:

```js
siteURL: "https://www.adamjolicoeur.com"
```

### Meta.js

The [`meta.js`](src/_data/meta.js) file includes a set of data attributes that are referenced by files under `_generate` and `_includes`. Edit these as you see fit in order to properly populate page headings and site meta data.

### Pages

All pages for this template are included under `src/pages/` and are written in Markdown (`.md`) with front-matter dictating the page title and description (called at the time of build and injected into the `page.njk` include).

Additionally, each page references a `pages.json` file which dictates what layout template to use as, well as the **permalink** and **key**.
> The **permalink** is the fixed URL string that is appended to the primary URL (i.e. adamjolicoeur.com/[permalink]).

For reference, this is the method for setting the link: `"permalink": "/{{ page.fileSlug }}/"`.
> If you wish to have these pages reside under `src/pages` but customize the URL string, you can do so by altering the **permalink**.
> Instead of "permalink": "/{{ page.fileSlug }}/" to have `adamjolicoeur.com/contact`, change it to "permalink": "/[pages/\{{ page.fileSlug }}/". Now the URL will be `adamjolicoeur.com/pages/contact`.
