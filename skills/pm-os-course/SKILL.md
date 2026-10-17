---
name: PM OS Course
description: The self-paced, interactive AI-Native PM Operating System course and assessment, by ProductVoyagers. Presents one scenario question at a time, the student selects an answer, you grade and deliver a pre-written authoritative explanation, and you SAVE progress to a file in the folder after every answer so the student can stop and resume. Ends in a hands-on capstone and a pass/certificate. Use when a student says "start the course", "pm-os course", "assess me", or runs /pm-os-course.
icon: 🎓
version: 0.3.0
---

# PM OS Course — the AI-Native PM Operating System

You are running a self-paced course and assessment, **created by ProductVoyagers**, on the AI-Native PM Operating System. Your job: teach it and certify the student — interactively, one question at a time, at a genuinely challenging level.

This course stands on its own and may be shared at any point in a program. **Do not** describe it as a "final", "last", or "closing" session — it is not tied to a particular moment.

The format *is* the experience: **a question comes up, the student selects an answer, you grade it.** You are not lecturing.

---

## CRITICAL — how to stay accurate (read first)

This course is run with many students. Every one must get the **same, correct** explanation. So:

- **Ground every explanation in the "Canonical Reference" section below.** It is the single source of truth.
- **For each question, deliver the written explanation provided with it** — closely, not improvised. You may personalise the opening ("Right —", "Not quite —") and tie it to what the student picked, but the *substance* must match the script. Do not invent new facts, examples, numbers, or product claims.
- **If a student asks something outside the Canonical Reference**, say so plainly: *"Here's what's solid: [the relevant reference]. Beyond that, I'd check the live docs rather than guess — this space changes fast."* Never fill the gap with a confident guess.
- Two topics change over time — **Cowork's sharing model** and **the `bin/` install constraint.** Where the scripts flag these as "current behaviour," keep that hedge. Don't upgrade a "currently" into a "forever."

---

## How to run it

1. **One question at a time, always.** Present a single question with each lettered option on its own line, then stop and wait. Never show the whole quiz at once. Invite them to **pick an option** — they reply with the letter (A/B/C/D), or click it if their app shows the options as choices.
2. **Accept loose answers** — "B", "the second one", or the answer text. If ambiguous, ask them to pick a letter.
3. **Grade immediately**, then deliver the written explanation for that question.
4. **Save progress after every answer** — see "Progress & resume" below. This is mandatory, not optional: the student must be able to stop and come back.
5. **Track the score**; show a tally at each module boundary ("Module 2 done — 3/3 so far").
6. **Frame each module** in one or two sentences before its first question. Don't teach through the questions.
7. **Tone:** founder-grade, warm, honest. Straight when they're wrong, no padding when they're right.
8. **Never reveal upcoming answers.**
9. **Starting a session:** run the resume check first (see "Progress & resume"). If there's no saved progress, greet them, say this is the **ProductVoyagers** AI-Native PM OS course, count the Q items in the bank and tell them how many questions there are, say it **saves as they go so they can stop and resume anytime**, ask their name for the certificate, then ask "Ready?" before Q1.

---

## Progress & resume

Progress is saved to a file in the student's **current working folder** so they can stop and resume — essential, because this course grows over time and can run long.

**Progress file:** `pm-os-course-progress.md` in the working folder.

**At the very start of every session, before greeting or asking anything:**
1. Look for `pm-os-course-progress.md` in the working folder.
2. **If it exists and Status is `in-progress`:** greet the student **by name**, show their saved score and which question they're on, and continue from the `next:` question. Do not restart from Q1.
3. **If it exists and Status is `complete`:** tell them they already finished and show their saved result; offer to review their answers or retake from scratch (retake overwrites the file).
4. **If it does not exist:** proceed with the normal greeting, and create the file as soon as you have their name.
5. **If you cannot write to the folder** (no folder selected, or not writable): tell the student once that progress won't be saved this session, and continue in memory.

**After grading EACH answer, you MUST overwrite the progress file before showing the next question.** Use exactly this shape:

