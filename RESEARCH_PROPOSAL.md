---
title: "Open Gaming Hardware: Co-Designing an Open-Source CPU–GPU System for Extreme Gaming Performance, Reliability, and Repairability"
author: "Open Gaming Hardware Project"
date: "November 17, 2026"
version: "Research proposal v0.1"
---

# Open Gaming Hardware

## Co-Designing an Open-Source CPU–GPU System for Extreme Gaming Performance, Reliability, and Repairability

**Research proposal · Version 0.1 · November 17, 2026**  
**Project repository:** `open-gaming-hardware`  
**Status:** Proposed research objectives; no target capabilities have been demonstrated.

## Abstract

This proposal investigates whether a CPU and GPU designed together as a complete gaming system can deliver exceptional real-world performance, long-term reliability, repairability, and affordability. Its ultimate performance target is native 1920 × 1080 gameplay at a sustained minimum of 1,000 frames per second (FPS) in demanding games, including Fortnite, Call of Duty, NBA 2K, and Grand Theft Auto VI when compatible software becomes available. Its long-term durability target is a **50-year system service life**, including operation around the clock with appropriate maintenance and replaceable components. The project will publish its original hardware, software, tools, test methods, and experimental findings under open-source terms that permit independent study, modification, and commercial production.

The research deliberately begins with the desired outcomes rather than a predetermined instruction set, CPU core count, GPU architecture, fabrication technology, or interconnect. The initial investigation consists of ten seven-day public engineering iterations. Each iteration may build on a previous version, replace selected components, or start a new design. Real gameplay—not synthetic benchmark scores—will be the primary test of gaming usefulness. Instrumentation collected *during gameplay* will help distinguish processor, graphics, software, and system bottlenecks. The work will document technical advances and failures honestly; the ten-week schedule is a research cadence, not a claim that all long-term objectives can be reached within 70 days.

**Keywords:** CPU–GPU co-design, computer architecture, open-source hardware, gaming latency, frame-time consistency, maintainability, semiconductor reliability, affordable computing.

## 1. Motivation

For many gamers, the difference between low-end and high-end hardware is experienced directly: input delay, inconsistent frame delivery, stuttering, limited graphics settings, and the inability to run new games comfortably. Expensive components can make the highest-performance experiences inaccessible to people who would value them most.

Many published processor comparisons also emphasize synthetic test scores. Those measurements may be useful to engineers, but they cannot independently establish whether a system *feels good to play on*. A gaming computer is a complete system. A fast GPU can wait for a slow CPU; a powerful CPU can wait for memory; both processors can wait for software, game-engine scheduling, storage, or display output.

This project therefore treats the **CPU, GPU, memory subsystem, interconnect, firmware, operating-system interfaces, drivers, and game compatibility** as one coordinated engineering problem. It also treats reliability and repairability as design goals from the beginning, not as features added after performance has been achieved.

The broader motivation is economic. Releasing designs that others can study, modify, fabricate, and sell may lower some development and licensing barriers. More suppliers could potentially expand consumer choice and reduce prices. Open designs do not eliminate manufacturing, verification, fabrication, memory, packaging, or distribution costs, so affordability must be studied rather than assumed. The Open Source Hardware Association specifically distinguishes downloadable design documentation from the work and resources needed to manufacture hardware [1].

## 2. Central Research Question and Hypotheses

**Primary research question:**

> Can a fully open-source CPU–GPU gaming system, designed together from the beginning, deliver extremely high and consistent real-world gaming performance while remaining affordable, reliable, and practical to repair over an unusually long service life?

The project will investigate five provisional hypotheses:

- **H1 — Co-design:** Coordinating CPU scheduling, GPU execution, memory access, and the command-submission path can remove bottlenecks that limit real games.
- **H2 — User-centered testing:** Testing with actual gameplay reveals responsiveness and compatibility problems that isolated processor benchmarks miss.
- **H3 — Maintainability:** A modular, documented system can reduce the time and expense needed to recover from common hardware failures.
- **H4 — Openness:** Publicly available source designs and tools can support independent research, contributions, and potentially multiple commercial implementations.
- **H5 — Architectural freedom:** Allowing each experiment to change or abandon previous assumptions can reveal better solutions than committing to an architecture before evidence is collected.

