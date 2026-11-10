# Security Policy

## Supported Versions

Security fixes are applied to the latest release on the active `main` branch only.

| Version | Supported |
| :--- | :--- |
| `1.15+` / `1.16+` | Yes |
| `< 1.15` | No |

## Hardware, Network Transport, & RF Safety Boundaries

`meshcomod` is an independent, non-commercial open-source firmware distribution for select LoRa mesh microcontroller boards (see [`LEGAL.md`](LEGAL.md)):

- **Local Transport Security (`USB` / `BLE` / `TCP :5000` / `WS :8765`):**
  - When TCP (`port 5000`) or plain WebSocket (`ws://` on `port 8765`) is enabled over Wi-Fi, companion frames are transported in plaintext over the local network. Enable TCP/WebSocket only on trusted local networks or isolated VLANs, and never expose port `5000` or `8765` directly to the public internet without an authenticated VPN or TLS tunnel.
  - Wi-Fi credentials configured at runtime are stored in microcontroller Non-Volatile Storage (`NVS`). Erase flash (`pio run -t erase` or web flasher full erase) before transferring or disposing of hardware.
- **Radio Frequency (RF), High-Power PA & Duty-Cycle Compliance (`Directive 2014/53/EU (RED)` / `ETSI EN 300 220-1/-2` / `FCC 47 C.F.R. Part 15.247 / Part 97`):**
  - The hardware operator is solely and exclusively responsible for ensuring that configured carrier frequencies, bandwidths, duty cycles (`<= 1%` in `868.0–868.6 MHz` SRD Sub-band `g1` at `<= 25 mW` ERP; `<= 10%` in `869.400–869.650 MHz` SRD Sub-band `g3` at `<= 500 mW` ERP under `ETSI EN 300 220-1/-2` / `ERC/REC 70-03` / `Decision (EU) 2017/1483`), and external Power Amplifier (`PA` / `FEM`) gain settings comply with applicable national spectrum regulations (see [`LEGAL.md`](LEGAL.md)).
- **Battery, Solar PMIC & Antenna Load Safety:**
  - Never transmit without a properly rated `50 Ohm` antenna connected to the sub-GHz LoRa port. Verify exact board and PCB revision compatibility before flashing to prevent improper PMIC/battery charger register initialization.
- **Authorized Local Owner Execution Only (`18 U.S.C. § 1030 (CFAA)`):**
  - Flashing or reconfiguring devices is authorized strictly on hardware owned or lawfully controlled by the user.

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

Use GitHub's private vulnerability reporting via [GitHub Security Advisories](https://github.com/TinkeringDao/meshcomod/security/advisories/new):
1. Navigate to **`https://github.com/TinkeringDao/meshcomod/security/advisories/new`** (or go to the **Security** tab of this repository and click **Report a vulnerability**).
2. Provide details on the affected component/file, target board/architecture (`ESP32-S3`, `nRF52840`, `STM32`, `RP2040`), reproduction steps or proof-of-concept packet/frame, and impact assessment.

## Scope

### In Scope
- Remote code execution, buffer overflows, memory corruption, or denial-of-service via crafted LoRa radio packets or companion frames (`USB` / `BLE` / `TCP` / `WebSocket`)
- Authentication or cryptographic verification bypasses in mesh routing or companion pairing
- Unintended exposure of stored Wi-Fi/NVS credentials or private keys

### Out of Scope
- Physical hardware attacks requiring UART/JTAG/SWD access or chip decapping
- Operator misconfiguration of radio frequency, transmit power, or duty cycle (`see LEGAL.md`)
- Physical-layer RF jamming or denial-of-service inherent to shared unlicensed ISM/SRD spectrum
- Vulnerabilities in unmodified upstream dependencies (`RadioLib`, vendor SDKs) — please report those upstream as well
