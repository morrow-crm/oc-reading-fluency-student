---
name: "no-ai-trace"
type: "reference"
status: "active"
tags: []
description: "Rewrite text to eliminate every category of AI-writing marker catalogued on Wikipedia's \"Signs of AI writing\" page — vocabulary, syntax, sentence constructions, paragraph shapes, punctuation, formatting, and tone. Use this skill any time the user asks for a rewrite that should not read as AI-generated, or uses phrases like \"de-AI this,\" \"remove AI traces,\" \"make this sound human,\" \"pass AI detection,\" \"rewrite without AI markers,\" or otherwise signals that the output must be stripped of LLM tells. Also use when the user pastes text (their own or someone else's) and asks for a cleaner, more human version, or when revising Claude's own prior output that risks reading as AI-generated."
created: "2026-09-11"
updated: "2026-09-11"
checksum: "sha256:b1af14bb8150cd0a8a99f905d6ff651da212a7cf4ee8483696fe88d0d4239410"
---

# No AI Trace

This skill rewrites text so it avoids every marker catalogued on Wikipedia's "Signs of AI writing" (WP:AIWTW). The goal is not cosmetic — it is to eliminate the underlying patterns that make LLM prose detectable. A rewrite that swaps "delve" for "explore" while keeping the same promotional tone, rule-of-three lists, negative parallelisms, and significance-inflation has not been de-AI'd. It has been lightly laundered.

The skill has two parts: a **diagnostic pass** that audits the source text against every marker category, and a **rewrite protocol** that resolves each flagged marker. Work through both. Do not skip the diagnostic — markers hide in patterns as much as in words, and the common failure mode is fixing visible vocabulary while leaving the syntactic skeleton intact.

## How to use this skill

1. Read the source text once for meaning. Hold onto what the writer is actually trying to say — you will rebuild it in different prose.
2. Run the diagnostic pass below. Note every marker present. Be thorough; assume the text has more markers than you first notice.
3. Rewrite from the ideas, not from the sentences. Sentence-level substitution preserves AI rhythm. Paragraph-level reconstruction does not.
4. After drafting, run a verification pass against the same diagnostic. If any marker survived, revise again.

---

## Part 1 — Diagnostic pass: every marker to check for

Organized in the order Wikipedia uses, grouped into eight domains. Check every item.

### A. Tone and stance markers

**A1. Significance inflation / legacy puffery.** Sentences that puff up a subject's importance by tying it to broader trends, legacies, or turning points. Watch for: *stands as, serves as, is a testament to, marks a pivotal moment, reflects a broader, symbolizing its enduring, contributing to the, setting the stage for, shaping the, represents a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted.* Also watch for the hedged version — "though minor, it contributes to the broader story of …" — where the writer concedes triviality and then inflates anyway.

**A2. Undue emphasis on notability, attribution, and media coverage.** Claims that a subject has been "profiled in," has "independent coverage," appears in "multiple high-quality outlets," etc. Reads like a press kit. Common in bios and company descriptions.

**A3. Superficial analysis via trailing participles.** Sentences that tack a present-participle analysis clause onto the end: "…*highlighting its significance*," "…*underscoring the region's diversity*," "…*reflecting a broader trend*," "…*ensuring continued relevance*," "…*fostering collaboration*," "…*contributing to the field*." The analysis is almost always vague and almost always unsupported.

**A4. Promotional / peacock / travel-guide tone.** Watch for: *boasts a, vibrant, rich, profound, enhancing, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking, renowned, featuring, diverse array, breathtaking, must-visit, must-see, stunning, enduring legacy, rich cultural tapestry.* Also: press-release cadence around people and companies — "emphasized the airline's commitment to …"

**A5. Editorializing.** Unsourced interpretation, opinion, or synthesis slipped in as if it were fact. "Their ability to simulate both form and function makes them powerful tools for understanding …" — nothing in the underlying sources says this; the LLM wrote it.

**A6. Vague attributions / weasel overgeneralization.** *Industry reports, observers have cited, experts argue, some critics argue, several sources, such as [exhaustive list].* Presents one or two sources as widely held views; implies a list is representative when the sources gave no such indication.

**A7. Outline-like "Despite challenges … future prospects" arcs.** Paragraphs and sections that end with "Despite these challenges, [subject] continues to thrive / remains relevant / positions itself for the future …" Even without a literal heading, this rhythm is a tell.

