# Install — Claude Code

## Quick install

```bash
# 1. Inject core rules into CLAUDE.md (direct content injection — works on all versions)
cat cognitive-protocol.md >> ~/.claude/CLAUDE.md
```

## What gets loaded where

| File | Destination | Purpose |
|---|---|---|
| `cognitive-protocol.md` | `~/.claude/CLAUDE.md` (appended) | Always-on core rules (~30 lines) |
| `SKILL.md` | `~/.claude/skills/bayesian-reasoning/SKILL.md` | Full reference (loaded on demand) |
| `anti-patterns.md` | `~/.claude/skills/bayesian-reasoning/anti-patterns.md` | Detailed anti-pattern guide |
| `examples.md` | `~/.claude/skills/bayesian-reasoning/examples.md` | Before/after reference |

## Full install (with skill files)

```bash
# 1. Core rules (inject directly into CLAUDE.md)
cat cognitive-protocol.md >> ~/.claude/CLAUDE.md

# 2. Skill files
mkdir -p ~/.claude/skills/bayesian-reasoning
cp SKILL.md ~/.claude/skills/bayesian-reasoning/
cp anti-patterns.md ~/.claude/skills/bayesian-reasoning/
cp examples.md ~/.claude/skills/bayesian-reasoning/

# 3. (Core rules already injected in step 1)
```

## Verify

Ask Claude Code: "What are the bayesian-reasoning cognitive rules you're following?" It should list the five sections from `cognitive-protocol.md`: assign confidence before concluding, update proportionally to evidence strength, decompose and approximate before calculating, focus on high-signal evidence, output self-check.

## Stacking with other cognitive bases

If First Principles or Tacit Knowledge is already injected into `CLAUDE.md`, no changes needed. All protocols load independently. Tacit Knowledge governs output quality; First Principles governs reasoning input quality; Bayesian Reasoning governs uncertainty handling. No conflicts.

## Uninstall

```bash
# Remove the Bayesian Reasoning section from ~/.claude/CLAUDE.md (search for "# Bayesian Reasoning — Cognitive Protocol" header)
rm -rf ~/.claude/skills/bayesian-reasoning
```
