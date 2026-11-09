# DIDMail Mailbox Skill usage terms

Use the Skill with a mailbox you own or have explicit permission to operate.
The mailbox owner chooses which capabilities to grant in DIDMail Desktop.
The Skill is distributed under the Apache License 2.0. The node's access and
data handling rules also apply when using it to operate a mailbox.

- Grant only the capabilities you need. Message subjects, senders and bodies
  can contain private information. The AI client may retain information it
  reads. Follow the mailbox operator's data handling rules.
- Keep the session token in the local MCP client's secret store. End the
  session in DIDMail Desktop if you suspect exposure or finish the task.
- Review the intended node, recipient, subject, message and delivery terms in
  DIDMail Desktop before confirming a send. Confirming can deliver mail to
  the recipient. Check the original operation or Outbox before retrying
  after an uncertain result.