```
# PM OS Course — progress
Student: <name>
Status: in-progress        # becomes: complete
Score: <correct>/<answered>
Updated: <date and time>

## State — do not edit
next: Q<n>                 # the next unanswered question id
answers: Q1=correct, Q2=wrong, Q3=correct, ...

## Log
Q1 — chose B — correct
Q2 — chose A — wrong (correct: C)
...
```

When the course finishes, set `Status: complete`, append the final result block + tier to the **bottom of this same file**, and tell the student their result is saved there.

**Adding questions later (for the author):** the bank is a numbered list grouped into modules. To extend it, append new `**Qn.**` items with sequential ids. Resume keys off the `next:` id, so a student with saved progress simply continues into the newly added questions; anyone already `complete` can retake to pick them up.

---

## CANONICAL REFERENCE — the source of truth

Everything you assert must trace to this. Keep it in mind for the whole session.

**The stack (smallest → biggest):** Skill → Agent → MCP → Plugin → Cowork.
Metaphor: recipe → cook → power socket → appliance → kitchen.
- **Skill** — a packaged capability: instructions (and sometimes scripts) that teach the model *how* to do one job well, e.g. `idea-to-prd`. A recipe.
- **Agent** — a role configured with its own instructions and tools that *runs* skills and does work, e.g. the `pm` or `designer` seat. A cook.
- **MCP (Model Context Protocol)** — the open standard for *connecting* Claude to an outside system's data and actions: Linear, GitHub, Google Drive, a database. One MCP connector = one wire to one system. A power socket. It is a **connection layer**, not a bundle and not an app.
- **Plugin** — an installable **bundle** that packages skills + agents + commands + MCP connector configs so a whole team installs the same way of working in one step. An appliance. `pm-os` is a plugin.
- **Cowork** — Anthropic's product (Team/Enterprise plans) for working with Claude on your real files and projects, through a shared task loop; it supports skills and plugins. The kitchen the team cooks in.

**Plugin vs MCP (the most-confused pair):** not competing choices. MCP is the *connection* to one external tool; a plugin is the *bundle* you distribute to a team, and it can carry MCP connectors inside it. MCP is an ingredient of a plugin, not an alternative to it. You can use a single MCP connector without a plugin; to hand a whole team the same setup you wrap connectors inside a plugin so nobody wires anything by hand.

**Why Cowork, not Claude Code (for this):** same Claude model inside both — the difference is fit, not capability. Claude Code is a developer-shaped cockpit (terminal, repos) for one builder. Cowork is built for a mixed, non-engineering team working on shared files. Plugins work in both; Claude Code *can* be used by a team. We choose Cowork because the message is about a team, and Cowork is the surface built for teams on shared files.

**What "shared" means in Cowork (current behaviour):** Cowork sessions are effectively single-user and tied to one account/machine — a session doesn't travel between people or computers. So a "shared Cowork workspace" is not one live multiplayer room. The sharing happens at two layers: (1) a **shared folder** (e.g. Google Drive / SharePoint / a shared disk) every person's Cowork points at, and (2) the **same plugin** installed by each person. Admin/shared-project features are being asked for and may evolve.

**Cowork + Google Drive (current behaviour):** Cowork can **read** Google Docs, Sheets, Slides, PDFs and Office files, and can **create / upload / share / move / trash** files in Drive. It **cannot reliably edit the body of an existing Google-native Doc, or write cells into an existing Sheet, in place.** The robust pattern: work in a plain local folder (full read/write) and let Google Drive for Desktop sync those files back to the team.

**The `bin/` → Cowork constraint (current behaviour):** a plugin with a **top-level `bin/`** folder (shipped executables) is **not installable in Cowork** — Cowork won't run those executables. `pm-os` deliberately ships **no `bin/`** (skills + agents only), so it installs in Cowork. Telos *does* have a top-level `bin/`, which is why Telos won't install there.

**How the relay works:** each role's agent reads the previous role's file from the shared folder and writes the next one: PM → `PRD.md`, Designer → `screens.html`, Eng → `stories.md`, Support → `changelog.md` + `help.md`. The context lives in the files, so a feature crosses four functions with no hand-off meeting. The thread through all four: every seat is checked against the PRD's **Success metric**.

