# Proofward

**AI you can leave alone: every decision it makes is provable, and every irreversible step waits for your yes.**

Proofward is a family of seven tools built on two habits. First, every tool answers with something you can check: a receipt of what it did, a checkpoint you can resume from, or a typed claim tied to a source. Second, every tool would rather refuse with a named reason than guess, and anything irreversible (installing software, spending money, publishing) stops and waits for a human yes.

![The Proofward product family](assets/family-sheet.png)

## The seven families

| | Family | What it does |
|:-:|:--|:--|
| <img src="assets/marks/choicegate.png" alt="ChoiceGate mark" width="48"> | [**ChoiceGate**](https://gitlab.com/krahul02004/ChoiceGate)<br>[![ChoiceGate PyPI version](https://img.shields.io/pypi/v/choicegate)](https://pypi.org/project/choicegate/) | When an agent is about to do a task, ChoiceGate picks the single best capability for it: a skill, a local tool, an MCP server, or an integration. It looks beyond what is already installed; if something materially better exists, it surfaces that as an owner-approved choice, with browser or manual work as the explicit last resort. Deterministic receipts, refusal with a named reason, and it never installs or runs anything itself. |
| <img src="assets/marks/runsteward.png" alt="RunSteward mark" width="48"> | [**RunSteward**](https://gitlab.com/krahul02004/RunSteward)<br>[![RunSteward PyPI version](https://img.shields.io/pypi/v/runsteward)](https://pypi.org/project/runsteward/) | Lets a developer hand an agent work too big for one sitting and walk away: queued tasks with a spending cap, checkpoints, resume after usage-limit resets, and a reviewable morning report. Bundles Claude Carry, the overnight runner. |
| <img src="assets/marks/cairnspan.png" alt="Cairnspan mark" width="48"> | [**Cairnspan**](https://gitlab.com/krahul02004/Cairnspan)<br>[![Cairnspan PyPI version](https://img.shields.io/pypi/v/cairnspan)](https://pypi.org/project/cairnspan/) | Lets one local coding agent hand a bounded task to another (Claude Code and Codex, each through its own logged-in client, no shared keys), with fail-closed launchers and a receipt for every run. |
| <img src="assets/marks/stormworthy.png" alt="StormWorthy mark" width="48"> | [**StormWorthy**](https://gitlab.com/krahul02004/StormWorthy)<br>[![StormWorthy PyPI version](https://img.shields.io/pypi/v/stormworthy)](https://pypi.org/project/stormworthy/) | A research engine that argues with itself before it answers: an adversarial refuter, typed claims verified against cited sources, and honest abstention when the evidence is thin. |
| <img src="assets/marks/rigwright.png" alt="Rigwright mark" width="48"> | [**Rigwright**](https://gitlab.com/krahul02004/Rigwright)<br>[![Rigwright PyPI version](https://img.shields.io/pypi/v/rigwright)](https://pypi.org/project/rigwright/) | A workshop for authoring and testing the small skill files agents run on: one measurable outcome per skill, its own eval set, and generated packaging for both Claude Code and Codex. |
| <img src="assets/marks/pixelhelm.png" alt="PixelHelm mark" width="48"> | [**PixelHelm**](https://gitlab.com/krahul02004/PixelHelm)<br>[![PixelHelm PyPI version](https://img.shields.io/pypi/v/pixelhelm)](https://pypi.org/project/pixelhelm/) | Makes an agent design UI the way a team does: generate candidates, render them in a real browser, judge them against accessibility gates and an honesty floor (missing data shows as unknown, never as a fake zero), repair, repeat. |
| <img src="assets/marks/releasebench.png" alt="ReleaseBench mark" width="48"> | [**ReleaseBench**](https://gitlab.com/krahul02004/ReleaseBench)<br>[![ReleaseBench PyPI version](https://img.shields.io/pypi/v/releasebench)](https://pypi.org/project/releasebench/) | Walks a repo from private to public without a public mistake: health audit, secret scan, governance files, README polish, and release prep, with each step stopping at a reviewable result. |

## How the pieces fit

This is the canonical topology used at both Proofward entry points.

[Rigwright](https://gitlab.com/krahul02004/Rigwright) authors the small skill files agents run on. [ChoiceGate](https://gitlab.com/krahul02004/ChoiceGate) picks which capability runs for a given task; it binds to an owner-accepted capability registry rather than managing capabilities itself. [RunSteward](https://gitlab.com/krahul02004/RunSteward) governs long unattended runs and ingests ChoiceGate's receipts. [Cairnspan](https://gitlab.com/krahul02004/Cairnspan) is the transport when a bounded task has to cross from one agent to another. [StormWorthy](https://gitlab.com/krahul02004/StormWorthy) verifies claims against cited sources, and [PixelHelm](https://gitlab.com/krahul02004/PixelHelm) vendors its engine to judge design briefs. [ReleaseBench](https://gitlab.com/krahul02004/ReleaseBench) is the exit door: the checked path from private work to a public repo.

```mermaid
flowchart LR
    RW[Rigwright<br>authors skills] --> CG[ChoiceGate<br>picks what runs]
    REG[owner-accepted<br>capability registry] -. binds to .-> CG
    CG -- receipts --> RS[RunSteward<br>governs long runs]
    RS -- tasks that cross agents --> CS[Cairnspan<br>cross-agent transport]
    SW[StormWorthy<br>verifies claims] -. verification engine .-> PH[PixelHelm<br>judges design briefs]
    RS --> RB[ReleaseBench<br>exit door to public]
```

## Start here

Start with [StormWorthy](https://gitlab.com/krahul02004/StormWorthy) and [Cairnspan](https://gitlab.com/krahul02004/Cairnspan): one shows the proof discipline, the other shows the handoff discipline.

## License

MIT. See [LICENSE](LICENSE).
