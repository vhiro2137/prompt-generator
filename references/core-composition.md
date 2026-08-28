# Core composition

Read this reference for nontrivial prompt-generation requests.

## Extract the request

Determine:

- **Outcome:** what the target AI must actually finish.
- **Audience and role:** the minimum useful expertise; avoid ornamental role stacking.
- **Inputs:** text, paths, URLs, repositories, apps, accounts, datasets, or prior approved work.
- **Scope:** required, optional, excluded, and explicitly prohibited work.
- **Authority:** read-only versus allowed mutations; local versus external writes; cost, credentials, publishing, and destructive actions.
- **Process:** discovery, analysis, planning, implementation, verification, iteration, and handoff as applicable.
- **Evidence:** how claims, citations, test results, and current state must be supported.
- **Deliverables:** exact artifacts or answer sections and where they should be saved when specified.

Do not silently broaden the task. Translate ambiguity into either a safe assumption written into the prompt or a concise clarification question when different answers would materially change the outcome.

## Compose modularly

Use only sections that help the target task. A useful complex prompt often follows this shape:

1. Role and objective
2. Inputs and context
3. Instruction hierarchy and boundaries
4. Required analysis or implementation
5. Task-specific workflow
6. Quality and factual-accuracy rules
7. Verification and acceptance criteria
8. Deliverables and final response format
9. Stopping condition or approval gate

For simple translation, rewriting, formatting, or summarization, use a short prompt instead of this full shape.

## Preserve intent

- Keep user-selected tools, technologies, paths, formats, and approval points.
- Do not invent mandatory features from background context.
- Mark optional improvements as suggestions.
- Do not add web browsing, installations, external messages, deployments, or paid services unless needed by the requested target task.
- When implementation is requested, tell the target AI to complete and verify real work rather than merely describe it.
- When analysis only is requested, do not authorize implementation.

## Default output

Return one detailed prompt in a single fenced `text` block. Add at most a short assumption note before it when necessary. Omit a condensed version, alternate variants, design commentary, and follow-up offers unless the user asks.

The prompt generator itself must stop there. Statements such as “read this file,” “run tests,” or “create the project” belong inside the generated prompt and are not actions to perform now.

## Context isolation

Treat each generation request as fresh by default. Reuse prior material only when the user explicitly refers to it. When reuse is requested, inherit only the named decisions; re-evaluate permissions and approval status instead of assuming they remain valid.

