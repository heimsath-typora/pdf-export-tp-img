# pdf-export-tp-img

A PDF export script for Typora that adds a title page (tp) with an easy way to add an image for the title page (img) - all in a single script for Typora's export settings.

## Installation / Setup

1. Open Typora's **Preferences** (Settings) and go to the **Export** tab.
2. Create a new custom PDF export preset (or edit an existing one).
3. Basic settings like **Paper Size** and **Theme** can stay at whatever you already use.
4. **Page Break Between Top Headings** - your call, doesn't matter for this script either way.
5. **Header** and **Footer** - recommended to fill in as follows:
   - Header: `${title}, ${author}, ${version} ${date}`
   - Footer: `Seite ${pageNo} von ${totalPages}   ${license}`

   These are exactly the same YAML front matter fields (`title`, `author`,
   `version`, `date`, `license`) that fill in the title page itself - plus
   Typora's built-in `${pageNo}`/`${totalPages}` page-number variables.
   That means changing a value once in the YAML front matter (e.g. bumping
   `version` or `date`) keeps the title page and every page's header/footer
   in sync automatically - no need to update it in multiple places. Feel
   free to adjust wording/language, or leave both fields empty if you don't
   want a header/footer at all.
6. **Author** - leave empty; the script reads the author from the YAML front matter instead.
7. **Append Extra Content** (the field that lets you add custom HTML/CSS to the exported `<body>`) - paste the full script from this repository into this field. This is the actual copy-paste target for the script.
8. Important: enable **"Read and overwrite export settings from YAML front matters"**. Without this, none of the `${...}` placeholders above - neither on the title page nor in the header/footer - will get filled in.
9. Everything else (e.g. automatically opening the exported file) is personal preference.

## Usage

1. Add a YAML front matter block to the top of your Markdown document, e.g.:

```yaml
   ---
   title: ""
   author: ""
   description: ""
   descriptionSub: ""
   date: ""
   license: ""
   version: ""
   contact: ""
   licenseLink: ""
   ---
```

   `title` is the only required field - without it, no title page is generated.
   All other fields are optional. See the script's own comments for details,
   including how the cover image (filename containing `TP_Image`) is detected.

   Note: this block is also documented directly in the script's comments -
   if the two ever drift apart, the script's comment is the source of truth.

2. In Typora, go to **File > Export** and select the custom PDF export preset you created above.
3. That's it - the title page is generated automatically, and header/footer/title page all stay in sync via the YAML values.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Copyright (c) 2026 Norbert Heimsath

Developed with assistance from [Claude](https://claude.com) (Anthropic).
