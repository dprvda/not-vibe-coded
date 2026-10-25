# Craft: what makes a screen read as designed

Use while refining a screen and for the visual review. The brief and the app's own look win over any default here.
No universal ban on colour, gradients or expressive motion; no element quota. Every rule serves the person's loop.

## Hierarchy and layout

- **Rank, then express.** Decide first, second, third for each screen. Express rank with position, size, weight,
  text contrast and space. Boxes and borders come last.
- **Proportion follows importance.** The focal region gets the most room: a list of 360–420 px and the detail the
  rest; a main chart across two thirds with its breakdown beside it. Equal columns only for equal things.
- **One rhythm.** A 4 px base. Inside a group 8–12 px, between groups 16–24 px, between sections 32–48 px. Inner gaps
  smaller than outer gaps, or groups dissolve.
- **Shared edges.** Title, content and actions of a column start on one edge. Numbers right-aligned with one
  precision. Label and value on one baseline. Icons centred on the text beside them.
- **Containment needs a reason:** a record, an interactive object, controls that act together, a chart or table.
  Otherwise a heading, space and a divider. Never a card inside a card.
- **Width serves the focal region.** Reading text 45–78 characters; forms in a 560–720 px column, or two columns
  with a live summary; a work tool spans the full width and gives the extra room to the list and the detail.
  Nothing stranded in the top-left third of an empty page.

## Type

- Three or four levels per screen. Emphasis by weight (500, 600) and contrast, not colour or capitals. Capitals only
  for short labels; never a sentence.
- Tabular figures (`font-variant-numeric: tabular-nums`) for every number that changes or sits in a column.
- Truncate fragments with an ellipsis and the full value on hover; never truncate words that carry a decision.

## Colour

- Neutral chrome. Colour belongs to data and state; the accent marks the primary action, selection and focus.
- Fix the semantic tones once: success for done, warning for needs attention, danger for failed or late, info for in
  progress, neutral for queued or archived. A status is colour, icon and word together.
- One colour per chart series across every chart on the page; good/bad colours in charts only when the data is
  literally good or bad.
- Unknown values read as not measured (a gap or hatch), never 0.
- If the app ships light and dark, look at both.

## Icons

- One icon per concept, decided once in a small map in code (state → icon, tone, word) and reused in navigation,
  filters, counts, rows, headers, timelines and empty states.
- Examples from lucide-react: waiting for a person `Hand`; running `LoaderCircle` (spins only while running); queued
  `Clock`; done `CircleCheck`; failed `CircleX`; late `AlarmClock`; money `Banknote`.
- 14 px in dense rows, 16 px beside body text. Icon-only buttons get an accessible name and a tooltip.

## Numbers, units and time

- Format with `Intl`; one precision per column; units in the label or beside the value.
- Durations in words ("2 h 14 min"). Relative times for recency with the exact time on hover; absolute dates where
  people sort and compare.
- Percentages with their base ("62% of 48 runs"). Averages of times hide the tail: show p50 and p95.

## Tables and lists

- Columns: identity → state → the numbers people compare → time → actions. The default sort follows the loop.
- First column pinned when the table scrolls sideways.
- Row actions on hover and focus, always reachable from a menu and the keyboard.
- Selection: a checkbox column and a bar that states the scope; "select all matching" apart from "select all on this
  page".
- Empty is two states: "No invoices yet" with Create, versus "No matches for 'acme' in Paid" with Clear filters.

## Forms and decisions

- Order by how people think, not by the database. Prerequisites first.
- Show price and consequence before commitment; keep units, bounds and validation visible.
- Real labels, `autocomplete`, input modes; paste and keyboard submit work. After a failed submit, focus the first
  error and keep valid input.
- Instant settings use a switch; settings saved together use one save bar that appears when something changed.
- Pick the control from the value: one of three options → cards or a segmented control, not a dropdown; a number in
  a range → a slider or stepper with its unit; a date → a date picker, not a text box.

## Feedback and motion

- Every action is acknowledged at once. Pending controls keep their size. Success appears only after the operation
  succeeds; errors say what happened and how to recover.
- Cause and effect: what changed moves (a count rolls, a row leaves, a status word changes) and where it went stays
  visible.
- What is done a hundred times a day never waits for an animation. Nothing loops at rest. Reduced motion keeps every
  meaning.

## Copy

- Name things the way the person does; one noun per concept on every screen.
- Buttons are verb and object ("Send reminder"); the confirmation uses the same words ("Reminder sent").
- Errors: what happened, why if known, what to do next. Never "Something went wrong" alone.
- Sentence case. No exclamation marks in working screens. No filler ("Easily manage your…").

## Template tells and what to do instead

| tell | instead |
|---|---|
| a capitals eyebrow above every title repeating the nav | a breadcrumb where there is hierarchy, otherwise the title alone |
| a subtitle restating the title | remove it, or one line of state ("5 waiting · oldest 2 h") |
| the same four figure tiles on every page | figures only where they drive that page's loop, each against a period or target |
| a tile strip repeating the filter counts | the counts inside the filter control |
| initials avatars on every row | avatars where people matter; otherwise the object's icon or nothing |
| "·"-joined meta on every line | columns, or a second line of labelled values |
| sparkles on anything AI | the agent's actual state: thinking, the tool it called, the step it's on |
| an empty-state tile in every panel | seeded content; empty states where empty is real |
| cards inside cards, equal cards everywhere | one frame with dividers; rank, and give the focal object the room |
| an indigo-to-purple gradient on the hero | the app's own colour on the one thing that matters |
| a narrow centred column for a daily work tool | full-width list and detail, context one move away |
| a third column as heavy as the detail | context as a tab or collapsed group in the detail, or a sheet |
| a labelled select per filter above the list | search, one view switch with counts, one Filter control; applied filters as chips |
| two badges on one row | one badge; the other dimension as its tone, an icon or the sort order |
| four lines of meta on every row | what, why, status and the one or two facts people sort by |
| every section open under a capitals label | tabs with counts or collapsible groups, sentence-case headings |
| a line of help under every heading | help where a decision is unfamiliar; a tooltip elsewhere |
