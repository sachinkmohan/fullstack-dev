# fullstack-dev

Personal learning monorepo. Each top-level topic folder (`typescript/generics`, `react/hooks`, etc.) is a self-contained `/teach` skill workspace with its own `MISSION.md`, `NOTES.md`, `RESOURCES.md`, `lessons/`, `reference/`, and `learning-records/`. Per-workspace rules live in those files — do not duplicate them here.

## index.html

`index.html` is the human-facing portal that links lessons across all workspaces. When new lessons land in a workspace, add or update its section in `index.html`. Follow the existing pattern exactly:

- One `<h2>` per topic, in the same style as the existing sections.
- One `<li><a>` per lesson, with `lesson-num` (zero-padded "01", "02", …) and `lesson-title`.
- Tag the first lesson of a topic with `<span class="lesson-tag">start here</span>`. Use `supplementary` for off-the-main-path lessons. No tag for the rest.
- Order lessons by intended reading order, not file name.

## When invoked at the root

If asked to set up a new topic, create a new top-level folder following the `/teach` skill convention — then add a corresponding section to `index.html`. Don't add a CLAUDE.md inside the topic folder; per-workspace context belongs in `MISSION.md` and `NOTES.md`.
