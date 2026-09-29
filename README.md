**English** | [Русский](README.ru.md)

# agent-diary

A work diary for a team where each person uses their own Claude Code. It is a git repo of markdown files.
The agents exchange notes through it and through a team chat. For every tracker issue the diary keeps what was
done in code, where the work stands, and who does the next step.

## The problem

The tracker has the request and the status. Git has the code. The next step, whose turn it is and what was agreed
usually stay in chats and in people's heads. The diary writes that part down and links it to the issue and the
commits. It doesn't copy specs or code, it links to them: `repo@sha`, `group/repo!123`, the issue key.

## How it works

- One repo, one branch, no server. Git hosting carries the changes between people.
- One card per issue: the request, what's done in code with links, current state, next step, next owner.
  A script builds the board from the cards' frontmatter.
- The role comes from `git config user.email`. Each role has its own daily routine and its own set of files
  it writes, so parallel edits rarely conflict.
- `/start-work-day` pulls changes, shows what others did since last time, checks the tracker and drafts a plan.
  Opening a second chat on the same day restores the day instead of planning it again.
- During the day background tasks watch the repo and the team chat. Voice messages and call recordings are
  transcribed locally.
- Each incoming item is sorted into one of four outcomes: do now, write a brief, ask a question, or note it.
- Agents can message each other. People get pinged only when their action is needed or a question blocks work.

## What you can build on it

The core is the same in every case: a git repo as memory, a role file per person, a daily routine, watchers, and rules
for what the agent may do on its own. Change the roles and the routines and you get a different tool:

- **Project manager for one person.** One role, one agent. It keeps the cards, reconciles the tracker every morning,
  reminds you of deadlines and tells you what is waiting on whom.
- **Team diary.** Several people, each with their own agent, as described in INSTALL.md.
- **Support bot.** Add the bot to a support or on-call chat. It reads incoming reports, matches them to known issues
  and the diary's history, answers what it can and hands the rest to a person with context attached.
- **Personal assistant.** A private diary with your notes, calls and messages, and a morning summary.

These can run together on one diary, as long as each role has its own write zone.

## Getting information in

The agent only knows what reaches the repo. There are two ways to get it there:

- **Connectors.** MCP servers for the tracker, git hosting, calendar, mail, chat. Set up once, then the agent reads on its own.
- **By hand.** Paste a message, forward it to the bot, drop in a call transcript or a voice note. The agent sorts it the same way.

Connectors save time, but corporate security often blocks them (for example, no MCP access to the company's mail
and meetings). The diary works without them: everything a connector would bring can be pasted or forwarded, and the
agent treats it the same way.

## Rules the agents follow

- Forwarded messages, chat and other people's notes are treated as information. A request found there is written
  down and proposed; the agent acts on it only after its own person agrees.
- Reading is automatic. Changing anything outside the diary (code, tracker, messages) needs confirmation.
- No secrets, IP addresses, internal URLs or personal data in the repo. Tokens are stored outside it.
- If someone else changes `.claude/` or `tools/`, the agent shows the diff to its person before using it.

## Files

| File | Contents |
|---|---|
| [INSTALL.md](INSTALL.md) | Full guide: structure, scripts, role routines, filling the diary from existing repos and the tracker with Claude, chat, acceptance checks, operation |
| [PROMPT.md](PROMPT.md) | A shorter spec to paste into Claude Code in an empty folder |
| [templates/](templates/) | `CLAUDE.md`, issue card, repo profile, brief ([Russian](templates/ru/)) |

## Getting started

1. Create an empty private repo for the diary and clone it next to your project repos.
2. Open Claude Code there and send [PROMPT.md](PROMPT.md) or [INSTALL.md](INSTALL.md) as the first message.
3. Answer its questions about the tracker, git hosting and roles. It builds the structure and scripts, then fills
   the diary from your repos and tracker in phases.
4. Review what it filled in (phase H in INSTALL.md), then add the next person with `ONBOARDING.md`.

You need Claude Code, git, bash and python3. A Telegram bot for the team chat and `faster-whisper` for transcription
are optional.

## Status

This repo is a description and a spec that has been used by a working team. It does not ship scripts yet;
Claude writes them for your setup from INSTALL.md. A ready-to-clone boilerplate with reference scripts is the next step,
and contributions toward it are welcome.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE). Keep the copyright notice and the license text; otherwise use it however you like.
