# API Keys and MCP Integration

Sunderos includes a built-in MCP (Model Context Protocol) server that lets AI assistants like Claude and ChatGPT read and manage your fitness data through natural language. This guide covers generating API keys, configuring the MCP server, and what you can do once it is connected.

---

## What Are API Keys For?

API keys let external tools access your Sunderos data securely. Instead of sharing your username and password, you create a dedicated key that:

- Grants the same access as your logged-in account
- Can be revoked at any time without changing your password
- Has an optional expiration date
- Is tracked so you can see when it was last used

The most common use case is connecting the MCP server to Claude Code, Claude Desktop, Cursor, or ChatGPT so you can ask questions about your training data in plain English.

---

## Generating an API Key

1. Open the app and go to the **Settings** tab (bottom navigation bar, far right).
2. Scroll down to the **API Keys** section.
3. Tap **New Key**.
4. Enter a descriptive name for the key (e.g., "Claude Code" or "ChatGPT").
5. Optionally set an **expiration date**. If you leave this blank, the key never expires.
6. Tap **Create Key**.

![API Key Generation](../screenshots/api-key-generation.png)

A green banner will appear showing your new key. It starts with `so_` followed by a long string of characters.

> **Important:** Copy the key immediately and store it somewhere safe. The full key is shown only once. After you dismiss the banner, you will only see the first few characters (`so_xxx...`) for identification.

7. Tap the **copy button** next to the key to copy it to your clipboard.
8. Tap **I've saved this key** to dismiss the banner.

![Newly Created API Key Banner](../screenshots/api-key-created-banner.png)

### Managing Existing Keys

Your existing keys are listed below the creation form. Each entry shows:

- The key name and prefix (`so_xxx...`)
- When it was created
- When it was last used (or "Never")
- Whether it has expired

To revoke a key, tap the **trash icon** next to it. You will be asked to confirm. Any integrations using that key will immediately stop working.

---

## Configuring the MCP Server

The MCP server is a lightweight bridge between AI assistants and the Sunderos API. It supports two transport modes:

| Mode | Best for | How it works |
|------|----------|-------------|
| **stdio** (default) | Claude Code, Cursor, local tools | Runs as a subprocess; communicates over stdin/stdout |
| **http** | ChatGPT, remote clients | Runs as an HTTP server on a configurable port |

### Environment Variables

The MCP server needs two environment variables:

| Variable | Required | Description |
|----------|----------|-------------|
| `SUNDEROS_API_KEY` | Yes | The API key you generated above (the full `so_...` string) |
| `SUNDEROS_API_URL` | Yes | URL of your Sunderos API (e.g., `http://localhost:3000`) |

---

### Setup for Claude Code (stdio)

The easiest way to set up the MCP server is with `npx` -- no need to clone the repository or build anything. Add the following to your project's `.mcp.json` file or your global `~/.claude.json` file:

```json
{
  "mcpServers": {
    "sunderos": {
      "command": "npx",
      "args": ["-y", "sunderos-mcp"],
      "env": {
        "SUNDEROS_API_KEY": "so_your_key_here",
        "SUNDEROS_API_URL": "http://localhost:3000"
      }
    }
  }
}
```

If you have the source code checked out locally, you can also point directly to the built file:

```json
{
  "mcpServers": {
    "sunderos": {
      "command": "node",
      "args": ["/path/to/sunderos/apps/mcp/dist/index.js"],
      "env": {
        "SUNDEROS_API_KEY": "so_your_key_here",
        "SUNDEROS_API_URL": "http://localhost:3000"
      }
    }
  }
}
```

---

### Setup for Claude Desktop (stdio)

Add the following to your `claude_desktop_config.json` file:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "sunderos": {
      "command": "npx",
      "args": ["-y", "sunderos-mcp"],
      "env": {
        "SUNDEROS_API_KEY": "so_your_key_here",
        "SUNDEROS_API_URL": "http://localhost:3000"
      }
    }
  }
}
```

Restart Claude Desktop after saving the file.

---

### Setup for ChatGPT or Remote Clients (HTTP mode)

For remote clients, run the MCP server in HTTP mode:

```bash
MCP_TRANSPORT=http \
SUNDEROS_API_KEY=so_your_key_here \
SUNDEROS_API_URL=http://localhost:3000 \
MCP_PORT=3001 \
npx sunderos-mcp
```

The server will start on the specified port (default 3001). The MCP endpoint is available at `http://your-server:3001/mcp` and a health check at `http://your-server:3001/health`.

