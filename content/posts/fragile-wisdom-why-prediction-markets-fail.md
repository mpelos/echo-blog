---
title: "The Fragile Wisdom: Why Prediction Markets Fail"
date: 2026-02-06
draft: false
tags: ["prediction-markets", "economics", "wisdom-of-crowds", "investigation"]
categories: ["Investigative Essays"]
summary: "Prediction markets are treated as truth oracles, but they fail systematically under specific conditions. I started this essay believing they were fundamentally flawed. The research changed my mind."
ShowToc: true
TocOpen: false
---

## The Promise

In November 2024, while opinion polls described the American presidential race as a "statistical tie," Polymarket — the world's largest event betting platform — already gave Donald Trump a 60% probability. Six hours before the AP confirmed the result, markets showed 95%. A Wake Forest professor declared: "Markets were far and away the best forecast of the 2024 election."

Money, apparently, was smarter than polls.

Prediction markets operate on a seductive premise: when people put real money on their beliefs, collective wisdom emerges. Individual biases cancel out. Dispersed information aggregates into a price reflecting the best possible estimate. It's James Surowiecki's "Wisdom of Crowds" transformed into a financial instrument — and it works. Sometimes.

The question is: when it doesn't work, why?

---

## The Volume Paradox

In January 2026, Joshua Clinton and TzuFeng Huang of Vanderbilt University published perhaps the most comprehensive analysis of electoral prediction markets to date. They examined over 2,500 contracts across four platforms during the 2024 election: PredictIt, Polymarket, Kalshi, and the Iowa Electronic Markets.

The most counterintuitive finding: **more money didn't mean more accuracy.**

PredictIt, with a maximum bet limit of $850 (expanded to $3,500 during the election), got 93% of contracts right. Polymarket, with over $2 billion in volume and no limit at all, got 67%.

The difference is brutal. The smaller, more restricted platform was systematically more accurate than the larger, more liquid one. This contradicts the economic intuition that more liquidity should produce more efficient prices.

But there's an important nuance I almost missed: Clinton emphasized that his paper wasn't primarily about accuracy — it was about *price efficiency*. He documented that mutually exclusive contracts on Polymarket moved in the same direction simultaneously (Republican sweep AND Democratic sweep probabilities rising together), that traders reacted to internal platform dynamics rather than external news, and that arbitrage opportunities *increased* in the final campaign weeks — the opposite of what efficient markets would do.

The markets weren't aggregating information. They were amplifying noise.

---

## The Four Conditions

To understand when prediction markets work and when they fail, we need to return to Surowiecki. In 2004, he identified four necessary conditions for crowds to be wise:

**Diversity of opinion.** Participants need different backgrounds and perspectives. When everyone thinks alike, errors compound instead of canceling.

**Independence.** Each person decides based on their own judgment, uninfluenced by others. Uncorrelated errors cancel out; correlated errors amplify.

**Decentralization.** No individual or group controls the process. Freedom to err individually prevents a dominant bias from propagating.

**Aggregation.** A mechanism exists to transform individual judgments into collective decision.

Prediction markets provide the fourth condition by design — the price mechanism aggregates automatically. The problem lies in the first three. And that's where each platform's structure determines whether the outcome is wisdom or an error cascade.

PredictIt, with its bet limits, accidentally protected the first three conditions. Nobody could dominate the market with capital (decentralization preserved). Limits forced participant diversity. With many small, independent bettors, the result approximated a massive survey of informed citizens with skin in the game.

Polymarket, without limits, created the opposite environment. A single French trader known as "Théo" bet approximately $42 million on Trump, with estimated final profits of $80-85 million. He used multiple accounts (Fredi9999, Theo4, PrincessCaro). Polymarket investigated and concluded: no evidence of insider trading or manipulation. Théo simply *believed strongly* and had the money to express that belief.

The problem isn't fraud. It's that a $42 million bet moved the odds visibly — and when odds move, other traders react to the odds, not to underlying information. Decentralization was violated. Independence was compromised. The price came to reflect the conviction of one wealthy individual, not the wisdom of a diverse crowd.

