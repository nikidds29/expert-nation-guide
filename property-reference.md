---
layout: default
title: Person Template Field Reference
nav_order: 35
---

# Person Template Field Reference

<!--
Nicole — this is the master lookup table: the label a participant sees on the
"Add Item" screen for the Person template, matched to the property name that
shows up in the Advanced Search "Search by value" dropdown. Link to this page
from Advanced Queries and from the Adding Person Records module instead of
repeating the table there.

This is schema/template metadata, not record data — no real person's
information appears here, so it's fine to publish on the public repo.

Built from your screenshots of the Person resource template's edit screen.
I wasn't able to reliably read the timestamp overlay cut off at the bottom of
most of the screenshots, so I couldn't sequence these by capture time as you
asked — instead I've grouped them by subject, which should be more usable as
a lookup table anyway. If you want it in the exact top-to-bottom order the
fields appear on the live form instead, the row order is easy to change —
just say which order and I'll rebuild it.

Three rows below are missing their property term because the screenshot cut
off before showing it — flagged with ⚠️ and listed again at the very bottom
so they're easy to find and fix.
-->

Every field on the Person "Add Item" screen is backed by a property — and
that property's name, not the field's on-screen label, is what you'll see in
Advanced Search's "Search by value" dropdown. This table matches the two up,
so you don't have to hop between the Add Item screen and the search screen to
find the right one.

**Worth knowing before you use this table:**

- **schema:additionalType is reused for two unrelated things.** On the
  Relationship template it holds the relationship type (`wasWifeOf`,
  `wasHusbandOf`...). On the Person template it holds "Person type (special
  flags)" — a completely different vocabulary. Searching by `additionalType`
  without also narrowing by Class or Resource Template will mix both
  together.
- **There appear to be two separate "related person" fields on the Person
  template**: "Related Person(s)" (`schema:relatedTo`) and "Related persons"
  (`expn:relatedPerson`) — different property terms, near-identical labels,
  both linking to other Person items. Worth confirming which one is actually
  in use for spouse/family links before you build a search example around
  either — searching the wrong one will quietly return nothing.

## Identity & naming

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Title | `dcterms:title` | Text (required) | Full name, format: [Family name], [Given name(s)] |
| Family name | `schema:familyName` | Text | |
| Given name(s) | `schema:givenName` | Text | |
| Initials | `expn:initials` | Text | Form A.B., period after each initial |
| Alternate name(s)/title(s) | `schema:alternateName` | Text | Simple alternatives, no extra metadata |
| Married name | `expn:marriedName` | Text | |
| Naming note | `expn:namingNote` | Text | Nee, AKA, Formerly, Now |
| Honorific | `schema:honorificPrefix` | Dropdown | Prof, Dr, Sir — recommend omitting Mr/Mrs/Ms |
| Married honorific | `expn:marriedHonorific` | Dropdown | e.g. Mrs |
| Gender | `schema:gender` | Dropdown | |
| Person role | `expn:personRole` | Dropdown | |
| Person type (special flags) | `schema:additionalType` | Dropdown | ⚠️ see note above — reused on the Relationship template for something else entirely |

## Birth & death

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Birth | `expn:birth` | Resource link (Items) | General birth facts, linked item |
| Place of birth | `schema:birthPlace` | Resource link (Items) | |
| Country of birth | `expn:countryOfBirth` | Dropdown | |
| Death | `expn:death` | Resource link (Items) | Date, place and nature of death |
| Death date | `schema:deathDate` | Date | |
| Place of death | `schema:deathPlace` | Resource link (Items) | |
| Country of death | `expn:countryOfDeath` | Dropdown | |
| Cause of death | `expn:causeOfDeath` | Dropdown | |
| Survived | `expn:survived` | Dropdown | Survived the war |

## Education

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Early education | `expn:earlyEducation` | Resource link (Items) | Primary/secondary schooling |
| Tertiary education | `schema:hasCredential` | Resource link (Items) | Degrees/qualifications |
| Start date | `schema:startDate` | Date | Description just says "Start Date" — it sits directly under Tertiary education, so it's probably a study start date, but that's my inference from position, not confirmed |
| Combined start dates | `expn:combinedStartDate` | Date | "All 'start of study dates' have been combined" |
| Education notes | `expn:educationNote` | Text | |
| War matriculation | `expn:matriculated` | Dropdown | Whether matriculated |

## University affiliation (general)

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| University connections | `expn:universityConnection` | Dropdown | Which university(ies) a person is connected to |
| University role | `expn:universityRole` | Dropdown | |
| University Commission | `expn:universityCommission` | Dropdown | Uni Commission funding |

## University affiliation — institution-specific (legacy/bulk-upload fields)

