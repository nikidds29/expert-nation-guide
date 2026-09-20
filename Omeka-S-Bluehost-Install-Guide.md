# Installing Omeka S on Bluehost — Step-by-Step Guide

This is a repeatable guide for installing Omeka S on a Bluehost shared hosting
account, based on the install carried out for Anatolikis (anatolikis.com). It
includes every snag hit the first time round and how to avoid or fix it.

**What's in the accompanying zip:** this guide, the three module packages
(Common, Log, BulkExport), and a ready-to-use `.htaccess` file. See the file
list at the very end.

---

## 0. Before you start

Check two version numbers first:

- **PHP version**: in Bluehost, go to your site's dashboard → **Advanced** →
  **MultiPHP Manager** (or check under Websites → your site → Settings).
  Omeka S needs **PHP 8.1+** (8.4+ is fine from Omeka S 4.2 onward).
- **Omeka S version**: download the latest release zip from
  https://omeka.org/s/download/. This guide was written against **Omeka S
  4.2.1**.

Also work out which folder is your site's actual **docroot** (the folder
Apache actually serves). On Bluehost, a site's dashboard has a **Files &
Access** tab that shows this — it is *not* always `public_html` on its own.
If the site was renamed after setup, the folder often still uses the old
domain name (this tripped us up: "Anatolikis" served out of
`public_html/levanatolia.com`, the site's original domain).

---

## 1. Create the database and database user (cPanel)

Use cPanel's **MySQL Databases** tool — not phpMyAdmin. On Bluehost,
phpMyAdmin only manages databases that already exist; it has no "create
database" option.

1. In cPanel, find **MySQL Databases** (search for it, or find it via
   "Manage Databases").
2. Under **Create New Database**, give it a name (e.g. `omekas`) and click
   Create. cPanel will prefix it with your account prefix automatically,
   e.g. `xiwyhnmy_omekas`.
3. Scroll down to **MySQL Users** → **Add New User**. Enter a username,
   click **Generate Password**, and save the generated password somewhere
   safe (you'll need it in step 3).
4. Scroll to **Add User to Database**, pick the user and the database you
   just made, click **Add**, then on the next screen check **All
   Privileges** and click **Make Changes**.

**If you forget the database name later:** go back to MySQL Databases and
look at the **Privileged Users** column — it shows which database your
username is attached to.

---

## 2. Upload and extract Omeka S

1. In cPanel **File Manager**, navigate to your site's docroot folder (see
   step 0).
2. Upload the Omeka S zip file.

   > **Watch for this:** if you upload the zip via drag-and-drop of an
   > unzipped folder (rather than the zip file itself), or if your browser
   > mangles it in transit, it can land on the server as a generic text
   > file instead of a zip. If File Manager shows it with no `.zip`
   > extension or as file type `text/x-generic`, just rename it to add
   > `.zip` back — Extract will then work normally.

3. Right-click the zip → **Extract**.
4. You may see a leftover `__MACOSX` folder after extraction — this is
   harmless Mac zip metadata and safe to delete. If you also see a
   duplicated folder (e.g. two "omeka-s" folders), check which one actually
   contains the real application files (`application/`, `config/`,
   `index.php` etc. directly inside it) and delete the empty/duplicate one.
5. Make sure the resulting Omeka folder ends up **inside your site's real
   docroot** (see step 0) — e.g. `public_html/yoursite.com/omeka`, not just
   `public_html/omeka`, if your docroot is a subfolder.

---

## 3. Configure the database connection

1. In File Manager, go into the Omeka folder → `config/` → open
   `database.ini` with **Edit** (plain text editor, not Code Editor).
2. It will look empty/blank apart from the field labels — that's normal for
   a fresh template, not an error. Fill in the four lines exactly like this
   (using your own values from step 1):

   ```ini
   user     = "xiwyhnmy_your_db_user"
   password = "the-generated-password"
   dbname   = "xiwyhnmy_omekas"
   host     = "localhost"
   ```

3. Save.

---

## 4. Create the `.htaccess` file — **do not skip this**

This was the single biggest blocker last time. Some zip tools strip
dotfiles (files starting with `.`) when packaging or transferring, so the
Omeka zip can arrive on the server **without** `.htaccess` or even the
`.htaccess.dist` template it's supposed to ship with.

**Symptom:** the installer loads fine at `index.php` directly, but
`/omeka/admin`, `/omeka/install`, or any "virtual" Omeka URL returns a raw
Apache **404 Not Found** page (not Omeka's own themed 404 — a plain server
error page). This means Apache itself has no rewrite rules to hand the
request to Omeka's front controller.

**Fix:**

1. In File Manager, go to the Omeka folder root and check whether
   `.htaccess` or `.htaccess.dist` already exists. Toggle "Show Hidden
   Files (dotfiles)" in File Manager's Settings if you don't see it.
2. If neither exists, create a new file named exactly `.htaccess` (make
   sure it starts with the dot — a file named `htaccess` without the
   leading dot will *not* work and Apache will ignore it).
3. Paste in the contents of `htaccess-for-omeka.txt` from the accompanying
   zip (rename it to `.htaccess` once uploaded — see the note in that file).
4. Save, then try `/omeka/admin` or `/omeka/install` again.

---

## 5. Set folder permissions

1. In File Manager, right-click the Omeka `files` folder (the one directly
   inside the Omeka install, not a subfolder or file within it) → **Change
   Permissions**.
2. It needs to be writable by the web server — **755** is Bluehost's
   default and usually already sufficient; **775** is more permissive
   (adds group write) and is sometimes needed if uploads/derivatives fail.
   Check what it's currently set to before changing it — it was already
   correct (775) last time, so no change was actually needed.

---

## 6. Run the web installer

1. Visit `https://yourdomain.com/omeka/install` (adjust the path to match
   wherever you put the Omeka folder).
2. Follow the wizard: set your admin username/email/password, and your
   site's general settings.
3. Once done, log in at `/omeka/admin`.

---

## 7. Install modules

Modules go in the Omeka install's `modules/` folder, one subfolder per
module, matching the module's own name (e.g. `modules/Common/`,
`modules/Log/`, `modules/BulkExport/`).

