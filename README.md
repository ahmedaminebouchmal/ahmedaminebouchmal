<div align="center">

<img src="./stack.svg" alt="Multi-domain instrument platform architecture" width="100%">

<br>

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)

![KiCad](https://img.shields.io/badge/KiCad-314CB0?style=for-the-badge&logo=kicad&logoColor=white)
![FPGA](https://img.shields.io/badge/FPGA-0091BD?style=for-the-badge&logo=xilinx&logoColor=white)
![Zephyr](https://img.shields.io/badge/Zephyr-000000?style=for-the-badge&logo=zephyrproject&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)

</div>

---

## What I build

Multi-domain instrument platforms — the hardware, the firmware, the synchronised capture
path, and the evidence model that makes a result defensible.

The architecture above is the one I keep returning to: **independently deployable nodes,
one capability contract, one timestamp domain, one evidence model.** Every node is a
complete instrument on its own — take Node C to a bench with a laptop and it still
captures, timestamps and hashes its own evidence. The control plane makes the nodes a
system without making itself a dependency.

<table>
<tr><td width="33%" valign="top">

### Node C · automotive
8–16 isolated CAN-FD channels, LIN, K-Line, Automotive Ethernet, FlexRay expansion,
FPGA/SoC with DDR and PCIe/NVMe, precision analog alongside high-speed waveform capture,
hardware timestamps with PPS/PTP.

</td><td width="33%" valign="top">

### RF, identity, vision, OT
Wideband SDR, Wi-Fi/BLE/802.15.4/sub-GHz, coherent multi-channel RF and direction finding,
NFC/RFID/contact cards and POS instrumentation, IP/PoE/ONVIF camera work, RS-485 and
industrial Ethernet.

</td><td width="33%" valign="top">

### Evidence & safety
Capture → Source → EvidenceLink with SHA-256 provenance on one correlated timeline.
Fail-silent, receive-only by default; transmit requires an independent per-channel chain,
never a shared gate.

</td></tr>
</table>

> **Timing is measured, not claimed.** An FPGA in the design is not evidence of nanosecond
> accuracy. Latency and jitter get characterised on the bench before either number appears
> in a document.

---

## Two things I care about more than tooling

**Reproduce before fixing.** A failure I can't trigger on demand isn't diagnosed — it's a
guess with a stack trace attached. Most "flaky" hardware bugs are perfectly deterministic
once the right variable is under control.

**Evidence over claims.** Timestamps, traces, exact firmware revisions, measured before and
after. If a conclusion can't be re-derived by someone else from the stored artefacts, it
isn't finished.

---

## Layers I work across

| | |
|---|---|
| **Hardware** | Schematic capture and PCB layout in KiCad · isolation and power-tree design · DFM review · bring-up, scope and logic-analyser debugging |
| **Firmware** | STM32 · ESP32 · nRF · Zephyr and FreeRTOS · BLE/GATT · OTA update paths · embedded Linux, device tree, Yocto |
| **Buses & protocols** | CAN / CAN-FD · LIN · K-Line · Automotive Ethernet · Modbus / RS-485 · OCPP and EVSE/CSMS behaviour |
| **Mobile** | Flutter · React Native · Kotlin · BLE provisioning and OTA flows for connected products |
| **Systems** | Rust · C/C++ · Python · TypeScript · deterministic pipelines, replay, regression evidence |

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
later request re-validated needlessly — the cache did the work without delivering the
benefit. Root-caused in the RFC 2616 cache policy, fixed, and covered by a regression test
that fails on the old behaviour.

</td>
</tr>
</table>

*Further upstream work in the EV-charging and CAN tooling ecosystems is in progress.*
