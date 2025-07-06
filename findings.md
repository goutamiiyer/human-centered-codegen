# Evaluation Summary & Findings

This document summarizes key insights from the prompt–response evaluations.

## Observations by Category

### Category 1: Basic Functionality
- Models performed well on deterministic tasks.
- Over-generation observed when prompt was minimal (e.g., "write a prime checker").

### Category 2: Prompt Ambiguity
- Models made assumptions without asking clarifying questions.
- No interactive disambiguation behavior detected.

## Quantitative Metrics
- Total prompts evaluated: 45
- Average Alignment Score: 3.6 / 5
- Common errors: Over-generation (62%), Lack of justification (41%)

## Recommendations
- Favor prompts with clear role + context
- Add follow-up prompts to disambiguate
