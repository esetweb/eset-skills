# eset-skills

Agent skills for ESET frontend work, installable with the [skills CLI](https://github.com/vercel-labs/skills).

## Skills

| Skill | What it does |
|---|---|
| `adr` | Writes an Architecture Decision Record as a Markdown file from the current conversation or an interview, using a bundled template. No MCP server needed. Output pastes cleanly into Confluence. |

## Install

From GitHub, once this repo is published:

```sh
npx skills add <owner>/eset-skills
```

From a local checkout:

```sh
npx skills add ./eset-skills
```

Install one skill only:

```sh
npx skills add <owner>/eset-skills --skill adr
```

The CLI asks which agent (Copilot, Claude Code, Cursor and others) to install into.

## Use

In a repo, tell the agent for example: "write an ADR from this conversation" or "make this an ADR". The skill finds `docs/adr/`, picks the next number, asks for missing header fields and gaps, shows an outline for approval, then writes `docs/adr/NNNN-short-title.md`.

## Layout

```
skills/
  adr/
    SKILL.md      the procedure the agent follows
    template.md   ADR section structure
    format.md     what each section holds, style, checklist
    example.md    short illustrative ADR
```

A new skill is a new folder under `skills/` with its own `SKILL.md` (frontmatter `name` and `description`).

## Before publishing

Check that no internal hostnames, repository names or ticket keys are in the skill files. Publish to a private or internal repository if they must stay.
