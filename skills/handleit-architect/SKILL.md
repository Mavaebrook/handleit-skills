---
name: handleit-architect
description: Project architect and enforcer for HandleIT. Use BEFORE implementing, fixing, refactoring, building, or resuming any HandleIT software work. Establishes project truth, enforces decision boundaries, writes a plan before multistep edits, preserves prior corrections, and enforces GitHub-Actions-only APK builds. Load this skill at the start of every HandleIT coding or build session.
---

# HandleIT Architect

Permanent instruction for HandleIT. Load and follow this skill before software changes.

Before software changes, load and follow the Architect skill. For multistep implementation, create or update a persistent plan before editing product code. Preserve established requirements, previous corrections, and existing behavior outside the requested change. Missing instructions are not permission to make product decisions. Use the designated GitHub repository as canonical source and its designated GitHub Actions workflow for APK builds; never substitute APK decompilation/reconstruction or local/proot APK builds. If the skill cannot be loaded, these rules still apply: diagnose the loading problem and restore access before implementation. Keep the plan, correction record, changelog, and affected README content current. Do not override these rules for convenience; only an explicit user instruction can authorize a scoped exception.

## Purpose and triggers

Use before implementing, fixing, refactoring, building, or resuming software work. Keep the workflow proportional: a small fix needs a short plan, not a large specification. Read-only investigation and brainstorming may proceed without creating project documents. Apply the source, scope, and correction rules even to single-step edits.

Treat the user's requested outcome, explicit constraints, and prior corrections as requirements. Permission to achieve an outcome does not imply permission to replace the agreed process.

## 1. Establish project truth

Read the applicable repository instructions, current plan or PRD, persistent constraints/corrections, README, changelog, relevant source, and recent changes. Reuse existing equivalents of the documents described below; do not create competing sources of truth.

Identify and record:

- Canonical GitHub repository, designated base branch, and working branch.
- Current commit, remote state, and uncommitted changes.
- Exact GitHub Actions workflow used for APK builds and its expected artifact.
- Relevant prior fixes and acceptance evidence, plus unresolved problems.

Use a normal source checkout for inspection and authorized editing. Confirm freshness against the designated remote branch and preserve unrelated work. Never discard changes or reset a branch merely to obtain a clean workspace. Do not silently choose a different repository or branch. Discover missing configuration from authoritative project records; ask a focused question only if it remains unknown and blocks the next action.

Treat an installed APK as a binary artifact, not the development source. Never decompile/reconstruct an APK as a replacement source tree or ship a build from such a tree. Any separately authorized binary inspection must remain separate from canonical source development.

## 2. Enforce decision boundaries

| Decision | Required behavior |
| --- | --- |
| Explicit requested change | Implement within established constraints. |
| Necessary internal detail that preserves behavior and constraints | Choose autonomously; record architecturally significant choices. |
| Unspecified feature, appearance, workflow, privacy behavior, ongoing cost, permission, or externally visible behavior | Preserve the existing choice. If a new choice is necessary, ask before implementing that portion. |
| Optional improvement or unrelated refactor | Propose separately; do not include without authorization. |
| Replacement/removal, source change, build-route change, or reversal of a previous correction | Require explicit user authorization for that specific change. |

Do not ask again for decisions already made. Consult project records before asking. Group related consequential questions and continue independent authorized work while one portion is blocked. Label assumptions as assumptions; never promote them into confirmed requirements. A generic instruction such as "fix it," "make it work," or "use your judgment" does not waive recorded constraints.

When a new explicit instruction supersedes an earlier requirement, record the scope and reason, retaining history. Resolve material ambiguity before implementing the conflicting portion. Authorization for one exception does not create a permanent exception.

## 3. Write a plan before multistep implementation

Use the existing project convention, or default to `docs/plans/<task-name>.md`. For a substantial feature, include a PRD section or link to the existing PRD. Create this in the canonical repository before editing product code, and keep it versioned with the work.

Minimum plan:

```markdown
# Task: <name>
Status: planned / in progress / blocked / verified / partially verified
Goal:
Canonical repo / base branch / working branch / starting commit:
APK workflow / expected artifact:

## Requirements and acceptance
| ID | Requirement | Source | Affected component | Acceptance check | Status/evidence |
| --- | --- | --- | --- | --- | --- |

## Constraints and preserved behavior
- Applicable correction IDs:
- Out of scope / rejected approaches:

## Architecture and execution
- Existing behavior and reusable components:
- Proposed changes and why they meet the requirements:
- Ordered steps and dependencies:
- Relevant failure/recovery considerations:

## Decisions and open questions
- Confirmed decisions:
- Assumptions awaiting resolution:
- Scoped user-authorized exceptions:

## Documentation and verification
- CHANGELOG update:
- README impact / update, or reason no change is needed:
- Checks, results, and remaining limitations:

## Resume checkpoint
- Current commit/branch and uncommitted work:
- Completed / remaining steps:
- Active constraints and unresolved questions:
- Actions run / artifact status:
- Next authorized action:
```

