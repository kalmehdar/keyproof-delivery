# Decisions and prioritisation

## The decision log

Every decision that changes scope, a rule, a process or something a customer sees goes in one append-only log, one line each:

```text
[date] DECISION: what was decided | REASONING: why, including what was rejected | CONTEXT: where it came from, what it touches
```

Corrections are new entries that point at the old one. Nothing is edited after the fact, so the log shows what we believed at the time and when that changed.

Real entries, lightly shortened:

```text
[2026-08-13] DECISION: KeyProof copy names the 24-month retention window rather
than implying a record is permanent. | REASONING: three pages promised a record of
"every hire you have ever done", while the daily retention sweep deletes a booking
24 months after the hire ends. False in the direction a firm cares about most. |
CONTEXT: the evidence hold (the clock stops while a dispute, claim or fine is open)
is named on the same page.

[2026-11-10] DECISION: the teaser post ends "Private beta opens Monday 16 Nov" and
the site switch flips that day. | CONTEXT: chosen so a visitor on the 16th sees the
same date as the post.

[2026-11-10] DECISION: CORRECTION to the entry above: the switch is NOT flipped. |
REASONING: the site already said the private beta was running (it opened 2 Nov);
flipping the switch would have moved the site backwards. | CONTEXT: found while
preparing the change.
```

The third entry is the reason the log exists. The mistake was caught in preparation, recorded next to the original, and nobody had to remember which version was right.

## The prioritisation rule

Written into the product repository in August 2026, for September to December 2026:

> No major feature is built unless it fixes a live customer's pain, removes onboarding friction, increases conversion, or meets a real compliance or security requirement.

Four tests, any one of which is enough, and "it would be nice" is not one of them. It turns "should we build this?" into a question that can be answered quickly.

## Decisions as options, not open questions

When a decision is mine to make, the work is prepared as two to four options with a recommendation first and the trade-off of each spelled out. A decision then takes one click, and the log records which option won and why.
