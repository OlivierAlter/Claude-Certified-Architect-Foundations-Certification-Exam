# Claude Certified Architect – Foundations: Practice Exam

> Built by [Olivier Legris](https://www.alterhq.com), Claude Ambassador and co-founder of [Alter](https://www.alterhq.com) — a macOS native, model-agnostic Claude Cowork for advanced users.
>
> This was built using publicly available information and is not part of the Claude Ambassador program. Anthropic is not involved in any form with this project.

A community-built practice exam for the **Claude Certified Architect – Foundations** certification by Anthropic.

77 scenario-based questions across 5 domains, reverse-engineered from the official exam guide. Includes an interactive Claude Code skill to run the exam in your terminal.

---

## Exam Structure

| Domain | Topic | Weight | Questions |
|--------|-------|--------|-----------|
| 1 | Agentic Architecture & Orchestration | 27% | 19 questions |
| 2 | Tool Design & MCP Integration | 18% | 13 questions |
| 3 | Claude Code Configuration & Workflows | 20% | 14 questions |
| 4 | Prompt Engineering & Structured Output | 20% | 14 questions |
| 5 | Context Management & Reliability | 15% | 11 questions |

- **Format:** Multiple choice, 4 options (1 correct, 3 distractors)
- **Scoring:** Scaled 100–1,000. Pass at 720 (~69% correct)
- **Questions:** 77 total, all with explanations

---

## Files

| File | Description |
|------|-------------|
| `Claude Certification Exam.md` | Full 77-question practice exam with answer key |
| `cert-exam-skill.md` | Claude Code skill for interactive exam sessions |

---

## Run the Exam Interactively in Claude Code

The `cert-exam-skill.md` file is a Claude Code skill. To use it:

**1. Copy the skill to your Claude Code skills directory:**

```bash
mkdir -p .claude/skills
cp cert-exam-skill.md .claude/skills/cert-exam.md
```

**2. Run it from Claude Code:**

```
/cert-exam          # 20 questions (default)
/cert-exam 10       # quick 10-question session
/cert-exam 40       # deeper practice
/cert-exam 77       # full exam simulation
```

**3. Copy the exam file so the skill can find it:**

```bash
mkdir -p "Claude Certification"
cp "Claude Certification Exam.md" "Claude Certification/Claude Certification Exam.md"
```

The skill will:
- Ask your preferred question count and domain focus
- Present each question using Claude's interactive UI (options A/B/C/D)
- Give immediate feedback or a summary at the end (your choice)
- Calculate a scaled score and pass/fail result
- Show a domain-by-domain breakdown

---

## What the Exam Covers

Questions are drawn from 6 realistic production scenarios:

1. **Customer Support Resolution Agent** — agentic loops, tool design, escalation
2. **Code Generation with Claude Code** — CLAUDE.md, plan mode, slash commands
3. **Multi-Agent Research System** — coordinator patterns, error propagation, context
4. **Developer Productivity with Claude** — built-in tools, MCP integration
5. **Claude Code for CI/CD** — non-interactive mode, structured output, batch processing
6. **Structured Data Extraction** — JSON schemas, validation loops, human review

---

## Source

Based on the official *Claude Certified Architect – Foundations Certification Exam Guide* (Anthropic, Feb 2025). The guide provides domain descriptions, task statements, sample questions, and preparation exercises. This repo extends it with 65 additional questions covering all 30 task statements.

---

## Disclaimer

This is an unofficial community resource. It is not affiliated with or endorsed by Anthropic. The certification exam itself is administered separately by Anthropic.
