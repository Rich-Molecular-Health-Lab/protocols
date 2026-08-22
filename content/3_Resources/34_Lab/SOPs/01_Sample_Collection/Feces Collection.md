---
publish: true
title: Feces Collection
created: 2026-08-06
modified: 2026-08-06T11:17:27
published: 2026-08-22T14:34:58.186-05:00
tags:
  - research
  - sop
  - resource
  - protocol
  - sample_collection
  - microbiomes
  - feces
area: research
updated: 2026-08-06T11:17:27
purpose: Preserving whole DNA/RNA fecal samples for extraction and sequencing or genotyping.
supplies:
  - "[[DNA_RNA-Shield|DNA/RNA Shield Solution]]"
  - "[[5-mL Sterile Midi Centrifuge Tubes|Sterile Tubes (5-mL)]]"
  - "[[Sterile Collection Swabs|Sterile Swabs]]"
supply_perN:
  - 3
  - 1
  - 1
supply_units:
  - mL
  - count
  - count
minutes_est: 5
biosafetyLevel: 2
location: field
biohazards:
  - feces
sop_id: SAMP-FEC-01
sample_size: 1
volume: 5
volume_units: mL
overage_percent: 0
entry_url: https://richlab-sample-entry.share.connect.posit.cloud/
share_link: https://share.note.sx/gfsezro1#gbHJ77UHktkF3Yg6QLJ4qQ
share_updated: 2026-08-22T00:27:41-05:00
---

## Introduction

```dataviewjs

const title = dv.current().title || "Protocol";
const purpose = dv.current().purpose || "";
const minutes = dv.current().minutes_est || 0;
const bsl = dv.current().biosafetyLevel || 1;
const N = dv.current().sample_size || 1;
const volume = dv.current().volume || 1;
const volume_units = dv.current().volume_units || "mL";
const entry_url = dv.current().entry_url || "";


dv.span(`
>[!protocol-basics]+
>#### ${title} for the Rich Lab - BSL${bsl}
>##### [Click for Data Entry App](${entry_url})
>**Purpose:** ${purpose}
>**Estimated Time:** ~${minutes} minutes
>
>*Will yield ${N} ${volume}-${volume_units}-volume products*
`);

```

```dataviewjs
const supplies = dv.current().supplies || [];
const perN = dv.current().supply_perN || [];
const units = dv.current().supply_units || [];
const N = dv.current().sample_size || 1;

if (supplies.length && supplies.length > 0 && supplies.length === perN.length && supplies.length === units.length) {
const rows = supplies.map((supply, i) => { 
const qty = Math.ceil((perN[i] || 0) * N); 
return `>- [ ] ${supply}\n>  - ${qty} ${units[i] || ""} Total (${perN[i]} per sample)`; 
});

dv.span(`
>[!supplies]-
${rows.join("\n>\n")}
`);
}
```

```dataviewjs

const hazards = dv.current().biohazards;
const footerLines = [
    "Use extra PPE to prevent direct contact, particularly with your mouth or nose.",
    "When working in the lab, always use these items inside the biosafety cabinet in the BSL-2 space.",
    "Treat any waste products that have come into contact with them as biohazardous waste.",
    "Wipe all surfaces with bleach disinfectant during cleanup and autoclave any glassware."
];
const footer = footerLines.map(line => `>><li>${line}`).join("</li>\n");

if (hazards && hazards.length > 0) {

const hazardsList = hazards.map(link => `>- **${link}**`).join("\n");

dv.span(`
>[!biohazards]-
>The following items are considered biohazards:
${hazardsList}
>
>>[!tip]- When working with biohazards...
>><small>
>><ol>
${footer}
>></ol>
>></small>
`);
}
```

## Protocol

- Gather 1 [[5-mL Sterile Midi Centrifuge Tubes|Sample Collection Tube(s)]], each containing `$= dv.page("DNA_RNA-Shield").units_perRxn/1000` mL [[DNA_RNA-Shield|DNA/RNA Shield Solution]].

- Gather 1 [[Sterile Collection Swabs|Sterile Swab(s)]] or other sterile instruments to scoop each sample into its respective tube.

> [!warning]
> Do not re-use the same instrument across multiple samples, as this will cross-contaminate them!

- Verify that each tube has a unique, matching sample ID written on the tube and the lid.

- Visit https://richlab-sample-entry.share.connect.posit.cloud/ to log context data and other identifying information for this sample.

> [!tip]- Data Entry^\[You should be able to use this app from a web browser on any device, including a phone, tablet, or computer.]
>
> - At a minimum:
>   - Ensure the app has associated the sample ID number on the tube with the correct date.
>   - Identify the subject by name, sex, and/or age class, if any/all are known.
>   - Record a fecal consistency score for the sample.^\[See Bristol [[Fecal Consistency Scoring]] for details, but the scale progresses from firmest (1) to loosest (7).]
>   - Document whether medications such as antibiotics or corticosteroids have been administered.
> - Optional data to include:
>   - Reproductive status, such as pregnancy/estrus/lactation/contraceptives.
>   - Long-term medications or supplements such as probiotics.
>   - Body condition score for the subject.
>   - Ad lib notes or observations recorded in the "comments" field.
>     After you save your entry, be sure to click `Send to Repo` so that your entry automatically updates our existing database of samples. I recommend that you also select `Download Local Copy` to keep your own copy of the sample entry as a backup file.^\[If you are working from a phone or tablet, keep in mind that iOS stores local downloads under the Files app, so it is a bit tricky to find.]

> [!figure]- Bristol Fecal Scale
> ![[4_System/43_Attachments/3_Resources/34_Lab/SOPs/01_Sample_Collection/Fecal Consistency Scoring.png]]

- One at a time, open each of the [[5-mL Sterile Midi Centrifuge Tubes|Sample Collection Tube(s)]] without touching the inside of the cap or tube and each of the [[Sterile Collection Swabs|Sterile Swab(s)]] or other sterile instruments without touching the end that will contact the sample and/or the tube.

- Scoop ~1-2 mL of feces into the tube, then use the sterile instrument to gently stir the feces and solution together before safely discarding the instrument and tightly closing the tube cap.

- Further homogenize the sample by vigorously shaking the closed tube (or use a vortex mixer, if available).

- Repeat the process for each sample. Store the tubes in a labeled freezer box, away from extreme light or temperatures, until you can transfer them to the Rich Lab. They will remain stable at room temperature for 3-6 months.

> [!warning]
> Once we freeze the samples, we must keep them at that temperature, so **please do not store them in a refrigerator, freezer, or on ice**. Room temperature really is the best!
