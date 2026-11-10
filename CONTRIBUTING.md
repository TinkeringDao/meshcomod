# Contributing to meshcomod

Contributions that improve reliability, test coverage, documentation, or hardware support are welcome. By participating in this repository, you agree to abide by [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) and the statutory interoperability, licensing, and regulatory terms documented in [`LEGAL.md`](LEGAL.md).

## Reporting Bugs & Security Issues

- Report security vulnerabilities privately via [`SECURITY.md`](SECURITY.md) rather than public issues.
- For general bug reports, include your target board, PlatformIO environment, firmware version, and steps to reproduce.

## Legal, Clean-Room Interoperability, & RF Regulatory Standards

All contributions must comply with [`LEGAL.md`](LEGAL.md) and [`LICENSE`](LICENSE):

- **MIT License**: All contributed source code is licensed under the [MIT License](LICENSE). Preserve all existing upstream copyright headers (`Scott Powell / Ripple Radios and MeshCore contributors`) and third-party license files (`arch/esp32/AsyncElegantOTA/LICENSE`, `arch/stm32/Adafruit_LittleFS_stm32/src/littlefs/LICENSE.md`).
- **Privacy & Credential Hygiene**: Never commit Wi-Fi SSIDs/passwords, private cryptographic keys, personal names, physical locations, GPS coordinates, or hardware serial numbers/MAC addresses.
- **No Proprietary Vendor Blobs**: Do not commit decompiled proprietary code, NDA-restricted SDK files, or third-party corporate logos/trademarks beyond factual hardware compatibility identifiers (indication of intended purpose and nominative fair use under `Article 14(1)(c) of Regulation (EU) 2017/1001 (EUTMR)` and `15 U.S.C. §§ 1115(b)(4), 1125`; see [`LEGAL.md`](LEGAL.md)).
- **RF & Hardware Safety**: Board variant additions (`variants/`) must accurately document external Power Amplifier (`PA` / `FEM`) gain pins and PMIC voltage rails (`AXP192`, `AXP2101`, `BQ25896`, `<= 4.20–4.288 V`, `0–45 °C` NTC guard) so operators maintain compliance with `Directive 2014/53/EU (RED)`, `ETSI EN 300 220-1/-2`, `ETSI EN 300 328`, `ERC/REC 70-03`, `Decision (EU) 2017/1483`, and `FCC 47 C.F.R. Part 15.247 / Part 97`.

## Local Build & Test Verification

Run native unit tests and a target firmware build locally before opening a pull request:

```bash
pio test -e native -e native_kiss_modem -vv
pio run -e Heltec_v3_companion_radio_usb_tcp
```

## Pull Request Workflow

1. Create a focused topic branch from `main` (`feat/...`, `fix/...`, `docs/...`, `chore/...`, `ci/...`) — one concern per pull request.
2. Keep commits atomic, use Conventional Commit headers (`feat:`, `fix:`, `docs:`, `ci:`, `refactor:`, `test:`), and sign all commits (`git config commit.gpgsign true`).
3. Update `README.md` and `library.json` when changing public APIs, and follow existing C++ formatting (`.clang-format`: 2-space indentation, `camelCase` functions/variables, `PascalCase` classes, `ALL_CAPS` macros).
4. Open a pull request against `main` summarizing the problem, root cause or design choice, and verification output. All pull requests squash-merge onto `main` once `ci` and `security` checks pass.
