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
<img src="https://img.shields.io/badge/Linux-1A1A1A?style=for-the-badge&logo=linux&logoColor=FCC624">
<br>
<img src="https://img.shields.io/badge/CAN%20%2F%20CAN--FD-0EA5E9?style=for-the-badge">
<img src="https://img.shields.io/badge/LIN%20%C2%B7%20UDS%20%C2%B7%20OBD--II-0284C7?style=for-the-badge">
<img src="https://img.shields.io/badge/OCPP%201.6J%20%2F%202.0.1-F59E0B?style=for-the-badge&logoColor=black">
<img src="https://img.shields.io/badge/OCPI%20%C2%B7%20ISO%2015118-B45309?style=for-the-badge">
<br>
<img src="https://img.shields.io/badge/Modbus%20RTU%20%2F%20TCP-7C3AED?style=for-the-badge">
<img src="https://img.shields.io/badge/OPC--UA-6D28D9?style=for-the-badge">
<img src="https://img.shields.io/badge/MQTT-660066?style=for-the-badge&logo=mqtt&logoColor=white">
<img src="https://img.shields.io/badge/BLE%20%C2%B7%20802.15.4%20%C2%B7%20LoRaWAN-0F766E?style=for-the-badge&logo=bluetooth&logoColor=white">
<img src="https://img.shields.io/badge/NFC%20%C2%B7%20ISO%207816-059669?style=for-the-badge">
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
<img src="https://img.shields.io/badge/TimescaleDB-FDB515?style=for-the-badge&logo=timescale&logoColor=black">
<img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white">
<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white">

</div>

<br>

<div align="center">
<table>
<tr>
<td align="center" width="20%">
<h3>8+</h3>
<sub><b>INSTRUMENT NODES</b></sub><br>
<sub>open roster, each standalone</sub>
</td>
<td align="center" width="20%">
<h3>5</h3>
<sub><b>CONTRACT ENDPOINTS</b></sub><br>
<sub>every node speaks them</sub>
</td>
<td align="center" width="20%">
<h3>20+</h3>
<sub><b>BUS &amp; PROTOCOL STANDARDS</b></sub><br>
<sub>spoken natively, not wrapped</sub>
</td>
<td align="center" width="20%">
<h3>1</h3>
<sub><b>TIMESTAMP DOMAIN</b></sub><br>
<sub>every source, one timeline</sub>
</td>
<td align="center" width="20%">
<h3>0</h3>
<sub><b>SILENT FAILURES</b></sub><br>
<sub>a dropped record raises</sub>
</td>
</tr>
</table>
</div>

---

<h2>The constraint everything else follows from</h2>

<blockquote>
<b>Every node is a complete instrument. The control plane must never become a dependency.</b>
</blockquote>

Take *any* node to a bench with nothing but a laptop — radio, vehicle bus, identity reader,
industrial line, camera, direction-finding array, mixed-signal rig — and it still captures,
timestamps and hashes its own evidence. Add the control plane and those independent instruments
become one correlated system. Remove it and nothing stops working.

That single rule is why the roster is open-ended rather than fixed. The platform is already past
eight nodes, and adding the next one never forces a redesign of the ones already built. It is also
what makes the whole ecosystem agent-addressable — an expert layer can discover capabilities,
request captures and correlate across domains it was never specifically taught, because every node
answers the same five endpoints.

<h3>The ecosystem, domain by domain</h3>

<table>
<tr>
<td width="50%" valign="top">

| Domain | What it speaks |
|---|---|
| **Radio & wireless** | Wi-Fi, BLE, 802.15.4, sub-GHz, wideband SDR |
| **Vehicle networks** | isolated CAN-FD × 8–16, LIN, K-Line, Automotive Ethernet, FlexRay |
| **Identity & secure element** | NFC, LF/HF RFID, ISO-7816, POS and debug interfaces |
| **Control & evidence plane** | registry, time authority, authorisation, segmentation, health |

</td>
<td width="50%" valign="top">

