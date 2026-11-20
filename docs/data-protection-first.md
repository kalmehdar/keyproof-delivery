# Data protection as delivery work

KeyProof handles photo ID, faces and driving licence details, so compliance was planned and scheduled like any other deliverable, not added at the end.

## Before the code

- **DPIAs written before the features they cover went live**, and hash-sealed by the product itself, so a sign-off can't outlive the document it signed. If the text changes, the seal breaks and the assessment has to be signed again.
- **Results, not documents.** Identity is checked by Stripe Identity (photo ID matched to a live selfie); KeyProof keeps the result, never a folder of passport scans.
- **KeyProof never runs the licence check.** The hirer gives a DVLA check code; the firm checks it on gov.uk; the product records that it was done and when.
- **Retention is enforced by scheduled code**, not by someone remembering to delete things.
- ICO registration from July 2026. KeyProof Ltd **Cyber Essentials certified**, November 2026.

## Rules the product enforces

Some decisions are written as architecture decision records and backed by tests, so they can't quietly erode:

- The product **never judges damage**. It records the before and after; the firm decides.
- A signed agreement snapshot is **never changed** after signing.
- Seals are **never backfilled** onto older records.
- Safety and verification features are **never put behind a paid tier**.

## When two correct controls cancel out

The licence check runs on a DVLA check code the hirer generates. That code is personal data, so a nightly job erases it after 30 days, the kind of retention rule you're supposed to write.

The evidence pack decided whether a licence had been checked by looking for that code. So on day 31, closed records began printing "no licence check recorded" for hires where the check had happened: 21 closed records in the test data, each ready to tell an insurer the firm had skipped a step it hadn't.

The fix was small: read the timestamp that says the check was done, which the retention sweep has no reason to touch, instead of the code. Data minimisation carries on exactly as before.

It only surfaced because the test database was seeded with hires old enough to cross the 30-day boundary. **Most retention policies have never been tested on data old enough to trigger them.**