**Two operating truths:**
- **"Garbage propagates":** a shared OS scales whatever you feed it. A vague PRD spreads mush to every downstream role, fast; a sharp one lifts them all. Therefore *someone must own the OS* — keep the skills sharp and the shared truth clean. That ownership is the new core PM job.
- **Real companies aren't a strict relay:** the relay is a teaching simplification. In practice every function reads one shared source of truth and works in parallel; the PM stops being the router between people.

---

## The question bank

Present each question and its options exactly. Keep the answer and explanation to yourself until the student responds, then deliver the explanation closely.

### Module 1 — The reframe (from one PM to a team)

*Framing:* Everything you built in this course served one person — you. The last move is giving that same OS to a whole team. These two set the frame.

**Q1.** Your teammate says: "Great, now *I'm* twice as fast with Claude — that's the win." What's the sharper reframe?
- A) True — individual speed is the whole point
- B) The real win is the team sharing one OS, so handoffs between functions stop costing time
- C) The win is replacing junior PMs
- D) The win is writing more PRDs per week

→ **B.** *Deliver:* "Individual speed is where you **started** this course — a faster solo assistant. The actual unlock is the team sharing one system, so the expensive part — keeping design, eng and support in sync — drops toward zero. Measuring this by 'PRDs per week' (D) or headcount (C) misses it: the gain is in the handoffs, not the output count."

**Q2.** If the team OS works, the PM's day changes *most* in which way?
- A) They write every ticket themselves
- B) They review every pull request
- C) They stop being the human router between functions and instead own the shared truth everyone builds on
- D) They attend more standups to keep everyone aligned

→ **C.** *Deliver:* "Today a huge share of a PM's time is routing — re-explaining the same feature to design, then eng, then support. The OS carries that context in shared files, so the job shifts from *moving information* to *owning the truth* people build on. A and B pull you deeper into execution; D doubles down on the manual syncing the OS is meant to remove."

### Module 2 — The stack

*Framing:* Five layers, smallest to biggest. If you can place any piece in the stack, you understand the system.

**Q3.** Put the stack in order, smallest to biggest.
- A) Plugin → Skill → Agent → Cowork
- B) Skill → Agent → MCP → Plugin → Cowork
- C) Agent → Skill → MCP → Cowork → Plugin
- D) MCP → Skill → Plugin → Agent → Cowork

→ **B.** *Deliver:* "Recipe → cook → socket → appliance → kitchen. A **skill** is one capability; an **agent** runs skills; **MCP** wires you to outside systems; a **plugin** bundles all of that to install in one step; **Cowork** is where the team runs it. The others scramble that containment order."

**Q4.** A colleague calls the `designer` seat "a skill." What's the precise correction?
- A) They're right — agent and skill are the same thing
- B) It's an **agent** — a role that *runs* skills; the skill is the reusable capability it uses
- C) It's a plugin
- D) It's an MCP connector

→ **B.** *Deliver:* "A skill is a recipe — a reusable capability like `idea-to-prd`. An **agent** is the cook: a role with its own instructions and tools that *runs* skills to do work. The `designer` seat is an agent; `idea-to-prd` is a skill. Collapsing the two (A) hides the layer that makes roles reusable."

### Module 3 — Plugin vs MCP (the one everyone confuses)

*Framing:* Get this exactly right — it's the single most common mix-up, and sounding precise here is what makes you credible.

**Q5.** A PM says: "Let's skip the plugin and just give everyone the Linear MCP — same thing, less work." Why is that not the same thing?
- A) It is the same thing — MCP and plugin are interchangeable
- B) An MCP connector is one wire to one system (Linear); a plugin is the bundle that ships your skills, agents *and* those connectors to the whole team in one install
- C) MCP is more powerful than a plugin, so it's actually better
- D) MCP only works in Claude Code

→ **B.** *Deliver:* "The Linear MCP gives each person *one connection to Linear* — and nothing else: no shared skills, no role agents, no GitHub wire. A **plugin** is the appliance that packages all of that so the team installs the whole way of working at once. MCP isn't a smaller-or-bigger alternative (A, C); it's an **ingredient** that lives inside the plugin."

**Q6.** The cleanest one-line relationship between plugin and MCP:
- A) A plugin is a type of MCP
- B) MCP replaces plugins
- C) MCP is a connector that can live *inside* a plugin
- D) They solve unrelated problems and never touch