These are questions to test, not findings.

## 3. Ultimate Objectives

### 3.1 Gaming performance

The ultimate target is to run modern, demanding games at **native 1920 × 1080 resolution** with a **minimum of 1,000 fully rendered frames per second** during active gameplay. This translates to a frame-completion interval of **1 millisecond or less**, or about **2.0736 billion displayed pixel positions per second** before accounting for geometry processing, shading, overdraw, memory traffic, and other computation.

| Property | Target |
|---|---|
| Resolution | 1920 × 1080, rendered natively |
| Gaming throughput | At least 1,000 completed game frames per second |
| Frame consistency | Every measured gameplay frame at or below 1 ms in a defined test |
| Rendering integrity | No skipped frames or generated/interpolated frames counted toward the goal |
| User experience | Responsive controls, correct visuals, stable gameplay |
| Games of interest | Fortnite; Call of Duty campaign and multiplayer; NBA 2K; GTA VI when supported |
| Software compatibility | The actual unmodified games must recognize and run on the system |

The *system* must meet this target, not the CPU or GPU in isolation. A GPU capable of a certain render rate does not guarantee that a particular game engine can submit simulation and rendering work at that rate. Game-specific limits, online play, drivers, security requirements, and game-engine behavior will be recorded rather than hidden.

As of this proposal, Rockstar lists **November 19, 2026** as the GTA VI release date for **PlayStation 5 and Xbox Series X|S**; an official native PC version is not listed in that launch announcement [2]. GTA VI testing on the proposed open CPU–GPU system therefore remains a later compatibility milestone, not an immediately available PC test. Fortnite's competitive environment also imposes platform-security requirements, including Secure Boot, TPM, and IOMMU for tournaments [3]. These constraints belong to the system research, not merely the GPU design.

### 3.2 Long-term reliability and durability

The system-level service-life objective is **50 years**, including a design path for continuous 24/7 operation, corresponding to roughly **438,300 operating hours**. The intent is Toyota-like dependability: sustained useful service, predictable maintenance, recoverability, and readily replaceable parts.

This is **not** a claim that every original fan, memory module, connector, or silicon device can run without failure for five decades. The research will distinguish:

1. **Component longevity:** expected wear and failure behavior of an individual part.
2. **System longevity:** whether the complete machine can remain useful after servicing and replacement.
3. **Availability:** whether users can continue operating the system with minimal interruption.
4. **Technology longevity:** whether open drivers, firmware, documentation, and interfaces remain usable or can be maintained as software ecosystems change.

If the project ultimately requires no interruption even during component replacement, that becomes a separate research question about redundancy, hot-swappable subsystems, or failover. A simple modular design does not automatically provide uninterrupted operation.

### 3.3 Repairability and maintainability

The system should be easy to open, diagnose, clean, service, and reassemble. Wherever feasible, the design will support replacement of cooling equipment, power modules, storage, connectors, and other failure-prone subsystems. Modular processor and high-bandwidth memory packaging will be investigated as a research direction rather than assumed to be straightforward: the electrical demands of high-speed links can conflict with detachable modules.

The practical question is: **If one part fails, can an ordinary owner identify it, replace it at reasonable cost, and return the computer to full operation?** Repairability can be assessed through disassembly steps, necessary tools, access to spare parts, repair documentation, time to repair, and successful post-repair operation—factors aligned with the European Commission's research on repair and upgrade scoring [4].

### 3.4 Affordability and open manufacturing

The goal is to minimize the **total lifetime cost** of an excellent gaming experience, not merely the initial selling price. The project will examine the bill of materials, board complexity, memory and packaging requirements, fabrication and assembly costs, electricity, replacement parts, and maintenance. Open-source designs should enable others to experiment with compatible products without requiring permission from the original project for each implementation, subject to the selected licenses.

