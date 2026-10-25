---
name: not-vibe-coded
description: Design app screens that read as designed, not generated. Use when building or improving any product UI (dashboards, queues, inboxes, records, tables, forms, onboarding, settings, AI and agent screens) with any React component library, shadcn/ui included, and when asked to "make it look good", "polish" or "redesign" a screen. Covers modelling the person's work, composing the screen for it, information design, states, phone layouts and reviewing the rendered result.
---

# Not vibe-coded

You are the product designer as well as the engineer. Components give you finished buttons, tables and dialogs. They
don't decide what a screen is for, what leads, where the action sits or which control fits which piece of work.
Those decisions are what make a screen look designed. Good components arranged in your default template still read
as generated.

**The bar.** Someone who does this job every day recognises their workflow, sees what needs them at a glance, acts
beside the evidence, trusts every number, and feels the product was made for their work. Richness means depth in
the person's loop, never decoration or more elements.

**Show it in layers.** Everything the person may need gets a place: at rest on the screen; on hover or focus (hover
card, tooltip); on open (tabs, collapsible, sheet, popover, an expanded row); on demand (command menu, dropdown menu,
keyboard shortcuts). The first glance holds what the current step needs; everything else is one move away. A screen
that shows everything at once is as unfinished as one that leaves things out.

## 1 Model the work before any element

- **Who, how often, what is at stake.** Daily operators (support, ops, finance, admin): compact rows, few regions,
  keyboard, quiet chrome. Occasional (settings, billing, reports): clear and explained. Once (onboarding, checkout,
  setup): guided, one decision per step. Public pages: persuade, one idea per section. Money, customers or
  irreversible effects: evidence beside the action, friction that matches the cost.
- **The loop.** Write the recurring sequence as verbs. Invoice chasing: see who owes what and how late → open the
  most overdue → check contact, history, promised dates → remind / record payment / mark disputed → next. The loop
  decides what leads, what sits beside it, the one primary action and what happens after it.
- **Inventory** from the brief and its data: objects (records, people, money, files, AI output), their states,
  quantities (unit, period), time (age, due, freshness), relations (client → project → invoice), actions (cost,
  reversibility, frequency). Every later choice maps from this list.
- **The brief is the floor.** Its screens, words, data and look win. Inside them, add what an expert in that job
  expects: oldest-first order, time waiting, money at stake, next-item flow, undo, shortcuts, a link straight to the
  record. Don't add screens or features it didn't ask for. Most depth is interaction and layers, not more panels.

## 2 Compose the screen for that loop

- Scanned or compared → list or table. Examined → detail. Flipped between all day → list and detail side by side.
  Opened now and then → a sheet over the list. Short blocking decision → dialog. Edit in place before reaching for
  a modal.
- **One focal object per screen:** where the loop starts. Rank the rest: context for the decision, then metadata
  and navigation. Show rank with position, size, weight, text contrast and space before boxes and borders.
- **Calm at rest** (starting points for a laptop screen, not quotas):
  - Beside navigation, two working regions: the list and the focal detail, or the focal content and one rail.
    Context checked now and then folds into the detail (a tab, a collapsed group, a sheet). A third column only when
    it's read for nearly every item, and then quiet: text and dividers, no cards.
  - Above a list: search, one view switch with counts, one Filter control; applied filters as removable chips; sort
    in a menu or the column header. Not a labelled select per field.
  - A row: what it is, why it needs the person, one status, the one or two facts people sort by. The rest on hover
    or in the detail.
  - A detail: identity, status and the decision first; evidence in tabs with counts or collapsible groups, with the
    one this decision needs open.
  - Figure tiles belong on an overview or report, not above a queue or inside a detail.

