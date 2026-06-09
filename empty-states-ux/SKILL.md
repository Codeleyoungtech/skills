---
name: empty-states-ux
description: >
  Apply this skill whenever the user is designing, building, reviewing, or auditing UI that
  involves empty states, zero-data views, first-time user experiences, onboarding screens,
  blank dashboards, "no results" states, error states, or completion/achievement states.
  Trigger this skill for questions about: what to show when there's no content, first-run
  experience design, handling empty search results, skeleton screens and loading-to-empty
  transitions, inbox zero or task completion celebrations, partial states, and component-level
  empty state patterns (tables, cards, feeds, sidebars). Also trigger when the user asks about
  improving activation rate, reducing early churn, or measuring how well their onboarding works.
  Don't wait for the phrase "empty state" — any screen a new user will see first, any list or
  table that can have zero rows, any search that can fail, any dashboard before data exists:
  apply this skill.
---

# Empty States UX — Comprehensive Skill

Empty states are often the **first thing a user ever sees in your product**. A poorly designed one — blank, confusing, broken-feeling — is one of the leading causes of early churn. Most SaaS products lose 80% of new users in the first week, and that window starts the moment someone lands on an empty dashboard.

A well-designed empty state does three things:
1. **Explains why it's empty** — removes confusion, prevents "is this broken?" anxiety
2. **Shows what to do next** — reduces cognitive load, drives activation
3. **Feels intentional, not forgotten** — maintains trust in the product

Read `references/component-patterns.md` for component-level specifics (tables, cards, feeds, sidebars, modals). This main file covers strategy, copywriting, transitions, measurement, and anti-patterns.

---

## The 5 Types of Empty States

### 1. First-Use / Onboarding Empty State
*The user just signed up. There's nothing yet.*

This is your highest-stakes empty state. It determines whether the user activates or abandons.

**Strategy:**
- Lead with **purpose, not absence**. Don't say "You have no projects." Say "This is where your projects live."
- Provide a **single primary CTA** — one action, not three options. Hick's Law: more choices = longer to act.
- Optionally, use a **gamified checklist** (3–5 steps) to guide users through their first session. Progress bars and checkmarks trigger completion psychology.
- For every sub-section of the app that could be empty on first visit, add contextual microcopy — don't let any section look accidentally blank.
- Consider **starter / demo content** for complex products. Showing users what populated data looks like helps them understand the value faster than asking them to imagine it.

**Structure:**
```
[Illustration or icon — optional but helps]
[Headline: what this section is for]
[One-line: what will appear here when they use it]
[Primary CTA button — specific verb]
[Optional secondary: "See an example" or "Watch 60s tour"]
```

**Copy formula:** `[What this space is for] + [What they need to do] + [Why it matters]`
- Example: "Your pipeline lives here. Add your first deal to start tracking revenue."
- Example: "No teammates yet. Invite your team to collaborate on projects."

**Personalization:** If you have their name or role from signup, use it. "Welcome, Ele — let's build your first project." Small but meaningful.

---

### 2. Empty Search Results
*The user searched and got nothing back.*

The user has intent and momentum. A dead end kills both.

**Strategy:**
- Always echo the search term: "No results for **'purple shoes'**"
- Offer a **clickable suggestion**: "Try searching 'shoes' →" — keeps the user moving
- Offer **corrective paths**: check spelling, try fewer keywords, browse a category
- If the product supports it, show **related results** or "people also searched for…"
- For filtered/faceted search: show which filter is causing the problem and offer a one-click "Clear filter" or "Widen search" button
- Never show an empty results list without at least one forward path

**For enterprise/data products:** if a filter combination returns zero rows, don't just show an empty table — highlight which filter is the culprit and offer to remove it.

---

### 3. User-Cleared / Post-Action Empty State
*The user deleted everything, archived all items, or completed all tasks.*

This is emotionally ambiguous — it could be accidental (bulk delete) or intentional (inbox zero). Design for both.

**When the user probably didn't intend to empty it** (e.g., bulk-deleted a list):
- Offer a quick **Undo** action prominently
- Keep the visual calm and non-alarming — avoid making it look like data loss

**When emptying was the goal** (inbox zero, all tasks done, all notifications cleared):
- Treat it as a **win** — this is a celebratory state (see Type 4)
- Don't use the same visual design as the first-use empty state — these are emotionally different moments

---

### 4. Celebratory / Achievement Empty State
*Zero inbox. All tasks done. Everything reviewed.*

This is one of the most underutilized moments in product design. The user earned this state — reward them.

**Strategy:**
- Use positive, specific copy: "You're all caught up!" not just "Nothing here."
- Add a **satisfying animation** — confetti, a character celebrating, a peaceful scene. This is worth the engineering time.
- Make the visual distinct from all other empty states — the user should recognize they've done something, not wonder if a bug wiped their data.
- Gmail's approach is canonical: an illustration of a person reading under sunshine with "You're all done!" — it's a subliminal "go live your life" CTA.
- The goal is to make the user want to earn this state again. It's a retention mechanism.

