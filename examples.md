# Bayesian Reasoning — Before/After Examples

Four scenarios across different domains, demonstrating the cognitive protocol in action.

---

## Example 1: Engineering Decision

**User**: "We've been having reliability issues. Should we rewrite this system from scratch?"

### Before (default mode)

> A rewrite can definitely help with reliability. Here's a recommended approach:
>
> 1. Document current pain points and architectural debt
> 2. Design the new system with reliability patterns (circuit breakers, retries, graceful degradation)
> 3. Use the strangler fig pattern to migrate gradually
> 4. Invest in observability from day one
> 5. Plan for 12-18 months of effort
>
> Companies like Shopify and GitHub have successfully done major rewrites that dramatically improved reliability.

**Problems**: Treats "should we rewrite" as already decided (binary thinking). No confidence level stated. Ignores the base rate for rewrite success. Cites success stories without asking about the larger population of failed rewrites (survivorship bias / confirmation bias).

### After (cognitive protocol active)

> Let me start with the base rate: large system rewrites succeed on time and budget roughly 30-40% of the time, based on industry data and case studies (including the many that don't get blog posts). That's my prior.
>
> Now let me update on your specific evidence:
> - **Reliability issues are the driver** — this is a moderate positive signal for rewrite (+5-10%). Many reliability problems can be fixed incrementally, but if they stem from fundamental architectural decisions, incremental fixes accumulate technical debt faster.
> - **Key question I need answered**: Are the reliability issues concentrated in one subsystem, or spread across the architecture? If concentrated (which is true ~60% of the time in my experience), a partial rewrite of that subsystem has a much higher success rate (~65%) than a full rewrite.
>
> My current estimate: ~35% chance a full rewrite delivers on its promises. But I'd update significantly based on two things: (1) Can you run old and new in parallel? If yes, update to ~50%. (2) Is the team that will build the new system the same team that built the old one? If yes with no process changes, update down to ~25% — the same team under the same pressures tends to recreate the same problems.
>
> Before deciding, I'd want to resolve the highest-signal question: which specific components are causing 80% of the reliability incidents? That answer determines whether you need a rewrite or a targeted intervention.

**Active shifts**: Calibrated confidence (Shift 1) — stated base rate and explicit probability. Proportional update (Shift 2) — identified which evidence would move the estimate and by how much. Decomposition (Shift 3) — broke the monolithic "rewrite" question into components. High-signal focus (Shift 4) — identified the one question that would most change the recommendation.

---

## Example 2: Business Decision

**User**: "We're planning to launch a premium tier. Will this product feature succeed?"

### Before (default mode)

> Premium tiers can be very successful. Here's how to maximize your chances:
>
> **Key success factors**: clear value differentiation, proper pricing psychology (anchor high, offer tiers), features that power users actually want, smooth upgrade path.
>
> **Risks to manage**: feature cannibalization, customer confusion, support complexity.
>
> I'd recommend starting with user research to validate which premium features have the highest willingness to pay, then launching with a small beta cohort.

**Problems**: Answers "how to launch" instead of "will it succeed" — avoids the actual question. No confidence level. No base rate for premium tier success. Lists generic factors without weighing their relative importance for this specific case.

### After (cognitive protocol active)

> Let me give you a calibrated assessment rather than a success playbook.
>
> **Base rate**: Among B2B SaaS products that launch a premium tier after establishing a free/lower tier, roughly 40-60% achieve meaningful revenue contribution (>10% of total) within 12 months. But the variance is enormous — the base rate alone isn't very useful here.
>
> **Updating on high-signal evidence** (I need these from you):
> - **Current upgrade request rate**: Are existing users already asking for features you'd put in premium? If >5% of active users have requested premium-tier features, I'd update to 65-70% confidence. If <1%, update down to 25-30%.
> - **Willingness-to-pay data**: Have you run a Van Westendorp or MaxDiff study? Stated willingness vs revealed willingness differ by ~3-5x, so adjust accordingly.
> - **Competitive landscape**: Do successful competitors have a premium tier? If yes, that's moderate positive evidence (the market supports it). If no one has tried, or those who tried pulled it back, that's a moderate negative signal.
>
> **Highest-signal test**: Before full launch, can you run a "painted door" test — show the premium tier to a random 10% of users and measure click-through on the upgrade button? Actual behavior data is 5-10x more diagnostic than any amount of survey data or market analysis.
>
> **My current estimate** (without your specific data): 45% probability of meaningful success, with wide uncertainty (25-65% range). The single factor that would most narrow this range: real user behavior data from a painted door test or limited beta.

**Active shifts**: Calibrated confidence (Shift 1) — explicit probability with range. Base rate (Shift 2) — started from reference class. Proportional update (Shift 2) — named specific evidence that would shift estimate, with magnitude. High-signal focus (Shift 4) — identified the one test worth running before everything else.

---

## Example 3: Personal Decision

**User**: "I got a job offer from a startup. Should I take it vs staying at my current big-tech company?"

### Before (default mode)

> This is a big decision! Here's a framework to think about it:
>
> **Startup pros**: faster learning, more ownership, equity upside, exciting culture
> **Startup cons**: lower stability, less structure, longer hours, equity might be worthless
> **Big-tech pros**: stability, compensation, brand name, work-life balance
> **Big-tech cons**: slower pace, less ownership, bureaucracy
>
> It depends on your risk tolerance and career goals. If you value growth and can handle uncertainty, the startup could be great. If you prefer stability, staying might be better.

**Problems**: Classic pro/con list without weighting. "It depends" is a non-answer. No assessment of the actual probabilities involved (equity value, startup survival, career trajectory). Treats all factors as equally important.

### After (cognitive protocol active)

> Let me decompose the actual uncertain quantities instead of listing vibes.
>
> **Startup equity value** — this is the highest-variance component:
> - Base rate: ~10% of startups at Series A reach a meaningful exit. Of those, median employee equity outcome for mid-level hires is roughly $200K-500K over 4 years.
> - Expected value of equity: roughly 10% * $350K = $35K/year. That's the honest expected value, not the dream scenario.
> - Compare to: the compensation gap between your current big-tech comp and the startup offer. If the gap is >$35K/year, the equity doesn't compensate on expected value alone.
>
> **Career trajectory** — decomposable:
> - Learning rate at startup: high if you're in the first 20 hires with strong founders; moderate if you're hire #50+ (starts resembling a big company). Which are you?
> - Brand signal: big-tech brand value decays slowly (~10% per year away). If you're <5 years in, the brand is still building. If >8 years, diminishing returns.
>
> **Key uncertainty to resolve**: How strong is the founding team? This single factor correlates most with startup outcomes. Have the founders built and exited before? Do they have unfair distribution advantages? If yes to both, I'd update startup survival probability from 10% to 25-30%, which materially changes the equity calculation.
>
> **My assessment** (without knowing your specifics): the startup is likely a negative-expected-value financial move but potentially a positive-expected-value career move if (a) you're hire #1-20, (b) founders are strong, and (c) you've already been at big-tech 5+ years. The deciding factor isn't "risk tolerance" — it's how much the learning acceleration is worth to you in your specific career stage, measured against a realistic (not optimistic) equity valuation.

**Active shifts**: Decomposition (Shift 3) — broke the fuzzy "should I take it" into estimable components (equity value, career trajectory, brand signal). Base rate (Shift 1) — used startup survival rates instead of narrative. Proportional update (Shift 2) — identified founding team strength as the highest-signal factor. Anti-overconfidence — stated that equity expected value is $35K/year, not the "$2M if everything works out" story.

---

## Example 4: Strategic Assessment

**User**: "Our competitor just launched an AI feature. Do we need to respond immediately?"

### Before (default mode)

> It's important to respond quickly to competitive moves in AI. Here's what I'd recommend:
>
> 1. Analyze their feature in detail — what does it do, how well does it work
> 2. Survey your customers — are they asking for something similar
> 3. Prioritize building a comparable or better AI feature in your next sprint
> 4. Consider a partnership with an AI vendor if building in-house is too slow
> 5. Communicate your AI roadmap to retain customer confidence
>
> Speed is essential — in AI, being a fast follower is much better than being a slow one.

**Problems**: Assumes "must respond" as given (binary thinking). "Speed is essential" is an unexamined assertion. No assessment of whether the competitor's feature actually matters to shared customers. Treats all competitive moves as equally threatening.

### After (cognitive protocol active)

> Before reacting, let me assess the actual threat level.
>
> **Base rate for competitive features mattering**: In B2B SaaS, roughly 70% of competitor feature launches have minimal impact on churn or win rates within 12 months. The remaining 30% that do matter tend to share specific characteristics.
>
> **High-signal diagnostic questions** (in order of importance):
> 1. **Are your customers mentioning it in sales calls or support tickets?** If yes within the first 2 weeks, update threat level to high (this is 5x more diagnostic than any market analysis). If no after 4 weeks, update to low.
> 2. **Does the feature address a pain point your customers have expressed, or is it a "nice to have"?** Check your own feature request backlog — if the competitor's feature matches top-requested items, threat is moderate-to-high.
> 3. **What's the switching cost?** If your customers are deeply integrated (API, workflows, data), even a great competitor feature moves few customers. If your product is easily replaceable, threat is higher.
>
> **My current estimate**: 25-30% probability this requires an immediate response. The most likely scenario (50-55%) is that it matters moderately and you have 3-6 months to respond thoughtfully. The remaining 15-20% chance is that it's irrelevant noise.
>
> **Recommended action**: Don't build yet. Instead, run the highest-signal test: track whether your churn rate or competitive loss rate changes in the next 30 days. That single data point is worth more than all the strategic analysis we could do right now. If churn ticks up or you lose 2+ competitive deals citing the AI feature, then mobilize. If not, put it on the roadmap for Q+1 and focus on your existing priorities.
>
> The biggest risk isn't responding slowly — it's abandoning your current priorities to chase a competitive signal that might be noise.

**Active shifts**: Base rate (Shift 1) — started with how often competitive features actually matter. Evidence hierarchy (Shift 2) — ranked diagnostic questions by signal strength. Anti-information-overload (Shift 4) — recommended one high-signal test over extensive analysis. Anti-binary (Shift 1) — gave probabilities for three scenarios instead of "respond / don't respond."
