<div align="center">

<img src="./stack.svg" alt="Multi-domain instrument platform architecture" width="100%">

</div>

<br>

<div align="center">

<img src="https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white">
<img src="https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white">
<img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white">
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white">
<img src="https://img.shields.io/badge/VHDL%20%2F%20Verilog-0091BD?style=for-the-badge&logo=xilinx&logoColor=white">

<img src="https://img.shields.io/badge/KiCad-314CB0?style=for-the-badge&logo=kicad&logoColor=white">
<img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white">
<img src="https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white">
<img src="https://img.shields.io/badge/nRF-00A9CE?style=for-the-badge&logo=nordicsemiconductor&logoColor=white">
<img src="https://img.shields.io/badge/Zephyr-000000?style=for-the-badge&logo=zephyrproject&logoColor=white">
<img src="https://img.shields.io/badge/Yocto-01A6D8?style=for-the-badge&logo=yocto&logoColor=white">

<img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white">
<img src="https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB">
<img src="https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white">
<img src="https://img.shields.io/badge/Swift-F05138?style=for-the-badge&logo=swift&logoColor=white">
<img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white">
<img src="https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white">

<img src="https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white">
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white">

</div>

---

## The design constraint everything follows from

**Every node is a complete instrument. The control plane must never become a dependency.**

Take the automotive node to a bench with nothing but a laptop — it still captures, timestamps
and hashes its own evidence. Add the control plane and eight independent instruments become
one correlated system. Remove it and nothing stops working.

That single rule is why the platform scales sideways: adding a ninth node never forces a
redesign of the other eight, and it's what makes the whole thing agent-addressable — an
expert layer can discover capabilities, request captures and correlate across domains
because every node answers the same five endpoints.

<br>

<div align="center">

<img src="./scope.svg" alt="Multi-domain synchronised capture" width="100%">

</div>

<br>

<table>
<tr>
<td width="34%" valign="top">

#### Measurement, split correctly
Slow precision analog and high-speed physical-layer capture are **different subsystems**.
A 24-bit simultaneous ADC is right for supply rails and CANH/CANL behaviour — and useless
for nanosecond edge ringing. Conflating them is how a spec sheet becomes fiction.

</td>
<td width="33%" valign="top">

#### Timing is measured, not inferred
An FPGA in the block diagram is not evidence of nanosecond accuracy. Latency and jitter get
characterised on the bench, against a disciplined reference, before either number appears in
a document.

</td>
<td width="33%" valign="top">

#### Evidence is an output, not a log
Capture → Source → EvidenceLink, hash-tracked on one timebase. An RF observation, a CAN
frame, a camera event and an analog measurement land on the same timeline — which is what
makes cross-domain reasoning defensible instead of suggestive.

</td>
</tr>
</table>

---

## From schematic to first power-on

<div align="center">

<img src="./board.svg" alt="Board bring-up sequence" width="100%">

</div>

Isolation and power-tree get reviewed before anything is energised. ERC and DRC are enforced,
diffs stay deterministic, and manufacturing output requires a human decision — a bench
instrument that can reach a vehicle network is not a place for silent automation.

---

## Mobile & connected product

The instrument is half a product. The other half is what someone holds: **Flutter** and
**React Native** where cross-platform is right, **Kotlin** and **Swift** where native wins —
plus the parts that decide whether connected hardware survives real users. BLE provisioning
that works on a bad day. OTA with a rollback path that has actually been tested. Pairing that
recovers from interruption. Fleet state that stays honest when a device has been offline for
a week.

---

## Principles I don't bend

<table>
<tr><td width="50%">

**Reproduce before fixing.**
A failure I can't trigger on demand isn't diagnosed — it's a guess with a stack trace
attached. Most "flaky" hardware is perfectly deterministic once the right variable is under
control.

</td><td width="50%">

**Fail silent by default.**
Receive-only unless every condition in the transmit chain agrees — service permission AND
supervisor healthy AND FPGA permission AND MCU request. Per channel. Never a shared gate.

</td></tr>
<tr><td width="50%">

**Smallest change that solves it.**
No rewrite sold as a fix. The change should be small enough that a reviewer can hold the
whole thing in their head.

</td><td width="50%">

**Evidence over claims.**
Timestamps, traces, exact firmware revisions, measured before and after. If a conclusion
can't be re-derived from stored artefacts by someone else, it isn't finished.

</td></tr></table>
