# Expert Nation Omeka User Guide

Source for the workshop participant guide, published via GitHub Pages.

Live site: _add the Pages URL here once it's enabled, e.g. https://nikidds29.github.io/expert-nation-guide/_

## Structure

```
index.md                                   Home
modules/
  01-mapping-entities.md                   Module 1 (hidden until ready — built last)
  02-the-omeka-s-universe.md               Module 2 (parent page)
  the-omeka-s-universe/
    items.md
    item-sets.md
    resource-templates.md
  03-advanced-queries.md                   Module 3
  04-organising-person-records.md          Module 4
  05-adding-person-records.md              Module 5 (parent page)
  adding-person-records/
    01-associated-person.md  ... 16 sub-template pages
assets/
  images/
```

## Adding a new page

1. Create a Markdown file wherever makes sense in `modules/`.
2. Add front matter at the top:
   ```
   ---
   layout: default
   title: Your Page Title
   nav_order: 4
   ---
   ```
3. To nest it under an existing module, add `parent: "Exact Title Of Parent Page"`
   to its front matter, and add `has_children: true` to the parent page's own
   front matter. **The `parent:` value has to match the parent page's `title:`
   exactly, character for character** — this is the one thing that breaks
   silently if you're not careful (see "If the structure changes" below).
4. Put any screenshots in `assets/images/` and reference them with:
   `![Description of the screenshot](../assets/images/your-file-name.png)`
5. Commit or upload the changes — the live site rebuilds automatically within a
   minute or two.

To hide a page while you're still drafting it, add `nav_exclude: true` to its
front matter — it stays in the repo and is reachable by direct link, but won't
appear in the site menu.

## If the structure changes

- **Reordering** modules or pages: just change the `nav_order` number. Top-level
  modules are numbered 10, 20, 30… and sub-pages 1, 2, 3… within their own
  module on purpose, so you can slot a new one in later (e.g. 25) without
  renumbering everything else.
- **Renaming a module that has sub-pages**: update its `title:`, then update the
  `parent:` line in *every one of its children* to match the new title exactly.
  Miss one and that child page doesn't error — it just quietly drops out of the
  menu (it still exists at its URL, just orphaned from the nav). Search the repo
  for the old title text before renaming to catch every reference.
- **Promoting or demoting a page** (e.g. turning a sub-part into its own
  top-level module, or the reverse): this is a front-matter-only change — add or
  remove its `parent:` line and adjust `has_children:` on whichever page is now
  the parent. The file doesn't need to move to a different folder for the site
  to work; moving it is just for your own tidiness when browsing the repo.
- **Renaming a file**: changes that page's URL (unless you set a custom
  `permalink:`), so anything already linking or bookmarked to the old URL
  breaks. Fine to do freely before you've shared links widely; worth avoiding
  once participants have the guide open during a workshop.
- **Deleting a page**: just delete the file. Nothing else in the site errors,
  but any other page that linked to it will now contain a dead link — Jekyll
  doesn't check for or warn about broken internal links, so that's on you to
  catch by eye.
