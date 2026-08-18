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
<br>
<img src="https://img.shields.io/badge/KiCad-314CB0?style=for-the-badge&logo=kicad&logoColor=white">
<img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white">
<img src="https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white">
<img src="https://img.shields.io/badge/nRF-00A9CE?style=for-the-badge&logo=nordicsemiconductor&logoColor=white">
<img src="https://img.shields.io/badge/Zephyr-000000?style=for-the-badge&logo=zephyrproject&logoColor=white">
<img src="https://img.shields.io/badge/Yocto-01A6D8?style=for-the-badge&logo=yocto&logoColor=white">
<br>
<img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white">
<img src="https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB">
<img src="https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white">
<img src="https://img.shields.io/badge/Swift-F05138?style=for-the-badge&logo=swift&logoColor=white">
<img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white">
<img src="https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white">
<br>
<img src="https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white">
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white">

</div>

<br>

<div align="center">
<table>
<tr>
<td align="center" width="25%">
<h3>8</h3>
<sub><b>INSTRUMENT NODES</b></sub><br>
<sub>each one standalone</sub>
</td>
<td align="center" width="25%">
<h3>5</h3>
<sub><b>CONTRACT ENDPOINTS</b></sub><br>
<sub>every node speaks them</sub>
</td>
<td align="center" width="25%">
<h3>1</h3>
<sub><b>TIMESTAMP DOMAIN</b></sub><br>
<sub>RF · CAN · vision · analog</sub>
</td>
<td align="center" width="25%">
<h3>0</h3>
<sub><b>MANDATORY DEPENDENCIES</b></sub><br>
<sub>remove the plane, nothing breaks</sub>
</td>
</tr>
</table>
</div>

---

<h2>The constraint everything else follows from</h2>

<blockquote>
<b>Every node is a complete instrument. The control plane must never become a dependency.</b>
</blockquote>

Take the automotive node to a bench with nothing but a laptop — it still captures, timestamps
and hashes its own evidence. Add the control plane and eight independent instruments become one
correlated system. Remove it and nothing stops working.

That single rule is why the platform scales sideways: adding a ninth node never forces a redesign
of the other eight. It's also what makes the whole thing agent-addressable — an expert layer can
discover capabilities, request captures and correlate across domains, because every node answers
the same five endpoints.

<details>
<summary><b>&nbsp;Why a mandatory control plane would have been the easier — and wrong — design</b></summary>

<br>

A central plane that owns time, identity and storage is simpler to build. Every node gets thinner,
the schema lives in one place, and you never reconcile two clocks. The cost only appears later:

<table>
<tr><td width="50%" valign="top">

**What you gain by centralising**
- one clock, one schema, one storage path
- thinner nodes, cheaper BOM per unit
- a single place to reason about identity

</td><td width="50%" valign="top">

**What you lose, permanently**
- a node alone on a bench becomes useless
- the plane becomes the single point of failure
- every new node negotiates with a central design
- field work needs the whole rack, not one box

</td></tr>
</table>

The deciding case is the ordinary one: an engineer takes a single node to a vehicle, a substation
or a customer site. If that requires the rack, the platform has failed at the exact moment it
matters most. So the plane earns its place by adding correlation — never by being required.

</details>

<br>

<div align="center">

<img src="./scope.svg" alt="Multi-domain synchronised capture" width="100%">

</div>

<br>

<table>
<tr>
<td width="34%" valign="top">

#### Measurement, split correctly
Slow precision analog and high-speed physical-layer capture are **different subsystems**. A 24-bit
simultaneous ADC is right for supply rails and CANH/CANL behaviour — and useless for nanosecond
edge ringing. Conflating them is how a spec sheet becomes fiction.

</td>
<td width="33%" valign="top">

#### Timing is measured, not inferred
An FPGA in the block diagram is not evidence of nanosecond accuracy. Latency and jitter get
characterised on the bench against a disciplined reference before either number appears in a
document.

</td>
<td width="33%" valign="top">

#### Evidence is an output, not a log
Capture → Source → EvidenceLink, hash-tracked on one timebase. An RF observation, a CAN frame, a
camera event and an analog measurement land on the same timeline — which is what makes
cross-domain reasoning defensible instead of suggestive.

</td>
</tr>
</table>

---

<h2>Where each domain touches the stack</h2>

<div align="center">

<img src="./matrix.svg" alt="Capability matrix" width="100%">

</div>

<details>
<summary><b>&nbsp;How the transmit-permission chain actually works</b></summary>

<br>

Anything that can reach a live bus defaults to receive-only. Transmit requires **every** condition
to agree, and the chain is per channel — never one shared gate, because a shared gate turns a
single fault into a multi-bus event.

```
  service permission ──┐
                       │
  supervisor healthy ──┼──> AND ──> TX ENABLED  (this channel only)
                       │
   FPGA permission ────┤
                       │
     MCU request ──────┘

  any input false ────────> fail silent, receive-only
```