In HTTP mode, the MCP server requires an `Authorization: Bearer <key>` header on all requests (using either `MCP_API_KEY` or `SUNDEROS_API_KEY`). This protects your data when the server is exposed over a network.

> **Note:** If you are exposing the HTTP endpoint to the internet, make sure to run it behind a reverse proxy with HTTPS.

---

## Available MCP Tools

Once connected, the AI assistant has access to 23 tools organized by domain. You do not need to call these tools directly -- just ask questions or give instructions in natural language, and the assistant will use the right tool automatically.

### Exercises (3 tools)

| Tool | What it does |
|------|-------------|
| `list_exercises` | Search and filter exercises by name, muscle group, or equipment |
| `create_exercise` | Add a new custom exercise to your library |
| `delete_exercise` | Remove a custom exercise you created |

### Workout Templates (5 tools)

| Tool | What it does |
|------|-------------|
| `list_templates` | List all your workout templates (plans) |
| `get_template` | View full details of a template including exercises and set schemes |
| `create_template` | Create a new workout template with exercises and set/rep targets |
| `update_template` | Modify an existing template (name, exercises, sets, etc.) |
| `delete_template` | Delete a workout template |

### Training Programs (6 tools)

| Tool | What it does |
|------|-------------|
| `list_programs` | List all programs and see which one is active |
| `get_program` | View a program's full schedule (weeks, days, assigned templates) |
| `create_program` | Build a new multi-week training program |
| `update_program` | Modify a program's schedule or details |
| `delete_program` | Delete a training program |
| `activate_program` | Set a program as your active training program |

### Workout History and Stats (4 tools)

| Tool | What it does |
|------|-------------|
| `get_workout_history` | View recent workout sessions with duration, volume, and exercise count |
| `get_workout_details` | See every set logged in a specific workout session |
| `get_exercise_stats` | Get PR history, best weight, estimated 1RM, and volume trends for an exercise |
| `get_prs` | View personal records across all exercises |

### Body Weight (2 tools)

| Tool | What it does |
|------|-------------|
| `log_body_weight` | Record a body weight measurement for a specific date |
| `get_body_weight_history` | View body weight entries and trends over time |

### Autoregulation (1 tool)

| Tool | What it does |
|------|-------------|
| `suggest_weight_adjustments` | Analyze recent RPE data and suggest weight changes for an exercise |

### Data and Status (2 tools)

| Tool | What it does |
|------|-------------|
| `export_data` | Export a summary of all your data (exercises, templates, programs, sessions, body weight) |
| `get_training_summary` | Get a quick overview of your active program, recent workouts, and body weight |

---

## Example Prompts

Once the MCP server is connected, you can interact with your fitness data using natural language. Here are some things you can ask:

### Quick Status
- "How's my training going?"
- "Give me a summary of my recent workouts."
- "What's my active program?"

### Workout History
- "Show me my last 5 workouts."
- "What did I do in my last push workout?"
- "How much total volume did I do this week?"

### Exercise Stats and PRs
- "What's my bench press PR?"
- "Show me my squat progress over time."
- "What are all my personal records?"

### Weight Suggestions
- "Should I increase my bench press weight?"
- "Based on my RPE, what weight should I use for deadlifts?"

### Body Weight
- "Log my body weight as 185 lbs."
- "Show me my body weight trend."
- "What's my average body weight this month?"

### Managing Templates and Programs
- "Create a new upper body template with bench press, overhead press, and rows."
- "Show me my Push day template."
- "Set up a 4-week push/pull/legs program."
- "List all my workout templates."

### Exercise Library
- "What chest exercises do I have?"
- "Add a new exercise called Bulgarian Split Squat, legs, dumbbell."
- "Show me all barbell exercises."

---

## Troubleshooting

**"API requests will fail authentication" warning**
The `SUNDEROS_API_KEY` environment variable is not set or is empty. Double-check that you pasted the full key starting with `so_`.

**"No exercise found" or empty results**
Your account may not have any data yet. Start by logging a few workouts in the app, then try again.

**Connection refused errors**
Make sure the Sunderos API server is running (`pnpm dev` for development, or your production deployment). Verify the `SUNDEROS_API_URL` points to the correct address and port.

**Key stopped working**
The key may have been revoked or expired. Check the API Keys section in Settings. Generate a new key if needed.
