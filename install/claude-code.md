# Install — Claude Code

## Quick install

```bash
# 1. Copy cognitive protocol to Claude's config
cp cognitive-protocol.md ~/.claude/bayesian-reasoning.md

# 2. Add reference in CLAUDE.md
echo '@~/.claude/bayesian-reasoning.md' >> ~/.claude/CLAUDE.md
```

## What gets loaded where

| File | Destination | Purpose |
|---|---|---|
| `cognitive-protocol.md` | `~/.claude/bayesian-reasoning.md` | Always-on core rules (~30 lines) |
| `SKILL.md` | `~/.claude/skills/bayesian-reasoning/SKILL.md` | Full reference (loaded on demand) |
| `anti-patterns.md` | `~/.claude/skills/bayesian-reasoning/anti-patterns.md` | Detailed anti-pattern guide |
| `examples.md` | `~/.claude/skills/bayesian-reasoning/examples.md` | Before/after reference |

## Full install (with skill files)

```bash
# 1. Core rules
cp cognitive-protocol.md ~/.claude/bayesian-reasoning.md

# 2. Skill files
mkdir -p ~/.claude/skills/bayesian-reasoning
cp SKILL.md ~/.claude/skills/bayesian-reasoning/
cp anti-patterns.md ~/.claude/skills/bayesian-reasoning/
cp examples.md ~/.claude/skills/bayesian-reasoning/

# 3. Register in CLAUDE.md
echo '@~/.claude/bayesian-reasoning.md' >> ~/.claude/CLAUDE.md
```

## Verify

Ask Claude Code: "What are the bayesian-reasoning cognitive rules you're following?" It should list the five sections from `cognitive-protocol.md`: assign confidence before concluding, update proportionally to evidence strength, decompose and approximate before calculating, focus on high-signal evidence, output self-check.

## Stacking with other cognitive bases

If `~/.claude/first-principles.md` or `~/.claude/tacit-knowledge.md` is already referenced in `CLAUDE.md`, no changes needed. All protocols load independently. Tacit Knowledge governs output quality; First Principles governs reasoning input quality; Bayesian Reasoning governs uncertainty handling. No conflicts.

## Uninstall

```bash
rm ~/.claude/bayesian-reasoning.md
rm -rf ~/.claude/skills/bayesian-reasoning
# Remove the @~/.claude/bayesian-reasoning.md line from ~/.claude/CLAUDE.md
```
