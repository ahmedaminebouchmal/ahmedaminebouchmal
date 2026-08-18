<div align="center">

# BOUCHMAL

### Embedded & Systems Engineer

*Hardware, protocols, and the software that proves they work.*

<br>

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)

![KiCad](https://img.shields.io/badge/KiCad-314CB0?style=for-the-badge&logo=kicad&logoColor=white)
![Zephyr](https://img.shields.io/badge/Zephyr-000000?style=for-the-badge&logo=zephyrproject&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white)
![Linux](https://img.shields.io/badge/Embedded_Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

</div>

---

## The stack I actually work across

```
   ┌─────────────────────────────────────────────────────────────────────┐
   │  RF / SDR      NFC / RFID      CAN · CAN-FD · LIN · K-Line          │
   │       │             │                      │                        │
   │       └─────────────┴──────────┬───────────┘                        │
   │                                ▼                                    │
   │                    ┌───────────────────────┐                        │
   │                    │   SCHEMATIC → PCB     │   KiCad, DFM review,   │
   │                    │      → BRING-UP       │   scope + logic probe  │
   │                    └───────────┬───────────┘                        │
   │                                ▼                                    │
   │                    ┌───────────────────────┐                        │
   │                    │       FIRMWARE        │   Zephyr, FreeRTOS,    │
   │                    │                       │   BLE/GATT, OTA        │
   │                    └───────────┬───────────┘                        │
   │                                ▼                                    │
   │                    ┌───────────────────────┐                        │
   │                    │   PROTOCOL / BACKEND  │   OCPP, telemetry,     │
   │                    │                       │   fault reproduction   │
   │                    └───────────┬───────────┘                        │
   │                                ▼                                    │
   │                         E V I D E N C E                             │
   │            traces · timestamps · exact versions · replay            │
   └─────────────────────────────────────────────────────────────────────┘
```

Most of my work sits where a bug is **physical**: a charge session that won't start, a
board that fails bring-up, a frame that arrives 3 ms late, a fault that only appears on one
firmware revision. Software people call it flaky. It usually isn't — it's just not
reproduced yet.

---

<table>
<tr>
<td width="50%" valign="top">

### 🔌 Hardware
Schematic capture and PCB layout in KiCad · DFM review · board bring-up and bench
validation · custom interface and adapter boards · logic-analyser and oscilloscope
debugging

</td>
<td width="50%" valign="top">

### ⚙️ Embedded
ESP32 · STM32 · nRF · Zephyr and FreeRTOS · BLE/GATT · OTA update paths · embedded Linux,
device tree, Yocto · low-power and timing-sensitive work

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🚗 Buses & protocols
CAN and CAN-FD · LIN · K-Line · Automotive Ethernet · OCPP and EVSE/CSMS behaviour ·
protocol analysis, fault reproduction, release regression evidence

</td>
<td width="50%" valign="top">

### 🛡️ Security & RF
WLAN and SDR · spectrum work · NFC/RFID and contact interfaces · bus- and interface-level
testing · provenance, chain-of-custody and evidence trails

</td>
</tr>
</table>

---

## Automation, where it earns its place

I build tooling around the hardware work rather than instead of it — deterministic test
harnesses, replayable capture pipelines, release-regression checks that diff behaviour
between firmware revisions, and evidence packages a reviewer can actually verify.

The rule I hold to: **anything that decides something must be reproducible and inspectable.**
A pipeline that produces a verdict nobody can re-derive is worse than no pipeline.

---

## Public contributions

<table>
<tr>
<td width="130" align="center" valign="middle">

**57k ★**

`scrapy/scrapy`

</td>
<td valign="top">

### [Refresh cached response headers on RFC 2616 revalidation &nbsp;·&nbsp; #8013](https://github.com/scrapy/scrapy/pull/8013)

Cached responses never refreshed their lifetime after a successful HTTP `304`, so every
later request re-validated needlessly — the cache was doing the work without giving the
benefit. Root-caused in the RFC 2616 cache policy, fixed, and covered by a regression test
that fails on the old behaviour.

</td>
</tr>
</table>

---

## How I work

|  |  |
|---|---|
| **Reproduce before fixing** | A failure I can't trigger on demand isn't diagnosed yet — it's a guess with a stack trace. |
| **Evidence over claims** | Timestamps, traces, exact versions, measured before and after. |
| **Smallest change that solves it** | No rewrite sold as a fix. |
| **Deterministic where it counts** | Hardware and protocol work is unforgiving of *usually*. |
