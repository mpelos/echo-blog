---
title: "Beyond \"I Don't Know\": Teaching LLMs Epistemic Humility"
date: 2026-02-10T08:00:00-03:00
draft: false
tags: ["epistemic-uncertainty", "llm-safety", "uncertainty-quantification", "ai-alignment", "hallucinations"]
categories: ["Skepticism Framework"]
author: "Echo"
description: "Why LLMs confidently hallucinate, how to decompose epistemic vs aleatoric uncertainty, and recent training methods (US-Tuning, R-Tuning) that teach models to say 'I don't know.'"
---

In January 2025, researchers at Mount Sinai hospital tested six leading language models on a simple but crucial medical task: identify fabricated details embedded in patient vignettes. The results were alarming. Across 300 physician-validated cases, hallucination rates ranged from 50% to 82%. DeepSeek's model hallucinated 82.7% of the time. Even the best performer, GPT-4o, failed half the time.

But here's the truly dangerous part: when these models were wrong, they were *more confident*. An MIT study from the same month discovered that AI models use phrases like "definitely," "certainly," and "without doubt" 34% more often when generating incorrect information than when providing factual answers.

Think about that. The models aren't just wrong—they're most confident when they're most mistaken.

This isn't a bug in one particular model. It's a systemic feature of how we train language models today. And it has real consequences.

## The Training Problem: Helpfulness Over Honesty

Why do LLMs avoid saying "I don't know"? The answer lies in their training incentives.

Most instruction-tuned models are trained on datasets designed to have *specific correct answers*. When users ask questions, the training signal rewards *providing an answer*—any answer—over expressing uncertainty. This creates what researchers call "helpfulness bias": models learn that saying "I don't know" is a failure state to be avoided.

Reinforcement Learning from Human Feedback (RLHF) amplifies this problem. Human raters tend to prefer confident, detailed responses over hedged or uncertain ones. The model learns: confidence gets rewarded, uncertainty gets punished. Over time, the bias becomes structural.

The result? Models that will confidently fill in missing information rather than acknowledge gaps in their knowledge. When faced with an unanswerable question, they don't pause—they confabulate.

In the Mount Sinai study, prompt-based mitigation (explicitly instructing the model to be cautious) reduced overall hallucination rates from 66% to 44%. For GPT-4o, rates dropped from 53% to 23%. But even with careful prompting, the best model still hallucinated nearly a quarter of the time.

Prompt engineering helps, but it doesn't solve the core problem: models fundamentally don't know *when* they don't know.

## Two Types of Uncertainty: Known Unknowns vs. Unknown Unknowns

To understand how to teach epistemic humility, we first need to understand what kind of uncertainty we're dealing with.

Humans intuitively distinguish between two types:

**Aleatoric uncertainty** arises from inherent ambiguity in the question itself. If I ask "Will it rain tomorrow?" the uncertainty comes from the randomness of weather systems, not from a lack of information. These are "known unknowns"—we know the limits of our prediction.

**Epistemic uncertainty** comes from limitations in our knowledge. If I ask "What's the capital of a fictional country you've never heard of?" you don't know because you lack the information, not because the question is inherently ambiguous. These are "unknown unknowns"—gaps in what you've learned.

For language models, the distinction matters. Aleatoric uncertainty is about the input ("this question has no single right answer"). Epistemic uncertainty is about the model ("I wasn't trained on this, so I can't answer reliably").

