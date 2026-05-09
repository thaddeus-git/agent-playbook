# agent-playbook

Shared method for building Claude Code agents in our team.

**Read [PLAYBOOK.md](PLAYBOOK.md) — that's the artifact.** This README only describes how to consume the playbook in a project.

---

## What's in here

- **[PLAYBOOK.md](PLAYBOOK.md)** — the method itself. Sequenced steps, named artifacts, and the discipline that keeps work reviewable when one person designs and Claude implements.

That's it. One file. The playbook itself is the deliverable; everything else is plumbing.

---

## How to consume it in a project

Two options. Pick based on how often you expect the playbook to change.

### Option A — Git submodule (recommended for active teams)

The project tracks a specific commit of the playbook. Update intentionally; never silently drift.

```bash
# In your project root (e.g., geo_agent/, my-other-agent-project/, etc.)
git submodule add git@github.com:thaddeus-git/agent-playbook.git docs/playbook
git commit -m "Add agent-playbook as submodule"
```

Then in your project's `CLAUDE.md`, add this line near the top so every Claude session loads it:

```markdown
@docs/playbook/PLAYBOOK.md
```

To update later when the playbook changes:

```bash
git submodule update --remote docs/playbook
git add docs/playbook
git commit -m "Update agent-playbook to latest"
```

### Option B — Copy the file (simpler for one-off use)

```bash
# In your project root
mkdir -p docs/playbook
curl -o docs/playbook/PLAYBOOK.md \
  https://raw.githubusercontent.com/thaddeus-git/agent-playbook/main/PLAYBOOK.md
git add docs/playbook/PLAYBOOK.md
git commit -m "Add agent-playbook (copy)"
```

Then add `@docs/playbook/PLAYBOOK.md` to your project's `CLAUDE.md` as above.

You'll need to manually re-copy when the playbook updates. Acceptable for solo / one-project use.

---

## Editing the playbook

The playbook is a living doc. Open a PR when:

- A team retro reveals a missing step
- A recurring mistake reveals an unwritten rule
- An Anthropic update changes a primitive's behavior

Don't update from theory. Update from real friction.

---

## Related repos

- **[agent-template](https://github.com/thaddeus-git/agent-template)** — empty scaffolding (intake / ADR / LikeC4 directories) you fork to start a new project. Pairs with this playbook.
