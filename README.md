# Day Challenge Tracker

A single-file, zero-dependency browser app for running 30–365 day personal challenges. Track daily completions, tasks, habits, and progress — all stored locally in your browser with no account or server required.

---

## Getting Started

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. Select a challenge duration: **30, 60, 90, 100, 180, or 365 days**.
3. Fill in your **Goal**, **Reward**, and **Start Date**.
4. Click **▶ Start** on Day 1 (or set a past start date to resume).
5. Click any unlocked day cell to open its detail modal and begin tracking.

No build step, no installation, no internet connection required after the file is loaded.

---

## Features

### Challenge Grid

The main view displays every day of your challenge as a grid of cells. Each cell shows the day number, completion status, and visual indicators for tasks, notes, challengers, and events. Future days are locked. Today's cell is highlighted and shows a live task completion percentage.

- **IMDB-style rating colors** — cells are color-coded based on 1–5 star ratings using a red → amber → yellow → lime → green scale. Days marked Done show green only when no rating has been set; otherwise the rating color shows through.
- **Roll-over indicator** — tasks rolled from a previous day show a small dot.
- **Event dot** — days with scheduled events show a colored dot in the corner.

#### Rating Color Scale

| ★ | Color | Meaning |
|---|---|---|
| 1 ★ | 🔴 Red | Poor |
| 2 ★ | 🟠 Amber | Below average |
| 3 ★ | 🟡 Yellow | Average |
| 4 ★ | 🟢 Lime | Good |
| 5 ★ | 💚 Green | Excellent |

### Day Modal

Click any past or present day to open its detail panel. Inside:

- **Day rating** — rate your day 1–5 stars; affects the cell color on the grid.
- **Events** — any events scheduled for the day appear at the top.
- **Challengers** *(collapsible)* — log progress on active challengers for that day. Click the section header to hide or show.
- **Daily Habits** *(collapsible)* — check off habits for the day. Click the section header to hide or show.
- **Tasks** — add, edit, reorder, and complete tasks. Supports subtasks, inner tasks, priorities, time estimates, recurrence, and dependencies.
- **Note** — a free-text note field for the day.
- **Mark Done** — marks the entire day as complete once all your goals are met.

### Tasks

Tasks are the core unit of daily work. Each task supports:

| Feature | Details |
|---|---|
| **Priority** | High / Medium / Low, shown as a colored left border |
| **Time estimate** | Free-text field (e.g. `30m`, `1h`) for display |
| **Subtasks** | Expandable sub-items with their own checkboxes and nested inner tasks |
| **Recurrence** | Repeat every N days (daily, every 2 days, weekly, or custom interval) |
| **Dependencies** | A task can be blocked until another task in the same day is completed |
| **Roll-over** | Incomplete tasks automatically roll to the next day (can be disabled per task) |
| **Templates** | Save a set of tasks as a named template to reapply on other days |
| **Drag & drop** | Reorder tasks and subtasks by dragging |

#### Inline Task Editing

Click the **✎** button on any task to open an inline edit panel below the task row. From there you can update:

- **Time estimate** — change the time field without re-adding the task.
- **Priority** — switch between None, High, Medium, and Low.
- **Recurrence** — set or change the repeat interval (or remove it entirely).

Hit **✓ Save** to apply changes or **Cancel** to dismiss.

#### Task Timer (Time Log)

Every task has a built-in multi-session stopwatch. Logged time persists in your save data and survives page reloads.

- Click **▶** on any task to start a session.
- Click **⏹** to stop and record the session.
- A `⏱ Xm XXs` tag in the task row shows total logged time at a glance.
- Expand the **Sessions** panel below the task to see a full log of start/end times and individual session durations, plus a grand total.
- Use **✕ Clear** to wipe all sessions for a task.
- Multiple sessions per task are supported — stop and restart as many times as you like.

### Habits

Define a list of recurring daily habits in the Habits panel (right sidebar → **Edit**). Inside each day's modal, the Habits section lets you check them off individually. The section is collapsible.

### Challengers

Challengers are parallel sub-goals running alongside your main challenge (e.g. "Run 100km in 30 days"). Each challenger tracks cumulative progress with a counter and progress bar.

- Set a name, emoji, target amount, unit, duration (in days), and start day.
- Log daily units using the **+/−** counter inside the day modal.
- Add optional milestone **Steps** (checklist items) to a challenger.
- Challengers show progress bars in the right sidebar and inside the day modal.
- The Challengers section in the day modal is collapsible.

#### Challenger Timer

Each challenger has a built-in timer, just like tasks. Click **▶ Start** in the Timer row at the bottom of any challenger card to begin logging time. Sessions are stored on the challenger object and persist across page reloads. A full session log with start/end times and totals is shown below the timer row, with a **✕ Clear** option.

Eight built-in templates are available: reading, running, meditation, writing, working out, guitar, no sugar, and saving money.

### Task Templates

