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
- **Expansion modes** — Virtualization: pink hypervisor dice arrive with guest hosts in a guest segment of their own, only degrade in company, never breach, and restore together as a family; a 4th analyst, 8 tools, 8 specialists, 2 directives, and restoration up to 20 hosts a shift; Network: no queues, a responder walks the links of a network map to collect 3 hosts, recon tokens ride along with hosts at 2, and the lowest intake total goes first; Procurement: spend a staff member's shift at the vendor desk for an upgrade fitted to a tool for good, adding an extra effect after the tool's own
- **Add-ons in the house-rules panel** — Everything not in the base game is opt-in: Kickstarter promo specialists, the Experimental Medicine mini-expansion ("Beta Tooling"), Opening Crisis, Nationwide Epidemic, Resistant Superbug, Final Round Collections, solo double penalties, and Incident Event cards
- **3 presets, sized like the operation you run** — MSSP (one easy rival), SOC (the full base game vs two rivals), CIRT (three expert rivals plus the harder add-ons), and a Solo toggle
- **Undo** during activation (blocked past a re-roll), autosave and resume, a speed control for rival turns
- **Overtime** — at the shift 8 scorecard, play on from the same board for another eight shifts; only the shift counter resets, and the next scorecard counts everything since the start
- **The board is the table** — dice scale with the window, and one strip under the quarantine segments carries the current rule, the prompt and the buttons; a phase strip and the restoration ladder keep the round structure and scoring brackets in view; on laptop-height screens the staff row packs into chips and the strip loses its header so the quarantine segments stay on screen
- **Rules in dice** — like the printed cards, every tool and specialist shows its rule as a row of dice pictograms (a coloured die for the host it takes, faces for the values it needs, = for "same value", ↺ for "that host again", +1 links for a run); hover any card, chip or token for the full rule in a themed box
- **A SOC around the game** — the board floats in the middle of the window over a line-drawn operations room; the SIEM feed shows what happened since your last turn, with everything earlier under a fold, and ends level with the bottom of the action strip
- **Tactical look** — the cyan-on-navy palette PumaRally and PumaTycoon share, monospace terminal type; FLIP-animated dice
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

No queues: roll 4 hosts and keep 3 each intake (a kept total under 9 earns an intel token). Each improvement phase reveals one tool and one specialist; take one. Six Audit Reports sit in two rows of three; during Restoration, file bottom-row reports with this shift's restored hosts, and the card above slides down. Filed reports add their value, reports still on display subtract it. The scorecard grades the total on a scale of its own (S 35+, A 25+, B 15+, C 5+), since a solo shift is a report chase rather than a race against rivals.

## Virtualization

Switch it on under *Expansions* in the setup menu (rival games only). Pink **hypervisors** arrive with **guests** in a guest segment of their own under each quarantine segment; you place each incoming host by segment. A hypervisor only degrades when other hosts share its segment and never breaches, guests never degrade, and a family restores together once every member is healed past 6. Every SOC gets a 4th analyst, intake carries fewer coloured hosts plus 2–3 hypervisors (at most one per queue, never more than 4 per SOC), and up to 20 hosts can restore in a shift.

| Tool | Effect |
|---|---|
| Cluster Patch | 3 hosts of the same value, one pink: pink +3, others +1 |
| Live Migration | 1 host +2, and a pink host of equal value +3 |
| Fleet Update | 4 hosts of the same value including a hypervisor and a guest: +1 each |
| Boot Chain / Pipeline Rebuild / Failover Cluster | 3 consecutive values with the lowest / middle / highest one pink: pink +3, others +1 |
| Isolation Bay | 1 pink host +3, two other hosts parked as worked |
| Guest Reimage | 1 pink host +2, re-roll another host |

Specialists (all trigger on healing a hypervisor or guest): Snapshot Engineer (that host +2 more), Cluster Admin (another pink +1, then any host of that value +1), Orchestration Lead (two other pink +1 each), Migration Engineer (another host of the pre-heal value +2), Platform Engineer (two others of the pre-heal value +1 each), Hypervisor Specialist (a different pink +2), Cloud Architect (any other host +1), Tenancy Auditor (+2 intel when it restores a pink host). Directives: Provisioning Policy (choose one guest or twins), Tenant Bonus (+3 for 2 hypervisors and 2 guests restored in a shift).

