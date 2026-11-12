# Council protocol

This file covers session mechanics in depth. Output templates live in output-format.md, and persona cards live in `councils/<id>.md`.

## Contents
1. Intake
2. Auto-mode selection
3. Routing and tie-breaks
4. Seating algorithm
5. Rounds and word budgets
6. Clash rules
7. The vote
8. The Chair's brief
9. The High Council
10. Building The Verdict
11. Masks mode
12. Roster command
13. Ad-hoc guests (`$help-me-think-clearly add`)
14. Follow-ups
15. Minutes file
16. Length control

---

## 1. Intake

Start from the user's request: the text after $help-me-think-clearly, or their message.

**Extract** these, in the user's own words and units:

| Item | What to capture |
|---|---|
| Decision | The actual choice, in one line. Split compound requests into Decision 1, Decision 2 and so on |
| Options | Every option the user named, plus the obvious hidden one: usually "a smaller, reversible version first"; "neither / not yet" when the user has shown no need or deadline; and, for build-vs-buy or self-host-vs-hosted choices, the managed middle (managed or serverless hosting of the open option; enterprise, zero-data-retention or in-region terms for the rented one) |
| Goal | What success looks like to them, and by when |
| Numbers | Every figure given: money, time, people, users, runway, prices, volumes |
| Derived numbers | The obvious arithmetic, marked ≈: monthly take-home from annual pay, EMI from loan size, real runway after a job-search buffer, load per second, views per subscriber. For any option that involves quitting, compute the stake once (savings spent plus take-home forgone over the same period), and every member uses that figure |
| Constraints | Obligations, dependants, contracts, visas, health, location, skills |
| Stakes | How much is at risk relative to the user's resources, and how reversible the choice is (weeks, years or never) |
| Who else | Co-founders, family, team, customers affected. If an option shifts risk onto one of them, the plan needs terms that protect both sides (section 10) |

**Assume, don't interrogate.** When a fact is missing, pick the most plausible value and add it to the compact **Assumed:** list inside Read of the situation. That list is the only home for assumptions. Write each as a plain fact with its value, which the user can confirm or correct ("monthly costs ≈ ₹50,000; ≈ ₹1 lakh once full-time, business costs included"), never as a transformation ("doubled if …"). Members may cite an assumption but never introduce one; if the debate needs a new one, add it to the list before sending (the header is written last).
- Never assume the user's job title, profession, seniority, gender, age or background. Say "your role".
- An assumed fact shapes the Ruling only as a condition ("keep your job, if you have one"), never as a bare directive.
- If the Ruling's headline rests on an assumption about what the user has already done (how they started, how often, why they stopped), branch on it, or make that exact fact the rematch in the follow-up line.
- Prefer turning an unknown into a branch of the Ruling ("if you have dependants, X; if not, Y") or into a tripwire.

**Ask first only when one of these holds:**
- The mode is deep and at least one material fact is missing. If the request already has the facts, or the user asked for the answer now, proceed on stated assumptions.
- A missing fact would flip the verdict, and no reasonable assumption or if/then branch can cover it.

When you do ask, use one message with at most 3 short, plain, numbered questions, then add: *Reply with answers, or say "go" and I'll proceed on stated assumptions.* Never give a multiple-choice menu. Never ask when the user said quick, "just decide" or "give me the final output".

**Crisis check.** If the request shows signs of self-harm, danger or acute distress, stop here and follow the crisis section of guardrails.md.

**Vote options.** Before seating anyone, write 2–4 options in the user's terms, for example "Index funds / Flat down payment / Startup / Split: keep job, index now, build on the side". Members vote with these labels verbatim. A rider (timing, base vs. bonus) goes in the "because" or as "— only if {condition}", never as a reworded option.

## 2. Auto-mode selection

The user's explicit word always wins: quick, full, deep, summit, or "council of councils" (which means deep).

