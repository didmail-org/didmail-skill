# DIDMail Management Skill

Use `$didmail-management` in Codex to manage a DIDMail node through its MCP
tools. The skill discovers tools and resolves technical identifiers before
asking you for any missing business parameters. For writes, it prepares the
operation, waits for a DIDMail administrator to approve it once, and executes
the approved operation through MCP.

## Install in Codex

Ask Codex to install the skill using its skill installer.

```text
Use $skill-installer to install https://github.com/didmail-org/didmail-management-skill/tree/v0.1.0/skills/didmail-management
```

Open a new chat and invoke `$didmail-management`. The skill instructions are
in [SKILL.md](skills/didmail-management/SKILL.md).

## Connect your DIDMail node

Your node operator needs to enable `/mcp/admin` and enroll a dedicated ARC
management access key for that instance. Use `admin` for general management
and `owner` for owner transfer and gas staking. Keep the key in a secret store
and make it available to the Codex process as `DIDMAIL_MCP_MANAGEMENT_KEY`.

Replace the example origin with your node's canonical protocol origin.

```sh
codex mcp add didmail-management \
  --url https://mail.example.com/mcp/admin \
  --bearer-token-env-var DIDMAIL_MCP_MANAGEMENT_KEY
```

For a local node, use the canonical local origin configured by its operator.
The read-only inspection connection uses a separate credential. To revoke
management access, revoke the dedicated access key in the instance's ARC
administration. Remove the saved Codex connection with
`codex mcp remove didmail-management` when it is no longer needed.

## Example prompts

- `$didmail-management Show this node's storage usage and explain what the reported size covers.`
- `$didmail-management Pick a business envelope sample and prepare to create and publish it. Ask me for any missing details.`
- `$didmail-management Show the current attachment limits and prepare to lower the maximum attachment count to three.`

For a proposed write, open the approval link and review the exact operation
and any applicable fees. Confirm in your ARC browser session, then return to
Codex so it can execute through MCP. ARC handles membership changes and
invitations. Recharge uses an external wallet.

## License

Distributed under the [Apache License 2.0](LICENSE). See [NOTICE](NOTICE).
