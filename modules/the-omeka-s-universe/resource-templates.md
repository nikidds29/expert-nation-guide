---
layout: default
title: Resource Templates
parent: The Omeka-S Universe
nav_order: 3
---

# Resource Templates

A **resource template** defines what an item looks like: which fields show
up when you create or edit it, what type each field is (text, dropdown, a
link to another item), and which ones are required. Every item uses exactly
one resource template — it's chosen from the "Resource template" dropdown
at the top of the "Add Item" screen, and everything below it changes to
match.

This collection currently has **17 resource templates** in use. One of them
— **Person** — is the core biographical record this whole guide is built
around. The other 16 each define a smaller, supporting record type that
gets linked to a Person to build out their biography (a place, a death, a
period of military service, and so on).

<!--
Nicole — add the Resource Templates admin list screenshot here (the one
showing Label / Class / Owner for all 17), so participants can see this
list exactly as it appears in the admin sidebar.
-->

| Resource template | What it's for in this collection |
|---|---|
| **Person** | The core biographical record — the record type covered in depth by the rest of this guide. See the [Person Template Field Reference](../property-reference.md) for every field it has. |
| Associated person | A related individual linked to a Person record, as a lighter-weight alternative to a full Person record. |
| Death | The circumstances of a person's death, linked from the Person's Death field. |
| Digital media item | Photographs, PDFs, and other media files linked to a Person — thumbnails, additional photographs, documents, and scanned book entries all use this template. |
| Educational institution | A school or university a person attended, linked from the Person's institution fields. |
| Eventlet | A smaller event in a person's life. |
| Life event | A significant event in a person's life — including, in practice, births. |
| Military award | A specific award or honour received during military service. |
| Military service | Details of a person's military service — rank and company. |
| Occupation eventlet | A specific job or occupation held by a person. |
| Organisation | An organisation record, linked from fields such as Professional Association Memberships. |
| Place | A location, linked from the Person's Place of birth and Place of death fields. |
| Professional association member | A person's membership in a professional association. |
| Relationship | A relationship between two people. |
| Scholarship award | An academic scholarship or award received. |
| Schooling | Details of a person's early/primary education. |
| Tertiary study | Details of a person's university or tertiary education. |

## Why this matters

The resource template an item uses is what determines which fields it has
— so if you're ever unsure why a field is missing (or unexpectedly present)
on a record, checking the resource template selected at the top of the
"Add Item" screen is the first thing to look at. It's also what "Advanced
Queries" filters by when you narrow a search to Person records only: see
[Advanced Queries](../03-advanced-queries.md).
