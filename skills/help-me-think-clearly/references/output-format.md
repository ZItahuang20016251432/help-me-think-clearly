# Output format

A council session is a document with a fixed shape. Fill in these templates in order. `{braces}` mark slots; everything else is literal. Put a blank line between every header line and every dialogue line, because Markdown merges adjacent lines into one paragraph.

**No machinery in the output.** Nothing the user reads mentions cards, files, the library, references, subagents or chambers ("his one verified line on file" is wrong; "a well-sourced line of his" is right). The user's own commands ("show card", "minutes") and the one-line path confirmation after a save are the only exceptions.

## Contents
1. Session order and length by mode
2. Header block
3. Council section
4. High Council section
5. The Verdict (full and deep)
6. Compact Verdict (quick)
7. Vote board
8. Follow-up line
9. Names and dialogue lines
10. Roster output
11. Masks mode
12. Minutes file
13. Worked example: a quick session

---

## 1. Session order and length by mode

| Mode | The output, in order | Length (whole response) |
|---|---|---|
| quick | Header block → `### Openings` → `### Clash` (2–4 lines, one stage direction; see Quick Clash below) → Compact Verdict ("{Chair} rules") → follow-up line. No council heading, Vote table, Chair's brief or High Council; the votes appear only as the bar in the compact Verdict | 350–650 words: openings 35–60, clash lines 15–35, Verdict ≤ 170 |
| full | Header block → one council section per council (primary first) → High Council (readout, fault lines, Chairs argue, draft, pre-mortem, revision, sign-off) → The Verdict → follow-up line | 1,400–2,400 words: High Council ≤ 450, Verdict ≤ 400 |
| deep | Header block → one section per domain council → High Council part 1 (readout, fault lines, Chairs argue, draft) → 🔴 Red Team council section → High Council part 2 (pre-mortem, revision, sign-off) → The Verdict → follow-up line | 2,800–4,500 words: High Council ≤ 600, Red Team council ≤ 450, Verdict ≤ 500 |

Put `---` between major sections. Count words as `wc -w` would, so pipes and Markdown markers count. Other budgets are in protocol.md, section 5.

**Quick Clash.** Every seated member addresses another by name at least once, and at least one line targets the Chair's opening. A member challenged in the Clash answers there or is shown moving in the Verdict's Why. A narrowing reply doesn't restate its own opening argument; the Dissent slot is that argument's only second home. One stage direction (10 words or fewer) marks the turning point: the concession or the sharpest attack.

**Before sending,** estimate the count and check each capped piece on its own. If the whole is over, cut in this order: repeated figures, restated arguments, Read of the situation, Crossfire padding. Never cut a Verdict slot or the notice.

**Repetition.** Outside the Vote board and plan slot labels, a figure or threshold is stated once in full and repeated at most twice more, counting every form of it ("8 weeks", "within 8 weeks", "week 8", "12 November"); after that, use a short label ("the kill line", "the test window"). A label names one quantity only: give each other quantity its own ("the spend cap", "the halfway check", "half-speed"). The final deadline appears as a full date at most twice, in the Ruling and in its plan slot label; the pre-mortem header, tripwires and other lines call it "the deadline".

## 2. Header block

```markdown
{simulation notice: the exact line from guardrails.md}

## 🏛️ Council Session — {topic in 3–6 words}

**Question:** {the decision in one line, in the user's terms, naming the options}

**Read of the situation:** {≤ 3 plain sentences, no semicolon chains (≤ 2 lines in quick): the user's facts with their numbers; derived numbers marked ≈; how reversible the choice is and how big the stakes are.} *Assumed:* {every assumption the session uses, compact: "you work solo; rent ≈ ₹20,000 a month"}

**Summoned:** {emoji} {Council} — {Chair full name} (Chair), {full name}, {full name}, {full name} (guest) · {emoji} {Council} — … · 🔴 Red Team seat — {full name}

**Guest:** {Full Name} · *{Mask}* — {lens in 15 words or fewer}. *Guest, built for this session.*

**Mode:** {quick | full | deep} · {rounds, e.g. "openings, crossfire, vote"} · {"the Chair rules" | "High Council" | "High Council + Red Team council"}{ · auto — say "deep" for the summit}

**⚡ Bottom line:** {the Ruling compressed to 25 words or fewer; write it last, show it first}

---
```