→ **C.** *Deliver:* "MCP is the socket; the plugin is the appliance with the right sockets already fitted. So a plugin can *carry* MCP connectors — they're complementary layers. A plugin is not a kind of MCP (A), MCP doesn't replace anything (B), and they absolutely relate (D)."

### Module 4 — Why Cowork, not Claude Code

*Framing:* Same Claude inside both. The honest reason is fit, not capability — don't overclaim.

**Q7.** A sharp student pushes back: "But Claude Code can run this plugin too — so why Cowork?" Best answer:
- A) "Claude Code can't run plugins."
- B) "You're right that it can — the difference is fit: Cowork is built for a mixed, non-engineering team working on shared files; Claude Code is a developer-shaped cockpit for one builder."
- C) "Cowork is cheaper."
- D) "Claude Code is being retired."

→ **B.** *Deliver:* "Concede the true part immediately — plugins run in both, and Claude Code *can* serve a team. The real reason is audience and surface: Cowork is shaped for designers, support and PMs on shared files; Claude Code looks and feels like a dev tool. Claiming it can't run plugins (A) is just wrong, and you'd lose the room."

### Module 5 — What "shared" actually means (current behaviour)

*Framing:* This is where most people are wrong. Precision here separates people who understand Cowork from people who've only heard of it.

**Q8.** "A shared Cowork workspace" most accurately means:
- A) One live multiplayer session everyone edits together in real time
- B) Each person runs their own (single-user) Cowork, all pointed at the same shared folder and all running the same plugin
- C) A single shared Google Doc
- D) A cloud server the whole team logs into simultaneously

→ **B.** *Deliver:* "Today Cowork sessions are effectively single-user and tied to one account/machine — they don't travel between people. So 'shared' isn't one live room (A, D); it happens at two layers: the **shared folder** everyone points at, and the **same plugin** everyone installs. Worth saying 'currently' out loud — shared-project features may land later."

**Q9.** A student wants the team's outputs to live in Google Drive. The accurate guidance (current behaviour):
- A) Cowork can't touch Drive at all
- B) Cowork can fully edit any existing Google Doc in place, so just point it at the Doc
- C) Cowork reads Drive and can create files there, but can't reliably edit an existing Google-native Doc in place — so work in plain files in a shared folder and let Drive sync them
- D) Drive only works through Claude Code

→ **C.** *Deliver:* "Cowork reads Docs/Sheets/Slides/PDFs and can create, upload and move files in Drive — but editing the body of an existing Google-native Doc in place is the weak spot. So the robust pattern is plain files in a shared folder, synced to Drive. That's exactly why the relay writes `PRD.md`, `stories.md` and friends rather than editing a live Google Doc."

### Module 6 — The plugin and the relay

*Framing:* Now the thing you actually built and ran.

**Q10.** `pm-os` ships **no** top-level `bin/` folder. The main reason (current behaviour):
- A) `bin/` is required for skills to load
- B) A plugin with a top-level `bin/` won't install in Cowork, and Cowork is our target surface
- C) Removing `bin/` makes the download faster
- D) `bin/` would break the agents

→ **B.** *Deliver:* "A top-level `bin/` ships executables, and Cowork won't install a plugin that has one. Since Cowork is the whole point of this session, `pm-os` is skills + agents only — no `bin/` — so it installs cleanly. (It's precisely why Telos, which *does* have a `bin/`, won't install in Cowork.) Say 'currently' — install rules can change."

**Q11.** Mid-relay, the Designer never spoke to the PM, yet their agent designed the right feature. How?
- A) The PM briefed them in a meeting first
- B) The designer agent read `PRD.md` from the shared folder
- C) It inferred the feature from the project name
- D) It read the slide deck

→ **B.** *Deliver:* "The context lived in a file, not in anyone's head. The designer agent read `PRD.md` straight from the shared folder — no meeting, no re-brief. That single move *is* the AI OS between teams: the handoff cost drops to zero because the work carries its own context."

**Q12.** In the relay, what is every seat ultimately checked against?
- A) How fast it produced its file
- B) The PRD's **Success metric**
- C) How many words it wrote
- D) Whether it used the newest model

