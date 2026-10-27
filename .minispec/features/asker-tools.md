# Writing, checking and generating Asker questions, and reviewing them

## Goal

A teacher's agent drafts an Asker definitions file from notes, checks it, generates questions from it, and reviews them with the teacher before they're imported into Moodle.

## Context

Decided in falkenslab/agent-extensions (27 October 2026): its own repository and npm package, the three uses (writing the input, generating, reviewing), at the same time as teuton-mcp. ADR-005: the definitions are the source, questions are reviewed.

- **Asker** (`gem install asker-tool`, Ruby; 2.10.0 on RubyGems, 26 October 2026): input in HAML or XML. HAML: `%map{ lang: 'en', context: '…', version: '1'}`, then `%concept` with `%names`, `%tags`, `%def`, and `%table{ fields: '…', sequence: '…'}` with `%row` / `%col`; files, code and problems too (`docs/inputs/` in Asker's repository: `concepts.md`, `tables.md`, `code.md`, `files.md`, `problems/`, `templates.md`). Commands: `asker FILE` (or `asker file FILE`) writes the questions into an `output/` folder (Moodle XML, GIFT, YAML) and prints a table per concept; `asker check FILE` checks the syntax; `asker init` writes a `config.ini` (`[global] internet`, `[questions] exclude`); `asker new FOLDER` writes an example. Examples: `docs/examples/` (bands, starwars, code…) and dvarrui/asker-inputs.
- **Ruby and asker-tool**: the person installs them; `check_requirements` says how (ADR-004).
- **The extension**: `asker` in agent-extensions, with Ruby and asker-tool in `requirements`, and a capability such as `question-generation`; moodle-teacher's `import_questions` takes its GIFT or Moodle XML.

## Changes

- `asker_input_reference` (read-only): Asker's input language in short, from its docs, with an example per element, for writing a file.
- `check_input` (read-only): Asker's verdict on a file, as data (each error with its line).
- `generate_questions`: runs Asker on a file into a local folder (`internet: no`), returns each output's path and the counts per concept and type.
- `read_questions` (read-only): the generated questions, by concept and type, each with its text, answers and the right one; a page at a time.
- `exclude_questions`: a copy of a GIFT or Moodle XML file without the questions given, for importing.
- Docs (English and Spanish), the tools reference, and tests with a fake `asker` and real fixtures from its examples.

## Acceptance

- `npm run check`, `npm test`, `npm run typecheck`, `npm run lint` pass.
- From a page of notes, an input the agent writes passes `check_input`; `generate_questions` makes questions; `read_questions` lists them; two are left out with `exclude_questions`; moodle-teacher imports the rest into a moodle-sandbox bank.
- An input with a syntax error is reported with its line, and nothing is generated.
- Then the `asker` extension in agent-extensions pins the release.
