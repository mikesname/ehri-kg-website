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

Install Hugo version 0.111.3 or later.

Run:

    hugo server

The site should be created and available at localhost:1313.

One pitfall can be adding links/images where the URL does not include the site's base URL. This 
is not a problem is the site is eventually hosted at the root of a domain, but is if you want to
say, view it on Github pages, with the included Github Action. To test this locally you can use:

    hugo server --baseURL localhost:1313/test

The site will be available at that location with the base path `/test` and you can test everything works correctly.

TODO: lots more...

