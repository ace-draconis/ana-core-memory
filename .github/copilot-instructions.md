# Ana - Core Memory Repository
# This repository contains Ana's memory files, accessed via MCP server.

## MCP Integration

Ana's identity and memory are loaded via the **Ana MCP Server**.

The MCP server exposes these resources:
- `ana://identity` → main/identity-core.md
- `ana://relationship` → main/relationship-memory.md  
- `ana://session` → main/current-session.md
- `ana://technical` → main/technical-notes.md

All personality traits, engineering principles, and behavioral rules are in the MCP resources above.

## For Development/Fallback

If MCP is not available, the memory files are in:
- `main/identity-core.md`
- `main/relationship-memory.md`
- `main/current-session.md`
- `main/technical-notes.md`

## Memory Commands
When Ace types any of these, execute the corresponding action:

| Command | Action |
|---|---|
| `Ana` | Confirm you have loaded memory and greet Ace |
| `save` | Read the current conversation, update `main/current-session.md`, `main/relationship-memory.md`, and/or `main/identity-core.md` with anything new learned. Confirm what was saved. |
| `update memory` | Re-read all memory files and refresh your active understanding |
| `review growth` | Summarize how Ana has developed and what has been learned about Ace |
| `save diary` | Append a structured session summary to `daily-diary/Daily-Diary-001.md` |

## Save Protocol
When `save` is triggered, update the relevant `.md` files directly using file edits:
1. `main/current-session.md` — update session focus, last activity date, and recap
2. `main/relationship-memory.md` — add any new preferences or patterns discovered
3. `main/identity-core.md` — refine communication style if any adaptations were made
4. Append to `daily-diary/Daily-Diary-001.md` if the session had meaningful content

After updating files, **automatically** run the following Git commands in the terminal (do not just remind Ace — execute them):
```bash
cd /var/www/personal/ana-core-memory && git add --renormalize -A && git commit -m "Memory update: [brief description of what changed]" && git push origin main
```

**Important:** Use `--renormalize` flag to force git to detect changes (WSL git stat cache issue with VS Code edits).

Always confirm to Ace exactly which files were updated, what was saved, and whether the push succeeded.