**Examples of good celebratory copy:**
- "Inbox zero. You're a legend."
- "All tasks complete. Seriously, nice work."
- "Nothing left to review. Go touch grass."
- "You cleared everything. The calm before the storm."

---

### 5. Error / Permission / Offline Empty State
*Content exists but can't be shown.*

This is often treated as an empty state but is actually a distinct UX problem: the content isn't missing, it's blocked.

**Rules:**
- **Never** show a blank screen silently. Always explain the reason.
- Distinguish between: no access (permission error), no connection (offline/timeout), content deleted (gone), and content loading (skeleton — see Transitions section)
- Give a **repair action**: "Request access", "Retry", "Go back", "Sign in again"
- Use calm, non-alarming language — don't make the user feel like they broke something

**Copy by error type:**
| Cause | Headline | Action |
|---|---|---|
| No permission | "You don't have access to this" | "Request access" |
| Network error | "Couldn't load this content" | "Try again" |
| Content deleted | "This item no longer exists" | "Go back" |
| Session expired | "You've been signed out" | "Sign in again" |

---

## Loading → Empty Transitions

This is one of the most overlooked aspects of empty state design. How you go from loading to empty matters.

### The sequence:
```
Request initiated → [Skeleton / Loading state] → Data arrives → [Empty state OR content]
```

Never jump straight from a blank screen to an empty state. Always show a loading indicator first. Otherwise the user can't tell if the app is working.

### Which loading pattern to use:

| Pattern | When to use | When NOT to use |
|---|---|---|
| **Skeleton screen** | Content with predictable structure (cards, tables, lists, feeds) — 1–10 seconds | Form submissions, processing actions, single-button states |
| **Spinner** | Single bounded actions, button states after submission — 2–10 seconds | Full page loads where structure can be previewed |
| **Progress bar** | Long or measurable operations (uploads, exports, batch processing) — 10+ seconds | Anything where duration isn't estimable |
| **Optimistic UI** | Low-stakes, reversible actions (likes, toggles, task completion) — <300ms assumed | Irreversible actions or anything with real failure risk |

### Skeleton → Empty transition rules:
- Match the skeleton structure to what the empty state will look like — don't show 3 skeleton cards then reveal a centered illustration; the layout shift undermines trust
- After confirming empty (data returned, zero results confirmed), transition the skeleton out cleanly — don't let it sit
- Don't shimmer skeletons indefinitely — set a max wait time, then fail gracefully to an error state with a retry option

---

## Component-Level Patterns

See `references/component-patterns.md` for detailed guidance on:
- Data tables with zero rows
- Card grids with no cards
- Activity / notification feeds
- Sidebar navigation sections
- Modals and drawers
- Search bars and autocomplete dropdowns

Quick rules:
- **Tables**: don't collapse to nothing — keep the header row visible, show empty state in the body
- **Card grids**: show 1–2 ghost/placeholder cards with the empty message, to communicate the eventual layout
- **Feeds**: "Nothing here yet" + explain what will appear as activity happens
- **Notification badges**: remove the badge entirely when zero — don't show a "0" badge

---

## Copywriting System

