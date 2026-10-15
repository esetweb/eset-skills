---
name: adr
description: 'Write an ADR (Architecture Decision Record) as a Markdown file, from the current conversation or from an interview, using the bundled template, with no MCP server or external service needed. The output pastes cleanly into Confluence. Use when: "write an ADR", "make this an ADR", "record this decision", after comparing options (library, architecture, framework choices), superseding or retrofitting an existing ADR.'
argument-hint: 'Optional: the decision in one sentence, status, authors, Jira key'
---

# ADR

Turns a decision into one ADR file. Everything the skill needs is in this folder:

- [template.md](./template.md): the section structure to follow exactly.
- [format.md](./format.md): what each section must contain, writing style, lifecycle, checklist.
- [example.md](./example.md): a short illustrative ADR for tone and level of detail.

No Confluence, Jira or other MCP server is needed. Never call one for this skill; links and keys come from the user.

## Procedure

Track the steps with the todo tool if available. Ask every question with the structured question tool if available (options plus free text); otherwise ask in plain text, grouped, with defaults.

### 1. Find the target and the numbering

- ADR folder: use `docs/adr/` if it exists, otherwise ask where ADRs live and create it.
- Next number: the highest four digit prefix in the folder plus one. A retrofit or rewrite of an existing ADR keeps its number and file.
- Read the existing ADRs to find overlaps and ADRs this one supersedes or relates to.

### 2. Extract the decision

If the conversation already compared options, read all of it and draft the mapping below. Otherwise interview the user for the same fields.

| Section | Take from |
|---|---|
| Title | The choice made, stated as a decision ("Use X for Y") |
| 1. Context | Current state, the problem, constraints, scope. No solution language |
| 2. Decision | What is adopted, by whom, its scope, what it does not cover |
| 3. Decision drivers | The criteria that actually decided it |
| 4. Alternatives considered | Every real option with concrete rejection reasons |
| 5. Consequences | Positives, and negatives with who carries them and the mitigation |
| 6. Implementation and risk mitigation | What must exist before release, who stays accountable |
| 7. Decision outcome | Adoption status, outcome if approved, implementation notes |
| 8. References | Jira story, related ADRs, docs, repos mentioned |

Show the draft and mark: facts from the conversation, gaps, and anything left undecided.

### 3. Ask

1. **Confirm the decision.** If the conversation did not settle on one option, ask which one. Never choose for the user.
2. **Header:** status (default Proposed), impact level (Low, Medium, High), date (default today), authors.
3. **Gaps:** scope and non-goals, ranked drivers, the real reason each alternative lost, negatives and mitigations, prerequisites before release, reviewers.
4. **Jira:** ask for the story key if there is one; otherwise leave `<TODO: Jira story>`. Ask for the parent epic key once if the team tracks ADRs under an epic.
5. **Evidence from the repo,** only with consent: search the code for real names (packages, modules, files, counts) to use in the ADR. Verify every number you cite against the repo.

### 4. Outline and approval

Present the outline: file path, header, bullets per section, remaining `<TODO>` items, side effects (superseded ADR to update). Iterate until the user approves. Do not write before approval.

### 5. Write

Write the file following [template.md](./template.md) and [format.md](./format.md). Then reopen it and run the checklist in format.md; fix what fails.

### 6. Report

Report the file path, the checklist result, open `<TODO>` items and any other file changed. Offer to paste-check: the file is plain Markdown and can be pasted into a Confluence page (Insert, Markup, Markdown) as is.

## Rules

- Never invent Jira keys, links, people, teams, dates or numbers; leave `<TODO: …>`.
- Never edit the meaning of an Accepted ADR. A new ADR supersedes it, and only the old ADR's status line changes.
- Write real Markdown lists ("- " bullets, "1." ordered, nested lists indented by two spaces, one item per line, a blank line before each list), never "•" characters, so the file pastes into Confluence correctly. No dashes as sentence separators.
- One decision per ADR.
