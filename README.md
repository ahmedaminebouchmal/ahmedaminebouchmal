<div align="center">

<img src="./stack.svg" alt="Multi-domain instrument platform architecture" width="100%">

</div>

<br>

<div align="center">

<!-- systems -->
<img src="https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white">
<img src="https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white">
<img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white">
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white">

<!-- hardware -->
<img src="https://img.shields.io/badge/KiCad-314CB0?style=for-the-badge&logo=kicad&logoColor=white">
<img src="https://img.shields.io/badge/FPGA-0091BD?style=for-the-badge&logo=xilinx&logoColor=white">
<img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white">
<img src="https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white">
<img src="https://img.shields.io/badge/Zephyr-000000?style=for-the-badge&logo=zephyrproject&logoColor=white">
<img src="https://img.shields.io/badge/Yocto-01A6D8?style=for-the-badge&logo=yocto&logoColor=white">

<!-- mobile -->
<img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white">
<img src="https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB">
<img src="https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white">
<img src="https://img.shields.io/badge/Swift-F05138?style=for-the-badge&logo=swift&logoColor=white">
<img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white">
<img src="https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white">

<!-- platform -->
<img src="https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white">
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white">

</div>

---

## The architecture, in one paragraph

Independently deployable instrument nodes, one capability contract, one timestamp domain,
one evidence model. Every node is a complete instrument on its own — take the automotive
node to a bench with nothing but a laptop and it still captures, timestamps and hashes its
own evidence. The control plane turns the nodes into a system **without becoming a
dependency of any of them**. Adding a ninth node should never require redesigning the
other eight.

That constraint is the whole design. It's also what makes the platform agent-addressable:
an expert layer can discover capabilities, request captures and correlate across domains,
because every node answers the same five endpoints.

<table>
<tr>
<td width="34%" valign="top">

#### Automotive · the flagship node
8–16 electrically isolated CAN-FD channels, LIN, K-Line, Automotive Ethernet with FlexRay
expansion. Two-plane internals: an STM32 + FPGA safety/control plane beside an FPGA/SoC
data plane with DDR, PCIe and NVMe for sustained capture.

</td>
<td width="33%" valign="top">

#### Measurement, split correctly
Slow precision analog and high-speed physical-layer waveform capture are **different
subsystems** — a 24-bit simultaneous ADC is right for supply-rail and CANH/CANL behaviour,
and useless for nanosecond edge ringing. Conflating them is how specs become fiction.

</td>
<td width="33%" valign="top">

#### Evidence as a first-class output
Capture → Source → EvidenceLink, hash-tracked, on one correlated timeline. An RF
observation, a CAN frame, a camera event and an analog measurement land on the same
timebase — which is what makes cross-domain reasoning defensible rather than suggestive.

</td>
</tr>
</table>

---

## Mobile & connected product

The instrument side is only half of a connected product. The other half is the app someone
actually holds: **Flutter** and **React Native** cross-platform, **Kotlin** on Android and
**Swift** on iOS where native is the right call, plus the parts that make hardware products
survive contact with users — BLE provisioning flows, OTA update paths and rollback,
device pairing, and fleet state that stays truthful when devices go offline for a week.

---

## Principles I don't bend

<table>
<tr><td width="50%">

**Reproduce before fixing.**
A failure I can't trigger on demand isn't diagnosed — it's a guess with a stack trace
attached. Most "flaky" hardware is perfectly deterministic once the right variable is under
control.

</td><td width="50%">

**Measure, don't infer.**
An FPGA in the block diagram is not evidence of nanosecond accuracy. Latency and jitter get
characterised on the bench before either number goes in a document.

</td></tr>
<tr><td width="50%">

**Fail silent by default.**
Receive-only unless every condition in the transmit chain agrees — service permission AND
supervisor healthy AND FPGA permission AND MCU request. Per channel, never a shared gate.

</td><td width="50%">

**Evidence over claims.**
Timestamps, traces, exact firmware revisions, measured before and after. If a conclusion
can't be re-derived from stored artefacts by someone else, it isn't finished.

</td></tr></table>

---

## Upstream contributions

<table>
<tr>
<td width="140" align="center" valign="middle">

**57k ★**

`scrapy`

</td>
<td valign="top">

**[Refresh cached response headers on RFC 2616 revalidation · #8013](https://github.com/scrapy/scrapy/pull/8013)**

Cached responses never refreshed their lifetime after a successful HTTP `304` — the cache
did the work of revalidating without ever delivering the benefit, so every subsequent
request revalidated again. Root-caused in the RFC 2616 cache policy, fixed, and covered by
a regression test that fails against the old behaviour.

</td>
</tr>
</table>

*Further upstream work in the EV-charging (OCPP) and CAN tooling ecosystems is in progress.*
