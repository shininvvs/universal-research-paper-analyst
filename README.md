# Universal Research Paper Analyst

A Claude Code skill for understanding research papers **and their implementation code** — in any discipline.

The goal is not to summarize a paper. It is to get you from *"I read it"* to
*"I understand the method, I can follow the code, I could reproduce it, and I can see what is weak."*

It connects the whole chain — research question → prior work → core idea → method → equations →
figures → experiments → limitations → implementation — and when a repository is available, it traces
the **actual execution flow** and maps paper concepts onto real code.

## Install

### Option 1 — Plugin marketplace (recommended)

Inside Claude Code:

```
/plugin marketplace add shininvvs/universal-research-paper-analyst
/plugin install universal-research-paper-analyst@shininvvs
```

You get updates with `/plugin marketplace update`.

### Option 2 — Clone as a personal skill

Available in every directory, updatable with `git pull`.

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/shininvvs/universal-research-paper-analyst.git \
  ~/.claude/skills/universal-research-paper-analyst
```

### Option 3 — Single file

```bash
mkdir -p ~/.claude/skills/universal-research-paper-analyst
curl -fsSL https://raw.githubusercontent.com/shininvvs/universal-research-paper-analyst/main/SKILL.md \
  -o ~/.claude/skills/universal-research-paper-analyst/SKILL.md
```

### Option 4 — Project-scoped

Drop it into a repository so it applies only when working there. Teammates just clone.

```bash
mkdir -p <your-project>/.claude/skills/universal-research-paper-analyst
cp SKILL.md <your-project>/.claude/skills/universal-research-paper-analyst/
```

> **Restart Claude Code after installing.** Skills are read at session start.

## Usage

Invoke it directly with `/universal-research-paper-analyst`, or just ask — it loads on its own when
you are analyzing a paper or a repository.

```
Analyze this paper: https://arxiv.org/abs/XXXX.XXXXX
Which equation does this repo implement, and where?
Explain Figure 3 as a data flow, not as a picture
What do I need to run this myself?
Where would I modify the code to test my own idea?
How does this paper differ from <other paper>?
```

## What it does differently

**Top-down, never line-by-line first.**
Research problem → core idea → method structure → detailed mechanism → equations → experiments →
implementation. Code is read only after you know where it sits in the system. When you ask about a
function, you first learn why it exists, who calls it, what goes in, and what comes out.

**It separates evidence from inference.**
Every important claim is labeled: *stated in the paper* / *verified in the code* /
*reasonable inference* / *unknown*. Inference never gets promoted to fact.

**It does not assume the paper and the code agree.**
Released implementations often diverge from the paper they describe — hardcoded constants, disabled
terms, inverted masks. The skill checks instead of assuming.

**It refuses to invent.**
Tensor shapes, repository behavior, experimental numbers. If a shape depends on runtime
configuration, it says so rather than guessing.

**It does not call standard components novel.**
Genuine contribution, engineering work, and reused existing technique are kept apart.

**It teaches instead of dumping.**
Default level is an intermediate beginner. Explanations deepen progressively rather than opening
with every implementation detail.

## Contents

44 sections covering: goal detection, one-sentence summary, problem definition, prior work, core
contribution, architecture, figure analysis, equation analysis, algorithms, repository structure,
execution entry point, data flow, tensor shape tracking, module classification (standard / modified
/ novel), paper↔code mapping tables, training and inference analysis, experiments, ablations,
limitations, computational cost, reproduction guides, modification guides, a researcher's critical
perspective, and structured paper comparison.

Domain adaptations are included for machine learning, computer vision, NLP and LLMs, generative AI,
reinforcement learning, graph learning, robotics, multimodal AI, systems, algorithms and theory,
mathematics, physics and natural sciences, and biology and medicine — with an explicit instruction
not to force ML-style analysis onto non-ML papers.

## Cost

Roughly 138 tokens always-on per session; about 7.5k tokens when the skill actually fires.

## License

MIT
