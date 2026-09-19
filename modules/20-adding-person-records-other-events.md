---
layout: default
title: Other events
nav_order: 20
---

# Other events: linking an Eventlet record

*Part of [Adding Person Records](08-adding-person-records.md). Read
that page first for how a new record and the Person template work in
general.*

**Other events** is for anything in a person's life that doesn't fit
[Life events](12-adding-person-records-life-events.md) or one of the more
specific fields already covered. Click the Items icon under **Other
events**, then **Create item**, and set **Resource template** to
**Eventlet** (Class fills in as `Event`).

![New item screen scrolled to Other events, with the Items icon, Resource template, Class, and Title all highlighted](../assets/images/adding-person-records-23-other-events-template-panel.png)

**Always use Eventlet here, never Life event.** Using the same
template consistently is what keeps this field distinct and findable
as its own group of records, separate from
[Life events](12-adding-person-records-life-events.md). See "Which field
for which event?" below for how the two compare.

Like Occupations and Professional Association Memberships, a person
can have several Other events, so use the **+** button next to **Add
value** to add more than one.

Title is required, and follows the same
**[Family name], [Initials] : [what the record is about]** pattern
introduced under
[Early education](09-adding-person-records-early-education.md), for
example `Smith, J.H. : Awarded OBE`.

![Zoomed view of the Eventlet panel, showing Type of event, Target person, Target organisation, and Other organisation or entity](../assets/images/adding-person-records-24-other-events-target-panel.png)

Below Title, **Type of event** is a dropdown, and it draws on the
same controlled list of event types as
[Life events](12-adding-person-records-life-events.md)'s **Type of life
event** field. **Target person**, **Target organisation** and **Other
organisation or entity** are worth a closer look too: despite their
names, they're plain free-text fields, not Items-icon links to an
actual Person or Organisation record, so typing a name into Target
person doesn't connect this Eventlet to that person's own record the
way, say, Related persons does. Having named "person" and
"organisation" fields at all suggests Eventlet was built with a
specific use in mind: recording who or what an event involved,
beyond just the Person it belongs to, even though right now that's
captured as text rather than a real link.

Once Title (and whichever other fields apply) are done, click **Add
and select item** as before.

## Which field for which event?

Birth, Death, Related persons, Life events and Other events can look
interchangeable when you're deciding where to record something. Use
this table to check you're in the right place before creating a
record:

| Event | Use this field | Resource template |
|---|---|---|
| Birth | [Birth](15-adding-person-records-birth.md) | Life event |
| Death | [Death](21-adding-person-records-death.md) | Death |
| A relationship to another person (marriage, and so on) | [Related persons](13-adding-person-records-related-persons.md) | Relationship |
| Something else notable in the person's life | [Life events](12-adding-person-records-life-events.md) | Life event |
| Something else notable that specifically involves another named person or organisation | Other events (this page) | Eventlet |
