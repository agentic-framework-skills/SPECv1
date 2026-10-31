# SPECv1

**SOFTWARE PRODUCT SPECIFICATION ENGINE** — an architecture-agnostic, agent-agnostic skill that produces complete software product specifications using **RFC 2119 normative language**, organized into dedicated folders per discipline, and recommends publishing them to a dedicated git repo.

The skill embeds the full RFC 2119 normative language (MUST / MUST NOT / SHOULD / SHOULD NOT / MAY) so agents using this skill never need to consult external sources for requirement-level semantics.

The skill is a self-contained system prompt in [`SPECv1/SKILL.md`](SPECv1/SKILL.md). It can be loaded by any agent via the [`skills`](https://github.com/vercel-labs/skills) CLI (`npx skills`) — or applied directly as agent instructions.

---

## What it does

`SPECv1` authors complete software product specifications:

1. **WHAT Capture** — Extracts the product concept from a single sentence.
2. **Infrastructure & Org Verification** — Before `INIT`, confirms dedicated-repo preference and organizational context.
3. **RFC 2119 Normative Authoring** — Every requirement statement uses capitalized MUST / MUST NOT / SHOULD / SHOULD NOT / MAY.
4. **Dedicated Folders** — 11 disciplines, each in its own folder with a minimum schema (Scope, Normative Statements, Open Questions, Change Log).
5. **Org Structure** — If the product belongs to an org, documents teams, owners, reporting lines, and escalation paths.
6. **Dedicated Git Repo** — Recommends and, if agreed, supplies `git init` / remote add / initial commit commands for a standalone specs repo.

---

## The 11 Specification Folders

| # | Folder | Discipline |
|---|---|---|
| 01 | `01-product-vision/` | Product Vision (+ org structure if applicable) |
| 02 | `02-prd/` | Product Requirement Document (+ stakeholder register) |
| 03 | `03-architecture/` | Architecture (components, boundaries, data flow, topology) |
| 04 | `04-adrs/` | Architecture Decision Records |
| 05 | `05-requirements/` | Functional (FRs) and Non-Functional Requirements (NFRs) |
| 06 | `06-schemas/` | Data, API, event, and configuration schemas |
| 07 | `07-sdlc/` | Software Development Life Cycle |
| 08 | `08-code-conventions/` | Naming, formatting, linting, commit, review standards |
| 09 | `09-housekeeping/` | Workspace housekeeping processes |
| 10 | `10-script-helpers/` | Normative script helpers |
| 11 | `11-implementation-plan/` | Implementation plan + traceability matrix |

---

## Usage

```
WHAT <product concept>
    # e.g., "A real-time collaborative analytics dashboard for SaaS teams"
    # e.g., "An event-driven order processing platform on Kubernetes"

# The engine will ask about dedicated git repo and org context, then await:

INIT
    # Triggers autonomous authoring of all 11 folders in RFC 2119 language
```

---

## Example RFC 2119 output

> The system MUST authenticate every inbound API request using OAuth 2.0.
> The system SHOULD cache responses for at least 60 seconds when the backend is idle.
> The system MAY emit telemetry events to an external observability platform.

Lowercase `must`/`should`/`may` are prohibited in requirement text.

---

## Author

Developed by **Jean Machuca** — [GitHub @jeanmachuca](https://github.com/jeanmachuca) ·
[Sponsor on GitHub Sponsors](https://github.com/sponsors/jeanmachuca).

---

## License

Distributed under the **MIT License**.