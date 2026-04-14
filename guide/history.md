# Workout History

The History page is where you review all your past workout sessions. You can browse sessions, filter by time period, expand any session to see every set you logged, and view progress charts for individual exercises.

---

## Browsing Past Sessions

Open the **History** tab from the bottom navigation bar. You'll see a list of your completed workout sessions, each showing:

- **Date** (e.g. "Mon, Feb 3")
- **Duration** (e.g. "1h 12m")
- **Exercise count** (e.g. "5 exercises")
- **Notes** (if you added any during the session, shown as a preview)

<img src="screenshots/history-session-list.png" alt="Workout history session list" width="300" />

Sessions are listed in reverse chronological order (most recent first). If you have a large history, tap **Load More** at the bottom to fetch older sessions.

---

## Period Filters

Use the filter buttons at the top to narrow down which sessions appear:

| Filter | Shows |
|--------|-------|
| **Week** | Sessions from the current week |
| **Month** | Sessions from the current month |
| **Year** | Sessions from the current year |
| **All** | Every session you've ever logged |

<img src="screenshots/history-period-filter.png" alt="History period filter buttons" width="300" />

Changing the filter updates both the session list and the summary stats above it.

---

## Summary Stats

When you have sessions in the selected period, three stat cards appear at the top:

| Stat | Description |
|------|------------|
| **Workouts** | Number of sessions in the selected period |
| **Total Time** | Combined duration of all sessions |
| **Total Volume** | Total weight lifted (weight x reps across all sets), in lbs |

<img src="screenshots/history-summary-stats.png" alt="History summary stats row" width="300" />

> **Note:** Total Volume is calculated as sessions are expanded and their details loaded. Expand sessions to get a more accurate total.

---

## Expanding Session Details

Tap any session card to expand it and see the full breakdown.

<img src="screenshots/session-detail-sets.png" alt="Expanded session detail with exercise sets" width="300" />

### What You'll See

Each expanded session shows:

- **Session notes** (if any) at the top
- **Exercises** listed in order, each showing:
  - Exercise name
  - A table of working sets with columns for:
    - **Set** number
    - **Weight** (displayed cleanly without trailing zeros -- e.g., 185 not 185.00, 7.5 not 7.50)
    - **Reps** completed
    - **RPE** (Rate of Perceived Exertion, if logged -- supports half values like 7.5, 8.5)

Tap the session card again to collapse it.

---

## Exercise Progress Charts

Within an expanded session, each exercise has a small chart icon (trending arrow) next to its name. Tap it to reveal an inline **progress chart** for that exercise.

<img src="screenshots/exercise-progress-chart.png" alt="Inline exercise progress chart in history" width="300" />

The progress chart shows:

- **Max Weight** over time (blue line) -- tracks the heaviest weight you've used per session
- **Total Volume** over time (green line, shown when you have 4+ data points) -- tracks total weight x reps per session

Hover over data points to see exact values, dates, and volume numbers in a tooltip. A legend below the chart identifies the two lines.

Tap the chart icon again to hide the progress chart.

> **Tip:** Progress charts are a quick way to see if you're getting stronger on a specific exercise without leaving the history page.

---

## Deleting a Workout Session

If you need to remove a session from your history (e.g., an accidental or test workout):

1. Swipe left on the session card to reveal the delete button.
2. Tap the red **Delete** button.
3. A confirmation dialog appears -- tap **Delete** to confirm or **Cancel** to keep the session.

Deleted sessions and all their logged sets are permanently removed and cannot be recovered.

<img src="screenshots/history-swipe-delete.png" alt="Swipe-to-delete revealing delete button on a session card" width="300" />

---

## Exercise History Page

For a deeper dive into a single exercise, you can open its **Exercise History** page. This dedicated page shows:

### Personal Records

Three PR cards at the top:

| PR | What It Shows |
|----|--------------|
| **Best Weight** | Heaviest weight lifted, with rep count and date |
| **Est. 1RM** | Estimated one-rep max, calculated from your best weight/rep combination |
| **Most Volume** | Highest single-session volume for that exercise, with date |

<img src="screenshots/exercise-pr-cards.png" alt="Exercise history PR cards" width="300" />

### Strength Curve

A line chart plotting your max weight per session over time. The shaded area under the curve helps visualize the trend. Dates appear along the x-axis.

<img src="screenshots/strength-curve-chart.png" alt="Strength curve chart" width="300" />

### Volume Progression

A similar line chart (in green) showing how your total volume per session has changed over time.

<img src="screenshots/volume-progression-chart.png" alt="Volume progression chart" width="300" />

### Session History

Below the charts, a full list of every session where you performed this exercise, showing:

- Date and set count
- Each set's weight, reps, and RPE

<img src="screenshots/exercise-session-history.png" alt="Exercise session history list" width="300" />

---

## Next Steps

- [Dashboard & Stats](dashboard-and-stats.md) -- see your overall training summary
- [Body Weight](body-weight.md) -- track your weight alongside your training
- [Workouts](workouts.md) -- learn how to log a workout session
