# Project Memory System

When the user corrects Codex or says to remember something about this project, save it as its own Markdown file inside the root `memory/` folder.

Use these filename prefixes:

- `user_` for how the user personally works.
- `project_` for this specific project.
- `feedback_` for corrections to Codex behavior.
- `reference_` for links, facts, or external context to remember.

Keep `memory/MEMORY.md` updated as an index of every rule with a one-line summary so the right memory loads next session.

Maintain companion files:

- `memory/lessons.md` for strategic learnings, patterns, and repeated corrections. Entries should include what happened, why it was wrong, what changed, and the deeper principle.
- `tasks/todo.md` for the active sprint. Plan here before building and mark items complete as work ships.

At the start of every new session, read:

- `memory/MEMORY.md`
- `memory/lessons.md`
- `tasks/todo.md`

Then confirm setup and continue working normally.
