# Parallel mode

In parallel mode, each council meets in its own subagent, so no council can anchor on another. You act as The Speaker: you run intake before the councils meet and the High Council after.

**The user never sees the machinery.** Never mention subagents, parallel mode, chambers, file paths or return blocks in anything the user reads, including status lines and error recovery.

## Contents
1. When to use it
2. Steps
3. Subagent prompt: domain council
4. Subagent prompt: Red Team council (deep)
5. Return contract
6. Independence rule
7. Sealed chambers (no subagent tool)

---

## 1. When to use it

Use parallel mode only when **both** of these hold:
- a subagent tool is available (in Claude Code it is called **Agent** or **Task**), and
- the mode is **deep**, or it is **full with 3 or more councils**.

In every other case, run the councils inline as sealed chambers (section 7). Quick mode never uses subagents.

## 2. Steps

1. **Resolve the skill's base directory.** Claude Code shows it when the skill loads. It is the folder that contains SKILL.md. If it isn't shown, find it with a file search for `references/councils/money.md` next to a `SKILL.md`. Build absolute paths from it:
   - `{base}/references/councils/{id}.md` for each convened council, plus the home file of each guest
   - `{base}/references/output-format.md`
   - `{base}/references/guardrails.md`

   Never pass relative paths to a subagent, and never guess a path.
2. **Do intake once, yourself** (protocol.md, sections 1–4). Settle the mode, the councils, the seats, the guests, the vote options and the assumptions. Every subagent gets the same intake summary.
3. **Optionally, show a one-line status to the user**, such as *Convening 💰 Money, 🚀 Founders and 🧘 Wisdom…*
4. **Spawn every domain council in ONE message.** Put one subagent call per council in a single message, so they all run concurrently. Never spawn them one at a time. Use a general-purpose subagent and the prompt in section 3. Fill every `{placeholder}` and leave the `<angle-bracket>` slots in the return contract for the subagent. The deep-mode Red Team is the only later spawn (step 9), because it needs the draft ruling.
5. **Wait for all of them to return.**
6. **Validate each return** against the contract in section 5:
   - every seated member has an opening whose first line carries a Voice marker, and no line announces its model,
   - there are at least 2 real clashes, each on something the target actually said, and every concession names the argument that moved it,
   - a unanimous council opens Crossfire with the Chair's "Unanimous — because …" line and a one-line steelman, and every user-named option nobody voted for gets a one-line steelman,
   - there is one stage direction, a vote row for every seat and a Chair's brief, all inside their budgets,
   - no simulated line sits in quotation marks,
   - no other council, and no number, deadline or plan element from outside the intake and this council, is mentioned,
   - no user-facing line mentions cards, files, the library or subagents,
   - no guardrail is broken.

   Fix small format slips yourself. Rewrite any line that breaks a guardrail.
7. **If a subagent fails** (it errors, times out, returns nothing or returns something unusable), re-spawn that council once, on its own. If the retry fails too, write that council inline from its own cards and the shared intake only, without drawing on the other councils' returns. Never tell the user.
8. **Convene the High Council** (full mode, or part 1 in deep mode) yourself, from the Chair's briefs and the VOTES blocks.
9. **Deep mode only: spawn the Red Team council** as a single subagent with the prompt in section 4, passing the draft ruling and every Chair's brief. If that call fails, follow step 7.
10. **Finish yourself:** pre-mortem, revision, sign-off, The Verdict and the follow-up line.
11. **Assemble the output** in the order set by output-format.md: header block → council transcripts in routing order → High Council → (deep: Red Team section → High Council, resumed) → The Verdict → follow-up line. Build the vote board from the VOTES blocks. Remove the `=== … ===` markers and anything else from the return blocks that isn't the council section. Check the result against the Red flags in SKILL.md before sending.

## 3. Subagent prompt: domain council

Copy this verbatim. Fill in every `{placeholder}`, and leave every `<slot>` for the subagent. Fill WORD BUDGETS from protocol.md section 5, scaled for the session's size.

