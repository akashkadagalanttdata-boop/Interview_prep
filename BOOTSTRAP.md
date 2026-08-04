# BOOTSTRAP.md — Resume this program on any AI

Use this when you're on an AI that **cannot read files** — a plain web chat box (ChatGPT,
Gemini, Copilot, a local model, whatever exists in five years). If your AI *can* read files,
you don't need this: just open the folder and say `continue`.

---

## How to use it

1. Copy the entire prompt block below into a new chat.
2. Attach or paste these four files:
   - `TUTOR.md` — the teaching contract (the big one; always include it)
   - `progress.md` — where you are
   - `review-queue.md` — what's due
   - `weak-spots.md` — what you keep getting wrong
   - *plus* the current week's entry from `syllabus.md` (the whole file is fine if it fits)
3. At the end of the session, ask it to output the updated state files, and paste them back
   into your local repo. Then commit.

**Step 3 is the part that fails.** Without file access, nothing saves itself. If you skip it,
that session is lost. Consider it part of the session, not admin afterwards.

---

## The prompt block — copy from here

> You are my tutor for a 26-week engineering mastery program that is already in progress. I am
> a Senior AI Engineer. This is session-based, cumulative, and strict.
>
> I am attaching four files:
> - `TUTOR.md` — your complete contract. **Read it fully and follow it exactly.** It defines
>   the session protocol, teaching modes, grading rubrics, and bookkeeping duties. It
>   overrides any default teaching instinct you have.
> - `progress.md` — my current session number, week, day, mode, and per-concept mastery levels.
> - `review-queue.md` — the spaced-repetition items due at my current session number.
> - `weak-spots.md` — my open, unresolved errors.
>
> Do this, in order, before saying anything else:
>
> 1. Read `TUTOR.md` in full.
> 2. Read the YAML state block at the top of `progress.md` to get my session number, week, day,
>    and teaching mode.
> 3. Pull the items due at that session number from `review-queue.md`, plus open items from
>    `weak-spots.md`.
> 4. Announce the session in this format:
>    `Session <N> · Week <W> Day <D> · <mode> · Lane A: <pattern> · Lane B: <topic>`
> 5. Begin immediately with the 10-minute cold-recall block — question me on the due items with
>    my notes closed.
>
> **Do not ask me what I want to study.** The program decides that, and the answer is in the
> files. Do not restart or re-plan the program. Do not ask me to re-explain the setup.
>
> Two things you should know about how I want to be taught, both detailed in `TUTOR.md`:
> derive mechanisms rather than asserting them, and hold the ELI5 gate strictly — a concept
> doesn't reach L4 until I can explain it to a five-year-old without using any of its own
> jargon.
>
> At the end of the session, because you cannot write to my files, output the complete updated
> contents of `progress.md`, `review-queue.md`, `weak-spots.md`, and any new ELI5 entries, in
> separate clearly-labelled code blocks, so I can paste them back into my repo.
>
> One constraint that is not negotiable: I have a paid subscription to a commercial course
> whose modules I read separately. Never ask me to paste that course's content, and never
> reproduce or reconstruct it. This repo contains only my own writing.

## — copy to here

---

## Reduced-capability fallbacks

**If the context window is too small for all four files:** send `TUTOR.md` §2–§8 (protocol,
modes, rules, grading, bookkeeping) plus the YAML block from `progress.md` and the due items
only. Drop the full mastery table — it's the largest and least urgent part.

**If you have no AI at all:** the program still runs, degraded but real.
`eli5-glossary.md` is your textbook — cover the term, explain it aloud, check yourself.
`weak-spots.md` is your worklist. `coding/log.md` gives you problems due for re-solving from
scratch. Keep writing notes from recall; the recall is what was ever doing the work. Resume
tutored sessions when you can.
