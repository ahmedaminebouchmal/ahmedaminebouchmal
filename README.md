# Ahmed Amine Bouchmal

**Embedded & systems engineer — hardware, protocols, and the software that proves they work.**

I work across the whole stack of a connected product: schematic and PCB, firmware, the
bus it speaks on, and the backend it reports to. Most of my work is in places where a bug
is physical — a charger that won't start a session, a board that fails bring-up, a CAN
frame that arrives 3 ms late.

---

### Domains

| | |
|---|---|
| **Hardware / PCB** | Schematic capture, PCB layout, KiCad, DFM review, bring-up and bench validation |
| **Embedded** | Firmware on ESP32 / STM32 / nRF, FreeRTOS & Zephyr, BLE/GATT, OTA, embedded Linux |
| **Vehicle & industrial buses** | CAN / CAN-FD, LIN, K-Line, Automotive Ethernet, protocol analysis and fault reproduction |
| **RF & identity** | WLAN/SDR, spectrum work, NFC/RFID and contact interfaces |
| **EV charging** | OCPP, EVSE/CSMS behaviour, release regression and pre-certification evidence |
| **Systems software** | Rust · Python · TypeScript · Kotlin · Java |

---

### Selected public work

**[scrapy/scrapy#8013](https://github.com/scrapy/scrapy/pull/8013)** —
Upstream fix to [Scrapy](https://github.com/scrapy/scrapy) (57k★). Cached responses never
refreshed their lifetime after a successful HTTP 304 revalidation, so every later request
re-validated needlessly. Root-caused in the RFC2616 cache policy, fixed, and covered by a
regression test that fails on the old behaviour.

**[production-rescue-demo](https://github.com/ahmedaminebouchmal/production-rescue-demo)** —
A worked rescue of an inherited codebase, end to end: SQL built by string concatenation,
no validation, unhandled rejections, zero tests → written audit, focused commits, 25 tests,
CI. The commit history *is* the case study; before-state, audit, and each fix are separate
commits you can read.

---

### How I work

- **Reproduce before fixing.** A failure I can't trigger on demand isn't diagnosed yet.
- **Evidence over claims.** Timestamps, traces, exact versions, measured before/after.
- **Smallest change that solves it.** No rewrite sold as a fix.
- **Deterministic where it counts.** Hardware and protocol work is unforgiving of "usually."

---

**Toolchain:** KiCad · oscilloscope/logic analyser bring-up · Zephyr/FreeRTOS ·
Rust · Python · TypeScript · PostgreSQL · Docker · GitHub Actions

📍 Germany · Open to remote contract work
