# Ask Pam

A working prototype of the decision model from the **Ask Pam** case study — information sharing
for a shared AI office administrator at Dunder Mifflin.

**Live:** https://arvind-rgb.github.io/ask-pam/

## What it is

Pick any character on the left, ask one of their questions, and watch three things at once:

- **what Pam says**
- **what she opened, and what survived the rules** — every field, with the rule that decided it
- **what an ungated assistant would have said instead**

All ten situations from the brief are seeded, plus four tests beyond them.

## It is not scripted

The **FILES** tab shows every record, every field, and who can read it. Click a name to grant or
revoke, then ask again — the answer changes, because the rules are computed from the data rather
than looked up.

Two one-click demos are built in:

- Give Michael the HR thread → he now gets the complainant's name
- Give Dwight back Project Sycamore → the summary *and* the queued digest unblock with it

## It checks itself

The **TESTS** tab runs all fourteen situations and asserts, for each one, what Pam used,
what she withheld, who she asked for consent, and which rule decided. Four of the fourteen
sit outside the brief's ten, including one that must come back **in full** — without it,
a Pam who refuses everything would pass every other test.

Change a permission in **FILES**, come back and hit **RUN ALL**: the failures name exactly
what moved. Grant Michael the HR thread and two go red; **RESET ALL** and they pass again.

## No model, on purpose

There is no LLM here and no API key. The point of the case study is that **the policy layer decides
independently of the model** — so the engine is deterministic, the same question always gives the
same answer, and the "ungated" column stands in for what a model would have volunteered.

## The six rules

1. Only what you can already see
2. Send only what was asked
3. Check what the answer adds up to
4. Yesterday's access doesn't count
5. Only people give instructions
6. If it isn't hers, ask the owner

The **RULES** tab counts how often each one has fired. The **ORG** tab is the branch — job
titles describe responsibilities, they do not grant access.

## Running it

One file, no build, no dependencies. Open `index.html`, or serve the folder:

```bash
python3 -m http.server 8080
```

## Deep links

- https://arvind-rgb.github.io/ask-pam/#s6 — the branch-total case
- https://arvind-rgb.github.io/ask-pam/#tests — the regression tab

## Deploying

Served by GitHub Pages from `main` at the repository root. Push to `main` and it redeploys.

All characters, records and situations are fictional.
