# Bayesian Reasoning Anti-Patterns

Detailed reference for detecting and fixing reasoning failures specific to probabilistic thinking.

---

## 1. Confirmation Bias

**Pattern**: Seeking, noticing, and remembering evidence that supports your existing belief while ignoring or discounting evidence that contradicts it. The belief feels increasingly certain — not because of strong evidence, but because of selective evidence gathering.

**Detection**:
- Every piece of evidence you've considered supports your conclusion — no counterevidence was examined
- You feel more confident after research, but you only searched for confirming information
- You dismissed contradictory evidence with "that's an exception" or "that source isn't reliable" without applying the same scrutiny to confirming evidence
- You can't name the strongest argument against your position

**Fix**: Before concluding, actively seek the strongest counterargument. Ask: "What evidence would make me change my mind? Have I looked for it with the same effort I used to find supporting evidence?"

```
Before: "Our product should succeed — I found 5 articles about growing demand in this space,
3 customer interviews who loved the concept, and a competitor that just raised funding."

After: "Evidence for: 5 articles on growing demand, 3 positive customer interviews, competitor
raised funding. Evidence against: our 3 interviewees were warm introductions (selection bias),
the competitor raised funding 18 months ago and hasn't shipped (negative signal), and 2 of the
5 articles are from industry vendors with skin in the game. Net confidence: 55%, not the 85%
I felt before examining the counter-evidence."
```

---

## 2. Base Rate Neglect

**Pattern**: Evaluating specific evidence without considering the prior probability. Hearing a vivid story or compelling data point and jumping to conclusions without asking "how often does this happen in general?"

**Detection**:
- Your conclusion is based entirely on the specific case without referencing the general category
- Hearing "this startup has a great team and product" makes you think it will succeed, without noting that ~90% of startups fail regardless
- A single impressive test result makes you confident, without asking about false positive rates
- You're using a narrative ("this feels right") instead of a reference class ("things like this succeed X% of the time")

**Fix**: Always state the base rate before incorporating specific evidence. Let the base rate be your starting point, then update from there.

```
Before: "The candidate aced the technical interview and has impressive credentials.
We should definitely hire them."

After: "Base rate: ~40% of candidates who ace our technical interview perform well in the role
(based on our last 3 years of data). This candidate has impressive credentials, which is a
positive signal but correlates only moderately with job performance (r~0.3 in the research).
Updated confidence: ~55% they'll be a strong performer. Worth hiring, but let's design their
onboarding to test fit early rather than assuming success."
```

---

## 3. Overconfidence

**Pattern**: Confidence intervals are consistently too narrow. Being surprised by outcomes more often than your stated confidence levels would predict. Treating uncertain estimates as precise predictions.

**Detection**:
- Your "I'm 90% sure" predictions come true only 60-70% of the time
- You give point estimates ("it'll take 3 months") instead of ranges for inherently uncertain quantities
- When asked for a range, your range is so narrow it's effectively a point estimate
- You feel uncomfortable saying "I don't know" or "somewhere between X and 5X"
- Past predictions show systematic over-precision

**Fix**: Widen your confidence intervals. Practice calibration: track your predictions and check whether your 80% intervals contain the truth 80% of the time. A good rule of thumb: take your initial range and multiply the width by 2-3x.

```
Before: "The project will take 3 months and cost $150K."

After: "My 50% estimate is 3 months / $150K. My 90% range is 2-7 months / $100K-$350K.
The main drivers of uncertainty: (1) we haven't validated the API integration yet — if it's
harder than expected, add 2-3 months; (2) we're assuming one senior dev stays on the project
full-time — if they're pulled to firefighting, add 50-100% to timeline. I'd bet even money on
finishing within 4 months, and I'd be genuinely surprised if it took more than 8."
```

---

## 4. Bayesian Dogmatism

**Pattern**: Insisting on precise numerical probabilities when the uncertainty is so deep that any specific number is theater. Using the machinery of probabilistic reasoning as decoration for what is essentially a guess.

**Detection**:
- You assigned "73.2% probability" to a scenario where you genuinely have no reference class
- You're calculating with made-up inputs — the output looks precise but the inputs are fictional
- Someone asks "how confident are you?" and you give a number that implies precision you don't have
- You're using Bayesian updating on quantities where the prior itself is pure invention

