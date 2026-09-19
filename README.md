# Expert Nation Omeka User Guide

Source for the workshop participant guide, published via GitHub Pages.

Live site: _add the Pages URL here once it's enabled, e.g. https://nikidds29.github.io/expert-nation-guide/_

## Structure

Every page in this guide is flat: nothing is nested under anything
else, so the sidebar never uses a collapse/expand arrow that could hide
a page from view. The sidebar order is controlled by each page's
`nav_order`, and the number at the start of each filename in `modules/`
matches that page's `nav_order`, so listing the folder (alphabetically,
the way GitHub does by default) shows the pages in the exact order they
appear in the guide.

```
index.md                                   1. Home
modules/
  02-mapping-entities.md                   2. Mapping Entities: from
                                            Heurist to Omeka
  03-the-omeka-s-universe.md               3. The Omeka-S Universe
  04-items.md                              4. Items
  05-item-sets.md                          5. Item Sets
  06-resource-templates.md                 6. Resource templates
  07-viewing-person-records.md             7. Viewing Person Records
  08-adding-person-records.md              8. Adding Person Records:
                                            creating an item, choosing the
                                            Person template, and a list of
                                            links to each field page below
  09-adding-person-records-early-education.md          8a. Early education
  10-adding-person-records-tertiary-education.md       8b. Tertiary education
  11-adding-person-records-place-of-birth.md           8c. Place of birth
  12-adding-person-records-life-events.md              8d. Life events
  13-adding-person-records-related-persons.md          8e. Related persons
  14-adding-person-records-place-of-death.md           8f. Place of death
  15-adding-person-records-birth.md                    8g. Birth
  16-adding-person-records-military-service.md         8h. Military service
  17-adding-person-records-military-award.md           8i. Military awards
  18-adding-person-records-occupations.md              8j. Occupations
  19-adding-person-records-professional-associations.md  8k. Professional
                                                        Association Memberships
  20-adding-person-records-other-events.md             8l. Other events
  21-adding-person-records-death.md                    8m. Death
  22-adding-person-records-making-a-person-findable.md 8n. Making a
                                            Person Findable
  23-person-vs-associated-person.md        9. Person vs Associated Person
  24-adding-media-items.md                 10. Adding media items
                                            (documents that this
                                            currently doesn't work; see
                                            the tech issues log)
  25-adding-uri-links.md                   11. Adding links to other
                                            resources outside Omeka (URI
                                            links)
  26-advanced-queries.md                   12. Advanced Queries
  27-exporting-records.md                  13. Exporting records
                                            (feature not yet enabled;
                                            screenshot is from a
                                            different Omeka S site)
  28-quick-reference-guide.md              14. Quick reference guide: Labels,
                                            properties and resource templates
assets/
  images/
```

The field pages under Adding Person Records (8a–8n above) are their own
separate top-level pages, exactly like every other page in this guide.
They just happen to sit next to each other in the sidebar because their
`nav_order` values are consecutive. Nothing about them is nested.

Item 10 (`24-adding-media-items.md`) is a special case: it's published
and visible, but it documents a workflow that doesn't currently
function (there is no confirmed way to attach a real media file and
keep it linked from a Person record). The page says so upfront. See
the tech issues log for the underlying problem.

Item 11 (`25-adding-uri-links.md`) is published and covers the
Person template's URI-type fields, but no completed example has been
found in the collection yet, so it's still a page in progress rather
than a finished, verified walkthrough.

Item 13 (`27-exporting-records.md`) documents a feature that hasn't
been enabled on Expert Nation Omeka yet, so its screenshot is from a
different Omeka S site rather than this collection.

## Adding a new page

1. Create a Markdown file in `modules/`, named with a number prefix one
   higher than the last page in the guide (e.g. if the last page is
   `28-quick-reference-guide.md`, the next one is
   `29-your-page-name.md`). This keeps the filename order and the
   sidebar order the same, so anyone browsing the raw repo sees pages
   in the same order the site shows them.
2. Add front matter at the top:
   ```
   ---
   layout: default
   title: Your Page Title
   nav_order: 29
   ---
   ```
   `nav_order` should match the number in the filename.
3. To slot a new page in between two existing ones instead of at the
   end, renumber every file from that point on (both the filename
   prefix and its `nav_order`), and update any links elsewhere in the
   guide that point to a renumbered file (see "If the structure
   changes" below). This guide deliberately doesn't use `parent:` or
   `has_children:` front matter anywhere, so there's no nesting to
   worry about, just this one flat, ordered list.
4. Put any screenshots in `assets/images/` and reference them with:
   `![Description of the screenshot](../assets/images/your-file-name.png)`
5. Commit or upload the changes. The live site rebuilds automatically within a
   minute or two.

To hide a page while you're still drafting it, add `nav_exclude: true` to its
front matter. It stays in the repo and is reachable by direct link, but won't
appear in the site menu.

## Adding a screen recording

Markdown has no native video syntax, but plain HTML works inside a Markdown
file, so a `<video>` tag embedded directly in the page works fine alongside
your regular screenshots. Three ways to host the actual file, roughly in order
of least to most effort:

1. **Drag the video into a GitHub issue or PR comment box** (not the repo file
   uploader). GitHub uploads it and gives you back a URL. Paste that as the
   `src` below. No size planning, no separate account. Try this first.
2. **Upload it into `assets/videos/` in the repo**, same as screenshots go in
   `assets/images/`. Works, but GitHub warns over 50MB and blocks over 100MB
   per file, and a repo full of video slows down every future clone/rebuild.
   Fine for one or two short clips, not for a recording on every page.
3. **Upload to YouTube as "unlisted"** and embed with an `<iframe>` instead.
   No size limit ever, more setup up front. The better long-term answer if
   recordings end up on most modules.

Embed code, once you have a URL from option 1 or 2:

```html
<video controls width="100%">
  <source src="../assets/videos/your-recording.mp4" type="video/mp4">
  Your browser doesn't support embedded video;
  <a href="../assets/videos/your-recording.mp4">download the recording</a> instead.
</video>
```

For a YouTube "unlisted" video (option 3):

```html
<iframe width="100%" height="400" src="https://www.youtube.com/embed/VIDEO_ID"
  title="Description of what the video shows" frameborder="0" allowfullscreen></iframe>
```

For a short, silent interaction (a couple of seconds, a menu opening, a
dropdown appearing) rather than a full walkthrough, an animated GIF is often
easier: it uses the exact same `![alt text](../assets/images/your-file.gif)`
syntax as a still screenshot, no HTML needed. No sound and it compresses worse
than real video, so keep GIFs short.

## If the structure changes

- **Reordering pages**: change the `nav_order` in the page's front matter,
  and rename its file to match (the number prefix should always equal
  `nav_order`). If you're inserting a page in the middle, every later
  page's number shifts up by one, in both its filename and its
  `nav_order`.
- **Renaming a file**: changes that page's URL (unless you set a custom
  `permalink:`), so anything already linking or bookmarked to the old URL
  breaks. Search the repo for the old filename (e.g.
  `grep -rn "old-filename.md" .`) and update every link to the new one.
  Fine to do freely before you've shared links widely; worth avoiding
  once participants have the guide open during a workshop.
- **Deleting a page**: just delete the file. Nothing else in the site errors,
  but any other page that linked to it will now contain a dead link. Jekyll
  doesn't check for or warn about broken internal links, so that's on you to
  catch by eye (the same `grep -rn` search works for this).
