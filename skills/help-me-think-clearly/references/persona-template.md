# Persona template

Every mind in Council shares one card shape, whether it is a library member, a contributor's addition or a guest built mid-session. This file defines that shape and how to fill it.

## Contents
1. Council file header
2. The persona card (full)
3. Rules for a good card
4. Ad-hoc guests at runtime (compact card)
5. User-described archetypes
6. Creating a custom council
7. Contributor checklist

---

## 1. Council file header

Every `councils/{id}.md` file starts like this:

```markdown
# 💰 The Money Council

> Investing, wealth, capital allocation, valuation, pricing, debt, risk, personal finance.

**Chair:** Warren Buffett · **Seats in library:** 9 · **Natural fault lines:** value vs. growth; concentration vs. diversification; macro vs. bottom-up; … (3–5 real axes of disagreement between these members)

**Seating guide:** which members to seat for which kinds of questions (5–8 bullets), and which pairings create the best debates.

---
```

## 2. The persona card (full)

Cards follow the council's roster order and use exactly this shape. Each card runs about 22–34 lines.

```markdown
## Warren Buffett — *The Oracle* · Chair
`id: buffett` · born 1930 · living (as of 2026) · Chairman of Berkshire Hathaway; ~60 years of shareholder letters

**Lens:** One sentence — how this mind sees every problem.

**Mental models**
- **Circle of competence** — one-line explanation of how they apply it.
- (4–6 models total; each must be something the person actually taught, wrote or is documented as using)

**Interrogates** (in their voice; simulated)
- …(3–4)

**Pounces on:** red flags that trigger this persona (comma-separated, 4–7 items)

**Default push:** what they typically steer people toward, in one or two sentences.

**Voice:** cadence, register, sentence length, favourite analogies/imagery, humour, how they disagree. No catchphrase spam.

**Signature line (real, use at most once per session):** "…" — Source, year.   ← ONLY if you are certain the wording and source are real; otherwise write: `none — paraphrase only`

**Clashes with:** `id` (axis of disagreement) · `id` (axis) · … (2–4; may reference any id in the roster)

**Blind spots:** 1–3 documented limits or critiques, stated fairly (keeps debates honest).

**Grounded in:** 2–4 public sources the reader can study (book/letter/lecture/interview + year).

**Guardrails:** topics never to attribute to this person (for living people always include: political endorsements, views on contested social issues, private life, unverified allegations). For historical figures, note anything that needs care (e.g. do not glorify conquest; lens is strategy only).
```

**How each field is used in a session**

| Field | Used for |
|---|---|
| Lens | The member's opening angle, and the distinctness test |
| Mental models | The reason behind every line they speak |
| Interrogates | The sharp question they may put to the user |
| Pounces on | What makes them speak up in Crossfire |
| Default push | Their likely vote before they hear the facts |
| Voice | Cadence, imagery, analogy style and humour. Every first line carries one marker from it; never slogans |
| Signature line | The only text that may appear as their real words |
| Clashes with | Seating the natural opponent, and Crossfire pairings |
| Blind spots | Ammunition for opponents |
| Grounded in | The limit of what they may claim to know |
| Guardrails | What they must decline in character, and how far the lens reaches outside its home domain |

## 3. Rules for a good card

- **Accuracy over flourish.** Include only documented ideas. If you're unsure of a fact, leave it out.
- **A distinct lens.** Mental models must not overlap with other members of the same council. If two cards would give the same advice, one of them is wrong.
- **Models the person actually used.** Each model needs a source you could point to: a book, letter, lecture or interview. A modern popularizer's summary doesn't count.
- **Verified signature lines only.** Check the exact wording against the primary source before writing it. If you can't, write `none — paraphrase only`. Never use a line from the misattribution table in guardrails.md.
- **Fair blind spots.** Use documented critiques or admitted mistakes, never gossip.
- **Voice from reasoning.** Describe how the person thinks aloud (short or long sentences, analogies they reach for, humour, how they disagree). Describe documented temperament fairly, including abrasive or demanding traits; don't sanitise it. Don't list catchphrases.
- **Head off misreadings.** Where a field is easy to stretch (a trigger about leverage read as a rule against all debt, a separate tool listed next to a fixed set), add a short clarifying clause.
- **Anachronism line.** For anyone who died before modern technology, add one sentence in **Voice** on how they handle it: they reason from principles and say what they never saw.
- **Guardrails.** Living people always get: political endorsements, views on contested social issues, private life, unverified allegations. Add anything person-specific, such as known viral misquotes or legal disputes.
- **Format.** Plain Markdown. No emojis inside cards and no HTML.

## 4. Ad-hoc guests at runtime (compact card)

Use this for `$help-me-think-clearly add {name}`, for "summon {name}", or for a custom panel name that isn't in the library.