<!-- Nicole: the Melbourne field's own description names it as a bulk-upload artifact — worth checking whether the rest of this group is the same, and whether it's worth a guide note that these are narrow/legacy rather than general-purpose. -->

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Year commenced - MELBOURNE UNI ONLY | `expn:yearCommenced` | Date | "For Melbourne University bulk upload" |
| Later at - SYDNEY UNI ONLY | `expn:laterAt` | Resource link (Items) | From the Book of Remembrance entry |
| USyd residential college | `expn:usydResidentialCollege` | Dropdown | |
| College start date (year) | `expn:collegeStartDate` | Date | |
| College end date (year) | `expn:collegeEndDate` | Date | |
| SUU Special Hon. Life Memb. 1939-1945 | `expn:suuSpecialHonLifeMemb1939To1945` | Dropdown | |
| Sydney Teachers College | `expn:sydneyTeachersCollege` | Dropdown | |

## Military & war-service classification

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Event flag | `expn:eventFlag` | Dropdown | Flags WW1/WW2 (or other) association |
| Military service | `expn:militaryService` | Resource link (Items) | Rank and company |
| Military awards | `expn:militaryAward` | Resource link (Items) | |
| CRTS | `expn:crts` | Dropdown | Commonwealth Reconstruction Training Scheme |
| UniMelb Category | `expn:uniMelbCategory` | Dropdown | Fallen / Died without service / Returned |
| DVA checked (Beyond 1939) | ⚠️ not visible in the screenshot | Dropdown | Description also cut off after "Whether Department of Veterans..." — needs a fresh look at the live form |

## Life events (the "eventlet" cluster)

<!-- Nicole: this is the same catch-all pattern flagged in the mapping diagram — worth a cross-reference once Module 1 is live. -->

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Life events | `expn:lifeEvent` | Resource link (Items) | |
| Other events | `schema:performerIn` | Resource link (Items) | "marriage, wounded, awards eg. OBE" |

## Family & relationships

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Related Person(s) | `schema:relatedTo` | Resource link (Items) | ⚠️ see note above — confirm this vs. the next row |
| Related persons | `expn:relatedPerson` | Resource link (Items) | ⚠️ see note above |
| Parental occupation | `expn:parentalOccupation` | Dropdown | |

## Occupation, associations, religion, language

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Occupations | `schema:hasOccupation` | Resource link (Items) | |
| Professional Association Memberships | `schema:memberOf` | Resource link (Items) | |
| Religion | `expn:religion` | Dropdown | |
| Language spoken | `schema:knowsLanguage` | Dropdown | |

## External links & identifiers

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Australian War Memorial | `expn:australianWarMemorialUrl` | URI + label | |
| People Australia | `expn:peopleAustraliaUrl` | URI + label | |
| University Archives Mediabank | `expn:universityArchivesMediabankUrl` | URI + label | |
| Discovering Anzacs | `expn:discoveringAnzacsUrl` | URI + label | |
| Department of Veteran Affairs | `expn:dvaUrl` | URI + label | |
| War Graves commission | ⚠️ not visible in the screenshot | URI + label | Needs a fresh look at the live form |
| Other URLs | `expn:otherUrl` | URI + label | Anything not covered by the named URL fields above |
| URL(s) | `schema:url` | URI + label | General — "relating to the current record" |
| ADB Entry ID | `expn:adbEntryID` | Text | Australian Dictionary of Biography |
| NLA Party Identifier | `expn:nlaPartyID` | Text | |
| Contact details or URL | `schema:contactPoint` | Text or URI (toggle) | |
| Email address | `schema:email` | Text | |

## Documents, media & narrative

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Thumbnail image | `schema:thumbnail` | Resource link (Items) | |
| Additional photograph(s) | `schema:image` | Resource link (Items) | |
| Documents | `expn:document` | Resource link (Items) | |
| Documents / photographs NOT TO BE PUBLISHED | `expn:privateDocument` | Resource link (Items) | |
| PDF of book entry | `expn:pdfOfBookEntry` | Resource link (Items) | |
| Publications | `schema:publication` | Text | Title, date, ISBN if applicable |
| Narrative | `expn:extendedDescription` | Text | |
| Narrative - quote | `expn:narrativeQuote` | Text | |
| Visible notes | `schema:description` | Text | |
| OCRd book entry or other narrative | ⚠️ not visible in the screenshot | Text | Needs a fresh look at the live form |

## Internal / admin

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| Internal notes | `expn:internalNote` | Text | Not for public view |

## Structural

| Field label (Add Item screen) | Property (Search by value) | Type | Notes |
|---|---|---|---|
| isPartOf | `schema:isPartOf` | Resource link (Item sets) | Item-set membership |

## Not part of "Search by value" at all

These two selectors set what kind of record you're looking at — they're the
"Class" and "Resource Template" filters, not properties you search *within*:

- **Resource template**: `Person`
- **Class**: `schema.org:Person`

---

## ⚠️ Still to confirm — property term not visible in the screenshots

- **DVA checked (Beyond 1939)** — description also cut off after "Whether Department of Veterans..."
- **War Graves commission**
- **OCRd book entry or other narrative**
