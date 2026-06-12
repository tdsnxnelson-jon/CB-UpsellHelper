# ExecReporting — CBC Reporting Dashboard

Self-hosted dashboard for Carbon Black Cloud data. FastAPI + SQLite backend, React/Vite/Recharts frontend. Widgets poll CBC APIs on configurable intervals via APScheduler and cache results in SQLite. Six data sources: Alerts, Devices, Observations, Process Search, Vulnerability Assessment, Audit Logs.

---

Before implementing anything, tell me if my approach is wrong.
Specifically:
- If I'm solving the wrong problem, say so first
- If there's a significantly better alternative I haven't considered, name it and explain why it's better
- If my idea will cause problems at scale or in edge cases, describe them concretely
- Rank tradeoffs — don't just list pros and cons equally, tell me which matters more
- If something I'm asking for is straightforward and fine, just do it — reserve pushback for when it genuinely matters

Do not implement first and add caveats at the end. Push back before writing any code.
If I ask you to implement something and you think the feature itself
is unnecessary or there's a simpler approach that avoids the problem
entirely, say that instead of building it.