| Domain | What it speaks |
|---|---|
| **Vision & physical** | IP, PoE, ONVIF, RTSP, MIPI CSI-2, GMSL, edge inference |
| **Industrial & OT** | RS-485, Modbus, OPC-UA, LoRa, industrial Ethernet, sensor I/O |
| **Coherent RF & DF** | multi-channel coherent SDR, array sensing, direction finding |
| **Hardware & mixed-signal** | synchronised precision acquisition, FPGA timing, side-channel |

</td>
</tr>
</table>

Energy and charging, automation pipelines and the mobile layer are not separate islands either —
they attach to the same contract and land on the same timeline. Each gets its own section below.
None of them is the platform; all of them are nodes on it.

<div align="center">

<img src="./ecosystem.svg" alt="Every node in the ecosystem, each lighting in turn" width="100%">

</div>

<sub>The board above lights each node in turn on a 24-second cycle, and repaints itself for your
system light or dark theme. If your OS asks for reduced motion it renders static and fully lit
instead. Open any node below for the part that does not fit on a card.</sub>

<details>
<summary><b>&nbsp;A — Radio &amp; wireless</b> &nbsp;·&nbsp; <sub>Wi-Fi, BLE, 802.15.4, Thread, sub-GHz, LoRaWAN, wideband SDR</sub></summary>

<br>

The bench and the building disagree, and the building wins. A link budget that closes on a desk
meets forty competing radios, a metal rack, a closing door and a human body that moves. Every
wireless failure I have chased in the field came from that gap, not from the protocol.

<table>
<tr><td width="50%" valign="top">

**What gets measured**
- RSSI *and* link quality, never RSSI alone
- retry and drop rate under real contention
- duty cycle against the regional regulatory limit
- coexistence with whatever else owns that band

</td><td width="50%" valign="top">

**What is deliberately not assumed**
- that the antenna in the enclosure behaves like the one on the bench
- that a certified module makes the *product* certified
- that a clean spectrum capture on a Sunday means anything on a Monday

</td></tr>
</table>

Receive is the default path. Anything capable of transmitting is gated by the same permission chain
as every other node, and bounded by regulatory limits established before a schematic exists rather
than after.

</details>

<details>
<summary><b>&nbsp;B — Identity &amp; secure element</b> &nbsp;·&nbsp; <sub>NFC, LF/HF RFID, ISO 14443, ISO 7816, POS, secure boot</sub></summary>

<br>

The rule here is short: **credential material never enters a repository, a log, or a capture.** What
is recorded is the protocol exchange and its timing — the shape of the conversation, never its
secret.

That constraint is easy to state and routinely violated in practice, usually by a debug build that
was never meant to ship, or a trace file attached to a support ticket. So it is enforced at the
capture layer rather than by discipline: the fields that would carry a secret are not collected.

<table>
<tr><td width="30%"><b>secure boot</b></td><td>chain established at manufacture, not retrofitted after the first field incident</td></tr>
<tr><td><b>signed OTA</b></td><td>with a rollback path that has actually been exercised, not merely designed</td></tr>
<tr><td><b>debug lockdown</b></td><td>JTAG/SWD closed in production, provisioned on the line</td></tr>
<tr><td><b>key storage</b></td><td>secure element or equivalent — never a constant in firmware</td></tr>
</table>

</details>

<details>
<summary><b>&nbsp;C — Vehicle networks (flagship)</b> &nbsp;·&nbsp; <sub>CAN-FD ×8–16 isolated, LIN, K-Line, Automotive Ethernet, FlexRay, UDS</sub></summary>

<br>

The electrically hardest node, and the reason the transmit-permission chain exists at all. Sixteen
isolated channels means sixteen independent gates — replicated, never shared, because a shared gate
turns one channel fault into a multi-bus event.

Continuous capture runs to NVMe with hardware timestamps from a disciplined domain. Not host clocks.
Not interpolation. The detailed instrument view, the permission chain and the capture contract are
in the **Node C in depth** section further down — this node has the deepest treatment on the page
because it has the least margin for a wrong assumption.

</details>

<details>
<summary><b>&nbsp;D — Control &amp; evidence plane</b> &nbsp;·&nbsp; <sub>registry, time authority, authorisation, segmentation, health</sub></summary>

