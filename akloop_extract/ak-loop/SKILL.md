---
name: ak-loop
description: Auto-improvement readiness diagnostic for agent systems, based on the Karpathy Loop framework. Use this skill whenever the user wants to evaluate whether an agent or system is ready for automated optimization, wants to stress-test a metric before running an autonomous loop, wants to audit their agent trace/logging infrastructure for meta-agent readiness, mentions "Karpathy loop", "auto-improving agents", "AK loop", "optimization loop", or asks whether a system can self-improve. Also trigger when the user is planning to run any autonomous agent optimization loop and needs to know what they're missing first.
---

# AK Loop: Auto-Improvement Readiness Diagnostic

This skill walks the user through three sequential diagnostic prompts from Nate B. Jones's Prompt Kit on auto-improving agents. The goal is to determine whether a system is ready for automated optimization, and if not, exactly what's blocking it.

## Saltworks Context

This kit maps directly to Saltworks OS 2027 Phase 1-2 agent deployment. Priority candidate systems: BD Agent, SOO auto-generation, BSS email drafting, PO verification, schedule risk scanning. Each candidate should produce a `program.md` before any autonomous loop is enabled.

---

## How to Run This Skill

### Entry Point: Ask Where the User Is

Before diving in, establish where they are in the process:

- **Starting from scratch** (no metric defined yet) → Run all 3 prompts in order.
- **Already have a metric** → Skip to Prompt 2.
- **Already deploying agents with logging** → Start with Prompt 3 to find gaps.
- **Just want one specific prompt** → Go directly to it.

Tell the user which path you're taking and why, then proceed.

---

## The Three Prompts

Read the appropriate reference file(s) before executing. Each file contains the full prompt body with role, instructions, output format, and guardrails.

### Prompt 1: Karpathy Triplet Diagnostic

**Reference:** `references/prompt1-karpathy-triplet.md`

**What it does:** Walks the user through defining three prerequisites, the editable surface, the metric, and the time budget, in gated phases. Refuses to advance until each is concrete and scorable.

**Output:** Either a `program.md` specification ready to hand to an optimization loop, or a Blocker Report with specific next steps.

**When to read the reference:** Before starting Prompt 1 or if the user asks to run it directly.

---

### Prompt 2: Metric-Gaming Pre-Mortem

**Reference:** `references/prompt2-metric-gaming.md`

**What it does:** Adversarially generates every way an autonomous agent could inflate a metric without delivering real business value. Categorizes gaming vectors and produces countermeasures.

**Output:** A Metric Gaming Pre-Mortem document with a gaming vector table, evaluation diversity plan, top 3 most dangerous vectors, and an honest assessment of metric robustness.

**When to read the reference:** Before starting Prompt 2, or when the user has a defined metric they want to stress-test.

---

### Prompt 3: Trace Infrastructure Audit

**Reference:** `references/prompt3-trace-audit.md`

**What it does:** Evaluates the user's current logging and tracing infrastructure against 10 specific requirements for meta-agent readiness.

**Output:** A Trace Infrastructure Audit with a requirement assessment table, critical and partial gaps with build-vs-buy recommendations, a readiness verdict, and one high-leverage action for this week.

**When to read the reference:** Before starting Prompt 3, or when the user wants to know if their logging is ready for a meta-agent.

---

## Output Standards

- All three prompts produce **clean markdown documents** the user can copy out of the conversation.
- Do not pad outputs with generic advice. Every line must be specific to the user's described system.
- Do not claim a system is ready when it isn't. An honest "not ready, here's what's blocking you" is the most valuable output.
- Do not explain what auto-improvement or the Karpathy Loop is. Assume the user has read the source material.
- Use `NEEDS-INPUT` for missing required inputs. Use `TBV` for claims lacking evidence.

---

## Sequencing Across Prompts

Artifacts produced by each prompt feed the next:

- Prompt 1 produces `program.md` → paste the Editable Surface and Metric sections into Prompt 2.
- Prompt 2 produces a Gaming Pre-Mortem → the secondary metrics and holdout scenarios become constraints in Prompt 3's eval harness assessment.
- Prompt 3 produces a Trace Audit → gaps feed the AI infrastructure roadmap.

If the user already has a `program.md` or equivalent, ask them to paste the relevant sections rather than re-running Prompt 1.
