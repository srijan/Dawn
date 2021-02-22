# Dawn Customized by srijan

* This repo has the dawn theme customized for [my blog](https://www.srijn.net/).
* Customizations released under the MIT license.
* For the original readme, scroll down.

## Changes done

### Generic changes

* [x] Make content area wider on index and post pages
* [x] Host jquery locally
* [x] Include prism (hosted locally), tomorrow night theme, limited languages
* [x] Group posts list on index page by year (but see limitation below)
* [x] Add year in posts list in related content box and tags pages (but not on
      index page)
* [x] Add icon for github
* [x] On index page: move the logo / logo-title to center of the page and make
      it bigger
* [x] Move navigation from center to the right
* [x] Link directly to RSS instead of opening in feedly
* [x] Remove author card and facebook/twitter share buttons from bottom of posts

### Very specific to my site

* [x] Add Isso comments, css customization (with dark mode), and add attribution
      (powered by ghost and isso)
* [x] Add github and linkedin links to the bottom of the page (hardcoded urls)

## Changes TODO / Limitations

* [ ] Dark mode toggle at the top
* [ ] Dark mode toggle for code highlights
* [ ] Fix pagination of posts.

  Pagination (load more) is broken because of group by year on index page.
  I've set `posts_per_page` to `100` to work around this for now.

* [ ] Move the search button to the right if members are enabled
* [ ] Social links for github and linkedin are hardcoded
* [ ] Even wider code area. I tried doing this simply, but it broke mobile view.
* [ ] Maybe remove the dependency on jquery?

# Dawn

A highly functional theme that adapts to the reader's preferences. Let them read, search, subscribe, navigate, and more with ease. Completely free and fully responsive, released under the MIT license.

**Demo: https://dawn.ghost.io**

&nbsp;

# Instructions

1. [Download this theme](https://github.com/TryGhost/Dawn/archive/master.zip)
2. Log into Ghost, and go to the `Design` settings area to upload the zip file

# Search

1. Navigate to the `Integrations` and click on `Add custom integration`. 
2. Copy the content API key; this will be used to fetch posts from your site.
3. Insert the generated key in `Code injection > Site Header` field.

```html
<script>
    var gh_search_key = 'API_KEY';
    var gh_search_migration = 'v1';
</script>
```

The theme generates an index of posts for highly performant search. The index is updated automatically when posts are added or updated. However, it isn't updated when posts are unpublished or deleted.

To force update the index, increment the search index migration version like `'v2'`.

## Disable Content Search

When your site has lots of posts, including the post content in the index cache ends up with exceeding the browser local storage quota. In that case, disabling content search is recommended. Also make sure increase the migration version to force update the old index.

```html
<script>
    var gh_search_key = 'API_KEY';
    var gh_search_migration = 'v2'; // Increased from v1
    var gh_search_content = false; // Disables content search
</script>
```

# White Logo

If your logo image isn't recognizable in dark mode, you can set a white version of the logo in `Code injection > Site Header` field.

```html
<script>
    var gh_white_logo = 'https://example.com/content/images/white-logo.png';
</script>
```

# Dropdown Menu

The theme looks for a menu item with three dots (`...`) in its URL, and uses that as a dropdown menu toggle. All menu items after the toggle will be added to the dropdown list automatically.

| Label      | URL                       |
|------------|---------------------------|
| More links | https://example.com/...   |
| Sub-1      | https://example.com/sub-1 |
| Sub-2      | https://example.com/sub-2 |

# Development

Styles are compiled using Gulp/PostCSS to polyfill future CSS spec. You'll need [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) and [Gulp](https://gulpjs.com) installed globally. After that, from the theme's root directory:

```bash
# Install
yarn

# Run build & watch for changes
$ yarn dev
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`, which you can then upload to your site.

```bash
yarn zip
```

# PostCSS Features Used

- Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.

# Copyright & License

Copyright (c) 2013-2021 Ghost Foundation - Released under the [MIT license](LICENSE).