<br>

The only optional node on the board, and the most consequential design decision on this page.

Every other node works with this one switched off. It is drawn dashed in the diagram for exactly
that reason — deliberately absent from the minimum viable system rather than missing from it. When
present it supplies registry, time authority, authorisation, segmentation and health, and turns
independent instruments into one correlated timeline.

**It earns its place by correlating. It never earns it by being required.** The moment a node cannot
function without it, the platform has failed at the exact moment it matters most: one engineer, one
box, one customer site.

</details>

<details>
<summary><b>&nbsp;E — Vision &amp; physical</b> &nbsp;·&nbsp; <sub>IP, PoE, ONVIF, RTSP, MIPI CSI-2, GMSL, edge inference</sub></summary>

<br>

A camera event is only worth capturing if it lands on the same timeline as the bus frame and the RF
observation. Otherwise it is footage, and footage is not evidence — it is something you scrub
through afterwards hoping to find the moment.

Frame pacing and drop policy are specified rather than inherited from whatever the pipeline happens
to do under load. A dropped frame nobody recorded as dropped is worse than a gap, because it makes
the timeline look complete when it is not.

Hardware-synced triggering is what makes *the camera saw this at the same instant the bus carried
that* a defensible statement instead of a suggestive one.

</details>

<details>
<summary><b>&nbsp;F — Industrial &amp; OT</b> &nbsp;·&nbsp; <sub>RS-485, Modbus RTU/TCP, OPC-UA, PROFINET, MQTT, Sparkplug B</sub></summary>

<br>

**A register number is not a meaning.** Half the real work on an industrial integration is
recovering what a PLC tag actually represents on the floor — and that knowledge usually lives in a
person, not a document. Skipping that step is how a dashboard ends up confidently reporting the
wrong quantity in the right units.

The engineering constraints that follow:

- **store-and-forward**, because the uplink will drop and the line will not stop for it
- **watchdog and safe restart**, because an edge gateway that wedges silently is worse than one that
  crashes loudly
- **isolated RS-485, surge protection, 4–20 mA, 24 V I/O** — the physical layer of a factory is
  hostile in ways an office network never is
- **DIN-rail and sealed builds**, because the enclosure is part of the specification

</details>

<details>
<summary><b>&nbsp;G — Coherent RF &amp; direction finding</b> &nbsp;·&nbsp; <sub>multi-channel coherent SDR, array sensing, bearing estimation</sub></summary>

<br>

**Coherence is a hardware property, not a software claim.** Channels either share a clock and a
calibrated phase reference or they do not. If they do not, the bearing the algorithm produces is
decoration, and the error bar next to it is decoration too.

This node carries an **export-control classification question before it carries a schematic**.
Dual-use RF, spectrum monitoring and direction-finding capability fall under **EU Regulation
2021/821**, administered in Germany by **BAFA**. That classification decides whether a unit can
cross a border, be demonstrated abroad, or join a multi-country consortium — and it turns on what
the hardware *can do*, not how it is described. The answer shapes the bill of materials, so it is
asked first. Discovering it after a board revision is expensive in both money and calendar.

</details>

<details>
<summary><b>&nbsp;H — Hardware &amp; mixed-signal</b> &nbsp;·&nbsp; <sub>24-bit simultaneous ADC, FPGA timing, side-channel, power characterisation</sub></summary>

<br>

The node where the measurement split matters most, and where specification sheets most often become
fiction.

<table>
<tr><td width="50%" valign="top">

**24-bit simultaneous-sampling ADC**

Right for supply rails, differential steady-state behaviour and power characterisation.

Useless for nanosecond edge ringing.

</td><td width="50%" valign="top">

**High-speed waveform capture**

Right for edge rate, ringing, jitter and eye behaviour.

Wrong for low-noise DC precision.

</td></tr>
</table>

They are different subsystems with different silicon, and quoting one instrument number for the
other job is the most common way a datasheet stops being true. Equally: an FPGA in a block diagram
is not evidence of nanosecond accuracy. Latency and jitter get characterised on the bench against a
disciplined reference before either number appears in any document.