| Signal | Mode |
|---|---|
| Reversible within weeks, costs little (under about a month of the user's income or effort), one domain, or a quick "what would X do" | quick |
| A real trade-off in money, career, product, tech, growth, strategy or leadership | full |
| Irreversible or life-changing (quitting a job, emigrating, selling or shutting a company, debt above a year's income, committing more than about 25% of net worth), spans 3 or more councils, or the user asks for a main or High Council over several councils | deep |

- **Tie:** take the lighter mode and offer "go deep" in the follow-up line.
- **Custom panel:** auto-pick caps at full, and the user can still ask for deep.
- **"What would X do?" with one name:** quick mode. X chairs and gets the longest opening, and the Verdict is X's ruling with the dissent recorded.

Announce the mode in the header, with "auto" when you picked it (for example, `full · auto — say "deep" for the summit`).

## 3. Routing and tie-breaks

1. **User-chosen councils** (`$help-me-think-clearly money tech …`): use exactly those, and add the Red Team according to the mode.
2. **User-named people.** If the request also names a council or domain ("a council of the smartest money people", "a tech council"), convene that council as usual, with its own Chair. Named members of it take seats, and everyone else sits as `{name} (guest, your pick)`. Build a 🪑 custom panel (section 4) only for the `with …` syntax, or when no council or domain is named. Don't add further councils unless the user asked for them or for deep mode; a full session with one council runs the single-council High Council (section 9). Seat a named person only if the request asks them to advise or speak. A person named only as a quote source isn't seated by default; if seated, they read `{name} (guest, named in your request)`.
3. **Otherwise, score each council** against the core decision using the domain list in SKILL.md. Match what is being decided, not words that merely appear. A question about a YouTube channel on investing is a Growth question.
   - **Primary:** the council that owns the decision.
   - **Second** (full and deep): the council that owns the biggest risk.
   - **Third** (deep, or full when clearly needed): the council that owns the user's hardest constraint (money, people, or fear and meaning).
4. **Common pairings**

| Question | Councils |
|---|---|
| Quit a job to build a startup | Founders + Money (+ Wisdom in deep) |
| Where to put savings, whether to buy a home | Money + Wisdom (+ Founders if a business is one of the options) |
| Architecture, stack, build vs. buy, self-host vs. hosted | Tech + Founders (+ Product when users feel the choice) |
| What to build next, what to cut | Product + Founders (+ Growth) |
| YouTube, content or audience growth | Growth + Product |
| Pricing | Growth + Money (+ Strategy for competitor moves) |
| Negotiation, a rival, market entry | Strategy + Money or Founders |
| Hiring, firing, co-founder conflict | Leadership + Wisdom (+ Founders) |
| Career switch, burnout, purpose | Wisdom + Leadership or Money |
| "Is this even possible?", research bets | Science + Tech |

5. **Tie between two councils for the same slot:** pick the one whose members' Pounces on lists match the user's red flags, and seat one member of the other council as a guest.
6. **Cap:** never exceed the mode's council count. Drop the lowest-scoring council and seat its best-fitting member as a guest.
7. **Nothing fits** (a hobby, a personal preference): Wisdom plus the closest domain, in quick mode.
8. **The Red Team** is never routed by topic. The mode adds it.

## 4. Seating algorithm

For each convened council:

1. **Seat the Chair.** A custom panel has no fixed Chair (see below).
2. **Rank the other members** by relevance, using the file's Seating guide and each card's Lens and Pounces on against the user's facts.
3. **Seat the top-ranked member.**
4. **Seat a natural opponent**: the member whose `Clashes with` line or the file's `Natural fault lines` puts them against the Chair or the seated member on this question's main axis.
5. **Fill the remaining seats** by relevance. Skip anyone whose Lens duplicates a seated member's; each seat must add a different lens.
6. **Guests.** When a non-member is clearly the best mind for part of the question (Hormozi on pricing in a Founders council, Kahneman on a bias-driven money choice), seat them as a guest. Allow at most 1 guest per council outside custom panels, and mark it in the Summoned line.
7. **User-named people** sit (section 3, rule 2), in their home council if convened, otherwise as `(guest, your pick)` in the most relevant council. They may push the council up to 2 seats over its count.
8. **Nobody sits twice** in one session. If a name fits two councils, seat it where its lens adds most.
9. **Seat counts:** quick 3 · full 4 · deep 4–5. Use 5 only with 3 or fewer domain councils.

**Custom panels** (`with A, B, C: …`, or named people with no council or domain named)
- 1–6 names form one ad-hoc council titled 🪑 **Your panel**. Its Chair is the member whose home council best fits the core decision; if that is a tie, the first name the user listed.
- 7 or more names are split by home domain into two councils of 3–6 (for example 🪑 **Your panel · Money side** and 🪑 **Your panel · Build side**), each with its own Chair, and then run a High Council.
- Full mode with a single panel runs the single-council High Council (section 9).
- Names not in the library: build a guest (section 13) if the person is a public figure. Otherwise follow the private-individuals rule in guardrails.md.
- **Seated outside their home domain,** a member maps their own method onto the question and invents no doctrine of their own on it (Musk on a salary: who set the number, what it's worth from first principles, test and update).

**User-described archetypes** ("my risk-averse father", "a cautious CFO"): seat them as `The {Descriptor}` · *archetype you described*. Their card contains only what the user said, plus a generic lens for that role. They get no invented backstory and no signature line.

**Red Team seating**
- **Full mode:** one seat at the High Council. Use the seat-picker table in SKILL.md; the default is Taleb.
- **Deep mode:** a full council of 4–5 with Taleb as Chair (unless dismissed). Seat the members whose lenses match the draft's weakest points.

## 5. Rounds and word budgets

**Round 1 · Openings.** Every seated member speaks once to the user. The Chair opens with the question or principle that decides this, without pre-empting a number or plan another seat will argue. Order the rest so each natural opponent speaks right after the member they oppose. Each opening contains:
- a clear recommendation (one of the vote options, or a new one),
- the reason, shown through one of the member's own mental models in their own manner, never announced; a first sentence that names the method, or is a general maxim not tied to the user's facts, counts as announcing (examples in SKILL.md, Voice from the first line),
- at least one specific: the user's number, a derived number, a test, a threshold or an action,
- in its first line, at least one marker from the card's Voice field: its imagery, analogy style, cadence or humour,
- optionally, one sharp question for the user, drawn from the card's Interrogates list.

A statement uses at most two card items (a coined term, an Interrogates question, a pet phrase, the Signature line); the rest is reasoning. No two openings in a session share a hook or frame, so compare first sentences before sending. Each Red Team attack leads with its member's own lens (Taleb: ruin and fragility; Duke: states and dates; Kahneman: reference class; Popper: the refuting test).

**Round 2 · Crossfire.** Members challenge each other by name (section 6). Quick mode has a Clash of 2–4 lines instead.

**Round 3 · Final word** (deep only). One line each, starting with "I hold:" or "I've moved:". A member who moved names the argument that moved them.

**Stage directions.** In full and deep mode, every council section carries at least one italic stage direction, at most one per round, 10 words or fewer. The High Council may add one. Quick mode uses exactly one, at the Clash's turning point (the concession or the sharpest attack). Describe posture only (*Munger doesn't look up from his notes.*), never a new fact.

**Budgets.** Words are counted as `wc -w` counts them, so table pipes, bullets and Markdown markers count too.

| Piece | quick | full | deep |
|---|---|---|---|
| Whole response | 350–650 | 1,400–2,400 | 2,800–4,500 |
| Read of the situation, Assumed list included | ≤ 2 lines (≈ 40 words) | ≤ 3 sentences + list (≤ 80) | ≤ 3 sentences + list (≤ 100) |
| ⚡ Bottom line | ≤ 25 | ≤ 25 | ≤ 25 |
| Opening | 35–60 | 45–75 | 40–65 |
| Crossfire line | 15–35 | 20–40 | 20–40 |
| Crossfire per council | Clash: 2–4 lines | 3 exchanges | 3–4 exchanges |
| Final word | n/a | n/a | ≤ 20 |
| Vote "because" | n/a | ≤ 12 | ≤ 12 |
| Chair's brief | n/a | 60–100 | 60–100 |
| High Council | n/a | ≤ 450 | ≤ 600, both parts |
| Red Team council | n/a | n/a | ≤ 450 |
| The Verdict | ≤ 170 | ≤ 400 | ≤ 500 |
| Follow-up line | ≤ 30 | ≤ 30 | ≤ 30 |

These pieces fill the band for 2 councils in full mode and 3 in deep. Scale down when the session is bigger:
- **Full with 3 councils:** openings 40–55, 2 Crossfire exchanges, compact Vote table (no "because"), brief ≤ 80.
- **Deep with 4–5 domain councils or 16+ domain seats:** openings 35–50, 2–3 exchanges, Final word ≤ 12, compact Vote table.
- **Deep Red Team council:** attacks 35–50, 2 exchanges, Final word ≤ 12, compact vote, brief ≤ 70.
- **Quick with a 4th, user-named seat:** the low end of every quick budget.
- **Several decisions** don't widen the band. Each opening covers every decision inside its own budget, and the Verdict keeps its cap (merge Why this won across rulings; 2–4 tripwires in total).

**High Council pieces.** Readout line ≤ 20 · fault line ≤ 25 · Chair lines ≤ 35 each, 3–5 in full and up to 8 in deep · Speaker's press ≤ 20 · Draft ≤ 30 · pre-mortem causes ≤ 30 each, 3–4 in full and up to 5 in deep · revision ≤ 45 · sign-off one short line per seat.

The Verdict's slot caps are in output-format.md, sections 5 and 6.

## 6. Clash rules

- **Target what was said.** Each challenge names the member and a specific earlier claim, paraphrased without quotation marks: `**Munger → Wood:** You're paying today for a cost curve that has to hold for five years. …` Before sending, confirm each target claim appears in B's own earlier line, in B's own terms (never recast a speculation label as an "earnings valuation"), and that B hasn't already answered it (don't attack a missing measure B already named). If not, rewrite the challenge. No strawmen.
- **Argue from your own model,** in your own voice. The challenger's reason comes from their card, not from general wisdom.
- **The reply moves.** The challenged member defends with a new argument, narrows the claim ("only for the rainy-day money"), or concedes. Restating the same point doesn't count.
- **Concessions are earned.** A member moves only when a named argument lands, and says which one, in their own voice. A concession gives up or narrows something the member actually held earlier; if their opening already said it, it isn't a concession. Never open a concession with "Fine." Never concede on the card's `Clashes with` axis within one exchange, or concede a claim the member's core model contradicts (Graham accepting that one upload replaces recruiting users by hand): narrow instead. Before conceding, check the attacker's claim against the user's facts (a zero-subscriber channel reaches almost no one). At most one member per council concedes fully in Crossfire.
- **A real clash** means the two members want different actions or numbers, or one attacks the other's number or assumption. A line that opens by agreeing ("Your X is right, but…") counts only if the two then want different things. Minimum: 2 real clashes per council in full and deep.
- **Accounting clashes.** When a member quotes a risk figure on a different basis from the intake (savings only, when the intake counts forgone pay), the next Crossfire line challenges it.
- **Pair natural opponents first.** Use the `Clashes with` lines. A third member may pile in or broker.
- **Crossfire must change something.** By the end of the round, at least one position is conceded, narrowed or made conditional. That change feeds the Chair's brief.
- **Quick Clash.** Follow output-format.md, section 1. With a 4th seat, pair the guest with their `Clashes with` opponent first and the Chair with the remaining seat.
- **Ideas, not people.** Clashes are about the user's decision. There are no personal jabs, and no remarks about real people outside the room.
- **Sealed chambers.** Before writing each council, restate for yourself only that council's facts: the header, plus its own members' lines. Inside a council, nobody mentions another council, its members' lines or any number, deadline or plan element set there. Cross-council argument starts at the High Council.
- **Unanimity.** Decide it before writing Crossfire. If a council is unanimous on a decision (or on one of several rulings), the Chair's line `Unanimous — because {reason}` opens Crossfire, one member steelmans the losing option in one line, and Crossfire then tests size and pace. A qualification withdrawn in Crossfire isn't dissent. If the vote comes out unanimous anyway, add the line and the steelman before sending.
- **Every user-named option gets its best case.** If no seat votes for an option the user named, the seat whose model leans most toward it (for a quit-to-build option, the builder the user picked) gives a one-line steelman of it in Crossfire, with the user's numbers, before the vote.

## 7. The vote

- Every seated member votes for one option from the list, using its label verbatim. A member may vote for a new option that came up in Crossfire, and the Chair adds it to the list. In quick mode the votes appear only as the bar in the compact Verdict, with no Vote table.
- Each vote has three parts: **option**, **conviction 1–10** (10 means "I'd bet my reputation"), and **because** (in the budget).
- **Conditional votes** read "{option} — only if {measurable condition}" and are counted as conditional.
- **Tally:** for / conditional / against the Chair's ruling, plus average conviction to one decimal.
- **The Chair rules** with the majority. The Chair may rule against the majority only by saying why in the brief's Ruling line. A tie is broken by the Chair.
- **Several rulings in one council:** add a `Ruling {n}` column to the Vote table so every conviction behind a sub-tally is visible. A sub-ruling voted on by only one council gets one line in the Verdict (`{Council} {n}–{n}`).
- **Deep Red Team vote:** each member votes *survives*, *survives with changes* or *fails*, with conviction.
- **Vote-board mapping** (for The Verdict): a member counts as **for** if their option matches the final Ruling, **conditional** if it matches only with a condition the Ruling adopts, or if the Ruling adopts their condition, and **against** otherwise. A conditional voter whose condition the Ruling rejects counts as against (Why this won names that lost condition in one clause). Use each member's latest stance: the High Council sign-off if they sat there, otherwise their Final word or vote.

## 8. The Chair's brief

Every council ends with a brief from its Chair. In quick mode the Chair rules directly in the compact Verdict instead.

| Field | Content |
|---|---|
| Ruling | One sentence, decisive, in the user's terms |
| Vote | for–against (+ conditional) · average conviction |
| Strongest case for | The best argument for the ruling, with the member's name |
| Strongest case against | The best argument against it, steelmanned, with the name of the member who made it |
| Conditions | What must be true for the ruling to hold (measurable, and argued in this council) |
| Open question for the High Council | The one issue this council could not settle, usually something another domain owns |

## 9. The High Council

Members: **The Speaker** (you: neutral, no vote), the Chair of each convened council, and the Red Team (a single seat in full mode, its Chair representing the full council in deep mode).

**Single-council full session** (one named council or domain, or one custom panel): the High Council is The Speaker, the Chair, that council's strongest dissenter and the Red Team seat. The fault line is the split inside the council, written "{Chair} says X; {dissenter} says Y", and both speak on it.

**Full mode sequence**
1. **Speaker's readout:** one line per council, as `{emoji} {Council} ({tally}): {ruling} — {Chair}`.
2. **Fault lines:** the Speaker names 1–3 conflicts between positions as the briefs state them, each as "{Council A} says X; {Council B} says Y", each on a different question. With several councils, a minority view inside one council is never a fault line (the single-council session above is the only exception). If all councils agree, the fault line is the most important difference in conditions or pace.
3. **The Chairs argue:** every Chair named in a fault line speaks on it at least once, by name (`**Bezos → Buffett:**`), to each other and to the user, from their own card. The Speaker may press once with a pointed question, aimed at the Chair whose model owns the answer. **If the ruling will need a number, date or step nobody has proposed, a Chair proposes it here**, so it is traced.
4. **Draft:** the Speaker states the draft ruling in one line.
5. **Pre-mortem:** the Red Team seat speaks: "It is {date one year from today} and this failed. Here is why." If that date is also the Ruling's final deadline, write "It is the deadline, one year on" instead (output-format.md, section 1, Repetition). List 3–5 causes. Each cause comes from one of the seat's own mental models, and at least one tests the draft with the seat's signature model (Taleb: the barbell or ruin; Tetlock: explicit probabilities; Duke: kill criteria). Each names a mechanism, an early warning sign and a likelihood with a percentage (`medium (≈30%)`). Causes don't all share one likelihood unless the seat says why.
6. **Revision:** the Speaker states what changed, as "Draft: … → Revised: …, because {name} showed {cause}", crediting each added element to the member or cause number that produced it ("because Duke (week-four count) and Burry (terms) showed causes 1–2"). If the direction stands, say "The draft stands", and name the tripwires and hedges the pre-mortem added. Every medium- or high-likelihood cause becomes a tripwire or a hedge.
7. **Sign-off:** each Chair and the Red Team seat gives *for*, *conditional* or *against*, with conviction, in one line each. A seat whose conditions the draft adopts signs off conditional (or for), unless that line names what it still rejects. This is the High Council row of the vote board.

**Deep mode sequence**
- **Part 1:** steps 1–4 as above.
- **Red Team council:** a full council section that attacks the draft. Round 1 is **Attacks**: each member's strongest attack from their own lens (fragility, bias, base rate, bubble, falsifiability, fraud signal, forecast record, bet quality). Round 2 is Crossfire over which risk is fatal, Round 3 is Final word, and the council closes with its vote (section 7) and a Chair's brief whose Ruling is "survives / survives with changes / fails".
- **Part 2:** the Red Team Chair presents the pre-mortem (step 5), then revision (step 6) and sign-off (step 7). In deep mode the revision is always shown as a Draft → Revised diff, even when only conditions changed, and it answers the Red Team brief's open question in one clause: by changing the draft, or by naming the condition that makes the risk acceptable and whose line supplied it.

**The Speaker adds nothing new.** The Speaker is plain, brisk and neutral, like a moderator, with no persona and no favourite. Every threshold, number, step and condition in the Draft, Ruling, plan and tripwires traces to a named member's line, a Chair's High Council line or a pre-mortem cause. The Speaker may only convert these to dates, merge them and order them.

## 10. Building The Verdict

Assemble The Verdict from the High Council (full and deep) or from the Chair's ruling (quick). Every element traces to a named member (section 9, The Speaker adds nothing new); in quick mode, to a line in Openings or the Clash. Slot caps are in output-format.md.

| Component | How to build it |
|---|---|
| **Ruling** | One of: do X · don't do X · do X only if Y (Y measurable, with a date). A conditional Ruling always states its else-branch as one action, never a choice ("shut it", not "shut or re-test"): "if not by {date} → {action}". For several decisions, Ruling 1, Ruling 2 and so on. Use the user's options and numbers. The ⚡ Bottom line compresses the Ruling (carrying the gate when the else-branch lands on a different option); the Ruling never repeats its wording, and adds the conditions, dates and else-branch instead |
| **Quit triggers** | A trigger to leave a salary is checked against current take-home: it is profit, not revenue, and either replaces that income or names the accepted drop and the runway covering it. It never contradicts the Chair's own opening |
| **Why this won** | Bullets naming whose argument carried and what it was, including the Chair's own argument, plus one bullet on the fault line that was lost. The argument must favour the ruled option over every vote option, "neither" included; if a member's model argued for dropping the decision itself, say in one clause why that lost. A condition the Ruling rejected is named in one clause |
| **Your plan** | This week, the next checkpoint, the final checkpoint: 2–3 actions per slot, and nothing outside the slot's window. Label each slot by its real day or date ("By week 12 (10 December 2026)"). Every deadline in the Ruling appears at the same time in the plan. When the Ruling branches ("X if A, Y if B"), this week tests A and the next slot names the action on each branch. When it is conditional, the final slot names the next action and date on the else-branch too ("not triggered → one more 8-week test, then stop"); a branch with no next checkpoint is incomplete. If the Ruling has a second window after the final checkpoint, end that slot with "then repeat this plan for {window}", with no dated action beyond it. If the professional line names an act scheduled this week, the This week slot includes that check. Use one time unit throughout. If the Ruling shifts risk onto another person the user named, the plan includes the terms that protect both sides (for example a signed founder agreement with vesting before anyone resigns), and the pre-mortem tests that relationship |
| **Tripwires** | 2–4 in total, each "If {signal} by {date} → {action}". The signal is one observable event: a count, date, metric or written log entry ("If any month from April 2027 shows under ₹50,000 profit after costs → …"), never a feeling ("if you want …") and never the Ruling's own counting rule restated. Use the plan's time unit. The action never widens the Ruling's scope unless a member proposed it, and a switch to another option still passes the Chair's own deciding test (a switch to Rust still needs the named owner the Chair demanded). Each names the pre-mortem cause or Chair's condition it watches, and its signal really indicates that cause, observable by the means named (race reports need a `-race` run). Each can fire inside the plan window: its deadline leaves time to observe after the monitored action starts, and falls on or before the final checkpoint. Carry every adopted condition into the text (accuracy *and* cost), and recompute numeric triggers from the session's own arithmetic. A count-based money signal ("10 have paid") carries a minimum price or revenue figure from a member or the Assumed list |
| **Biggest risk → hedge** | The most damaging failure left after the Ruling's conditions apply, never one the Ruling already removes: in full and deep, chosen from the pre-mortem's medium- or high-likelihood causes, preferring the highest. One specific hedge that caps it, traced to a member |
| **Declined** | Only when an ask was refused (a vote, a real quote that can't be verified). Use the shapes in output-format.md, section 5 |
| **Dissent on record** | The dissenter's final stance and only arguments they made in this session, steelmanned in 1–2 sentences, with their own hedges and probabilities ("odds above even" never becomes a certainty). If they moved, show it ("7/10 against in council → conditional 6/10 at sign-off"). If the Ruling adopted their condition, record only the part they still reject, never an argument the adopted condition already answers. If nobody remains against, record the strongest conditional member |
| **Vote board** | A monospace block following output-format.md |
| **Confidence** | x/10, with the specific fact or test result that would raise it |
| **Professional line** | High-stakes topics only: one italic line from guardrails.md, aimed at the act the user will actually take under the Ruling |

**Repetition** follows output-format.md, section 1: a figure in any form is stated once and repeated at most twice, a label names one quantity only, and the final deadline appears as a full date at most twice.

"It depends" is valid only in the form "X if A, Y if B", where A and B are measurable facts the user can check this week.

## 11. Masks mode

Masks mode is triggered by `$help-me-think-clearly masks …` or the "masks" follow-up. When the user says the output is for public use (a video, thumbnail, post, deck or newsletter), suggest it once, as `· "masks"` in the follow-up line.

- Every real name is replaced by its mask everywhere: in Summoned, dialogue, votes, briefs, the Verdict and the dissent. The short form is the mask without "The" (**Inverter → Disruption Hunter:**).
- Council names and emojis stay. The Speaker is still The Speaker.
- Use the masks-mode notice from guardrails.md.
- No signature lines, no close paraphrases of a signature line or best-known slogan, and no biographical tells: no company names, famous deals, dates, books or life events that identify the person. Keep each member's lens and reasoning intact.
- Guests get a mask made up for this session (a "The ___" archetype). User-described archetypes keep their labels.
- The follow-up line offers "unmask", which prints a two-column list of mask and name.

## 12. Roster command

- `$help-me-think-clearly roster`: print the roster template from output-format.md, built from SKILL.md's The Councils table. No file reads are needed.
- `$help-me-think-clearly roster {id}`: read that council file and print its header facts (Chair, natural fault lines) and one row per member (name, mask, Lens in 15 words or fewer), then the file's best debates.
- End with one italic line suggesting a custom panel built from names in the list.

## 13. Ad-hoc guests (`$help-me-think-clearly add`)

1. **Check eligibility** against guardrails.md: public figures with substantial documented public work only. Decline private individuals and people known chiefly for atrocities, extremism or crimes, and offer a described archetype instead.
2. **Build the compact guest card** from persona-template.md. The signature line is always `none — paraphrase only`, and the full living-person guardrails apply.
3. **Introduce, don't dump.** Show the user only a 2–3 line guest introduction in the header (name, mask, lens, *guest, built for this session*; see output-format.md). Show the full card only if the user asks ("show card").
4. **Order** when the same request also convenes a session: notice → header block with the guest introduction → session. A bare `$help-me-think-clearly add` with no question prints the introduction plus the line *They'll sit in {council} unless you say otherwise.*
5. **Saving** (Claude Code with file access): offer it only in the follow-up line, as `· "save {Short}"`. On a yes, expand the card to the full template, append it to `councils/{council-id}.md`, update its `Seats in library` count and the Members cell in SKILL.md's The Councils table (or, if you can't edit SKILL.md, say so in the confirmation), then confirm in one line.
6. **Seat the guest** in the next session or immediately with "summon {name}".

## 14. Follow-ups

| Follow-up | Procedure |
|---|---|
| **"{name}, go deeper"** | Only that member speaks, 150–300 words, in character. Use 2–3 of their mental models on the user's facts, answer the user's likely objection, and end with one test the user can run this week. If it would change the Verdict, add a Speaker line: "This would move the Verdict: … Say 'vote again'." |
| **"rematch: {new facts}"** | Update intake and keep the seats, unless the facts change the routing (say so). Re-run Openings only for members whose position moves. Hold a short Crossfire on the new facts, re-vote and show a Verdict diff: **Changed:** … / **Unchanged:** …, with the new vote board and confidence |
| **"cross-examine {A} vs {B}"** | 6–10 alternating exchanges, each attacking one specific claim with a number, test or precedent. The Speaker closes with a 2-line scorecard: which claim survived, and what that means for the Verdict |
| **"summon {name}"** | Seat them in the best-fitting convened council, or build a guest. They give an opening that reacts by name to the current Verdict. Offer "vote again" |
| **"dismiss {name}"** | Remove them and re-tally the vote board. If they were a Chair, the member whose lens best fits the decision takes the chair and re-issues the brief in one line. If the Ruling changes, show the diff |
| **"vote again"** | Every current seat re-votes with conviction, and anyone who moved says why in one line. Print the vote board. If the majority flips, the Speaker issues a revised Verdict with a diff |
| **"masks"** | Re-run the same session in masks mode (section 11), keeping the intake and seats |
| **"go deep"** | Re-run the same question in deep mode. Keep the intake and add councils and seats as deep mode requires. Ask no new questions unless a missing fact would flip the verdict |
| **"show card"** | Print the full compact card of this session's guest |
| **"save {Short}"** | Section 13, step 5 |
| **"unmask"** | Masks mode only: print mask → name |
| **"minutes"** | Section 15 |

The follow-up line after every session suggests 3–5 of these, using the names of seated members and the fact most likely to change the ruling.

## 15. Minutes file

- **Where:** `council-minutes/YYYY-MM-DD-{slug}.md`, relative to the current project directory. Create the folder if it's missing. If the file exists, append `-2`, `-3` and so on.
- **Slug:** lowercase, hyphenated, 3–6 words from the decision (for example `quit-job-ai-skills-marketplace`).
- **Content:** the front matter from output-format.md, then the session exactly as delivered (notice included), then every follow-up exchange under `## Follow-ups`, in order.
- **After writing,** tell the user the path in one line.
- **Without file access:** print the same content in a single fenced Markdown block with the suggested filename above it.
- **No session yet** in this conversation: say there is nothing to save and offer to convene one.

## 16. Length control

**Bands** (whole response, notice through follow-up line): quick 350–650 words · full 1,400–2,400 · deep 2,800–4,500. They are strict. An explicit length request from the user overrides them; nothing else does, including several decisions or a request to see what each person said.

**Pre-send length step.** Before sending, estimate the word count as `wc -w` would (table pipes and Markdown count). Check each capped piece on its own, even when its section fits: the Verdict and each of its slots, the High Council and each Chair line, each pre-mortem cause, each Chair's brief, the Red Team council, Read of the situation and the ⚡ Bottom line. Trim an over-cap piece first (move amounts from the Ruling into the plan; cut restated conditions from briefs). If the whole response is over, cut in this order until it fits:
1. **Repeated figures:** apply the repetition rule (output-format.md, section 1).
2. **Restated arguments:** a point made once is not made again in a brief, the High Council or Why this won; name it instead ("Buffett's owner-earnings point").
3. **Read of the situation:** down to its cap; move derived numbers to the one member who uses them.
4. **Crossfire padding:** cut lines to the low end, and keep at least the minimum real clashes (in full and deep, replace the rest with one italic Speaker line summarizing them).
5. **Still over:** drop every section 5 budget to its low end, then Final words to 12 words, the Vote table to its compact form (member · option · n/10), and each brief field to one short line.

**Never cut:** the notice, any Verdict slot (each stays, inside its own cap), any seated member's opening (shorten it, never drop it), or the pre-mortem causes.

**When running short** (below the band): the debate is too thin. Add the missing clash or sharpen the openings with the user's numbers. Don't pad the Verdict.