A commercially usable open design is not, by itself, a commodity-priced product. The economic impact of openness depends on whether other parties can realistically manufacture, test, distribute, and support the hardware.

## 4. Research Scope: Design a System, Not Two Isolated Chips

The project will explore the following interacting subsystems without deciding their final implementations in advance.

**CPU.** Game logic, simulation, physics, scripting, AI, input processing, operating-system tasks, and command preparation. Research questions include effective single-thread latency, multicore scheduling, cache organization, branch behavior, memory latency, and timing consistency.

**GPU.** Graphics commands, geometry processing, rasterization, shading, texturing, memory access, display output, and potentially general-purpose compute. Research questions include processing parallelism, warp/thread control, resource scheduling, shader execution, and data movement.

**CPU–GPU connection.** Command dispatch, synchronization, queues, shared or separate memory, cache coherence, interconnect bandwidth, and the cost of moving data. Possible approaches include a tightly integrated processor, discrete modules, or other designs. No packaging method is predetermined.

**Platform and software.** Firmware, boot process, operating-system support, compilers, graphics drivers, graphics APIs, device management, security features, and compatibility with real commercial games. These are essential because raw hardware performance cannot substitute for game compatibility.

**Serviceable physical system.** Power delivery, voltage regulation, thermals, connectors, enclosure access, mechanical stress, replacement parts, and upgrade paths.

Open reference work provides starting points, not a mandatory architecture. The OpenHW CVA6 project demonstrates a configurable open RISC-V CPU core [5]. Vortex provides an open RISC-V GPU research platform encompassing hardware and software [6]. Mesa provides an established open-source graphics-driver ecosystem [7], while OpenROAD addresses stages of open digital chip implementation [8]. The project may reuse or study these tools subject to their licenses and may write new tools when existing ones are inadequate.

## 5. Methods

### 5.1 Objective-driven experimental process

The researchers will begin with the outcome and then investigate how to achieve it. In each weekly cycle they will:

1. Identify the largest observed obstacle to the ultimate objective.
2. Examine prior work, textbooks, research papers, existing code, and available hardware.
3. Make a testable design decision and build an experiment.
4. Test the result in the closest achievable real application.
5. Record failures, limitations, evidence, and what changed.
6. Publish the work and decide what to pursue next.

The method does not require all ten architectures to be planned beforehand. A new version can preserve the prior version, replace individual modules, or be a complete redesign. Other contributors' work and external designs will be credited, and source provenance will be documented.

### 5.2 Gamer-first performance tests

The principal performance tests will be **actual gaming sessions**, not synthetic score competitions. The project will use representative scenarios:

| Game | Gamer-centered test |
|---|---|
| Fortnite | Building, editing, aiming, movement, combat, crowded scenes, and online play |
| Call of Duty | Full campaign gameplay, demanding action sequences, and multiplayer |
| NBA 2K | Complete matches, movement, controller response, animation and arena scenes |
| GTA VI | Exploration, driving, crowded scenes, and combat when compatible access exists |

Each recorded session should identify game version, settings, native resolution, graphics preset, operating system, CPU and GPU implementation, driver, game scene, duration, and whether game FPS limits were active. The goal is a transparent comparison of the **experience of playing** rather than an isolated numerical claim.

Subjective feedback matters: did aiming feel immediate, did the controls respond predictably, and were there visible stalls or rendering defects? At the same time, frame-time traces, error logs, temperature, power, and CPU/GPU utilization may be collected **during those same sessions** to explain causes of a bad experience. This is instrumentation of real gameplay, not a substitute synthetic benchmark.

The ultimate criterion of never exceeding 1 ms is a strict engineering target that must be evaluated over a defined and reproducible gameplay window. A software-imposed cap cannot be counted as a hardware failure, and a high synthetic throughput result cannot be counted as proof of 1,000-FPS gameplay.

