---
layout: default
title: "Quick reference guide: Labels, properties and resource templates"
nav_order: 28
---

# Quick reference guide: Labels, properties and resource templates

<!--
Nicole: this is the master lookup table, in the exact order fields appear
on the Person "Add Item" screen (top to bottom). Link to this page from
Advanced Queries and from the Adding Person Records module instead of
repeating the table there.

This is schema/template metadata, not record data; no real person's
information appears here, so it's fine to publish on the public repo.
-->

Every field on the Person "Add Item" screen is backed by a property, and
that property's name, not the field's on-screen label, is what you'll see in
Advanced Search's "Search by value" dropdown. This table matches the two up,
in the same order the fields appear on the live form, so you don't have to
hop between the Add Item screen and the search screen to find the right one.
The last column names the resource template used by whatever gets linked
in. It's left blank where the field is a plain value stored directly on the
Person record rather than a link to another item.

| Field label (Add Item screen) | Property (Search by value) | Type | Associated resource template |
|---|---|---|---|
| Title | `dcterms:title` | Text (required) | N/A |
| University connections | `expn:universityConnection` | Dropdown | N/A |
| Event flag | `expn:eventFlag` | Dropdown | N/A |
| Thumbnail image | `schema:thumbnail` | Resource link (Items) | Digital media item |
| Alternate name(s)/title(s) | `schema:alternateName` | Text | N/A |
| Family name | `schema:familyName` | Text | N/A |
| Given name(s) | `schema:givenName` | Text | N/A |
| Initials | `expn:initials` | Text | N/A |
| Honorific | `schema:honorificPrefix` | Dropdown | N/A |
| Gender | `schema:gender` | Dropdown | N/A |
| Naming note | `expn:namingNote` | Text | N/A |
| Person role | `expn:personRole` | Dropdown | N/A |
| Early education | `expn:earlyEducation` | Resource link (Items) | Schooling |
| Tertiary education | `schema:hasCredential` | Resource link (Items) | Tertiary study |
| Start date | `schema:startDate` | Date | N/A |
| Country of birth | `expn:countryOfBirth` | Dropdown | N/A |
| Combined start dates | `expn:combinedStartDate` | Date | N/A |
| University role | `expn:universityRole` | Dropdown | N/A |
| Place of birth | `schema:birthPlace` | Resource link (Items) | Place |
| Education notes | `expn:educationNote` | Text | N/A |
| Life events | `expn:lifeEvent` | Resource link (Items) | Life event |
| War matriculation | `expn:matriculated` | Dropdown | N/A |
| Related Person(s) / Related persons | `schema:relatedTo` / `expn:relatedPerson` | Resource link (Items) | Relationship |
| Death date | `schema:deathDate` | Date | N/A |
| University Commission | `expn:universityCommission` | Dropdown | N/A |
| Country of death | `expn:countryOfDeath` | Dropdown | N/A |
| CRTS | `expn:crts` | Dropdown | N/A |
| Place of death | `schema:deathPlace` | Resource link (Items) | Place |
| Birth | `expn:birth` | Resource link (Items) | Life event |
| Cause of death | `expn:causeOfDeath` | Dropdown | N/A |
| Military service | `expn:militaryService` | Resource link (Items) | Military service |
| Military awards | `expn:militaryAward` | Resource link (Items) | Military award |
| Contact details or URL | `schema:contactPoint` | Text or URI (toggle) | N/A |
| Survived | `expn:survived` | Dropdown | N/A |
| Email address | `schema:email` | Text | N/A |
| Occupations | `schema:hasOccupation` | Resource link (Items) | Occupation eventlet |
| Professional Association Memberships | `schema:memberOf` | Resource link (Items) | Professional association member |
| Language spoken | `schema:knowsLanguage` | Dropdown | N/A |
| Other events | `schema:performerIn` | Resource link (Items) | Eventlet |
| URL(s) | `schema:url` | URI + label | N/A |
| Death | `expn:death` | Resource link (Items) | Death |
| PDF of book entry | `expn:pdfOfBookEntry` | Resource link (Items) | Digital media item |
| OCRd book entry or other narrative | `schema:text` | Text | N/A |
| Year commenced - MELBOURNE UNI ONLY | `expn:yearCommenced` | Date | N/A |
| Later at - SYDNEY UNI ONLY | `expn:laterAt` | Resource link (Items) | Educational institution |
| USyd residential college | `expn:usydResidentialCollege` | Dropdown | N/A |
| College start date (year) | `expn:collegeStartDate` | Date | N/A |
| College end date (year) | `expn:collegeEndDate` | Date | N/A |
| SUU Special Hon. Life Memb. 1939-1945 | `expn:suuSpecialHonLifeMemb1939To1945` | Dropdown | N/A |
| Sydney Teachers College | `expn:sydneyTeachersCollege` | Dropdown | N/A |
| Additional photograph(s) | `schema:image` | Resource link (Items) | Digital media item |
| Documents | `expn:document` | Resource link (Items) | Digital media item |
| Publications | `schema:publication` | Text | N/A |
| Documents / photographs NOT TO BE PUBLISHED | `expn:privateDocument` | Resource link (Items) | Digital media item |
| Person type (special flags) | `schema:additionalType` | Dropdown | N/A |
| Religion | `expn:religion` | Dropdown | N/A |
| Parental occupation | `expn:parentalOccupation` | Dropdown | N/A |
| Married name | `expn:marriedName` | Text | N/A |
| Married honorific | `expn:marriedHonorific` | Dropdown | N/A |
| Narrative | `expn:extendedDescription` | Text | N/A |
| Narrative - quote | `expn:narrativeQuote` | Text | N/A |
| Visible notes | `schema:description` | Text | N/A |
| Internal notes | `expn:internalNote` | Text | N/A |
| ADB Entry ID | `expn:adbEntryID` | Text | N/A |
| NLA Party Identifier | `expn:nlaPartyID` | Text | N/A |
| Discovering Anzacs | `expn:discoveringAnzacsUrl` | URI + label | N/A |
| Department of Veteran Affairs | `expn:dvaUrl` | URI + label | N/A |
| War Graves commission | `expn:warGravesCommissionURL` | URI + label | N/A |
| Australian War Memorial | `expn:australianWarMemorialUrl` | URI + label | N/A |
| People Australia | `expn:peopleAustraliaUrl` | URI + label | N/A |
| University Archives Mediabank | `expn:universityArchivesMediabankUrl` | URI + label | N/A |
| Other URLs | `expn:otherUrl` | URI + label | N/A |
| UniMelb Category | `expn:uniMelbCategory` | Dropdown | N/A |
| DVA checked (Beyond 1939) | `expn:dvaChecked` | Dropdown | N/A |
| isPartOf | `schema:isPartOf` | Resource link (Item sets) | Links to People Item Set |
