Skeleton for EHRI National Node websites
========================================

This is a work-in-progress example EHRI National Node theme, multilingual for English and Welsh
(apologies to Welsh speakers for the incorrect translations.)

To adapt this theme, fork the repository and change:

- things relating to the languages in `config.yaml`
- the equivalent translations in `i18n/cy.yaml`
- files in the content directory ending with `.cy.md`

See the [theme README](https://github.com/EHRI/ehri-nn-hugo-theme) for more info on content types and shortcodes
as they become available.

---

## Running

Install Hugo version 0.129.0 or later, as per the instructions [here](https://gohugo.io/installation/): .

Check out this repository and its submodules:

    git clone --recurse-submodules

From inside the repository directory, run the Hugo server:

    hugo server

The site should be created and available at localhost:1313.

## Setting up the base URL

One pitfall can be adding links/images where the URL does not include the site's base URL. This 
is not a problem is the site is eventually hosted at the root of a domain (e.g. https://example.com), but is if you want to
say, view it on Github pages, with the included Github Action. To test this locally you can use:

    hugo server --baseURL localhost:1313/test

The site will be available at that location with the base path `/test` and you can check everything works correctly.

## Updating the theme

Most of the styling and templates in the sample site come from the Hugo theme, which is a [separate project](https://github.com/EHRI/ehri-nn-hugo-theme)
that is included as a submodule. If the theme is updated and you want the changes reflected in your site, you need to update the theme submodule by running:

    git submodule update --remote --merge

## Multilingual Content

There are several aspects to providing translations for multilingual sites:

* the `config.yaml` file contains a `defaultContentLanguage` setting, which should be set to the default language for the site.
* the `i18n` directory contains a file for each language, e.g. `en.yaml` and `cy.yaml`. These contain translations for strings used in the theme.
* the `content` directory contains a file for each page, e.g. `index.md` and `index.cy.md`. These contain the content for each page, and should be translated into each language.
* for data-driven pages such as Services and Partners, the `data` directory contains a file for each page, e.g. `services.yaml` and `services.cy.yaml`.
  This data structures need to be duplicated for each language, but the textual content can be translated.

## Adding new pages

To add a new page, create a new file in the `content` directory. The file should have a `.md` extension and contain
frontmatter at the top of the file, which is a YAML block surrounded by `---` lines. The frontmatter should contain
at least the page title, e.g.

    ---
    title: Some Info
    ---

    Hello, this is a new page containing some information.

If the file is named `some-info.md` then the page will be available at the URL `/some-info/` on the site. If your site is multilingual
you should also create a file with the same name but with the non-default language code in the file name, e.g. `.cy.md`, and
translated content.

## Creating a menu entry for the new page

The various menus are defined in the `config.yaml` file. To add a new entry to the main menu, add a new entry to the `menu.main` list, e.g.

    menu:
      main:
        - identifier: some_info
          pageRef: /some-info/
          weight: 80

Here, the `identifier` is the unique ID for a menu entry, `pageRef` is the URL of the page, which includes the language prefix 
for translated pages, and `weight` is the position of the entry in the menu.

For the entry to appear there must be a corresponding translated entry in the `i18n/[LANG-CODE].yaml` file, e.g.

    some_info:
      other: Some Info

_NB: English i18n labels are provided with the theme. However, if you add new keys (such as menu `identifiers`) you
will need to create a new `en.yaml` file in the `i18n` directory and add the new keys there._

To add a translated menu entry repeat the info with a different `pageRef` under the `languages/[LANG-CODE]` setting, e.g:

    languages:
      cy:
        menu:
          main:
            - identifier: some_info
              pageRef: cy/some-info/
              weight: 80

Likewise, provide the translated label in the `i18n/[LANG-CODE].yaml` file, e.g.

    some_info:
      other: Rhywfaint o wybodaeth