Save the current set of tasks on any day as a named template, then reapply it to other days in one click.

- **💾 Save set** — saves all tasks from the open day as a new template.
- **✎ Manage** — opens the Templates Manager modal where you can:
  - **Rename** any template by clicking its name inline.
  - **Apply** a template to the currently open day.
  - **Delete** a template permanently.
  - Preview all tasks inside each template with their priority dots and time estimates.

### Events

Schedule named events on specific day numbers of your challenge. Events appear in the right sidebar and at the top of the day modal. Each event has a title, optional description, and a color dot.

### Profiles

Multiple independent challenge profiles are supported. Each profile has its own state, tasks, habits, challengers, events, and badges — all stored separately in localStorage.

- **＋ Profile** — create a new profile with a custom name.
- **✕ Delete** — remove the current profile and all its data.
- Switch between profiles using the dropdown in the top bar.

### Stats Dashboard

Open **📊 Stats** from the status bar for a summary across your whole challenge:

- Days completed, current streak, best streak
- Total tasks and completed tasks
- Average day rating
- Challenger units logged
- **Total Time Tracked** — sum of all timer session time across every task and every challenger
- Completion rate
- Completion rate by day of week (bar chart)
- Star rating distribution (bar chart)

### Weekly Review

Open **📅 Review** to browse any week of your challenge. Shows a 7-cell grid with completion and rating for each day, plus summary stats (days completed, tasks done, average rating, completion rate).

### Weekly Planner

Open **🗓 Weekly Planner** to see a 7-column grid spanning any week. Add tasks directly to any day from the planner view without opening the day modal.

### Badges

Eleven achievements unlock automatically as you make progress. Earned badges are highlighted; locked ones are greyed out. A toast notification appears when a new badge is awarded. Badges track how many times they have been earned — streak badges can be re-earned each time you rebuild a streak after breaking it, and the count shows on the card (`×2`, `×3`, etc.).

| Badge | Condition |
|---|---|
| 🔥 On Fire | 3-day streak |
| ⚡ Week Warrior | 7-day streak |
| 💎 Two Weeks | 14-day streak |
| 🏆 Monthly Master | 30-day streak |
| 👑 Iron Will | 60-day streak |
| 🏅 Centurion Days | 100 days completed |
| 🌟 Year of Growth | 365 days completed |
| ✅ Getting Started | 10 tasks completed |
| 🎯 Half Century | 50 tasks completed |
| 💯 Centurion | 100 tasks completed |
| 🚀 Powerhouse | 250 tasks completed |

Open **🏅 Badges** from the status bar to view all badges. Use **↺ Reset badges** to clear all earned badges for the current profile.

### Pomodoro Timer

A floating Pomodoro timer can be launched from any task. It runs standard 25-minute focus sessions with 5-minute breaks and tracks session count.

### Data & Sync

All data is stored in browser `localStorage`. Nothing is sent to any server.

**Export / Import**
- **↓ Export** — downloads a `.json` file containing all state, tasks, habits, challengers, events, and badges for the current profile.
- **↑ Import** — loads a previously exported `.json` file to restore or transfer data.

**Folder Sync** (Chromium-based browsers only)
- Connect a local folder using the File System Access API.
- **Save Now** writes a `challenge-tracker-sync.json` file to the folder.
- **Load Now** reads that file back into the app.
- Auto-saves to the folder whenever state changes (debounced).
- Useful for keeping a backup or syncing between sessions on the same machine.

### Display

- **Dark / Light mode** — toggle with ☀️ / 🌙 in the top bar. Preference is saved.
- **Live clock bar** — shows the current time, date, streak, day number, and countdown to midnight.
- **Progress bar** — shows overall challenge completion percentage below the tabs.
- **Responsive layout** — the right sidebar stacks below the grid on narrow screens.

---

## Data Structure

All challenge data is saved to `localStorage` under profile-namespaced keys. The main state object looks like:

```json
{
  "duration": 100,
  "goal": "...",
  "reward": "...",
  "startDate": "2025-01-01",
  "days": {
    "1": {
      "done": true,
      "rating": 4,
      "note": "...",
      "habitChecks": { "habit-id": true },
      "tasks": [
        {
          "id": "ls_1234567890",
          "text": "Task name",
          "checked": false,
          "priority": "high",
          "time": "30m",
          "recurInterval": 7,
          "subs": [],
          "sessions": [
            { "start": 1712000000000, "end": 1712001800000 },
            { "start": 1712005000000, "end": null }
          ]
        }
      ]
    }
  }
}
```

`sessions` is the timer log stored on each task. `end: null` means the session is currently running. Challengers also carry a `sessions` array at the top level of the challenger object (not per-day).

---

## Browser Compatibility

Requires a modern browser with ES6+ support. The Folder Sync feature requires a Chromium-based browser (Chrome, Edge, Brave) that supports the File System Access API. All other features work in Firefox and Safari.
