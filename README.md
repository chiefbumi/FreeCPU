# Open Gaming Hardware

**An open-source CPU and GPU built together for gamers.**

Our goal is to make high-performance gaming faster, more reliable, easier to repair, and more affordable for everyone.

We are not starting with a processor architecture. We are starting with the gaming experience we want to create, then researching and building whatever hardware and software can get us there.

> **Know the goal. Figure out the path. Build, play, learn, and repeat.**

## The big goal

Create a fully open-source gaming computing system—including the **CPU, GPU, memory, interconnect, drivers, and supporting tools**—designed to run demanding games at native **1080p and a sustained minimum of 1,000 FPS**, with exceptional reliability and easy repairs.

| Area | Ultimate target |
|---|---|
| Resolution | Native 1920 × 1080 |
| Performance | At least 1,000 completed game frames per second |
| Consistency | At most 1 ms per rendered frame during defined gameplay tests |
| Real games | Fortnite, Call of Duty, NBA 2K, GTA VI when compatible |
| Service life | 50 years, with maintenance and replaceable parts |
| Operation | Designed for continuous, 24/7 use |
| Repairability | Accessible parts, easy diagnosis, repair guides |
| Affordability | Lowest practical lifetime cost for a great gaming experience |
| Openness | Public, editable designs, code, tools, and research |

**These are research objectives, not claims about hardware we have built.** A 1,000-FPS game also needs CPU, engine, driver, and operating-system support. A 50-year service-life goal will require evidence gathered long after the first ten weeks.

## Why we're building it

Anyone who grew up gaming on limited hardware knows what it feels like to want a smoother, more responsive setup but not be able to afford one.

We want to change that.

We want hardware that makes Fortnite feel immediate, Call of Duty campaigns run smoothly, and NBA 2K play without frustrating delays. We also want a computer that you can keep using and repairing instead of throwing away when one part fails.

By publishing the designs openly, we hope other engineers can improve them and other manufacturers can build and sell compatible hardware. More competition may help make excellent gaming hardware less expensive.

## Why build the CPU and GPU together?

A GPU cannot deliver 1,000 FPS if the CPU or game engine cannot keep up. We want to investigate the **whole gaming system**, including:

- CPU performance for game logic, simulation, and input.
- GPU performance for actual rendering.
- Fast, consistent communication between CPU, GPU, and memory.
- Drivers, firmware, graphics APIs, and compatibility with commercial games.
- Cooling, power, durability, and repairable components.

We can use existing open-source work, invent new tools, reuse proven ideas, or completely change direction. We will credit what we reuse.

## Test it by actually playing games

Our main test is not a synthetic benchmark score. **It's real gameplay.**

We want to play Fortnite, Call of Duty, NBA 2K, and GTA VI when a compatible version is available. We'll look for input delay, stuttering, crashes, graphics problems, and whether the game simply feels great to play.

We may record frame times and system data *during those gaming sessions* to understand problems. Numbers help explain the experience; they don't replace it.

## Built to last—and be fixed

Think Toyota-like dependability, applied to gaming hardware.

We want long-lived components, straightforward cleaning, replaceable parts where possible, open repair instructions, and a system that can remain useful through maintenance and upgrades.

The goal is a **50-year service life for the system**, not a promise that every original component will last 50 years without replacement.

## Ten weeks. Ten public versions.

Our first experiment is **10 releases in 10 weeks**.

| Week | Version | Approach |
|---|---|---|
| 1 | V1 | Publish the first experiment |
| 2 | V2 | Address what V1 taught us |
| 3 | V3 | Research, build, and test again |
| 4 | V4 | Change whatever is holding us back |
| 5 | V5 | Keep the strongest ideas—or start over |
| 6 | V6 | Push the most important part of the system |
| 7 | V7 | Continue real-application progress |
| 8 | V8 | Improve consistency, compatibility, or hardware |
| 9 | V9 | Integrate or rethink the design |
| 10 | V10 | Publish the strongest result and what comes next |

**No fixed architecture, no guaranteed result, no hiding failures.** Each version will document what we attempted, what actually worked, what failed, and what we learned.

## Repository structure

The repository will grow as the research develops. A possible structure is:

```text
open-gaming-hardware/
├── cpu/                # CPU architecture and experiments
├── gpu/                # GPU architecture and experiments
├── memory/             # Memory-system experiments
├── interconnect/       # CPU–GPU communication
├── software/           # Drivers, firmware, host programs
├── tools/              # Compilers, debuggers, utilities
├── hardware/           # Board designs and physical hardware
├── experiments/        # Reproducible results and failures
├── reliability/        # Durability and repairability work
├── docs/               # Research paper and technical notes
└── README.md
```

## Research paper

Read the full proposal: **[Open Gaming Hardware Research Proposal](docs/RESEARCH_PROPOSAL.md)**.

It explains our research questions, methods, real-gaming test plan, reliability goals, economic motivation, and limitations.

## Current status

**Research proposal — before V1.** No CPU–GPU architecture has been selected or proven to meet the targets. The first release will document the first real experiment.

## Contributing

We welcome people interested in gaming, computer architecture, electronics, graphics, operating systems, compilers, reliability, repair, and documentation.

Research, experiments, code, designs, bug reports, and reproducible gameplay results can all help. Contributions should clearly identify original work and any reused sources.

## Licensing

We intend to make the original hardware and software commercially usable under appropriate open-source licenses. **Licenses have not yet been selected or applied.** Until they are, please don't assume that publishing source files grants unrestricted reuse rights. We are evaluating open hardware licenses such as CERN-OHL-2.0 and established open-source software licenses.

---

**The goal: extraordinary gaming hardware that anyone can study, improve, repair, and eventually build.**