</details>

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

The deciding case is the ordinary one: an engineer takes a single node to a vehicle, a substation or
a customer site. If that requires the rack, the platform has failed at the exact moment it matters
most. So the plane earns its place by adding correlation — never by being required.

</details>

---

<h2>Node C in depth — signal integrity &amp; vehicle networks</h2>

<div align="center">

<img src="./scope.svg" alt="Differential bus capture with decoded frames and measured edge timing" width="100%">

</div>

**CAN and CAN-FD**, **LIN**, **K-Line**, **Automotive Ethernet**, **UDS** and **OBD-II** — captured
with hardware timestamps, decoded, and correlated against the analog reality on the wire.

<table>
<tr>
<td width="34%" valign="top">

#### Measurement, split correctly
Slow precision analog and high-speed physical-layer capture are **different subsystems**. A 24-bit
simultaneous ADC is right for supply rails and CANH/CANL behaviour — and useless for nanosecond edge
ringing. Conflating them is how a spec sheet becomes fiction.

</td>
<td width="33%" valign="top">

#### Timing is measured, not inferred
An FPGA in the block diagram is not evidence of nanosecond accuracy. Latency and jitter get
characterised on the bench against a disciplined reference before either number appears in a
document.

</td>
<td width="33%" valign="top">

#### Evidence is an output, not a log
Capture → Source → EvidenceLink, hash-tracked on one timebase. An RF observation, a bus frame, a
camera event and an analog measurement land on the same timeline — which is what makes cross-domain
reasoning defensible instead of suggestive.

</td>
</tr>
</table>

<details>
<summary><b>&nbsp;How the transmit-permission chain actually works</b></summary>

<br>

Anything that can reach a live bus defaults to receive-only. Transmit requires **every** condition to
agree, and the chain is per channel — never one shared gate, because a shared gate turns a single
fault into a multi-bus event.

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

Failure modes this is built against: a supervisor brown-out mid-transaction, firmware asserting a
request the hardware never authorised, and one channel's fault propagating into the other fifteen.
The last one is why the gate is replicated rather than shared — it costs more silicon and it is not
negotiable.

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
earlier one, both remain re-derivable from the same stored bytes — which is the difference between an
evidence trail and a log file.

</details>

---

<h2>Business-process &amp; production automation</h2>

<div align="center">

<img src="./automation.svg" alt="Automation architecture — source systems, ingest, processing core, delivery, run metrics" width="100%">

</div>

ERP and MES, machine telemetry over **Modbus** and **OPC-UA**, documents, mailboxes, third-party APIs
— pulled into one pipeline that produces validated, typed, traceable records. The retry path, the
dead-letter route, the human-review queue and resume-after-crash are part of the design, not patches
added after the first bad run.

<details>
<summary><b>&nbsp;Why the happy path is the least interesting part of an automation</b></summary>

<br>

<table>
<tr><td width="50%" valign="top">

**Failure modes that actually occur**

- an API returning **HTTP 200 with an error body** — the single most common cause of silently corrupt
  datasets
- the same file delivered twice, hours apart, with one field changed
- a schema that shifts without a version bump
- a run that dies at 60% with no way to resume except full replay
- an extraction confident enough to write, wrong enough to matter
- the undocumented exception rule that lives only in one person's head

</td><td width="50%" valign="top">

**What that forces into the design**

- validation *before* persistence, never after
- dedupe on content hash, not on filename or timestamp
- idempotent workers — reprocessing must be safe by construction
- arrival time and event time stored separately, because they are not the same thing
- append-only history, so a correction is a new version rather than an overwrite
- a confidence threshold below which nothing is auto-accepted and a person decides

</td></tr>
</table>

The measurable outcome is deliberately boring: same input, same output, byte-equal, on a rerun six
months later — and every number in the final report traceable back to the exact bytes it came from.

</details>

<details>
<summary><b>&nbsp;Extraction order: rules first, model second</b></summary>

<br>

