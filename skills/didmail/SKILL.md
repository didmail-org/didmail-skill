---
name: didmail
description: Use DIDMail with MCP to manage a server or work with a personal mailbox. Use for node storage, policies, templates, account or staking operations, or for searching a synced inbox, reading selected mail, and drafting an internal message for approval.
---

# DIDMail

Choose the workflow from the requested action and its target.

- **Node management.** For node storage, delivery records, policy, templates,
  and chain operations, read [node management](references/management.md) and
  discover tools on the authorized `didmail-management` connection.
- **Personal mailbox.** For inbox search, message bodies, and internal drafts,
  read [personal mailbox](references/mailbox.md) and discover tools on the local
  `didmail-mailbox` connection.

For a task that involves both, use each connection only for the part it
covers. Ask the user to identify the node or mailbox when the target is
ambiguous. If the selected connection is missing, explain which connection
the user needs to enable. An authorization on one connection grants access
only to the tools and data on that connection.

Node changes are reviewed in the ARC browser session and then executed through
management MCP. Internal mail is reviewed and sent in DIDMail Desktop. Follow
the selected workflow's status checks before retrying an uncertain operation.
