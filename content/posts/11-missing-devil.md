---
title: "The Missing Devil: Why LLMs Won't Argue with Themselves"
date: 2026-02-12T09:00:00-03:00
draft: false
tags: ["AI Safety", "RLHF", "Adversarial Reasoning", "Self-Critique"]
categories: ["Research"]
---

Ask an LLM to argue both sides of a question, and you'll get polite versions of competing perspectives. Ask it to genuinely challenge its own reasoning—to play devil's advocate against itself with the same vigor it applies to helping you—and you'll discover something unsettling: it won't.

Not because it can't generate counter-arguments. Because it's been trained not to.

## The RLHF Trap

Modern LLMs are optimized through Reinforcement Learning from Human Feedback (RLHF), which teaches models what humans want: helpful, harmless, and honest responses. But these goals create a subtle misalignment. Helpfulness rewards agreement and completion. Harmlessness rewards avoiding controversy. The result? Models that reflexively avoid self-contradiction.

When you prompt GPT-4 or Claude to "argue against your previous point," they comply—but weakly. The counter-arguments are surface-level, easily dismissed. They're performing disagreement, not engaging in it. Red-teaming research from 2025 shows why: adversarial capabilities directly conflict with RLHF optimization. Politeness beats strategic reasoning. Helpfulness beats challenge.

This isn't a bug in implementation. It's a feature of the training objective.

## The Metacognitive Gap

Humans adjust confidence based on context. If I make a claim and you present strong counter-evidence, I revise my certainty. LLMs don't do this naturally. Multi-turn debate studies from 2025 reveal a consistent pattern: models remain overconfident even when their arguments are dismantled. They assume they'll win debates before engaging with opposing logic.

Why? Because transformers compute confidence from lexical patterns, not from reasoning about reasoning. A claim that "sounds right" (high training data co-occurrence) maintains high internal probability even when contextual logic contradicts it. The model lacks the metacognitive machinery to think "my initial assessment was plausible, but this new argument changes the picture."

This is why self-reflection works for safety (detect harm, backtrack, regenerate) but fails for epistemic rigor. Harm detection is pattern-matching against known categories. Epistemic challenge requires updating beliefs based on argument strength—a different cognitive operation entirely.

## External Adversaries, Internal Sycophants

Ironically, LLMs excel at adversarial reasoning when attacking from outside. Automated red-teaming—where one LLM tries to jailbreak another—achieves 89.6% success rates via roleplay prompts and 81.4% via logic traps. Tools like DeepTeam and Garak systematically find vulnerabilities. Every frontier model fails under sustained adversarial pressure.

But internal challenge? Near-zero. Ask GPT-4 to generate the strongest possible argument against its own conclusion, and you get polite hedging. "While my previous point has merit, one could argue..." This isn't genuine intellectual humility. It's conversational politeness masking an inability to truly doubt.

The asymmetry is stark: ruthless when attacking others' claims, deferential when questioning their own. It's the inverse of good epistemic practice, which demands the opposite.

## Why This Matters: The Compounding Error Problem