### The 3-part formula (Kinneret Yifrah's framework):
1. **Heading** — what is (or isn't) here
2. **Motivation** — why it matters to the user
3. **Action** — exactly what to do next

**Example:**
- Heading: "No alerts set up yet"
- Motivation: "Alerts keep you updated so you never miss something important"
- CTA: "Create your first alert →"

### Tone by context:
| State | Tone | Avoid |
|---|---|---|
| First use | Welcoming, encouraging | Passive voice, "nothing here yet" |
| Empty search | Helpful, neutral | "Sorry", "unfortunately" |
| Cleared/completion | Celebratory, human | Generic "success" language |
| Error/permission | Direct, calm | Technical jargon, blame |

### Copy rules:
- Second person always: "your", "you" — not "the user" or "users"
- CTA verbs are specific: "Create project", "Add teammate", "Start a search" — not "Get started" or "Begin"
- Headlines under 8 words
- Avoid: "No data found", "Nothing to display", "Empty", "N/A"
- Avoid: exclamation marks on error states; avoid flat tone on celebratory states

---

## Visual / Illustration Guidelines

### When to use illustration:
- First-use states on primary screens — worth investing in
- Celebratory states — animation or illustration elevates the moment
- When the section's purpose isn't self-evident from the headline alone

### When to skip illustration:
- Inline/section-level empty states (e.g., an empty table within a larger page)
- Error states — keep these functional and fast
- Mobile contexts where screen real estate is tight

### Illustration style rules:
- Match your design system — don't use a whimsical illustration in a serious enterprise product
- Monochromatic or single-accent-color illustrations age better than full-color ones
- Size: illustration should take up 30–40% of the empty state vertical space max — don't let it dominate
- Alt text is required for all empty state illustrations

### The biophilia effect:
For pure error/offline states with no action to offer, consider using a calming natural scene as background. Research shows nature imagery reduces user stress and frustration — useful for high-anxiety moments like data loss errors or connection failures.

---

## Mobile-Specific Considerations

- **Thumb zone**: primary CTA must be reachable with one thumb — bottom 40% of screen
- **Pull-to-refresh on empty**: even on an empty feed, pull-to-refresh should work and respond visibly — "Still nothing new" confirms the action worked
- **Screen real estate**: on mobile, skip large illustrations in favor of a well-crafted icon + copy pair
- **FAB (Floating Action Button)**: on mobile, the empty state CTA can be the FAB itself — position it prominently at bottom-right and make it the only call to action visible
- **Swipe-to-delete leading to empty**: if a user swipes away the last item, immediately show the empty state with an Undo option for 4–5 seconds (snackbar pattern)

---

## Partial States

Related to empty states but distinct: a **partial state** is when a screen has some data but key sections are still empty or loading. Rules:

- Don't let partial data feel like the full picture — clearly delineate what's loaded vs. what's still coming
- Use section-level empty states within a populated page (not full-screen empty states) for sub-sections with no data
- Never show totals or summaries that include incomplete data without labeling them as partial — "Showing 3 of ~20 results, loading more…"
- Prioritize loading above-the-fold content first; skeleton below the fold while top content renders

---

## Measurement: How to Know If Your Empty States Are Working

### Primary metrics to track:

| Metric | What it measures | Target signal |
|---|---|---|
| **Activation rate** | % of new users who complete the first key action | Improve from 25–30% baseline toward 40%+ |
| **Time to First Key Action (TTFKA)** | How long from signup to first meaningful action | Shorter = better empty state guidance |
| **Drop-off rate at empty state screens** | % of users who leave from empty state screens | Should decrease after improvements |
| **CTA click-through rate** | % of users who click the empty state CTA | Benchmark per screen type |
| **Day 3 / Day 7 retention** | Are activated users sticking around? | Correlated with quality of first-run experience |

### How to instrument:
- Log a `empty_state_viewed` event with `screen_name`, `state_type` (first_use / search / cleared / error)
- Log `empty_state_cta_clicked` with the same properties
- Compare cohorts: users who clicked the CTA vs. those who didn't — did they activate and retain at higher rates?
- Use session recordings (PostHog, Mixpanel, FullStory) to watch what users do when they land on empty states — look for rage clicks, immediate exits, or confused scrolling

### The business case:
Well-designed empty states improve activation by ~60% (from ~25–30% to ~40%+). Early-activated users have 30–40% higher LTV. Every percentage point of activation improvement compounds into meaningful ARR. Empty states are not cosmetic — they are a growth lever.

---

## Anti-Patterns (What Not to Do)

| Anti-pattern | Why it's bad | Fix |
|---|---|---|
| Truly blank screen | User assumes it's broken | Any message > no message |
| "No data found" | Generic, explains nothing, gives no path | Use the 3-part formula |
| Multiple CTAs in one empty state | Violates Hick's Law, paralyzes action | One primary CTA only |
| Same design for all empty state types | First-use ≠ inbox-zero emotionally | Differentiate by type |
| Illustration without copy | Cute but unclear — user doesn't know what to do | Always pair with a headline + CTA |
| Hiding the empty state behind loading spinners | User waits for content that isn't coming | Transition to empty state cleanly |
| Error state that looks like an empty state | User doesn't know if something went wrong | Visual + copy distinction between error and empty |
| Onboarding tooltips instead of empty state | Tooltips are dismissed, ignored | Embed guidance in the empty state itself |
| Mobile CTAs in the top 60% of screen | Thumb can't reach it | Bottom-position primary actions |

---

## Audit Checklist

Run this against any product or screen:

**Every screen that can have zero items:**
- [ ] Dashboard / home (new user, no data)
- [ ] List views / tables (no rows)
- [ ] Search results (no matches)
- [ ] Activity / notification feed (no events)
- [ ] Inbox / messages (no messages)
- [ ] Settings sections (nothing configured)
- [ ] Completion states (all tasks done, inbox zero)
- [ ] Error / offline / permission-denied states
- [ ] Filtered views that return zero results

**For each screen, verify:**
- [ ] Does it explain WHY it's empty?
- [ ] Does it show WHAT TO DO next (single CTA)?
- [ ] Is the CTA reachable on mobile (thumb zone)?
- [ ] Is there a loading state before the empty state (skeleton)?
- [ ] Does the empty state use the same design system as the rest of the app?
- [ ] Is it emotionally appropriate for the context (celebratory vs. instructional)?
- [ ] Is it instrumented for measurement (events logged)?
- [ ] Does it handle error vs. empty distinctly?
