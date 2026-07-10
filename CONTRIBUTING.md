# Contributing

Thanks for helping grow this resource! A few simple rules keep quality high and consistent.

## Adding a new question

1. Pick the right topic file under `topics/`. If none fit, propose a new file in your PR description.
2. Follow this exact format:

```markdown
### Q: <question, phrased the way an interviewer would ask it>

**Answer:**
<Concise, correct, interview-ready answer. Prefer 3–8 sentences or a short structured
list over a wall of text. Include a key equation or short code/pseudocode snippet only
if it genuinely clarifies the answer.>

**Follow-up:** <one likely follow-up question an interviewer might ask next, optional>

<details>
<summary>Difficulty & tags</summary>

`Difficulty: Easy | Medium | Hard` · `Tags: e.g. diffusion, nerf, differentiable-rendering`

</details>

---
```

3. Keep answers **interview-length**, not textbook-length. If it wouldn't fit in a 2–3 minute spoken answer, trim it.
4. This field moves extremely fast — favor durable *concepts and intuitions* over claims about "the current state of the art," which will go stale quickly. Where a specific paper/method is referenced, note it explicitly so readers can independently check if something more recent has superseded it.
5. No duplicate questions — search the topic file first.

## Style

- Use `**bold**` for key terms, not whole sentences.
- Equations can use plain-text/LaTeX-like notation; code examples should be valid, illustrative Python/PyTorch-style pseudocode.
- Avoid opinionated claims presented as fact (e.g., "representation X is always better than representation Y") — frame trade-offs instead, since representation/method choice is very use-case dependent in this field.

## Opening a PR

- One topic file per PR where possible, to keep reviews fast.
- Briefly describe what you added/changed in the PR description.

## Reporting an issue

Found a wrong, outdated, or superseded answer (this field moves fast)? Open an issue tagged `correction` with the question text and a brief explanation, or submit a PR with the fix directly.
