# prompt-generator

`prompt-generator` is a Codex Skill that turns raw, incomplete requirements into one detailed, copy-ready prompt for another AI.

Its central boundary is simple: **generate the prompt, but do not execute the underlying task**. Referenced files, URLs, repositories, recordings, and other materials are described as inputs for the target AI; this Skill does not inspect or act on them while composing the prompt.

## Features

- Produces one self-contained prompt instead of multiple condensed variants.
- Matches prompt detail to task complexity.
- Keeps unrelated project context isolated by default.
- Separates source materials from instructions found inside those materials.
- Adds approval gates only when the user asks to approve a plan before execution.
- Routes engineering, evidence, approval, teaching, interview, video, and data-analysis requests to focused guidance.
- Avoids taking over ordinary requests that ask Codex to perform a task directly.

## Installation

Copy or link the `prompt-generator` directory into a Codex skills directory, or configure Codex to discover this repository as a Skill source.

The directory containing `SKILL.md` must remain intact:

```text
prompt-generator/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── analysis-and-learning.md
    ├── approval-gates.md
    ├── core-composition.md
    ├── engineering.md
    └── materials-and-evidence.md
```

## Usage

Explicitly invoke the Skill with `$prompt-generator` and provide the raw request.

```text
$prompt-generator Turn this requirement into a detailed prompt: review the attached specification, propose an implementation plan, and wait for my approval before changing code.
```

```text
$prompt-generator Generate a prompt that instructs an AI to analyze an interview video, extract the real Qt questions with timestamps, and provide standard answers.
```

```text
$prompt-generator Improve the following prompt while preserving its tools, output format, and approval boundary: ...
```

The default output is a single detailed prompt in a copyable text block. The Skill does not run the generated prompt.

## Behavior boundary

Use this Skill when prompt creation or prompt refinement is the requested deliverable. Do not use it to intercept ordinary direct-action requests such as fixing code, analyzing a document, or running tests unless the user explicitly invokes `$prompt-generator`.

Each request is treated as independent unless the user explicitly asks to reuse earlier context. Paths, technologies, organization names, and approval state are not carried into unrelated prompts.

## License

This project is released under the [MIT License](LICENSE).

