---
layout: default
title: Items
parent: The Omeka-S Universe
nav_order: 1
---

# Items

An **item** is Omeka S's word for a single record — one row in the database,
one thing you can open, edit, and search for. In this collection, every
item is built from one of the **17 resource templates** currently in use
(the [Resource Templates](resource-templates.md) page covers all 17), which
falls into two rough groups:

- **Person** — the core biographical record. This is what you'll spend most
  of your time creating and editing, and the record type the rest of this
  guide focuses on.
- **The other 16 templates** — Associated person, Death, Digital media item,
  Educational institution, Eventlet, Life event, Military award, Military
  service, Occupation eventlet, Organisation, Place, Professional
  association member, Relationship, Scholarship award, Schooling, and
  Tertiary study. These aren't stand-alone biographies — each one records a
  single fact, event, or supporting detail (a place, a death, a period of
  military service) that then gets **linked to a Person record** through
  one of the Person template's fields. See the
  [Person Template Field Reference](../property-reference.md) for exactly
  which field links to which of these.

<!--
Nicole — add a screenshot of the Items browse screen (Items list in the
admin sidebar) here, showing a mix of Person and non-Person items, so
participants can see what "everything is an item" actually looks like in
practice.
-->

## Why this matters when you're searching

Because every one of those 17 record types is an item, the main **Items**
browse screen in the admin area — and a plain search — mixes Person records
in with every Life event, Death, Place, and Military service record too.
There's no way to tell, at a glance, whether a result in a general items
list is a full Person or a small supporting record for someone else's
Person record — you have to check which resource template it uses, or
filter by resource template directly.

If you want Person records specifically, filter by resource template
(Person) rather than browsing or searching Items generally — the
[Advanced Queries](../03-advanced-queries.md) page walks through how.
