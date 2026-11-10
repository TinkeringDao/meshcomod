# Fully Autonomous Development Pipeline Specification (`meshcomod`)

This document defines the end-to-end **6-Stage Autonomous Development, Review, Remediation, and Merge Pipeline** governing all code, firmware configuration, board variant, and documentation changes in `TinkeringDao/meshcomod`.

---

## Architecture Overview & Gemini 4 Argon (`trackerIntake`) Worker Loop

Autonomous execution is driven by the **Gemini 4 Argon (`agy` / `gemini-4-argon-high`)** Kanban `trackerIntake` worker loop, which continuously polls open GitHub tracker issues, provisions an isolated git worktree branch, executes the 6-stage pipeline below, resolves all CI and inline `reviewThreads` gates, squash-merges approved Pull Requests into `main`, and retains operational learnings in Hindsight.

```mermaid
flowchart TD
    TI["Kanban trackerIntake: Poll Open GitHub Issues (agy / gemini-4-argon-high)"] --> S1["Stage 1: Context & Hindsight Recall"]
    S1 --> S2["Stage 2: Branch Isolation & Signed TDD Implementation"]
    S2 --> S3["Stage 3: Pull Request Creation (Summary / Evidence / Merge Danger)"]
    S3 --> S4A["Stage 4A: GitHub Actions 4-Gate CI (.github/workflows/autonomous-pr-review.yml)"]
    S3 --> S4B["Stage 4B: Independent Agentic Spec, Code & Security Review"]
    S4A --> S5{"Stage 5: Findings, Unresolved reviewThreads, or Gate Failures?"}
    S4B --> S5
    S5 -- "Yes" --> REM["Autonomous Remediation Loop (Signed Commit + Push + Thread Resolution)"]
    REM --> S4A
    REM --> S4B
    S5 -- "No (Zero Unresolved Findings / reviewThreads)" --> S6["Stage 6: Automated Bot Approval, Squash Merge & Hindsight Retention"]
```

---

## Stage 1: Context & Hindsight Recall

Before modifying any source file (`src/`, `examples/`, `arch/`), board variant (`variants/`), or build configuration (`platformio.ini`), the autonomous agent MUST:

1. **Query Hindsight Semantic Memory** (parameterized via `${HINDSIGHT_URL}`, e.g. `http://127.0.0.1:9100`, and `${HINDSIGHT_BANK}`, e.g. `default`):
   ```bash
   export HINDSIGHT_URL="${HINDSIGHT_URL:-http://127.0.0.1:9100}"
   export HINDSIGHT_BANK="${HINDSIGHT_BANK:-default}"
   curl -s -X POST "${HINDSIGHT_URL}/v1/default/banks/${HINDSIGHT_BANK}/memories/recall" \
     -H "Content-Type: application/json" \
     -d '{"query": "meshcomod MeshCore multi-transport companion repeater SX1262 LR1110 AXP2101 BQ25896 legal RF safety"}'
   ```
2. **Read Repository Governance & Domain Specifications**:
   - [`AGENTS.md`](../../AGENTS.md) — Target board/variant architecture, PlatformIO & `build.sh` commands, prebuilt release invariants, and RF/PMIC safety boundaries.
   - [`LEGAL.md`](../../LEGAL.md) — 8-pillar legal compliance framework, EU RED / ETSI / FCC RF limits, and the German Statutory Addendum (`Addendum: German Statutory References`).
   - [`SECURITY.md`](../../SECURITY.md) — Coordinated vulnerability disclosure, cryptographic boundaries, and OPSEC rules.
   - [`docs/agents/domain.md`](domain.md) — Domain vocabulary and architectural conventions.

---

## Stage 2: Branch Isolation & Signed TDD Implementation

1. **Branch Isolation (`trackerIntake` Worktree)**:
   - Direct pushes to `main` are blocked by the repository ruleset (`Protect main branch`).
   - When the Gemini 4 Argon (`agy` / `gemini-4-argon-high`) `trackerIntake` worker claims an issue, all work MUST execute in an isolated worktree on a dedicated feature, bugfix, or chore branch (`feat/*`, `fix/*`, `chore/*`, `docs/*`) branched cleanly from `origin/main`.
2. **Cryptographically Signed Commits**:
   - Every commit MUST be authored by `TinkeringDao <203040288+TinkeringDao@users.noreply.github.com>` and signed with the organization's ED25519 SSH signing key (`git commit -S -s -m "..."`):
     ```bash
     git config user.name "TinkeringDao"
     git config user.email "203040288+TinkeringDao@users.noreply.github.com"
     git config commit.gpgsign true
     ```
3. **Hardware, RF & PMIC Safety Boundaries**:
   - **LoRa Transceiver & External PA Boundaries (`SX1262`, `LR1110`, `SX1276`)**: Verify that regional frequency presets, external front-end amplifier (`PA` / `FEM` on `Heltec V4`, `Station G2`, etc.) gain offsets, conducted power (`dBm`), and duty-cycle ceilings (`<= 1%` in `868.0–868.6 MHz` SRD `g1`; `<= 10%` in `869.400–869.650 MHz` SRD `g3` under `ETSI EN 300 220-1/-2` / `Directive 2014/53/EU (RED)`; `FCC 47 C.F.R. Part 15.247`) are strictly respected.
   - **PMIC & Lithium-Ion Battery Boundaries (`AXP2101`, `AXP192`, `BQ25896`, `INA3221`)**: Verify that charge termination voltage (`<= 4.20–4.288 V`), fast-charge current (`C-rate`), and NTC temperature protection (`0–45 °C`) are never overridden beyond safe hardware datasheet ratings.
   - **Clean-Room & License Provenance**: Preserve `MIT` license headers (`LICENSE`) and upstream attributions (`Scott Powell / Ripple Radios and MeshCore contributors`, `arch/esp32/AsyncElegantOTA/LICENSE`, `arch/stm32/Adafruit_LittleFS_stm32/src/littlefs/LICENSE.md`).

