# Settings

The Settings page lets you customize your experience, manage your data, and control your account. Access it from the **Settings** tab in the bottom navigation bar.

---

## Profile

The Profile section shows your **username** and **user ID**.

### Changing Your Password

1. Tap **Change Password** in the Profile section.
2. Enter your **current password**.
3. Enter a **new password** (must be at least 8 characters).
4. Enter the new password again to **confirm** it.
5. Tap **Update Password**.

A green confirmation message appears on success. Tap **Cancel** to close the form without making changes.

<img src="screenshots/change-password-form.png" alt="Change password form" width="300" />

---

## Weight Unit

Choose your preferred unit for displaying and logging weights:

- **Pounds (lb)** -- default
- **Kilograms (kg)**

Tap your preferred option. The selection saves immediately. This affects the plate calculator and weight displays throughout the app.

<img src="screenshots/weight-unit-toggle.png" alt="Weight unit toggle" width="300" />

---

## Distance Unit

Choose your preferred unit for logging and displaying cardio distances:

- **Kilometers (km)** -- default
- **Miles (mi)**

Tap your preferred option. The selection saves immediately. This affects the Dist column on cardio set rows, the pace readout (e.g. `5:30/km` vs `8:30/mi`), and distance summaries in your history.

<img src="screenshots/distance-unit-toggle.png" alt="Distance unit toggle" width="300" />

---

## Workout View Mode

Control how exercises are displayed during an active workout:

| Mode | Description |
|------|------------|
| **Tabbed** | Shows one exercise at a time. Navigate between exercises using tabs. Best for focused, one-exercise-at-a-time training. |
| **Scroll** | Shows all exercises on a single scrollable page. Best if you like seeing everything at once. |

Tap your preferred mode. The selection saves immediately.

<img src="screenshots/workout-view-mode-toggle.png" alt="Workout view mode toggle" width="300" />

---

## Rest Timers by Set Type

Configure how long the rest timer counts down after completing a set. Each set type has its own timer so you can rest differently for warmups versus heavy working sets.

| Set Type | Description |
|----------|------------|
| **Warmup** | Light preparatory sets |
| **Working** | Your main working sets |
| **Backoff** | Lighter sets after your top sets |
| **Drop** | Reduced-weight sets done immediately |
| **AMRAP** | As Many Reps As Possible sets |

### Adjusting a Timer

Use the **-** and **+** buttons next to each set type to adjust the rest time in **15-second increments**. Timers can be set from 0 seconds (no rest timer) up to 10 minutes.

<img src="screenshots/rest-timer-configuration.png" alt="Rest timer configuration" width="300" />

### Apply to All Templates

Tap **Apply working set timer to all templates** to update the rest time on all your workout templates to match your current working-set rest timer value. This is useful when you want consistent rest periods across your entire program.

> **Tip:** A rest timer of 0 seconds disables the automatic timer for that set type.

---

## Plate Calculator

Configure the plate calculator to match your gym's equipment. The plate calculator helps you figure out which plates to load on each side of the bar.

### Bar Weight

Use the **-** and **+** buttons to set your barbell weight (adjusted in 5 lb/kg increments). Common values:

- 45 lb / 20 kg (standard Olympic barbell)
- 35 lb / 15 kg (women's Olympic barbell)
- 25 lb / 10 kg (training bar)

### Available Plates

This shows the plate weights you have available. Plates are listed from heaviest to lightest and represent the weight of a **single plate** (the calculator figures out how many to put on each side).

**To add a plate weight:**

1. Type the weight in the input field at the bottom.
2. Tap the **+** button (or press Enter).

**To remove a plate weight:**

Tap the plate chip directly -- it will be removed from your available plates.

<img src="screenshots/plate-calculator-configuration.png" alt="Plate calculator configuration" width="300" />

---

## API Keys

API keys let external tools like Claude, ChatGPT, or Cursor access your fitness data through the MCP server.

### Creating a Key

1. Tap **New Key** in the API Keys section.
2. Enter a **name** for the key (e.g. "Claude Code", "ChatGPT").
3. Optionally set an **expiration date**.
4. Tap **Create Key**.
5. **Copy the key immediately** -- it won't be shown again after you dismiss the banner.
6. Tap **I've saved this key** to dismiss.

<img src="screenshots/api-key-banner.png" alt="Newly created API key banner" width="300" />

You can have up to **25 API keys** per account. If you reach the limit, revoke unused keys before creating new ones.

### Managing Keys

Each key shows:

- Key name and prefix (e.g. `so_abc1234...`)
- Creation date
- Last used time
- Expiration status

### Revoking a Key

Tap the trash icon next to any key to revoke it. You'll be asked to confirm. Once revoked, any integration using that key will immediately stop working.

> **Note:** For details on using API keys with AI tools, see [API & MCP Integration](api-and-mcp.md).

---

## Data Management

### Export All Data

Tap **Export All Data** to download a JSON file containing all your data:

- Exercises
- Workout templates
- Programs
- Workout sessions (with all sets)
- Body weight entries

The file is named `sunderos-export-YYYY-MM-DD.json` and downloads directly to your device. Use this for backups or transferring data.

### Import Data

Tap **Import Data** and select a previously exported JSON file. The import processes:

- Exercises
- Templates
- Programs
- Sessions
- Body weight entries

A summary message shows how many items of each type were imported (e.g. "Imported: 5 exercises, 3 templates, 12 sessions").

> **Tip:** Import is additive -- it adds new data without deleting your existing records.

### Clear Offline Data

Tap **Clear Offline Data** to remove all cached workout data from your device's local storage. This does not affect your data on the server -- it only clears the offline cache on the current device.

Use this if:

- The app is behaving unexpectedly
- You want to free up local storage space
- You're logging out of a shared device

---

## Dead Letter Queue

If the app was unable to sync some offline changes to the server after multiple attempts, a warning banner appears showing how many items failed.

[Screenshot: Dead letter queue warning]

You have two options:

- **Retry All** -- requeues the failed items for another sync attempt
- **Discard All** -- permanently removes the failed items (the data will be lost)

> **Note:** This only appears when there are failed sync items. If you don't see this section, all your data is synced.

---

## Log Out

Tap **Log Out** at the bottom of the Settings page to sign out. You'll be asked to confirm before being logged out.

---

## Next Steps

- [Getting Started](getting-started.md) -- review the basics
- [Dashboard & Stats](dashboard-and-stats.md) -- check your training progress
- [API & MCP Integration](api-and-mcp.md) -- connect AI tools to your data
