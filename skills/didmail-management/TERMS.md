# DIDMail Management Skill usage terms

These terms apply when you use the Skill to operate a DIDMail node. The node
operator controls access to the instance, its data, and its signing wallet.
The Skill is distributed under the Apache License 2.0. The instance's access
and data handling rules apply separately from that software license.

## Authorization and credentials

- Connect only to an instance you administer or are explicitly authorized to
  manage. Confirm its canonical origin and chain network with the operator.
- Use a dedicated ARC management key for that instance. Choose the lowest ARC
  role that covers the task. Use the separate inspection connection when a
  node summary is sufficient.
- Store the key in your client's secret store. Keep keys, wallet secrets, and
  login tokens out of prompts, logs, tickets, and shared documents. Revoke the
  key in ARC if access ends or you suspect exposure.

## Data and operation risks

- An AI client may receive the inputs and operational records it processes.
  Limit queries to the data needed for the task and follow the instance's
  data handling rules for client retention and sharing. Keep mail metadata,
  member information, and private files out of public or unapproved systems.
- Mail deletion can remove records and encrypted attachments. Policy changes
  can affect future delivery or access. Template publication can make a
  template available to its selected audience. Confirm scope and recovery
  requirements before approving changes.
- NFT acquisition, transfers, and staking can incur network or factory fees,
  spend funds, or lock assets. Confirmed on-chain transactions generally cannot
  be reversed. Verify the instance, network, target, amount, fees, and scope on
  the node's ARC approval page before confirming a write. Treat AI suggestions
  as proposals for your review.

## Approval and uncertain results

Review each write on the intended instance, sign in to ARC, and confirm once.
After execution, check the result against the affected records or chain. If
the client times out or the result is unclear, recover the original operation
status and reconcile any effects before preparing or submitting it again.