**Order matters for BulkExport** — it depends on Common and Log, so install
those two first:

1. Upload `Common-3.4.90.zip` into `modules/`, right-click → Extract, then
   delete the zip (and any `__MACOSX` folder) once extracted.
2. Repeat for `Log-3.4.40.zip`.
3. Repeat for `BulkExport-3.4.40.zip`.
4. Go to **Admin → Modules** and install/enable them in that same order:
   Common → Log → BulkExport.

**Problem we hit and fixed:** an earlier copy of the BulkExport zip had been
repackaged incorrectly, so its files were nested inside a folder literally
named `BulkExport.zip` instead of `BulkExport`. Extracting it produced
repeated errors like:

```
checkdir error: BulkExport.zip exists but is not directory
              unable to process BulkExport.zip/composer.lock.
```

This happens because the extractor tries to create a directory with the
same name as the zip archive file sitting right next to it — a name
collision. The `BulkExport-3.4.40.zip` included in this package has been
re-verified (downloaded fresh from the official GitLab/GitHub release and
checked) and has the correct internal structure (a single top-level
`BulkExport/` folder), so this shouldn't recur — but if you ever download a
module zip from somewhere else and hit this exact error message, that's the
cause: delete the bad extraction remnants and the zip, then re-extract a
correctly-packaged copy.

**What BulkExport gives you:** CSV/JSON/other export, including
public-facing export URLs (e.g. appending `.csv` to a public item URL,
depending on configuration) — this is what enables site visitors to export
data from the public side, not just admins.

**Other modules needing a server path** (if you install these too): **File
Sideload** and **Exports** both ask for an absolute *server filesystem
path* in their settings (not a URL) — e.g. something like
`/home1/xiwyhnmy/public_html/yoursite.com/sideload` — pointing at an
already-created, writable folder. Create the folder first in File Manager,
then paste its full server path into the module's settings field.

