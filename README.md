# PumaTriage

**An incident-response dice game** — Run a Security Operations Center, work compromised hosts back to health, and restore them to production before dwell time finishes them off.

Inspired by [Dice Hospital](https://www.alleycatgames.com/dice-hospital) by Stanislav Kordonskiy and Mike Nudd (Alley Cat Games), re-themed around a SOC. Single-player against AI rivals, or the rulebook's solo score-chase.

## Play

[greykit.com/games/pumatriage](https://greykit.com/games/pumatriage/)

No install required. Single HTML file, runs in any modern browser, saves your shift in `localStorage`.

## How It Works

The rules are a one-for-one port of the Dice Hospital base game, re-themed: Hospital → SOC, Patient → Compromised host, Discharge → Restore, Fatality → Breach, Ward → Quarantine segment, Nurse → Analyst, Department → Tool, Ambulance → Escalation queue, Blood bag → Intel token, Hospital Administrator → CISO Directive, Medical Report → Audit Report, Round → Shift.

Compromised hosts are dice. The face is the host's **integrity**: 1 is about to be lost, 6 is nearly clean. Each shift you staff your tools with analysts to raise integrity. A host healed past 6 is **restored** and scores reputation; a host that drops below 1 is a **breach** and costs reputation at the end. Dice colours are just colours, exactly as in the original: some tools and specialists only work on red, yellow or green hosts.

Each of the eight shifts runs six phases: **Intake** (three hosts are rolled per escalation queue and each SOC takes one queue), **Improvement** (take one tool or one specialist from the display), **Activation** (place staff on tools, one at a time), **Dwell time** (every host still queued degrades), **Restoration** (score this shift's restored hosts together: 1st = 1, 2nd–6th = 2 each, 7th–8th = 3, 9th–10th = 4, 11th–12th = 5, +5 for clearing every segment) and **Shift change**. Final score: −2 per breach, +1 per unspent intel token.

![Setup screen — presets and house rules](screenshots/setup.png)

![Mid-game — an analyst about to work a red host on the Sandbox](screenshots/midgame.png)

![Solo mode — Audit Reports on the right, rolled hosts to keep](screenshots/solo.png)

![Game over — final ranking](screenshots/gameover.png)

## Features

- **Faithful base-game rules** — 12 quarantine slots with queued/worked positions, the six starting tools, 12 improvement tools and 12 specialists (two of each), 8 CISO Directives, escalation-queue drafting with the Incident Commander restriction, intel tokens, the "must resolve in full" rule, specialist follow-ups that fire once
- **Two modes** — Vs 1–3 AI SOCs (2–4 player rules, including the 2-player extra reveal) or the rulebook's solo score-chase with Audit Reports (draw 4 keep 3, one-of-each reveal, bottom-row filing)
- **Add-ons in the house-rules panel** — Everything not in the base game is opt-in: Kickstarter promo specialists, the Experimental Medicine mini-expansion ("Beta Tooling"), Opening Crisis, Nationwide Epidemic, Resistant Superbug, Final Round Collections, solo double penalties, and Incident Event cards
- **4 presets** — Beginner, Standard (the full base game vs two rivals), Solo, Hard
- **Undo** during activation (blocked past a re-roll), autosave and resume, a speed control for rival turns
- **The board is the table** — dice scale with the window, and one strip under the quarantine segments carries the current rule, the prompt and the buttons; a phase strip and the restoration ladder keep the round structure and scoring brackets in view
- **Retro CRT aesthetic** — Scanlines, vignette, phosphor glow, monospace terminal look; FLIP-animated dice
- **Sound effects** — Web Audio API procedurally generated retro sounds (mutable)
- **Tutorial** — 7-step introduction on first play
- **Accessible** — Keyboard shortcuts, every host/tool/analyst reachable by Tab, screen reader announcements, prefers-reduced-motion support, stacked layout on phones
- **Headless harness** — `__PT.runSim(50)` in the console plays bot-vs-bot games for crash and balance testing

## Tools

| Tool (Dice Hospital original) | Effect |
|---|---|
| Sandbox (Critical Care Unit) · starting | Heal one red host 1 step |
| Forensics Lab (Oncology) · starting | Heal one yellow host 1 step |
| Patch Console (Pharmacy) · starting | Heal one green host 1 step |
| War Room (Intensive Care) · starting | Heal one host at 1–2 one step |
| SIEM Console (Imaging) · starting | Heal one host at 3–4 one step |
| Help Desk (Clinic) · starting | Heal one host at 5–6 one step |
| Reimage Station (Operating Theatre) | Heal one red host 3 steps |
| Kill-Chain Lab (Cardiology) | Heal exactly 3 red hosts of consecutive values 1 step each |
| Decryptor (Anaesthesia) | Heal exactly 3 red hosts of the same value 1 step each |
| Backup Restore (Crash Centre) | Heal one host at 1–2 four steps |
| Config Baseline (ENT) | Heal one green host 3 steps |
| Scanner Sweep (Immunology) | Heal exactly 3 green hosts of consecutive values 1 step each |
| Patch Tuesday (Allergy Centre) | Heal exactly 3 green hosts of the same value 1 step each |
| MFA Rollout (Orthopaedics) | Heal one yellow host 3 steps |
| Credential Rotation (Urology) | Heal exactly 3 yellow hosts of consecutive values 1 step each |
| Log Review (Renal Medicine) | Heal exactly 3 yellow hosts of the same value 1 step each |
| EDR Sweep (Radiology) | Heal exactly 3 hosts of any colour at 1–3 one step each |
| Triage Desk (Triage Centre) | Heal exactly 2 hosts of any colour at 1–3 two steps each |

## Specialists

| Specialist (original) | Colour | Follow-up |
|---|---|---|
| Incident Responder (Surgeon) | red | Heals a red host → one of those red hosts +1 |
| Reverse Engineer (Anaesthetist) | red | Heals a red host → a different red host +1 |
| Threat Hunter (Cardiologist) | red | Heals a red host → a different host with the same pre-heal value +1 |
| Patch Engineer / Vuln Researcher / Config Auditor (Pharmacist / Virologist / Microbiologist) | green | Green analogues |
| IAM Engineer / Forensic Examiner / Network Engineer (Haematologist / Urologist / Radiologist) | yellow | Yellow analogues |
| Triage Lead (Triage Nurse) | white | Heals a host → two different hosts at 1–3 +1 each |
| First Responder (Paramedic) | blue | Heals a host → a different host at 1–3 +2 |
| Help Desk Lead (General Practitioner) | blue | Heals a host → a different host at 4–6 +1 |

Promo (add-on): Consultant, Intake Coordinator (Admissions Nurse). Beta Tooling (add-on): Beta Agent, Retagging Desk, Rollback Snapshot, Tabletop Exercise; Postmortem Lead, Chaos Engineer, Compliance Officer, Intern, Intel Analyst, Intel Broker.

## CISO Directives

Red / Yellow / Green Priority (+1 for restoring two of that colour in a shift), Defense in Depth (+1 for one of each colour), Red / Yellow / Green Containment (one queued host of that colour ignores dwell time), Executive Visibility (+1 for restoring the most in a shift).

## Solo mode

No queues: roll 4 hosts and keep 3 each intake (a kept total under 9 earns an intel token). Each improvement phase reveals one tool and one specialist; take one. Six Audit Reports sit in two rows of three; during Restoration, file bottom-row reports with this shift's restored hosts, and the card above slides down. Filed reports add their value, reports still on display subtract it.

## What's approximated

The rulebook doesn't print the 15 Event cards or the 15 Medical Report cards, and its component list says each starting board "depicts 9 hospital departments" while only six starting types exist; the starting SOC uses one of each (`START_DEPTS` at the top of `index.html`) on the reading that the count includes the station, discharge and mortuary areas. Audit Reports and Incident Events are PumaTriage originals in the same spirit. Final Round Collections slots are generated randomly. Adjust the tables at the top of `index.html` if your copy differs.

## Keyboard Shortcuts

| Key | Action |
|---|---|
| 1–9 | Select an analyst or specialist |
| Double-click a host | Confirm the current selection (a slow second click deselects it) |
| Enter | Confirm the highlighted action |
| Escape | Cancel selection / close dialogs |
| U | Undo the last placement |
| E | End activation |
| B | Spend an intel token to heal |
| H or ? | How to play |
| M | Toggle sound |
| S | Rival and phase speed: normal, fast, instant |

## Tech

- Single HTML file (~3100 lines), vanilla JS/CSS
- DOM/CSS-grid board, CSS-pip dice, FLIP animation
- Web Audio API for procedurally generated sound effects
- No frameworks, no dependencies, no build step, no network at play time
- localStorage for the autosave and the tutorial flag (`pumatriage_save_v1`, `pumatriage_tutorial_v1`)

## Other Puma Games

- [PumaPanic](https://greykit.com/games/pumapanic/) — Cyber tower-defense card game
- [PumaSOC](https://greykit.com/games/pumasoc/) — SOC management simulator
- [PumaSecure](https://greykit.com/games/pumasecure/) — Infosec roguelike network defense

## Credits

Game design and code by [shandower](https://gitlab.com/shandower) with AI assistance from Claude.

Inspired by Dice Hospital by Stanislav Kordonskiy and Mike Nudd / Alley Cat Games.