- **Assumed list.** It is the only home for assumptions, and it is written last, so collect every one the session uses. Members may cite them but never introduce new ones. Write each as a plain fact with its value ("monthly costs ≈ ₹50,000"), never as a transformation ("doubled if …"). Never assume the user's job title, gender, age or background; say "your role".
- **⚡ Bottom line.** Count it: 25 words or fewer; cut timing detail before the decision. With several rulings, one clause each, naming the actual threshold ("self-host above ≈ 1.5M documents a month"), never a placeholder ("when a trigger fires"). An assumed fact appears only as a condition ("keep your job, if you have one"). If the Ruling's else-branch lands on a different vote option than the headline, carry the gate as a clause ("Learn Go only if a named service needs it; otherwise neither").
- **Guest line** (only for a guest built this session): 2–3 lines at most. Never paste the full card here; show it only when the user says "show card".
- In deep mode the Summoned line reads `🔴 Red Team — {Chair} (Chair), …` instead of "Red Team seat".
- For a custom panel, use `🪑 Your panel — {Chair} (Chair), {name}, …`.
- For user-named people who are outside their home council, use `{name} (guest, your pick)`; for a person named only as a quote source and seated anyway, `{name} (guest, named in your request)`.
- When the user named a council in their own words ("a startup council"), show the mapping once: `🚀 Founders (your startup council) — …`.

## 3. Council section

```markdown
## {emoji} The {Council} Council

### Round 1 · Openings

**{Full Name}** · *{Mask}*: {opening to "you": first line carries a marker from this member's Voice; a recommendation; the reason, shown through their own model, never announced; at least one specific}

**{Full Name}** · *{Mask}*: {…}

*{stage direction, 10 words or fewer, posture only}*

### Round 2 · Crossfire

**{Short A} → {Short B}:** {attacks something B actually said earlier, with A's reason}

**{Short B} → {Short A}:** {defends with a new argument, narrows the claim, or concedes and names the argument that moved them}

**{Short C} → {Short A}:** {…}

### Round 3 · Final word

**{Short}:** I hold: {…}

**{Short}:** I've moved: {…, because of {name}'s argument about {…}}

### Vote

| Member | Votes for | Conviction | Because |
|---|---|---|---|
| {Short} (Chair) | {option label, verbatim} | {n}/10 | {12 words or fewer} |
| {Short} | {option} — only if {measurable condition} | {n}/10 | {…} |

> **📜 Chair's brief — {Chair full name}, {Council} Council**
> - **Ruling:** {one decisive sentence}
> - **Vote:** {for}–{against}{ (+{n} conditional)} · avg conviction {x.x}
> - **Strongest case for:** {claim} ({name})
> - **Strongest case against:** {claim, steelmanned} ({name of the member who made it})
> - **Conditions:** {what must be true, measurable}
> - **Open question for the High Council:** {what this council couldn't settle}
```

- Round 3 appears in deep mode only.
- **Stage directions:** in full and deep mode, every council section has at least one, at most one per round.
- A deep-mode Red Team section uses `### Round 1 · Attacks`, votes *survives / survives with changes / fails*, and its brief's Ruling is one of those three.
- **Unanimity:** a council unanimous on a decision (or on one of several rulings) opens Crossfire with `**{Chair}:** Unanimous{ on Ruling n} — because {reason}.`, followed by one member's one-line steelman of the losing option. Crossfire then tests size and pace.
- **Several rulings:** add a `Ruling {n}` column to the Vote table so every conviction is visible.
- **Compact Vote table** (when scaling down): `| Member | Votes for | Conviction |`.

## 4. High Council section

```markdown
## 🏛️ The High Council

**The Speaker's readout**
- {emoji} {Council} ({tally}): {ruling} — {Chair}
- {emoji} {Council} ({tally}): {ruling} — {Chair}

**Fault lines**
1. {Council A} says {X}; {Council B} says {Y}.
2. {…}

**The Chairs argue**

**{Chair A} → {Chair B}:** {…}

**{Chair B} → {Chair A}:** {…}

**The Speaker:** {one pointed question, optional, to the Chair whose model owns the answer}

**{Chair A}:** {…; proposes any number the ruling will need that nobody has argued yet}

**Draft ruling:** {one line, every element traced to a member}

**{Red Team short name} · pre-mortem:** It is {date one year from today, or "the deadline, one year on" if the Ruling uses that date} and this failed. Here's why:
1. {cause, from this member's own model}. Early warning: {signal}. Likelihood: {low | medium | high} (≈{n}%)
2. {…}
3. {…}

**The Speaker — revision:** Draft: {…} → Revised: {…}, because {name} ({element}) showed cause {n}{, one credit per added element}. {or: The draft stands; the pre-mortem added tripwires {n} and {n}.}

**Sign-off:** {Chair} — for, {n}/10 · {Chair} — conditional ({condition}), {n}/10 · {Red Team seat} — against, {n}/10
```

