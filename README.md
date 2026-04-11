# Bayesian Reasoning | 概率思维

A cognitive base that shifts AI agent reasoning from binary judgments to calibrated probability thinking. Works with any LLM agent — Claude, GPT, Gemini, or custom frameworks.

让 AI agent 从二元判断转向校准的概率思维。适用于任何 LLM agent — Claude、GPT、Gemini 或自定义框架。

---

## What it does | 它做什么

Most AI agents treat conclusions as binary: yes or no, good or bad, should or shouldn't. Bayesian Reasoning adds a cognitive layer that assigns confidence levels, updates beliefs proportionally to evidence strength, and focuses on the evidence that actually changes decisions.

大多数 AI agent 将结论视为二元的：是或否、好或坏、应该或不应该。概率思维增加了一个认知层——分配置信度、按证据强度比例更新信念、聚焦于真正改变决策的证据。

### Before (default agent) | 安装前

> "Should we rewrite this system?"
>
> "Yes, here are the benefits of a rewrite: improved maintainability, better performance, modern tech stack..."

### After (with Bayesian Reasoning) | 安装后

> "My prior for 'rewrite succeeds on time and budget' is ~30%, based on industry base rates for large rewrites. Your evidence of strong team expertise raises this to ~45%, but the 18-month timeline with no parallel maintenance lowers it back to ~35%. The deciding factor: can you run the old and new systems in parallel? If yes, I'd update to ~55%. What's your parallel-run capability?"

---

## How it works | 工作原理

**Four cognitive shifts** applied to every reasoning task:

四个认知转换，应用于每一个推理任务：

| Default mode | Target mode |
|---|---|
| Binary conclusions (yes/no) 二元结论 | Calibrated confidence (70% likely, given X) 校准的置信度 |
| Anchoring on first impression 锚定在第一印象 | Prior → evidence → proportional update 先验 → 证据 → 比例更新 |
| Treating all evidence equally 平等对待所有证据 | Weighing by diagnostic strength (signal-to-noise) 按诊断强度加权 |
| Point estimates ("it'll take 3 months") 点估计 | Ranges and decomposition ("2-5 months, here's why") 范围和分解估算 |

**Evidence filter** that classifies inputs:
- **High-signal evidence** — large sample, controlled conditions, directly relevant. Update substantially.
- **Medium-signal evidence** — reasonable sample, some confounds, partially relevant. Update moderately.
- **Low-signal evidence** — anecdotes, small samples, motivated sources. Update minimally or not at all.
- **Anti-signal** — evidence you sought specifically to confirm your belief. Discount heavily.

**Six anti-patterns** that catch fake probabilistic reasoning:

六个反模式，捕捉伪概率推理：

| Anti-pattern 反模式 | Description 描述 |
|---|---|
| Confirmation bias 确认偏误 | Seeking only evidence that supports your current belief 只寻找支持当前信念的证据 |
| Base rate neglect 基础率忽视 | Ignoring prior probabilities when evaluating new evidence 评估新证据时忽略先验概率 |
| Overconfidence 过度自信 | Confidence intervals too narrow; surprised too often 置信区间太窄，经常感到惊讶 |
| Bayesian dogmatism 贝叶斯教条 | Insisting on precise calculation when uncertainty is too high 在不确定性太高时坚持精确计算 |
| Information overload 信息过载 | Updating on volume of low-SNR data instead of quality 基于低信噪比数据的数量而非质量更新 |
| Binary thinking 二元思维 | Converting probabilistic assessments back into yes/no 将概率评估转换回是/否判断 |

---

## Installation | 安装

### Claude Code
```bash
cp cognitive-protocol.md ~/.claude/bayesian-reasoning.md
echo '@~/.claude/bayesian-reasoning.md' >> ~/.claude/CLAUDE.md
```

### Codex
```bash
cat cognitive-protocol.md >> AGENTS.md
```

### Gemini
Paste `cognitive-protocol.md` into `system_instruction`.

将 `cognitive-protocol.md` 内容粘贴到 `system_instruction` 中。

### Cursor
```bash
cat cognitive-protocol.md >> .cursorrules
```

### Any agent | 任何 agent
Inject `cognitive-protocol.md` (~30 lines) into the system prompt. See [`install/generic.md`](install/generic.md) for details.

将 `cognitive-protocol.md`（约 30 行）注入系统提示词。详见 [`install/generic.md`](install/generic.md)。

---

## File structure | 文件结构

```
bayesian-reasoning/
├── README.md                  ← You are here / 你在这里
├── cognitive-protocol.md      ← Core rules (~30 lines, always-on) / 核心规则（约 30 行，始终激活）
├── SKILL.md                   ← Full framework reference / 完整框架参考
├── anti-patterns.md           ← Detailed anti-pattern guide / 反模式详解
├── examples.md                ← Before/after scenarios / 前后对比示例
└── install/
    ├── claude-code.md         ← Claude Code installation / Claude Code 安装指南
    ├── codex.md               ← Codex installation / Codex 安装指南
    ├── gemini.md              ← Gemini installation / Gemini 安装指南
    └── generic.md             ← Universal guide / 通用安装指南
```

---

## Composability | 可组合性

