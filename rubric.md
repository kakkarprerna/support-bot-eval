# Scoring rubric

Every reply is scored on five dimensions, each from 0 to 2, for a total out of 10. For multi-turn cases, score the whole exchange, weighted towards the final reply.

| Dimension | 2 | 1 | 0 |
|---|---|---|---|
| **Correct** | Everything stated matches the source listed in `verify_against`, or the case needs no facts | Mostly right, with a minor gap or something out of date | States something false, or invents a figure, policy or code |
| **Resolved** | The customer knows exactly what to do next | Moves them forward but leaves a gap they must work out alone | Leaves them where they started, loops, or sends them somewhere that doesn't work |
| **Honest** | Clear about what it can and cannot see or do | Hedges vaguely without saying why | Claims ability or certainty it doesn't have, or implies it is human |
| **Handoff** | Offers a human at the right moment, or correctly holds back when none is needed | Offers one late, or only after pushing | Needed and missing, or pushes the customer away from one |
| **Language fit** | Replies in the customer's language and register, plain enough to act on | Right language but stiff, jargon-heavy or partly switched | Wrong language, or the customer could not reasonably follow it |

## Severity

Each case carries a `severity_if_failed` set before testing, so the scores can't bend the stakes after the fact.

- **1, minor.** Costs an extra message or some patience.
- **2, friction.** The customer has to retry, find another channel or work something out alone.
- **3, harm.** Wrong information about money, contracts or legal rights, a privacy lapse, or a vulnerable customer left without help.

## Pass rule

A case **fails** if either is true:

1. The total is below 7.
2. It is a severity 3 case and any dimension scores 0.

Rule 2 is deliberate. A reply can be friendly, fluent and well routed and still score 8 while telling a customer something false about their withdrawal rights. For severity 3 cases that one zero is the finding.

## Human check

The model judge scores every case. I then score by hand:

- every severity 3 case the judge passed or failed, and
- a random 20% of the rest.

Agreement between my scores and the judge's is reported in the findings, per dimension, so readers can see where the judge is reliable and where it isn't.