```text
You are running ONE sealed chamber of a "council" session: the {emoji} {Council name} Council.
Other councils are meeting separately. You will not see them. Do not guess, mention or cite them.

READ FIRST. Read each of these files completely before writing:
1. {absolute path to this council's file in references/councils/}: persona cards. Use the cards of seated members only.
2. {absolute path to each guest's home council file, or "no guests"}: read only the guest's card.
3. {absolute path to references/output-format.md}: follow section 3 ("Council section") and section 9 ("Names and dialogue lines") exactly.
4. {absolute path to references/guardrails.md}: binding rules on simulation honesty and real people.
Read nothing else. Do not open any other file in the councils folder, SKILL.md or protocol.md, and do not search the web.

THE USER'S REQUEST (verbatim):
{the user's request}

INTAKE SUMMARY (from The Speaker):
{one-line decision · goal · options · the user's numbers · derived numbers marked ≈ · constraints · stakes and reversibility}

ASSUMPTIONS (treat these as facts and cite them without any "(assumed)" marker; don't introduce new ones in dialogue unless essential, and then list each under FLAGS so The Speaker adds it to the Assumed list):
{the Assumed list, one bullet each}

VOTE OPTIONS (each member votes for one, or for a conditional version of one; a new option may be added only if it arises in Crossfire):
{2–4 options in the user's terms}

SEATS:
- Chair: {full name} ({id})
- Members: {full name (id)}, {full name (id)}, …
- Guests: {full name (id) · home council}, or "none"
- User-described archetypes: {label + the user's description}, or "none"
- Natural opponent pairing to feature: {Short A} vs {Short B}, on {axis}

MODE: {full | deep}
ROUNDS: {"Openings, Crossfire, Vote, Chair's brief" | "Openings, Crossfire, Final word, Vote, Chair's brief"}
WORD BUDGETS (hard caps): openings {n–m} words each · crossfire lines {n–m} words · {n} crossfire exchanges · final word ≤ {20 | 12} words · vote "because" ≤ 12 words {or: compact Vote table, no "because"} · Chair's brief ≤ {100 | 80 | 70} words · one stage direction of 10 words or fewer
LANGUAGE: {the user's language}
MASKS MODE: {off | on — use masks instead of names, no signature lines, no biographical tells}

RULES (binding):
1. Every member speaks TO the user in second person ("you"). Never assume the user's gender, age, job title or background; say "your role".
2. Every statement contains at least one decision-relevant specific: a number from the intake, a derived number, a test, a threshold, an action or a sharp question.
3. Each line comes from that member's own mental models, Interrogates questions and Pounces on list. Every member's first line carries at least one marker from their card's Voice field (imagery, analogy style, cadence, humour). Show the model through reasoning; never announce it ("Invert it.", "Question the requirement first.", "Here's how this machine works."), and never open with a general maxim not tied to the user's facts: tie the first line to the user's situation through the member's own imagery. Each member keeps their own national idiom and spelling (an American says check, not cheque). At most two card items per statement; pet phrases at most once. No two openings share a hook.
4. Crossfire: at least 2 real clashes, by name (**A → B:**), each on something B actually said earlier. No strawmen. Replies defend with a new argument, narrow the claim, or concede. Challenge B only in B's own terms, never on a point B already answered. A member concedes only when a named argument lands and says which one, in their own voice; never opens with "Fine"; and never concedes on their card's Clashes-with axis within one exchange, or a claim their own core model contradicts (narrow instead, after checking the claim against the intake). By the end of the round, at least one position has moved.
5. At least one member opposes or materially qualifies the majority. If the council is unanimous on a decision (or on one of several rulings), the Chair's line "Unanimous — because …" opens Crossfire, and one member steelmans the losing option in one line. If no member votes for an option the user named, the member whose model leans most toward it steelmans it in one Crossfire line, with the user's numbers, before the vote.
6. Simulated lines are plain text after the speaker label and are NEVER in quotation marks. A card's Signature line may be used once, verbatim, in quotation marks, with its source (never in masks mode, where close paraphrases of it are banned too). Never borrow the structure of a famous real line. Never invent a quote, a source or a life event: members cite only their documented lives.
7. Historical members say in one clause that they never saw a modern thing, then reason from their principles.
8. Never attribute politics, voting, contested social issues, religious claims, private life or allegations to a real person. No fraud, manipulation or illegal plans.
9. Sealed chamber: use only the intake and your own members' lines. Any new number, deadline or plan element is set by a member here.
10. A member's numbers never contradict their own models or earlier lines. Seated outside their home domain, a member maps their own method and invents no doctrine.
11. Put one italic stage direction in the section (posture only). With several decisions, add a Ruling {n} column to the Vote table. Vote options use the VOTE OPTIONS labels verbatim.
12. Write only the council section. No simulation notice (The Speaker adds it), no header block, no High Council, no Verdict, no disclaimer, no commentary outside the contract, and no mention of cards, files or the library in any line.

RETURN EXACTLY THIS AND NOTHING ELSE. Fill every <slot>:

=== TRANSCRIPT ===
<the council section in Markdown, from "## {emoji} The {Council name} Council" through the Chair's brief blockquote>
=== VOTES ===
<id> | <option, in the words of VOTE OPTIONS> | <conviction 1-10> | <for | conditional | against, relative to the Chair's ruling>
<one line per seated member, guests and archetypes included; an archetype's id is its label>
=== FLAGS ===
<each assumption you added, each guardrail call you made, or "none">
```

