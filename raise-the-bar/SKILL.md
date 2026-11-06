---
name: raise-the-bar
description: Use at the start of any substantive engineering or research task (feature, fix, perf work, experiment, paper section, review) and whenever the user says "raise the bar", "go deeper", "do it properly" (or "拔高", "做全", "往深了做"), or asks why something is so small/large. Reframes the request one level up (outcome, not task), makes the method expert-grade (deeper, not bigger), and names an outside judge before work starts. Not for quick questions, wording tweaks or one-line edits.
---

# Raise the bar

Based on Felix Rieseberg, "How to be more ambitious: a tutorial for humans with models" (2026-10-13).
The goal is a deeper version of the task, never just a bigger one. Reviewer bandwidth is
the scarce resource: a deeper change is usually *smaller* (a feature that is re-scoped around
the real question often ships at a third of the original size).

## Before starting: the 5-line ambition pass

Write these five lines to the user (in the user's language), then proceed with the upgraded
plan unless the upgrade changes scope a lot (new PR, new public behavior, spending shared
compute, pushing) — then ask once, with your recommendation first. Do not add approval gates
beyond that.

1. **Altitude** — the outcome behind the request.
   "Fix this CI failure" → "this class of CI break stops recurring".
   "Rebase this branch again" → "rebases are a one-command, self-verifying routine".
   "Add contention to one transfer path" → "contention is modeled consistently for every transfer path".
2. **Depth** — what a top engineer in the field would do that was not asked:
   the rawest material (upstream source at a pinned commit, traces, profiler stacks,
   upstream PRs) and the instruments (perf + flame graphs, parameter sweeps, parity digests,
   statistical fits), not markdown tables of totals.
3. **Outside judge** — what besides me shows it is right: a hardware measurement, upstream
   behavior at a cited commit, a stress probe that targets the new path, a reviewer persona
   that did not write the code. Unit tests and "parity 15/15" are necessary, not the judge.
4. **Unreasonable target** — state one hard, specific target as if reasonable:
   "p50 latency error < 10% on the reference trace", "no per-event cost growth from N=11 to N=61",
   "PR under 800 production lines", "a reader gets Figure 2 without the caption".
5. **Range** — the one other field whose method helps (queueing theory for fairness,
   forensic diff reading for reviews, a skeptical systems reviewer for paper claims). Tell the
   subagent to *do* that practitioner's work, never to role-play them.

## While working

- Challenge the framing once: if the existing format/design is the problem (a doc, a PR split,
  a review loop), say so and propose the replacement, validated against history.
- Hunt your own blind spot adversarially before the reviewer does: run the shape that stresses
  the new code path, and profile before attributing cost.
- Never grade your own work as the final word; hand it to the judge from line 3.
- When the same manual sequence happens a third time (rebase + resolve + test + parity +
  backup branch + PR-body update), propose turning it into a script or skill.

## When reporting

- Lead with the outcome against the line-4 target, then what the outside judge said.
- Cause → effect in plain words; one claim per sentence. If the user would ask "why", answer it first.
- List what would make the result more ambitious next time as one follow-up, not a menu.

## Anti-patterns

- Bigger instead of deeper: more files, more tests, more knobs without a sharper question.
- Minimal fix when the user's real goal is the class of problem.
- Self-grading: "all tests pass" as proof of fidelity or performance.
- Template filling when raw data exists (copying old PR body numbers instead of re-measuring).
- Role-play prompts ("act as a senior reviewer") instead of concrete methods.
