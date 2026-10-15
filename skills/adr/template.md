# ADR template

Copy everything below the line into `docs/adr/NNNN-short-kebab-title.md`. Keep the header fields, section names, numbering and order. Lists are real Markdown lists so the file pastes into Confluence correctly.

---

# ADR NNNN: <Decision stated as a sentence>

**Status:** <Proposed | Accepted | Rejected | Superseded by [ADR NNNN](NNNN-file.md)>

**Impact level:** <Low | Medium | High>

**Date:** <DD Mon YYYY>

**Authors:** <name>, <name>

## 1. Context

<The situation in domain terms: what exists today, what was planned, and why that is a problem now. No solution language.>

<What the domain is coupled to, as a short list:>

- <coupling one>,
- <coupling two>,
- <coupling three>.

<Scope of the domain (local to one product or cross project) and the constraint or friction that forces a decision.>

## 2. Decision

<Who> will <do what>, as <concrete technical shape>.

<Scope boundary: what this decision covers and what it explicitly does not, and the condition under which that would change.>

<Secondary benefits, clearly marked as not the primary reason.>

## 3. Decision drivers

- **<Driver headline>**
  - <One line explaining why it pushes towards the decision.>
- **<Driver headline>**
  - <...>
- **<Driver headline>**
  - <...>

## 4. Alternatives considered

### 4.1. <Alternative>

Rejected because:

- <concrete reason>,
- <concrete reason>.

### 4.2. <Alternative>

Rejected because:

- <concrete reason>.

### 4.3. <Alternative that may become valid later>

Rejected for now because:

- <concrete reason>.

<The condition under which this alternative would be reconsidered.>

### 4.4. Keep the current state

Rejected because:

- <concrete reason>.

## 5. Consequences

### ✅ Positive

- <Benefit>.
- <Benefit>.

### ⚠️ Negative / Trade-offs

- **<Cost or risk>**
  - <Who carries it, and how it is mitigated>.
- **<Cost or risk>**
  - <Who carries it, and how it is mitigated>.

## 6. Implementation and risk mitigation

Before <milestone, e.g. production release>, <the thing> must define:

- <contract, versioning>;
- <security model>;
- <operations: deployment, monitoring, incident ownership>;
- <testing>;
- <review with the relevant stakeholders>.

<Who remains accountable after release.>

## 7. Decision outcome

**Status:** <Under evaluation | Pending adoption | Adopted | Partially adopted>

**Outcome if approved:** <What changes in practice once the ADR is accepted.>

**Implementation notes:**

- <Concrete change required>.
- <Follow-up work, owner or ticket>.

## 8. References

- <Jira story key, only a real one, otherwise a TODO>
- <Related ADR or documentation page>
- <Book, article or internal guideline>