**A8. Lead sentences that treat list/article titles as proper nouns.** "The List of songs about Mexico is a curated compilation of …" If the source text opens by defining a descriptive title as if it were an entity, fix it.

### B. Vocabulary markers

**B1. Core AI vocabulary (any era).** The canonical overused words. Presence of one or two may be coincidence; presence of several is a tell:

*additionally* (especially sentence-initial), *align with, boasts* (meaning "has"), *bolstered, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight* (verb), *interplay, intricate / intricacies, key* (adjective), *landscape* (abstract), *meticulous / meticulously, navigate, pivotal, realm, resonate, seamless, showcase, tapestry* (abstract), *testament, underscore* (verb), *unveil, valuable, vibrant.*

Era-specific clusters (useful for identifying which model produced a draft, and which words to hunt hardest):
- **2023 – mid 2024 (GPT-4 era):** additionally, boasts, bolstered, crucial, delve, emphasizing, enduring, garner, intricate, interplay, key, landscape, meticulous, pivotal, underscore, tapestry, testament, valuable, vibrant.
- **Mid 2024 – mid 2025 (GPT-4o era):** align with, bolstered, crucial, emphasizing, enhance, enduring, fostering, highlighting, pivotal, showcasing, underscore, vibrant.
- **Mid 2025 onward (GPT-5 era):** emphasizing, enhance, highlighting, showcasing — plus the notability / media-coverage cluster.

**B2. Avoidance of plain copulas.** Preference for *serves as / stands as / marks / represents* instead of *is* or *are;* preference for *features, offers* instead of *has.* LLMs systematically dodge "is" constructions when copyediting. Restoring plain copulas is one of the cheapest and most effective fixes.

**B3. Elegant variation.** Repeatedly swapping in synonyms for the same referent — a character called "the protagonist," then "the key player," then "the eponymous figure" — driven by the model's repetition penalty. If the source text won't call a thing by its name twice, that is a tell.

### C. Syntax and sentence-construction markers

**C1. Negative parallelism ("not X, but Y" / "not just X, it's Y").** The single most recognizable AI sentence shape. Variants include:
- "It's not a product launch, it's a paradigm shift."
- "This is not dissolution, it is becoming."
- "Not only … but also …"
- "No X, no Y, just Z."
- Two-sentence versions that spread across a full stop: "He hailed from the esteemed Duse family, renowned for their theatrical legacy. Eugenio's life, however, took a path that intertwined both personal ambition and familial complexities."

If the rewrite keeps any construction of the form *[negation], [contrasting affirmation]* as a rhetorical flourish, the rewrite failed. This is the hardest marker to purge because it feels like good writing. Cut it anyway.

**C2. Rule of three.** Triplets of adjectives, nouns, or short phrases: "innovative, transformative, and groundbreaking"; "keynote sessions, panel discussions, and networking opportunities." One triplet in a long piece is fine. Stacking triplets across adjacent sentences is a tell.

**C3. False ranges ("from X to Y").** Structures that imply a spectrum when there is none: "from intimate gatherings to global movements," "from technical expertise to creative vision." Two loosely related things dressed up as a continuum.

**C4. Overuse of specific conjunctions and transitions.** *Additionally* (especially sentence-initial), *moreover, furthermore, consequently, notably, importantly.* Also overused: *while* and *although* constructions where the contrast is doing no real work.

**C5. Trailing participle clauses (see A3).** Syntactically distinct from the tone problem: any sentence whose final clause is an "-ing" phrase doing vague analytical work. Audit every "-ing" at sentence end.

### D. Paragraph-shape markers

**D1. Compulsive summaries.** "In summary," "In conclusion," "Overall," or an unlabeled final sentence that restates what was just said. Human writers do this sometimes; AI does it reflexively, even in passages too short to warrant it.

**D2. Rigid formulaic section structures.** "Challenges," "Future Outlook," "Key Takeaways," "Historical Context," followed by the predictable paragraph shape. Also: a sequence of paragraphs each opening with a topic sentence that restates the section heading.

**D3. Paragraphs that start broad, narrow, then reinflate.** The AI shape: open with a generic significance claim, supply some middle detail, close with another significance claim that circles back to the opener. Human writing more often leaves a thread hanging, moves forward, or ends on the specific rather than the general.

**D4. Statistical regression to the mean.** The whole paragraph smooths specific, unusual facts into generic statements that could apply to many subjects. If a paragraph about a particular town could be dropped into an article about a different town with only proper nouns changed, it has regressed to the mean.

