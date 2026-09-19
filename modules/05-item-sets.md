---
layout: default
title: Item Sets
nav_order: 5
---

# Item Sets

An **item set** is Omeka S's way of grouping items into a named collection,
useful for browsing a defined subset of records instead of everything at
once.

In this collection, item sets are used to group **Person records only**.
None of the 16 supporting record types (Life event, Death, Place, Military
service, and so on) are organised into item sets themselves. They're
linked to a Person instead (see [Items](04-items.md)), and reached from there,
not by browsing an item set directly.

You can see this on the Person template itself: the **isPartOf** field is
what assigns a Person record to an item set. It's the last field on the
Person "Add Item" screen (see the
[Quick reference guide](28-quick-reference-guide.md)), and it's a
link to an Item Set rather than to another Item. See
[Making a Person Findable](22-adding-person-records-making-a-person-findable.md)
for how to set it, and why it needs to be set on every Person record.

<!--
Nicole: this is the one page where I don't have collection-specific detail
yet: which item sets currently exist (their names, and what each one is
for, e.g. a particular project or cohort of people), and a screenshot of
the Item Sets browse screen and/or the isPartOf field being set on a Person
record. Once you drop those in, I'd suggest a short list here along the
lines of:

- **[Item set name]**: [what it's for / which people it covers]
- **[Item set name]**: [what it's for / which people it covers]
-->

## Why this matters

Because item sets only ever hold Person records here, they're a quick way
to browse "everyone in project X" or "everyone in cohort Y" without wading
through Life events, Places, and all the other supporting records that
share the same database. If you're looking for a defined group of people
rather than searching by a specific field, checking whether an item set
already covers that group is often faster than an Advanced Search.