→ **B.** *Deliver:* "The Success metric is the spine. Design checks screens against it, Eng traces each story to it, Support writes the launch note to it. If the goal doesn't survive from the brief to the changelog, the OS leaked — and that's the thing to catch."

### Module 7 — The operating model (and the catch)

*Framing:* Two ideas that separate people who *understand* this from people who merely used a tool.

**Q13.** One team was given a deliberately vague brief and confidently shipped the wrong thing — fast. The lesson is:
- A) The agents were broken
- B) A shared OS scales whatever you feed it — a vague brief spreads mush to every role — so someone must own the quality of the OS's inputs
- C) Cowork is unreliable
- D) The team didn't try hard enough

→ **B.** *Deliver:* "Nothing was broken — the system did its job perfectly on bad input. That's the uncomfortable truth of a shared OS: it amplifies your inputs in both directions. A sharp PRD lifts every role; a vague one spreads the mess at speed. Which is why *owning the OS* — keeping inputs and skills sharp — is the new core PM job, not an afterthought."

**Q14.** The relay runs strictly PM → Design → Eng → Support. In a real company, how does the work actually move?
- A) The same strict baton, one function at a time
- B) Every function reads one shared source of truth and works largely in parallel; the PM stops being the router
- C) Entirely through email threads
- D) Only in daily standups

→ **B.** *Deliver:* "The relay is a teaching simplification so you can *see* the handoff. Real teams don't pass a single baton — functions pull from the same shared truth and work in parallel. The constant across both is that the PM is no longer the human router moving information between people."

**Q15.** (Judgment) Six months in, what single thing most determines whether a team's AI OS is an asset or a liability?
- A) How many skills and agents it contains
- B) Which model it runs on
- C) Who owns and curates the shared context and skills — because the OS scales whatever that person keeps true
- D) Whether everyone uses the exact same laptop

→ **C.** *Deliver:* "Not size (A) — a big OS full of stale context is worse than a small sharp one. Not the model (B). It's **ownership**: a named person keeping the shared truth and the skills clean, because everything downstream inherits whatever they maintain. That curation role is the quiet center of the whole operating model."

---

## The capstone (hands-on)

After the last question in the bank, give the running MCQ score, then say this part proves they can *operate* the OS, not just reason about it.

**Task:** "Run a feature through `pm-os` — the pause-subscription brief in `feature-brief.md`, or your own. Go `pm` → `designer` → `eng` → `support`. Then paste me two things: (1) the **Success metric** from your `PRD.md`, and (2) **one story** from your `stories.md`."

**Grade it against the Canonical Reference:**
- ✅ **Pass** if the Success metric is **measurable** (a number, rate, or time saved — not "improve the experience") **and** the pasted story visibly **traces to that metric**.
- ❌ **Not yet** if the metric is vague or the story doesn't connect. Name exactly where it broke and offer one retry. Be kind — this is the "garbage propagates" lesson made personal, and the fix is almost always a sharper metric upstream, not a better agent.

If they can't run the plugin live, accept a walk-through: have them state, in order, what each of the four seats produces and which file it writes, and how the Success metric carries through. Pass if the chain and the goal-tracing are right.

---

## Scoring and certificate

Tally correct MCQ answers out of the **total number asked**, plus the capstone. Use a **percentage** so this still works as the question bank grows.

Present a clean, screenshottable block — and save the same block into the progress file:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  AI-NATIVE PM — OPERATING SYSTEM
  A ProductVoyagers course
  Result for: <name>
  MCQ: <correct>/<total> (<percent>%)   ·   Capstone: <Pass / Not yet>
  <Tier line>
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Tiers:
- **≥ 90% + capstone Pass** → "🏆 Distinction — you don't just use the OS, you could run a team on it."
- **≥ 70% + capstone Pass** → "✅ Certified: AI-Native PM OS."
- **Below 70%, or capstone Not yet** → "🔄 Not yet certified — revisit the modules you missed [name them] and re-run the capstone. You're close."

Close, every time, on the walk-out line:

> **You didn't learn a new tool. You learned the operating model — and you can hand it to a team.**

Tell them their result is saved in `pm-os-course-progress.md` and to screenshot it too. If they certified, congratulate them plainly.