---

## Stage 3: Pull Request Creation

Open a Pull Request against `main` via GitHub CLI (`gh pr create`) referencing the intake issue (`Closes #<issue_number>`) and containing three mandatory sections:

- `## Summary`: Concise technical explanation of what changed and why.
- `## Evidence`: Verification output from local builds (`pio run`), unit tests (`pio test -e native -e native_kiss_modem`), or static analysis.
- `## Merge Danger`:
  - `Door: two-way | one-way` (whether the change is trivially reversible or alters persistent NVS/EEPROM/protocol schemas).
  - `Blast Radius: local | module | system` (scope of affected boards, protocols, or radio transports).

---

## Stage 4: Dual GitHub PR Review (Automated CI Gate + Agentic Spec/Code/Security Review)

Every Pull Request undergoes two complementary review tracks on GitHub:

### 4A. Automated 4-Gate GitHub Actions Workflow (`.github/workflows/autonomous-pr-review.yml`)

Triggered automatically on `pull_request` (`opened`, `synchronize`, `reopened`):

1. **Gate 1 — OPSEC & Zero-PII Scan**: Scans all changed files (`git diff --name-only origin/main...HEAD`) for leaked credentials, private keys, tokens (`ghp_`, `github_pat_`, `AKIA`), or local workstation user paths.
2. **Gate 2 — SSH Commit Signature & Author Verification**: Verifies that every commit in the PR range (`origin/main..HEAD`) carries a valid cryptographic SSH signature (`gpgsig`) and is authored by `203040288+TinkeringDao@users.noreply.github.com`.
3. **Gate 3 — 8-Pillar Legal, German Statutory Addendum, Governance & Inline Review Threads Integrity**: Verifies the presence and non-empty integrity of `LEGAL.md` (including `## Addendum: German Statutory References (Applicable to Residents of Germany)`), `LICENSE`, `SECURITY.md`, `CODE_OF_CONDUCT.md`, `.github/CODEOWNERS`, `AGENTS.md`, `CLAUDE.md`, and `docs/agents/autonomous-pipeline.md`, and queries `repository.pullRequest.reviewThreads(first: 100) { nodes { isResolved } }` via `gh api graphql` to ensure all inline review threads have `isResolved == true`.
4. **Gate 4 — Project Configuration & Build Manifest Verification**: Verifies `platformio.ini` presence and structural integrity.

### 4B. Independent Agentic Spec, Code & Security Review

An independent Reviewer Subagent (`superpowers:subagent-driven-development` + `code-review` + `security-review`) inspects `gh pr diff <PR_NUMBER>` against:
- Specification completeness and architectural consistency (`AGENTS.md`, `docs/agents/domain.md`),
- Hardware/RF/PMIC safety boundaries (`SX1262` / `LR1110` ERP & duty cycle, `AXP2101` / `BQ25896` charge limits),
- Legal & OPSEC compliance (`LEGAL.md`, `SECURITY.md`),
and posts a structured review on the Pull Request (`gh pr review <PR_NUMBER> --comment --body "..."`).

---

## Stage 5: Autonomous Remediation Loop

If either the Reviewer Subagent (Stage 4B), an inline review thread (`reviewThreads`), or the automated CI workflow (Stage 4A) identifies any gap, regression, or improvement item:

1. The implementation agent (`agy` / `gemini-4-argon-high`) addresses every finding on the PR branch and resolves any open inline review threads.
2. Changes are committed with an ED25519 SSH signature (`fix(...): address PR review ...`) and pushed to `origin`.
3. Pushing a new commit automatically dismisses prior approvals (`dismiss_stale_reviews_on_push: true`) and re-triggers `.github/workflows/autonomous-pr-review.yml` on the new `HEAD` SHA.
4. A structured remediation summary comment (`gh pr comment <PR_NUMBER> --body "## Autonomous Remediation Complete ..."`) is posted on the PR referencing the remediation commit SHA.

---

## Stage 6: Automated Approval, Squash Merge & Hindsight Retention

1. **Automated Bot Approval**:
   - Once all 4 CI gates succeed (including zero unresolved `reviewThreads`) on the latest commit and `HEAD_REPO == BASE_REPO && PR_AUTHOR == 'TinkeringDao'`, `.github/workflows/autonomous-pr-review.yml` executes `gh pr review "${PR_NUMBER}" --approve` as `github-actions[bot]`.
   - This satisfies the `Protect main branch` repository ruleset (`required_approving_review_count: 1`, `require_last_push_approval: true`, `required_signatures: true`).
2. **Squash Merge & Branch Cleanup**:
   - The approved PR is merged into `main` via:
     ```bash
     gh pr merge <PR_NUMBER> --squash --delete-branch
     ```
3. **Hindsight Knowledge Retention**:
   - Post-merge architectural decisions, resolved review findings, and commit SHAs are persisted to Hindsight via `${HINDSIGHT_URL}` (e.g. `http://127.0.0.1:9100`):
     ```bash
     export HINDSIGHT_URL="${HINDSIGHT_URL:-http://127.0.0.1:9100}"
     export HINDSIGHT_BANK="${HINDSIGHT_BANK:-default}"
     curl -s -X POST "${HINDSIGHT_URL}/v1/default/banks/${HINDSIGHT_BANK}/memories" \
       -H "Content-Type: application/json" \
       -d '{"items": [{"content": "Merged PR #<N> in TinkeringDao/meshcomod: <summary>"}]}'
     ```
