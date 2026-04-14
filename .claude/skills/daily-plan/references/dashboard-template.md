# Dashboard HTML Template Reference

When generating the HTML dashboard, use these design specifications:

## Colour Palette (Dark Mode)

```
--bg-primary: #0f172a        (slate-900 — main background)
--bg-secondary: #1e293b      (slate-800 — card backgrounds)
--bg-tertiary: #334155        (slate-700 — hover/active states)
--text-primary: #f1f5f9       (slate-100 — headings, primary text)
--text-secondary: #94a3b8     (slate-400 — secondary text, timestamps)
--text-muted: #64748b         (slate-500 — muted labels)
--border: #334155             (slate-700 — borders, dividers)
--accent-blue: #3b82f6        (blue-500 — links, Medium priority)
--accent-red: #ef4444         (red-500 — Urgent priority, overdue)
--accent-orange: #f97316      (orange-500 — High priority, warnings)
--accent-green: #22c55e       (green-500 — Done/completed states)
--accent-purple: #a855f7      (purple-500 — In Progress state)
--accent-yellow: #eab308      (yellow-500 — Todo state)
--accent-grey: #64748b        (slate-500 — Low priority, Backlog)
```

## Layout Structure

```
┌──────────────────────────────────────────────┐
│  Header: Date, Greeting, State Summary       │
├──────────────────────────────────────────────┤
│  Priority Cards (horizontal scroll or grid)  │
├───────────────────────┬──────────────────────┤
│  Linear Tasks Panel   │  Email Panel         │
│  (grouped by state)   │  (sorted by urgency) │
├───────────────────────┼──────────────────────┤
│  Slack Panel          │  Carryover + Weekly   │
│  (grouped by channel) │  Priorities           │
└───────────────────────┴──────────────────────┘
```

## Priority Badges

```html
<span class="badge urgent">Urgent</span>   <!-- red bg -->
<span class="badge high">High</span>       <!-- orange bg -->
<span class="badge medium">Medium</span>   <!-- blue bg -->
<span class="badge low">Low</span>         <!-- grey bg -->
```

## State Badges (Linear)

```html
<span class="state in-progress">In Progress</span>  <!-- purple -->
<span class="state todo">Todo</span>                  <!-- yellow -->
<span class="state backlog">Backlog</span>            <!-- grey -->
<span class="state done">Done</span>                  <!-- green -->
```

## Collapsible Sections

Each panel should be collapsible with a chevron toggle:

```html
<div class="panel">
  <div class="panel-header" onclick="togglePanel(this)">
    <h2>Linear Tasks <span class="count">(12)</span></h2>
    <span class="chevron">▼</span>
  </div>
  <div class="panel-body">
    <!-- content -->
  </div>
</div>
```

## Source Icons

Use simple text/emoji indicators for data sources:
- Linear: 📋
- Gmail: ✉️
- Slack: 💬
- Vault: 📝

## Responsive Breakpoints

- Desktop (>1024px): 2-column grid for panels
- Tablet (768-1024px): single column, cards still horizontal
- Mobile (<768px): fully stacked, cards vertical

## Empty State

If a data source returns nothing:
```html
<div class="empty-state">
  <p>No unread emails — inbox zero! 🎉</p>
</div>
```