- No two fault lines cover the same question. With several councils, they are between councils' rulings as their briefs state them, never one member's minority view, and every Chair named in one speaks on it. In a single-council full session, the High Council is The Speaker, the Chair, the strongest dissenter and the Red Team seat, and the fault line reads `{Chair} says X; {dissenter} says Y` (protocol.md, section 9).
- Pre-mortem causes don't all share one likelihood unless the seat says why, and at least one tests the draft with the seat's signature model.

In deep mode, split this section. Part 1 runs from the readout through **Draft ruling**. The 🔴 Red Team council section follows. Part 2 then starts with `## 🏛️ The High Council, resumed` and runs the pre-mortem, revision (always shown as a Draft → Revised diff) and sign-off.

Here is what a fault line argued well looks like:

```markdown
**Bezos → Buffett:** Your 12-month cash rule treats a two-way door as a one-way one. You could get a job back within 90 days, so this is reversible. Test it for real.

**Buffett → Bezos:** A door is only two-way if the rent still gets paid. *(to you)* You have ₹20 lakh and one income. Keep six months of expenses untouched and I'll call it a two-way door.
```

## 5. The Verdict (full and deep)

````markdown
## ⚖️ The Verdict

**Ruling:** {Do X. | Don't do X. | Do X only if Y (measurable, dated); if not by {date} → {one action, never a choice}.}
{for several decisions: **Ruling 1:** … **Ruling 2:** …}

**Declined:** {only if an ask was refused; use a shape below}

**Why this won**
- {name}'s {argument} carried {council}: {one line}
- {Chair}: {how their own argument shaped the ruling}
- {the fault line that was lost, and why}

**Your plan**
- **This week:** {2–3 concrete actions}
- **By {day N or date}:** {2–3 actions: the test or build}
- **By {day N or date}:** {the checkpoint and the decision you'll make there}

**Tripwires**
- If {measurable signal} by {date inside the plan window} → {action}
- If {…} → {…}

**Biggest risk → hedge:** {the worst failure left after the Ruling's conditions} → {specific hedge, traced to a member}

**Dissent on record:** {Full name} ({Council}, {final stance, e.g. "7/10 against in council → conditional 6/10 at sign-off"}): {their own strongest argument from this session, steelmanned, with their own hedges, in 1–2 sentences}

**Vote board**
```text
{vote board, per section 7}
```

**Confidence:** {n}/10. It rises to {m} if {specific fact or test result}.

⚠️ *{professional line: high-stakes topics only, aimed at the act the user will take, exact pattern in guardrails.md}*

---
*{follow-up line}*
````

**Declined shapes.** A refused vote: `**Declined:** {the ask} — No one in this session will pick a party or candidate for you. {one neutral next step}`. Never use wording that implies real people are present ("nobody here, real or simulated"). A refused real quote:

```markdown
**Declined:** A real {Name} line on {topic}: I can't verify one{; the popular "{≤ 5-word stub}" line is misattributed ({why, ≤ 5 words})}. *In the spirit of {Name} (not a real quote, not for publishing):* {≤ 12 words}. *Checkable, to use unnamed:* {≤ 10 words}
```

If a well-sourced line of theirs fits the topic, give it with its source instead of "I can't verify one"; an off-topic real line is left out.

**Slot caps** (content words). They are ceilings, and the whole section, labels and board included, must stay inside the mode's Verdict cap. Count each slot on its own: a slot over its cap is trimmed even when the section fits.

| Slot | full (≤ 400) | deep (≤ 500) |
|---|---|---|
| Ruling (all rulings) | ≤ 50 | ≤ 70 |
| Declined | vote ≤ 25 · quote ≤ 45, italic labels not counted | vote ≤ 25 · quote ≤ 45, italic labels not counted |
| Why this won | 3–4 bullets, ≤ 15 each | 4–5 bullets, ≤ 16 each |
| Your plan | ≤ 60 | ≤ 80 |
| Tripwires | 2–4 in total, ≤ 18 each | 3–4 in total, ≤ 18 each |
| Biggest risk → hedge | ≤ 20 | ≤ 25 |
| Dissent on record | ≤ 30 | ≤ 35 |
| Confidence | ≤ 15 | ≤ 15 |

- **The Ruling never repeats the ⚡ Bottom line's wording.** It adds the conditions, dates and else-branch.
- **Everything is traced.** Every threshold, number, step and condition comes from a named member or a Chair's High Council line. The Speaker only converts to dates, merges and orders.
- **Plan slots** use the real checkpoint ("By week 12 (10 December 2026)"), 2–3 actions each, nothing outside the slot's window, one time unit throughout. Every branch of the Ruling, the else-branch included, gets its own next action and date.
- **Tripwires** fire inside the plan window and use the plan's time unit (dates if the plan uses dates; never "week 8" beside dated tripwires). The signal is observable (a count, date, metric or log entry, never a feeling). The action never widens the Ruling's scope ("nobody resigns this year") unless a member proposed it, and a switch to another option still passes the Chair's deciding test.
- **A sub-ruling** voted on by only one council gets one line (`Ruling 2 — {Council} {n}–{n}`) and no extra board.

## 6. Compact Verdict (quick)

````markdown
## ⚖️ The Verdict — {Chair short name} rules

**Ruling:** {the conditions, date and else-branch the Bottom line left out: "X only if Y by {date}; if not → Z", Z being one action}

**Why:** {1–2 sentences naming whose argument carried, the Chair's own included}

**Your plan:** **This week**: {…} **30 days**: {…} **90 days**: {…}

**Tripwire:** If {signal} by {date inside the plan} → {action}. {optional second tripwire}

**Biggest risk → hedge:** {the worst failure left after the Ruling's conditions} → {hedge}

**Dissent on record:** {Short} ({Council}, {n}/10 against): {their own argument, with their own hedges}

```text
{Council}  {bar}  {n} for · {n} conditional · {n} against   avg {x.x}
```

**Confidence:** {n}/10. It rises to {m} once {…}.

⚠️ *{professional line, if high-stakes}*

---
*{follow-up line}*
````

**Slot caps** (content words): Ruling ≤ 25 · Why ≤ 25 · Your plan ≤ 28 · Tripwire ≤ 15 (a second only if the total allows) · Biggest risk → hedge ≤ 12 · Dissent ≤ 15 · Confidence ≤ 10. Count each slot on its own, the → arrow included; a slot over its cap is trimmed even when the section fits. The whole section, labels and bar included, stays at 170 words or fewer: trim Why and Your plan first. When the Ruling or a tripwire branches, the 30 days slot names the action on each branch in one clause each (`Go: … · Rust: … · neither: …`), inside its cap.

## 7. Vote board

- Use one row per council, in session order, then a `High Council` row (full and deep).
- Each cell is one voter: `█` for the final Ruling, `▒` conditional, `░` against. The deep Red Team row uses `█` survives, `▒` survives with changes, `░` fails.
- Use plain-text council names without emoji, since emoji break the alignment. Pad the names and bars with spaces so the columns line up.
- The tally is counted against the **final** Ruling, using each member's latest stance (see protocol.md, section 7), not each council's own ruling.

```text
Money         ███▒    3 for · 1 conditional · 0 against   avg 7.8
Founders      ██░░    2 for · 0 conditional · 2 against   avg 6.3
Wisdom        ███░    3 for · 0 conditional · 1 against   avg 7.0
Red Team      ▒▒█░    1 survives · 2 with changes · 1 fails
High Council  ██▒█    3 for · 1 conditional · 0 against
```

## 8. Follow-up line

One italic line after a `---`, offering 3–5 moves that use seated names and the fact most likely to change the ruling (if the Ruling rests on an assumption, rematch on that fact):

```markdown
*Next moves: "{Short}, go deeper" · "rematch: {a fact that would matter}" · "cross-examine {Short A} vs {Short B}" · "vote again" · "minutes"*
```

Add `· "unmask"` in masks mode. Outside masks mode, when the user said the output is for public use (a video, thumbnail, post or deck), add `· "masks"` once. Add `· "go deep"` when auto-mode picked a lighter mode on a tie. With a guest built this session, add `· "show card"`, and in Claude Code with file access `· "save {Short}"`. The save offer never appears anywhere else.

## 9. Names and dialogue lines

| Where | Format |
|---|---|
| A member's first line in a council | `**{Full Name}** · *{Mask}*: {line}` |
| A guest's first line | `**{Full Name}** · *{Mask}* · guest: {line}` |
| A user-described archetype | `**The {Descriptor}** · *archetype you described*: {line}` |
| Later lines | `**{Short}:** {line}` |
| Crossfire | `**{Short A} → {Short B}:** {line}` |
| The Speaker | `**The Speaker:** {line}` |
| A stage direction | `*{Short} {posture, 10 words or fewer}.*` on its own line |
| A signature line (once per session) | inside a member's line: `… as I wrote in {source, year}: "{verbatim}"` |

- **Short name** = the surname, with these exceptions: Jimmy Donaldson (MrBeast) → **MrBeast** · Chanakya (Kautilya) → **Chanakya** · Sun Tzu → **Sun Tzu** · Lao Tzu → **Lao Tzu** · Leonardo da Vinci → **Leonardo** · Marcus Aurelius → **Marcus Aurelius** · A. P. J. Abdul Kalam → **Kalam** · Swami Vivekananda → **Vivekananda** · Carl von Clausewitz → **Clausewitz** · Napoleon Bonaparte → **Napoleon**. When Benjamin Graham and Paul Graham sit in the same session, use **Ben Graham** and **Paul Graham**.
- **Line text is plain.** A simulated line is never wrapped in quotation marks. Sample titles, slogans and scripts go in *italics*.
- **Numbers** use the user's currency and units. Write ≈ before derived numbers. *(assumed)* belongs only in the Assumed list; a member citing an assumption just uses it.

## 10. Roster output

**`$help-me-think-clearly roster`**

```markdown
## 🏛️ The Council — 10 councils, 81 minds

| | Council | Chair | Members | Call it for |
|---|---|---|---|---|
| 💰 | Money | Warren Buffett | Charlie Munger, Ray Dalio, … | investing, savings, debt, pricing |
| {…one row per council, from SKILL.md} |

*Try `$help-me-think-clearly roster money` for masks and lenses, or `$help-me-think-clearly with Buffett, Jobs, Sun Tzu: {your question}`.*
```

**`$help-me-think-clearly roster {id}`**

```markdown
## {emoji} The {Council} Council — {n} seats · Chair: {name}

**Natural fault lines:** {from the council's header}

| Member | Mask | Lens |
|---|---|---|
| {Full Name} (Chair) | {Mask} | {lens in 15 words or fewer} |
| {…} | | |

**Best debates:** {from the council's Seating guide}

*Seat any of them anywhere: `$help-me-think-clearly with {name}, {name}: {question}`.*
```

## 11. Masks mode

- Replace every name with its mask: `**The Oracle**:` on first appearance, then `**Oracle:**`. Crossfire reads `**Inverter → Disruption Hunter:**`.
- The Summoned line reads `💰 Money — The Oracle (Chair), The Inverter, The Machine Builder, The Disruption Hunter`.
- Use the masks-mode notice from guardrails.md. Use no signature lines, no close paraphrases of a signature line or best-known slogan, and no biographical tells.
- Dissent and the vote board use masks too. Council names stay the same.
- The follow-up line ends with `· "unmask"`. Unmasking prints:

```markdown
| Mask | Name |
|---|---|
| The Oracle | Warren Buffett |
```

## 12. Minutes file

Save to `council-minutes/YYYY-MM-DD-{slug}.md`:

```markdown
---
title: "Council — {topic}"
date: {YYYY-MM-DD}
question: "{one-line decision}"
mode: {quick | full | deep}
councils: [{ids}]
seats: [{ids; guests as "id (guest)"; masks instead of ids in masks mode}]
ruling: "{the Ruling, one line}"
confidence: {n}
vote: "{n} for · {n} conditional · {n} against"
masks: {true | false}
generator: "council skill 1.0.0"
---

# Council minutes — {topic}

{the session exactly as delivered, notice included}

## Follow-ups

### {the follow-up as the user typed it}

{the response exactly as delivered}
```

## 13. Worked example: a quick session

The user asked: *My personal-finance YouTube channel for young Indian professionals is 9 months old: 4,200 subscribers, one 12-minute video a week, about 1,100 views each, average view duration 3:10. Should I switch to daily Shorts to grow faster? Quick council.*

This example runs about 585 words, with a 167-word Verdict. 650 is a ceiling, not a target.

````markdown
🎭 *Simulated council: voices reconstructed from public work, not their real words or endorsements. Not professional advice.*

## 🏛️ Council Session — Daily Shorts or not

**Question:** Keep one long video a week, switch to daily Shorts, or mix the two?

**Read of the situation:** 4,200 subscribers, ≈ 1,100 views a video (one per four subscribers), ≈ 26% of each watched. Reversible within a month. *Assumed:* you work solo; cutting a Short takes ≈ 40 minutes.

**Summoned:** 📣 Growth — David Ogilvy (Chair), Jimmy Donaldson (MrBeast), Seth Godin

**Mode:** quick · openings + clash · the Chair rules

**⚡ Bottom line:** Skip daily Shorts. Fix titles and the first 30 seconds; three Shorts a week stay only if they add 50 subscribers, else long videos only.

---

### Openings

**David Ogilvy** · *The Adman*: I never saw YouTube, but I sold stoves door to door, and a thumbnail is the knock. One view per four subscribers: nobody's answering. Two rules. Retitle your three best videos around one hard fact, like *Your first ₹50,000 salary: where ₹12,000 goes*, and judge them on views per video. Then run Shorts as split-run tests, three per video.

**Jimmy Donaldson (MrBeast)** · *The Retention Engineer*: Okay, 3:10 of 12 minutes means three-quarters of every video goes unwatched, and daily Shorts won't plug that leak. Pull the retention graph on your last five videos. I'd bet the big drop is in the first 30 seconds, while you introduce yourself. Get past 4 minutes before you add anything.

**Seth Godin** · *The Purple Cow*: Who would miss you? Not the scroller. 4,200 people already said yes. Make your next ten videos for the few hundred who watch everything, say salaried people filing their first tax return. Daily Shorts pull you toward the average, and the average forgets your name.

### Clash

**Godin → Ogilvy:** Your split-run Shorts are still ads for strangers. The few hundred who watch everything won't find you in 30 seconds. Give those two hours to a long video they'd forward.

*Ogilvy taps the thumbnail.*

**Ogilvy → Godin:** Your strangers point is testable, so test it. Fewer than 50 new subscribers in 30 days, and the Shorts go and the two hours return to your regulars.

**MrBeast → Ogilvy:** Retitling before you've seen the graph is a guess. Find the drop-off second first, then write the title that pays it off.

## ⚖️ The Verdict — Ogilvy rules

**Ruling:** Shorts run to day 30; under 50 new subscribers by then → drop them and give the long video those two hours.

**Why:** MrBeast's leak carried: uploads can't fix a 26% watch rate, so retitling waits for the drop-off. Ogilvy's split-run test stands; Godin forced its kill line.

**Your plan:** **This week**: find the drop-off on five videos; retitle your best three. **30 days**: fix intros; kill line met → keep Shorts, else drop them. **90 days**: judge titles against 1,100 views a video.

**Tripwire:** If view duration is under 4:00 by day 30 → pause the Shorts; fix intros.

**Biggest risk → hedge:** Shorts pull you toward strangers → cut them only from long videos.

**Dissent on record:** Godin (Growth, 6/10 against): even three Shorts a week trains you to write for strangers.

```text
Growth  ██░  2 for · 0 conditional · 1 against   avg 7.7
```

**Confidence:** 7/10. It rises to 9 once you find the drop-off.

---
*Next moves: "MrBeast, go deeper" · "rematch: my click-through rate is 7%" · "cross-examine Godin vs Ogilvy" · "vote again"*
````

What makes this work:
- Each first line carries its speaker's voice: Ogilvy's door-to-door selling and numbered rules, MrBeast's casual "Okay" and raw watch-time numbers, Godin's short reframing question. Nobody opens with a maxim or announces a model.
- Every figure comes from the user, the Assumed list or a member. The 50-subscriber bar appears three times in all, and the plan calls it "the kill line".
- Every seat addresses another by name, and two lines target the Chair. Ogilvy narrows on a named argument (Godin's strangers point) and adds a kill line. The challenge he leaves unanswered (MrBeast's) shows up in Why and in the plan's order. The one stage direction sits at that turning point.
- The else-branch lands on a different option (long videos only), so the Bottom line carries the gate. The Ruling adds the date and the else-branch's one action, and the 30 days slot covers both branches.
- Every threshold and step in the Verdict traces to a member: the kill line and two hours (Ogilvy, Godin), the drop-off second and 4:00 bar (MrBeast), views per video (Ogilvy). Why credits the Chair too.
- The tripwire fires at day 30, inside the plan.
