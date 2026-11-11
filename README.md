# HandoverTrail

Turns scattered project activity into a reviewed, evidence-linked handover for the person taking over a project.

**Live demo:** [add your published link here]
**Round:** 2 (working prototype). Demo data is fully synthetic.

## Try it (no setup)

Open `handovertrail.html` in any browser, or use the live link.

1. **Connect:** tick the authorised sources, set sensitivity, optionally paste your own lines (`2026-10-09 | Meeting: agreed to use Redis`).
2. **Reconstruct:** choose the incoming role. Sources that role cannot see are removed before extraction.
3. **Review:** open any citation to see the exact source line. Approve, reject or edit each claim.
4. **Handover:** finalize a versioned handover, then acknowledge receipt as the incoming person.

Suggested check: run as *Backend maintainer*, then *Project lead*. The private committee note appears only for the lead.

## What works

- Import of repo log, meeting notes, task board and chat sources, with redaction of emails, phone numbers and keys
- Role-based source filtering before extraction
- Claims for ownership, decisions, risks, dependencies, blockers, open questions and next actions
- Exact-line citations with a source viewer; a verifier drops any claim whose quoted line is not in its source
- Status labels: Verified, Inferred, Conflicting (sources disagree), Missing (gap, not guessed), Reviewer-confirmed
- Decision timeline, per-claim approve/reject/edit, versioned handover, acknowledgement, activity log

## How it works

Single client-side page (HTML, CSS, JavaScript, no dependencies). Each source line is `date | text`. Rule-based pattern matching turns lines into typed claims, each carrying its source id, line number and quoted text. A verifier re-checks every quote against the stored source. Inferred next actions are labelled as system suggestions. Edited claims are labelled as having no source evidence.

## Known limitations (Round 2)

- Extraction is rule-based, not an LLM, and expects the `date | text` line format
- Access control runs in the browser, so it is a demonstration, not real security
- No login, and nothing is saved after a refresh
- Conflict detection currently covers database decisions only

## Planned for Round 3

1. Flask and MongoDB backend with login, server-side access control, persistence and an audit log
2. LLM-based extraction, with the same quote verifier kept as a gate
3. Gap-closing exit interview for the leaver, plus a knowledge-at-risk map

## AI disclosure

Code and documentation were written with AI assistance (Claude). No AI model runs inside the product.
