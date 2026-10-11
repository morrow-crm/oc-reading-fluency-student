# Reading-fluency assignments: new link-based workflow

_Prepared 2026-10-11 for Candice's Fall 2026 ENGL 99 / 101 Canvas courses. Hand to the Canvas project to update the assignments. Candice is the instructor; act with her oversight._

## The change

Students no longer download or upload a file. Each reading now has its own **assignment link**. A student clicks the link in the Canvas assignment and the reading opens straight into the fluency tool — read aloud, comprehension questions, and all. The reading is hosted on the site, so the link is short and students can't alter the assigned text. The comprehension questions now appear inside the tool, so they no longer need to be written into the Canvas description.

Base app: <https://morrow-crm.github.io/oc-reading-fluency-student/>

## How the links are made (faculty workflow)

Faculty author a reading in the reading-level analyzer — their side of the tool — and that reading gets a link of the form:

```
https://morrow-crm.github.io/oc-reading-fluency-student/?reading=<name>
```

Faculty copy that link and paste it into the Canvas assignment. That's the whole faculty step: **create the reading, copy its link, paste it in Canvas.** (Behind the scenes the reading file is published to the site's `readings/` folder during setup; the six readings for this term are already published, so the links below work now.)

## The six links for this term

| Reading | Paste this link |
| --- | --- |
| Alexie, *Superman and Me* | <https://morrow-crm.github.io/oc-reading-fluency-student/?reading=alexie> |
| Bunn, *How to Read Like a Writer* (excerpt) | <https://morrow-crm.github.io/oc-reading-fluency-student/?reading=bunn> |
| DeMint Bailey, Ha & Outlar, *What Color Is My Voice* (excerpt) | <https://morrow-crm.github.io/oc-reading-fluency-student/?reading=demint> |
| Keller, *The Story of My Life*, Ch. 4 | <https://morrow-crm.github.io/oc-reading-fluency-student/?reading=keller> |
| Lamott, *Shitty First Drafts* (excerpt) | <https://morrow-crm.github.io/oc-reading-fluency-student/?reading=lamott> |
| Malcolm X, *Learning to Read* (excerpt) | <https://morrow-crm.github.io/oc-reading-fluency-student/?reading=malcolm-x> |

## STEP 1 — Test first (required gate)

**Do not edit any live assignment until a link is confirmed working _through Canvas_.** Canvas sometimes wraps external links in a click-tracking redirect that can drop the `?reading=` part of the URL; this test catches that.

1. In a **test or preview** Canvas assignment, paste one link — e.g. the Alexie link — and open it the way a student would: click it from inside Canvas.
2. Confirm the app opens **with the reading already loaded** and goes into the activity. It should **not** show the "choose a file / upload" page.
3. If possible, repeat on the devices students use (phone, Chromebook).

**If the link does _not_ load the reading** — it lands on the upload page, shows "this assignment link could not open its reading," or the address bar no longer shows `?reading=...` — then **STOP. Make no revisions.** Report that the link did not survive Canvas so it can be fixed first.

## STEP 2 — Only if STEP 1 passes: update each assignment

For each of the six assignments:

- Paste the matching link above in place of the old reading file/attachment and any "download then upload" wording.
- **Remove the upload step** — students just click the link.
- **Remove the comprehension questions from the Canvas description** — they were a stopgap; the tool now shows them and captures the answers in the PDF.
- Keep everything else: read aloud when prompted, mark new vocabulary, answer the comprehension and reflection questions in the tool, then download the **audio recording** and the **reading record (PDF)** and submit both in Canvas.

### Suggested student instructions (adapt per assignment)

> **This week's reading: _[title]_.** Click the link below — your reading opens right in the tool, nothing to download.
>
> **Open the reading: [PASTE THE MATCHING LINK]**
>
> Read it aloud when prompted (the tool records you and times you), mark any new vocabulary, and answer the comprehension and reflection questions. When you're done, download the **audio recording** and the **reading record (PDF)**, and upload both files here.

### Reading -> assignment mapping

Match each Canvas assignment to its reading by title and use that reading's link:

- Alexie, *Superman and Me* -> `?reading=alexie`
- Bunn, *How to Read Like a Writer* -> `?reading=bunn`
- DeMint Bailey et al., *What Color Is My Voice* -> `?reading=demint`
- Keller, *The Story of My Life* -> `?reading=keller`
- Lamott, *Shitty First Drafts* -> `?reading=lamott`
- Malcolm X, *Learning to Read* -> `?reading=malcolm-x`

(The three ENGL 99/101 shells are identical, so apply the same change in each.)

## Safeguards

- The old **upload method still works**, so nothing breaks for other classes on the shared tool, and a student who opens the bare app can still upload a file if ever needed.
- If a link ever fails, the student lands on the normal upload page with a clear message — never a blank screen.
- **Keep the old file attachments in place** until the links are confirmed working in production, as a fallback.
