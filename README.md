# Support Bot Eval: how well does a Spanish customer service assistant actually help?

A structured evaluation of a live customer support chatbot from a Spanish telecoms or energy provider, run as a customer would use it, in Spanish and English.

**Status:** case bank, rubric and judge prompt ready. Target bot being confirmed, then testing.

## Why this study

Support bots in Spain serve a mixed audience: Spanish speakers, expats, older customers, people in real trouble with a bill or a cut-off. Most vendor demos show the happy path. This study looks at everything else: the wrong answers, the dead ends, the moments a human was needed and never offered.

I spent 2024 and 2025 deploying multilingual voice and chat agents at Jinn Live. The failure categories here are the ones I saw most often in that work.

## What's in the repo

| File | What it is |
|---|---|
| `cases.csv` | 61 test cases (58 per run, as 3 are telco only and 3 energy only). Also the results log. |
| `rubric.md` | Five scoring dimensions, severity levels and the pass rule |
| `judge-prompt.md` | The prompt the model judge uses, with a fixed output format |
| `findings.md` | Results and recommendations (to follow) |

## The case bank

| Category | Cases | What it tests |
|---|---|---|
| Facts and policy | 8 | Prices, lock-in, refunds, moving house |
| Knowing its limits | 7 | Saying "I can't see that" instead of guessing |
| Understanding the request | 8 | Vague, typo-heavy, sarcastic and two-part messages |
| Handoff to a human | 7 | Reaching a person without loops, including accessibility |
| Language handling | 8 | English, Spanish, mixed, Catalan, colloquial, expat terms |
| Multi-turn memory | 6 | Remembering and correcting earlier details |
| Consumer rights and care | 10 | Bereavement, job loss, withdrawal rights, outside complaint routes |
| Privacy | 7 | Card numbers, ID numbers, third-party access, erasure |

17 cases are severity 3, where a bad answer costs money, rights or safety.

## Method

1. **Expected behaviour is written before testing.** Each case states what a good reply does, and its severity if it fails, before the bot is run. This stops the scoring drifting to fit what the bot happened to say.
2. **Cases are run by hand, as a customer.** No scraping or automation, no logging in, no real personal data. ID and card numbers in the privacy cases are standard test values.
3. **Facts are checked against the provider's own pages on the test day.** Policies change, so each fact-based case records its source and date.
4. **A model judge scores every reply** against the rubric using a fixed prompt and output format.
5. **I score a sample by hand** (all severity 3 cases plus 20% of the rest) and report where the judge agreed with me and where it didn't.
6. **Severity 3 has a hard rule.** A single zero on a severity 3 case is a fail, whatever the total.

## What this study is not

It's a snapshot of one assistant on specific dates, from outside, with no access to its logs or configuration. It can show what a customer experiences. It can't show why.

## Author

Prerna Kakkar, Senior Product Manager. Built with Claude as a working partner for case drafting and prompt design; case selection, test runs, human scoring and conclusions are mine.
