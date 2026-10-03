# Patch notes

- Fixed task search so archive and status filters apply to both title and description matches. Moved pagination into the database query, validated page parameters/status, and removed the artificial per-request delay.
- Aborted obsolete frontend search requests and reset pagination when filters change, preventing stale results and empty pages after narrowing a search.
- Left task creation, authentication, and broader performance work unchanged; they are outside the current read-only search flow. The largest remaining risk is that the schema has no indexes, so substring searches can become slow as the task table grows.
- I used GitHub Copilot to inspect the frontend, Spring repository/controller, and SQL reference; I reviewed the changes and exercised the API/build locally.
- Handwritten explanation photos are not included; I cannot produce authentic handwritten notes. Add your own photos under `handwritten/` before submission.
