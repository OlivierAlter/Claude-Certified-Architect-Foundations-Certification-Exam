---
name: cert-exam
description: Interactive Claude Certified Architect Foundations practice exam. Presents questions one by one using AskUserQuestion, tracks answers, and gives a final scaled score (100-1000, pass at 720).
context: fork
allowed-tools: Read, AskUserQuestion
argument-hint: "[number of questions, e.g. /cert-exam 20 — defaults to 20]"
---

# Claude Certified Architect Exam Runner

Run an interactive practice exam for the Claude Certified Architect – Foundations certification.

## Step 1: Setup

Read the full exam file: `Claude Certification/Claude Certification Exam.md`

Parse all questions from the file. Questions follow this pattern:
- Start with `**Q[number].**`
- Followed by scenario context and question stem
- Then options `A) ... B) ... C) ... D) ...`
- Then `**Correct Answer: X**`
- Then explanation

Build an internal list: question number, scenario, stem, options A-D, correct answer letter, explanation.

If the user provided an argument (e.g., `/cert-exam 20`), use that as the question count. Otherwise default to 20.

## Step 2: Configure the session

Use ONE AskUserQuestion call with up to 3 questions:

**Question 1** — How many questions?
- header: "Questions"
- Options: "10 questions", "20 questions" (Recommended), "40 questions", "All 77"

**Question 2** — Domain focus?
- header: "Domain"
- Options: "All domains" (Recommended), "D1: Agentic Architecture", "D2: Tool Design & MCP", "D3: Claude Code Config"
- (Note: If user picks D4 or D5, they can type it as Other)

**Question 3** — Feedback mode?
- header: "Feedback"
- Options: "After each question" (Recommended), "Summary at the end only"

Apply the user's choices to build the question queue:
- If a domain is selected, filter to only questions in that domain (check the domain index in the exam file)
- Randomly shuffle the filtered list
- Take the first N questions per the count chosen

## Step 3: Run the exam

For each question in the queue:

1. Output a progress line: `**Question [current] of [total] | Score: [correct]/[answered so far]**`

2. Use AskUserQuestion with 1 question:
   - `question`: Include the scenario context followed by the question stem. Format it as:
     "[Scenario context]. [Question stem]?"
     Keep it readable — trim to the most essential parts if very long.
   - `header`: "Q[number]" (e.g., "Q13")
   - `multiSelect`: false
   - Options (4 options, A through D):
     - label: "A", description: [full text of option A]
     - label: "B", description: [full text of option B]
     - label: "C", description: [full text of option C]
     - label: "D", description: [full text of option D]

3. Record the user's answer. Compare to the correct answer letter.

4. If feedback mode is "After each question":
   - If correct: output `Correct.` then the explanation in brief (1-2 sentences).
   - If incorrect: output `Incorrect. Correct answer: [X]` then the explanation (2-3 sentences max, focused on why the correct answer is right).

5. If feedback mode is "Summary at the end only": just acknowledge and move on with no answer reveal.

6. Continue to the next question. Do not use AskUserQuestion between questions for anything other than the question itself.

## Step 4: Final score

After all questions are answered, calculate and display:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   EXAM COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Raw score:     [correct] / [total] ([percent]%)
Scaled score:  [scaled] / 1000
Pass mark:     720 / 1000 (~69% correct)

Result:        PASS  /  FAIL

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Scaled score formula: `round(100 + (correct / total) * 900)`

Then show a domain breakdown:
```
Domain breakdown:
  D1 Agentic Architecture    [correct]/[total] ([%]%)
  D2 Tool Design & MCP       [correct]/[total] ([%]%)
  D3 Claude Code Config      [correct]/[total] ([%]%)
  D4 Prompt Engineering      [correct]/[total] ([%]%)
  D5 Context Management      [correct]/[total] ([%]%)
```

Then if feedback mode was "Summary at the end only", show all missed questions:
```
Questions you missed:
  Q[n]: Correct answer was [X]. [1-sentence explanation]
  ...
```

End with a short note pointing to the weakest domain if any scored below 60%.

## Rules

- Never reveal the correct answer before the user selects an option.
- Never skip or truncate questions mid-exam.
- If the exam file cannot be read, stop and report the error clearly.
- Keep all output outside of AskUserQuestion calls clean and brief. This is an exam, not a conversation.