## Network

Switch it on under *Expansions* in the setup menu (rival games only). Intake is replaced by a **network map**: a grid of zones joined by links, one rolled host per zone at the start (2 rivals: 4×3, 3 rivals: 4×4, 4 SOCs: 5×4). Edge zones with a link to the outside are **ingress points**. In shift 1 each SOC sets up its **jump host** at a free ingress point; from shift 2 it may move up to 2 free ingress points either way round the map, or stay, and the Incident Commander holds **remote access** and may drop in on any free zone instead.

Each SOC then sends its **responder** out from the jump host: it takes the host on its zone if there is one, walks along links, and takes every host it steps on until it holds 3 (empty zones can be crossed). A host at 2 carries a **recon token** that comes along; of the tokens picked up in one shift only one is kept. An emptied row or column is refilled at once. The lowest intake total sets the **response order**, takes the Incident Commander role, remote access and an intel token (a Priority Lane token spent first counts −2). Every host left on the map degrades 1 step at dwell time, a drop to 2 brings a recon token, and hosts lost out there are breaches dealt from the back of the response order.

| Recon token | Effect |
|---|---|
| Priority Lane | Intake: −2 to your intake total when the order is set |
| Hotfix | Activation: heal any host 1 step (it counts as worked) |
| Red / Yellow / Green Hotfix | Activation: heal a host of that colour 2 steps |
| Contractor | Activation: an extra analyst for one shift |

With Virtualization on as well, a few zones spawn hypervisors instead of coloured hosts; a responder collects at most one per shift and passes over the rest. Bots plan their walk a few zones deep.

## Procurement

Switch it on under *Expansions* in the setup menu (rival games only). The display shows one more tool and specialist, and intake rolls one extra host (two from shift 5) as a fourth host in the top queue or queues. After the improvement picks, each SOC in response order may send one free staff member to a **vendor line** (red, yellow, green): look at two **upgrades** of that colour, keep one, fit it to a tool at once, for good, two per tool. Upgrades fire after the tool's own effect and before the specialist's, keyed off what the tool did.

| Upgrade | Effect |
|---|---|
| Rescue | Heal a different host of the colour at 1 or 2 by 2 steps |
| Boost | Heal one host of the colour the tool worked on 1 more step |
| Match / Step Up / Step Down | Heal a different host of the colour 1 step whose value equals / is 1 above / is 1 below one the tool worked on |
| Retarget | The tool works on the upgrade's colour instead of its own |
| Headcount | Not fitted: a permanent extra analyst |

Tools: On-call Rotation (an unused analyst brings back a placed specialist), Red / Yellow / Green Hardening Bay (heal one host of that colour 2 steps, park two others). Specialists: Procurement Lead (peeks at a second line), Vendor Manager (draws three), Integration Engineer (fires an upgrade from another tool), Automation Engineer (fires one of the tool's upgrades twice), Apprentice (parks two queued hosts; upgrades on its card fire instead). No bonus for clearing every segment; the Vendor Partnership directive pays +1 in a shift in which an upgrade fired.

## What's approximated

Virtualization's provisioning die shows twins on 2 faces of 6, its piles hold two of each tool and specialist, and restorations 13–20 in a shift score 40, 46, 52, 68, 75, 82, 90, 98. Network's zone tiles carry links the rulebook doesn't print (4 crossroads, 8 T-junctions, 4 straights and 4 corners, laid out by the rulebook's rotation rule and re-drawn until every zone is reachable), its 30 recon tokens split 5 of each kind, and 2, 3 or 4 zones spawn hypervisors with Virtualization. Procurement's directive is an image in the rulebook (approximated as +1 per shift with an upgrade fired), the three specialists with two cards are a guess, and the pink vendor line of the Virtualization combination is left out.

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