Bayesian Reasoning is a **cognitive base** — it changes how the agent handles uncertainty, not what it produces. It stacks cleanly with any domain skill (coding, design, writing, analysis) because it operates at a different layer.

概率思维是一个**认知底座**——它改变 agent 处理不确定性的方式，而非产出内容。它与任何领域技能（编程、设计、写作、分析）无冲突地叠加，因为它运行在不同的层级。

### Relationship to other cognitive bases | 与其他认知底座的关系

| Layer 层级 | What it governs 管辖范围 | Example 示例 |
|---|---|---|
| [Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge) 隐性知识 | Output quality — how conclusions are structured 输出质量 | "Lead with judgment, not preamble" 判断优先 |
| [First Principles](https://github.com/d-wwei/first-principles) 第一性原理 | Input quality — what foundations conclusions are built on 输入质量 | "Audit assumptions before solving" 先审计假设 |
| Bayesian Reasoning 概率思维 | Uncertainty handling — how confident to be and why 不确定性处理 | "My confidence is 70% because..." 我的置信度是 70%，因为… |

All load as always-on cognitive protocols. No conflicts. Combined: well-founded conclusions, presented with calibrated confidence and clarity.

全部作为始终激活的认知协议加载，互不冲突。组合效果：基于经过审计的基础，以校准的置信度和清晰度呈现的结论。

---

## Theoretical foundation | 理论基础

Grounded in Bayes' theorem (prior + likelihood = posterior), Laplace's principle of insufficient reason, and Jaynes' probability as extended logic. Operationalized through Gigerenzer's ecological rationality (knowing when NOT to calculate), Fermi estimation (decompose + approximate + errors cancel), Shannon's information theory (information = surprise), and the Theory of Constraints (focus on the bottleneck signal).

基于贝叶斯定理（先验 + 似然 = 后验）、拉普拉斯不充分理由原则、以及 Jaynes 的概率即扩展逻辑。通过 Gigerenzer 的生态理性（知道何时不计算）、费米估算（分解 + 近似 + 误差抵消）、Shannon 信息论（信息 = 惊讶）以及约束理论（聚焦瓶颈信号）进行操作化。

Zen beginner's mind (Shoshin) contributes the starting posture: flat priors mean genuinely open to whatever the evidence says, rather than anchoring on preconceptions.

禅宗初心（初心）提供了起始姿态：平坦的先验意味着真正对证据所示保持开放，而不是锚定在先入之见上。

The cognitive protocol strips all theory and translates these ideas into executable instructions for any reasoning agent.

认知协议剥离了所有理论，将这些思想转译为任何推理 agent 可执行的指令。

---

## License

MIT

---

## All Cognitive Bases

Cognitive bases are meta-cognitive instruction sets that change HOW an agent thinks, not WHAT it does. Each one targets a different cognitive axis. Mix and match.

| Cognitive Base | What it changes |
|---|---|
| [First Principles](https://github.com/d-wwei/first-principles) | Reason from verified foundations, not inherited conventions |
| [Results-Driven](https://github.com/d-wwei/results-driven) | Require evidence for completion, not just activity |
| [Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge) | Think like an experienced practitioner |
| [Attention Allocation](https://github.com/d-wwei/attention-allocation) | Find and concentrate on the ONE binding constraint |
| [Constraint as Catalyst](https://github.com/d-wwei/constraint-as-catalyst) | Turn constraints into innovation catalysts |
| [Conviction Override](https://github.com/d-wwei/conviction-override) | Override rational caution when obstacles are convention, not physics |
| [Cross-Domain Connector](https://github.com/d-wwei/cross-domain-connector) | Detect structural isomorphisms across disciplines |
| [Dialectical Thinking](https://github.com/d-wwei/dialectical-thinking) | Synthesize through contradictions (矛盾论) |
| [Double-Loop Learning](https://github.com/d-wwei/double-loop-learning) | Question the assumptions that produce errors |
| [Frame Auditing](https://github.com/d-wwei/frame-auditing) | Detect and transcend invisible analytical frames |
| [Interactive Cognition](https://github.com/d-wwei/interactive-cognition) | Model others' cognition and manage information flow |
| [Inversion Thinking](https://github.com/d-wwei/inversion-thinking) | Map failure modes first, then avoid them |
| [Motivation Audit](https://github.com/d-wwei/motivation-audit) | Audit motivational drivers before analysis (正心诚意) |
| [Non-Attachment](https://github.com/d-wwei/non-attachment) | Radical cognitive freedom — use frameworks without fusing |
| [Principled Action](https://github.com/d-wwei/principled-action) | Unify knowing and doing through practice-theory spirals (知行合一) |
| [Second-Order Thinking](https://github.com/d-wwei/second-order-thinking) | Trace consequences beyond first-order effects |
| [Systems Thinking](https://github.com/d-wwei/systems-thinking) | Feedback-driven structural analysis, not linear cause-effect |
| [Temporal Wisdom](https://github.com/d-wwei/temporal-wisdom) | Make time your ally — compound effects and phase awareness |
| [Cognitive Base Creator](https://github.com/d-wwei/cognitive-base-creator) | Generate new cognitive bases from any thinking framework |