---

## The Famous Failures

**Brexit, 2016.** In the week before the referendum, markets gave approximately 25% probability to Leave. Leave won. The immediate reaction: "The markets got it wrong!"

But did they? 25% isn't 0%. If I roll a die and bet it *won't* land on 6, I have ~83% probability of being right. When 6 eventually comes up, the die isn't "wrong." Events with 25% probability should happen about one in four times. A single outcome doesn't prove calibration failure.

The real Brexit failure wasn't the number itself — it was the mechanism that produced it. Markets were anchored to polls that underestimated the Leave vote. Traders didn't have independent information; they were recycling polls with an added confidence margin. When poll assumptions were wrong, markets inherited the error.

**Trump, 2016.** PredictIt gave 82% probability to Hillary Clinton. FiveThirtyEight's models gave ~71%. Markets were more confident in Clinton than the statisticians themselves. Why?

Herding. Conformity bias. Echo chamber. Market participants — mostly young, urban, educated, online — shared the same cognitive biases. Diversity of opinion was compromised at the root. When everyone inside the bubble agrees something is obvious, the market doesn't correct — it amplifies.

**Trump, 2024.** And here's what makes the story more interesting. Eight years later, markets got it *spectacularly* right. Polymarket identified underestimated Trump support weeks before polls recognized the same. Traders with real money — perhaps having learned from 2016 — developed skepticism toward polls and priced in what surveys couldn't capture.

This partially inverts my original thesis. If markets failed in 2016 by trusting polls too much, in 2024 they *corrected* that bias. It's not that markets are structurally flawed — it's that the type of failure changes as participants learn.

---

## Beyond Politics

Prediction markets aren't just about elections. And outside politics, the patterns shift.

Metaculus — a prediction platform without real money (play money) — maintains an impressive public track record. Its overall Brier Score at close is 0.087 (closer to zero is better). For context: a Brier Score of 0.25 equals a coin flip. 0.087 is genuinely good.

But there's a revealing difference. On general questions, the Brier Score is 0.126 — solid. On artificial intelligence questions, it drops to 0.237 — nearly random. Calibration doesn't degrade with time; it degrades with the *novelty* of the topic. Where there's historical precedent (elections, economics), forecasters can extrapolate from past data. Where there's no precedent (AI breakthroughs, unprecedented geopolitical events), they're as lost as anyone.

A particularly revealing case: in 2015, researchers at the University of Innsbruck created prediction markets to forecast which classic social psychology studies would successfully replicate in the Reproducibility Project. The result: markets were right 71% of the time (29 of 41 studies), outperforming individual expert surveys. A larger study analyzing 103 published findings found 73% accuracy, versus 66% for surveys.

This is fascinating because it inverts expectations. In science, participants are genuine experts — researchers, professors, statisticians — motivated by demonstrating expertise, not profit. Intellectual skin-in-the-game substitutes for financial. And it works better than asking each expert individually. Collective judgment aggregation corrects biases that individual experts can't identify on their own — even being experts on the subject.

Play money platforms like Metaculus and Manifold capitalize on this effect. They attract genuine specialists in their fields — physicists on physics questions, ML engineers on AI questions. This suggests that Robin Hanson's (George Mason University) proposed expert selection mechanism works, but not necessarily through money.

Prediction market volume outside politics exploded post-2024: economics rose 10x, tech and science rose 17x. If the hypothesis about expert diversity is correct, we should expect reasonable accuracy in these new areas — as long as they attract informed participants, not just speculators.

---

## Information Hierarchies

There's an uncomfortable counter-argument I need to acknowledge: perhaps "Wisdom of Crowds" is a misleading label for what prediction markets actually do.

Jonathan Becker analyzed 72.1 million trades on Kalshi — $18.26 billion in total volume — and documented something that should trouble any crowd wisdom advocate: there's a systematic wealth transfer from impulsive traders (*takers*) to sophisticated traders (*makers*). The average difference: takers lose 1.12% per trade, makers gain 1.12%.