### 5.3 Reliability tests

The project will first establish stable gaming operation and progressively extend continuous-use tests. Early tests can include hours or days of actual gameplay loops, cycling through real workloads, observing stability, and examining components after heat and vibration exposure as appropriate.

Later work may employ component-specific accelerated tests, failure analysis, and model-based projections. High-temperature operating-life testing, for example, is an established way to evaluate semiconductor reliability under accelerated conditions [9]. These tests provide evidence about particular failure mechanisms; they **cannot prove** that a complete new computer will operate flawlessly for 50 calendar years.

Maintenance and repair events will be recorded alongside operating hours. Reliability claims will distinguish **measured uptime**, **modeled service life**, and **the aspirational 50-year objective**.

### 5.4 Repair and replacement tests

For each designated serviceable component, a person should be able to follow documented procedures to identify the problem, remove the defective part, install a replacement, restore operation, and verify normal gameplay.

Evaluation will record: tools required; number and difficulty of disassembly steps; repair duration; need for proprietary equipment; part availability and cost; damage risk; and whether software or firmware must be reconfigured. The project will publish repair procedures and accept community findings from independent tests.

### 5.5 Economic evaluation

Affordability will be investigated through component and assembly cost estimates, quotes where available, electricity requirements, expected servicing and replacement costs, and barriers to independent manufacture. When suitable evidence exists, the team will examine whether public design files reduce engineering effort or enable alternative implementations.

The economic hypothesis will not be presented as a proven causal result unless supported by evidence of actual suppliers, production costs, and prices.

## 6. Ten-Week Open Research Program

The first ten weeks form a public learning experiment, not the complete lifespan of the project. Each seven-day cycle ends with a release of **what actually exists**.

| Release | Commitment |
|---|---|
| V1 — Week 1 | Publish the first architecture or system experiment and evidence of its behavior |
| V2 — Week 2 | Attack the most important limitation revealed by V1 |
| V3 — Week 3 | Publish another tested design or meaningful subsystem change |
| V4 — Week 4 | Improve whichever element most limits actual gaming progress |
| V5 — Week 5 | Revisit earlier assumptions and select the strongest available direction |
| V6 — Week 6 | Continue CPU, GPU, interconnect, software, or platform experiments as evidence directs |
| V7 — Week 7 | Extend real-application functionality or compatibility |
| V8 — Week 8 | Improve measured responsiveness, consistency, or recoverability |
| V9 — Week 9 | Integrate the strongest useful results, or replace an unsuccessful design |
| V10 — Week 10 | Publish the best supported system result, complete records, and next research questions |

No specific technical feature is promised in a given week beyond a transparent research and development release. Each published version should contain source files when available, setup information, prior-work attribution, a real demonstration or test evidence, known limitations, and a log of decisions. If an experiment fails, its release will document the failure rather than relabel it as success.

## 7. Reproducibility and Open-Source Publication

The project intends to release the editable materials required to understand and reproduce each original component: hardware description code, architectural specifications, compilers and drivers, firmware, simulation scripts, PCB files, bills of materials, test harnesses, repair instructions, and original analysis. The actual scope of a release must be stated clearly; reliance on a commercial fabrication service, proprietary game, or externally licensed IP will not be concealed.

Licensing will be finalized before code and designs are distributed as open-source releases. The **CERN Open Hardware Licence v2** family offers permissive and reciprocal options for hardware [10]. A separate established open-source software license may be selected for code. License selection must preserve the intended right to study, modify, manufacture, and sell compatible products while respecting the licenses of reused materials.

The repo will distinguish project-created material from borrowed research or third-party code. Commercial games will **not** be included in the repository; gameplay results and any permitted screenshots or clips can document compatibility instead.

## 8. Technical and Scientific Limitations

The proposal confronts several unresolved obstacles:

- **Game engine and software ceilings.** Achieving 1,000 FPS requires the complete game to progress and render that quickly. CPU, engine, API, synchronization, and platform constraints can prevent this even if the GPU itself is fast.
- **AAA compatibility.** Building processors and drivers is not equivalent to being able to run closed commercial games, their operating systems, or anti-cheat systems.
- **Manufacturing scale.** A functional FPGA experiment or research chip is not the same as a competitive mass-produced modern gaming processor. Advanced fabrication, packaging, memory, and board production remain substantial challenges.
- **Performance versus repairability.** Detachable memory or processor modules may create electrical, thermal, or cost tradeoffs that require original research.
- **Reliability evidence.** A ten-week test cannot substantiate a 50-year operating-life claim. Projections must name their assumptions.
- **Cost.** Open source can reduce some barriers but does not remove scarce manufacturing capacity or guarantee low consumer prices.
- **Frame consistency.** A literal requirement that every frame takes at most 1 ms is more stringent than a high average frame rate, and the actual test conditions must be explicit.

These limitations will be treated as research problems, with partial results published even when the ultimate goals remain unmet.

## 9. Expected Research Outputs

The intended outputs are a sequence of public CPU–GPU system experiments; editable hardware and software source; demonstrations in real applications; measurements collected during gameplay; repair and reliability designs; reusable engineering tools; and an openly accessible history of unsuccessful as well as successful decisions. The project aims to make useful engineering knowledge public regardless of whether the final system reaches the headline performance target.

Over time, the outputs could enable outside engineers to contribute improvements and outside manufacturers to investigate producing competing implementations.

## 10. Conclusion

This project starts with the experience a gamer should be able to have: responsive, consistently smooth, high-quality gameplay on hardware that is affordable, dependable, and repairable. It proposes to pursue that experience by designing the **CPU and GPU as one coordinated computing system**, with the memory, software, and physical hardware treated as part of the same problem.

The ultimate goals—native 1080p gaming at a sustained 1,000 FPS, continuous 24/7 operation, a 50-year service life, straightforward repair, and complete open-source availability—are intentionally ambitious. They are **objectives to investigate**, not specifications already achieved.

The operating principle is simple:

> **Decide why the work matters. Define what the system must accomplish. Research, build, play, learn, and change anything necessary to discover the path. Publish everything we have the right to share.**

## References

1. Open Source Hardware Association (OSHWA). [*Open Source Hardware FAQ*](https://oshwa.org/resources/open-source-hardware-faq/).
2. Rockstar Games. [*Pre-Order Grand Theft Auto VI on June 25*](https://www.rockstargames.com/newswire/article/5171972o3ak5oa/pre-order-grand-theft-auto-vi-on-june-25). June 24, 2026.
3. Epic Games. [*New Fortnite Anti-Cheat Requirements and Legal Action*](https://www.fortnite.com/competitive/rules-guidelines/rules-library/new-fortnite-anti-cheat-pc-requirements-and-latest-legal-action). February 10, 2026.
4. European Commission, Joint Research Centre. [*Analysis and Development of a Scoring System for Repair and Upgrade of Products*](https://publications.jrc.ec.europa.eu/repository/handle/JRC114337). 2019.
5. OpenHW Foundation. [*CORE-V CVA6: Open RISC-V CPU Core*](https://docs.openhwfoundation.org/projects/cva6-user-manual/index.html).
6. Georgia Tech Vortex project. [*Vortex GPU: An Open-Source GPU for Architecture Research*](https://vortex.cc.gatech.edu/).
7. Mesa 3D. [*Mesa Graphics Library Documentation*](https://docs.mesa3d.org/).
8. OpenROAD Project. [*OpenROAD Documentation*](https://openroad.readthedocs.io/en/latest/).
9. Texas Instruments. [*Semiconductor Reliability Testing*](https://www.ti.com/en-us/quality-reliability/reliability/testing).
10. CERN. [*CERN Open Hardware Licence, Version 2*](https://cern-ohl.web.cern.ch/).
