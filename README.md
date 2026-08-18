<div align="center">

# BOUCHMAL

**Embedded & Systems Engineer**

*Hardware, protocols, and the software that proves they work.*

<br>

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)

![KiCad](https://img.shields.io/badge/KiCad-314CB0?style=for-the-badge&logo=kicad&logoColor=white)
![Zephyr](https://img.shields.io/badge/Zephyr_RTOS-000000?style=for-the-badge&logo=zephyrproject&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white)
![Linux](https://img.shields.io/badge/Embedded_Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

</div>

---

## Where I work

```
     RF / SDR ──┐
    NFC / RFID ──┤
   CAN / CAN-FD ──┼──▶  [ board ]  ──▶  [ firmware ]  ──▶  [ backend ]  ──▶  evidence
    LIN / K-Line ──┤         │                │                  │              │
  Automotive Eth ──┘      schematic         Zephyr            OCPP /         traces,
                           PCB              FreeRTOS          telemetry      timestamps,
                           bring-up         BLE / OTA                        reproducible
                                                                             failures
```

Most of my work is where a bug is **physical** — a charger that won't start a session, a
board that fails bring-up, a CAN frame that arrives 3 ms late, a session that dies only on
one firmware revision.

<table>
<tr>
<td width="50%" valign="top">

### Hardware
- Schematic capture & PCB layout (KiCad)
- DFM review, bring-up, bench validation
- Logic analyser / oscilloscope debugging
- Custom interface boards

</td>
<td width="50%" valign="top">

### Embedded
- ESP32 · STM32 · nRF
- Zephyr · FreeRTOS
- BLE / GATT, OTA update paths
- Embedded Linux, device tree

</td>
</tr>
<tr>
<td width="50%" valign="top">

### Buses & protocols
- CAN / CAN-FD, LIN, K-Line
- Automotive Ethernet
- OCPP, EVSE / CSMS behaviour
- Protocol analysis & fault reproduction

</td>
<td width="50%" valign="top">

### Security & RF
- WLAN / SDR, spectrum work
- NFC / RFID, contact interfaces
- Bus- and interface-level testing
- Provenance and evidence trails

</td>
</tr>
</table>

---

## Selected public work

<table>
<tr>
<td width="120" align="center" valign="middle">

**57k★**<br>
`scrapy`

</td>
<td valign="top">

### [scrapy/scrapy#8013](https://github.com/scrapy/scrapy/pull/8013)
Cached responses never refreshed their lifetime after a successful HTTP `304`
revalidation — so every later request re-validated needlessly. Root-caused in the
RFC 2616 cache policy, fixed, and covered by a regression test that fails on the old
behaviour.

</td>
</tr>
<tr>
<td width="120" align="center" valign="middle">

**case<br>study**

</td>
<td valign="top">

### [production-rescue-demo](https://github.com/ahmedaminebouchmal/production-rescue-demo)
An inherited codebase taken from broken to production-ready: SQL built by string
concatenation, no validation, unhandled rejections, zero tests → written audit, focused
commits, 25 tests, CI. **The commit history is the case study** — before-state, audit, and
each fix are separate, readable commits.

</td>
</tr>
</table>

---

## How I work

> **Reproduce before fixing.** A failure I can't trigger on demand isn't diagnosed yet.

> **Evidence over claims.** Timestamps, traces, exact versions, measured before and after.

> **Smallest change that solves it.** No rewrite sold as a fix.

> **Deterministic where it counts.** Hardware and protocol work is unforgiving of *usually*.
