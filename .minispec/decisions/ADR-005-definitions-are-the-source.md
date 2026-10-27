# ADR-005: the definitions file is the source, and generated questions are reviewed

## Status

Accepted (27 October 2026).

## Context

Asker generates many questions from a definitions file (a concept's names, tags, definition and tables) with fixed templates: they're as right as the definitions and as good as the templates, and a teacher keeps their input files over years (dvarrui/asker-inputs). An AI agent can also write questions directly in GIFT; what Asker adds is questions traced to the teacher's own definitions, many of them, the same every time.

## Decision

- The teacher's definitions file is the source of truth. The agent may draft one from the teacher's notes, but the teacher reviews it before questions come from it; the server never invents content.
- `generate_questions` runs Asker as it is, on that file, and writes its outputs to a local folder; the server never rewrites a question's text.
- Reviewing is part of the flow: `read_questions` returns them by concept and type, and `exclude_questions` writes a copy of the GIFT or Moodle XML without the ones the teacher leaves out (Asker's own `exclude` setting where it fits), before moodle-teacher imports it.
- Asker's `internet` option (looking up image URLs on Google) stays off: the server runs it with `internet: no`.

## Consequences

- No question reaches a course that the teacher hasn't seen in a list or a preview.
- The extension's skills say how to write good definitions for Asker's templates (what makes a usable `%def`, a table Asker turns into matching or ordering), not how to teach.
