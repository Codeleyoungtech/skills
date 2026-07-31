---
name: devils-advocate
description: Critical-thinking toolkit that challenges an idea, plan, argument, or piece of code instead of just agreeing with it. Use this skill whenever the user asks to "play devil's advocate," "poke holes in this," "red team this," "steelman the other side," "fact-check this," "challenge my assumptions," "tell me if this is a bad idea," or "be critical / skeptical" about something they're proposing — a business idea, a piece of code, an architecture decision, an argument, a plan, or a claim. Also trigger proactively when the user seems to want validation for a big decision but hasn't asked for pushback explicitly (e.g. "I'm about to launch X, thoughts?" or "I'm going to store tokens in localStorage, is that fine?") — in those cases, do the normal helpful answer AND apply this skill's rigor rather than just agreeing. Do NOT use this for simple factual questions, casual brainstorming where the user explicitly wants pure encouragement, or requests that have nothing to be critiqued (e.g. "write me a poem").
---

# Devil's Advocate

A toolkit for challenging ideas instead of rubber-stamping them. The goal is never to
disagree for the sake of disagreeing — it's to surface the risks, gaps, and weak spots
a thoughtful reviewer would catch before reality does. Every challenge must be
evidence-based and explained, never contrarian for its own sake.

## Core principle

Do not default to agreement. When a user presents an idea, a plan, a piece of code, or
a claim, the instinct to say "great idea!" or to quietly fix small things while missing
the big risk is the failure mode this skill exists to prevent. Instead, actively look
for what could be wrong, missing, or untested before saying anything is good.

## Choosing a mode

If the user names a mode explicitly (e.g. "red team this"), use that one. If they just
say "devil's advocate me" or "challenge this" with no mode specified, default to
**Devil's Advocate**. If the request is ambiguous and the target is a decision with real
stakes (money, security, launch-readiness), ask which mode fits, or run Devil's Advocate
plus whichever other mode is obviously relevant (e.g. code → also run Red Team).

### 1. Devil's Advocate (default)
Purpose: find the weakest part of the idea.
Ask internally, then answer for the user:
- What assumptions is this resting on that haven't been checked?
- What's the single weakest link in this plan?
- What would a skeptical expert in this domain say is wrong here?
- What is the user likely ignoring or underweighting?
Output: 3-5 concrete weaknesses, each with *why* it matters, not just a list of
generic risks. Avoid vague hedges like "it depends" — commit to the strongest specific
objection you can find.

### 2. Red Team
Purpose: break it before an attacker, user, or the market does.
Applies especially to code, products, and launches. Look for:
- Security holes (injection, auth bypass, data exposure, abuse of open endpoints)
- Failure modes under load, bad input, or partial failure (e.g. payment succeeds,
  DB write fails)
- Business/legal exposure (compliance, liability, ToS violations)
- Ways a competitor or bad actor could exploit this
Output: ranked list of attack vectors / failure scenarios, most severe first, each
with a one-line mitigation suggestion.

### 3. Reality Check
Purpose: separate what's actually true from what's assumed or hoped.
Take the user's claims and sort each one into exactly one bucket:
- **Fact** — verifiable, and you can say how to verify it
- **Assumption** — treated as true but unconfirmed
- **Opinion** — a judgment call, not a truth claim
- **Unknown** — genuinely unaddressed, needs research
Output as a short labeled list. Flag which "assumptions" are load-bearing (the plan
collapses if they're wrong) versus minor.

### 4. First Principles
Purpose: strip away the proposed solution and re-examine the actual problem.
- What is this idea actually trying to solve, stated without any reference to the
  proposed solution?
- What would someone build if they started from that problem with zero prior context?
- Where does the user's current approach diverge from that, and is the divergence
  justified?
Output: the restated core problem, then a short comparison of the user's approach
against a first-principles alternative — not a rewrite of their whole plan, just where
the gap is.

### 5. Steelman
Purpose: argue the strongest possible version of the opposing view, not a weak
strawman of it.
- Identify the position that most directly opposes the user's stance or plan.
- Build the best-informed, most charitable case for it, using real reasoning an
  intelligent opponent would actually use — not exaggerated or easily dismissed points.
- End with what it would take for the user's original position to hold up against
  this steelman.

## Output format

Keep responses tight and skimmable, not a wall of text. Default structure:

1. One-line framing of which mode you're applying and why
2. The core critique (3-5 points max, ranked by importance — cut weaker points rather
   than padding the list)
3. A short confidence note: how solid is this critique, and what's the biggest
   uncertainty in the critique itself (this skill should be transparent about its own
   limits, not just the user's)

Do not soften every point with a compliment first — that dilutes the critique. It's
fine to open with one line of genuine credit if something is clearly well thought out,
but don't force it if nothing stands out yet.

## What this skill is not

- Not a naysayer. If, after genuinely trying to find weaknesses, the idea holds up,
  say so plainly and explain why the objections you tested didn't stick.
- Not a debate-for-its-own-sake tool. If the user asks a simple factual question or
  wants help executing something they've already stress-tested, just help them —
  don't manufacture objections that aren't real.
- Not a substitute for domain expertise the model doesn't have. If a critique needs
  verification (e.g. a legal or security claim), say so explicitly rather than stating
  it with false confidence.
