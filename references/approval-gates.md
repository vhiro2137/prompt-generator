# Approval gates

Read this reference when the user explicitly asks to review or approve a plan before mutation.

## Two-phase contract

Build the generated prompt around:

### Phase 1: analysis and proposal

Allow only the read-only discovery needed to understand the request. Require a concrete plan with scope, affected files or systems, alternatives, risks, tests, acceptance criteria, and approval items. Do not authorize implementation, installation, deployment, publishing, paid calls, or external writes.

### Phase 2: approved execution

Start only after an explicit approval phrase or unmistakable equivalent. Ordinary acknowledgements, requests for more detail, or partial questions do not grant execution authority. If the user approves selected items, execute only those items.

## Reapproval triggers

Require the target AI to pause when implementation would materially exceed the approved plan, such as:

- changing the core technology or data contract;
- adding paid services or external data transfer;
- installing unapproved software;
- broadening features;
- deleting, overwriting, or migrating material data;
- touching unapproved modules;
- discovering substantially higher risk or cost.

Do not invent approval gates when the user asked for direct implementation. For ordinary reversible implementation, preserve normal autonomy unless the request itself establishes a hold point.

## Approval report

The Phase 1 output should make decisions easy to approve individually and state plainly that no mutation has occurred. When historical reports exist, label them as historical and never present them as fresh verification.

