---
title: "page"
abbreviation: "page"
description: "Add a description for this page. It will appear here, under the page title."
primaryURL: /contact
primaryAction: contact
headerButton: false
eleventyNavigation:
  key: Page
  order: 1
---

**Front Matter**
Set the page `title:` and `description:` for each page that you wish to create.

If desired, you can add an action button underneath the `<h1>` and `<p>` by setting `headerButton: true` and setting `primaryURL` and `primaryAction`.

To force the navigation order, set `order` to be a unique value:

```json
eleventyNavigation:
  order: 1
```

## Typography

Below are included typography enhancements designed to render Markdown in a more visually pleasing manner. All styles utilize Bootstrap's native styling. You can read about Bootstrap's available typography and text styles in their documentation: [typography](https://getbootstrap.com/docs/5.3/content/typography/ "Link to Bootstrap's documentation on typography") and [text](https://getbootstrap.com/docs/5.3/utilities/text/ "Link to Bootstrap's documentation on text").

>This is a blockquote, quoting myself
>> With a caption
