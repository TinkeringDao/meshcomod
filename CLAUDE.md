# CLAUDE.md — Project Instructions for Claude & Autonomous Agents (`meshcomod`)

Always read and follow these canonical specifications before exploring or modifying this repository:

1. **[`AGENTS.md`](AGENTS.md)** — Master agent engineering & release playbook, target board/variant matrix (`Heltec V4`, `Heltec V4 TFT`, `Heltec V3`, `Heltec Wireless Paper`, `Xiao S3 WIO`, `ThinkNode M9`, `LilyGo T-Deck`, `Tanmatsu`), PlatformIO & `build.sh` commands, and RF/PMIC safety invariants.
2. **[`docs/agents/autonomous-pipeline.md`](docs/agents/autonomous-pipeline.md)** — Full 6-Stage Autonomous Development, Dual GitHub PR Review, Remediation, and Automated Merge Pipeline specification, enforced by [`.github/workflows/autonomous-pr-review.yml`](.github/workflows/autonomous-pr-review.yml).
3. **[`LEGAL.md`](LEGAL.md)** — 8-pillar legal framework (EU CRA `Regulation (EU) 2024/2847` & PLD `Directive (EU) 2024/2853` non-commercial FOSS exemption, clean-room interoperability, nominative fair use, `Directive 2014/53/EU (RED)` / `ETSI EN 300 220` / `FCC Part 15.247` RF compliance, `AXP2101` / `BQ25896` battery safety, and the mandatory `## Addendum: German Statutory References (Applicable to Residents of Germany)`).
4. **[`SECURITY.md`](SECURITY.md)** & **[`docs/agents/domain.md`](docs/agents/domain.md)** — Vulnerability reporting, OPSEC/Zero-PII rules, and domain modeling conventions.
