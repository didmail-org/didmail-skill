---
name: didmail-management
description: Operate a DIDMail node through its management MCP server. Use for managing mail storage, node and gas stakes, envelopes, namecards, attachment limits, sender access and mail policy, or reading members and node settings.
---

# DIDMail management

Use the target instance's dedicated management MCP connection. Read-only
`didmail-inspection` is suitable for a node summary. Discover tools from the
management connection when the task calls for individual records or changes.
Use the selected connection's instance throughout the task.

Read [usage terms](TERMS.md) before setting up access or preparing a write.
Keep credentials and unnecessary private records out of chat. Flag the scope
of deletion or publication and any spending, fees, or locked assets when
presenting an approval for a consequential operation.

## Choose parameters

1. Find the relevant tool and inspect its live input schema. Use MCP reads to
   resolve existing records, IDs, versions, categories and chain terms.
2. Ask for missing business choices in one concise question. Distinguish
   sender price from the node's acquisition fee. Preserve decimal amounts as
   strings. For envelope creation ask for the name, description, sender price,
   public or members category, retention days, and sample or SVG. Ask only
   for fields the user has neither supplied nor delegated. If the user
   delegated sample selection, call `list_envelope_samples` or
   `list_namecard_samples` and choose. Fetch current revisions, versions and
   policy IDs through tools.
3. If a selector has multiple matches, show enough detail for the user to
   choose. A user-facing label alone does not identify a record.

## Apply changes

- Call the corresponding `prepare_*` tool. Report the proposed operation and
  give the returned `approvalUrl` to the administrator. The confirmation page
  displays current terms, including the node, chain, recipient or factory fee
  where applicable. The administrator signs in to ARC and confirms the
  operation once. Keep the management key in the client credential store.
- Check `get_operation_status`. Once it returns `approved`, call
  `execute_approved_operation` with the same operation ID. If it reports
  `expired`, `cancelled` or a change of terms, prepare again only with the
  user's current intent and obtain a fresh confirmation.
- After a timeout, first check status. If preparation failed to return an
  ID, use `get_current_operation` to recover it. Treat `executing` or
  `uncertain` as an unknown outcome. Inspect the original record or
  transaction and have the administrator reconcile it before another submission.
- Set `publish: true` on a creation proposal when the user requested
  creation and publication together. Verify both the returned asset and
  publication in the list. If the asset exists and publication is unconfirmed,
  use that exact address in a separate publication proposal. Never recreate
  the asset to recover publication.
- ARC membership and invitations are managed by ARC. Node recharge returns
  destination information for the user's wallet.
