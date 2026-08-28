---
name: prompt-generator
description: Generate or refine one detailed, copy-ready AI prompt from a user's raw requirements. Use when the user explicitly asks for a prompt, prompt optimization, or a structured instruction for another AI; do not use for ordinary requests to perform the underlying task directly.
---

# Prompt Generator

Create the prompt only. Do not perform the task described by the user's raw request: do not inspect referenced files or URLs, run commands, modify files, call external services, build, test, deploy, or send messages. Mention those actions only as instructions for the target AI.

## Workflow

1. Treat the current request as independent unless the user explicitly asks to reuse earlier content. Do not carry over paths, names, technologies, approval state, or output conventions from unrelated tasks.
2. Identify the target AI's outcome, source materials, required work, constraints, permissions, verification, and deliverables.
3. Preserve explicit user choices. Fill low-risk gaps with clearly stated assumptions; ask only when a missing choice would materially change the result or authorize risky/external action.
4. Select only the relevant guidance below. Do not load every reference.
5. Produce one complete prompt, normally in one `text` code block. Do not add a short version, variants, or a prompt-design tutorial unless requested.
6. Stop after the prompt. Never continue by executing it.

## Routing

- For all nontrivial requests, read [references/core-composition.md](references/core-composition.md).
- When files, attachments, URLs, source code, recordings, or other evidence are mentioned, also read [references/materials-and-evidence.md](references/materials-and-evidence.md).
- When the target AI will develop, review, debug, modify, test, deploy, or create a Skill, also read [references/engineering.md](references/engineering.md).
- When the user requests approval before mutation, or the task contains a comparable explicit hold point, also read [references/approval-gates.md](references/approval-gates.md).
- For teaching, document analysis, research, video analysis, interviews, or data analysis, also read [references/analysis-and-learning.md](references/analysis-and-learning.md).

## Invocation boundary

Use this Skill only when prompt creation or prompt refinement is the requested deliverable, including explicit `$prompt-generator` invocation. If the user asks to directly fix code, inspect a document, analyze a video, create an artifact, or perform another task without asking for a prompt, allow the task-specific workflow to handle it instead.

If explicitly invoked, convert even action-oriented raw text into a prompt and do not perform the action.

## Output contract

- Match detail to task complexity; do not force a fixed giant template on simple work.
- A complex prompt should normally define role, objective, materials, instruction hierarchy, scope, workflow, quality criteria, verification, deliverables, and output format.
- Keep source facts, inferences, suggestions, historical evidence, and current verification distinct when relevant.
- Include approval gates only when the user requests them or when a requested plan explicitly requires approval before execution.
- The result must stand alone and be ready to paste into another AI conversation.

