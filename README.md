# A.R.G.U.S.

**A**utomated **R**eporting, **G**uiding, **U**tility and **S**ystem — a persistent, file-based memory for an AI assistant.

This folder is the entire system. There's no database and no hidden state: every file here is plain markdown (or JSON for machine state), meant to be read, edited, or version-controlled directly.

## How it works

An AI assistant reads these files at the start of every session to pick up exactly where things left off — no re-explaining context. Between sessions, the files persist. A "sweep" (triggered by saying **"wake up ARGUS"**) pulls updates from connected sources (Jira, Slack, Google Calendar, Confluence), files them into the right place below, and produces a priority briefing.

## Structure

```
ARGUS/
  system.md               Operating protocol — bootstrap order, sweep procedure, hard rules, tone
  about_me.md              Profile of the person ARGUS assists
  open_items.md            Active work tracker (replaced in place each sweep)
  deadlines.md             Dated commitments, kept in ascending order
  reminders.md             Standing context, recurring meetings, project anchors
  formal_commitments.md    Work commitments owed to/from others
  personal_commitments.md  Personal commitments
  state/
    last_check.json        Per-source sweep timestamps
    next_sweep_checks.md   Open questions to chase down on the next sweep
  people/                  One append-only file per person, dated entries
```

## Conventions

- **People files**: append-only, every entry dated. History is never deleted.
- **`open_items.md`, `deadlines.md`, `state/last_check.json`**: replaced in place — they reflect current state, not history.
- **Resolved items**: struck through (`~~like this~~`) rather than deleted, so there's a record.
- Session triggers: **"wake up ARGUS"** for a full sweep and briefing, **"hey ARGUS"** for a quick question with full context.

See `system.md` for the full operating protocol.