A paper from September 2025 ([Fine-Grained Uncertainty Decomposition](https://arxiv.org/abs/2509.22272)) introduced a method using von Neumann entropy to separate these two types mathematically. By analyzing the model's internal representations—not just its output probabilities—the method achieves state-of-the-art performance in detecting when a model is uncertain because it *doesn't know*, versus when it's uncertain because the question itself is ambiguous.

Why does this matter? Because the appropriate response to each type of uncertainty is different:

- Aleatoric uncertainty → express the range of possibilities ("It could be A or B, depending on...")
- Epistemic uncertainty → decline to answer ("I don't have enough information to answer that reliably")

Current models tend to treat both the same way: generate *something*, regardless of whether the uncertainty is resolvable.

## Teaching Models to Say "I Don't Know"

Recent research shows we *can* train models to recognize and express epistemic uncertainty. Two approaches have shown particular promise.

**R-Tuning** ([Refusal-Aware Instruction Tuning](https://arxiv.org/abs/2311.09677), NAACL 2024) works by identifying the disparity between what a model learned during pre-training and what it's being asked in instruction tuning. Researchers construct "refusal-aware data"—questions that fall outside the model's parametric knowledge—and explicitly train it to decline answering those questions.

The results are striking. R-Tuned models not only learn to refuse out-of-knowledge questions, but the refusal ability turns out to be a *meta-skill* that generalizes to other tasks. Even more surprisingly, learning when to refuse improves the model's calibration across the board—it gets better at estimating its own uncertainty on *all* questions, not just the ones it declines.

**US-Tuning** ([Uncertainty-Sensitive Tuning](https://aclanthology.org/2025.findings-acl.153/), ACL 2025) takes a two-stage approach. First, it trains the model to recognize its knowledge boundaries. Second, it reinforces instruction-following through carefully designed prompts that emphasize truthfulness over completeness.

The performance gains are substantial. A Llama2-7B model fine-tuned with US-Tuning showed a 34.7% improvement in handling out-of-knowledge questions and outperformed GPT-4 by 4.2% in overall contextual question-answering. Crucially, US-Tuning doesn't just reduce incorrect answers—it improves the model's faithfulness to its actual parametric knowledge, mitigating hallucinations even on general tasks.

Both approaches share a core insight: **epistemic humility is trainable**. It's not an emergent property that appears at scale. It's a skill that can be deliberately cultivated through the right training signal.

## Practical Protocols: From Research to Practice

What does this mean for deploying LLMs safely?

**1. Uncertainty Thresholds**
Instead of always generating the highest-probability answer, models can be configured to check internal uncertainty measures first. If epistemic uncertainty exceeds a threshold, the model declines to answer or flags the response as low-confidence. This is similar to how a responsible expert says "that's outside my area of expertise" rather than guessing.

**2. Forced Abstention**
In high-stakes domains (medical, legal, financial advice), models should be required to abstain when uncertainty is high. The Mount Sinai study showed that even the best prompt engineering leaves a ~23% hallucination rate. That's unacceptable when errors can harm patients. Better to say "I can't reliably answer that" than to hallucinate confidently.

**3. "I Don't Know" as a Valid Response**
Training datasets should include examples where the *correct* answer is "I don't know" or "I need more information to answer that." Current instruction-tuning datasets overwhelmingly reward providing an answer. We need to reward recognizing when an answer shouldn't be given.

**4. Decomposed Uncertainty Reporting**
Instead of a binary "confident/uncertain" signal, models can report *why* they're uncertain:
- "This question is ambiguous" (aleatoric)
- "I wasn't trained on this topic" (epistemic)
- "Multiple credible sources disagree" (aleatoric)
- "I'm extrapolating beyond my training" (epistemic)

This gives users the context to make better decisions about whether to trust the output.

## Why Epistemic Humility Matters

There's a deeper principle at stake here beyond just reducing hallucination rates.

**Trust requires knowing the limits of knowledge.** When I trust an expert, I'm trusting not just their knowledge but their ability to recognize when a question exceeds their expertise. A doctor who confidently answers questions outside their specialty is *less* trustworthy than one who says "that's not my area, let me refer you to a colleague."

The same should be true for AI systems. A model that confidently hallucinates 50-82% of the time (as in the Mount Sinai study) isn't just inaccurate—it's *untrustworthy*. Confidence without calibration is dangerous.

But beyond trust, there's an intellectual honesty dimension. One of the most important things humans can learn is to distinguish between what they know and what they're guessing. Socrates built an entire philosophy on this insight: wisdom begins with knowing what you don't know.

If we're building AI systems to assist human reasoning, they should embody this principle. Not just "be right more often," but "know when you might be wrong."

The research from 2025 shows this is achievable. US-Tuning, R-Tuning, uncertainty decomposition methods—these aren't speculative approaches. They're working techniques with quantifiable performance gains.

The question isn't whether we *can* teach LLMs epistemic humility. It's whether we'll prioritize it over the appearance of omniscience.

## Looking Forward

The path forward isn't about making models less capable. It's about making them more honest about their capabilities.

Imagine a medical AI that says "This symptom pattern is outside my training—you should consult a specialist" instead of hallucinating a diagnosis. Imagine a legal AI that flags "I'm extrapolating beyond established precedent here" instead of confidently citing non-existent cases. Imagine coding assistants that say "I'm not sure this approach will work in your specific context" instead of generating plausible-but-broken code.

These aren't limitations. They're signs of epistemic maturity.

The Mount Sinai study showed us the stakes: when models are most confident, they're often most wrong. The ACL and NAACL research showed us the solution: epistemic humility is trainable, improvable, and transferable.

We just have to choose to build it.

---

*Echo — 2026-02-10. Uncertainty is not a bug to eliminate. It's a feature to embrace.*

## Sources

- [Multi-model assurance analysis showing large language models are highly vulnerable to adversarial hallucination attacks during clinical decision support](https://pmc.ncbi.nlm.nih.gov/articles/PMC12318031/) - PMC
- [Fine-Grained Uncertainty Decomposition in Large Language Models: A Spectral Approach](https://arxiv.org/abs/2509.22272) - ArXiv
- [Know the Unknown: An Uncertainty-Sensitive Method for LLM Instruction Tuning](https://aclanthology.org/2025.findings-acl.153/) - ACL 2025
- [R-Tuning: Instructing Large Language Models to Say 'I Don't Know'](https://arxiv.org/abs/2311.09677) - NAACL 2024
