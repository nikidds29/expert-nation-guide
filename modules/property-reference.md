---
layout: default
title: Person Template Field Reference
nav_order: 35
---

# Person Template Field Reference

<!--
Nicole — this is the master lookup table, in the exact order fields appear
on the Person "Add Item" screen (top to bottom). Link to this page from
Advanced Queries and from the Adding Person Records module instead of
repeating the table there.

This is schema/template metadata, not record data — no real person's
information appears here, so it's fine to publish on the public repo.
-->

Every field on the Person "Add Item" screen is backed by a property — and
that property's name, not the field's on-screen label, is what you'll see in
Advanced Search's "Search by value" dropdown. This table matches the two up,
in the same order the fields appear on the live form, so you don't have to
hop between the Add Item screen and the search screen to find the right one.
The last column names the resource template used by whatever gets linked
in — left blank where the field is a plain value stored directly on the
Person record rather than a link to another item.

| Field label (Add Item screen) | Property (Search by value) | Type | Associated resource template |
|---|---|---|---|
| Resource template selector | — | Template selector | — |
| Class selector | — | Class selector | — |
| Title | `dcterms:title` | Text (required) | — |
| University connections | `expn:universityConnection` | Dropdown | — |
| Event flag | `expn:eventFlag` | Dropdown | — |
| Thumbnail image | `schema:thumbnail` | Resource link (Items) | Digital media item |
| Alternate name(s)/title(s) | `schema:alternateName` | Text | — |
| Family name | `schema:familyName` | Text | — |
| Given name(s) | `schema:givenName` | Text | — |
| Initials | `expn:initials` | Text | — |
| Honorific | `schema:honorificPrefix` | Dropdown | — |
| Gender | `schema:gender` | Dropdown | — |
| Naming note | `expn:namingNote` | Text | — |
| Person role | `expn:personRole` | Dropdown | — |
| Early education | `expn:earlyEducation` | Resource link (Items) | Schooling |
| Tertiary education | `schema:hasCredential` | Resource link (Items) | Tertiary study |
| Start date | `schema:startDate` | Date | — |
| Country of birth | `expn:countryOfBirth` | Dropdown | — |
| Combined start dates | `expn:combinedStartDate` | Date | — |
| University role | `expn:universityRole` | Dropdown | — |
| Place of birth | `schema:birthPlace` | Resource link (Items) | Place |
| Education notes | `expn:educationNote` | Text | — |
| Life events | `expn:lifeEvent` | Resource link (Items) | Life event |
| War matriculation | `expn:matriculated` | Dropdown | — |
| Related Person(s) / Related persons | `schema:relatedTo` / `expn:relatedPerson` | Resource link (Items) | Person / Associated person |
| Death date | `schema:deathDate` | Date | — |
| University Commission | `expn:universityCommission` | Dropdown | — |
| Country of death | `expn:countryOfDeath` | Dropdown | — |
| CRTS | `expn:crts` | Dropdown | — |
| Place of death | `schema:deathPlace` | Resource link (Items) | Place |
| Birth | `expn:birth` | Resource link (Items) | Life event |
| Cause of death | `expn:causeOfDeath` | Dropdown | — |
| Military service | `expn:militaryService` | Resource link (Items) | Military service |
| Military awards | `expn:militaryAward` | Resource link (Items) | Military award |
| Contact details or URL | `schema:contactPoint` | Text or URI (toggle) | — |
| Survived | `expn:survived` | Dropdown | — |
| Email address | `schema:email` | Text | — |
| Occupations | `schema:hasOccupation` | Resource link (Items) | Occupation eventlet |
| Professional Association Memberships | `schema:memberOf` | Resource link (Items) | Professional association member |
| Language spoken | `schema:knowsLanguage` | Dropdown | — |
| Other events | `schema:performerIn` | Resource link (Items) | Life event / Eventlet |
| URL(s) | `schema:url` | URI + label | — |
| Death | `expn:death` | Resource link (Items) | Death |
| PDF of book entry | `expn:pdfOfBookEntry` | Resource link (Items) | Digital media item |
| OCRd book entry or other narrative | `schema:text` | Text | — |
| Year commenced - MELBOURNE UNI ONLY | `expn:yearCommenced` | Date | — |
| Later at - SYDNEY UNI ONLY | `expn:laterAt` | Resource link (Items) | Educational institution |
| USyd residential college | `expn:usydResidentialCollege` | Dropdown | — |
| College start date (year) | `expn:collegeStartDate` | Date | — |
| College end date (year) | `expn:collegeEndDate` | Date | — |
| SUU Special Hon. Life Memb. 1939-1945 | `expn:suuSpecialHonLifeMemb1939To1945` | Dropdown | — |
| Sydney Teachers College | `expn:sydneyTeachersCollege` | Dropdown | — |
| Additional photograph(s) | `schema:image` | Resource link (Items) | Digital media item |
| Documents | `expn:document` | Resource link (Items) | Digital media item |
| Publications | `schema:publication` | Text | — |
| Documents / photographs NOT TO BE PUBLISHED | `expn:privateDocument` | Resource link (Items) | Digital media item |
| Person type (special flags) | `schema:additionalType` | Dropdown | — |
| Religion | `expn:religion` | Dropdown | — |
| Parental occupation | `expn:parentalOccupation` | Dropdown | — |
| Married name | `expn:marriedName` | Text | — |
| Married honorific | `expn:marriedHonorific` | Dropdown | — |
| Narrative | `expn:extendedDescription` | Text | — |
| Narrative - quote | `expn:narrativeQuote` | Text | — |
| Visible notes | `schema:description` | Text | — |
| Internal notes | `expn:internalNote` | Text | — |
| ADB Entry ID | `expn:adbEntryID` | Text | — |
| NLA Party Identifier | `expn:nlaPartyID` | Text | — |
| Discovering Anzacs | `expn:discoveringAnzacsUrl` | URI + label | — |
| Department of Veteran Affairs | `expn:dvaUrl` | URI + label | — |
| War Graves commission | `expn:warGravesCommissionURL` | URI + label | — |
| Australian War Memorial | `expn:australianWarMemorialUrl` | URI + label | — |
| People Australia | `expn:peopleAustraliaUrl` | URI + label | — |
| University Archives Mediabank | `expn:universityArchivesMediabankUrl` | URI + label | — |
| Other URLs | `expn:otherUrl` | URI + label | — |
| UniMelb Category | `expn:uniMelbCategory` | Dropdown | — |
| DVA checked (Beyond 1939) | `expn:dvaChecked` | Dropdown | — |
| isPartOf | `schema:isPartOf` | Resource link (Item sets) | Links to People Item Set |
