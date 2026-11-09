# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

## Before exploring, read these

- **`GLOSSARY.md`** at the repo root, or
- **`GLOSSARY-MAP.md`** at the repo root if it exists: it points at one `GLOSSARY.md` per context. Read each one relevant to the topic.
- **`docs/adr/`**: read ADRs that touch the area you're about to work in. In multi-context repos, also check `src/<context>/docs/adr/` for context-scoped decisions.

If any of these files don't exist, **proceed silently**. Don't flag their absence; don't suggest creating them upfront.

## Core Domain Vocabulary (`meshcomod` / `MeshCore`)

- **Companion Radio (`examples/companion_radio/`)**: Multi-transport MeshCore node exposing USB serial, BLE (`6E400001-B5A3-F393-E0A9-E50E24DCCA9E`), TCP (`:5000`), and WebSocket (`:8765`) transports simultaneously.
- **Repeater TCP (`examples/simple_repeater/`)**: Store-and-forward LoRa mesh repeater with optional Wi-Fi TCP management and telemetry bridge (`rX.Y.Z.W-repeater-tcp`).
- **Room Server Multitransport (`examples/simple_room_server/`)**: Persistent bulletin/room node supporting multi-transport client connections (`rX.Y.Z.W-room-mt`).
- **Variant (`variants/`)**: Board-specific hardware pinout, SPI/I2C bus mapping, LoRa radio (`SX1262`, `LR1110`, `SX1276`), Front-End Module (`PA` / `LNA`), and PMIC (`AXP2101`, `AXP192`, `BQ25896`, `INA3221`) definitions.
