# Legal, Trademark, Interoperability, & RF Regulatory Notice

## 1. Independent Open-Source Project & Trademark Nominative Fair Use

**`meshcomod` — Unofficial Multi-Transport Companion Firmware & Utilities for Select LoRa Mesh Hardware** is an **independent, non-commercial, community-maintained free and open-source software (FOSS) fork and extension** of the open-source [MeshCore](https://github.com/meshcore-dev/MeshCore) project.

- **No Affiliation or Endorsement:** This project is **not affiliated with, authorized by, sponsored by, or endorsed by Ripple Radios / MeshCore (`rippleradios.com`), Heltec Automation (`Chengdu Heltec Automation Technology Co., Ltd.`), LilyGo (`Shenzhen Xin Yuan Electronic Technology Co., Ltd.`), Seeed Studio (`Seeed Technology Co., Ltd.` / `SenseCAP`), RAKwireless (`RAKwireless Technology Co., Ltd.` / `WisBlock`), Elecrow (`Elecrow Technology Co., Ltd.` / `ThinkNode`), B&Q Consulting (`Station G2`), Semtech Corporation (`LoRa`, `SX1262`, `SX1276`), Espressif Systems (`ESP32`, `ESP32-S3`, `ESP32-C3`), Nordic Semiconductor ASA (`nRF52840`), or STMicroelectronics (`STM32`).**
- **Indication of Intended Purpose & Nominative Fair Use:**
  - Pursuant to **Article 14(1)(c) of Regulation (EU) 2017/1001 (EUTMR)**, settled jurisprudence of the Court of Justice of the European Union (*Case C-228/03 — Gillette Company v. LA-Laboratories Ltd Oy*; *Case C-63/97 — Bayerische Motoren Werke AG (BMW) v. Ronald Karel Deenik*), and **US Nominative Fair Use (`15 U.S.C. §§ 1115(b)(4), 1125`**, *New Kids on the Block v. News America Publishing, Inc.*, 971 F.2d 302 (9th Cir. 1992)), all third-party brand names, product designations, and silicon part numbers are referenced strictly as a necessary indication of intended purpose, nominative fair use, and target hardware compatibility of this firmware:
    - "MeshCore" and "Ripple Radios" are trademarks or designations of **Scott Powell / Ripple Radios**.
    - "Heltec", "WiFi LoRa 32", "Wireless Paper", "Wireless Tracker", and "MeshNode" are trademarks or product designations of **Chengdu Heltec Automation Technology Co., Ltd.**
    - "LilyGo", "T-Deck", "T-Beam", "T-Echo", and "T-LoRa" are trademarks or product designations of **Shenzhen Xin Yuan Electronic Technology Co., Ltd.**
    - "Seeed Studio", "XIAO", "Wio", and "SenseCAP" are trademarks or registered trademarks of **Seeed Technology Co., Ltd.**
    - "RAK", "RAKwireless", and "WisBlock" are trademarks or registered trademarks of **RAKwireless Technology Co., Ltd.**
    - "Elecrow" and "ThinkNode" are trademarks or product designations of **Elecrow Technology Co., Ltd.**
    - "Station G2" is a product designation of **B&Q Consulting**.
    - "Semtech", "LoRa", "LoRaWAN", "SX1262", and "SX1276" are registered trademarks or trademarks of **Semtech Corporation**.
    - "Espressif" and "ESP32" are registered trademarks of **Espressif Systems (Shanghai) Co., Ltd.**
    - "Nordic Semiconductor" and "nRF52840" are trademarks or registered trademarks of **Nordic Semiconductor ASA**.
    - "STM32" and "STMicroelectronics" are registered trademarks of **STMicroelectronics International N.V.**

---

## 2. Open-Source License Provenance, Statutory Interoperability & Trade Secret Safe Harbor

### 2.1 Open-Source License Provenance
- **MIT License Core:** This repository derives from upstream [MeshCore](https://github.com/meshcore-dev/MeshCore) (`Copyright (c) 2024-2026 Scott Powell / Ripple Radios and MeshCore contributors`) with modifications and multi-transport companion extensions (`Copyright (c) 2026 TinkeringDao`), distributed under the [MIT License](LICENSE) (see also [`license.txt`](license.txt)).
- **Third-Party Open-Source Components:** All bundled third-party libraries retain their upstream permissive licenses and copyright notices in full, including `AsyncElegantOTA` (`arch/esp32/AsyncElegantOTA/LICENSE`, MIT License, `Copyright (c) 2019 Ayush Sharma`) and `littlefs` (`arch/stm32/Adafruit_LittleFS_stm32/src/littlefs/LICENSE.md`, BSD 3-Clause License, `Copyright (c) 2017, Arm Limited`).

### 2.2 European Union (`Directive 2009/24/EC (Articles 1(2), 5(3), 6, 8)` & `Article 3(1)(b) of Directive (EU) 2016/943`)
1. **Exclusion of Functional Protocols, Pinouts & Interfaces from Copyright (`Directive 2009/24/EC Article 1(2)`):**
   - Under **Article 1(2) of Directive 2009/24/EC** and settled Court of Justice of the European Union precedent (*SAS Institute Inc. v. World Programming Ltd*, Case `C-406/10`, paras. 39–46), ideas, principles, hardware GPIO pin mappings, SPI/I2C register definitions, packet framing, and serial/TCP/BLE companion protocols are **excluded from copyright protection**.
2. **Right to Observe, Study, and Test (`Directive 2009/24/EC Article 5(3)`):**
   - Authorizes the lawful owner or user of hardware and software to observe, study, and test its functioning without prior authorization in order to determine the underlying ideas, principles, and hardware interfaces.
3. **Mandatory Right of Interoperability (`Directive 2009/24/EC Article 6`):**
   - Permits independent analysis necessary to achieve the **interoperability** of an independently created or modified computer program (`meshcomod`) with open-market microcontroller boards, peripherals, and companion clients (USB serial, Bluetooth Low Energy GATT, TCP port `5000`, WebSocket port `8765`, and Home Assistant integrations).
4. **Statutory Nullity of Contrary Contractual Restrictions (`Directive 2009/24/EC Article 8`):**
   - Under **Article 8 of Directive 2009/24/EC**, any contractual or EULA provisions purporting to restrict or waive rights under Articles 5(3) or 6 are **statutorily null and void**.
5. **Lawful Hardware Reverse Engineering & Trade Secret Safe Harbor (`Article 3(1)(b) of Directive (EU) 2016/943`):**
   - Under **Article 3(1)(b) of Directive (EU) 2016/943**, obtaining technical information by observing, examining, disassembling, or testing a product that has been made publicly available or is in the lawful possession of the observer free from any valid duty to limit acquisition is explicitly lawful.

### 2.3 United States (`17 U.S.C. §§ 102(b), 107, 1201(f)`, `18 U.S.C. § 1839(6)(B)`)
1. **Uncopyrightable Systems, Methods of Operation & Merger (`17 U.S.C. § 102(b)`):**
   - Hardware pin assignments, radio register configurations, and wire-level framing specifications constitute uncopyrightable methods of operation and functional facts necessary for hardware/software compatibility (*Baker v. Selden*, 101 U.S. 99 (1879); *Google LLC v. Oracle America, Inc.*, 593 U.S. 1 (2021); *Lexmark Int'l, Inc. v. Static Control Components, Inc.*, 387 F.3d 522 (6th Cir. 2004)).
2. **Fair Use & Interoperability Exemptions (`17 U.S.C. § 107` & `17 U.S.C. § 1201(f)`):**
   - Firmware adaptation and protocol compatibility with lawfully acquired microcontroller boards and companion clients fall squarely within statutory interoperability exemptions and transformative fair use (*Sega Enterprises Ltd. v. Accolade, Inc.*, 977 F.2d 1510 (9th Cir. 1992); *Sony Computer Entertainment, Inc. v. Connectix Corp.*, 203 F.3d 596 (9th Cir. 2000)).
3. **Defend Trade Secrets Act Reverse-Engineering Safe Harbor (`18 U.S.C. § 1839(6)(B)`):**
   - Under the federal Defend Trade Secrets Act (DTSA), reverse engineering, independent derivation, and clean-room analysis of lawfully acquired hardware on the open market are expressly excluded from "improper means".

---

## 3. Non-Circumvention of Technological Protection Measures (`Directive 2009/24/EC` & `17 U.S.C. §§ 1201(a), 1201(f)`)

Under **Directive 2009/24/EC (Articles 1(2), 5(3), 6, 8)** and **US `17 U.S.C. §§ 102(b), 107, 1201(a), 1201(f)`**, `meshcomod` **circumvents zero Technological Protection Measures (TPMs)**:

- **Open Microcontroller Development Platforms:** All supported boards (`ESP32-S3`, `ESP32-C3`, `ESP32`, `nRF52840`, `STM32`, `RP2040`) are general-purpose developer and maker hardware platforms specifically marketed and designed by their manufacturers to be flashed with custom user firmware via documented, unencrypted factory bootloaders (`esptool` UART/USB-CDC ROM bootloader, Adafruit/Nordic UF2 mass-storage bootloader, `nrfutil` DFU, or STM32 DFU/SWD).
- **Zero Secure-Boot Bypass or Key Extraction:** This repository contains zero exploit payloads, eFuse/OTP fault-injection routines, cryptographic key extractors, or mechanisms to defeat hardware secure boot or flash encryption.

---

## 4. Authorized Local Owner Execution Only & US CFAA (`18 U.S.C. § 1030`)

In accordance with **Authorized Local Owner Execution Only** principles and the US Computer Fraud and Abuse Act (`18 U.S.C. § 1030 (CFAA)`, *Van Buren v. United States*, 593 U.S. 374 (2021)):

- **Authorized Local Owner Execution Only:** This firmware and its associated flashing scripts are intended exclusively for installation and execution on microcontroller hardware owned or explicitly authorized by the operator. Flashing, reconfiguring, or accessing third-party radio nodes without the explicit consent of the hardware owner is strictly prohibited.
- **No Access-Security Circumvention:** Optional local network transports (BLE pairing PIN, local Wi-Fi station connection, TCP port `5000`, WebSocket port `8765`) operate strictly on the hardware owner's local area network and personal devices.

---

## 5. Non-Commercial Open-Source Software Exemption (EU CRA `Regulation (EU) 2024/2847` & EU PLD `Directive (EU) 2024/2853`)

- **EU Cyber Resilience Act Exemption (`Regulation (EU) 2024/2847`, Recitals 15 & 18; `Art. 2(5)`; `Art. 3(13)-(14)`):** This repository and any prebuilt firmware binaries published in GitHub Releases are developed, maintained, and supplied strictly as **non-commercial free and open-source software outside the course of any commercial activity**. No fee is charged, no paid support or commercial services are offered, and no personal data is collected or monetized. Accordingly, the authors and contributors are neither "manufacturers" (`Art. 3(13)`) nor "open-source software stewards" (`Art. 3(14)`), and CE-marking (`Art. 28 CRA`), conformity assessments, and commercial manufacturer obligations under Regulation (EU) 2024/2847 do not apply.
- **EU Product Liability Directive Exemption (`Directive (EU) 2024/2853`, `Art. 2(2)` & Recitals 14, 15, 24):** Pursuant to **Article 2(2)** and **Recitals 14, 15, and 24 of Directive (EU) 2024/2853**, strict product liability under this Directive does not apply to free and open-source software developed or supplied outside the course of a commercial activity. Any natural or legal person who subsequently integrates, bundles, flashes onto hardware for resale, or redistributes this software in the course of a commercial activity assumes sole legal and regulatory responsibility as a manufacturer.

---

## 6. Radio Frequency (RF), High-Power PA Warning, Duty Cycle & Telecom Regulatory Compliance (`Directive 2014/53/EU (RED)`, `ETSI EN 300 220-1/-2`, `ETSI EN 300 328`, `ERC/REC 70-03`, `Decision (EU) 2017/1483`, `FCC 47 C.F.R. Part 15.247 / Part 97`)

`meshcomod` is general-purpose firmware capable of driving sub-GHz LoRa transceivers (**Semtech `SX1262`, `SX1268`, `SX1276`, `SX1278`, `LR1121`**) and `2.4 GHz` Bluetooth Low Energy / Wi-Fi transceivers across multiple international hardware variants, including devices equipped with **external RF Front-End Modules (FEMs) and high-power Power Amplifiers (PAs)** (such as the **Heltec WiFi LoRa 32 V4**, **B&Q Consulting Station G2**, **Seeed SenseCAP Solar**, and amplified repeater boards).

> [!CAUTION]
> **SOLE OPERATOR RESPONSIBILITY FOR RF COMPLIANCE:** Flashing firmware onto a radio transceiver module does not grant regulatory authorization to transmit. The **physical hardware operator is solely and exclusively responsible** for verifying and configuring legal carrier frequencies, bandwidths, duty-cycle ceilings, and maximum Effective Radiated Power (`ERP` / `EIRP`) before connecting an antenna or enabling transmissions.

### 6.1 European Union (`Directive 2014/53/EU (RED)`, `ETSI EN 300 220-1/-2`, `ETSI EN 300 328`, `ERC/REC 70-03`, `Decision (EU) 2017/1483`)
1. **License-Exempt Short Range Devices (SRD) in the `863–870 MHz` Band (`Decision (EU) 2017/1483` / `ERC/REC 70-03` / `ETSI EN 300 220-1/-2`):**
   - **SRD Sub-band `g1` (`868.000–868.600 MHz`):** Maximum **`25 mW` ERP (`+14 dBm`)** and strict **`<= 1%` duty cycle** (or compliant Polite Spectrum Access / LBT+AFA).
   - **SRD Sub-band `g3` (`869.400–869.650 MHz`):** Maximum **`500 mW` ERP (`+27 dBm`)** and strict **`<= 10%` duty cycle** (channel bandwidth `<= 250 kHz`).
2. **External Power Amplifier (PA) & Antenna Gain Calculation:**
   - Boards incorporating an external PA/FEM (e.g., Heltec V4, Station G2) can amplify the `SX1262` baseband output well beyond `+14 dBm` (often up to `+27 dBm`–`+30 dBm` / `0.5 W`–`1 W` conducted power). Operators **must** account for total system gain (`Transceiver TX Power + External PA Gain - Cable Insertion Loss + Antenna Gain in dBi/dBd`) to ensure radiated `ERP`/`EIRP` never exceeds the statutory ceiling for the selected sub-band.
3. **`2.4 GHz` BLE & Wi-Fi (`ETSI EN 300 328`):**
   - `2.4 GHz` Wi-Fi and BLE operation must remain within `2400–2483.5 MHz` and `<= 100 mW` (`+20 dBm`) EIRP (`<= 10 mW/MHz` spectral density).

### 6.2 United States (`FCC 47 C.F.R. Part 15.247 / Part 97`) & Other Jurisdictions
- **US ISM Band (`902–928 MHz`, `47 C.F.R. § 15.247`):** Unlicensed operation under FCC Part 15 Subpart C requires compliance with digital modulation, frequency-hopping, spectral density, and maximum conducted output power (`<= 1 W` / `+30 dBm` conducted with `<= 6 dBi` antenna gain, or `+36 dBm` EIRP) rules.
- **Amateur Radio Service (`ITU Radio Regulations` & `FCC 47 C.F.R. Part 97`):**
  - Operating on allocated Amateur Radio frequencies or at power/duty-cycle levels restricted to licensed radio amateurs requires a valid Amateur Radio Operator License.
  - **Prohibition on Cryptographic Encryption on Amateur Bands:** Under **ITU Radio Regulations `Art. 25.2A`** and **`47 C.F.R. § 97.113(a)(4)`** (United States), transmitting encrypted messages or messages obscured to conceal their meaning on amateur radio frequencies is **strictly prohibited**. Because MeshCore utilizes public-key and symmetric cryptographic encryption by default, standard encrypted MeshCore traffic **must not** be transmitted under Amateur Radio privileges and must instead strictly obey license-exempt SRD/ISM power and duty-cycle limits.

---

## 7. AS IS Warranty Disclaimer, Battery, Solar PMIC & Hardware Risk Disclaimer

THE SOFTWARE, PREBUILT FIRMWARE BINARIES, AND DOCUMENTATION ARE PROVIDED **"AS IS"**, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT (SEE [`LICENSE`](LICENSE)).

- **AS IS Warranty Disclaimer & Limitation of Liability:** To the fullest extent permitted by applicable law, the authors and contributors provide this open-source software free of charge on an **"AS IS"** basis and shall not be liable for any direct, indirect, incidental, or consequential damages arising from flashing, configuring, or operating this firmware.
- **Lithium Battery (`LiPo` / `Li-Ion` / `LiFePO4`), Solar MPPT & PMIC Safety:** Custom firmware configurations interact with onboard Power Management ICs (`AXP192`, `AXP2101`, `BQ25896`, `INA3221`), ADC voltage dividers, solar charge controllers, and GPIO load switches. Improper board selection (flashing a binary compiled for a different PCB revision), damaged battery cells, or unattended solar charging in extreme temperatures can cause over-voltage, over-discharge, thermal runaway, or fire. Always verify exact board and PCB revision compatibility before flashing, never operate radio transceivers without a properly matched `50 Ohm` antenna load connected to the LoRa port, and always use hardware-protected battery cells.

---

## Addendum: German Statutory References (Applicable to Residents of Germany)

For contributors, maintainers, and operators residing in Germany, the English legal provisions above correspond directly to the following national statutory provisions under German law:

1. **Trademark Indication of Intended Purpose (`§ 23 Abs. 1 Nr. 3 MarkenG` & BGH `I ZR 6/10`):**
   - Section 23(1) No. 3 of the German Trademark Act (*Markengesetz* — `§ 23 Abs. 1 Nr. 3 MarkenG`, *Bestimmungsangabe*) and settled German Federal Court of Justice jurisprudence (BGH `I ZR 6/10`) authorize the descriptive use of third-party trademarks and hardware designations where necessary to indicate the intended purpose or compatibility of software and accessories.
2. **Software Copyright, Observation & Interoperability (`§§ 69a Abs. 2 & 5, 69d Abs. 3, 69e, 69f Abs. 2, 69g Abs. 2, 95a UrhG`):**
   - **Exclusion of Ideas & Interfaces (`§ 69a Abs. 2 S. 2 UrhG`):** Ideas and principles underlying computer program elements, including functional interfaces, hardware register maps, and protocols, are not protected by copyright.
   - **Observation & Testing (`§ 69d Abs. 3 UrhG`) and Interoperability (`§ 69e UrhG`):** Authorize lawful users to observe, study, and test program functioning and to perform analysis required to achieve interoperability of an independently created program.
   - **Mandatory Nature (`§ 69g Abs. 2 UrhG`):** Contractual provisions contrary to `§ 69d Abs. 2, 3` or `§ 69e UrhG` are statutorily null and void (*nichtig*).
   - **Computer Program TPM *Lex Specialis* (`§ 69a Abs. 5`, `§ 69f Abs. 2`, `§ 95a UrhG`):** Under `§ 69a Abs. 5 UrhG`, the general anti-circumvention provisions of `§§ 95a–95d UrhG` do not apply to computer programs, which are governed exclusively by `§ 69f Abs. 2 UrhG`; `meshcomod` targets open developer bootloaders and circumvents zero protection measures.
3. **Trade Secret Reverse-Engineering Safe Harbor (`§ 3 Abs. 1 Nr. 2 lit. a & b GeschGehG`):**
   - Section 3(1) No. 2 of the German Trade Secrets Act (*Geschäftsgeheimnisgesetz* — `§ 3 Abs. 1 Nr. 2 lit. a & b GeschGehG`) explicitly permits acquiring technical information by observing, examining, disassembling, or testing a publicly available product (`lit. a`) or a product in the lawful possession of the observer free from any valid duty to limit acquisition (`lit. b`).
4. **German IT Criminal Law & Hardware Owner Authority (`§§ 202a–202c, 303a StGB` & `§ 903 BGB`):**
   - In accordance with German Federal Constitutional Court jurisprudence (*BVerfG, 2 BvR 2233/07*) and property owner authority under `§ 903 BGB` (*Befugnisse des Eigentümers*), flashing and configuring firmware on one's own microcontroller hardware (*eigene Daten*, `§ 303a StGB`) is fully authorized and does not circumvent any third-party access security barrier (*Zugangssicherung*, `§§ 202a–202c StGB`).
5. **Statutory Gratuity Liability Privilege (`§§ 521, 523, 524, 599, 600 BGB`):**
   - For gratuitous, non-commercial open-source software provision (*unentgeltliche Überlassung*), liability under the German Civil Code (*Bürgerliches Gesetzbuch* — `§§ 521, 523, 524, 599, 600 BGB`) is limited to intent (*Vorsatz*) and gross negligence (*grobe Fahrlässigkeit*), with no warranty for material or legal defects (*Sach- oder Rechtsmängel*).
6. **German Radio Equipment & Spectrum Regulations (`FuAG`, `TKG`, `BNetzA Vfg 99/2022` / `Vfg 34/2020`, `AFuG` / `AFuV`):**
   - Radio operation in Germany is governed by the Radio Equipment Act (*Funkanlagengesetz* — `FuAG`), the Telecommunications Act (*Telekommunikationsgesetz* — `TKG`), the Federal Network Agency general spectrum allocations for Short Range Devices (*Allgemeinzuteilungen der Bundesnetzagentur* — `BNetzA Vfg 99/2022` / `Vfg 34/2020`), and—where operating on amateur bands—the Amateur Radio Act and Ordinance (`AFuG` / `§ 16 Abs. 1 Nr. 4 AFuV`, which prohibits encrypted transmissions on amateur radio frequencies).
