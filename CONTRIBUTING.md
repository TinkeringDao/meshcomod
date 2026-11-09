# Contributing to meshcomod / MeshCore

Thanks for considering contributing to this project! By participating in this repository, you agree to abide by the [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) and the statutory interoperability, licensing, and regulatory terms documented in [`LEGAL.md`](LEGAL.md).

## How Can I Contribute?

### 1. Reporting Bugs
- Use the **Issues** tracker (for security vulnerabilities, see [`SECURITY.md`](SECURITY.md) and report privately via [GitHub Security Advisories](https://github.com/TinkeringDao/meshcomod/security/advisories/new))
- Use a clear title (e.g. "Crash when calling begin() with invalid pin")
- Describe the **exact steps** to reproduce
- Include your **board**, **IDE / PlatformIO version**, **library version**, and **relevant code snippet**
- Attach a minimal complete example sketch if possible

### 2. Suggesting Enhancements / New Features
- Open an issue with the prefix **[Feature request]**
- Explain the use-case -> what problem would this solve?
- Describe your ideal API / behavior (code examples are very helpful)

### 3. Submitting Code Changes (Pull Requests)

#### Small fixes (typos, comments, examples, small bug fixes)
-> Open a pull request directly — no prior issue needed.

#### Larger changes / new features
1. Open an issue first to discuss the idea
2. Get confirmation from maintainer(s)
3. Fork the repo and create your branch (`fix/xxx`, `feature/yyy`, `docs/whatever`)
4. Make your changes
5. Update or add examples when appropriate
6. Add/update comments in code
7. Submit the pull request

### Pull Request Guidelines

- **One feature / fix = one pull request** (smaller PRs are easier & faster to review)
- Use descriptive commit messages
  - Good: `Fix I2C timeout handling on ESP32`
  - Bad: `update`
- Reference any related issue (`Fixes #123`, `Closes #89`, etc.)
- If you change public API, update `README.md` and `library.json`
- New features should include an example sketch in `examples/`

## Legal, Clean-Room Interoperability, & RF Regulatory Standards

All contributions must comply with [`LEGAL.md`](LEGAL.md) and [`LICENSE`](LICENSE):

- **MIT License**: All contributed source code is licensed under the [MIT License](LICENSE). Preserve all existing upstream copyright headers (`Scott Powell / Ripple Radios and MeshCore contributors`) and third-party license files (`arch/esp32/AsyncElegantOTA/LICENSE`, `arch/stm32/Adafruit_LittleFS_stm32/src/littlefs/LICENSE.md`).
- **Privacy & Credential Hygiene**: Never commit Wi-Fi SSIDs/passwords, private cryptographic keys, personal GPS coordinates, or personal hardware serial numbers/MAC addresses.
- **No Proprietary Vendor Blobs**: Do not commit decompiled proprietary code, NDA-restricted SDK files, or third-party corporate logos/trademarks beyond factual hardware compatibility identifiers (indication of intended purpose and nominative fair use under `Article 14(1)(c) of Regulation (EU) 2017/1001 (EUTMR)` and `15 U.S.C. §§ 1115(b)(4), 1125`; see [`LEGAL.md`](LEGAL.md)).
- **RF & Hardware Safety**: Board variant additions (`variants/`) must accurately document external Power Amplifier (`PA` / `FEM`) gain pins and PMIC voltage rails so operators can maintain compliance with `Directive 2014/53/EU (RED)`, `ETSI EN 300 220-1/-2`, `ETSI EN 300 328`, `ERC/REC 70-03`, `Decision (EU) 2017/1483`, and `FCC 47 C.F.R. Part 15.247 / Part 97` (see [`LEGAL.md`](LEGAL.md)).

### Pre-Merge Verification & RF Safety Gate Checklist

| Gate | Requirement | Verification Standard |
|---|---|---|
| **1. OPSEC & Zero-PII** | Zero personal identifiers, local paths, Wi-Fi credentials, or tokens in diff | Automated Gate 1 in `.github/workflows/autonomous-pr-review.yml` |
| **2. Signed Commits** | All commits authored by `TinkeringDao <203040288+TinkeringDao@users.noreply.github.com>` with ED25519 SSH signature (`-S -s`) | Automated Gate 2 (`gpgsig` verification) |
| **3. RF ERP & Duty Cycle** | `SX1262` / `LR1110` / `SX1276` & external PA/FEM configs respect `<= 1%` (`g1`) / `<= 10%` (`g3`) duty cycle & ERP limits (`ETSI EN 300 220-1/-2`, `Directive 2014/53/EU`, `FCC Part 15.247`) | Variant & radio preset audit (`variants/`, `LEGAL.md`) |
| **4. PMIC & Battery Safety** | `AXP2101` / `AXP192` / `BQ25896` charge termination `<= 4.20–4.288 V` and `0–45 °C` NTC thermal protection preserved | Driver & board variant review (`variants/`) |
| **5. Clean-Room & Legal** | `MIT` headers intact; `LEGAL.md` retains `Addendum: German Statutory References` | Automated Gate 3 & Stage 4B Agentic Review |

## Coding Style

Please follow the existing C++ style (per `.clang-format`):

- 2 spaces indentation (no tabs)
- `camelCase` for functions and variables
- `UpperCamelCase` / `PascalCase` for class names
- `#define` constants in `ALL_CAPS`
- Keep lines < ~100 characters when reasonable

(Consistency with existing code is more important than strict rules.)