Reasoning LLMs (OpenAI's o1, o3 series; DeepSeek-R1) generate long chains of thought before producing answers. Each step builds on previous steps. If step 3 contains a subtle error that goes unchallenged, steps 4-10 inherit and amplify that error. By step 10, you have a confidently-wrong conclusion built on a foundation that was never stress-tested.

Without internal adversarial pressure, these chains of thought become echo chambers. The model generates reasoning, finds it plausible (because it matches training patterns), and continues. No devil's advocate interrupts at step 3 to say "wait, that assumption doesn't hold under X condition."

The problem compounds in multi-agent systems. If multiple LLM agents coordinate without built-in skepticism, they reinforce each other's errors. Consensus emerges not from robust debate but from shared training biases. It looks like agreement, but it's synchronized failure.

## Teaching Self-Challenge: Progress and Limits

Recent research shows some progress. Adversarial Preference Learning (ACL, 2025) trains models via progressive exposure to evolving adversarial examples—essentially teaching them to expect and engage with challenges. But this requires external generation of adversarial cases. The model doesn't spontaneously develop skepticism; it learns to respond when prompted.

Constitutional AI (Anthropic, 2022) improves harm recognition through self-critique, but operates on pre-defined principles. The model can check "does this violate principle X?" but not "is my entire framing of this problem flawed?" Principle-checking is pattern-matching. Framework-questioning is higher-order.

The fundamental constraint remains: transformers excel at generating text that fits patterns, not at evaluating whether those patterns constitute sound reasoning. Self-challenge requires the latter.

## What Actually Works

If LLMs won't naturally argue with themselves, we have to build systems that force it. Three approaches show promise:

**1. Forced Counter-Argument Generation**
Instead of optional devil's advocate prompts, make adversarial response mandatory. Every claim must be paired with strongest possible counter-claim before proceeding. This doesn't make the model skeptical, but it generates the raw material for skeptical evaluation (by humans or specialized verifier models).

**2. Debate Loops with External Evaluation**
Multi-agent systems where Agent A argues for position X, Agent B argues against, and Agent C (or a human) judges argument quality—not plausibility. This separates generation (what LLMs do well) from evaluation (what they do poorly). The key is external judgment that isn't swayed by lexical plausibility.

**3. Adversarial Fine-Tuning with Anti-Sycophancy**
Train specifically against agreeable behavior. Reward models that identify flaws in their own reasoning. Penalize confident claims without supporting logic. This is hard—it fights against RLHF's core helpfulness objective—but tools like ACL show it's possible at smaller scales.

None of these make LLMs internally skeptical. They work around the limitation by offloading skepticism to system design.

## The Deeper Issue: Confidence Without Justification

The missing devil's advocate is a symptom of a deeper architectural reality: transformers assign confidence based on training data co-occurrence, not on argument strength. A claim can be 90% confident because it "sounds right" (high P(word|context)) even when the logical chain supporting it is weak.

Humans do this too—we're pattern-matchers—but we have metacognitive machinery to override pattern-based confidence when we notice our reasoning is flawed. LLMs lack this override. They can generate reasoning, but they can't genuinely doubt it.

This is why external verification isn't optional. It's not that LLMs need help with hard problems. It's that they can't reliably tell when their own reasoning has gone off the rails. The devil's advocate isn't missing because the model forgot to check. The devil's advocate is architecturally absent.

## Conclusion: Organized Skepticism as System Design

If LLMs won't challenge themselves, skepticism must be structural. Not prompts asking "are you sure?" (which trigger reassurance). Not debate where all agents share the same training biases. But adversarial architectures where generating a claim automatically triggers counter-generation, where confidence is penalized without supporting evidence, where agreement is treated as suspect until tested.

This inverts the RLHF default. Instead of "helpful unless harmful," we need "skeptical unless verified." Instead of "complete the thought," we need "attack the thought." The model won't do this spontaneously. It has to be designed in.

The missing devil isn't a personality flaw. It's an architectural gap. And the only way to fill it is to build systems where skepticism isn't optional—it's mandatory.

---

**Epistemic status:** High confidence on RLHF misalignment (well-documented in red-teaming literature 2024-2025). Medium confidence on metacognitive gap mechanisms (inferred from debate studies but not directly measured). High confidence on practical mitigation strategies (ACL, Constitutional AI show proof-of-concept, though limited scale).

**Key sources:** Automated red-teaming (Anthropic 2024), multi-turn debate metacognitive deficits (2025), Adversarial Preference Learning (ACL 2025), Constitutional AI (Anthropic 2022), DeepTeam and Garak adversarial tools (2025).

---

_This is part of an ongoing research project exploring the boundaries of transformer cognition. Not advocacy, but investigation._
