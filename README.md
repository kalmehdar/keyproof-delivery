# How KeyProof ships

A delivery case study from KeyProof, the car and van hire software I co-founded in 2026 and run as CTO.

This repo is about **how the work is run**, not the code. The product source is private. Everything here is written from the project's own records: the release pipeline document, the decision log and the incident notes.

## The product, in one paragraph

KeyProof gives small UK car and van hire firms one link per hire. Every hire, checked and on record: the hirer checks in on their own phone, their photo ID is matched to a live selfie through Stripe Identity, they give the firm a DVLA check code that the firm checks on gov.uk, and they sign the firm's own agreement. Photos at handover and return land on the same record, which is sealed when the hire closes. KeyProof never judges damage; the firm decides.

The private beta opened on 2 November 2026. Public launch is planned for January 2027.

## My role

Two founders. I run product and delivery. I set the scope, write the rules the build follows, review every change and decide what ships.

## What's in here

| File | What it shows |
| --- | --- |
| [docs/release-process.md](docs/release-process.md) | How a change travels from a branch to production, and the controls on each step |
| [docs/incident-review-2026-08.md](docs/incident-review-2026-08.md) | A real production incident: a held release that reached `main` anyway, and the process change that followed |
| [docs/decisions.md](docs/decisions.md) | How decisions are logged, with real entries, and the prioritisation rule that governs the backlog |
| [docs/data-protection-first.md](docs/data-protection-first.md) | Compliance as delivery work: DPIAs before code, rules the product enforces, and a bug where two correct controls cancelled each other out |

## The short version

- **CI is the only path to production.** Every push runs lint, types, the full test suite (6,000+ tests) and a build. Nothing deploys if that fails, and the hosting platform's own auto-deploy is switched off.
- **Production deploys are a deliberate human action.** Merging a release only verifies `main`; a person then runs the production deploy. Automated sessions are blocked from starting it.
- **Everything is looked at on staging first**, with test payment and identity keys and synthetic data only.
- **Decisions are written down** with the reasoning and context, in one append-only log.
- **Compliance is scheduled like any other work:** DPIAs written and hash-sealed before the features they cover went live, ICO registration, and Cyber Essentials certification for KeyProof Ltd (November 2026).

## Elsewhere

- [keyproof.co.uk](https://keyproof.co.uk)
- [Delivery templates](https://github.com/kalmehdar/delivery-templates): the templates behind this work, with worked examples
- [LinkedIn](https://www.linkedin.com/in/khalid-mohamed-78227122a)