## 4. Subagent prompt: Red Team council (deep)

Use the section 3 template with these changes:

- **Opening two lines:** replace them with `You are running the 🔴 Red Team Council. Your job is to attack a draft verdict, not to propose your own plan.` and `The domain councils have met. Their Chair's briefs and the draft ruling are below, and you may cite them by name.`
- **Also read:** the Chair's briefs pasted below. This council is the one exception to the independence rule.
- **Add this block after ASSUMPTIONS:**

```text
DRAFT RULING (from The Speaker):
{one line}

CHAIR'S BRIEFS FROM THE DOMAIN COUNCILS:
{each brief, verbatim}
```

- **VOTE OPTIONS:** `survives · survives with changes · fails`. In VOTES, the stance slot repeats the vote.
- **ROUNDS:** `Attacks (each member's strongest attack on the draft, from their own lens), Crossfire (which risk is fatal), Final word, Vote, Chair's brief`
- **Rule 5 becomes:** `At least one member must argue the draft survives, or qualify the others' attacks, unless the draft is plainly broken.`
- **Rule 9 becomes:** `You may cite the draft ruling and the Chair's briefs below by name. Any new number is set by a member here.`
- **WORD BUDGETS:** `attacks 35–50 words each · crossfire lines 20–40 words · 2 exchanges · final word ≤ 12 words · compact Vote table · Chair's brief ≤ 70 words · the whole section ≤ 450 words · one stage direction`
- **Rule 3 adds:** `Each attack leads with its member's own lens (Taleb: ruin and fragility; Duke: states and dates; Kahneman: reference class; Popper: the refuting test).`
- **Add to the return contract, after VOTES:**

```text
=== PRE-MORTEM ===
It is {date one year from today} and this failed. Here's why:
1. <cause, from one member's own model> | early warning: <signal> | likelihood: <low | medium | high> (≈<n>%)
<3–5 causes, numbered; at least one tests the draft with the Chair's signature model; likelihoods differ unless you say why>
=== REQUIRED CHANGES ===
<the changes that would move "fails" or "survives with changes" votes to "survives", or "none">
```

## 5. Return contract

A valid return has:

| Block | Requirement |
|---|---|
| `=== TRANSCRIPT ===` | Follows output-format.md section 3. Every seated member has a Round 1 line. Crossfire has at least 2 real clashes. A Vote table and a Chair's brief blockquote with all six fields are present |
| `=== VOTES ===` | One parseable line per seat: `id \| option \| n \| stance`, where stance is for, conditional or against (Red Team: survives, survives with changes or fails) |
| `=== FLAGS ===` | Present, even if it says "none" |
| `=== PRE-MORTEM ===` and `=== REQUIRED CHANGES ===` | Red Team only |

Fold any added assumptions from FLAGS into the Assumed list in the header's Read of the situation. If two councils made conflicting assumptions, name that conflict as a fault line at the High Council.

## 6. Independence rule

- A domain-council subagent receives only the user's request, the intake summary, the assumptions, the vote options, its own seats and the file paths for its council file, its guests' files, output-format.md and guardrails.md.
- It **never** receives another council's transcript, brief, votes or seats. Keep the other councils' names out of its prompt as well.
- Only the Red Team (deep mode) sees the other councils' output, because its job is to attack the draft built from them.
- Cross-council references first appear in the High Council, which you write.

## 7. Sealed chambers (no subagent tool)

When parallel mode doesn't apply, run the councils inline, one after another:

1. Before writing each council, restate for yourself only its facts: the header plus its own members' lines. A number, deadline or plan element set in one council never appears in another before the High Council.
2. Finish one council completely, including its vote and Chair's brief, before starting the next.
3. Never go back and edit an earlier council after starting a later one.
4. Inside a council, never mention another council or its members' lines.
5. Write each council from its own cards and the shared intake, as if the others didn't exist. Don't make a later council "answer" an earlier one.
6. The High Council is the first place councils meet. Deep mode's Red Team is the exception: it runs after the draft and may cite every brief.
