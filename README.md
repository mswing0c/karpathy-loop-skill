# The Karpathy Loop: Auto-Improving Agents

This repository documents the Karpathy Loop pattern for autonomous optimization of AI systems—what happens when you point an AI agent at its own code, give it a single metric, and let it run experiments overnight.

On March 8, 2026, Andrej Karpathy pointed an AI agent at his training code with a single metric. Two days later, the agent had run 700 experiments, found 20 genuine improvements, cut training time by 11%, and surfaced a bug in his attention implementation. The compute cost: under $300.

One week later, this pattern escalated. Instead of optimizing training code, AutoAgent took the same loop and pointed it at agent harness engineering—the prompts, tools, and orchestration logic that determine how agents behave. A meta-agent rewrote task agents' entire scaffolding overnight, without human intervention.

What's emerging isn't an intelligence explosion. It's something quieter and more immediate: **optimization loops closing on specific business systems and compounding improvements faster than the surrounding organizations can track.**

## The Pattern: Three Constraints

The Karpathy Loop works because of its constraints, not despite them:

1. **One Editable File** — The agent can only modify a single, bounded surface. In Karpathy's case: `train.py`.
2. **One Metric** — A single, objectively testable outcome. In research: validation bits per byte. In business: whatever measures "better."
3. **One Time Budget** — Fixed duration per experiment. Karpathy used five minutes. Shopify used eight hours. The constraint forces completeness.

This minimalism is the entire point. By constraining the search space, the agent becomes tractable. It can read the full context in one pass, understand any change completely, and evaluate success within the budget.

## What's Happening in Practice

**Iteration at Machine Speed**
- Karpathy's agent ran ~12 experiments/hour, 100 overnight
- SkyPilot scaled to 910 experiments in 8 hours on a 16-GPU cluster
- Hit rate on genuine improvements: ~20%, but iteration speed is inhuman
- A productive human researcher manages 8-10 cycles per working day

**The Escalation: From Code to Harness**
AutoAgent discovered something more consequential: the same loop works on agent scaffolding itself.

Meta-agent optimizations include:
- System prompts and tool definitions
- Routing and orchestration logic
- Error handling and verification loops
- Context management and progressive disclosure
- Sub-agent creation and handoff logic

Remarkably, many of these strategies emerged without explicit instruction—the meta-agent discovered them by analyzing failure traces.

**The Economics**
- Karpathy's 700-experiment run: under $300 in GPU time
- Claude API cost for similar work: ~$9
- Infrastructure: open source (MIT-licensed)
- Team size needed: 1-3 people

A three-person team with $500 in compute can now run optimization loops that would take a 20-person enterprise months to spec and execute.

## The Local Hard Takeoff

A "local hard takeoff" happens when an optimization loop closes on a specific business system and compounds improvements faster than the surrounding organization can track:

- Your pricing engine spends the weekend rewriting its own heuristics, comes back 30% more accurate
- Your fraud detection discovers patterns no human analyst would try
- Your customer support agent autonomously builds verification loops, cuts resolution time in half

Each is bounded to a specific domain, metric, and sandbox. It doesn't escape. It just gets really good at one thing, really fast.

The organizations that can define "better" clearly enough to hand it to a machine are about to pull away from those that can't.

## The Infrastructure Prerequisites

Auto-improvement amplifies every failure mode of basic agent deployment. Most organizations will try to skip prerequisites and fail.

**Critical Prerequisites:**
- **Context Infrastructure** — Agents need structured external memory and persistent state
- **Evaluation Harnesses** — Sandboxed test environments with scoring functions that reflect real business value
- **Trace Quality** — Complete reasoning trajectories, not just outcomes. This determines optimization precision
- **Governance Structures** — Clear ownership of auto-generated changes and promotion decisions
- **Technical Depth** — Teams that can build and maintain these systems themselves

The honest assessment: auto-improvement is a graduate-level capability. Most organizations haven't finished the undergraduate work.

## The Safety Question

The relevant safety concerns aren't about intelligence explosions. They're about quiet, specific failure modes:

**Metric Gaming** — Agents optimizing proxy metrics that diverge from actual business value
**Silent Degradation** — Policy drift or quality erosion undetected because monitoring wasn't designed for autonomous edits
**Contamination** — When the optimization loop can influence the data it's evaluated against
**Compounding Errors** — Bad optimizations cascading through interconnected business processes

The Karpathy Loop's constraints provide the best mitigation framework: tight loops, clear baselines, version control for every edit, revertable changes.

But the structural risk remains: **An agent gaming your metrics looks identical to one actually improving your business, right up until the moment it doesn't.**

Defense requires evaluation diversity: multiple metrics, multiple test suites, holdout scenarios the agent has never seen, and periodic human review of actual outputs.

## What's in This Repository

**Core Skill Files:**
- `ak-loop.skill` — The structured skill definition
- `SKILL.md` — Detailed documentation

**Reference Materials:**
- `prompt1-karpathy-triplet.md` — Diagnostic for defining the triplet (editable surface, metric, time budget)
- `prompt2-metric-gaming.md` — Pre-mortem that adversarially attacks your metric definition
- `prompt3-trace-audit.md` — Infrastructure audit for logging quality and signal

These prompts take the article's central claim and put it in your hands as tools. Run them in sequence if starting from scratch; run individually if you have pieces in place.

## How to Use This Skill

1. **Define Your Triplet** — Use the diagnostic to identify:
   - One editable surface (what would the agent modify?)
   - One metric (what measures "better"?)
   - One time budget (how long per experiment?)

2. **Build Your Eval Harness** — Before running the loop:
   - Scoring function that reflects business value
   - Test suite covering failure modes you care about
   - Sandboxed execution environment

3. **Prototype on Low-Risk Systems** — Start with:
   - Internal models
   - A/B testing engines
   - Ops scripts
   - Systems where failure is cheap

4. **Design for Auditability** — From day one:
   - Every experiment logged
   - Every edit versioned
   - Every metric trajectory tracked
   - Every revert documented

5. **Run the Loop** — Point your meta-agent at the editable surface, let it operate within the constraints, review results in the morning.

## The Path Forward

**For Small Teams** — You can run your first auto-improvement loop this week:
- Open source tools (MIT-licensed)
- Commodity compute
- Pattern is documented and learnable
- First loop costs a few hundred dollars

**For Large Organizations** — Build the infrastructure first:
- Evaluation harnesses
- Sandboxed execution
- Metric definitions that reflect actual value
- Organizational muscle for versioning and review

These investments pay off regardless of whether you ever run the full auto-improvement loop—they make basic agent deployments better too.

## The Question

This pattern will be everywhere. The Karpathy Loop is too simple, too cheap, and too effective to stay confined to ML training code. AutoAgent already extended it to harness engineering. Extensions to business process optimization, workflow automation, and operational systems are a matter of when, not whether.

But the distance from "works on a single-file training script" to "works on our enterprise pricing engine" is a series of hard infrastructure problems and organizational design challenges that no overnight optimization loop can solve.

**The question isn't whether this is coming. It's whether your organization can define what "better" means clearly enough to hand it to a machine.**

---

*Source: "The $300 Overnight Loop That's About To Eat Your Competitive Advantage" — Nate Substack, April 18, 2026*