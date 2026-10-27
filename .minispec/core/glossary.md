# Glossary

- **Tool**: what the server offers a client, with a name, a description for the model, schemas and annotations.
- **Requirement**: a program the person installs apart on their computer (Docker, ffmpeg), which the server checks and explains but never installs.
- **Extension**: the folder in agent-extensions that runs this server for an agent (and Claude Code), with its skills and capabilities.
- **Capability**: what an extension lets an agent do, for the person: its skills plus its tools.

- **Input**: an Asker definitions file (HAML or XML), a `%map` of `%concept`s.
- **Concept**: one entry of an input, with its names, tags, definition and tables, from which Asker makes its questions.
