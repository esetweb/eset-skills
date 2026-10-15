# ADR format

How an ADR must look and read. The section structure comes from [template.md](./template.md); this file explains what goes into each part, the writing style, and how to check the result.

## What an ADR is

One architectural decision: the problem, what was decided, what was rejected and why, and what it costs. One decision per file; a second decision is a second ADR.

1. **The title states the decision, not the topic.** "Use Drizzle ORM for the nomination API", not "ORM choice".
2. **The decision is prescriptive and scoped.** Who does what, in which shape, and what it explicitly does not cover.
3. **Rejections have reasons.** A preference is not a reason.
4. **Trade-offs are honest.** Every decision has negatives; each one comes with its mitigation.
5. **Numbered headings**, so reviews can cite "ADR 0003 section 4.2".

## File

- `docs/adr/NNNN-short-kebab-title.md`, next free four digit number. A retrofit keeps its number and file.
- Title line: `# ADR NNNN: <decision as a sentence>`.
- The introduction of the template is not copied into the ADR.

## Sections

| Part | What goes in it |
|---|---|
| Header | **Status** (Proposed, Accepted, Rejected, Superseded by …), **Impact level** (Low, Medium, High), **Date**, **Authors**. |
| 1. Context | The situation in domain terms: what exists today, what was planned, what the domain is coupled to, its scope, and the friction that forces a decision. No solution language. |
| 2. Decision | Who will do what, in which concrete technical shape. Then the scope boundary (what it does not cover, when that would change) and any secondary benefit, marked as not the primary reason. |
| 3. Decision drivers | Bold headline per driver, a nested line explaining why it pushes towards the decision. |
| 4. Alternatives considered | `4.1`, `4.2`… one `###` sub section per real alternative, each with a "Rejected because:" list of concrete reasons. Use "Rejected for now because:" plus the reconsider condition for options that may become valid later. Include "keep the current state" when it was a real option. |
| 5. Consequences | `✅ Positive` and `⚠️ Negative / Trade-offs`. The negatives list is never empty and names who carries each cost and how it is mitigated. |
| 6. Implementation and risk mitigation | What must be defined before the milestone (contracts, security, data, operations, testing, stakeholder review), and who stays accountable after release. |
| 7. Decision outcome | **Status** of adoption (Under evaluation, Pending adoption, Adopted, Partially adopted), separate from the ADR status; **Outcome if approved**; **Implementation notes** with concrete follow up work. |
| 8. References | Jira story, related ADRs and pages, sources, compared repositories. |

## Writing style

- Plain, direct English, short sentences, no marketing language.
- Past tense for what was considered, present tense for what is decided.
- Specific: how many teams, which services, which versions. Verify every number against the repo or source.
- Real names from the codebase in backticks. A 3 to 6 line example beats a paragraph.
- Roughly one to two pages. Link out instead of pasting long analysis.
- Unknown facts stay a visible `<TODO: …>`. Never invent Jira keys, links, people, teams, dates or numbers.

## Markdown that pastes into Confluence

- Lists are real Markdown lists: `- ` bullets, `1.` for ordered, one item per line. Never "•" characters, never items joined into one sentence.
- A blank line goes before every list.
- Detail under an item is a nested list indented by two spaces.
- Section `4.x` alternatives are `###` headings.
- No dashes as sentence separators.

## Lifecycle

1. New ADRs start as **Proposed**, with a tracking story in References.
2. Affected teams review; on agreement the status becomes **Accepted** and the date is the decision date.
3. An Accepted ADR is never edited to change its meaning. A new ADR supersedes it: the old one's status becomes `Superseded by [ADR NNNN](NNNN-file.md)` and the new one references the old one.
4. **Decision outcome** is updated as adoption progresses.

## Checklist

1. Title states the decision, not the topic.
2. Header complete: status, impact level, date, authors.
3. Jira and other links are real or marked `<TODO>`.
4. Context describes the problem without solution language.
5. Decision is prescriptive and states its scope and what it does not cover.
6. Decision drivers are named, each with a reason.
7. Every alternative has a concrete "Rejected because" list.
8. Consequences have a non-empty Negative / Trade-offs list with mitigations.
9. Implementation and risk mitigation lists what must exist before release and who stays accountable.
10. Decision outcome separates adoption status from ADR status and lists implementation notes.
11. References cite the Jira story, related ADRs and sources.
12. Examples use real names from the codebase.
13. Lists are real Markdown lists with a blank line before each.