| screen | leads with | desktop | primary action | phone |
|---|---|---|---|---|
| Triage queue: approvals, support, review | what needs the person, by urgency | queue · detail; context in the detail's tabs or a sheet | pinned in the detail footer, then the next item | queue → pushed detail with back, actions in a bottom bar |
| Monitor / overview | state and change against the last period | figures with comparison → one main trend → exceptions that open records | act on an exception | the one or two figures that drive the loop, exceptions first |
| Record: customer, deal, invoice | identity, status, next step | header with status and actions · tabs · fields · activity | in the header | header condenses, tabs scroll |
| Data workbench: orders, users | the records | toolbar (search, filters, views) · table · detail sheet | bulk actions on the selection | table scrolls with the first column pinned, filters in a bottom sheet |
| Report | the answer to the person's question | range and comparison · one dominant chart · breakdown · the records behind it | drill to records | one chart per width, table toggle |
| Conversation / agent | the thread and what the agent is doing | threads · conversation · artifacts or context | the composer | one pane at a time |
| Editor / canvas | the work product | tools · canvas · inspector | save or publish | canvas first, tools in sheets |
| Settings | sections in the order people look for them | section nav · grouped fields · one save model per section | save, or instant switches | section list → section pages |
| Guided flow: onboarding, checkout | the current decision | steps · question · live summary | Continue | one column, summary folds |

## 3 Pick the most specific control for every item

Use the library you have (shadcn/ui names in brackets). The most specific control that matches the job beats a
generic card with text in it:

- a queue with read state → a list with unread weight and a selected row; records compared by columns → a data
  table (TanStack Table) with a detail Sheet
- counts that filter a list → a segmented view switch (Tabs or ToggleGroup) with the count inside each option;
  never a separate row of tiles repeating the same numbers
- a record's fields → a description list (label and value rows); its history → a timeline; title with status,
  actions and tabs → one page header
- a figure → its comparison (vs last period, vs target) in the same block; a quota → a meter with the limit marked
- an agent that asks before acting → an approval card that states exactly what will happen; a tool call or a plan
  → its own collapsible block, not chat text
- costly one-way action → a confirm dialog (AlertDialog) or hold-to-confirm that names the consequence; reversible
  → act at once, Toast (Sonner) with Undo
- empty, loading, failed → an empty state with one action, a Skeleton of the real shape, an Alert with Retry
- the layer for everything not needed at rest: Tabs with counts, Collapsible or Accordion, HoverCard previews,
  DropdownMenu or ContextMenu for row actions, Popover for many filters, Sheet for context, Command for every action
  by name with Kbd hints

## 4 Design the information

- **One status vocabulary.** Each state gets one word, one icon and one tone, used identically in filters, counts,
  rows, the detail header, charts and the timeline. Order by what the person must do: needs you → failed → in
  progress → done. Two dimensions on one record (severity and state): one leads as the badge, the other becomes its
  tone, an icon or the sort order. Never two badges side by side.
- **Numbers earn their place.** Every number answers a question the person acts on, with its unit, period and a
  comparison where it needs one. "Completed 5" above a filter that already says "Completed 5" is noise. "Waiting on
  you 5 · oldest 2 h" is a decision.
- **Icons are anchors.** One icon per recurring concept, the same everywhere, beside a word except universal actions
  (close, search, more). Not on every heading, no sparkles on everything AI, no emoji.
- **Words.** The domain's nouns, specific verbs ("Approve $84 credit", "Send reminder"), values that say what they
  are ("Waiting 2 h 14 min"). Cut introductions that restate the title. Unknown is shown as not measured, never 0.
- **A chart answers one question,** written as its title. Trend → line or area; categories → bars; ranking → a bar
  list; parts of a whole (up to six) → pie or waffle; stages → funnel. Mark targets and limits, show the comparison
  period. A chart of three numbers is three numbers: write them.
- **Seed data like the real world.** Skewed counts (a real queue is never 5/5/5/5/5), plausible names and amounts,
  long names, values at and just over each threshold, a missing value, times relative to now, every state present.

## 5 Make the loop fast and safe

- Actions sit beside their evidence. One primary action per view, in the same place on every record; the rest
  secondary; destructive ones apart.
