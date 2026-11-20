# Incident review: a held release reached main

**Dates:** 13 to 14 August 2026 · **Severity:** process failure, no customer data affected · **Owner:** Khalid Mohamed

Written in the format from [delivery-templates](https://github.com/kalmehdar/delivery-templates/blob/main/templates/post-incident-review.md).

## Summary

A production release was on hold while I reviewed staging. A change reached `main` anyway, through a second working session in the same checkout, which defeated the hold. Separately, two working sessions following the same handover note edited the same files and overwrote each other's work, twice on 13 August and twice again on 14 August.

## Timeline

| When | What happened |
| --- | --- |
| 13 Aug | A large batch of operator-app work and audit fixes is deployed to staging. The production release is **held** for my review. |
| 13 Aug, overnight | Two sessions run from the same handover note. Because the note named specific working folders and branches, both sessions went into the same folders and wrote competing fixes. Finished work is reverted underneath one of them. |
| 13 to 14 Aug | A release reaches `main` through a second session sharing one checkout, while the hold is in place. |
| 14 Aug | Diagnosed and written up. Rules changed (below). The held release is then cut deliberately, all at once, after review. |

## Root cause

Not a code bug. Two process gaps:

1. **The hold existed only as an instruction.** Nothing enforced it, and a second session never saw it.
2. **Isolation was per folder, but the handover named the folders.** Separate working folders don't help if the plan sends every worker to the same one.

## What changed

| Change | Owner | Status |
| --- | --- | --- |
| One working folder (git worktree) per worker, never shared | Khalid | Done |
| A handover never names working folders as if they were free; each worker makes its own | Khalid | Done |
| A production hold is enforced by the person holding it, not by asking others to respect it | Khalid | Done |
| Production deploys became a manual step only a person can run (October 2026) | Khalid | Done |
| A single merge-queue claim for staging, so only one session merges at a time | Khalid | Done |

## What I took from it

The failure was in how work was handed over, not in what was built. When several workers share a codebase, the controls have to live in the system, not in the instructions.
