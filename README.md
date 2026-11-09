# DIDMail Skills

Use DIDMail from Codex with a skill for the task at hand.

| Skill | What it does | Connection |
| --- | --- | --- |
| `$didmail-management` | Inspect and manage a node, including storage, policies, templates and reviewed chain operations | An authorized DIDMail Server at `/mcp/admin` |
| `$didmail-mailbox` | Search a synced inbox, read selected cached bodies, and prepare a text-only internal email | An explicitly enabled local session in DIDMail Desktop |

## Install in Codex

Ask Codex to install one or both versioned skills.

```text
Use $skill-installer to install https://github.com/didmail-org/didmail-skill/tree/v0.2.0/skills/didmail-management
Use $skill-installer to install https://github.com/didmail-org/didmail-skill/tree/v0.2.0/skills/didmail-mailbox
```

Open a new chat and invoke the installed skill by name. Each skill uses the
tools exposed by its configured connection.

## Node management

The node operator enables `/mcp/admin` and enrolls a dedicated ARC key for
that instance. Use `admin` for general management and `owner` for owner
transfer and gas staking. Supply the key to Codex via your secret store.

```sh
codex mcp add didmail-management \
  --url https://mail.example.com/mcp/admin \
  --bearer-token-env-var DIDMAIL_MCP_MANAGEMENT_KEY
```

Replace the example origin with the node's canonical protocol origin. A
proposed write requires a one-time review in the node's ARC browser session.
Deletion can remove encrypted mail and attachments. Chain operations can
spend funds, incur fees, or lock assets. Check the original operation after
an uncertain result. Revoke access in the instance's ARC administration.
[Management usage terms](skills/didmail-management/TERMS.md)

## Personal mailbox

Use a DIDMail Desktop build that includes **Settings → Mailbox MCP**. Select
the node and mailbox in Desktop, sync your inbox, and start a local session.
Enable message-body reads or internal drafting if needed. Keep the page open
and use the displayed loopback URL and token on the same computer.

```sh
codex mcp add didmail-mailbox \
  --url http://127.0.0.1:PORT/mcp \
  --bearer-token-env-var DIDMAIL_MAILBOX_MCP_TOKEN
```

Replace the example URL with the URL shown by Desktop. Supply the session
token to the Codex process through a local secret store. The session expires
after 30 minutes or when you leave the page, hide the app, or switch account
or node. Set up the connection again with the new URL and token for a later
session.

The AI can see the mailbox data you authorize. Drafting is limited to plain
text and internal delivery. Review the recipient, message and retention in
Desktop and confirm there to send. Use Outbox to check an uncertain result.
[Mailbox usage terms](skills/didmail-mailbox/TERMS.md)

## Example prompts

- `$didmail-management Show this node's storage usage and explain what the reported size covers.`
- `$didmail-mailbox Find the recent onboarding email in my synced inbox. Read it if body access is enabled.`
- `$didmail-mailbox Draft an internal reply thanking the sender. Ask me for any missing details, then prepare it for my review.`

## License

Distributed under the [Apache License 2.0](LICENSE). See [NOTICE](NOTICE).
