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

Track the steps with the todo tool if available. Ask every question with the structured question tool if available (options plus free text, defaults prefilled); otherwise ask in plain text, grouped, with defaults.

### 1. Find the target and the numbering

- ADR folder: use `docs/adr/` if it exists, otherwise ask where ADRs live and create it.
- Next number: the highest four digit prefix in the folder plus one. A retrofit or rewrite of an existing ADR keeps its number and file.
- Read the existing ADRs to find overlaps and ADRs this one supersedes or relates to.

### 2. Gather what is known

Read the whole conversation and the files the user mentioned or attached. Sort everything into two piles:

- **Known:** stated by the user or visible in the conversation or repo (the decision, the compared options, reasons given, numbers shown).
- **Unknown:** everything else.

Map the known pile onto the sections:

| Section | Take from |
|---|---|
| Title | The choice made, stated as a decision ("Use X for Y") |
| 1. Context | Current state, the problem, constraints, scope. No solution language |
| 2. Decision | What is adopted, by whom, its scope, what it does not cover |
| 3. Decision drivers | The criteria that actually decided it |
| 4. Alternatives considered | Options that were really compared, with the reasons given for rejecting them |
| 5. Consequences | Positives, and negatives with who carries them and the mitigation |
| 6. Implementation and risk mitigation | What must exist before release, who stays accountable |
| 7. Decision outcome | Adoption status, outcome if approved, implementation notes |
| 8. References | Jira story, related ADRs, docs, repos mentioned |

Never fill a section from your own reasoning. An alternative nobody compared, a driver nobody named or a trade-off nobody mentioned is not "known"; you may propose it as a suggestion in the questions, clearly marked as yours.

### 3. Ask (always, every run)

Always ask before anything is written, even when the conversation is rich. Invoking the skill never means "write it now". How much you ask depends on what is known.

**No context** (empty conversation, or the topic is unclear): do not guess. Start with one question: what decision is this about? Then interview section by section: the situation and problem, the options considered and why each lost, what drives the choice, costs and risks, what must exist before release. Offer concrete choices where you can, plus free text.

**Some or full context:** prefill. Show the draft as a short summary, marking what comes from the conversation and what is missing, then ask the user to confirm or correct it. Each question carries the prefilled value as the default, so the user can accept it with one action.

Ask these, in one grouped form if the tool allows:

1. **The decision,** as a sentence that becomes the title. If the conversation did not settle on one option, ask which one; never choose for the user.
2. **Header:** status (default Proposed), impact level (Low, Medium, High), date (default today), authors.
3. **Context and scope:** the problem in the user's words, what the ADR covers and what it does not.
4. **Drivers:** the criteria that decided it. Prefill with what was said; offer your own suggestions separately.
5. **Alternatives:** the options that were really considered and the real reason each lost. If only one was compared, say so and ask whether others were considered rather than inventing them.
6. **Consequences:** positives, and negatives with who carries them and the mitigation. Prefill only what was discussed.
7. **Before release and ownership:** prerequisites, who stays accountable, who reviews.
8. **Jira:** the story key if there is one; otherwise `<TODO: Jira story>`. Ask for the parent epic key once if the team tracks ADRs under an epic.
9. **Evidence from the repo,** only with consent: search the code for real names (packages, modules, files, counts) to cite. Verify every number against the repo.

Skip a question only when the user already answered it explicitly in this conversation, and then show the answer as prefilled so it can be corrected. Ask follow ups until no section depends on a guess.

### 4. Outline and approval

Present the outline: file path, header, bullets per section (mark every item that is your suggestion, not the user's), remaining `<TODO>` items, side effects (superseded ADR to update). Iterate until the user approves. Do not write before approval.

### 5. Write

Write the file following [template.md](./template.md) and [format.md](./format.md). Then reopen it and run the checklist in format.md; fix what fails.

### 6. Report

Report the file path, the checklist result, open `<TODO>` items and any other file changed. Offer to paste-check: the file is plain Markdown and can be pasted into a Confluence page (Insert, Markup, Markdown) as is.

## Rules

- Always ask before writing. Never write from conversation context alone, and never fill a section with content the user did not give or confirm.
- Never invent Jira keys, links, people, teams, dates or numbers; leave `<TODO: …>`.
- Never edit the meaning of an Accepted ADR. A new ADR supersedes it, and only the old ADR's status line changes.
- Write real Markdown lists ("- " bullets, "1." ordered, nested lists indented by two spaces, one item per line, a blank line before each list), never "•" characters, so the file pastes into Confluence correctly. No dashes as sentence separators.
- One decision per ADR.