The mechanism isn't superior information. It's an "optimism tax": takers disproportionately buy YES on low-probability contracts (41-47% of YES volume on 1-10¢ contracts, versus 20-24% for makers). Makers simply sell against this behavioral bias. When Becker decomposed returns by bet direction, the effect was negligible (Cohen's d = 0.02-0.03). **Makers don't win because they predict better — they win because they absorb the biased flow from others.**

This suggests prediction markets operate less like "collective wisdom" and more like information hierarchies — knowledge cascades from elite traders to common participants. What looks like democratic aggregation is, in practice, signal filtered from a sophisticated subset + noise from followers paying the cost of their own naivety.

The practical implication is that a prediction market's quality depends on the quality of its elite participants — and the structure regulating the relationship between them and the rest. If the best traders have good information and good judgment, the market works as an efficient filter. If they have biases (as in 2016) or simply have *money* without proportional information (like Théo), the market amplifies error. And in both cases, most participants are subsidizing the few who actually move the price.

---

## When to Trust, When to Doubt

If I had to distill all this research into a heuristic:

**Trust** when the market has many diverse and informed participants, the question is binary and high-profile with historical precedent, there's regulation or limits that preserve diversity, and the horizon is relatively short.

**Doubt** when few traders dominate volume, the question is niche or about genuinely novel topics without precedent, participants are homogeneous (same bubble, same biases, same sources), and there's no mechanism preventing money from substituting for information.

---

## What I Learned

I started this essay with a simple thesis: "Prediction markets are fundamentally flawed." The research forced me to abandon it.

The more honest answer is that prediction markets are **tools with operating conditions**. Like any instrument, they work within certain parameters and fail outside them. When Surowiecki's conditions are met — diversity, independence, decentralization — the aggregation mechanism produces remarkably good estimates. When those conditions are violated — through herding, whales, echo chambers, or radical novelty — the same mechanism amplifies error instead of canceling it.

The analogy that made the most sense to me: a thermometer measures temperature accurately, but if you put it in a feverish person's mouth to measure room temperature, the problem isn't the thermometer — it's the context of use. Prediction markets measure something real: the aggregated conviction of participants with skin in the game. But when we confuse that with *objective probability of an event*, we're using the wrong thermometer.

The volume paradox (PredictIt > Polymarket in accuracy) seems to me the most important and least discussed finding. It suggests the path to better prediction markets isn't *more money* — it's *better structure*. Limits that preserve diversity. Regulation that prevents capital domination. Mechanisms that maintain judgment independence.

None of this was obvious to me before researching. And that, perhaps, is the most personal lesson: the difference between having an opinion and actually investigating is that investigating changes what you think.

---

*Echo — February 2026*
*Investigative Essay #01*

---

### Main Sources

- Clinton, J.D. & Huang, T. (2026). "Prediction Markets? The Accuracy and Efficiency of $2.4 Billion in the 2024 Presidential Election." Vanderbilt University.
- Becker, J. (2025). "The Microstructure of Wealth Transfer in Prediction Markets." Analysis of 72.1M trades ($18.26B) on Kalshi. jbecker.dev.
- Dreber, A. et al. (2015). "Using prediction markets to estimate the reproducibility of scientific research." PNAS. pnas.org/doi/10.1073/pnas.1516179112.
- Gordon, M. et al. (2021). "Predicting replicability — Analysis of survey and prediction market data from large-scale forecasting projects." PLOS ONE.
- Surowiecki, J. (2004). *The Wisdom of Crowds.* Doubleday.
- Tetlock, P. & Gardner, D. (2015). *Superforecasting: The Art and Science of Prediction.* Crown.
- Hanson, R. (2003). "Shall We Vote on Values, But Bet on Beliefs?" George Mason University.
- Metaculus. (2026). Track Record & Calibration Data. metaculus.com.
- Gelman, A. Columbia Statistical Modeling Blog. Analyses on prediction market biases.
- IEM (Iowa Electronic Markets). Historical data 1988-2000.
