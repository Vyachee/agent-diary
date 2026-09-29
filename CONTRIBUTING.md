**English** | [Русский](CONTRIBUTING.ru.md)

# Contributing

## What would help

- Scripts that implement the spec in [INSTALL.md](INSTALL.md): `sync.sh`, `watch.sh`, `day.sh`, `board.py`,
  `chat.py`, `setup.sh`, passing the checks from the acceptance section.
- Tracker adapters (an MCP server and `tracker_pull.py`) for Jira, YouTrack, Linear, GitHub Issues, GitLab Issues.
- Support for messengers other than Telegram.
- Problems you ran into using this in a team, and the rule that fixed them. These go into "Common mistakes".
- Translations. English is the default, Russian is in `*.ru.md` and `templates/ru/`. A new language follows the
  same naming (`*.<lang>.md`, `templates/<lang>/`) and gets a link in the language line at the top of each file.

## Rules

- For a large change, open an issue first and describe what and why.
- One topic per PR.
- Examples must be made up: no real companies, people, addresses, tokens or issues.
- Scripts use bash or python3 with the standard library only.
- If you change a document, update the other languages too, or say in the PR that they need updating.
- Contributions are accepted under the [MIT](LICENSE) license.
