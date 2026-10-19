---
layout: default
title: Adding sources
nav_order: 25.5
---

# Adding sources

Every Person record should say where its information came from. On the Person template, a source is recorded across **two separate fields** that work together:

| Field label         | Property            | What goes in it                                                                 |
| ------------------- | ------------------- | ------------------------------------------------------------------------------- |
| SourceInfo          | `expn:sourceInfo`   | **Which** source: chosen from a drop-down list, or added as a URI link          |
| Source Details text | `expn:sourceDetails` | **Where in** that source: free text, such as a URL, collection and box number, or newspaper title and date |

Think of SourceInfo as naming the source, and Source Details text as the citation that lets someone else find the exact page, file or article again.

## What the source fields look like

![Person record edit screen showing two fields. SourceInfo (Source of information, expn:sourceInfo) has a URI box with a Label box underneath, and a second value showing a drop-down reading "Select term below", with buttons below for plus, URI and SourceInfo. Source Details text (Details on source of information, e.g. URL, Collection & box number, newspaper title & date, expn:sourceDetails) has a single empty text box and an Add value button.](../assets/images/adding-sources-01-fields-blank.png)

The two fields sit next to each other near the end of the Person "Add Item" screen. Underneath SourceInfo are three buttons, and each one adds a different kind of value:

- **SourceInfo** adds a drop-down list of named sources. This is the one to use in most cases.
- **URI** adds a **URI** box and an optional **Label** box, for linking to a source online.
- **+** adds another value of the same kind as the one above it.

Source Details text is an ordinary text box. **+ Add value** adds another box underneath.

## Choosing a source from the list

![The SourceInfo drop-down opened, listing Australian Dictionary of Biography, CRTS Card scan, Department of Veterans Affairs, National Archives of Australia, National Library of Australia, Other, Sancta Sophia College Archives, StudBio, Trove and UniComp, with a scroll bar showing there are more options below.](../assets/images/adding-sources-02-sourceinfo-dropdown.png)

1. Under **SourceInfo**, click the **SourceInfo** button to add a drop-down, or use the one already showing.
2. Click **Select term below** and choose the source. The list is longer than it first looks, so scroll down to see every option.
3. If the source isn't in the list, choose **Other** and name the source in Source Details text.

To link to a source online instead, click the **URI** button, paste the web address into **URI**, and optionally type a short description into **Label**. Whatever is in **Label** displays as the clickable link text instead of the raw web address.

## Adding the source details

In **Source Details text**, type the information someone would need to find the exact item again. The field's own hint gives the main examples:

- a **URL** for an online record
- a **collection and box number** for archival material
- a **newspaper title and date** for a newspaper article

## More than one source

A person's information often comes from several places. Click the **SourceInfo** button again to add another source from the list, and **+ Add value** under Source Details text to add matching details.

{: .note }
The two fields aren't linked to each other: Omeka doesn't know which details belong to which source. When you record more than one source, add them in the same order in both fields, and start each Source Details entry with the source name (for example, "Trove: Sydney Morning Herald, 12 March 1915, p. 8") so each one makes sense on its own.

---

Prepared for Expert Nation Omeka workshop participants.