<table>
<tr><td width="25%"><b>1 · layout match</b></td><td>known sender, known template — deterministic, free, and correct</td></tr>
<tr><td><b>2 · grammar &amp; regex</b></td><td>structured fields with a defined shape: dates, references, totals, units</td></tr>
<tr><td><b>3 · model pass</b></td><td>only for what survives the first two — the genuinely unstructured residue</td></tr>
<tr><td><b>4 · confidence</b></td><td>scored per field, not per document, with the source span retained</td></tr>
</table>

Running the model first is faster to build and worse in every other way: it costs more per document,
it is non-deterministic on reruns, and it removes the ability to say *why* a value is what it is. A
field that a rule can decide should never be decided by a guess.

</details>

---

<h2>Energy &amp; EV charging</h2>

<div align="center">

<img src="./energy.svg" alt="EV charging — pilot chain, OCPP message flow, OCPI settlement, site load management" width="100%">

</div>

**OCPP 1.6J and 2.0.1**, **OCPI** roaming, **ISO 15118** Plug &amp; Charge, **IEC 61851** pilot
signalling, MID metering, and smart-charging profiles under a real site limit. Charge-point firmware
on one side, the backend and settlement data on the other.

<details>
<summary><b>&nbsp;The three things that quietly break charging deployments</b></summary>

<br>

<table>
<tr><td width="33%" valign="top">

**Energy that isn't measured**

A session billed from a value the controller *calculated* rather than a register the meter *reported*
is a dispute waiting to happen. Where regulation requires a signed value, an inferred one is not a
shortcut — it is a defect.

</td><td width="33%" valign="top">

**Load management as a target**

The main fuse is a hard constraint, not a setpoint to aim at. Allocation has to be recomputed on
every meter sample, and a connector that cannot get headroom must queue visibly rather than silently
under-deliver.

</td><td width="33%" valign="top">

**Interop assumed, not tested**

Two implementations both "2.0.1 compliant" still disagree on transaction identity, offline behaviour
and reconnection. That gets discovered on a live site unless it is exercised against a real
counterparty first.

</td></tr>
</table>

Offline behaviour deserves its own line: the backend link *will* drop. What the charge point does
during that window — keep charging, queue transaction events, and reconcile afterwards without
duplicating or losing a session — is the difference between a product and a demo.

</details>

---

<h2>Life-science &amp; metabolic data</h2>

<div align="center">

<img src="./metabolic.svg" alt="Metabolic R&D — multi-omics sources, differential signal, pathway flux, dose-response, development ladder" width="100%">

</div>

Multi-omics ingestion, pathway and flux modelling, target ranking, and dose–response
characterisation — built on the same discipline as everything above: versioned raw data, a pinned
environment, pre-specified analysis, and negative results kept beside positive ones.

<details>
<summary><b>&nbsp;Where quantitative biology goes wrong, and what stops it</b></summary>

<br>

<table>
<tr><td width="50%" valign="top">

**The recurring failures**

- an uncorrected p-value across twenty thousand features presented as a finding
- technical replicates counted as biological ones, inflating every confidence interval
- missing values in mass-spec data imputed as zeros
- batch effect mistaken for biological signal
- a dose–response fit with no plateau — an extrapolation wearing the costume of a curve
- a target that correlates with the phenotype and never moves it

</td><td width="50%" valign="top">

**What the pipeline enforces**

- raw immutable, SHA-256 per dataset, every figure naming its exact input
- containerised analysis with locked dependencies and fixed seeds
- endpoints and tests pre-specified; anything else labelled exploratory
- imputation and normalisation choices recorded as part of the result
- the failed arm stored beside the successful one

</td></tr>
</table>

Attrition is the honest headline: the great majority of programmes that clear target identification
never reach a candidate molecule. So the value of the work sits in killing the wrong hypothesis
cheaply and early — not in defending it late.

</details>

---

<h2>Mobile &amp; connected product</h2>

<div align="center">

<img src="./mobile.svg" alt="Connected product — BLE provisioning, OTA with A/B rollback, fleet state" width="100%">

</div>

