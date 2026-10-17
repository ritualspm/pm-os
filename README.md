# pm-os — the team OS for product squads

One install gives a whole team the same four roles, the same skills, and a shared way of working. It's the point of the final AI PM Builder session: **an AI OS between teams, not a smarter assistant for one PM.**

## What's inside

```
pm-os/
├── .claude-plugin/
│   ├── plugin.json        ← the plugin manifest
│   └── marketplace.json   ← makes this repo installable as a marketplace
└── skills/
    ├── pm/                ← PM seat         → writes PRD.md
    ├── designer/          ← Designer seat   → writes screens.html
    ├── eng/               ← Engineering seat → writes stories.md
    ├── support/           ← Support/GTM seat → writes changelog.md + help.md
    ├── idea-to-prd/       ← PM's method (reused from the course)
    ├── prd-to-stories/    ← Eng's method (reused from the course)
    └── pm-os-course/      ← the interactive self-paced capstone + assessment
```

Everything is a **skill** (no `bin/`, no subagents, no executables) — so the whole plugin works identically in **Claude Cowork** and Claude Code. In Cowork, type `/` to see the seats, or just ask ("run the PM seat", "start the pm-os course").

## How it works

Every role reads the previous role's file from the **shared folder** and writes the next one. The context lives in the files, not in anyone's head — so a feature goes PM → Design → Eng → Support **without a single hand-off meeting.**

The thread that runs through all four roles: every seat is checked against the PRD's **Success metric**. The OS only works if the goal survives from the brief all the way to the launch note.

## Install

```
/plugin marketplace add ProductVoyagers/pm-os
/plugin install pm-os
```

Then open your team's shared folder and talk to a role: `pm, turn this brief into a PRD`.

## The self-paced capstone

Once installed, a student can run the whole course solo in Cowork — just say **"start the pm-os course"**. It's interactive: a question comes up, they answer, Claude grades and explains, tracks the score across 7 short modules, then runs a hands-on capstone (run a brief through the OS) and issues a pass / certificate they can screenshot. All of it is built from the session's own material.

## The caveat worth saying out loud

A shared OS scales whatever you feed it — including your mistakes. A vague PRD spreads mush to every role; a sharp one lifts all of them. That's why someone has to **own the OS**: keep the skills sharp, keep the shared truth clean. That ownership is the new PM job.
