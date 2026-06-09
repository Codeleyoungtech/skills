# Component-Level Empty State Patterns

Reference file for `empty-states-ux` skill. Read this when the user is working on a specific component type.

---

## Data Tables

Tables are the most common place empty states are botched — either the entire table disappears or a raw "No records" appears in a collapsed space.

**Rules:**
- **Always keep the header row visible** — it orients the user to what will be in the table when populated
- Show the empty state message in the table body, spanning all columns
- If the table has pagination controls, hide them when empty (don't show "Page 1 of 0")
- If the empty state is caused by active filters, show which filter is responsible and offer a "Clear filters" button inline

**Structure:**
```
[Table header: Column A | Column B | Column C]
[Empty body spanning full width]
  [Icon — optional]
  "No [items] yet"
  [What will appear here]
  [CTA button — if applicable]
```

**Filter-caused empty table:**
```
[Table header visible]
[Body:]
  "No results match your current filters"
  [Highlighted filter chips showing active filters]
  [Button: "Clear all filters"]
```

**Copy examples:**
- "No transactions yet. Your payment history will appear here."
- "No team members found. Try a different search or invite someone new."

---

## Card Grids

Card grids (dashboards, project lists, product catalogues) benefit from showing the **shape** of what's coming, even when empty.

**Rules:**
- Show 2–3 **ghost/placeholder cards** at reduced opacity — this communicates the layout and sets expectations
- OR show a centered empty state with an illustration that visually suggests cards/items
- The "Add your first X" button should be styled similarly to how a real card would look if it had a "+" action — this builds muscle memory for future use
- On mobile, a single centered empty state is fine (no ghost cards needed)

**Structure option A — ghost cards:**
```
[Ghost card 1 (opacity 20%)] [Ghost card 2 (opacity 20%)] [Ghost card 3 (opacity 20%)]
                    [Centered: "No projects yet"]
                    ["Create your first project" button]
```

**Structure option B — centered illustration:**
```
[Illustration: suggests multiple items/collection]
"Your projects will appear here"
"Everything you build lives in one place"
[Button: "Create project"]
```

---

## Activity Feeds & Timelines

Feeds (notifications, audit logs, activity streams, social feeds) are empty for new users and occasionally after clearing.

**Rules:**
- Explain **what triggers entries** — users often don't know what causes events to appear
- For new users: "Activity appears here as your team takes actions — creating items, leaving comments, and making changes"
- For cleared/empty after action: brief confirmation that it's up to date, not that something's wrong
- Never show timestamps or date dividers in an empty feed — it looks broken

**New user empty feed:**
```
[Icon: activity/pulse]
"Nothing to show yet"
"Activity appears here as you and your team take actions — creating projects, commenting, and making updates."
```

**Post-clear / up-to-date feed:**
```
[Icon: checkmark or checkmark-clock]
"You're all caught up"
"New activity will appear here as it happens."
```

---

## Sidebar Navigation Sections

Sidebars with collapsible sections (e.g., "My Projects", "Favorites", "Recent") often become problematic when empty.

**Rules:**
- Don't collapse the section entirely when empty — the user needs to know the section exists
- Show a subtle inline empty message, not a full empty state component
- Keep it minimal: 1 short line, no illustration, no CTA button (the sidebar is the wrong place for primary CTAs)
- Exception: if the section is a core workflow driver (e.g., "Your Workspaces"), a small CTA inline is acceptable

**Examples:**
- "No favorites yet — star items to add them here"
- "No recent files"
- "No projects — [+ New project]"

---

## Modals and Drawers

Modals that load data (e.g., "Select a team member", "Choose a template") can be empty.

**Rules:**
- Show the empty state **inside** the modal — don't close the modal or replace it with a full page
- Keep the empty state compact and proportional to the modal size
- The CTA should either close the modal + redirect ("Create a template first") or provide an inline action if possible
- Always give the user an escape: the modal close button should still work clearly

**Structure:**
```
[Modal header: "Choose a template"]
[Modal body:]
  [Small icon]
  "No templates yet"
  [Button: "Create a template" → navigates to templates section]
[Modal footer: [Cancel button]]
```

---

## Search Bars and Autocomplete Dropdowns

Inline search with autocomplete (not full-page search) has its own rules.

**Rules:**
- Show "No results for X" in the dropdown — don't just collapse it to nothing
- Keep the dropdown visible with the message — disappearing dropdowns are alarming
- For type-ahead: don't show "no results" until the user has typed 3+ characters — before that, show suggestions or recent searches
- Offer a "Search all X" link at the bottom of the dropdown to escalate to full search

**Dropdown empty state:**
```
[Dropdown open]
  "No results for 'purple sh…'"
  [Divider]
  "Search all items for 'purple sh…' →"
```

---

## Notification / Alert Badges

These aren't traditional empty states but follow the same principles.

**Rules:**
- **Remove the badge entirely when zero** — don't show a "0" badge. Zero-badge = no indicator.
- Exception: if a zero-count is semantically meaningful (e.g., a failed tests counter that went to 0), show it with a positive green treatment
- "You have no notifications" in the notification panel is fine — it's informational without being alarming

---

## Onboarding Checklists (Gamified Empty States)

A special pattern where the empty state itself IS the onboarding experience.

**Rules:**
- 3–5 steps maximum — more than 5 feels like homework
- Show progress: "2 of 5 complete" with a visual progress bar
- Each step should be completable in under 60 seconds
- Mark completed steps visually (strikethrough, checkmark, greyed out) but keep them visible — completion history is motivating
- The checklist should disappear or collapse once all steps are done — don't make it permanent UI
- Optionally: offer "Dismiss" from the start, for power users who don't need it

**Checklist structure:**
```
Get started with [Product] — 0 of 4 complete [====    ]

☐ Create your first project       [Start →]
☐ Invite a teammate               [Invite →]
☐ Connect an integration          [Connect →]
☐ Set your notification prefs     [Set up →]

[Dismiss checklist]
```