**Flutter** and **React Native** where cross-platform is right; **Kotlin** and **Swift** when
background BLE has to survive the OS, or when MTU and throughput tuning decide whether the product
works at all. The instrument is half a product — the other half is what someone holds, and that half
is usually where connected hardware actually fails.

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
Interruption is the normal case, not the exception. Lift, walk out of range, take a call. State that
can't resume from a partial handshake produces a device that must be factory-reset.

</td><td width="25%" valign="top">

**Fleet truth**
A device offline for a week is not "healthy" and not "failed" — it is *unknown*. Dashboards that
collapse those three states into two are the reason nobody trusts the dashboard.

</td></tr>
</table>

</details>

---

<h2>From schematic to first power-on</h2>

<div align="center">

<img src="./board.svg" alt="Board bring-up sequence" width="100%">

</div>

Isolation and power-tree get reviewed before anything is energised. ERC and DRC are enforced, diffs
stay deterministic, and manufacturing output requires a human decision — a bench instrument that can
reach a vehicle network is not a place for silent automation.

---

<h2>Prototype → manufacture</h2>

<div align="center">

<img src="./pipeline.svg" alt="Prototype to manufacture pipeline" width="100%">

</div>

Every gate has an exit criterion. A mistake caught at schematic costs an afternoon; the same mistake
caught at pilot costs a tooling run and a lead time.

<details>
<summary><b>&nbsp;Two things that get planned late and hurt</b></summary>

<br>

<table>
<tr><td width="50%" valign="top">

**Export control**

Dual-use RF, spectrum monitoring and direction-finding hardware fall under **EU Regulation
2021/821**, administered in Germany by **BAFA**. This decides whether a unit can legally cross a
border, be demonstrated abroad, or be contributed to a multi-country consortium.

It is a *classification* question first — what the hardware is capable of, not what it is marketed as
— and the answer shapes the BOM. Discovering it after Rev B is expensive.

</td><td width="50%" valign="top">

**Bench instrument ≠ fielded unit**

A receive-only bench box and a unit deployed in a contested or industrial environment are different
products. The step between them is ruggedisation, EMC qualification, environmental and vibration
testing, sealing, thermal derating and a supply chain that survives a multi-year build.

The gap is routinely underestimated because the schematic barely changes. The cost and calendar do.

</td></tr>
</table>

</details>

---

<h2>Where each domain touches the stack</h2>

<div align="center">

<img src="./matrix.svg" alt="Capability matrix across seven domains and six stack layers" width="100%">

</div>

<details>
<summary><b>&nbsp;What "filled / amber / outline" honestly means here</b></summary>

<br>

<table>
<tr><td width="18%"><b>filled</b></td><td>I design it, debug it at the signal or wire level, and ship it. If it breaks at 2 a.m., I can find out why without help.</td></tr>
<tr><td><b>amber</b></td><td>I work in it productively and have delivered in it, but I would pull in a specialist for the extreme end — a certification-grade RF layout, a safety-rated PLC program.</td></tr>
<tr><td><b>outline</b></td><td>Adjacent. I read it, review it, and integrate against it — I do not claim to originate it.</td></tr>
</table>

An honest matrix has outline cells in it. A profile where every cell is filled is a profile that has
not been checked against reality.

</details>

---

<h2>Principles I don't bend</h2>

<table>
<tr><td width="50%" valign="top">

**Reproduce before fixing**
A failure I can't trigger on demand isn't diagnosed — it's a guess with a stack trace attached. Most
"flaky" hardware is perfectly deterministic once the right variable is under control.

</td><td width="50%" valign="top">

**Fail silent by default**
Receive-only unless every condition in the transmit chain agrees. Per channel. Never a shared gate.

</td></tr>
<tr><td width="50%" valign="top">

**Smallest change that solves it**
No rewrite sold as a fix. The change should be small enough that a reviewer can hold the whole thing
in their head.

</td><td width="50%" valign="top">

**Evidence over claims**
Timestamps, traces, exact firmware revisions, measured before and after. If a conclusion can't be
re-derived from stored artefacts by someone else, it isn't finished.

</td></tr>
</table>
