# TimeTrack MCP Server

Log and query billable hours through any MCP client.

**Tools:** `log_time`, `get_timesheet`, `get_project_summary`, `list_projects`, `summarize_week`, `log_time_with_confirmation`, `slow_tool`
**Resource:** `timesheet://projects` · **Prompt:** `generate_weekly_report`

## Run locally

```
uv run fastmcp run main.py:mcp --transport http --port 8000
```

MCP endpoint: `http://127.0.0.1:8000/mcp`

## Deploy on Prefect Horizon

1. Push this repo to GitHub.
2. Sign in at https://horizon.prefect.io with the same GitHub account and select this repo.
3. Server name: `timetrack` · Entrypoint: `main.py:mcp`
4. Environment variable: `ANTHROPIC_API_KEY` (needed only by `summarize_week`).
5. Deploy. The server will be live at `https://<name>.fastmcp.app/mcp`.

## Data

SQLite at `TIMETRACK_DB_PATH` (default `/tmp/timetrack.db`), seeded with sample entries on first start.
`/tmp` is wiped when the container restarts, so logged hours don't survive a redeploy. Use a hosted database for real data.