---

## 8. (Optional) Install the Schema.org vocabulary

In **Admin → Vocabularies → Add new vocabulary**, you need a Label,
Namespace URI, a prefix, and either an uploaded file or a URL in one of:
Autodetect, JSON-LD, N-Triples, RDF-XML, or Turtle format.

**Problem we hit:** the official current schema.org file
(`https://schema.org/version/latest/schemaorg-current-https.ttl`) has grown
very large over successive releases (now bundling many extensions), and
imports of it can fail on shared hosting — even if it worked previously
with an older, smaller version of the file.

**Fix / workaround:** use a smaller, curated snapshot instead, such as the
Linked Open Vocabularies (LOV) version:

```
https://lov.linkeddata.es/dataset/vocabs/schema/versions/2020-03-10.n3
```

(Format: Autodetect or N-Triples — it's an N3/Turtle-family file.) This
gives you the core schema.org classes and properties without the full
current bundle.

**If an import fails and you want to see the real error:** Omeka doesn't
always log to a file you can easily find on shared hosting. The reliable
way to see the underlying PHP error is to temporarily flip
`.htaccess`'s environment setting to development mode:

```
SetEnv APPLICATION_ENV "development"
```

Reproduce the error, look at the raw error output in the browser (or the
failing request's response body via DevTools → Network), then **switch it
back to `"production"` afterwards** — development mode should never be left
on.

---

## 9. (Optional) Using "item stubs" to create linked records inline

On any property using the **Resource** data type, the item-selection
drawer has a **"Create an Item"** option, letting you create a new linked
item without leaving the form you're on.

**Problem we hit:** clicking "Create an Item" failed with a generic
"Something went wrong" message.

**Cause:** the *parent* item (the one you're creating the stub from) hadn't
been saved yet — it had no ID, so there was nothing for the new stub to
attach to. **Fix:** save the parent item first (even as a draft/first pass),
then use "Create an Item" on it — the stub feature only works on
already-saved items.

---

## Troubleshooting quick reference

| Symptom | Likely cause | Fix |
|---|---|---|
| `/admin` or `/install` gives a raw Apache 404, but `index.php` works directly | Missing `.htaccess` | Create `.htaccess` per step 4 |
| Uploaded zip shows as a text file, no `.zip` extension | Upload/transfer stripped the extension | Rename to add `.zip` back |
| Module zip extraction gives "checkdir error: X.zip exists but is not directory" | Zip's internal folder is named `X.zip` instead of `X` | Re-download/re-package with the correct top-level folder name |
| "Something went wrong" creating an item stub | Parent item not saved yet | Save the parent item first |
| Schema.org Turtle import fails / reverts to Notation3 | Official file too large for shared hosting | Use the LOV snapshot URL instead |
| Can't see the real PHP error anywhere | No accessible Omeka error log | Temporarily set `APPLICATION_ENV` to `development` in `.htaccess`, reproduce, then switch back to `production` |
| Module needs a "directory path" setting (File Sideload, Exports) | Wants an absolute server path, not a URL | Create the folder in File Manager first, paste its full server path |

---

## Files included in this package

- **`Omeka-S-Bluehost-Install-Guide.md`** — this guide
- **`htaccess-for-omeka.txt`** — the working `.htaccess` content; upload it,
  then rename it to `.htaccess` (with the leading dot) once it's on the
  server — see step 4
- **`Common-3.4.90.zip`** — required dependency module, install first
- **`Log-3.4.40.zip`** — required dependency module, install second
- **`BulkExport-3.4.40.zip`** — the export module (public + admin CSV/JSON
  export), install third; this copy has been re-verified to have the
  correct internal folder structure

Still outstanding from our last session, not covered here: replicating this
same vocabulary/resource-template setup on a second Omeka S site, and
surfacing the public CSV export links on the site itself rather than
requiring visitors to guess the URL — happy to write that up next time you're
ready for it.
