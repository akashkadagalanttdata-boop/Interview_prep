# 26-Week Engineering Mastery Program

A tutored, spaced-repetition study system for five tracks: **AI/LLM fundamentals**, **coding
interview patterns**, **system design**, **ML system design**, and **GenAI system design**.

**26 weeks · 1.5 hr/day · 7 days/week · ~273 hours.**

Designed to be **AI-portable**: the repo is the program. Any AI tutor — or none — can pick it
up mid-stream with no context loss.

---

## Start a session

Open this folder in an AI coding tool and say:

```
continue
```

That's it. The tutor reads `progress.md`, `review-queue.md`, `weak-spots.md`, and `syllabus.md`,
then opens with the cold-recall block. If it asks *"what would you like to study?"*, something
is broken — see [Troubleshooting](#troubleshooting).

On a plain chat box with no file access, use [`BOOTSTRAP.md`](BOOTSTRAP.md) instead.

---

## How it works

**Two lanes, every day, 90 minutes:**

| Min | Block |
|-----|-------|
| 0–10 | Cold recall — due review items, notes closed |
| 10–40 | Lane A — one Python coding problem |
| 40–75 | Lane B — new concept material |
| 75–85 | You write the note / design / ELI5 **from recall** |
| 85–90 | Tutor updates state files and commits |

Lane A (coding) runs all 26 weeks in parallel — patterns decay without daily contact.
Lane B moves through the tracks: AI fundamentals (W1–6) → system design (W7–17) → ML
(W18–22) → GenAI system design (W23–25) → blind mixed mocks (W26).

**Day 7 of each week is consolidation** — no new material. That slack is deliberate; a plan
with none doesn't survive month two.

**Three rules do most of the work:**

1. **Notes are written from recall, never copied.** The recall *is* the learning.
2. **Nothing advances below L3** (derives it from fundamentals, defends it under attack).
3. **L4 requires an ELI5 that passes** — ≤120 words, one physical analogy, and the concept's
   own jargon is banned. You can't explain attention using "query," "key," or "value."

Reviews resurface at sessions **+1, +3, +7, +16, +35, +80** — indexed by session count, not
calendar date, so a skipped week doesn't silently expire the queue.

---

## Files

| File | What it is |
|---|---|
| [`TUTOR.md`](TUTOR.md) | **The contract.** Vendor-neutral teaching rules, protocol, rubrics. The one file that matters most. |
| [`BOOTSTRAP.md`](BOOTSTRAP.md) | Resume prompt for an AI with no file access |
| [`syllabus.md`](syllabus.md) | 26 weeks, day-level, both lanes |
| [`progress.md`](progress.md) | Current state (YAML block) + mastery table + session log |
| [`review-queue.md`](review-queue.md) | What's due, by session number |
| [`weak-spots.md`](weak-spots.md) | Open errors. The best review fuel in the repo. |
| [`eli5-glossary.md`](eli5-glossary.md) | Your growing plain-language textbook |
| `CLAUDE.md`, `AGENTS.md`, `GEMINI.md`, `.cursorrules` | Stubs pointing every AI tool at `TUTOR.md` |
| `ai/`, `design/`, `coding/` | Your notes, design writeups, and pattern write-ups |
| `builds/` | Three hands-on projects: mini-GPT, eval harness, LoRA fine-tune |
| `mocks/` | Mock interview transcripts + scorecards |
| `templates/` | Note, design, pattern, and scorecard templates |

---

## If you lose access to an AI

This is the scenario the repo is built for. Nothing here depends on a specific vendor.

**Switching to another agentic tool** (Codex, Cursor, Gemini CLI, whatever's next):
just open the folder and say `continue`. The stub files (`AGENTS.md`, `GEMINI.md`,
`.cursorrules`, `CLAUDE.md`) all point at `TUTOR.md`, so any tool that reads a convention file
finds the contract. If yours uses a filename not listed here, copy an existing stub to it.

**Dropping to a plain chat box with no file access:** follow [`BOOTSTRAP.md`](BOOTSTRAP.md).
Paste the prompt, attach four files, and remember to paste the updated state files back at the
end — that's the step people skip, and skipping it loses the session.

**No AI at all:** the program degrades rather than stops.
`eli5-glossary.md` is a textbook you wrote — cover the term, explain it aloud, check yourself.
`weak-spots.md` is your worklist. `coding/log.md` lists problems due for re-solving from
scratch. Keep writing recall notes. Resume tutored sessions whenever you can.

**Keep it pushed.** One commit per session, pushed to a private remote. The repo is the
backup, and `git log` is a five-month record of showing up.

---

## Troubleshooting

**Tutor asks "what do you want to study?"** — it didn't read the state files. Point it at
`TUTOR.md` §2. If it happens repeatedly on one tool, that tool's stub file isn't being picked
up; check the filename that tool actually looks for.

**Tutor is too agreeable, or grades ELI5 leniently** — the most common failure, and the one
that quietly wastes months. Point it at `TUTOR.md` §5 and §7. Spot-check three concepts marked
L4: if any ELI5 uses a banned word or needs a follow-up question to make sense, demote it and
tell the tutor to recalibrate.

**Sessions stop being logged** — check `git log --oneline`. One commit per session; a
`progress.md` diff that shows no mastery movement means the last five minutes got skipped.

---

## Content policy

Course modules from a paid subscription are read **in the browser**, never copied here. Every
note in this repo is written from recall, in the learner's own words. That's both the license
boundary and the reason the method works — and it's what makes the repo safe to hand to a
third-party AI tutor.

No model weights, checkpoints, or datasets get committed; see `.gitignore`.