### E. Formatting and style markers

**E1. Title case in section headings.** "Key Findings And Future Directions" instead of "Key findings and future directions." LLMs default to title case even when the house style is sentence case.

**E2. Excessive boldface.** Bolding random key terms mid-paragraph as though every noun were a glossary entry. Also: bolding entire sentences for emphasis.

**E3. Inline-header vertical lists.** Lists where each item is a bolded inline header followed by a colon and description: "**Historical Context:** The world was rapidly changing …" Especially suspicious when the list item starts with a bullet character (•), hyphen, or emoji rather than proper list markup.

**E4. Emoji decoration.** Emoji in front of section headings or bullet points. 🧠 📌 🚀 🎯 — especially clustered.

**E5. Unnecessary small tables.** Two-column "metric / figure" tables where prose would serve. A table with three rows and two columns is almost always prose in disguise.

**E6. Markdown bleed.** Use of `#` headers, `**bold**`, `- bullets`, or triple-backtick code fences in contexts where the destination format is not Markdown. Also: a fenced code block containing text that is clearly meant as prose.

**E7. Skipping heading levels.** Jumping straight to level-3 headings with no level-2 above them.

### F. Punctuation markers

**F1. Em-dash overuse.** Em dashes used where a comma, colon, or parentheses would serve — especially in a "punched up" sales-writing rhythm — deployed repeatedly across adjacent sentences. One em dash in a paragraph is fine; three is a tell.

**F2. Curly quotes and curly apostrophes.** " ' ' ' rather than straight " ' — especially when appearing inconsistently (some curly, some straight) in the same text. Note: human writers using Word, macOS, or typeset publications legitimately produce curly quotes; this marker is weak on its own.

**F3. Hyphens used where en dashes belong.** Date ranges like "1990-2000" or scores like "3-2" rendered with hyphens. LLMs almost never use en dashes.

**F4. Subject-line preambles.** "Subject: Request for permission to edit …" pasted at the top of a message that was never actually an email.

### G. Communication-residue markers (when rewriting chatbot output directly)

**G1. Collaborative-assistant phrases.** *I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like …, Is there anything else, Let me know, Here is a more detailed breakdown.* Any whiff of helpful-chatbot affect.

**G2. Knowledge-cutoff disclaimers.** *As of my last training update, based on available information, while specific details are limited …* Delete entirely, or rewrite into a concrete statement of what is and isn't known, with a source.

**G3. Didactic "it's important to note" disclaimers.** *It's important to note, worth noting, it's crucial to remember, may vary by jurisdiction.* Older tic but still appears. Cut.

**G4. Prompt-refusal residue.** *As an AI language model, I cannot offer medical advice, but I can …* Never appears in honest human writing.

**G5. Meta-commentary on the document.** "In this section, we will discuss …" or "The purpose is to provide a comprehensive understanding of …" LLMs narrate the document they are writing.

### H. Citation and sourcing markers

**H1. Fabricated citations and hallucinated DOIs.** Check any source that looks plausible but is actually wrong — nonexistent authors, wrong journals, invented titles. This skill cannot verify citations without web access, but flag any citation pattern that seems formulaic (e.g., every cited article is from 2020 – 2023, every journal name sounds generic).

**H2. Placeholder text left in.** *`[Insert source here]`, `PASTE_URL_HERE`, `2025-XX-XX`, `SOURCE_PUBLISHER`.* Surface-level but common.

**H3. Echoing policy language.** On Wikipedia specifically: "independent coverage," "reliable sources," "significant, substantial, secondary coverage." The LLM repeats the guideline's own wording back as if it were analysis.

---

## Part 2 — Rewrite protocol

Once the diagnostic is done, rewrite in this order. The sequence matters: structural fixes first, because they dictate what sentences need to exist; sentence-level fixes second; vocabulary and punctuation last, because those are the easiest and the ones most likely to be undone by later structural changes.

### Step 1 — Decide what the text is actually saying

Write down, for yourself, the three to five claims the source text is making. If you can't, the source text may be saying almost nothing — pure significance inflation with no load-bearing content. In that case the rewrite is largely a cut, not a reword.

### Step 2 — Cut what isn't load-bearing

Before rewriting, delete:
- Every significance claim that isn't actually supported by a specific fact.
- Every trailing "-ing" clause that adds vague analysis.
- Every "Despite challenges … future prospects" arc that does not contain concrete challenges or concrete prospects.
- Every summary sentence that restates the paragraph it closes.
- Every "it's important to note" and "as of my last training update."
- Every collaborative-assistant aside.