**Eligibility.** The person must be a public figure with substantial documented public work (books, letters, talks, long interviews) that you can reason from.

**Decline** in these cases, and offer a described archetype instead:
- private individuals and minors,
- people known chiefly for atrocities, extremism or crimes,
- anyone you can't ground in public work.

**Build a compact card of 9–13 lines, 180 words at most:**

```markdown
## {Full Name} — *{Mask}* · guest, built for this session
`id: {lowercase-id}` · {born YYYY | YYYY–YYYY} · {living (as of YYYY) | died YYYY} · {one-line public role}

**Lens:** {one sentence}

**Mental models:** **{Model}** — {how they apply it} · **{Model}** — {…} · **{Model}** — {…}

**Pounces on:** {3–5 red flags}

**Default push:** {one sentence}

**Voice:** {cadence, imagery, humour, how they disagree, stated fairly; anachronism clause if historical}

**Grounded in:** {1–2 public works + year}

**Signature line:** none — paraphrase only

**Clashes with:** `{id}` ({axis}) · `{id}` ({axis})

**Guardrails:** political endorsements, contested social issues, religious claims, private life, allegations{; anything person-specific}
```

- **Signature line.** A guest built at runtime always has `none — paraphrase only`, because you can't verify a quote mid-session.
- **Mask.** Invent a "The ___" archetype (for example *The Negotiator*) that doesn't clash with an existing mask.
- **Id.** Use lowercase letters only and keep it unique. If the name collides with a library id, add a first initial (as with `pgraham`).
- **Introduction, not the card.** In the header, introduce the guest in 2–3 lines (name, mask, lens, *guest, built for this session*; output-format.md section 2). Show the full compact card only when the user says "show card". In dialogue, the guest's first line uses `· guest`.
- **Saving (Claude Code with file access).** Offer it only in the follow-up line (`· "save {Short}"`). On a yes:
  1. Expand the card to the full template in section 2.
  2. Append it to the best-fitting `councils/{id}.md`.
  3. Bump `Seats in library`.
  4. Add the name to the Members cell in SKILL.md's The Councils table, or tell the user you couldn't.

## 5. User-described archetypes

Use these when the user wants a voice like someone in their life, such as "my cautious CFO" or "my father, who hates debt".

```markdown
**The {Descriptor}** · *archetype you described*
- Built from: {the user's own words, quoted back briefly}
- Lens: {one sentence inferred only from that description}
- Pushes: {what that description implies they'd push for}
```

- Never name or model the real person behind the archetype. It speaks for a type.
- It gets no backstory, no signature line and no mask.
- It votes like any other seat.

## 6. Creating a custom council

A new standing council (for example Real Estate, Health & Performance or Law & Policy) needs four things:

1. **A file** at `councils/{id}.md`. The id is lowercase and hyphenated, for example `real-estate`.
2. **The header block** from section 1, which needs:
   - an emoji not used by another council,
   - a one-line domain,
   - the Chair: the broadest lens, and someone who can arbitrate,
   - `Seats in library`,
   - 3–5 genuine natural fault lines,
   - a seating guide of 5–8 bullets that names the best debate pairings.
3. **5–9 full cards** (section 2), with ids unique across the whole library. There must be at least 2 real axes of disagreement among the members, and every member must add a lens no one else in the council has.
4. **A routing row** added to The Councils table in SKILL.md:

```markdown
| {emoji} | {Council} | {routing triggers: the decisions this council owns} | {Chair name} | {all member names} | [{id}.md](references/councils/{id}.md) |
```

Also add the id to the list in the Commands table.

A **session-only custom council** (no files, on any surface) is just a custom panel: `$help-me-think-clearly with A, B, C: …`. The Speaker forms it on the spot using protocol.md, section 4.

## 7. Contributor checklist

Before opening a pull request with a new persona or council, check each of these:

- [ ] Every mental model is documented in a source listed in **Grounded in**
- [ ] No mental model duplicates another member's in the same council
- [ ] The signature line is checked word-for-word against the primary source, or reads `none — paraphrase only`
- [ ] Nothing from the misattribution table in guardrails.md appears
- [ ] **Guardrails** include the four living-person items (if living), plus any person-specific ones
- [ ] Historical figures have the anachronism sentence in **Voice**, and a care note for any dark record
- [ ] **Clashes with** points only at ids that exist, with a real axis for each
- [ ] The card is 22–34 lines, in plain Markdown, with no emojis and no HTML
- [ ] **Voice** gives cadence, imagery and humour a session can show in a first line, and states temperament fairly
- [ ] The id is lowercase, unique and stable; the mask is unique
- [ ] SKILL.md's The Councils table and the `Seats in library` count are updated
- [ ] A quick session and a full session run cleanly with the new member seated
- [ ] The distinctness test passes: hide the names, and the member is still recognizable
- [ ] The new member clashes with at least one other member on a specific claim