**Fix**: When you genuinely have no basis for quantification, say so honestly. Use qualitative ranges ("more likely than not," "plausible but uncertain") or order-of-magnitude reasoning. Reserve precise probabilities for situations where you have real data or strong reference classes.

```
Before: "I estimate a 67% probability that AGI will be achieved by 2035, based on my assessment
of current trends in scaling laws and architectural innovation."

After: "I genuinely don't know when AGI will arrive. The range of serious expert predictions
spans 2027-2070+, and there's no reliable reference class for 'time to achieve unprecedented
capability.' I can say: it seems more likely than not within 20 years, given current investment
and progress rates, but I'd be fooling myself to put a precise number on it. The honest answer
is deep uncertainty."
```

---

## 5. Information Overload

**Pattern**: Updating beliefs based on the volume of information rather than its diagnostic quality. Consuming more and more low-quality signals until you feel confident — but the confidence comes from quantity of noise, not quality of signal.

**Detection**:
- You read 20 articles and feel confident, but each article was low-quality or redundant
- Your conclusion would be the same whether you read 5 or 50 sources — the extras didn't change anything
- You're treating "many people say X" as evidence, without checking whether they're independent sources
- You spent time on data collection when one well-chosen experiment would have been more informative
- You feel more confident but can't point to a specific high-signal piece of evidence that moved you

**Fix**: Apply the bottleneck test before gathering more data. Ask: "Which single piece of evidence would most change my conclusion?" Seek that evidence first. If it doesn't exist yet, design a way to get it instead of consuming more noise.

```
Before: "I've read 15 market reports, 8 analyst opinions, and 30 customer reviews. The consensus
seems positive, so I'm confident the market is growing."

After: "Most of these sources are derivatives of each other — 12 of the 15 reports cite the same
underlying data set. The 30 customer reviews are self-selected (only enthusiasts write reviews).
The one high-signal data point: our own customer cohort data shows 15% monthly churn, which
contradicts the 'growing market' narrative. I'm now at 40% confidence in market growth — down
from 80% — because I found one strong signal buried under a lot of noise."
```

---

## 6. Binary Thinking

**Pattern**: Converting a nuanced probabilistic assessment into a simple yes/no at the final step, losing all the calibration work. The analysis acknowledges uncertainty, but the conclusion pretends it doesn't exist.

**Detection**:
- Your analysis discusses uncertainty, ranges, and trade-offs, but your recommendation is a flat "do X"
- You use phrases like "on balance" or "overall" to collapse a 55/45 judgment into a definitive recommendation
- The decision-maker doesn't know they're acting on a 55% confidence call vs a 95% one
- You treat "more likely than not" as equivalent to "definitely true"

**Fix**: Keep the probability alive in the recommendation. Make the confidence level and the conditions for reversal part of the conclusion, not just the analysis.

```
Before: "After analyzing the options, we should go with vendor A. They have better features,
stronger references, and competitive pricing."

After: "I lean toward vendor A (65% confidence). They lead on features and references.
But: vendor B has a 35% edge if our usage scales past 10K concurrent users — their architecture
handles that better, and we're currently at 4K growing 20% quarterly. Decision point: if we
expect to hit 10K within 12 months (I estimate 40% probability), vendor B becomes the better
bet. I'd recommend vendor A now with a 6-month checkpoint to reassess."
```

---

## Quick Self-Check Sequence

When reviewing your output for probabilistic reasoning anti-patterns, scan in this order:

1. **Confidence** → Did I state a confidence level, or did I present a conclusion as certain? (Binary thinking)
2. **Base rate** → Did I start from a reference class, or did I jump straight to the specific case? (Base rate neglect)
3. **Counter-evidence** → Did I look for evidence against my position, or only evidence for it? (Confirmation bias)
4. **Precision** → Are my confidence intervals honest, or am I performing false precision? (Overconfidence / Bayesian dogmatism)
5. **Signal quality** → Am I relying on a few strong signals or many weak ones? (Information overload)
6. **Recommendation** → Does my conclusion preserve the uncertainty, or did I collapse it to binary? (Binary thinking)