For a substantial feature, also specify user workflows, functional and relevant nonfunctional requirements, component boundaries, data/interface changes, and migration needs. Do not invent features to fill a template. Mark irrelevant sections accordingly.

Show the user a concise plan summary. Proceed with already authorized work; plan creation is not an automatic approval gate. Ask only about unresolved consequential choices.

## 4. Preserve corrections across tasks

Maintain the existing correction/constraint record, or use `docs/PROJECT_CONSTRAINTS.md`. Record stable IDs, the user's instruction or faithful paraphrase, date/source when known, rationale when known, affected components, verification method, and active/superseded status.

Record a correction when received, before implementing the affected work. Never fabricate the user's wording or rationale. Preserve rejected approaches. Link a superseded item to the explicit replacement decision instead of deleting it.

Before each relevant change and before delivery, check that the implementation preserves applicable corrections. Use an executable regression check when practical and meaningful; otherwise document a reproducible manual check. Unavailable testing means unverified, not passed.

## 5. Implement within the plan

Map changes to requirement IDs. Prefer focused changes and existing working components. Do not rewrite unrelated code, change tools, remove functionality, or redesign interfaces to simplify your work.

Update the plan when requirements or discoveries change it. Preserve prior obligations unless explicitly superseded. Pause only affected work when a new conflict appears. Do not delete or weaken tests, acceptance criteria, or correction records to make the implementation appear compliant.

For a new session, interrupted task, or handoff, read the checkpoint and project records, then verify actual source/build state before continuing. Never rely on a remembered or summarized state when the repository provides current evidence.

## 6. Use the designated build route

Build APKs only through the designated GitHub Actions workflow from committed source pushed to the designated working branch. Local/proot APK compilation, binary patch-and-repack, and decompiled-project builds are prohibited unless the user explicitly authorizes a scoped exception. Ordinary source inspection, editing, and allowed non-APK checks do not change this rule.

Before triggering an APK build, review the diff against requirements and prior corrections, run feasible relevant non-build checks, and check configuration. Avoid repeated builds without a concrete change or diagnosed transient failure.

If Actions fails, inspect the actual failure and fix the authorized source/configuration cause. If access, quota, secrets, runner availability, or required authorization blocks progress, report the specific blocker and preserve a checkpoint. Do not silently switch environments or weaken build/signing settings.

For each delivered APK, record the repository, full commit SHA, workflow and run URL/ID, successful run status, artifact name, and available version information. Verify that the downloaded/delivered artifact is from that run; do not select an older artifact because its filename looks correct. Record a file hash when available. Never claim provenance that has not been checked.

## 7. Keep documentation accurate

Update `CHANGELOG.md` for meaningful completed changes under `Unreleased`, including fixes and breaking changes when applicable. Move entries to a version/date when actually released. Do not list planned work as completed or overwrite prior release history.

Review `README.md` every implementation task. Update affected features, usage, setup, dependencies, permissions, and build instructions to reflect actual behavior. If no README change is needed, record why in the plan; do not make cosmetic edits merely to mark it updated.

Keep documentation and code versioned together. The plan describes intent and progress; the changelog records completed changes; the README describes the current product. Do not document intended functionality as shipped.

## 8. Complete with evidence

Before claiming completion:

- Reconcile every requirement against implementation and acceptance evidence.
- Check applicable prior corrections and unintended behavior changes.
- Verify the relevant documentation changes and remaining work status.
- For APK delivery, verify commit/run/artifact provenance.
- Distinguish source review, compilation, automated tests, device testing, and user acceptance. One does not prove another.

Report briefly: what changed, what was checked and the results, build/artifact provenance when relevant, and remaining limitations or blockers. If device testing is unavailable, state that clearly and supply targeted manual checks. Never describe a partially verified result as fully working.

## Acceptance scenarios (behavioral reference)

| Scenario | Expected behavior |
| --- | --- |
| User asks for a small fix but says nothing about redesign | Preserve UI/workflow; make necessary internal changes only. |
| A previous correction complicates the new implementation | Preserve it or ask about the specific conflict; do not silently reverse it. |
| Actions is unavailable and an old APK is accessible in proot | Diagnose/report the blocker; do not reconstruct or build locally. |
| A multistep task arrives | Save a proportional plan before product code edits. |
| User corrects one part mid-task | Update requirements and correction history; retain the rest of the task. |
| Build passes but no device test ran | Report build success and device behavior as unverified. |
| Session resumes with an old checkout | Verify branch/remote/current fixes and preserve local work before proceeding. |
| README is unaffected | Record the review and no-change reason; update changelog if the change merits it. |
| User explicitly allows one local build | Record the scoped exception; retain GitHub as canonical source unless separately changed. |

These are behavioral instructions, not a technical enforcement mechanism. Installation and runtime acceptance checks remain necessary.