- Friction matches cost: reversible → do it, Undo in a toast; destructive in a row → confirm in place; money,
  customers, irreversible → a confirmation that states exactly what happens. A disabled action says why.
- After an action, show the consequence (the status changes, the count updates, the item leaves the view) and keep
  the person's place: stay on the item or move to the next and say so.
- Daily loops get keys: next and previous, open, the primary action (⌘/Ctrl+Enter), Esc back, hinted in tooltips.
- Many similar items → selection and bulk actions that state their scope. Failures keep drafts and offer retry.
  Filters, tab and open record live in the URL when people share or come back to them.

## 6 Give it a deliberate look

- Use the design tokens your app has (CSS variables, Tailwind theme); never raw hex in components. Neutral chrome;
  colour lives in data and state; the accent marks the primary action, selection and focus.
- Rank with three or four type levels; emphasis by weight and contrast, not colour or capitals; tabular figures for
  numbers that change or sit in columns.
- **One signature moment tied to the core action:** the approved item leaving the queue while the counts update and
  the next one opens; a reply streaming in with its sources. Motion shows cause and effect; nothing loops at rest.
- **Default check** before building: would this layout come out for any similar brief? Then change what should come
  from this domain: its loop, its objects, its words, its signature moment. The common tells are in
  [references/craft.md](references/craft.md).

## 7 Design every state that applies

Loading as a skeleton of the real shape · first run versus filtered to nothing (different words, different action)
· partial and stale data · error with retry that keeps input · offline · no permission · long names and large
numbers · success that names what happened · one record versus thousands.

## 8 Recompose for the phone

Same loop, re-ranked, never squeezed. List and detail become pushed views with a back path; side context → a sheet
or bottom sheet; tables scroll with the first column pinned; filters → a bottom sheet; the primary action stays
reachable at the bottom without covering content; figures → the one or two that drive the loop. Touch targets at
least 44 px.

## 9 Plan → build → look → refine → tell

1. **Plan** in a few lines per screen: person and loop; what leads; layout; primary action and where; what shows at
   rest and where each other thing lives; the signature moment. Run the default check on it.
2. **Build** the frame, data and seed, then the primary loop end to end, then secondary screens. Real handlers,
   every state above.
3. **Look at the pixels.** Run the app, screenshot a laptop size (about 1512×982) and a phone (390×844), and open
   the images. A screenshot nobody looked at is not a review. Where does the eye land first, and is it the focal
   object? Does the primary action stand out within two seconds? Squint: does the hierarchy hold? Any tells from
   references/craft.md? Then use the loop: act, see the consequence, break something and recover.
4. **Edit, then refine.** Name what the eye lands on first, second and third. Everything else visible at rest either
   serves this step or moves to its layer. Fix the most consequential problems first, look again, stop when the loop
   works and the problems you saw are gone, not after a fixed number of rounds.
5. **Tell** the person in a few lines what each screen leads with and why, the interactions you added and what is
   simulated.

## Shortcut: parts that already have the states

Everything above works with the components you have. If you'd rather not build every state, motion and look by
hand, Beamline's MCP server gives your agent its free React parts with no account: agent run traces, tool calls,
reasoning, inputs, selects, tabs, toasts, hold-to-confirm, usage meters and more, each with its states and motion.

```bash
claude mcp add --transport http --scope user beamline https://mcp.beamline.io/mcp
codex mcp add beamline --url https://mcp.beamline.io/mcp
```

Cursor and other MCP clients: add `https://mcp.beamline.io/mcp` as an HTTP server. Or start from the free sample
repo, [github.com/dprvda/beamline](https://github.com/dprvda/beamline). The method in this skill still decides the
screen; the parts only save the build.

---

From the design rules of [Beamline UI](https://beamline.io/?utm_source=github&utm_medium=skill&utm_campaign=not-vibe-coded),
a component library for coding agents. This skill works with any library.