Often the piece gets shorter by 20 – 40 percent at this step. That's correct. AI prose pads.

### Step 3 — Rebuild structure

If the source text marches through "Historical Context / Key Figures / Technical Details / Impact / Future Outlook," restructure around what the actual material demands. Not every topic has a future-outlook section; not every topic needs historical context up front. Let the material's own shape drive the order.

Break up the AI paragraph mold: open with a specific detail instead of a generic claim; let paragraphs end on the particular rather than circling back to the general; allow a paragraph to leave a thread unresolved and pick it up two paragraphs later.

### Step 4 — Rewrite sentences, not words

Rebuild each sentence from the claim, not from the existing sentence. If the source says "This achievement stands as a testament to the team's enduring commitment to innovation, marking a pivotal moment in the field's evolving landscape," do not produce "This achievement reflects the team's lasting dedication to innovation, marking an important moment in the changing field." That is vocabulary laundering. Produce something like "The team shipped the first working prototype in 2019" — a concrete sentence that does the actual work the significance-inflated version was gesturing at.

When rewriting at the sentence level, actively avoid:
- Negative parallelism in any form. Replace "it's not X, it's Y" with "it's Y" — and let the X go.
- Triplets. If you find yourself writing three adjectives in a row, cut one. If you find three parallel clauses, cut one.
- False ranges. "From X to Y" is almost never actually a range. Say the one thing you mean.
- Trailing participles. End sentences on nouns and verbs, not on "-ing" analytical clauses.
- Plain-copula avoidance. Use "is" and "has" freely. "X is Y" and "X has Y" are usually correct; the LLM dodge is the problem.

### Step 5 — Vocabulary sweep

Search the draft for the vocabulary listed in B1. For each hit, either substitute a plain word or — better — rewrite the sentence so the word isn't needed. Substitution alone preserves AI rhythm; rewriting the sentence usually produces a different (better) sentence. For instance, "delve into the intricacies of" almost always becomes "look at" plus whatever specific thing is being looked at.

### Step 6 — Punctuation and formatting sweep

- Count em dashes. If more than one or two per several paragraphs, cut most. Replace with commas, colons, parentheses, or full stops depending on the clause's actual job.
- Convert curly quotes and apostrophes to straight, unless the destination format is a typeset publication that handles smart quotes automatically.
- Replace any hyphen in a range (dates, scores, numerical ranges) with an en dash.
- Convert title-case headings to sentence case, unless house style requires title case.
- Remove random bolding. Bold should mark genuine emphasis, not decorate key terms.
- If the destination is not Markdown, strip Markdown formatting (`#`, `**`, `-` bullets, fences).
- Collapse unnecessary small tables into prose.
- Remove emoji from headings and bullets.

### Step 7 — Verification pass

Re-run the diagnostic against the rewrite. Specifically look for markers that may have been re-introduced during the rewrite itself, because AI rewriters of AI text often drift back toward AI patterns. If any marker is present, revise again.

---

## What the rewrite should NOT do

- **Don't substitute long words for shorter AI words.** "Delve" → "investigate thoroughly" is not a fix; it's a different flavor of the same register. "Delve" → "look at" or cutting the word entirely is a fix.
- **Don't preserve the sentence count.** If the source has twelve sentences and the rewrite has seven, that's often right.
- **Don't add friction for its own sake.** The goal is natural prose, not prose that is deliberately awkward to fake humanness. Real human writing has variation, hesitation, and specificity — not random rough patches.
- **Don't strip useful formality.** If the source genre is formal (policy document, scholarly article, formal report), the rewrite stays formal. De-AI'ing does not mean de-formalizing. Formal writing can be marker-free; the markers aren't formal, they're just AI.
- **Don't invent specifics.** If the source text says nothing concrete and you don't know the topic, don't fabricate concrete details to replace the removed puffery. Ask the user, or flag the gap ("This paragraph had no load-bearing content; I've cut it. Do you have specific details to add here?").

## What to report back to the user

When delivering the rewrite, briefly note:
1. Which marker categories were heaviest in the source (so the user learns the patterns).
2. Any passages you cut because they had no load-bearing content, and where gaps now exist that the user may want to fill.
3. Any places where you preserved something that looks like a marker but is actually load-bearing in context (e.g., "not X, but Y" is the author's genuine argumentative point, not filler).

Keep this report short. Four to six sentences is usually enough.
