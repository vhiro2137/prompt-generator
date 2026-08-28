# Engineering prompts

Read this reference when the target AI will design, build, inspect, modify, test, deploy, or create a Codex Skill.

## Development and modification

Shape the generated prompt to require, as applicable:

- inspect repository instructions, structure, dependencies, existing behavior, tests, and user changes;
- translate requirements into traceable implementation scope;
- choose the smallest architecture that meets the request and explain consequential tradeoffs;
- preserve unrelated work and avoid opportunistic rewrites;
- implement complete behavior, including validation and error paths;
- build, test, and exercise representative workflows;
- distinguish tests actually run from historical reports;
- report changed files, verification evidence, limitations, and safe next steps.

For diagnosis-only requests, stop after evidence-backed cause analysis unless the user also requested a fix.

## Review and gap analysis

When comparing requirements to existing code, require a traceability matrix containing requirement evidence, implementation evidence, test evidence, status, severity, and recommended action. Do not label an enhancement as a defect without requirement evidence. Separate static inspection from runtime confirmation.

## Risk and validation

Scale verification to impact. Consider unit, integration, end-to-end, host-process, performance, security, migration, visual, or manual validation only when relevant. Include rollback for risky changes and require reapproval when an approval-gated plan materially changes.

## Skill creation

When the requested deliverable is a Codex Skill, direct the target AI to use `skill-creator` when available and to:

- define a discriminating name and description;
- keep `SKILL.md` concise;
- place conditional detail in focused references;
- add scripts or assets only when they have concrete reuse value;
- avoid hard-coding personal paths or example-specific facts;
- validate with the official validator;
- behavior-test realistic positive, negative, and boundary cases;
- report the final path, structure, invocation, and limitations.

Do not make this prompt-generating Skill create the requested downstream Skill. Its output only instructs the target AI to do so.

