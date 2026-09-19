---
layout: default
title: Life events
nav_order: 54
---

# Life events: linking a Life event record

*Part of [Adding Person Records](05-adding-person-records.md). Read
that page first for how a new record and the Person template work in
general.*

**Life events** is a catch-all field, for anything significant in a
person's life that doesn't already have its own dedicated field on the
Person template, for example moving overseas to a particular country,
taking up a board position at a company, and events like that. A few kinds of event
*do* have their own dedicated field elsewhere on the form: birth,
death, and relationships all do. Those should never be added here
instead, even though the Life events field is technically capable of
recording any of them. See "Which field for which event?" below for the
full picture, and why it matters.

## Adding a Life event

Click the Items icon under **Life events**, then **Create item**, and
set **Resource template** to **Life event** (Class fills in as
`LifeEvent`).

![New item screen scrolled to Life events, with the Items icon highlighted, and the resulting Create item panel showing Title (Required) and Type of life event (Required, empty)](../assets/images/adding-person-records-14-life-event-empty-panel.png)

Title is required, and follows the same
**[Family name], [Initials] : [what the record is about]** format
introduced under
[Early education](adding-person-records-early-education.md), so this
record can be traced back to the Person it belongs to.

**Type of life event** is also required, and is a controlled dropdown
rather than free text. Pick the closest match from the list.

![The Type of life event dropdown open, showing the full list of available event types](../assets/images/adding-person-records-15-life-event-type-dropdown.png)

Note that this list includes **Birth**, **Death** and **Relationships**
among the options. It's technically possible to record any of them
this way. Don't: use the Person template's dedicated
[Birth](adding-person-records-birth.md),
[Related persons](adding-person-records-related-persons.md), and Death
fields instead, for the reasons covered below.

Once Title and Type of life event are done, click **Add and select
item** as before. If a person has more than one Life event to record,
use the **+** button beneath the field (next to **Add value**) to add
another. Each one creates and links a separate Life event record, the
same way.

## Some examples

Things that belong under Life events: the person moved overseas to a
particular country; the person became a board member of a company;
the person was awarded an honorary doctorate. Anything notable that
doesn't already have a dedicated field of its own on the Person
template is fair game here.

## Which field for which event?

Some event types look like they'd belong under Life events but
actually have their own dedicated field, backed by their own property. Using that field
instead of Life events matters, because it's what
makes the record findable later as specifically "this person's birth,"
or "this person's death," rather than just one more entry in a general
list. Use this table to check before creating a record:

| Event | Use this field | Resource template |
|---|---|---|
| Birth | [Birth](adding-person-records-birth.md) | Life event |
| Death | [Death](adding-person-records-death.md) | Death |
| A relationship to another person (marriage, and so on) | [Related persons](adding-person-records-related-persons.md) | Relationship |
| Anything else notable in the person's life | Life events (this page) | Life event |

Birth is the one that catches people out: it uses the *same* Life
event resource template as this field does, so nothing stops you
creating it here by mistake. The only thing that makes it findable as
a birth record specifically is using the Birth field itself. See
[Birth](adding-person-records-birth.md) for why that matters.
