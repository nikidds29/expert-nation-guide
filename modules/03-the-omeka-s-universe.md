---
layout: default
title: The Omeka-S Universe
nav_order: 3
---

# The Omeka-S Universe

Collections in Omeka-S are organised around three ideas: **items**,
**item sets**, and **resource templates**. The platform makes a lot more sense once you can see how they fit together,
so before anything else, here's the short version of each, specific to what
this collection actually contains.

- **Items** are the individual records. Every entry in the database, every
  Person, but also every Life event, Death, Place, Military service and so
  on attached to a Person, is an item. This collection currently has 17
  different kinds of item in use.
- **Item Sets** group items together. In this collection, item sets are used
  to collect **Person records only**; the smaller, supporting record types
  (Life events, Places, Military service, and the rest) aren't organised
  into item sets themselves.
- **Resource templates** define what an item looks like: which fields
  appear when you create or edit it. Every item uses exactly one resource
  template. One of the 17 templates, **Person**, is the record type this
  whole guide is built around; the other 16 define the smaller record types
  that get linked to a Person to build out their full biography.

Put together: a **Person** is an **item**, built from the **Person resource
template**, and optionally grouped into an **item set** alongside other
Person records. Everything else you'll come across (a Life event, a Death
record, a Place) is also an item, just built from a different resource
template, and linked *to* a Person rather than filed in an item set of its
own.

The three pages below go through each of these in more detail, with what
they specifically look like in this collection.
