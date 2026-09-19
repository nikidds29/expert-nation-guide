---
layout: default
title: Introduction
nav_order: 2
---

# Introduction

This guide walks through building and adding to **Person** records in
Expert Nation Omeka: the biographical record at the centre of this
collection, and the fields you'll use to add detail to it, one topic at a
time.

A Person record doesn't hold a person's whole life on its own. It stores
some details directly (name, dates, and so on), and for almost everything
else it links out to a separate, smaller record: a place, a period of
military service, a relationship to someone else. Each of those smaller
records is built from its own **resource template**, which defines
exactly what fields it has. The diagram below shows how they all connect.

![Diagram of the Person record data model: Person at the centre, connected to its linked fields, most backed by their own resource template (Place, Life event and Digital media item each cover more than one field), with External links as the one exception, holding a plain web address rather than a linked item](../assets/images/mapping-entities-data-model.svg)

The rest of this guide works through each of these in turn: what a
resource template is and does ([Resource Templates](06-resource-templates.md)),
then building a Person record field by field
([Adding Person Records](08-adding-person-records.md)).
