# RFC Authoring Guide

Use this when drafting an RFC (Request For Comments / design note) inside any
product repo in the Leo workspace. An RFC is the artefact you write **before**
code, to align on scope, API, risks, and acceptance criteria.

## When to write an RFC

Write one when the work:

- takes more than a single PR, or
- introduces or breaks a public API, or
- affects more than one repo, or
- commits to a non-obvious engineering trade-off.

Do **not** write one for local refactors, bug fixes, dependency bumps, or any
task that is obvious from reading the code.

## Where RFCs live

Inside the product repo, at `docs/plans/`. Not in `multica-home` — this repo is
for cross-project and reusable knowledge only. Examples:

- `pcl-rustic/docs/plans/rfc-0001-2026-04-30-pcl-rustic-roadmap.md`
- `multica/docs/plans/rfc-0005-2026-03-12-agent-runtime-sandbox.md` (hypothetical)

## Naming

```
rfc-{id}-{YYYY-MM-DD}-{kebab-case-title}.md
```

- `id` — zero-padded four-digit sequence, issued in order per repo (`0001`,
  `0002`, …). Never reuse an id. To pick the next one, `ls docs/plans/ | sort`.
- `YYYY-MM-DD` — the draft date (day you first wrote it), not the day it was
  accepted or merged.
- `kebab-case-title` — short slug, ≤ 6 words. No stopwords (the, of, a).

## Required sections

Each RFC includes these, in order:

1. **Front matter block** — Status, Date, Author, Tracking issue, Related RFCs.
   Status is one of `Draft`, `Proposed`, `Accepted`, `Rejected`, `Superseded`.
2. **Summary** — one paragraph. What this RFC commits to, in plain language.
   Should stand on its own when someone skims only this section.
3. **Motivation** — why now, why this way. Cite concrete constraints (user
   reports, audit findings, issue IDs), not aesthetic preferences.
4. **Detailed design** — API shapes, algorithms, file layout. Prefer Rust/Python
   code blocks with real type signatures over prose. Every design choice has a
   one-line "why this not the alternative" note.
5. **Acceptance criteria** — checklist of testable statements. Each item must
   answer "how do we know this is done" in a way a different agent can verify
   without reading the author's mind. Prefer commands (`cargo test …`,
   benchmark thresholds, comparison tests against a reference library) over
   adjectives ("fast", "correct").
6. **Risks & mitigations** — a table or bullet list. For each risk, name the
   trigger and the mitigation. "This might be hard" is not a risk.
7. **Out of scope** — list what this RFC *explicitly defers*. Prevents scope
   creep during review and tells future agents where to look when they find an
   adjacent gap.
8. **Open questions** — unresolved points that *should not block merging the
   RFC*. Each question names a proposed default and the trigger that would
   force a decision.

Optional, but often useful:

- **References** — links to prior art (Open3D tutorials, academic papers, Burn
  book, etc.). Avoid linking to chat transcripts.
- **Migration notes** — if the RFC breaks existing code, list the rename /
  delete / behaviour changes that downstream users will see.

## Style

- **Concrete > aspirational.** "`select(mask)` returns `Result<Self>` and runs
  on the tensor device" beats "selection should be fast and ergonomic."
- **Include the code signatures.** An RFC without at least one Rust/Python
  block of real type signatures is usually too vague to act on.
- **No TBDs in the acceptance criteria.** If something is genuinely open,
  put it in §8 Open questions and propose a default.
- **No marketing voice.** Skip "best-in-class", "world-class", "seamless".
- **Link downstream RFCs** when one unblocks another. Future agents tracing
  design decisions follow those links instead of re-reading everything.

## Size

Aim for 150–400 lines of Markdown. Under 100 usually means the design is too
vague to act on; over 500 usually means the RFC should be split. If you need
to split, the second RFC gets the next id in sequence and front-matter-links
the first as "Related".

## Lifecycle

1. **Draft** — author opens a PR against the product repo with the RFC file.
2. **Proposed** — reviewers add comments on the PR; the author addresses
   them in-place (amend, don't append).
3. **Accepted** — RFC PR is merged. Implementation tracking issue(s) open
   referencing the RFC's path. Status field flips to `Accepted`.
4. **Rejected / Superseded** — the status field changes but the file stays in
   the repo. Never delete an RFC; later RFCs reference its number as "the
   reason we did not go that way."

## Checklist before opening the RFC PR

- [ ] All eight required sections present.
- [ ] File is named per the convention above.
- [ ] Tracking issue ID in the front matter (open one first if missing).
- [ ] Acceptance criteria are testable and name specific artefacts.
- [ ] `docs/plans/README.md` (index) updated with a row for the new RFC.
- [ ] No literal `YOUR_USERNAME` / `TBD` / `TODO` strings in the body.
