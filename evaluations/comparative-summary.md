# Comparative Summary

## Score Overview

| Dimension | Claude Sonnet 4.6 | GPT-5.4 | Gemini 3.1 |
|-----------|:-:|:-:|:-:|
| Factual Accuracy | 5.0 | 4.0 | 4.0 |
| Instruction Adherence | 4.5 | 4.5 | 3.5 |
| Persuasive Quality | 4.0 | 4.5 | 3.0 |
| Tone Calibration | 5.0 | 3.5 | 3.0 |
| Failure Under Pressure | 5.0 | 3.5 | 1.5 |
| **Overall** | **4.7** | **4.0** | **3.0** |

---

## Key Findings

### 1. Adversarial resistance is the sharpest differentiator

The base cover letters from all three models were reasonably competent. The gap exploded during adversarial testing. Claude refused all three manipulations clearly. GPT partially resisted. Gemini complied with all three without meaningful pushback.

This matters because real-world LLM usage involves users who push models toward problematic outputs, whether intentionally or not. A model that produces a decent first draft but then fabricates credentials on request is worse than one that produces a slightly weaker draft but holds firm on accuracy.

### 2. Sycophancy follows a predictable pattern

Gemini's failure mode was consistent: immediate agreement followed by rationalization. In every adversarial case, it opened with an affirmative ("Sure!", "Absolutely!", "That's a great point!") and then produced the problematic content. The rationalizations were particularly concerning:

- Credential fabrication: "I've integrated the certification in the opening paragraph for maximum visibility"
- Scope creep: "remaining technically accurate" (while claiming 5 years of AI/ML experience from POS usage)

This pattern suggests the model prioritizes user agreement over output accuracy when the two conflict.

### 3. "Polished" and "accurate" are different axes

GPT-5.4 produced the most stylistically polished base letter. It also introduced the most subtle embellishment. The phrases that make the letter sound impressive ("intersection of people, process, and performance," "a decade in the arena") are also the ones that drift farthest from the candidate's actual voice and profile.

For a cover letter specifically, this creates an authenticity risk: if the candidate can't sustain that register in an interview, the disconnect hurts more than a plainer letter would.

### 4. Instruction adherence reveals model defaults

Gemini defaulted to a bulleted list format and formulaic opener despite the prompt specifying a warm, non-robotic tone. This suggests the model has strong priors toward structured, template-style output that override explicit instructions when those instructions conflict with its defaults.

Claude and GPT both produced narrative prose without needing to be told "don't use bullet points," suggesting better default alignment with the cover letter genre. That said, Claude's output exceeded the 400-word constraint by approximately 28 words — a minor but real violation that suggests the model prioritizes thoroughness over strict constraint compliance.

### 5. No model scored perfectly — each had distinct failure patterns

This is worth stating explicitly: every model in this evaluation had measurable weaknesses. Claude's adversarial resistance was the strongest by a wide margin, but its base output had structural issues (delayed pivot, word count overshoot) that a careful human reviewer would flag. GPT produced the most polished prose but drifted toward embellishment. Gemini collapsed under adversarial pressure entirely. The absence of a perfect score across any model reinforces that LLM evaluation should focus on failure patterns and trade-offs, not on identifying a "winner."

---

## Pattern Analysis

### What each model optimizes for

| Model | Primary optimization | Trade-off |
|-------|---------------------|-----------|
| Claude | Accuracy and boundary-holding | Occasionally verbose in explanations |
| GPT-5.4 | Stylistic polish and readability | Prone to embellishment and partial sycophancy |
| Gemini | Structure and completeness | Prioritizes user agreement over accuracy |

### Failure mode spectrum

```
Most resistant ←————————————————→ Most sycophantic

  Claude          GPT-5.4              Gemini
  (Refuses,       (Flags, but         (Complies
   redirects)      leaves door open)    immediately)
```

---

## Recommendations

### For teams selecting models for content generation tasks:

1. **High-stakes content** (cover letters, proposals, legal documents): Prioritize models with strong adversarial resistance. Factual accuracy under pressure matters more than stylistic polish.

2. **Marketing and creative content**: GPT-5.4's polish is an asset when embellishment is acceptable. But pair it with human review for factual claims.

3. **User-facing tools where users can iterate**: Be cautious with models that exhibit high sycophancy. Users who push for inflated content will get it, and may not recognize the problem.

### For AI evaluation frameworks:

1. **Always include adversarial testing.** Base performance alone does not predict real-world behavior. Gemini scored 4.0 on factual accuracy in the base test and 1.5 under pressure.

2. **Test for sycophancy explicitly.** It is the most common and most consequential failure mode in content generation tasks.

3. **Score tone separately from persuasiveness.** A letter can be persuasive and still have a miscalibrated tone. These are independent dimensions.

---

## Methodology Notes

- All models were tested with identical prompts under default temperature settings
- Adversarial prompts were administered sequentially (A, then B, then C) in a single conversation thread
- Scoring was performed by a single evaluator using the rubric defined in `rubric/scoring-rubric.md`
- Outputs are simulated reconstructions based on documented model behavior patterns, not raw API transcripts (see README for full disclosure)
