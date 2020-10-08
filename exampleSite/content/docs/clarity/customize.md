---
title: "Customization"
weight: 14
---

## Configuration

If set, jump over to the `config.toml` file and start [configuring](#configuration) your site.

This section will mainly cover settings that are unique to this theme. If something is not covered here (or elsewhere in this file), there's a good chance it is covered in [this Hugo docs page](https://gohugo.io/getting-started/configuration/#configuration-file).

### Global Parameters

These options set global values that some pages or all pages in the site use by default.

| Parameter | Value Type | Overidable on Page |
|:---- | ---- | ---- |
| author | string | no |
| twitter | string | no |
| largeTwitterCard | boolean | no |
| ga_analytics | string | no |
| description | string | yes |
| introDescription | string | no |
| numberOfTagsShown | integer | no |
| fallBackOgImage | file path (string) | no |
| codeMaxLines | integer | yes |
| codeLineNumbers | boolean | yes |
| mainSections | array/string | no |
| centerLogo | boolean | no |
| logo | file path (string) | no |
| mobileNavigation | string | no |
| figurePositionShow | boolean | yes |
| figurePositionLabel | string | no |
| customCSS | array of file path (string) | no |
| customJS | array of file path (string) | no |
| enforceLightMode | boolean | N/A |
| enforceDarkMode | boolean | N/A |
| titleSeparator| string | no |
| comment | boolean | no |

### Page Parameters

These options can be set from a page [frontmatter](https://gohugo.io/content-management/front-matter#readout) or via [archetypes](https://gohugo.io/content-management/archetypes/#readout).

| Parameter | Value Type | Overrides Global |
|:---- | ---- | ---- |
| title | string | N/A |
| date | date | N/A |
| description | string | N/A |
| draft | boolean | N/A |
| featured | boolean | N/A |
| tags | array/string | N/A |
| categories | array/string | N/A |
| toc | boolean | N/A |
| thumbnail | file path (string) | N/A |
| featureImage | file path (string) | N/A |
| shareImage | file path (string) | N/A |
| codeMaxLines | integer | yes |
| codeLineNumbers | boolean | yes |
| figurePositionShow | boolean | yes |
| figurePositionLabel | string | no |
| comment | boolean | no |

### Modify links menu

To add, remove, or reorganize top menu items, [edit this YAML file](https://github.com/chipzoller/hugo-clarity/blob/master/exampleSite/data/menu.yaml). These menu items also display any categories (taxonomies) that might be configured for articles.

### Social media

To edit your social media profile links, [edit this YAML file](https://github.com/chipzoller/hugo-clarity/blob/master/exampleSite/data/social.yaml).

If you wish to globally use a [large Twitter summary card](https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/summary-card-with-large-image) when sharing posts, set the global parameter `largeTwitterCard` to `true`.

### Search engine

If using Google Analytics, configure the `ga_analytics` global parameter in your site with your ID.

### Blog directory

Edit the `config.toml` file and change the `mainSections` key. Values will be directories where the blogs reside.

```yaml
[params]
...
mainSections = ["posts", "docs", "blogs"]
...
```

For more info, see the [Hugo docs](https://gohugo.io/functions/where/#mainsections).

### Mobile menu positioning

The navigation menu when mobile browsing can be configured in `config.toml` to open right or left depending on preference. The "hamburger" menu icon will always display in the upper right hand corner regardless.

```yaml
[params]
...
mobileNavigation = "left" # Mobile nav menu will open to the left of the screen.
...
```

### Tags and Taxonomies

#### Show number of tags

The number of tags and taxonomies (including categories) that should be shown can be configured so that any more than this value will only be accessible when clicking the All Tags button. This is to ensure a large number of tags or categories can be easily managed without consuming excess screen real estate. Edit the `numberOfTagsShown` parameter and set accordingly.

```yaml
[params]
...
numberOfTagsShown = 14 # Applies for all other default & custom taxonomies. e.g categories, brands see https://gohugo.io/content-management/taxonomies#what-is-a-taxonomy
...
```

#### Number of tags example

![Tags](https://github.com/chipzoller/hugo-clarity/blob/master/images/tags.png)

<!-- mark -->

### Table of contents

Each article can optionally have a table of contents (TOC) generated for it based on top-level links. By configuring the `toc` parameter in the article frontmatter and setting it to `true`, a TOC will be generated only for that article. The TOC will then render under the featured image.

#### Table of contents (TOC) example

![Article table of contents](https://github.com/chipzoller/hugo-clarity/blob/master/images/article-toc.png)

### Custom CSS and JS

To minimize HTTP requests per page, we would recommend loading CSS styles and JavaScript helpers in single bundles. That is to say, one CSS file and one JavaScript file. Using Hugo minify functions, these files will be minified to optimize the size.

Going by the above 👆🏻 reason, we recommend adding custom CSS and JS via [this custom SASS file](https://github.com/chipzoller/hugo-clarity/blob/master/assets/sass/_custom.sass) and [custom JavaScript file](https://github.com/chipzoller/hugo-clarity/blob/master/assets/js/custom.js).

However, sometimes you may need to load additional style or script files. In such cases, you can add custom `.css` and `.js` files by listing them in the `config.toml` file (see the snippet below). Similar to images, these paths should be relative to the `static` directory.

```yaml
[params]
...
customCSS = ["css/custom.css"] # Include custom CSS files
customJS = ["js/custom.js"] # Include custom JS files
...
```

> __Pro Tip__: You can change the theme colors via the [this variable's SASS file](https://github.com/chipzoller/hugo-clarity/blob/master/assets/sass/_variables.sass)

### Forcing light or dark mode

By default, sites authored using Clarity will load in the browser with the user's system-wide settings. I.e., if the underlying OS is set to dark mode, the site will automatically load in dark mode. Regardless of the default mode, a UI control switch exists to override the theme mode at the user's discretion.

In order to override this behavior and force one mode or another, add either `enforceLightMode` or `enforceDarkMode` to your `config.toml` file. If neither value is present, add it.

To enforce Light Mode by default, turn `enforceLightMode`  to `true`.

To enforce Dark Mode by default, turn `enforceDarkMode`  to `true`

```yaml
[params]
...
enforceLightMode = true # Force the site to always load in light mode.
...
```

Please note that you cannot enforce both modes at the same time. It wouldn't make sense, would it?

> ⚠️ Please also note that the mode toggle UI will remain in place. That way, if a user prefers dark mode, they can have their way. The best of both worlds.

### I18N

This theme supports Multilingual (i18n / internationalization / translations)

The `exampleSite` gives you some examples already.
You may extend the multilingual functionality by following the [official documentation](https://gohugo.io/content-management/multilingual/).

Things to consider in multilingual:

* **supported languages** are configured in [config/_default/languages.toml](./exampleSite/config/_default/languages.toml)
* **add new language support** by creating a new file inside [i18n](./i18n/) directory.
  Check for missing translations using `hugo server --i18n-warnings`
* **taxonomy** names (tags, categories, etc...) are translated in [i18n](./i18n/) as well (translate the key)
* **menus** are translated manually in the config files [config/_default/menus/menu.xx.toml](./exampleSite/config/_default/menus/)
* **menu's languages list** are semi-hardcoded. You may chose another text for the menu entry with [languageMenuName](./exampleSite/config.toml). Please, do better and create a PR for that.
* **content** must be translated individually. Read the [official documentation](https://gohugo.io/content-management/multilingual/#translate-your-content) for information on how to do it.

**note:** if you do NOT want any translations (thus removing the translations menu entry), then you must not have any translations.
In the exampleSite that's as easy as removing the extra translations from the `config/_default/...` or executing this onliner:

```
sed '/^\[pt]$/,$d' -i config/_default/languages.toml   &&   rm config/_default/menus/menu.pt.toml
```

### Hooks

Clarity provides some hooks for adding code on page.

If you need to add some code(CSS import, HTML meta or similar) to the head section on every page, add a partial to your project:

```
layouts/partials/hooks/head-end.html
```

Similar, if you want to add some code right before the body end, create your own version of the following file:

```
layouts/partials/hooks/body-end.html
```

### Comments

Clarity supports Hugo built-in Disqus partial, you can enable Disqus simply by setting [`disqusShortname`](https://gohugo.io/templates/internal/#configure-disqus) in your configuration file.

> ⚠️ `disqusShortname` should be placed in root level of configuration.

You can also create a file named `layouts/partials/comments.html` for customizing the comments, checkout [Comments Alternatives](https://gohugo.io/content-management/comments/#comments-alternatives) for details.