Failure modes this is built against: a supervisor brown-out mid-transaction, firmware asserting
a request the hardware never authorised, and one channel's fault propagating into the other
fifteen. The last one is why the gate is replicated rather than shared — it costs more silicon
and it is not negotiable.

</details>

<details>
<summary><b>&nbsp;What a capture carries before it is allowed on the timeline</b></summary>

<br>

<table>
<tr><td width="30%"><b>timestamp</b></td><td>from the disciplined domain, not the host OS clock</td></tr>
<tr><td><b>source</b></td><td>which physical interface, on which node, in which mode</td></tr>
<tr><td><b>node identity</b></td><td>so a federated timeline can be pulled apart again</td></tr>
<tr><td><b>content hash</b></td><td>SHA-256 over the raw bytes, before any normalisation</td></tr>
<tr><td><b>uncertainty</b></td><td>the honest error bar — absent uncertainty is a red flag, not a clean result</td></tr>
</table>

Raw is preserved and never overwritten by a derived view. If a later analysis disagrees with an
earlier one, both remain re-derivable from the same stored bytes — which is the difference between
an evidence trail and a log file.

</details>

---

<h2>From schematic to first power-on</h2>

<div align="center">

<img src="./board.svg" alt="Board bring-up sequence" width="100%">

</div>

Isolation and power-tree get reviewed before anything is energised. ERC and DRC are enforced, diffs
stay deterministic, and manufacturing output requires a human decision — a bench instrument that
can reach a vehicle network is not a place for silent automation.

---

<h2>Prototype → manufacture</h2>

<div align="center">

<img src="./pipeline.svg" alt="Prototype to manufacture pipeline" width="100%">

</div>

Every gate has an exit criterion. A mistake caught at schematic costs an afternoon; the same
mistake caught at pilot costs a tooling run and a lead time.

<details>
<summary><b>&nbsp;Two things that get planned late and hurt</b></summary>

<br>

<table>
<tr><td width="50%" valign="top">

**Export control**

Dual-use RF, spectrum monitoring and direction-finding hardware fall under **EU Regulation
2021/821**, administered in Germany by **BAFA**. This decides whether a unit can legally cross a
border, be demonstrated abroad, or be contributed to a multi-country consortium.

It is a *classification* question first — what the hardware is capable of, not what it is marketed
as — and the answer shapes the BOM. Discovering it after Rev B is expensive.

</td><td width="50%" valign="top">

**Bench instrument ≠ fielded unit**

A receive-only bench box and a unit deployed in a contested or industrial environment are
different products. The step between them is ruggedisation, EMC qualification, environmental and
vibration testing, sealing, thermal derating and a supply chain that survives a multi-year build.

The gap is routinely underestimated because the schematic barely changes. The cost and calendar
do.

</td></tr>
</table>

</details>

---

<h2>Mobile &amp; connected product</h2>

<div align="center">

<img src="./mobile.svg" alt="Connected product app side" width="100%">

</div>

The instrument is half a product. The other half is what someone holds — and it's usually where
connected hardware actually fails.

<details>
<summary><b>&nbsp;The four app-side failures that break connected hardware in the field</b></summary>

<br>

<table>
<tr><td width="25%" valign="top">

**Provisioning**
Works perfectly on the developer's desk with one device and clean RF. Fails in a room with forty
devices, a bad advertising interval, and a user who backgrounds the app halfway through pairing.

</td><td width="25%" valign="top">

**OTA rollback**
Almost every product has A/B slots. Far fewer have *exercised* the rollback path — pulled power
mid-write, corrupted the image deliberately, confirmed the unit still boots the old slot.

</td><td width="25%" valign="top">

**Pairing recovery**
Interruption is the normal case, not the exception. Lift, walk out of range, take a call. State
that can't resume from a partial handshake produces a device that must be factory-reset.

</td><td width="25%" valign="top">

**Fleet truth**
A device offline for a week is not "healthy" and not "failed" — it is *unknown*. Dashboards that
collapse those three states into two are the reason nobody trusts the dashboard.

</td></tr>
</table>

**Flutter** and **React Native** where cross-platform is right; **Kotlin** and **Swift** when
background BLE has to survive the OS, or MTU and throughput tuning decide whether the product works
at all.

</details>

---

<h2>Principles I don't bend</h2>

<table>
<tr><td width="50%" valign="top">

**Reproduce before fixing**
A failure I can't trigger on demand isn't diagnosed — it's a guess with a stack trace attached.
Most "flaky" hardware is perfectly deterministic once the right variable is under control.

</td><td width="50%" valign="top">

**Fail silent by default**
Receive-only unless every condition in the transmit chain agrees. Per channel. Never a shared gate.

</td></tr>
<tr><td width="50%" valign="top">

**Smallest change that solves it**
No rewrite sold as a fix. The change should be small enough that a reviewer can hold the whole
thing in their head.

</td><td width="50%" valign="top">

**Evidence over claims**
Timestamps, traces, exact firmware revisions, measured before and after. If a conclusion can't be
re-derived from stored artefacts by someone else, it isn't finished.

</td></tr>
</table>
